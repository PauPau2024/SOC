# **Introduction to Cyber Kill Chain**

<span style="font-family: Roboto, Nunito, -apple-system, BlinkMacSystemFont, Segoe UI, Oxygen, Ubuntu, Cantarell, Fira Sans, Droid Sans, Helvetica Neue, sans-serif; color: rgb(235, 237, 242); font-size: 16px">Cyber Kill Chain is a framework created by Lockheed Martin in 2011 and used to model the attacks of attackers. Within this framework, attacker behaviors and the whole cyber attack process consists of 7 steps that follow one another. </span>

## **Significance of Cyber Kill Chain**

Cyber Kill Chain is important for the SOC analyst to have a better understanding of the stages of a cyber attack and to determine which action(s) the cyber attack starts with and which action(s) follows. The SOC analyst can use Cyber Kill Chain to analyze where in the cyber attack the acts of the attacker noticed on the systems occur.

### **Cyber Kill Chain Steps**

There are several actions that an attacker can take before, during, and after a successful cyber attack. These actions are sequential, and if the attacker fails at one stage, it is not possible to execute the next step of the cyber attack. The Cyber Kill Chain model divides these stages of attackers into 7 steps

1. Reconnaissance
2. Weaponization
3. Delivery
4. Exploitation
5. Installation
6. Command & Control (C2)
7. Actions on Objectives

### **Reconnaissance**

The Cyber Kill Chain begins with the "Reconnaissance" step. The attacker attempts to obtain information about the target system at this step. The more knowledge an attacker has about the target system, the more the attack surface seems to him. Attack vectors for the target are disclosed in this way. The techniques employed at this stage may be divided into two subcategories:

1. Passive Reconnaissance
2. Active Reconnaissance

The term "**Passive Reconnaissance**" refers to the collecting of information from sources about the target system without physically engaging with the target system. As an instance of this, Web archive websites can be used to obtain information that is no longer available on the target system's website.

"**Active Reconnaissance**" refers to the method of acquiring information about a target system by engaging with it directly. By submitting a request to a web server, for instance, version information about the web server may be acquired from the response.

## **Adversary**

The attacker can gather information from a variety of sources using a variety of approaches during the "Reconnaissance" process. At this phase, the attacker can perform the following operations:

- Obtaining version information of servers and software belonging to the target
- Obtaining information from open sources of information about the target has previously been released
- Obtaining e-mail addresses of employees of the organization
- Obtaining internal or personal information about employees of the organization using social networking platforms
- Detection of devices that are connected to the Internet
- Detection of security vulnerabilities on servers open to access on the Internet
- Identifying the IP address block belonging to the organization
- Identification of vendors that the organization cooperates with

## **Defender**

Blueteams may take action in response to attackers' attempts at this stage. This reduces the amount of information that an attacker can obtain. Some methods that SOC analysts and blueteams can implement are listed below:

- Detection of areas of information disclosure with external pentest
- Obtaining leak information about the organization from Threat Intelligence sources
- Not to keep the documents providing organizational information available on the internet
- Monitoring traffic by installing security solutions such as firewalls in areas of the company that are accessible over the internet
- Instantly updating to avoid new security vulnerabilities from being exploited

### **Weaponization**

The "Weaponization" is the second step in the Cyber Kill Chain. At this stage, the attacker uses the information obtained in the previous stage to access the tools needed for the attack or develops the tool/script directly. At this stage, preparation for a cyber-attack may differ depending on the sort of attack

The attacker might build many alternative attack techniques or prepare the essential components for a cyber attack during the "Weaponization" process. The following are some of the processes that the attacker might employ at this stage:

- Creating malware
- Developing exploits
- Creating malicious content for use in a phishing attempt (such as an email template and a malicious document).
- Identifying the best instrument for the cyber attack

## **Defender**

It is not possible for SOC analysts and Blueteams to directly prevent the attack preparations of attackers at this stage. However, some measures can be taken, albeit limited. Some of these measures are as follows:

- Checking the systems on a regular basis to see if any identified security vulnerabilities exist.
- Installing security updates for the systems of the institutions as soon as possible
- Analyzing the impact of known or newly produced cyber attack tools on systems by tracking the known or newly developed attack tools and therefore being able to detect when the tool is utilized

### **Delivery**

The third step of the Cyber Kill Chain is the "Delivery" stage. At this stage, the attacker executes the cyber attack that he prepared for in the preceding phases. This is the stage where the first interaction with the victim happens. For instance, malware is uploaded to the proper environment at this step, and the victim downloads the malware from the uploaded environment to their systems.

## **Adversary**

In the "Delivery" stage, the attacker can deliver a variety of cyber weapons to the victim via a variety of methods. At this stage, the attacker can carry out the following operations:

