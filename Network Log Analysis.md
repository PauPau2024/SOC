### **Generic Log Analysis (Netflow)**

Netflow is a network protocol that collects IP traffic information. Although it was developed by Cisco, it supports Netflow from different manufacturers.

\- ISPs can bill for services

\- It is used in network design or analysis

\- It is used for network monitoring. (The sources that generate the most traffic, the most used port information, etc.)

\- Service quality can be measured

\- It provides information for SOC analysts for the detection of anomalies.

\
Via the NetFlow outputs, we can detect:

\- Abnormal traffic volume increases

\- Data leaks

\- Access to private systems

\- New IPs in the network

\- Systems accessed for the first time as well as analyze related issues

### **Firewall Log Analysis**

Firewalls are physical or virtual devices that control incoming and outgoing packets on the network according to rules created depending on the network’s cyber policies.\
<span style="font-family: Roboto, Nunito, -apple-system, BlinkMacSystemFont, Segoe UI, Oxygen, Ubuntu, Cantarell, Fira Sans, Droid Sans, Helvetica Neue, sans-serif; color: rgb(235, 237, 242); font-size: 12px">The most essential firewall logs are the logs of the traffic passing over the device. Basically, this log provides us traffic time, source IP/Port information, destination IP/Port information, interface information, location information, etc.</span>

### **A sample firewall traffic log**

date=2022-05-21 time=14:06:38 devname="FG500" devid="FG5HSTF109K" eventtime=1653131198230012501 tz="+0300" logid="0000000013" type="traffic" subtype="forward" level="notice" vd="root" srcip=172.14.14.26 srcname="CNL" srcport=50495 srcintf="ACC-LAN" srcintfrole="lan" dstip=142.250.186.142 dstport=443 dstintf="Wan" dstintfrole="wan" srccountry="Reserved" dstcountry="United States" sessionid=445180938 proto=6 action="accept" policyid=284 policytype="policy" poluuid="8ec32778-a70a-51ec-9265-8fdf896d07f1" service="HTTPS" trandisp="snat" transip=89.145.185.195 transport=50495 duration=72 sentbyte=2518 rcvdbyte=49503 sentpkt=13 rcvdpkt=42

#### Looking at the details of the above log

date= Date

time= Time

devname= Hostname

devid= Device ID

eventtime= 1653131198230012501

tz= time zone

logid= Log ID

type= Log Type (traffic, utm, event, etc.)

subtype=Sub Log Type (Forward, vpn, webfilter, virus, ips, system, etc.)

level= log level

srcip= Source IP Address

srcname= Source Hostname

srcport= Source Port

srcintf= Name of the Source Interface

srcintfrole= Role of the Source Interface

dstip= Destination IP Address

dstport= Destination Port

dstintf= Name of the Destination Interface

dstintfrole= Role of the Destination Interface

srccountry= Source IP information (Country)

dstcountry= Destination IP information (Country)

action= info on the action taken (drop, deny, accept, etc.)

service= service information

transip= NAT IP info (internal output of the private source address)

transport= NAT port info

duration= time elapsed

sentbyte= size of the packets sent (byte)

rcvdbyte= size of the packets received (byte)

sentpkt= number of the packets sent

rcvdpkt= number of the packets received

As action;

\- accept: indicates that the packet passed successfully.

\- deny: packet transmission is blocked, information is returned back to the IP address that it is blocked.

\- drop: packet transmission is blocked. No information is returned back to the IP address that it is blocked.

\- close: indicates that the communication is mutually terminated.

\- client-rst: indicates that the communication was terminated by the client.

\- server-rst: indicates that the communication was terminated by the server.

**Advantages of Firewall :** 

\- Is there a accept request at different times from the IP address that was detected as attacking and denied by the IPS on firewall logs?

\- Checking the firewall logs, you will be able to find whether there is access to/from the suspicious IPs/Domains obtained as a result of the analysis of the malicious content in the antivirus logs.

\- Firewall traffic logs are also good resources to detect which different systems an infected system is communicating within the network.

#### Through the firewall logs, suspicious activities like:

\- Port-Scan activities

\- Communication detection with IoCs

\- Lateral (lan-lan) or vertical (lan-wan, wan-lan) unauthorized access can be detected

### **VPN Log Analysis**

VPN is the technology that allows you to connect to a local network that you are not physically connected to. Generally, organizations prefer this technology to access their internal systems remotely. Today, it is known as a technology to access sites that are not accessible.

### **An example VPN log**

date=2022-05-21 time=14:06:38 devname="FG500" devid="FG5HSTF109K" eventtime=1653134913959078891 tz="+0300" logid="0101039424" type="event" subtype="vpn" level="information" vd="root" logdesc="SSL VPN tunnel up" action="tunnel-up" tunneltype="ssl-web" tunnelid=462105151 remip=13.29.5.4 user="letsdefend-user" reason="login successfully" msg="SSL tunnel established"

