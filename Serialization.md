Serialization is the process of transforming an object's state into a human-readable or binary format (or a mix of both) that can be stored or transmitted and reconstructed as and when required. This capability is essential in applications where data must be transferred between different parts of a system or across a network, such as in web-based applications. 
**Example**

```php
   <?php $noteArray = array("title" => "My THM Note", "content" => "Welcome to THM!"); 
   $serialisedNote = serialize($noteArray);  // Converting the note into a storable format 
   file_put_contents('note.txt', $serialisedNote);  // Saving the serialised note to a file 
   ?>
```

The following output shows the serialized string in the `note.txt` file, which includes details of the note's structure and content. It’s stored in a way that can be easily saved or transmitted.

**Serialised Note**: `a:2:{s:5:"title";s:12:"My THM Note";s:7:"content";s:12:"Welcome to THM!";}`
## Deserialization
Deserialization is the process of converting the formatted data back into an object. It's crucial for retrieving data from files, databases, or across networks, restoring it to its original state for usage in applications.
#### Specific Incidents Involving Serialisation Vulnerabilities
**Log4j Vulnerability CVE-2021-44228**  
- **Incident**: The [Log4j vulnerability](https://nvd.nist.gov/vuln/detail/CVE-2021-44228), or Log4Shell, is a critical security flaw found in the Apache Log4j 2 library, a widely used logging library in Java applications. The vulnerability allows remote attackers to execute arbitrary code on affected systems by exploiting the library's insecure deserialisation functionality. If you want to learn more about this vulnerability.
**WebLogic Server Remote Code Execution CVE-2015-4852**
- **Incident**: This vulnerability was related to how the [Oracle WebLogic Server](https://www.oracle.com/security-alerts/alert-cve-2015-4852.html) deserialised data was sent to the T3 protocol. Attackers could send maliciously crafted objects to the server, which, when deserialised, led to remote code execution.
**Jenkins Java Deserialisation CVE-2016-0792**
- **Incident**: [Jenkins](https://www.tenable.com/plugins/nessus/89034), a popular automation server used in software development, experienced a critical vulnerability involving Java deserialisation. Attackers could send crafted serialisation payloads to the Jenkins CLI, which, when deserialised, could allow arbitrary code execution.
## Serialization Formats
### PHP Serialization
In PHP, serialisation is accomplished using the `serialize()` function. This function converts a PHP object or array into a byte stream representing the object's data and structure. The resulting byte stream can include various data types, such as strings, arrays, and objects, making it unique. To illustrate this, let's consider a notes application where users can save and retrieve their notes.
Example: 
```php
$note = new Notes("Test serialize"); // goes to Notescontent attribute in the Notes class.
$serialized_note = serialize($note);
```

This will generate the output:
`O:5:"Notes":1:{s:7:"content";s:14:"Test serialize";}`
Where: 
- `O:5:"Notes":1:`: This part indicates that the serialized data represents an object of the class **Notes**, which has one property.
-  `s:7:"content"`: This represents the property name "**content**" with a length of 7 characters. In serialized data, strings are represented with `s` followed by the length of the string and the string in double quotes. Integers are represented with `i` followed by the numeric value without quotes.
- `s:14:"Test serialize"`: This is the value of the **content** property, with a length of 14 characters.
**Magic Methods**
PHP provides several [magic methods](https://www.php.net/manual/en/language.oop5.magic.php) that play crucial roles in the serialization process. A few of the important methods are mentioned below:
- `__sleep()`: This method is called on an object before serialization. It can clean up resources, such as database connections, and is expected to return an array of property names that should be serialized.
- `__wakeup()`: This method is invoked upon deserialization. It can re-establish any connections that the object might need to operate correctly.
- `__serialize()`: As of PHP 7.4, this method enables you to customize the serialization data by returning an array representing the object's serialized form.
- `__unserialize()`: This counterpart to `__serialize()` allows for customizing the restoration of an object from its serialized data.

### Python
Python uses a module called **Pickle** to serialise and deserialise objects. This module converts a Python object into a byte stream (and vice versa), enabling it to be saved to a file or transmitted over a network.
```python
import pickle
import base64
...
pickled_content = pickle.dumps(notes_obj)
serialized_data = base64.b64encode(pickled_content).decode('utf-8')
...
serialized_data = request.form['serialized_data']
notes_obj = pickle.loads(base64.b64decode(serialized_data))
...
```
**Serialisation (Pickling)**: When a user submits a note, the Notes class instance (including all notes) is serialised using `pickle.dumps()`. This function transforms the Python object into a binary format that Python can later turn back into an object.
**Unpickling**: The binary data is then passed to `pickle.loads()`, which reconstructs the original Python object from the binary stream.
Obs: base64 is used to display serialized data in binary.

