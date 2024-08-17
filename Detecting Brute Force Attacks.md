### **Introduction to Detecting Brute Force Attacks**

Brute force attacks are a frequently preferred attack technique by attackers as they provide direct access to the system if successful.

### **Brute Force Attacks**

Brute force attack is the name given to the activity performed to find any username, password or directory on the web page or an encryption key by trial and error method. 

### **1.1.1. Passive Online Brute Force Attacks**

In passive online brute force attacks, the attacker and the victim are on the same network, but do not have direct contact with each other. Usually, the attacker tries to obtain the password in passive ways without establishing a one-to-one connection with the victim machine

**Man in the Middle,Sniffing**

### **1.1.2. Active Online Brute Force Attacks**

In active online brute force attacks, the attacker communicates directly with the victim machine and makes the necessary trials to the relevant service on the victim machine. For example, user/password attempts made to a web server, email server, SSH service, RDP service or a database service can be given as an example for this title.

## **1.2. Offline Brute force attacks**

Offline brute-force attacks are used for previously captured encrypted or hashed data. In this type of attack, the attacker does not need to establish an active connection directly with the victim machine. Attacker can perform an offline attack on the password file that he/she somehow gained access to. The password information to be attacked 

- By capturing packets on wireless networks
- Capturing a package with a mitm attack
- Dumping hashes from db with a SQLi weakness
- SAM or NTDS.dit database on Windows systems

### **1.2.1. Dictionary Attacks**

This is a problem caused by the use of a common password. This is an attack method that usually occurs as a result of more than one person using the same password accidentally.

### **1.2.2. Brute Force Attacks**

Brute force attacks are a method performed by trying all possibilities in a certain range one by one.

### **1.2.3. Rainbow Table Attacks**

![](https://ld-images-2.s3.us-east-2.amazonaws.com/Detecting+Brute+Force+Attacks/images/image-1024x576.jpeg)We should keep in mind that all password possibilities in a certain range are calculated with the relevant function in a rainbow attack

<span style="font-family: Roboto, Nunito, -apple-system, BlinkMacSystemFont, Segoe UI, Oxygen, Ubuntu, Cantarell, Fira Sans, Droid Sans, Helvetica Neue, sans-serif; color: rgb(235, 237, 242)">In this attack type, the attacker quickly compares the pre-calculated hash file with the password summary he/she wants to crack and obtains the password if there is a  match.</span>

### **Protocol/Services That Can Be Attacked by Brute Force**

- Web application login pages
- RDP services
- SSH services
- Mail server login pages
- LDAP services
- Database services(mssql,mysql, postgresql, oracle, etc.)
- Web application home directories(directory brute force)
- DNS servers, in order to detect DNS records (dns brute force)

### **How to Avoid Brute Force Attacks?**

You can find some best practices for passwords below:

- Never use information that can be found online (like names of family members).
- Have as many characters as possible.
- Combine letters, numbers, and symbols.
- Minimum 8 characters.
- Each user account is different.
- Avoid common patterns.

**Lock Policy** - After a certain number of failed login attempts, you can lock accounts and then unlock them as an administrator.

**Progressive delays** - You can lock accounts for a limited time after a certain number of failed login attempts. 

**Strong Password Policy** - You can force users to define long and complex passwords and force them to change their password periodically.

**2FA** - It is the method where a second verification is required from the user with an additional verification mechanism (SMS,mail,token,push notification, etc.) after entering the username and password.

Specific rules are usually defined on SIEM systems to detect brute force attacks. When defining these rules, we consider how many unsuccessful login attempts are made by the user within a certain period of time<span style="font-family: Roboto, Nunito, -apple-system, BlinkMacSystemFont, Segoe UI, Oxygen, Ubuntu, Cantarell, Fira Sans, Droid Sans, Helvetica Neue, sans-serif; color: rgb(235, 237, 242); font-size: 16px">.</span>

### **SSH Brute Force Attack Detection** 

Simple passwords used on the server with an SSH brute force attack can be easily found by the attackers. If such attacks fail, the attacker will only attempt a certain number of failed passwords. If successful, the password is entered successfully after a certain number of unsuccessful login attempts.

<span style="font-family: Roboto, Nunito, -apple-system, BlinkMacSystemFont, Segoe UI, Oxygen, Ubuntu, Cantarell, Fira Sans, Droid Sans, Helvetica Neue, sans-serif; color: rgb(235, 237, 242)">In HTTP login brute force attacks, the attacker usually tries a password with a dictionary attack on a login page. In order to analyze this, the content of the relevant log file should be opened with a text editor and the logs should be examined. </span>