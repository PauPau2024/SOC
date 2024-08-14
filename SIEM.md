### **SIEM Introduction**

Security information and event management (SIEM) is a security solution that collects and interprets data within the organization and then detects potential threats. Thanks to SIEM, security threats can be monitored in real-time.

- How does SIEM work?
- How does SIEM collect logs?
- Log storage
- Creating alerts

### **Log Collection**

First of all, we need data for the SIEM solution to detect threats. That's why the log collection process is one of the most important parts of the SIEM architecture, because without the log SIEM would be useless.

**What is Log and Logging?**

In computing, a log file is a file that records either events that occur in an operating system or other software runs, or messages between different users of a communication software. Logging is the act of keeping a log. In the simplest case, messages are written to a single log file.

Our goal at this point is to transfer logs from various places (Hosts, Firewall, Server log, Proxy, etc.) to SIEM. Thus, we can process all data and detect threats at a central point. Logs are generally collected in the following 2 ways:

- Log Agents
- Agentless

### **Log Agents**

In order to implement this method, a log agent software is required. Agents often have parsing, log rotation, buffering, log integrity, encryption, conversion features. In other words, this agent software can take action on the logs it collects before forwarding them to the target.

**Pros of the method**\
It is a tested, and a working application by the developers

- Has many additional features like automatic parsing, encryption, log integrity, etc.\
  \
  **Cons of the method**
- As the additional features are activated, resource consumption increases. That requires the system's resources such as CPU, RAM to be increased, so the cost increases.

**Syslog**

It is a very popular network protocol for log transfers. It can work with both UDP and TCP, and can optionally be encrypted with TLS. Some devices that support syslog: Switch, Router, IDS, Firewall, Linux, Mac, Windows devices can become syslog supported with additional software.

**Syslog Format:**\
\
<span style="font-family: Roboto, Nunito, -apple-system, BlinkMacSystemFont, Segoe UI, Oxygen, Ubuntu, Cantarell, Fira Sans, Droid Sans, Helvetica Neue, sans-serif; color: rgb(235, 237, 242); font-size: 12px">Timestamp - Source Device - Facility - Severity - Message Number - Message Text</span>

### **Agentless**

Agentless log sending process is sometimes preferred as there is no installation and update cost. Usually, logs are sent by connecting to the target with SSH or WMI. For this method, the username and password of the log server are required, therefore there is a risk of the password being stolen

### **Log Aggregation and Parsing**

The first place where the generated logs are sent is the log aggregator. We can edit the logs coming here before sending them to the destination. For example, if we want to get only status codes from a web server logs, we can filter among the incoming logs and send only the desired parts to the target

**What is EPS?**

EPS is an event per seconds. The formula is Events/Time period of seconds.

**Scaling the Aggregator**\
More than one aggregator can be added so that the incoming logs do not load the same aggregator each time.

**Log Aggregator Process**\
The log coming to the Aggregator is processed and then directed to the target. This process can be parsing, filtering, and enrichment.

![](https://ld-images-2.s3.us-east-2.amazonaws.com/SIEM+101/images/aggregator3.jpg)**Log Enrichment**\
Enrichment can be done to increase the efficiency of the collected logs and to save time. Example enrichments:

- Geolocation
- DNS
- Add/Remove

### **Log Storage**

![](https://ld-images-2.s3.us-east-2.amazonaws.com/SIEM+101/images/storage1.jpg)\
One of the common mistakes made in SIEM structures is to focus on storage size. High-sized storage is important, as well as the speed of accessing this data.

<span style="font-family: Roboto, Nunito, -apple-system, BlinkMacSystemFont, Segoe UI, Oxygen, Ubuntu, Cantarell, Fira Sans, Droid Sans, Helvetica Neue, sans-serif; color: rgb(235, 237, 242); font-size: 12px">Timely occurrence of alerts varies depending on our search speed. For a log created today, we want to create a warning immediately instead of generating an alert after 2 days. Therefore, as we mentioned in our previous article, a suitable storage environment should be created. The alarms we will create for SIEM will usually be suspicious and need to be investigated. This means that the alert must be optimized and not triggered in large numbers (except in exceptional cases). Here are some ways to create an alert</span>

### **Blacklist**

It can be used to catch undesirable situations. For example, we can collect the prohibited process names (Example: mimikatz.exe) and write them to a list. Then, if a process in this list appears in the logs, we can create an alert.

### **Whitelist**

Unlike blacklist, it is used for desired situations. For example, a list of IP addresses with normal communication can be kept. If communication is made with an address other than this list, we can generate an alert.

### **Long Tail Log Analysis**

This method assumes that the behaviors that occur constantly are normal. In other words, if an "Event ID 4624 An account was successfully logged on" log is constantly occurring on a device, with this method we should take it as normal and approach the least occurring logs with suspicion.