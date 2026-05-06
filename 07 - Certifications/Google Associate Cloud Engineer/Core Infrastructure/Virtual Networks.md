# Virtual Private Cloud (VPC)
Google Cloud’s networks are global, spanning all available regions across the world.
So, you can have one network that literally exists anywhere in the world - Asia, Europe, Americas - all simultaneously.
Inside a network, you can segregate your resources with regional subnetworks.


Every project is provided with a default VPC network with preset subnets and firewall rules. Specifically, a subnet is allocated for each region with non-overlapping CIDR blocks and firewall rules that allow ingress traffic for ICMP,

In an auto mode network, one subnet from each region is automatically created within it. The default network is actually an auto mode network. These automatically created subnets use a set of predefined IP ranges with a /20 mask that can be expanded to /16. All of these subnets fit within the 10.128.0.0/9 CIDR block.

A custom mode network does not automatically create subnets. This type of network provides you with complete control over its subnets and IP ranges.

Google Cloud now supports IPv6 in a custom VPC network mode, for example you can configure IPv6 addressing on ‘dual-stack’ VM instances running both IPv4 and IPv6.

# IP Addresses for Default Domains
Google publishes the complete list of IP ranges that it announces to the internet in goog.json. Google also publishes a list of Google Cloud customer-usable global and regional external IP addresses ranges in cloud.json.
The following files replace the \_spf.google.com TXT records previously recommended to use for listing Google IP addresses.
- https://www.gstatic.com/ipranges/cloud.json provides a JSON representation of CloudIP addresses organized by region.
-  https://www.gstatic.com/ipranges/cloud_geofeed is a standard geofeed formatted IP geolocation file that we share with 3rd-party IP geo providers like Maxmind, Neustar, and IP2Location.
-  https://www.gstatic.com/ipranges/goog.json and https://www.gstatic.com/ipranges/goog.txt are JSON and TXT formatted files respectively that include Google public prefixes in CIDR notation.
For more information as well as an example of how to use this information, refer to https://cloud.google.com/vpc/docs/configure-private-google-access#ip-addr-defaults

# Pricing

| Traffic type                                                               | Price            |
| -------------------------------------------------------------------------- | ---------------- |
| Ingress                                                                    | No charge        |
| Egress to same zone (internal IP address)                                  | No charge        |
| Egress to Google Products (Youtube, Maps, Drive)                           | No charge        |
| Egree to a different Google Cloud service (within same region; exceptions) | No charge        |
| Egress between zones in the same regions (per GB)                          | $0.01            |
| Egress to the same zone (external IP address, per GB)                      | $0.01            |
| Egress between regions within the US and Canada (per GB)                   | $0.01            |
| Egress between regions, not including traffic between US regions           | Varies by region |
