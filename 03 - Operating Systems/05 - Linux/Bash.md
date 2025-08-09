Shebang line: `#!/bin/bash`
Command line parameters are used using $1 $2 $3 $n... where 1 is the first argument after the command name, for example
```bash
#!/bin/bash
/usr/bin/cat $1
```
`./othercat file.txt

`$@` is the array containing all input arguments.
`$#` is the number of elements of arguments.

### Output Redirection
`PROGRAM > FILENAME` Writes the program's output into the file with that name ( or creates it).
`PROGRAM >> FILENAME` Appends the output of the program to the end of the file. 
`PROGRAM < FILENAME` Uses the contents of the file as input to the program
`PROGRAM1 | PROGRAM 2` Known as pipe, uses the output of P1 as input of P2.

### Variables
To declare variables we use the following syntax: VARIABLE_NAME=VARIABLE_VALUE
The syntax for referencing variables is $VARIABLE_NAME.
We may use ${VARIABLE_NAME}STRING to append the content of the variable to a string.

### Using other commands
Let's say we want the current time in our script. To do so we can declare a variable to hold the date for us.
`DATE=$(date)`
This will execute the command `date` and store it's output to the variable DATE.

## Conditions
If clauses are declared like:
```bash
if [condition 1]
then
#code block
elif [condition 2]
then
#code block
else
#code block
fi #closes the if clause
```

Switch clause is also available on bash scripting as case:
```bash
case $VAR in
	case1)
	#Code
	;;
	case2)
	#code
	;;
	*)
	#Default code
	;;
esac #closes the case clause
```

### Functions 
To declare a function on bash we can do so as:
```bash
FUNCTION_NAME()
{
#Code block
}
```

### Array
To create an array we can declare like:
```bash
my_array=(arr1 arr2 arr3)

# Accessing the elements
${my_array[index]}
${my_array[*]} # all elements
${my_array[@]} # all elements
${!my_array[@]} # all indexes 

# Apending
my_array+=(arr4)

# Deleting element
unset my_array[index]

# Subset
${my_array:START_INDEX:END_INDEX}

```

### Loop
There is two kinds of loops on bash scripting, the for loop and while loop.
the for loop is as follows:
```bash
#!/bin/bash     
for i in $ARRAY  
do  
       #block
done
```
And the while loop:

### Options
Using the `getopts OPTSTRING NAME` we can parse options from the command line by using single-character flags.
Where  `OPTSTRING` specifies the options letters that getopts should recognize and `OPTIND` is the starting index position of the flag.
```bash
#!/bin/bash  
  
getopts "m" OPTION  
  
for i in "${@:OPTIND:$#}"  
do  
       echo $i  
done
```
