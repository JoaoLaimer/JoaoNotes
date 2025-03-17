Yara can identify information based on both binary and textual patterns. Rules are used to label these patterns.

- **Rules**
Using rules: 
```bash
yara myrule.yar somedirectory
```

Creating Rules: 
```yara
rule example {
	condition: true
}
```

	Meta: description of the yara rule
	Strings: Search for strings 
```yara
rule helloworld_checker{
	strings:
		$hello_world = "Hello World!"
	condition:
		$hello_world
}
```

```yara
rule helloworld_checker{
	strings:
		$hello_world = "Hello World!"
		$hello_world_lowercase = "hello world"
		$hello_world_uppercase = "HELLO WORLD"

	condition:
		any of them
}
```

	Conditions:
		

| Op  | Key |
| --- | --- |
| >=  | And |
| <=  | Or  |
| !=  | Not |

```yara
rule helloworld_checker{
	strings:
		$hello_world = "Hello World!"
	condition:
		#hello_world >= 10 and filesize >= 10KB
}
```
![[Yara Rules CheatSheet.png]]
-**Tools**
LOKI: free open-source Indicator of Compromise(IOC) scanner.
Based on the GitHub page, detection is based on 4 methods:

1. File Name IOC Check
2. Yara Rule Check **(we are here)**
3. Hash Check
4. C2 Back Connect Check
THOR: multi-platform IOC and YARA scanner. Can scan throttle to limit CPU usage. Note that THOR is geared towards corporate customers.
FENRIR: Just like the other two but is a bash script and slightly updated.
YAYA: Based on their website, "_YAYA is a new open-source tool to help researchers manage multiple YARA rule repositories. YAYA starts by importing a set of high-quality YARA rules and then lets researchers add their own rules, disable specific rulesets, and run scans of files._"


**USING LOKI**
```bash
python loki.py -h
```
Scanning a file:
```bash
python loki.py -p <file>
```

**Creating rules with yarGen**
```bash
python3 yarGen.py --update
```
This will update the good-opcodes and good-strings DB's from the online repository. This update will take a few minutes. 
To use yarGen to generate a Yara rule for file 2, you can run the following command:

```bash
python3 yarGen.py -m /home/cmnatic/suspicious-files/file2 --excludegood -o /home/cmnatic/suspicious-files/file2.yar
```
A brief explanation of the parameters above:

- `-m` is the path to the files you want to generate rules for
- `--excludegood` force to exclude all goodware strings (_these are strings found in legitimate software and can increase false positives_)
- `-o` location & name you want to output the Yara rule