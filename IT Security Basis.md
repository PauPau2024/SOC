### **Introduction to IT Security Basis for Corporates**

- Inventory
- Backups
- Phishing Prevention
- Internet Browsing Protection
- Patching
- Access Control
- Risk Analysis
- Network
- Incident Response for IT Security

### **Inventory**

Protecting your infrastructure requires knowing what devices are connected to your network, what applications are being used, who has access to them, and what security measures are in place.

## **\
What should your inventory contain and why?**

- the hardware of each workstation and server 
- the software installed with the exact version 
- the date of the last report

## **End-of-Life Equipment**

<span style="font-family: Roboto, Nunito, -apple-system, BlinkMacSystemFont, Segoe UI, Oxygen, Ubuntu, Cantarell, Fira Sans, Droid Sans, Helvetica Neue, sans-serif; color: rgb(235, 237, 242)">Equipment that is no longer maintained is equipment that will no longer receive security patches. It is then necessary to exclude from your network all the equipment that cannot be maintained. In case of extreme necessity, a risk acceptance by a CISO(Chief Information Security Officer) must be performed and traced in your inventory.</span>

## **Secure Boot**

The secure boot must be enabled on all your compatible devices. This feature ensures that the computer boots using only manufacturer-approved software.

## **Softwares List**

In order to reduce the attack surface, it is important that your company has a strict policy regarding authorized and unauthorized software.

### **Allowed Softwares**

To do so, the use of GPO (Group Policy Object) or [Intune](https://learn.microsoft.com/en-us/mem/intune/fundamentals/what-is-intune) allows you to provide your users with a quickly available software library without the need for administrative rights to its stations.

### **Forbidden Softwares**

In the same way, whether via Intune or AppLocker, it is necessary to block software identified as forbidden (either because you do not legitimize the application or because its version is subject to a CVE (Common Vulnerabilities and Exposures) that is dangerous for you)

## **Security Hardening**

- Station handover procedures with prerequisite checklist
- Audit of the secure configuration of the devices 
- Alert in case of configuration modification

### **Backups**

Backups are not a mechanism for fighting Ransomware but they are your last line of defense. A non-operational backup system following an attack could jeopardize the survival of your business.

### **Rule 3-2-1**

As a basic rule and the minimum expected for an infrastructure, the 3-2-1 rule states that you must:

- \- Have at least three copies of your data 

  \- Store on two different media

  \- One of which must be an offsite external backup

### **Three Copies**

The principle is to have your data on the server and two backups. This is to avoid that a failure makes your backups inoperative.

### **Two Different Media**

Here, two media should not be understood as necessarily two different physical formats (hard disk and LTO tape) but as having one's backup on two different and unrelated points

### **One Offsite External Backup**

The idea behind this request is to have a backup stored outside your building that contains the main data to protect against risks such as fire.

## Minimum Storage Time

It is important that the backups allow to restore at least 30 days old data. Why 30 days? Because the average time between the intrusion in the park and the detection by the company is about this time.

## Backup Tests

Now that your data is backed up according to best practices, it is important to ensure that your test restores are tracked and that each server is restored at least once a year.

### **Phishing Prevention**

Phishing attacks represent one of the biggest initial attack vectors along with the exploitation of vulnerabilities on your online servers.

### **Antispam and Email Protection**

Do all emails received by your employees pass through a spam filter? Does your Antivirus (AV) software analyze the attachment in the mail? Is this configuration reviewed and kept up to date with new threats?

**Analysis Procedure**

When one of your employees receives an email and has a doubt, she/he should have the possibility to contact someone to perform an analysis of the email.

**Phishing Drill**

It is often experienced as an attack on the staff, it may be worthwhile to conduct a test to ensure that your staff is properly aware.

### **Internet Browsing Protection**

### **DNS Filtering**

Block dangerous sites and filter unwanted content through your firewalls. In addition to "unprofessional" categories like +18 adult content, there is one category that is rarely blocked, URL shorteners. This service is massively used, especially for phishing

### **Centralized Management of Browsers**

Updating browser security settings can make it harder for malware to install.

### **Patching**

Deploy patches to your software and firmware as quickly as possible. Enable automatic updates whenever possible.

**What is SLA?**

A service-level agreement (SLA) is a contract between a service provider and its customers that documents what services the provider will furnish and defines the service standards the provider is obligated to meet.

### **Access Control**

Implement policies, processes and technologies that ensure that only authorized users are granted the least privileges necessary.

### **Password & MFA**

The lowest level of protection is the implementation of a password policy within your environment. In the case of a Windows environment, this policy should be set in the "Default Domain Policy" to ensure that it applies to all computers. 

### **Zero Trust**

Identify and disable unused accounts, eliminate shared accounts, remove unnecessary privileges and enforce strong password policies.

### **Audit of Account Usage**

Monitor and analyze user activity for anomalous behavior such as access attempts outside of normal business hours or from unusual locations

### **Return to Service**

Has your company conducted a study to define which resources should be recovered first? This analysis can also be used to estimate the impact of disruptions and identify allowable downtime.

### **Review of Risks on Connected Networks**

Every connection to your company is a risk to it. Whether it's within an entity of your company or a partner. Keep in mind that each of these parties may not have the same security requirements as you do. 

### **Network**

Monitor your organization's incoming and outgoing Internet traffic.

### **PCAP**

Use the SPAN ports of your network equipment to capture your network activities.

### **Segmentation**

Segmentation divides a computer network into smaller parts. Network segmentation improves network performance and security by reducing the attack surface and limiting the range of an attack.

### **Review of Blocked Flows**

Now that your corporate network is segmented, and flows are prohibited, the next step is to set up a review to identify the origin of the requests that get blocked with your new policy.

### **Alert Outside of Standard Use**

Once all this is in place, you can generate alerts in case of abnormal network usage.