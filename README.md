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

let see the docmention and read about the company we procat

<img width="1858" height="904" alt="{96EA312A-5387-465F-8194-08F6A6EE35BF}" src="https://github.com/user-attachments/assets/5cab45ce-514f-4637-8777-3f2e24e6ddfa" />
here we see the employee name ip and there roll in the comapny


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

next we have this alert 

<img width="1851" height="891" alt="{AF917955-384F-4E59-8964-51B40891CF75}" src="https://github.com/user-attachments/assets/256b556b-b440-4d94-a8ee-415f51ee99e1" />

here as we see here this reguest is comming form amazon.amazon.biz but here is the suspicions thing is that amazon end with .com TLD here the attacker whant the employee to thing that this rguest is comming from amazon and he add urgents to make him like to the link and there is other thing is that amazon will not use links like http://bit.ly/3sHkX3da12340 if its from the realy amazon they mayuse something like check.amazon.com so this is true postitfe

and let write the report
<img width="1849" height="908" alt="{69FC4F19-02DF-4808-8888-5EAA07729970}" src="https://github.com/user-attachments/assets/b57010a2-4e45-4294-8002-f337b061226a" />
it a true postive alert the attacker want the employee to click in the URL using the fear techic and the attacker pretnted to be legitiment website

next alert 
<img width="1851" height="922" alt="{18AA5514-39E1-4FD3-B796-59945434E07B}c" src="https://github.com/user-attachments/assets/7d64122f-1849-41b4-8431-02d772cc2338" />
it seem like the employee click to that malilios URL but fortunatly the firwall blocked that reguest let see what happend in splunk

<img width="1845" height="911" alt="{39C8C39D-CEE5-45F8-BDC5-4E85A500C3F8}ee" src="https://github.com/user-attachments/assets/99c26c2c-f4e6-460e-9cd3-e5c305470a23" />

as we see here the source ip is 10.20.2.17 which is the employee and the destnation ip address is 67.199.248.11
let see the local tryhackme threat intelligent and chek that ip address(even thoue we know from the prives alert that this URL is malilious)

<img width="1855" height="899" alt="{3E12FF05-3697-4C9E-8608-9A2781605A2D}" src="https://github.com/user-attachments/assets/05ee958c-56fa-4bc7-bfbc-9ef6474bc2d3" />
here we see that the threat intelligent classfied this ip as malilious and we know that this URL bit.ly/3sHkX3da12340 is a lso malilious(form the previous alert)
now let start writing report 

<img width="1843" height="910" alt="{9F000C72-CD74-4AC3-AE0E-B8F111FCE2EE}" src="https://github.com/user-attachments/assets/c73188d1-313e-41a3-8a27-f91336e00c0e" />
and we close this alert 
<img width="1846" height="905" alt="{E849A9D8-68D3-46DA-AB24-67F0C91B6D62}phisiong" src="https://github.com/user-attachments/assets/ae6b2a0f-92d9-426d-a146-f7ec377e785c" />
here it is obvious that this alert is Phishing becase here we see a massage from no-reply@m1crosoftsupport.co urge the employee to to scure has Microsoft account
here first we see that this URL m1crosoftsupport is pretnd to be from microsoft the attacker changed the (i) in microsoft to (1) to be m1crosoft
