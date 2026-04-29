[OpenVAS](https://openvas.org/), by Greenbone Networks, is a publicly available vulnerability scanner. Greenbone Networks has an entire Vulnerability Manager, part of which is the OpenVAS scanner. Greenbone's Vulnerability Manager is also open to the public and free to use. OpenVAS has the capabilities to perform network scans, including authenticated and unauthenticated testing.
## Installing Package
```
$ sudo apt-get update && apt-get -y full-upgrade
$ sudo apt-get install gvm && openvas
$ gvm-setup
```
## Starting OpenVas
```
$ gvm-start
```
# OpenVAS Scan
If you navigate to the `Scans` tab shown below, you will see the scans that have run in the past. You will also be able to see how to create a new task to run a scan. The tasks work off of the scanning configurations that the user sets up.

## Configuration
Before setting up any scans, it is best to configure the targets for the scan. If you navigate to the `Configurations` tab and select `Targets`, you will see targets that have been already added to the application.

## Setting Up a Scan
Multiple scan configurations leverage OpenVAS Network Vulnerability Test (NVT) Families, which consist of many different categories of vulnerabilities, such as ones for Windows, Linux, Web Applications, etc.
OpenVAS has various scan configurations to choose from for scanning a network. We recommend only leveraging the ones below, as other options could cause system disruptions on a network:

- `Base`: This scan configuration is meant to enumerate information about the host's status and operating system information. This scan configuration does not check for vulnerabilities.
- `Discovery`: This scan configuration is meant to enumerate information about the system. The configuration identifies the host's services, hardware, accessible ports, and software being used on the system. This scan configuration also does not check for vulnerabilities.
- `Host Discovery`: This scan configuration solely tests whether the host is alive and determines what devices are `active` on the network. This scan configuration does not check for vulnerabilities as well. _OpenVAS leverages ping to identify if the host is alive._
- `System Discovery`: This scan enumerates the target host further than the 'Discovery Scan' and attempts to identify the operating system and hardware associated with the host.
- `Full and fast`: This configuration is recommended by OpenVAS as the safest option and leverages intelligence to use the best NVT checks for the host(s) based on the accessible ports.
# Exporting The Results
OpenVAS provides the scan results in a report that can be accessed when you are on the `Scans` page. Once you click the report, you can view the scan results and operating system information, open ports, services, etc., in other tabs in the scan report.
# Exporting Formats
There are various export formats for reporting purposes, including XML, CSV, PDF, ITG, and TXT. If you choose to export your report out as an XML, you can leverage various XML parsers to view the data in an easier to read format.
We will export our results in XML and use the [openvasreporting](https://github.com/TheGroundZero/openvasreporting) tool by the TheGroundZero.

```
$ python3 -m openvasreporting -i report-2bf466b5-627d-4659-bea6-1758b43235b1.xml -f xlsx
```
