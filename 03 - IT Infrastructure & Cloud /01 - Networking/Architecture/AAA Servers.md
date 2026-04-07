#### Authentication
- Users and administrators must prove that they are who they say they are.
- Authentication can be established using username and password combinations, challenge and response questions, token cards, and other methods.
- AAA authentication provides a centralized way to control access to the network.
#### Authorization
- After the user is authenticated, authorization services determine which resources the user can access and which operations the user is allowed to perform.
- An example is “User ‘student’ can access host serverXYZ using SSH only.”
#### Accounting
- Accounting records what the user does, including what is accessed, the amount of time the resource is accessed, and any changes that were made.
- Accounting keeps track of how network resources are used.
- An example is “User ‘student’ accessed host serverXYZ using SSH for 15 minutes.”


Terminal Access Controller Access-Control System Plus (TACACS+) and Remote Authentication Dial-In User Service (RADIUS) are both authentication protocols that are used to communicate with AAA servers. Whether TACACS+ or RADIUS is selected depends on the needs of the organization.

While both protocols can be used to communicate between a router and AAA servers, TACACS+ is considered the more secure protocol. This is because all TACACS+ protocol exchanges are encrypted, while RADIUS only encrypts the user’s password. RADIUS does not encrypt usernames, accounting information, or any other information carried in the RADIUS message.

|                 | TACACS+                                                                                                    | RADIUS                                                                                                                        |
| --------------- | ---------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| Functionality   | Separates AAA according to the AAA architecture, allowing modularity of the security server implementation | Combines  authentication and authorization but separates accounting, allowing less flexibility in implementation than TACACS+ |
| Standard        | Mostly CISCO supported                                                                                     | Open/RFC standard                                                                                                             |
| Transport       | TCP                                                                                                        | UDP                                                                                                                           |
| Protocol CHAP   | Bidirectional challenge and response as used in Challenge Handshake Authentication Protocol (CHAP)         | Unidirectional challenge and response from RADIUS security server to the RADIUS client.                                       |
| Confidentiality | Entire packet encrypted                                                                                    | Passwod encrypted                                                                                                             |
| Customization   | Provides authorization of router commands on a per-user or per-group basis                                 | Has no option to authorize router commands on a per-user or per-group basis                                                   |
| Accounting      | Limited                                                                                                    | Extensive                                                                                                                     |