#### When we review the details of the above log

date= Date

time= Time

devname= Hostname

devid= Device ID

eventtime= 1653131198230012501

tz= time zone

logid= Log ID

type= Log Type (traffic, utm, event, etc.)

subtype=Sub Log Type (Forward, vpn, webfilter, virus, ips, system, etc.)

level= log level

logdesc= log description

action= action taken

tunneltype= VPN tunnel type

remip= IP address that established the VPN connection

user= User information

reason= VPN Connection Request Result

msg= Message (Detailed message after the access)

After a successful VPN connection, an IP is assigned to you for your access through the VPN system. The log of the assigned IP information may be sent either in the same log record or in a different log. In addition to the information in the sample log above, you can also see the IP information assigned to you with the “tunnelip” value in the other log after successful VPN connection.

Following suspicious activities can be detected through the VPN logs:

\- Successful/Unsuccessful VPN accesses

\- Detection of brute-force attacks against VPN accounts

\- Detection of VPN accesses outside the specified countries

\- Detection of VPN accesses outside the specified time periods

### **Proxy Log Analysis**

The Proxy basically acts as a bridge between the endpoint and the internet. Organizations generally use proxy technology for purposes such as internet speed, centralized control and increasing the level of security.

**Transparent Proxy:** Target server that we access can see the real source IP address.

**Anonymous Proxy:** Target server that we access cannot see the real source IP address. It sees the IP address of the proxy as the source IP address. Thus, it cannot obtain any information about the system that actually made the request in the backgroun

```
date= date information
time= time information
type= log type
subtype= log sub type (values like forward, vpn, webfilter, virus, ips, system etc.)
eventtype= event type that belongs to the sub type
level= incident severity level
srcip= source IP address
srcport= source port information
srcinfrole= source interface information
dstip= destination IP address
dstport= destination port information
dstinfrole= destination interface information
service= service information
hostname= requested domain
profile= source profile
action= action information
url= URL address requested
sentbyte = size of data sent by bytes
rcvdbyte= size of data received by bytes
direction= direction of the traffic
urlsource= URL sources
msg= message information
```

\
- We can detect following suspicious activities through reviewing the proxy logs:

\- Connections to/from suspicious URLs

\- Infected system detection

\- Detection of tunneling activities

### **IDS/IPS Log Analysis**

The IDS/IPS concept and solutions are technologies developed at the point where only rule-based access controls of firewall devices are not sufficient in the security world.

### **IDS vs IPS**

\- IPS: Intrusion Prevention System - Detects and prevents the suspicious activities

\- IDS: Intrusion Detection System - Only detects the suspicious activities

<span style="font-family: Roboto, Nunito, -apple-system, BlinkMacSystemFont, Segoe UI, Oxygen, Ubuntu, Cantarell, Fira Sans, Droid Sans, Helvetica Neue, sans-serif; color: rgb(235, 237, 242); font-size: 12px">IDS and IPS have signature database. A signature is a set of rules designed to detect known attacks. The structure that presents this set of rules centrally is called the signature database. An open source signature database link is shared below. These databases are constantly updated against newly formed attack vectors. Network activities that trigger these signatures can be blocked or only detected according to the determined action of the signature</span>

<span style="font-family: Roboto, Nunito, -apple-system, BlinkMacSystemFont, Segoe UI, Oxygen, Ubuntu, Cantarell, Fira Sans, Droid Sans, Helvetica Neue, sans-serif; color: rgb(235, 237, 242); font-size: 14px">IDS/IPS systems are one of the sources that will generate the most frequent alarms amongst all in place security tools for the detection of network-based or host-based attacks. Because many attacks are on the network or endpoint, IDS/IPS systems can detect and block many suspicious activities.</span>

Following information should be investigated in details when analyzing IDS/IPS logs;

\- The direction of attack (inbound or outbound) should be checked.

\- The event severity level should be checked. Levels are usually set as low, medium, high, critical. High and critical levels indicate that activity is more important, quick action is required, and a false positive is less likely.

\- A different signature trigger state should be checked between the same source and target. Triggering different signatures means that the severity level of the event should be raised higher and a faster action should be taken.

<span style="font-family: Roboto, Nunito, -apple-system, BlinkMacSystemFont, Segoe UI, Oxygen, Ubuntu, Cantarell, Fira Sans, Droid Sans, Helvetica Neue, sans-serif; color: rgb(235, 237, 242); font-size: 14px">- Is the port/service specified in the attack detail running on the target port? If it is running, the event level should be raised to the critical level, and the target system should be checked for infection.</span>

