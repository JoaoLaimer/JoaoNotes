Ruby on Rails is a web application framework that is vulnerable to this type of attack. The following example shows how attackers can exploit mass assignment vulnerability in Ruby on Rails. Assuming we have a `User` model with the following attributes:
```ruby
class User < ActiveRecord::Base
  attr_accessible :username, :email
end
```
The above model specifies that only the `username` and `email` attributes are allowed to be mass-assigned. However, attackers can modify other attributes by tampering with the parameters sent to the server. Let's assume that the server receives the following parameters.
```javascript
{ "user" => { "username" => "hacker", "email" => "hacker@example.com", "admin" => true } }
```

Although the `User` model does not explicitly state that the `admin` attribute is accessible, the attacker can still change it because it is present in the arguments. Bypassing any access controls that may be in place, the attacker can send this data as part of a POST request to the server to establish a user with admin privileges.

