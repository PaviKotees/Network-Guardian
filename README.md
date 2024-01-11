# Network-Guardian
**Summary:** Creating a LAN consisting of Windows Server 2019, Windows 10 and Kali Linux. Performing DoS on Windows 10 machine using Kali Linux and detecting the attacking with SIEM, Splunk configured on Windows Server 2019 system. 

#### Table of Contents

1. [Introduction](#introduction)


# Introduction

## Platforms used for this project:

**Splunk** - Splunk is a **Security Information and Event Management**(SIEM) tool that simplifies the task of collecting and managing massive volumes of machine-generated data and searching for information within it. Using Splunk we can detect an attack and create an alert to prevent future attacks.

**Windows 10** - This will be the target machine, Splunk Unviversal Forwarder will be installed on this machine which will forward logs to central server.

**Windows Server 2019** - This will be the machine where Splunk Enterprise will be installed and all logs from the *target machine* will be forwarded to this machine.

**Kali Linux** - Kali Linux is platform that is made for attacking. 
