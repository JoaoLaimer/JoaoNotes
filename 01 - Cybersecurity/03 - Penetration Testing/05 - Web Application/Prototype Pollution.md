Prototype pollution is a vulnerability that arises when an attacker manipulates an object's prototype, impacting all instances of that object. In JavaScript, where prototypes facilitate inheritance, an attacker can exploit this to modify shared properties or inject malicious behavior across objects.
_Prototype pollution, on its own, might not always present a directly exploitable threat. However, its true potential for harm becomes notably pronounced when it joins with other types of vulnerabilities, such as XSS and CSRF._

## A Common Example
Let's assume, we have a basic prototype for `Person` with an `introduce` method. The attacker aims to manipulate the behavior of the `introduce` method across all instances by altering the prototype.
```JavaScript
// Base Prototype for Persons 
let personPrototype = {   
	introduce: function() {     
		return `Hi, I'm ${this.name}.`;   
	} 
};  
// Person Constructor Function 
function Person(name) {   
	let person = Object.create(personPrototype);   
	person.name = name;   
	return person; 
}  
// Creating an instance 
let ben = Person('Ben');
```
What if an attacker injects malicious content into the introduce method for all instances using the `__proto__` property. In JavaScript, the `__proto__` property is a common way to access the prototype of an object, essentially pointing to the object from which it inherits properties and methods. Let's see, somehow, the attacker executes the following code using any attack vector like XSS, CSRF, etc.  

```JavaScript
// Attacker's Payload 
ben.__proto__.introduce=function(){console.log("You've been hacked, I'm Bob");} 
console.log(ben.introduce());
```
- **Prototype Definition**: The Person prototype (personPrototype) is initially defined with a harmless `introduce` method, introducing the person.
- **Object Instantiation**: An instance of Person is created with the name `'Ben' (let ben = Person('Ben');)`.
- **Prototype Pollution Attack**: The attacker injects a malicious payload into the prototype's `introduce` method, changing its behaviour to display a harmful message. We have polluted the `__proto__` property here.
- **Impact on Existing Instances**: As a result, even the existing instance (`ben`) is affected, and calling `ben.introduce()` now outputs the attacker's injected message.

## Standard Approach
The `constructor` and `__proto__` properties stand out as particularly notable targets for exploitation by threat actors.
The `constructor` property points to the function that constructs an object's prototype, while `__proto__` is a reference to the prototype object that the current object directly inherits from. 
### Golden Rule

The concept hinges on an attacker's ability to influence certain key parameters, such as `x` and `val`, in expressions akin to `Person[x][y] = val`. Suppose an attacker assigns `__proto__` to `x`. In that case, the attribute identified by `y` is universally set across all objects sharing the same class as the object with the value denoted by `val`.

In a more intricate scenario, when an attacker has control over `x`, `y`, and `val` in a structure like `Person[x][y][z] = val`, assigning `x` as `constructor` and `y` as `prototype` leads to a new property defined by `z` being established across all objects in the application with the assigned `val`. This latter approach necessitates a more complex arrangement of object properties, making it less prevalent in practice.

```JSON 
{
	"path": "reviews[0].content",
	"value": "&#60;script&#62;alert('anycontent')&#60;/script&#62;" 
};
```
```JSON
{ "__proto__": { "newProperty": "value" } }
```