- Delivering a malicious URL via email
- Delivering malware as a file attachment via email
- Delivering malware through the website
- Delivering the malicious URL via social media
- Delivering malware via social media
- Uploading the malware directly to the target server (if direct access to the server is possible) 
- Physically installing or enabling the installation of malware directly to the target system via a USB device

## **Defender**

Blueteams and individual users can take plenty of precautionary measures at this stage. Although they cannot totally prevent the cyber attack from occurring, these precautions can drastically minimize the risk of a successful cyber attack. Some of these measures are listed below:

- Adopting a skeptical attitude towards URLs in email content and viewing them in a sandbox environment
- Scanning the email's attachments using antivirus software
- Using email security solution products in organizations
- Ensuring that users/institutional employees receive training on information security
- Constant monitoring of server access and recording of logs
- Effective use and management of security solutions such as Firewall
- Conducting detailed analysis of suspicious activities when needed
- Detecting anomalies and determining the initial reason

### **Exploitation**

The attacker ensures that the malicious content provided to the victim in the previous step gets activated in this stage. During the exploitation step, the process of running the malware transmitted to the victim's device is carried out. The initial operation in the system is performed by the attacker at this stage.

## **Defender**

Defending against exploitation poses a significantly more intricate and labor-intensive task for Blueteams compared to other stages. This is primarily due to the potential encounter with previously unseen malware or exploits, which adds a layer of complexity to the defense process. To elucidate, the use of zeroday exploits can complicate the detection and prevention procedures during this phase. The following points may be considered to detect and prevent malicious activities:

- Training the employees of the organization on when it is/is not necessary to open a file uploaded on the systems and what issues should be considered
- Constantly monitoring system security operations on the assets belonging to the organization and detecting anomalies
- Tracking the security vulnerabilities published for the assets belonging to the organization, writing the appropriate monitoring rule, and detecting them when they are exploited
- Following the security updates of the assets belonging to the organization and installing them immediately
- Monitoring activities on endpoints using EDR products
- Providing secure coding training to software developers in order to prevent security vulnerabilities in locally developed applications 
- Conducting pentests on assets of the organization on a regular basis
- Regular automated vulnerability scanning and monitoring of reports
- Organizing the authorizations on the assets belonging to the institution and giving each account the authority needed

### **Installation**

the attacker attempts to maintain persistence on the target system that was exploited. The attacker attempts to gain an access path that can be accessed at any time by installing a backdoor on the system. Because the exploited vulnerability will be patched and rendered inoperable after a certain time, the attacker must use a different method to gain access to the target system

- Install malware on the victim's device.
- Placing a backdoor on the victim's system
- Install web shell on the web server (if it is a web server).
- Adding a service, firewall rule, or scheduled task to ensure the persistence of the victim device

## **Defender**

The operations that Blueteams apply against attackers at this stage consist of the operations of Threat Hunting. The fact that an attacker who reached this stage is performing malicious activities on the systems indicates that the attacker cannot be detected. Therefore, whether the attacker is present or not, the SOC team should manage and execute security operations under the assumption that there is always an attacker present in the system.

- To carry out Network Security Monitoring operations on all assets of the organization
- Using EDR security solutions to be aware of configuration changes applied on each endpoint
- Restricting access to critical files on systems and monitoring access 
- Restricting access to critical paths on systems and monitoring access
- To allow the use of admin privileges only for mandatory situations by making authorization arrangements for users on the systems
- Detecting malicious process activities by monitoring the processes running on the systems
- Allowing only executable files with a valid signature to be run on the system
- Detect anomalies in all monitored system activities and find the root cause

### **Command and Control (C2)**

At this point, the attacker has completed several crucial tasks of the attack and has prepared the Command and Control (C2) server to deliver commands to the system. The attacker can send remote commands to the system and execute them at this step.

## **Defender**

- To determine whether the known C2 tools are available on systems
- Blocking C2 server IP addresses from Cyber Threat Intelligence sources through security products such as Firewall
- To detect network traffic that may be C2 communication with Network Security Monitoring on the system

### **Actions on Objectives**

"Actions on Objectives" is the seventh and final step of the Cyber Kill Chain. At this point, the attacker takes the actions planned at the first stages of the cyber attack. The attacker goes through numerous phases each of which needs to be accomplished succesfully before getting to this step. Therefore, the attacker can carry on the desired operations on the system.

## **Defender**

- Detecting anomalies in network traffic
- Restricting network access to the outside and monitoring it continuously
- Restricting access to files/folders containing critical information and controlling access regularly
- Restricting the authorization of access to databases containing critical information and continuously monitoring access
- Using DLP products to prevent data leakage
- Detecting unauthorized access by users