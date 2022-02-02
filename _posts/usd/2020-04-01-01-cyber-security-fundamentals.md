---
layout: post
title: "Cyber Security Fundamentals"
date: 2020-04-01
tags:
  - CSOL
author: Naveen
avatar: assets/img/favicon.ico
category: usdpaper
---



The progression of computers and information technology has been explosive with the introduction of the internet. It has brought immense benefits on how we communicate and collaborate with people around the world to develop technologies that help advance in

the fields of manufacturing, space, medial, and many more. Unfortunately, there is also a dark side; adversaries try to take advantage of these technologies for financial or personal gain. The cyber security fundamental course provided a firm understanding of concepts that helped to learn the tools and techniques to keep information secure while adhering to professional and ethical responsibilities.

Here are some of the topics that covered in cyber security fundamentals:

- Threats and Vulnerabilities
- Policy
- Encryption
- Reference Monitor
- OSI Models
- Topology
- Network Scanning
- Intrusion Detection
- Incident Response, and
- Privacy Goals

<table> 
<tr style="background-color:DodgerBlue; color:white">
    <th> Vulnerability Assessment </th>
    <th> Encryption</th>
</tr> 
<tr style="text-align:left; vertical-align=top">
    <td style="text-align:left; vertical-align=top">
    In module 2, I learned how to perform a vulnerability assessment on my home network. It is one of the most important things we do as a cyber security professional. It allows us to understand the weaknesses of the network before an attacker can find the vulnerabilities to exploit them. In the vulnerability assessment exercise, I used Kali Linux and the OpenVAS (Open Vulnerability Assessment System) tool o scan the systems in the home lab. The tasks include three phases: network discovery, vulnerability assessment and a manual scan. Once the scan was completed, OpenVAS generated a detailed report to show the vulnerabilities that existed in each of the systems discovered on the network.
    </td>
   <td style="text-align:left; vertical-align=top">
    In module 5, I had the opportunity to learn how to securely exchange emails between two parties using encryption. In this exercise, I generated a private and public asymmetric key pair with a 2048-bit key size using the service provided by the http://www.comodo.com Certificate Authority. The certificate was installed on my computer and secure emails with my peer were exchanged. I used Wireshark to monitor the communication exchange and was able to see the encrypted tra!c. I also identified the cipher suite, protocol and algorithm that was used.
    </td>
</tr>
</table>

## Reflection

The two artifacts I choose to reflect on are Vulnerability Assessment and Encryption.

Vulnerability assessment is the process of identifying, enumerating, and prioritizing the vulnerabilities in a system. It is critical to understand what vulnerabilities exist in your network before an adversary can find them to exploit and gain access to the network. To perform an active vulnerability scan, you should follow four simple steps: 1) Initial Assessment, 2) System baseline definition, 3) Perform the vulnerability scan, and 4) Assessment report generation (Gonzalez, 2018). For module 2 assignment, I did a vulnerability assessment on my home network using Kali Linux and the OpenVAS (Open Vulnerability Assessment System) tool. My home network consisted of following operating systems Linux (Ubuntu), windows (windows seven desktop and 2012 server), FreeNAS, and a Metasploitable 2 Linux. In my assessment, I found server vulnerabilities to exploit to gain full access to the systems. By doing this hand-on exercise, I have learned how easy it is to find vulnerabilities in the systems using freely available scanning tools. Imagine that you are not aware of how easy it would be for an adversary to gain access to the network and infect it with malware and exfiltrate data out of the network. By doing regular vulnerability assessments, you can prioritize and fix the vulnerable systems by patching them. One should always keep a baseline configuration of the system to compare the system status after each assessment so that you have a clear understanding of the overall health of the network.

Encryption enhances the security of the data by scrambling it. It ensures that only the sender and receiver who has the keys can securely read the information. There are two methods of encryption – asymmetric and symmetric. Asymmetric encryption is also called public-key encryption in which a pair of public and private keys are used to encrypt and decrypt the data. Symmetric encryption is also called a secret key that is shared between the sender and receiver to encrypt and decrypt the message securely. According to security and privacy specialist Bruce Schneier, encryption should be part of our daily lives because it protects our data from criminals, competitors, malicious attackers, and accidents (Schneier, 2015). In one of my assignments, I had tasked with exchanging an encrypted email message with my peers. I learned how to generate public and private keys and use a certificate authority (CA) to certify my public key. Once I exchanged my public key with my peer, he was able to send me an encrypted email using my public key, which I was able to decrypt with my private key. I used Wireshark to see the encrypted tra!c and identify the cipher suite, protocol, and the algorithm that was used.

The knowledge I gained through this fundamental course helped me understand di”erent encryption methods and vulnerability assessments that are available to secure systems and data. When we conduct vulnerability assessments, it is not ethical nor professional to disclose the results outside the organization. The same goes for encryption when we are tasked with protecting the information; it is our responsibility to protect the keys that are used to encrypt the data. As a cyber security professional, it is crucial to bound to ethics and professionalism because it is what distinguishes us from criminals.

## References

- Gonzalez, K. (2018, June 8). A step-by-step guide to vulnerability assessment. Retrieved from https://securityintelligence.com/a-step-by-step-guide-to- vulnerability-assessment/
- Schneier, B. (2015, June 23). Why We Encypthttps://www.schneier.com/blog/archives/2015/06/why_we_encrypt.html
Cyber Security Fundamentals related links

## Cyber Security Fundamentals related links
- [10 Things to Include in Your Employee Cyber Security Policy](https://www.cysecops.com/wp-admin/post.php?post=315&action=edit)
- [InfraGard a partnership between FBI and private sector](https://www.infragard.org/)
- [Nessus Essentials Vulnerability Scanner from Tenable](https://www.tenable.com/products/nessus/nessus-essentials)
- [Nmap Scanning Series](http://opensourceforu.com/tag/advanced-nmap-series/)
- [OpenVAS – Open Vulnerability Assessment Scanner](https://openvas.org/)
- [Wireshark Network Analyser](https://www.wireshark.org/)