# Final Report

## Scenario 

The organization experienced a security incident on January 22, 2024, at 7:20 p.m., PT, during which an individual was able to gain unauthorized access to customer personal identifiable information (PII) and financial information. Approximately 50,000 customer records were affected. The financial impact of the incident is estimated to be $100,000 in direct costs and potential loss of revenue. The incident is now closed and a thorough investigation has been conducted. At approximately 3:13 p.m., PT, on January 20, 2024, an employee received an email from an external email address. The email sender claimed that they had successfully stolen customer data. In exchange for not releasing the data to public forums, the sender requested a $25,000 cryptocurrency payment. The employee assumed the email was spam and deleted it. On January 22, 2024, the same employee received another email from the same sender. This email included a sample of the stolen customer data and an increased payment demand of $50,000. On the same day, the employee notified the security team, who began their investigation into the incident. After a thorough review, the security team found there is a vulnerability in the e-commerce web application. This vulnerability allowed the attacker to perform a forced browsing attack and access customer transaction data by modifying the order number included in the URL string of a purchase confirmation page. The organization collaborated with the public relations department to disclose the data breach and offered free identity protection services to those affected customers. The lesson learned from this incident is performing routine vulnerability scans and penetration testing. The one log that the investigation found is the information of thousands of purchase confirmation pages. In addition, the organization may implement a control mechanism to allow a specific set of URLs to block all requests outside of the URL range and ensure that only authenticated users are authorized to gain access.

## Executive Summary 
> A high-level summary of the report including the key findings and essential facts related to the incident.

The type of security incident is data theft. The incident took place on January 22, 2024 at 7:20 pm, during which an individual gained unauthorized access to customer personal identifiable information and financial information. The attacker used forced browsing to exploit the e-commerce web application vulnerability. Approximately 50,000 customers records were affected and the financial loss is estimated to be $100,000. The incident is now closed and investigation has been conducted. The recommendation to prevent the future recurrences are: 
* Implement access control mechanisms.
* Implement routine vulnerability scans.

## Timeline 
>  A detailed chronological timeline of the incident that includes timestamps dating the sequence of events that led to the incident.

At 3:13 pm, on January 20, 2024, an employee received an email from an external email address. The email claimed that they had successfully stolen customer data. They requested a $25,000 cryptocurrency payment. The employee assumed it was spam and deleted it.
On January 22, 2024, the same employee received another email from the same sender. This time, the attacker attached a sample of the stolen data and demanded $50,000. On the same day, the employee notified the security team, and the security team is conducting the investigation.

## Investigation 
>  A compilation of the actions taken during the detection and analysis of the incident. For example, analysis of a network artifact such as a packet capture reveals information about what activities happen on a network.

* The root cause of the incident was identified as a vulnerability in the e-commerce web application. This vulnerability allowed the attacker to perform a forced browsing attack and access customer transaction data by modifying the order number included in the URL string of a purchase confirmation page. This vulnerability allowed the attacker to access customer purchase confirmation pages, exposing customer data, which the attacker then collected and exfiltrated.
* After confirming the web application vulnerability, the security team analyzed the web application access logs. The logs indicated that the attacker accessed the information of thousands of purchase confirmation pages.

## Response and Remediation
> Proposed solutions. 

The organization collaborated with the public department to disclose the data breach to its customers and offered free identity protection services to customers affected by the incident. 

## Recommendations 
> A list of suggested actions for future prevention.
* Perform routine vulnerability scans and penetration testing.
* Implement the following access control mechanisms:
  * Implement allowlisting to allow access to a specified set of URLs and automatically block all requests outside of this URL range.
  * Ensure that only authenticated users are authorized access to content.
