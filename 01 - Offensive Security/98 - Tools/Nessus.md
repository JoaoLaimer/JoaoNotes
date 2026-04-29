After downloading Nessus, from the Tenable [Download Page](https://www.tenable.com/downloads/nessus?loginAttempted=true) and installing it, we can assess the dashboard from port `8834`.
```
$ sudo systemctl start nessusd.service
```
# Nessus Scan
A new Nessus scan can be configured by clicking `New Scan`, and selecting a scan type. Scan templates fall into three categories: `Discovery`, `Vulnerabilities`, and `Compliance`.
## Advanced Settings
We can configure a number of advanced settings for Nessus and its scans, like scan policies, plugins, and credentials.
## Scan Policies
Nessus gives us the option to create scan policies. Essentially these are customized scans that allow us to define specific scan options, save the policy configuration, and have them available to us under `Scan Templates` when creating a new scan. This gives us the ability to create targeted scans for any number of scenarios, such as a slower, more evasive scan, a web-focused scan, or a scan for a particular client using one or several sets of credentials. Scan policies can be imported from other Nessus scanners or exported to be later imported into another Nessus scanner.

To create a scan policy, we can click on the `New Policy` button in the top right, and we will be presented with the list of pre-configured scans. We can choose a scan, such as the `Basic Network Scan`, then customize it, or we can create our own.

## Nessus Plugins
Nessus works with plugins written in the [Nessus Attack Scripting Language (NASL)](https://en.wikipedia.org/wiki/Nessus_Attack_Scripting_Language) and can target new vulnerabilities and CVEs. These plugins contain information such as the vulnerability name, impact, remediation, and a way to test for the presence of a particular issue.

Plugins are rated by severity level: `Critical`, `High`, `Medium`, `Low`, `Info`.

## Scanning with Credentials
Nessus also supports credentialed scanning and provides a lot of flexibility by supporting LM/NTLM hashes, Kerberos authentication, and password authentication.

# Nessus Scan Output
Nessus gives us the option to export scan results in a variety of report formats as well as the option to export raw Nessus scan results to be imported into other tools, archived, or passed to tools, such as [EyeWitness](https://github.com/FortyNorthSecurity/EyeWitness), which can be used to take screenshots of all web applications identified by Nessus and greatly assist us with working through the results and finding more value in them.

## Nessus Reports
Once a scan is completed we can choose to export a report in `.pdf`, `.html`, or `.csv` formats. The .pdf and .html reports give the option for either an Executive Summary or a custom report.

## Exporting Nessus Scans
Nessus also gives the option to export scans into two formats `Nessus (scan.nessus)` or `Nessus DB (scan.db)`. The `.nessus` file is an `.xml` file and includes a copy of the scan settings and plugin outputs. The `.db` file contains the `.nessus` file and the scan's KB, plugin Audit Trail, and any scan attachments.
Scripts such as the [nessus-report-downloader](https://raw.githubusercontent.com/eelsivart/nessus-report-downloader/master/nessus6-report-downloader.rb) can be used to quickly download scan results in all available formats from the CLI using the Nessus REST AP.

# Mitigating Issues

Some firewalls will cause us to receive scan results showing either all ports open or no ports open. If this happens, a quick fix is often to configure an Advanced Scan and disable the `Ping the remote host` option. This will stop the scan from using ICMP to verify that the host is "live" and instead proceed with the scan. Some firewalls may return an "ICMP Unreachable" message that Nessus will interpret as a live host and provide many false-positive informational findings.

In sensitive networks, we can use rate-limiting to minimize impact. For example, we can adjust `Performance Options` and modify `Max Concurrent Checks Per Host` if the target host is often under heavy load, such as a widely used web application. This will limit the number of plugins used concurrently against the host.

We can avoid scanning legacy systems and choose the option not to scan printers, as we showed in an earlier section. If a host is of particular concern, it should be left out of the target scope or we can use the `nessusd.rules` file to configure Nessus scans. More information about it you can find [here](https://community.tenable.com/s/article/What-is-the-Nessus-rules-file?language=en_US).

Finally, unless specifically requested, we should never perform [Denial of Service checks](https://www.tenable.com/plugins/nessus/families/Denial%20of%20Service). We can ensure that these types of plugins are not used by always enabling the ["safe checks"](https://www.tenable.com/blog/understanding-the-nessus-safe-checks-option) option when performing scans to avoid any network plugins that can have a negative impact on a target, such as crashing a network daemon. Enabling the "safe checks" option does not guarantee that a Nessus vulnerability scan will have zero adverse impact but will significantly minimize potential impact and decrease scanning time.

It is always best to communicate with our clients or internal stakeholders and alert necessary personnel before starting a scan. When the scan is completed, we should keep detailed logs of the scanning activity in case an incident occurs that must be investigated.

## Network Impact
It is also essential to keep in mind the potential impact of vulnerability scanning on a network, especially on low bandwidth or congested links. This can be measured using [vnstat](https://humdi.net/vnstat/).