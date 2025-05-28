Object-Relational Mapping is a programming technique that facilitates data conversion between incompatible systems using object-oriented programming languages. It allows developers to interact with a database using the programming language's native syntax, making data manipulation more intuitive and reducing the need for extensive SQL queries. ORM is particularly beneficial when complex data interactions are required, as it simplifies database access and promotes code reusability.
## Commonly Used ORM Frameworks
Several ORM frameworks are widely used in the development community, each catering to different programming languages and environments. Here are a few examples:
**Doctrine (PHP)**

Doctrine is a powerful and flexible ORM framework for PHP. It is particularly popular in the Symfony framework but can be used independently. Doctrine provides a comprehensive set of tools for database interactions, including a query builder, schema management, and an object-oriented query language. Its ability to map complex object structures to database schemas makes it a favourite among PHP developers.

**Hibernate (Java)**

Hibernate is a robust and mature ORM framework for Java applications. It simplifies the mapping of Java classes to database tables and provides powerful data retrieval and manipulation capabilities through its Hibernate Query Language (HQL). Hibernate supports various database management systems and is known for its performance optimisation features, such as caching and lazy loading.

**SQLAlchemy (Python)**

SQLAlchemy is a versatile and powerful ORM for Python. It offers an SQL toolkit and an ORM system that allows developers to use raw SQL when needed while still providing the benefits of an ORM. SQLAlchemy's flexibility and modular architecture make it suitable for a wide range of applications, from small scripts to large-scale enterprise systems.

**Entity Framework (C#)**

Entity Framework is Microsoft's ORM framework for .NET applications. It enables developers to work with relational data using domain-specific objects, eliminating the need for most data-access code that developers typically need to write. Entity Framework supports a variety of database providers and integrates seamlessly with other .NET technologies.

**Active Record (Ruby on Rails)**

Active Record is the default ORM for Ruby on Rails applications. It follows the Active Record design pattern, which means that each table in a database corresponds to a class, and each row in the table corresponds to an instance of that class. Active Record simplifies database interactions by providing a rich set of methods for querying and manipulating data.

## How ORM Works
ORM is a technique that simplifies data interaction in an application by mapping objects in code to database tables. In PHP, this process involves defining classes that represent database tables and their relationships. Each class property corresponds to a column in the table, and each class instance represents a row.
For instance, using Laravel's Eloquent ORM, you might define a model class like this:

 ```php 
 namespace App\Models; 
 use Illuminate\Database\Eloquent\Model; 
 class User extends Model {     
	protected $table = 'users';     
	protected $fillable = [         
		'name', 'email', 'password',
	];     
	// Other Eloquent model configurations can go here... 
}
 ```
 In this example, the `User` class maps to the `users` table in the database, with properties corresponding to columns.
### Common ORM Operations (Create, Read, Update, Delete)
**Create**: Creating new records in the database involves instantiating a new model object, setting its properties, and saving it to the database.
```php
use App\Models\User;

// Create a new user
$user = new User();
$user->name = 'Admin';
$user->email = 'admin@example.com';
$user->password = bcrypt('password'); 
$user->save();
```
**Read**: Reading records from the database involves retrieving data using various Eloquent methods.
```php
use App\Models\User;

// Find a user by ID
$user = User::find(1);

// Find all users
$allUsers = User::all();

// Find users by specific criteria
$admins = User::where('email', 'admin@example.com')->get();
```
The function `find(1)` retrieves the user with ID 1 by executing a SELECT SQL statement.
