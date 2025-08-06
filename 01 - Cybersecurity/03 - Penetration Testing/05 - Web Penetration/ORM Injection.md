[[SQL injection]] and ORM injection are both techniques used to exploit vulnerabilities in database interactions, but they target different levels of the stack.
- **SQL Injection**: Target raw SQL queries, allowing attackers to manipulate SQL statements directly.
- **ORM injection**: Targets the ORM framework, exploiting how it constructs queries from object operations.

| **Aspect**         | **SQL Injection  <br>**                                             | **ORM Injection**                                                                                 |
| ------------------ | ------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| Level of injection | Targets raw SQL queries directly                                    | Targets the ORM framework's query construction                                                    |
| Complexity         | More straightforward, as it manipulates raw SQL                     | Requires understanding of ORM internals and methods                                               |
| Detection          | Easier to detect with traditional WAFs and query logs               | Harder to detect, as payloads are within ORM methods                                              |
| Mitigation         | Use of prepared statements, parameterised queries, input validation | Proper ORM configuration, application-level input validation, ORM features enforcing query safety |
