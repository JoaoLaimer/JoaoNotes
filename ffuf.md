At a minimum we're required to supply two options: `-u` to specify an URL and `-w` to specify a wordlist. The default keyword `FUZZ` is used to tell ffuf where the wordlist entries will be injected. We can append it to the end of the URL like so:

`ffuf -u http://MACHINE_IP/FUZZ -w /usr/share/wordlists/SecLists/Discovery/Web-Content/big.txt`

You could also use any custom keyword instead of `FUZZ`, you just need to define it like this `wordlist.txt:KEYWORD`
 `ffuf -u http://MACHINE_IP/JOAO -w /usr/share/wordlists/SecLists/Discovery/Web-Content/big.txt:JOAO`

You can use the `-e` flag to include extensions when directory fuzzing.
`ffuf -u http://MACHINE_IP/FUZZ -w /usr/share/seclists/Discovery/Web-Content/raft-medium-words-lowercase.txt -e .php,.txt`

By adding `-fc <code-num>`  (filter code) we'll hide from the output all specified HTTP status codes.

Sometimes you might want to filter out multiple status codes such as 500, 302, 301, 401, etc. For instance, if you know you want to see 200 status code responses, you could use `-mc 200` (match code) instead of having a long list of filtered codes.

Filter flags start with 'f' and matching flag start with 'm', most flags have their counterpart.

We can use a regexp to match all files beginning with a dot.
`ffuf -u http://10.201.112.188/FUZZ -w /usr/share/seclists/Discovery/Web-Content/raft-medium-files-lowercase.txt -fr '/\..*'`

## Fuzzing Parameters
`ffuf -u 'http://10.201.93.109/sqli-labs/Less-1/?FUZZ=1' -c -w /usr/share/seclists/Discovery/Web-Content/raft-medium-words-lowercase.txt -fw 39`

Using the wordlist flag like so: `-w -`. You can use the stdin as a wordlist:
`seq 0 255 | ffuf -u 'http://10.201.93.109/sqli-labs/Less-1/?id=FUZZ' -c -w - -fw 33`

## Fuzzing DNS and vhosts

`$ ffuf -u http://FUZZ.mydomain.com -c -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-5000.txt -fs 0   $ ffuf -u http://mydomain.com -c -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-5000.txt -H 'Host: FUZZ.mydomain.com' -fs 0`  

It is possible that you can't find a sub-domain with direct subdomain enumeration (1st command) but that you can find it with vhost enumeration (2nd command).

Vhost enumeration technique shouldn't be discounted as it may lead to discovering content that wasn't meant to be accessed externally.