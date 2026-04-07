Powershell is the Windows Scripting Language and shell environment built using the .NET framework.

This also allows Powershell to execute .NET functions directly from its shell. Most Powershell commands, called _cmdlets,_ are written in .NET. Unlike other scripting languages and shell environments, the output of these _cmdlets_ are objects - making Powershell somewhat object-oriented.

This also means that running cmdlets allows you to perform actions on the output object (which makes it convenient to pass output from one _cmdlet_ to another). The normal format of a _cmdlet_ is represented using **Verb-Noun**; for example, the _cmdlet_ to list commands is called `Get-Command`

Common verbs to use include:

- Get
- Start
- Stop 
- Read
- Write
- New
- Out

To get the complete list of approved verbs, visit [this](https://docs.microsoft.com/en-us/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands?view=powershell-7) link.
### Get-Help
`Get-Help` displays information about a cmdlet. 
`Get-Help Commnad-Name`
You can also understand how exactly to use the command by passing in the `-Examples` flag.

### Get-Command
`Get-Command` gets all the cmdlets installed on the current Computer. The great thing about this cmdlet is that allows for pattern matching like the following:
`Get-Command Verb-*` or `Get-Command *-Noun`

### Object Manipulation
The Pipeline(`|`) is used to pass output from one cmdlet to another. A major difference compared to other shells that Powershell passes an object to the next cmdlet instead of passing text or string.
You can use the following command to view the members of the object: 
```Powershell
Get-Command | Get-Member -MemberType Method
```


### Creating Objects From Previous cmdlets
Using the `Select-Object` cmdlet, you can manipulate objects pulling out the properties from the output and creating a new object.
```Powershell
Get-ChildItem | Select-Object -Property Mode, Name
```

You can also use the following flags to select particular information: 
- first - gets the first x object 
- last - gets the last x object
- unique - shows the unique objects
- skip -skips x objects
### Filtering Objects 
When retrieving output objects, you may want to select objects that match a very specific value. You can do this using the `Where-Object` to filter based on the value of properties.
The general format for using this cmdlet is:

`Verb-Noun | Where-Object -Property PropertyName -operator Value`

`Verb-Noun | Where-Object {$_.PropertyName -operator Value}`

The second version uses the `$_` operator to iterate through every object passed to the `Where-Object` _cmdlet_.

Where `-operator` is a list of the following operators:
- `-Contains`: if any item in the property value is an exact match for the specified value
-  `-EQ / -GT`: if property value is equal/greater than the specified value.

### Sort-Object
When a cmdlet outputs a lot of information, you may need to sort it to extract the information more efficiently. You do this by pipe-lining the output of a cmdlet to the `Sort-Object` cmdlet.
An example: 
```Powershell
Get-ChildItem | Sort-Object
```

#### Notes
Decoding/Encoding base64:
```Powershell
[Text.Encoding]::UTF8.GetString(([Convert]::FromBase64String((Get-Content "C:\File"))))

[Convert]::ToBase64String([IO.File]::ReadAllBytes("C:\Path"))
```

Find file:
```Powershell
Get-ChildItem -Path "Path" -Filter "filename" -Recurse -ErrorAction SilentlyContinue
```

Count instances: 
```Powershell
(Rest-of-commands) | Measure-Object
```

Get open ports: 
```Powershell
Get-NetTCpConnection -State Listen
```

Get IP information:
```Powershell
Get-NetIPAddress
```
