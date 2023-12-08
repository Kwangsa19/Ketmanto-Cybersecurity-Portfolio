# Cybersecurity Incident Report: Analyze Network Layer Communication

Please enroll to the Google Cybersecurity [course](https://www.coursera.org/learn/networks-and-network-security?specialization=google-cybersecurity) on Coursera to view other attachments to solve this task. I only uploaded my answer to it. 

## Identify the type of attack that may have caused this network interruption 

One potential explanation for the website's connection timeout error message is: DOS attack. <br>
The logs show that: Web server stops responding after receiving so many SYN packet requests. <br>
This event could be: Syn flood attack.

## Part 2: Explain how the attack is causing the website malfunction 
When website visitors try to establish a connection with the web server, a three-way handshake occurs using the TCP protocol. Explain the three steps of the handshake: 

| Step | Description |
|---|---|
| 1 | `SYN` : Client sends SYN packet to the server, requesting a connection. |
| 2 | `SYN/ACK` : Server responds with SYN/ACK packet, acknowledging the client's SYN and requesting confirmation of the connection. |
| 3 | `ACK` : Client sends ACK packet to the server, acknowledging the server's SYN/ACK. |

Explain what happens when a malicious actor sends a large number of SYN packets all at once: It slows down the traffic to the point where such request will fail to be executed. It overwhelms the server’s available resources to reserve for the connection. When this happens, there are no server resources left for legitimate TCP connection requests. <br>
Explain what the logs indicate and how that affects the server: The server has become overloaded and unable to receive any more visitors. In addition, those new visitors will receive a connection timeout message. 

