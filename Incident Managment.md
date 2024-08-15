<span style="font-family: Roboto, Nunito, -apple-system, BlinkMacSystemFont, Segoe UI, Oxygen, Ubuntu, Cantarell, Fira Sans, Droid Sans, Helvetica Neue, sans-serif; color: rgb(235, 237, 242); font-size: 14px">The National Cyber Security Centre (NCSC) defines a cyber incident as a breach of a system's security policy in order to affect its integrity or availability and/or the unauthorized access or attempted access to a system or systems; in line with the Computer Misuse Act.</span>

<span style="font-family: Roboto, Nunito, -apple-system, BlinkMacSystemFont, Segoe UI, Oxygen, Ubuntu, Cantarell, Fira Sans, Droid Sans, Helvetica Neue, sans-serif; color: rgb(235, 237, 242); font-size: 14px">Since you will encounter these concepts frequently during your education and your daily work routine, we recommend that you understand these concepts thoroughly:</span>

- Alert
- Event
- Incident
- True Positive
- False Positive

<span style="font-family: Roboto, Nunito, -apple-system, BlinkMacSystemFont, Segoe UI, Oxygen, Ubuntu, Cantarell, Fira Sans, Droid Sans, Helvetica Neue, sans-serif; color: rgb(235, 237, 242); font-size: 14px">in SIEM, as seen in the image below. Then, we start the analysis process by sending the generated alarms to the Incident Management System.</span>

![](https://ld-images-2.s3.us-east-2.amazonaws.com/Incident+Management+101/images/siem-alert.png)**Event**\
<span style="font-family: Roboto, Nunito, -apple-system, BlinkMacSystemFont, Segoe UI, Oxygen, Ubuntu, Cantarell, Fira Sans, Droid Sans, Helvetica Neue, sans-serif; color: rgb(235, 237, 242); font-size: 14px">An event is any observable occurrence in a system or network. Simply, events are activities like a user connecting to a file share, a server receiving a request for a Web page, a user sending electronic mail (e-mail), a firewall blocking a connection attempt, etc.</span>

**Incident**\
<span style="font-family: Roboto, Nunito, -apple-system, BlinkMacSystemFont, Segoe UI, Oxygen, Ubuntu, Cantarell, Fira Sans, Droid Sans, Helvetica Neue, sans-serif; color: rgb(235, 237, 242); font-size: 14px">The definition of a computer security incident has evolved over time. In the past, a computer security incident was thought of as a security-related adverse event in which there was a loss of data confidentiality, disruption of data or system integrity, or disruption or denial of availability.</span>

**True Positive Alert**\
<span style="font-family: Roboto, Nunito, -apple-system, BlinkMacSystemFont, Segoe UI, Oxygen, Ubuntu, Cantarell, Fira Sans, Droid Sans, Helvetica Neue, sans-serif; color: rgb(235, 237, 242); font-size: 14px">If the situation to be detected and the detected (triggered alert) situation are the same, it is a True Positive alert.</span>

**False Positive Alert**\
<span style="font-family: Roboto, Nunito, -apple-system, BlinkMacSystemFont, Segoe UI, Oxygen, Ubuntu, Cantarell, Fira Sans, Droid Sans, Helvetica Neue, sans-serif; color: rgb(235, 237, 242); font-size: 14px">In short, it is a false alarm. For example, there is a security camera in your house and if the camera alerts you due to your cat's movements, it is a false positive alert.</span>

![](https://ld-images-2.s3.us-east-2.amazonaws.com/Incident+Management+101/images/false-positive-true-positive.png)### **Incident Management Systems (IMS)**

Incident Management Systems is where SOC teams conduct the investigation process and record the actions taken when an incident occurs. For this reason, SOC analysts spend a significant part of their time at the interface of these systems.

**How Incident Management Systems (IMS) Works?**\
<span style="font-family: Roboto, Nunito, -apple-system, BlinkMacSystemFont, Segoe UI, Oxygen, Ubuntu, Cantarell, Fira Sans, Droid Sans, Helvetica Neue, sans-serif; color: rgb(235, 237, 242); font-size: 12px">In order to open a record on the Incident Management platform, a data entry must first be provided here. This data can directly come from the SIEM or from other security products. After the data flow is established, a ticket/case is created on the Incident Management System.</span>

<span style="font-family: Roboto, Nunito, -apple-system, BlinkMacSystemFont, Segoe UI, Oxygen, Ubuntu, Cantarell, Fira Sans, Droid Sans, Helvetica Neue, sans-serif; color: rgb(235, 237, 242); font-size: 12px">Alert details from SIEM are transmitted to the Incident Management System and the Incident Management System works in coordination with the Threat Intelligence and SOAR platforms to process all the data and a new case/ticket is created. Thanks to Threat Intelligence and SOAR integrations on IMS, data enrichment and various actions are provided. Finally, the alert is closed when the operations are complete.</span>

### **Case/Alert Naming**

It is important that the ticket/case/records created in the Incident management system have meaningful title as having unified naming conventions will help in the retrospective inquiries for quickly finding the relevant record or extracting statistics easily when an investigation is made

EventID: {Alert ID Number} - \[{Alert Name}\]

![siem alert naming](https://ld-images-2.s3.us-east-2.amazonaws.com/Incident+Management+101/images/alert-naming-siem.png)<span style="font-family: Roboto, Nunito, -apple-system, BlinkMacSystemFont, Segoe UI, Oxygen, Ubuntu, Cantarell, Fira Sans, Droid Sans, Helvetica Neue, sans-serif; color: rgb(235, 237, 242); font-size: 16px">sometimes the following fields may be included in the title:</span>

- Alert Category
- Event Source
- Description

### **Playbooks**

There are many different types of alerts (web attacks, ransomware, malware, phishing, etc.) in the SOC environment. The methods and approaches of investigating these alerts are different from each other. The workflows prepared for effective and consistent analysis of alerts created on SIEM or a different security tool are called playbooks.

**Why is Playbook Important?**\
<span style="font-family: Roboto, Nunito, -apple-system, BlinkMacSystemFont, Segoe UI, Oxygen, Ubuntu, Cantarell, Fira Sans, Droid Sans, Helvetica Neue, sans-serif; color: rgb(235, 237, 242)">As SOC analysts, we may not always know exactly what to do when handling alerts. We can carry out the investigation process step by step, thanks to the instructions in the Playbook. Playbooks will provide guidance, especially to analysts who have just started their careers in the SOC field.</span>

### **What Does the SOC Analyst Do When An Alert Occurs?**

As a SOC Analyst, your main task is to detect threats to your organization. You usually do this task by analyzing the alerts created in SIEM or a different environment.

<span style="font-family: Roboto, Nunito, -apple-system, BlinkMacSystemFont, Segoe UI, Oxygen, Ubuntu, Cantarell, Fira Sans, Droid Sans, Helvetica Neue, sans-serif; color: rgb(235, 237, 242)">The alerts that occur do not always indicate an actual incident. Sometimes you will encounter false positive alerts. In fact, you will spend most of your time dealing with the false positives, so you need to be in constant communication with the team that creates the SIEM rules and give them feedback all the time. As a SOC Analyst, you need to dig into the details to understand whether an alert is a false positive.</span>