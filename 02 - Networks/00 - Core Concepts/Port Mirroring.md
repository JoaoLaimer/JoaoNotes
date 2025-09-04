### Traffic Sniffing Using a Switch

A packet analyzer (also known as a packet sniffer or traffic sniffer) is typically software that captures packets entering and exiting the network interface card (NIC). It is not always possible or desirable to have the packet analyzer on the device that is being monitored. Sometimes it is better on a separate station designated to capture the packets.

Because network switches can isolate traffic, traffic sniffers or other network monitors, such as IDS, cannot access all the traffic on a network segment. Port mirroring is a feature that allows a switch to make duplicate copies of traffic passing through a switch, and then send it out a port with a network monitor attached