### **Introduction to VirusTotal for SOC Analysts**

<span style="font-family: Roboto, Nunito, -apple-system, BlinkMacSystemFont, Segoe UI, Oxygen, Ubuntu, Cantarell, Fira Sans, Droid Sans, Helvetica Neue, sans-serif; color: rgb(235, 237, 242)">“VirusTotal” is a service that gathers many antivirus solutions in a single point and you can query and analyze them all. It was acquired by Google in 2012. It can be used in two different ways, paid and free. The parts that we will explain during the training include completely free parts.</span>

### **File Analysis with VirusTotal**

While reviewing the alert of a SIEM or other security solution, you may have noticed a suspicious file and want to analyze it. To view the file analysis results of different AV companies, you can upload the file on VirusTotal and find out if AV products detect this file as malicious.

\
Here you can find some basic information about the file and details about its VirusTotal history. For example, the “Basic Properties” area contains file hash information and more.

![](https://ld-images-2.s3.us-east-2.amazonaws.com/VirusTotal+for+SOC+Analysts/images/image-5-1024x273.png)In the "**History**" field, there are the dates of the first and last analysis of the file in VirusTotal.

![](https://ld-images-2.s3.us-east-2.amazonaws.com/VirusTotal+for+SOC+Analysts/images/image-6.png)As a SOC Analyst, you can draw very important conclusions from this field. For example, there is a phishing attack on your institution and you analyze the attachment in the email. After you upload the file to VirusTotal, if you see that this file has been analyzed before you, you can draw the conclusion that this malware was not written specifically for your institution. (Not exactly, but more likely.)

Similarly, if you come across a file that has been analyzed before, you can understand that this attack was done on different institutions.

### **Relations**

This is the tab that shows detailed information about the domain, IP, URL, and other files that the suspicious file in your hand communicates with. The data shown here is scanned by security vendors within VirusTotal and you can see the results.

![](https://ld-images-2.s3.us-east-2.amazonaws.com/VirusTotal+for+SOC+Analysts/images/image-7.png)You can usually use this tab to check for a suspicious address that the file is communicating with. At the same time, you can detect suspicious communication activities faster by viewing its reputation with the “Detections” score. There is an important point to note: new generation malware does not always exhibit the same behavior. They try to bypass security solutions by taking different actions in different systems. For this reason, the addresses you display in the relations tab may not give the entire list that the malware wants to communicate with, you should be aware that this list may be incomplete.

### **Behavior**

What determines whether a file is malicious is its activities. In the "Behavior" tab, you can see that different manufacturers list the activities that the scanned file has done. Among these activities, you may encounter many behaviors such as network connections, DNS queries, file reading/deletion, registry actions, and process activities.

![](https://ld-images-2.s3.us-east-2.amazonaws.com/VirusTotal+for+SOC+Analysts/images/image-8.png)In section 1, you can specify which manufacturer you want to see the results of. Section 2 contains the activities performed by the scanned file. For example, if you look at the image above, you can see that the file makes four HTTP requests and a few DNS queries.

**IMPORTANT NOTE:** As we mentioned earlier, today's malware may not always exhibit the same behavior. For example, malware that cannot communicate with the command and control center (CC) may not activate itself. If the command and control center of the malware you want to analyze is not active, dynamic and static analyzes may not yield a clear result. In such cases, you should find old analysis reports made in environments such as VirusTotal and examine the behavior as in the "Behavior" tab.

### **Key Points to Pay Attention**

VirusTotal is frequently used by SOC Analysts during the day, the data provided by the platform quickly makes the analysts' job much easier. If care is not taken in some matters, the data obtained may cause incorrect analysis. It is very important that you read the following section carefully and avoid this common mistake.

### **Old Analysis Results**

When you start a scan/search on VirusTotal, old results, if any, are shown for faster results. For example, if you scan the URL "[letsdefend.io](http://letsdefend.io)", you may see a result like the one below.

![](https://ld-images-2.s3.us-east-2.amazonaws.com/VirusTotal+for+SOC+Analysts/images/image-18-1024x164.png)If you pay attention to the area in the image above, you are viewing the scan result 1 month  ago. Since attackers know that you use the VirusTotal platform a lot, they can follow this method: Generate a harmless URL address and scan it in VirusTotal (For example [letsdefend.io/file](http://letsdefend.io/file)). It then replaces the content of the URL with something that is harmful. An amateur SOC analyst thinks the address is harmless when he sees a green screen (where all security vendors give the result Clean) when he searches VirusTotal.

![](https://ld-images-2.s3.us-east-2.amazonaws.com/VirusTotal+for+SOC+Analysts/images/image-19.png)But in this case, the analyst falls into the trap of the attacker. All it needs to do is start a new query and view the analysis results of the current content in the URL address. By clicking the “**Reanalyse**” button, the analysis is performed again.

### **Detection Tags**

One of the points to consider when deciding whether a file is malicious or not via VirusTotal is how AV companies label it.

A file may have a detection rate of 10/52 on VirusTotal, but when you examine the tags, you can see that it's not actually harmful. The most common example of this situation is setup files. In the setup files, there may be advertisements that appear on the setup screen from time to time. Since AV engines generally work on a rule-based basis, they can mark files with these ads as "Adware". For this reason, you may see these types of files as “red” on VirusTotal.