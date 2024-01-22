# Network-Guardian
**Summary:** Creating a LAN consisting of Windows Server 2019, Windows 10 and Kali Linux. Performing DoS on Windows 10 machine using Kali Linux and detecting the attacking with SIEM, Splunk configured on Windows Server 2019 system. 

#### Table of Contents

1. [Introduction](#introduction)

   - [Intro To Splunk](#intro-to-splunk)
   - [Setting Up pfsense firewall](#setting-up-pfsense-firewall)


# Introduction

## Platforms and tools used for this project:

**Splunk** - Splunk is a **Security Information and Event Management**(SIEM) tool that simplifies the task of collecting and managing massive volumes of machine-generated data and searching for information within it. Using Splunk we can detect an attack and create an alert to prevent future attacks.

**pfsesne Firewall** - This is open source and free firewall which will be used for managing traffic, DHCP leasing.

**Windows 10** - This will be the target machine, Splunk Unviversal Forwarder will be installed on this machine which will forward logs to central server.

**Windows Server 2019** - This will be the machine where Splunk Enterprise will be installed and all logs from the *target machine* will be forwarded to this machine.

**Kali Linux** - Kali Linux is platform that is made for penetration trsting which I will be using to attack.

**Hydra** - Hydra on Kali Linux will be used to perform a simple brute force attack to identify the target machine's username and password. 

## Intro To Splunk

Splunk can be used to monitor all types of activity on the host machines as well as remote machines. Here's an example of adding the logs we want to be analyzed by Splunk and viewing the system's logs on Splunk:

<img src="https://github.com/PaviKotees/Network-Guardian/assets/154454339/144d0ed5-acbc-43e5-a07b-b78cb6dbcfe7" height="40%" width="40%"/> <img src="https://github.com/PaviKotees/Network-Guardian/assets/154454339/3a47fa18-a756-48a2-9408-b5de73a0422d" height="45%" width="45%"/>

Splunk shows detailed description of every log. On the screenshot above,

**LogName=Security** - Security logs show Login attempts, object access, and file deletion. 

**EventCode=4634** - This event code is generated when a user is logged off. In this case I let the machine running and it went on sleep mode hence logging out the user(me) therefore generating an **event code 4636.**

**EventType** - 

**ComputerName** - From which machine the logs came from and the domain the machine belongs to.

### **Configuring Splunk Forwarder**

Splunk Forwarder will be the tool that will forward the logs from a machine to a central log aggregating machine, usually a server. 

The Splunk Forwarder setup will require us to indicate the source (logs) which it should be forwarding and enter the receiver's IP as well as the port at which the receiver will be accepting the logs. 

<img src="https://github.com/PaviKotees/Malware-Analysis/assets/154454339/37e2c183-b1ca-4409-8471-a5516061947a" height="30%" width="30%"/> <img src="https://github.com/PaviKotees/Malware-Analysis/assets/154454339/7e014f31-9ddc-43fd-a18d-9d189885f27e" height="30%" width="30%"/> <img src="https://github.com/PaviKotees/Malware-Analysis/assets/154454339/755585cc-8bb4-46a0-88a2-d4c5cb0e9380" height="29%" width="29%"/>

Very important to configure the receiving port on the server's Splunk which will be our central repository.

<img src="https://github.com/PaviKotees/Network-Guardian/assets/154454339/01c0d6f7-4206-45b3-85a2-eec7c6d100be" height="30%" width="30%"/>

## Setting Up pfsense Firewall



**I will be adding to this lab from time to time.**