<span style="font-family: Roboto, Nunito, -apple-system, BlinkMacSystemFont, Segoe UI, Oxygen, Ubuntu, Cantarell, Fira Sans, Droid Sans, Helvetica Neue, sans-serif; color: rgb(235, 237, 242); font-size: 14px">- Is the action taken just detection or has it been blocked as well? If the attack is blocked and there are no other requests from the same IP address on the firewall, we can wait a little longer for taking the action.</span>

Following suspicious activities can be detected monitoring the IDS/IPS logs;

\- Port scanning activities

\- Vulnerability scans

\- Code Injection attacks

\- Brute-Force attacks

\- Dos/Ddos attacks

\- Trojan activities

\- Botnet activities

### **WAF Log Analysis**

WAF (Web Application Firewall) is the technology used to secure web-based applications. The analysis of firewall or IDS/IPS logs alone are often not sufficient for the detection of web-based attacks. The main reasons for this are the SSL offload issue and the control of the data in the payload (data) part of the web request.

<span style="font-family: Roboto, Nunito, -apple-system, BlinkMacSystemFont, Segoe UI, Oxygen, Ubuntu, Cantarell, Fira Sans, Droid Sans, Helvetica Neue, sans-serif; color: rgb(235, 237, 242); font-size: 14px">In networks equipped with WAF, requests from end users reach WAF first over the internet. Then the WAF inspects the request, and makes the decision whether it will be transferred to the Web Server or not. One of the biggest advantages of WAFs here is that it can perform SSL Off-load, which helps examine the content of HTTPS traffic. WAF without SSL Offloading capability cannot provide a full effective protection as it won’t be able to inspect the payload (data) part of the HTTPS communication.</span>

<span style="font-family: Roboto, Nunito, -apple-system, BlinkMacSystemFont, Segoe UI, Oxygen, Ubuntu, Cantarell, Fira Sans, Droid Sans, Helvetica Neue, sans-serif; color: rgb(235, 237, 242); font-size: 14px">WAF systems are generally the systems that handle the web access requests on the public faced systems. Therefore, we can say that WAFs are the first systems to detect web attacks and WAF logs are the ones that help SOC Analysts to detect suspicious activities.</span>

<span style="font-family: Roboto, Nunito, -apple-system, BlinkMacSystemFont, Segoe UI, Oxygen, Ubuntu, Cantarell, Fira Sans, Droid Sans, Helvetica Neue, sans-serif; color: rgb(235, 237, 242); font-size: 14px">While examining the alerts generated for detected or blocked attacks, the reputation of the source IP address that created the log/alert should be analyzed also other similar activities that the source IP created in other log sources (such as IDS/IPS, Firewall) should be investigated.</span>

```
date= date information
time= time information
type: log type
main_type: detection type
sub_type: detected activity detail
severity_level: incident severity level
proto: protocol
service: service information
action: action taken
policy: rule name
src: source IP address
src_port: source port address
dst: destination IP address
dst_port: destination port address
http_method: http request method
http_url: URL requested
http_host: host requested
http_agent: user-agent info
msg: message related to the incident
signature_subclass: signature class
srccountry: source IP country
attack_type: attack type
```

<span style="font-family: Roboto, Nunito, -apple-system, BlinkMacSystemFont, Segoe UI, Oxygen, Ubuntu, Cantarell, Fira Sans, Droid Sans, Helvetica Neue, sans-serif; color: rgb(235, 237, 242); font-size: 14px">If the application responded 200 for an attack that WAF could not prevent, it means that the attack reached the web server and returned a successful response. In some cases, the application returns code 200 while it should actually return code 404 due to some technical deficiencies in the application.</span>

\- 200 (OK): The request was received successfully and the response was returned.

\- 301 (Permanent Redirect): The request was redirected to a different location.

\- 403 (Forbidden): Data requested to be accessed is not allowed.

\- 404 (Not Found): The requested content could not be found.

\- 503 (Service Unavailable): The server cannot respond.

We can help use WAF logs when analyzing the following detections:

\- Detection of known web vulnerabilities

\- Detection of variety of web attacks like SQL Injection, XSS Attack, Code Injection, Directory Traversal

\- Detection of suspicious method usage such as PUT, DELETE

\- Top requesting IP address information

\- Most requested URL information

### **DNS Log Analysis**

SOC analysts generally use DNS logs to check which domains and when they were requested during an incident investigation of a system. We should keep the followings when checking these logs:

\- Has the system made domain requests in categories that actually should not access?

\- Has the system made domain requests that are actually risky categories?

\- Were any known services (google drive, one drive, etc.) attempted to access during situations like data leak, and etc.?

\- Is there any systems that make requests to domains obtained from Threat Intelligence resources?

\- Investigations on DNS logs should be conducted to detect if there is access to DNS Over TLS (DOT) or DNS over HTTPS (DOH) services.

#### DNS query logs generally contain the following data

\- Date-Time

\- Querying IP, Port

\- Query type

\- The requested domain