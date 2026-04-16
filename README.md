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
Today, we will solve the Introduction to Phishing lab on TryHackMe.
<img width="1850" height="574" alt="{FE2E5405-C96C-4A17-ABE5-44572FDB3360}" src="https://github.com/user-attachments/assets/e7b4c84a-8dec-4aaf-b159-f9cc96689dd9" />

After starting the lab, the first thing we see is the dashboard.
<img width="1846" height="912" alt="{04642EAC-3BC4-4FF4-9673-6A9302541A36}" src="https://github.com/user-attachments/assets/2c1bea0c-26b3-4786-9b6a-05f3633cbe92" />

Next, let’s open the documentation and read about the company we are protecting.
<img width="1858" height="904" alt="{96EA312A-5387-465F-8194-08F6A6EE35BF}" src="https://github.com/user-attachments/assets/5cab45ce-514f-4637-8777-3f2e24e6ddfa" />
Here, we can see employee names, IP addresses, and their roles in the company.


In the Alert Queue, we see the first alert.

<img width="1856" height="910" alt="{2A030A5A-933E-4006-BF57-F7DA4A0B9307}" src="https://github.com/user-attachments/assets/23a0a8ea-1894-48a8-a790-f2537e9bb975" />

Let’s start the investigation.

The alert says there is a suspicious link: hrconnex.thm. So, let’s open the splunk and check it by search for hrconnex.thm.
<img width="1851" height="909" alt="{A6A2AEEA-A421-491D-8A89-1D3A8505A5C3}Fals" src="https://github.com/user-attachments/assets/af5bf7cc-3f12-4225-b786-b78fab383390" />


From the logs in Splunk, we see that the alert was triggered by a second log.

Looking at the first log in Splunk, we notice that the sender is h.harris@thetrydaily.thm and the recipient is j.carter@thetrydaily.thm. This means the traffic is internal (both users are from the same company).

Now, if we look at the content field, we see a message saying that this website is “our new third-party HR partner for handling account setup and paperwork.”

This tells us that hrconnex.thm is a legitimate website.

Therefore, this alert is a false positive.

<img width="1854" height="907" alt="{B7F7C8C1-874F-4409-A9B1-C2B7B553FA38}" src="https://github.com/user-attachments/assets/295dca05-7cec-4a89-a46d-9d6b4139cbce" />

Now, we write a report explaining why it is a false positive.
<img width="1844" height="916" alt="{41D011B4-FF59-4102-AEAD-4AD24B30BFF6}" src="https://github.com/user-attachments/assets/5f4c78da-64b6-458f-8d0a-e2dab29fd853" />

Second Alert
<img width="1851" height="891" alt="{AF917955-384F-4E59-8964-51B40891CF75}" src="https://github.com/user-attachments/assets/256b556b-b440-4d94-a8ee-415f51ee99e1" />
This request is coming from argents@amazon.biz. The suspicious part is that Amazon usually uses the .com domain, not .biz.
The attacker is trying to trick the employee into thinking the email is from Amazon. They also create urgency to make the user click the link.
Another red flag is the shortened URL: http://bit.ly/...
Legitimate companies like Amazon usually use their own domains, such as check.amazon.com.

and let write the report
<img width="1849" height="908" alt="{69FC4F19-02DF-4808-8888-5EAA07729970}" src="https://github.com/user-attachments/assets/b57010a2-4e45-4294-8002-f337b061226a" />

We write the report explaining that:
- The attacker used a fake domain
- They created urgency
- They used a suspicious shortened link

Third Alert

<img width="1851" height="922" alt="{18AA5514-39E1-4FD3-B796-59945434E07B}c" src="https://github.com/user-attachments/assets/7d64122f-1849-41b4-8431-02d772cc2338" />
In the next alert, it looks like the employee clicked the malicious URL from the previous alert. Fortunately, the firewall blocked the request.
Let’s check Splunk to see what happened.
<img width="1845" height="911" alt="{39C8C39D-CEE5-45F8-BDC5-4E85A500C3F8}ee" src="https://github.com/user-attachments/assets/99c26c2c-f4e6-460e-9cd3-e5c305470a23" />

As we can see, the source IP is 10.20.2.17, which belongs to the employee’s machine. The destination IP is 67.199.248.11.

Now, let’s check the local TryHackMe Threat Intelligence to verify this IP address (even though we already know from the previous alert that the URL bit.ly/3sHkX3da12340 is malicious).

<img width="1855" height="899" alt="{3E12FF05-3697-4C9E-8608-9A2781605A2D}" src="https://github.com/user-attachments/assets/05ee958c-56fa-4bc7-bfbc-9ef6474bc2d3" />
Here, we see that the Threat Intelligence system has classified the IP address 67.199.248.11 as malicious.
We also know from the previous alert that the URL bit.ly/3sHkX3da12340 is malicious.
So, we write a report and close the alert.

<img width="1843" height="910" alt="{9F000C72-CD74-4AC3-AE0E-B8F111FCE2EE}" src="https://github.com/user-attachments/assets/c73188d1-313e-41a3-8a27-f91336e00c0e" />

Final Alert

<img width="1846" height="905" alt="{E849A9D8-68D3-46DA-AB24-67F0C91B6D62}phisiong" src="https://github.com/user-attachments/assets/ae6b2a0f-92d9-426d-a146-f7ec377e785c" />
It is clear that this alert is a phishing attack.
We can see a message from no-reply@m1crosoftsupport.co urging the employee to secure their Microsoft account.
The first suspicious sign is the domain m1crosoftsupport. The attacker is pretending to be Microsoft by replacing the letter “i” with the number “1” (m1crosoft).
Now, let’s check Splunk to see if other employees received the same email.we search in splunk for "m1crosoftsupport*"
<img width="1851" height="866" alt="{6BFA5F8D-7D75-42C6-BAC5-C02D99B8A099}efd" src="https://github.com/user-attachments/assets/35d23589-4f9c-45aa-acc4-9b45b9484f20" />
Here we can see in (1) the alert that appears in the Alert Queue. We also notice something interesting in (2): the same employee visited the website https://m1crosoftsupport.co/login.

So, let’s write the report for this alert.

<img width="1901" height="902" alt="{D53FEDFF-E56C-41B6-85F5-6BB425C22005}" src="https://github.com/user-attachments/assets/e71d7874-1c31-48b1-9956-b242b375737a" />

We successfully finished the lab.
<img width="1896" height="918" alt="{798E6D48-A6FD-4128-B98F-AB108F244306}" src="https://github.com/user-attachments/assets/d4e21732-3400-4655-a987-57c25ea488cb" />

<img width="1753" height="911" alt="{B6A1691F-1FF2-4221-A7AC-2439FAA387AD}" src="https://github.com/user-attachments/assets/96cf358c-2ab5-4340-8412-ed9cfb1f38bb" />

### Area to improve:
Improving report writing skills
