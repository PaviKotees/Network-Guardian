# Network-Guardian
**Summary:** Creating a LAN consisting of Windows Server 2019, Windows 10 and Kali Linux. Performing DoS on Windows 10 machine using Kali Linux and detecting the attacking with SIEM, Splunk configured on Windows Server 2019 system. 

#### Table of Contents

1. [Introduction](#introduction)

   - [Intro To Splunk](#intro-to-splunk)
      - [Monitoring and creating alerts](#creating-alerts) 
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

## Creating alerts

Splunk has feature where we can create alerts for specific attacks.

For example,let's do a port scan against my Windows 10 **(10.0.0.230)** machine from my Kali Linux **(10.0.0.61)** machine
<img src="https://github.com/PaviKotees/Malware-Analysis/assets/154454339/092ed852-aed8-434f-82e4-f8bd7c5a17a8" height="30%" width="30%"/>

The logs for the port scan can be see on Splunk on the host machine, Windows 10 **(10.0.0.230)**

<img src="https://github.com/PaviKotees/Malware-Analysis/assets/154454339/c5520137-264a-4a51-a4b3-ecad2c811682" height="30%" width="30%"/>

Creating an alert for the port scan done by Linux machine:

<img src="https://github.com/PaviKotees/Malware-Analysis/assets/154454339/a2b8525d-975a-400b-b140-887d2623ce61" height="30%" width="30%"/>

Conducting the port scan once again and alert is triggered:

<img src="https://github.com/PaviKotees/Malware-Analysis/assets/154454339/7f529e98-a8f4-431a-aebe-d0230a7f6c0c" height="30%" width="30%"/>



### **Configuring Splunk Forwarder**

Splunk Forwarder will be the tool that will forward the logs from a machine to a central log aggregating machine, usually a server. 

The Splunk Forwarder setup will require us to indicate the source (logs) which it should be forwarding and enter the receiver's IP as well as the port at which the receiver will be accepting the logs. 

<img src="https://github.com/PaviKotees/Malware-Analysis/assets/154454339/37e2c183-b1ca-4409-8471-a5516061947a" height="30%" width="30%"/> <img src="https://github.com/PaviKotees/Malware-Analysis/assets/154454339/7e014f31-9ddc-43fd-a18d-9d189885f27e" height="30%" width="30%"/> <img src="https://github.com/PaviKotees/Malware-Analysis/assets/154454339/755585cc-8bb4-46a0-88a2-d4c5cb0e9380" height="29%" width="29%"/>

Very important to configure the receiving port on the server's Splunk which will be our central repository.

<img src="https://github.com/PaviKotees/Network-Guardian/assets/154454339/01c0d6f7-4206-45b3-85a2-eec7c6d100be" height="30%" width="30%"/>

## Setting Up pfsense Firewall

After downloading [pfsense firewall](https://www.pfsense.org/download/). Set up the firewall with the number of interfaces required depending on the number of systems it will be connected to. 

<img src="https://github.com/PaviKotees/Network-Guardian/assets/154454339/11ca0a99-d575-410c-9127-1a121e479e95" height="30%" width="30%"/> 

Configure adapter em1 with an IP and set it up for DHCP leasing. Confiure rest of the adapters with an IP except one adapter which will act as a span port.

<img src="https://github.com/PaviKotees/Network-Guardian/assets/154454339/00bce584-dca6-43eb-a301-9f1c8c62e0e9" height="30%" width="30%"/> 

Installed Kali Linux on another machine which will be the attack machine and can be used to finish setting up the pfsense firewall.

Enter the firewall's IP in the browser and we will directed to the firewall's login page.

<img src="https://github.com/PaviKotees/Network-Guardian/assets/154454339/a0a58fba-ddbc-4803-b3d1-bb0f44419055" height="30%" width="30%"/> <img src="https://github.com/PaviKotees/Network-Guardian/assets/154454339/ba8f4d11-fc84-4cc7-9aa2-b02e3cc6dc61" height="30%" width="30%"/>

**I will be adding to this lab from time to time.**
