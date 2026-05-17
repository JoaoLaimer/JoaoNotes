Nuclei is a open-source vulnerability scanner that runs on templates. Templates specify a kind of vulnerability. The template is feed to the Nuclei engine, that it then uses the information contained on it to scan a specified target. Nuclei templates are community managed so new templates are released frequently.

## Installation
```
# With brew
brew install nuclei

# With golang
go install -v github.com/projectdiscovery/nuclei/v2/cmd/nuclei@latest

# Compile from source
git clone https://github.com/projectdiscovery/nuclei.git; \
cd nuclei/v2/cmd/nuclei; \
go build; \
mv nuclei /usr/local/bin/; \
nuclei -version;

# Download compiled release
https://github.com/projectdiscovery/releases

```

## Templates
Nuclei templates are written on `yaml`. Here's a example of a template used to detect workstations.
```yaml 
id: detect-worksites

info:
  name: Worksites.net Service Detection
  author: melbadry9
  severity: info
  description: A worksites.net service was detected.
  reference:
    - https://blog.melbadry9.xyz/dangling-dns/xyz-services/ddns-worksites
  classification:
    cwe-id: CWE-200
  metadata:
    max-request: 1
  tags: dns,service,discovery

dns:
  - name: "{{FQDN}}"
    type: A
    matchers:
      - type: word
        words:
          - "69.164.223.206"
```
Community templates on the official repository are automatically added to `.local/nuclei-templates`.

Here you can find documentation about writing [Nuclei Templates](https://docs.projectdiscovery.io/templates/introduction). 
# Basic Usage
Nuclei can be called using all templetes simply by specifying a single host with:
```bash
nuclei -u <host>
```
To specify a category of templates you can use the `-t` flag, like:
``` shell
# Scan using all DNS templates
nuclei -t dns -u <host>
```
Those templates are in a folder called `dns` inside the `nuclei-templates` directory. To specify another set of templates, use any named folder inside the nuclei templates directory.

### Specify a list of hosts
Using a file with multiple hosts is possible in nuclei.
```shell
nuclei -t dns -list targets.txt
```

# Filters
Filters are separated by commas. Any filter can be included or excluded by prefixing the filter with `i` or `e` respectively.
### Tags
You can use the `-tags` to filter for templetes tagged with a specified tag.
```
nuclei -tags dns,http <host>
```
Excluding tags is also possible with the `-etags`.
Including tags, overrides defaults and configs, `-itags`.

## Others
- `-author`
- `-severity`: low,medium, high and critical
- `-pt`: Filter by protocol type.
## DSL (Domain Specific Language)
Nuclei has its own querying language with DSL, which helps us filter the templates.
```
nuclei -tc "contians(tags,'xss') && contains(author, 'xss_master123')"

nuclei -tc "contians(tags,'xss') || contains(tags, 'cve')"
```
Note: we can run commands without specifying hosts to confirm the usage of our filters.

# Outputing
All information and banners are outputted to STDERR.
All results are outputted to STDOUT.
Also nuclei has its own flag called `-silent` to silence banners and information.

Nuclei also contains a verbose mode.

We can output to JSON using the `-json`
We can output to a file using the `-output`
We can store responses on a directory called output using `-sresp`. If you want to change the directory name use `-srd`.
We can output to Markdown using the `-me` specifying a name for the file.

We can output in SARIF using `-se`.

# Configuration Files
Nuclei configuration files are written in `.yaml`.  The configuration file is used to specify all flags in one file.
```yaml
template-condition:
	- "conatins(tags, 'cve')"
header:
	- "X-Custom-Auth: Bearer super-secrete-token"
follow-redirects: true
max-redirects: 10
verbose: true
store-resp: true
```

```bash
nuclei -config config.yaml -u <host>
```

The default config file can be found on `.config/nuclei/config.yaml` 

