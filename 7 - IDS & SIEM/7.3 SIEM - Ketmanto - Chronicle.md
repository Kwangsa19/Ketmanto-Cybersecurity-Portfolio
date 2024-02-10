# SIEM - Chronicle
>  SIEM is an application that collects and analyzes log data to monitor critical activities in an organization.

>  Chronicle is a cloud service, built as a specialized layer on top of core Google infrastructure, designed for enterprises to privately retain, analyze, and search the massive amounts of security and network telemetry they generate.

## Overview 

In Chronicle, we can search for events using the Search field. Procedural Filtering applies filters to a search to further refine the search results. For example, you can use Procedural Filtering to include or exclude search results that contain specific information relating to an event type or log source. In addition, YARA-L is the a computer language used to create rules for searching through ingested log data. 
There are two types: Unified Data Mode or Raw Log Search. 
*  Unified Data Mode (UDM) is the default search type used in Chronicle. Through a UDM Search, Chronicle searches security data that has been ingested, parsed, and normalized. This search retrieves results faster than a Raw Log Search due to indexed and structured normalized data in UDM.
*  Raw Log Search will search through the raw, unparsed logs. It searches through raw logs, making it slower than UDM. Here, we can specify the information such as usernames, filenames, hashes, and more. It also supports the use of regular expressions to narrow down the search to match on specific patterns. 

## Scenario 

You are a security analyst at a financial services company. You receive an alert that an employee received a phishing email in their inbox. You review the alert and identify a suspicious domain name contained in the email's body: `signin.office365x24.com`. You need to determine whether any other employees have received phishing emails containing this domain and whether they have visited the domain. You will use [Chronicle](https://demo.backstory.chronicle.security/?warstory=) to investigate this domain.

## Expectation 
* Access threat intelligence reports on the domain
* Identify the assets that accessed the domain
* Evaluate the HTTP events associated with the domain
* Identify which assets submitted login information to the domain
* Identify additional domains

## Step-by-step 

1. Launch Chronicle.
2. Perform a domain search.
* In the search bar, type `signin.office365x24.com` and click Search. Under `DOMAINS`, click signin.office365x24.com to complete the search. Below are the screenshots of the legacy view, VT, and IP address `40.100.174.34`.
    
  * Image 1 Legacy View
    
  ![chrome_QnyIg5thvH](https://github.com/Kwangsa19/Ketmanto-Cybersecurity-Portfolio/assets/135963482/c7f605fc-8796-4d97-948b-e207cbd06f49)

  * Image 2 VT 
  
  ![chrome_u1p0eD2S4u](https://github.com/Kwangsa19/Ketmanto-Cybersecurity-Portfolio/assets/135963482/45c34c3f-21e0-4c19-aa07-1f9569078237)

  * Image 3 IP address `40.100.174.34`
  
  ![chrome_WS7N0VCXT1](https://github.com/Kwangsa19/Ketmanto-Cybersecurity-Portfolio/assets/135963482/93256920-bd8b-4246-b3d6-a876f6df6af9)

  
* Evaluate the search result (Legacy view).
   
  | Observe | Description | Note |
  | :----: | :----: | :----: |
  | VT context | Provides  `VirusTotal` information available for the domain. | Chronicle found 7 security vendors flagged this domain as malicious.  | 
  | WHOIS | Summary of information about the domain using WHOIS which includes domain names, contact information of the domain owner. This may help determining the origin of malicious websites. | Reference time can be found and first/last seen is 7 months ago, as of February 10th, 2024. |
  | Prevalence | A graph which outlines historical prevalence of the domain. | The domain has been accessed on July 9th, 2023 and February 10th, 2024. |
  | Resolved IP | This provides additional context about the domain such as the IP address to `signin.office365x24.com`. This can be helpful for further investigation to determine whether there is a broader compromise. | We found 2 IP addresses that map to `signin.office365x24.com`: `104.215.148.63` & `40.100.174.34`. |
  | Sibling Domains | This provides additional context about the domain, such as the top or parent domain. | We found one sibling domain: `login.office365x24.com`.
  | ET Intelligence Rep List | This includes additional context on the domain, such as known threats using ProofPoint's Emerging Threats (ET) Intelligence Rep List | Category: Drop site for logs or stolen credentials. Confidence (Min: 20, Max 127): 22, Severity: Medium, Active from: 2018-12-31 T00:00:00Z, Active until: 2019-0-8T00:00:00Z. More information can be found [here](https://tools.emergingthreats.net/docs/ET%20Intelligence%20Rep%20List%20Tech%20Description.pdf).|
  | Timeline | This provides information about the events and interactions made with the domain. | It reveals the details about the HTTP requests made including `GET` and `POST`. `GET` retrieves the data from a server while a `POST` request submits data to a server`.|
  | ASSETS | This provides a list of the assets that have been assessed the domain. | There are 6 assets that have accessed the domain. |

3. Launch an Investigation. 
  * According to ET Intelligence Rep List, `signin.office365x24.com` is categorized as "Drop site for logs or stolen credentials".
  * The following assets are those who accessed the domain:
      * `ashton-davidson-pc`
      * `bruce-monroe-pc`
      * `coral-alvarez-pc`
      * `emil-palmer-pc`
      * `jude-reyes-pc`
      * `roger-spence-pc`
  * We found 2 IP addresses that map to `signin.office365x24.com`: `104.215.148.63` & `40.100.174.34`.
  * The IP address `40.100.174.34` resolves to `signin.office365x24.com` and `signin.accounts-google.com`.
  * As we can see from image 2 above, there are three `POST` requets made to `40.100.174.34`.
  * Some `POST` requests were made to `signin.office365x24.com`. Their target URL of the web page were sent to `http://signin.office365x24.com/login.php`. 
