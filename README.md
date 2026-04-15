# Phishing-Email-Analysis-Using-SOC-Techniques-TryHackMe-Write-Up-

## Objective
The objective of this lab is to develop practical SOC investigation skills by analyzing phishing alerts, classifying them as true or false positives, and leveraging SIEM tools like Splunk alongside threat intelligence platforms such as VirusTotal to validate suspicious indicators and support incident response decisions
### Skills Learned
- Phishing Detection & Analysis
- True Positive vs False Positive Classification
- Log Analysis using Splunk
- Analytical thinking
- Attention to detail

### Tools Used
- Splunk Security Information and Event Management (SIEM) system for log ingestion, correlation, and analysis of security events.
-  VirusTotal Threat intelligence platform for analyzing URLs, domains, and file hashes to identify malicious indicators.

## Steps
To day we will solve Introduction to Phishing lab in TryHackMe

<img width="1850" height="574" alt="{FE2E5405-C96C-4A17-ABE5-44572FDB3360}" src="https://github.com/user-attachments/assets/e7b4c84a-8dec-4aaf-b159-f9cc96689dd9" />
after we start the lab the first thing will see is the Dashbord 

<img width="1846" height="912" alt="{04642EAC-3BC4-4FF4-9673-6A9302541A36}" src="https://github.com/user-attachments/assets/2c1bea0c-26b3-4786-9b6a-05f3633cbe92" />

in the **Alert queue** we see the first alert 
<img width="1856" height="910" alt="{2A030A5A-933E-4006-BF57-F7DA4A0B9307}" src="https://github.com/user-attachments/assets/23a0a8ea-1894-48a8-a790-f2537e9bb975" />

let start invastgion 

so the alert said that there suspicious link which is hrconnex.thm so if we let look to that email and see what is that 

<img width="1851" height="909" alt="{A6A2AEEA-A421-491D-8A89-1D3A8505A5C3}Fals" src="https://github.com/user-attachments/assets/af5bf7cc-3f12-4225-b786-b78fab383390" />


here we that the lsit log is what create the alert then we see that there is malicious link which is https://hrconnex.thm/onboarding/15400654060/j.garcia 
Now if we look to the above log we see that there is a massage come from  h.harris@thetrydaily.thm to  j.carter@thetrydaily.thm said that is websit is **our new third-party HR partner for handling account setup and paperwork** so this mean that hrconnex.them is legitimate wibsite and this alert is false positive 

<img width="1854" height="907" alt="{B7F7C8C1-874F-4409-A9B1-C2B7B553FA38}" src="https://github.com/user-attachments/assets/295dca05-7cec-4a89-a46d-9d6b4139cbce" />

here we write the report as a false positive explaining why it is false positive 

<img width="1844" height="916" alt="{41D011B4-FF59-4102-AEAD-4AD24B30BFF6}" src="https://github.com/user-attachments/assets/5f4c78da-64b6-458f-8d0a-e2dab29fd853" />
next 
<img width="1837" height="898" alt="{D21078C9-7363-459A-8BAE-07EF04A1E8D6}su" src="https://github.com/user-attachments/assets/2ab6e07e-f6be-4a2c-a081-3596f137bd60" />

here we see that there is suspiciios links so lets start invastion by search in splunk for that suspicios link bit.ly
<img width="1847" height="912" alt="{A1637359-4BC8-4860-9463-09E0138F1F7B}sus" src="https://github.com/user-attachments/assets/3ba927f1-6dac-470a-9824-8d1030329103" />

here we sea that the employee whcih is 	h.harris@thetrydaily.thm is clicing in that link and and that regest is blocked by the firewall and the destination is  67.199.248.11

now let check and see if that ip is maliusions by check it in the tryhackme local threat intalligence 


