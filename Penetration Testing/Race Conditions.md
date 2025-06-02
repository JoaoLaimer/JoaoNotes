You call a restaurant to reserve a table for a crucial business lunch. One particular table, number 17, is your preferred choice. You call to make a reservation for Table 17; the host confirms it is free as no “Reserved” tag is placed on it. At the same time, another customer is talking with another host and making a reservation for the same table.Who really reserved the table? That’s a race condition.

## Burp Suite: Repeater
In the **Repeater** tab:
1. Click on the `+` icon next to the received request tab and select **Create tab group**.
2. Assign a group name, and include the tab of the request you just sent to the importer before clicking **Create**.
3. Right-click on the request tab and choose **Duplicate tab** (If this option is not available in your version, you can press **CTRL**+**R** multiple times instead)
4. As a starting point.
5. Next to the Send button, the arrow pointed downwards will bring a menu to decide how you want to send the duplicated requests.
## Sending Request Group in Sequence

Sending the group in sequence provides two options:

- Send group in sequence (**single connection**)
- Send group in sequence (**separate connections**)

**Send Group in Sequence over a Single Connection**
This option establishes a single connection to the server and sends all the requests in the group’s tabs before closing the connection. This can be useful for testing for potential client-side desync vulnerabilities.

**Send Group in Sequence over Separate Connections**
As the name suggests, this option establishes a TCP connection, sends a request from the group, and closes the TCP connection before repeating the process for the subsequent request.
## Send Request Group in Parallel

Choosing to send the group’s requests in parallel would trigger the Repeater to send all the requests in the group at once.
According to [Sending Grouped HTTP Requests](https://portswigger.net/burp/documentation/desktop/tools/repeater/send-group) documentation, when sending in parallel, Repeater implements different techniques to synchronize the requests’ arrival at the target, i.e., they arrive within a short time frame. The synchronization technique depends on the HTTP protocol being used:

- In the case of HTTP/2+, the Repeater tries to send the whole group in a single packet. In other words, a single TCP packet would carry multiple requests.
- In the case of HTTP/1, the Repeater resorts to last-byte synchronization. This trick is achieved by withholding the last byte from each request. Only once all packets are sent without the last-byte are the last-byte of all the requests sent. The screenshot below shows our `POST` request sent over two packets.