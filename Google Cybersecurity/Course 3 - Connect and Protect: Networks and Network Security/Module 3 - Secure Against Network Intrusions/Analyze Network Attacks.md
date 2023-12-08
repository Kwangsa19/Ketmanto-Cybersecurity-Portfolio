## Cybersecurity Incident Report: Analyze Network Layer Communication

Please enroll to the Google Cybersecurity [course](https://www.coursera.org/learn/networks-and-network-security?specialization=google-cybersecurity) on Coursera to view other attachments to solve this task. I only uploaded my answer to it. 
| Part 1: Provide a summary of the problem found in the DNS and ICMP traffic log |
| ----------- |
| DNS server is down as a result of port 53 being unreachable. The ICMP request packet indicates that the packet has not been delivered to the port of DNS server successfully. 
As we know, Port 53 is commonly used for DNS. That being said, the most likely issue is the DNS is not responding and it can be caused by DDOS attack against the DNS server.
The UDP protocol reveals that:  DNS is not responding. 
This is based on the results of the network analysis, which show that the ICMP echo reply returned the error message: at port 53 , UDP port 53 unreachable
The port noted in the error message is used for: DNS Server
The most likely issue is: DNS server is not responding. |

| Part 2: Explain your analysis of the data and provide at least one cause of the incident. |
| ----------- |
| Time incident occurred: 1.23pm 
Explain how the IT team became aware of the incident: The customer reported to the company that they were unable to gain access to the company’s website. It was then reported that the message on the web page is “port unreachable”. 
Explain the actions taken by the IT department to investigate the incident:
Security engineers had a look on the webpage and received an error “port being unreachable”. The team used TCPdump (network analyzer) to see the network traffic surrounding the website.
Note key findings of the IT department's investigation (i.e., details related to the port affected, DNS server, etc.): 
Go to website then load the webpage while monitoring the networks via TCPdump. It received lots of traffic. Sent UDP packets and received ICMP response to return to the host that indicates port 53 unreachable. 
Note a likely cause of the incident:
Determine whether port 53 is working or not. IF it’s fine, then check firewall. 
-Firewall: The ability to block network traffic on specific ports. Port blocking can be used to stop or prevent an attack.
-DOS: There could be flood of information being sent to the network device to make it crash or unable to function. The hacker could disable dns server using DOS attack. Or someone within the organization might have disabled port 53 on firewalls. |

