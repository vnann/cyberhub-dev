---
layout: post
title: "Cryptography"
date: 2020-04-01
tags:
  - CSOL
author: Naveen
avatar: assets/img/favicon.ico
category: usdpaper
---

Cryptography is art and science that applies complex mathematics and logic to design strong encryption. Encryption is the process of disguising the data so that its meaning is not apparent. Cryptography is one of the tools used in information security to assist in ensuring the primary goals of confidentiality, integrity, authentication, and non-repudiation (Olzak, 2012). In the cryptography and security module of this course, security is defined as the trustworthy control of authorized access by people to information in computer systems. Security can be physical (such as locks, fences, and doors), Administrative ( laws, and background checks), and Technical (firewalls, and antivirus software). A common presumption among people is that encryption means security because no one can read the data they encrypted. Still, they don’t understand that there are other ways an attacker can obtain the encryption keys if they don’t secure the system or safeguard the keys.

## Overview of Cryptography of a Fictitious Health Insurance Company

As a final project, we were asked to present how a fictitious health insurance company can use cryptographic techniques to improve the security of their network. The health industry is regularly targeted by hackers to steal health records since it yields the most money on the dark web. The main reason for such a high demand for health records is because it includes dates of birth, credit card information, Social Security numbers, addresses, and emails. To protect the electronic protected health information (ePHI) data, the Health Insurance Portability and Accountability Act (HIPAA) was introduced in 1996, which requires that covered entities and a!liated companies protect the ePHI data. Covered entities are health care providers, health insurance clearinghouses, and health plans. HIPAA has three primary rules which apply to the fictitious health insurance company, they are the HIPAA Security Rule, the HIPAA Privacy Rule, and the HIPAA Breach Notification Rule.

This final project is mainly concerned with the Security Rule in Title II of HIPAA. The Security Rule is made up of Administrative Safeguards, Physical Safeguards, and Technical Safeguards. The Administrative Safeguards in § 164.308 focuses on policies and procedures to prevent, detect, contain, and correct security violations (Scholl, Stine, Hash, Bowen, Johnson, Smith, & Steinberg, 2008, p. 17). The Physical Safeguards in § 164.310 deal with the physical protection of the equipment where ePHI data is stored (Scholl et al., 2008, p. 35). The Technical Safeguards in § 164.312 focus on authentication and encryption using cryptographic techniques to control access to ePHI data (Scholl et al., 2008, p. 40).

Cryptographic mechanisms enforce confidentiality policies in the presence of threats. It helps with the confidentiality and integrity of ePHI. The network architecture shown in Figure 1 consists of components and interfaces. It is divided into the following categories: External users, internal users, databases and storage devices, servers, network devices, key distribution protocols, and Public Key Infrastructure (PKI).

### Image place holder

<table> 
<tr style="background-color:DodgerBlue; color:white">
    <th> External Users </th>
    <th> Internal Users </th>
</tr> 
<tr style="text-align:left; vertical-align=bottom">
    <td>
        This group consists of customers and providers who have access to ePHI data via an internet connection to the company’s web server. They will use a modern web browser to access ePHI data hosted on the web server using TLS v1.2 protocols. The web server supports TLS v1.2 protocol with Advanced Encryption Standard (AES) symmetric key encryption algorithm in CBC mode with a 128-bit key length, secure hash function HMAC-SHA256 and Elliptic Curve Di!e-Hellman Ephemeral algorithm (ECDHE) for key distribution. TLS 1.2 is the approved protocol to provide authentication, confidentiality, and data integrity by NIST SP 800-52r1 (Polk, McKay, & Chokhani, 2014, p. 18). ECDHE provides the basis for a range of authenticated protocols and is used to provide forward secrecy for web browsers using HTTPS. It provides bidirectional encryption of communication between a client and server, which protects against eavesdropping and tampering or forging the contents of the communication (Ahirwal & Ahke, 2013).
    </td>
    <td >
        This group consists of remote workers who connect to the corporate network via IPSec VPN with AES encryption algorithm in CBC mode and a key length of 128-bits. Employees located on site will connect directly to the corporate LAN via a wired or wireless network. Authentication of users is done using domain credentials and the Kerberos protocol to access resources on the network.
    </td>
</tr>

</table>

<table> 
<tr style="background-color:DodgerBlue; color:white">
    <th> Database and Storage Devices </th>
    <th> Servers </th>
</tr> 
<tr style="text-align:left; vertical-align=bottom">
    <td>
        The databases and storage devices containing ePHI data and corporate data are protected by utilizing full disk encryption at rest using an AES block cipher algorithm with a key length of 128-bits, in CBC block cipher mode with a secure hash function of SHA-256. The ePHI data is securely backed up and stored at the o”-site backup location to comply with HIPAA contingency plan §164.308(7) (Scholl et al., 2008, pp. F-2, F-3). The o”-site backup will also include corporate data based on company RPO and RTO requirements. Backup data is encrypted with the AES block cipher algorithm with a key length of 128-bits, CBC block cipher mode and secure hash function SHA-256.
    </td>
    <td>
        The servers consist of Microsoft Domain Controllers (DC), an Active Directory (AD) server, a Kerberos server, and web servers. The Kerberos server is located on the corporate LAN and is integrated with AD to provide strong authentication for client/server communication using symmetric key authentication to secure the tra!c over the network. It will help eliminate the risk of tra!c sni!ng by an unauthorized person who gains access to the network to capture unencrypted credentials. The Web server provides ePHI data to external users over TLS v1.2 protocol.
    </td>
</tr>

</table>
<table>
<tr style="background-color:DodgerBlue; color:white">
    <th> Network Devices </th>
</tr> 
<tr style="text-align:left; vertical-align=bottom">
    <td>
        This group consists of Wireless Access Point (WAP), Firewalls, and VPN. Employees located onsite can connect to corporate LAN using the WAP to access the resources on the network. Connections over the WAP are encrypted using WAP2-AES Enterprise AES block cipher, CCMP mode with a key length of 128-bit and HMAC-SHA256. The WAP uses Kerberos protocols to authenticate users.

        The Palo Alto Networks VPN device uses the IPSec protocol to securely connect remote workers to the corporate network using AES-128-CBC algorithm for encryption, HMAC-SHA-256 for message authentication and ECDHE for the key distribution protocol (“PAN-OS 8.0 IPSec Cipher Suites”, 2019). Access to the Firewall is limited to a few network administrators. The firewall is a critical part of the network, so access to the administration portal is secured with a strong password in accordance with the password policy defined in the security policy.
    </td>
</tr>

</table>

<table>
<tr style="background-color:DodgerBlue; color:white">
    <th> Key Distribution Protocols </th>
    <th> Public Key Infrastructure </th>
</tr> 
<tr style="text-align:left; vertical-align=bottom">
    <td>
        The Palo Alto Networks VPN device uses the IPSec protocol to securely connect remote workers to the corporate network using AES-128-CBC algorithm for encryption, HMAC-SHA-256 for message authentication and ECDHE for the key distribution protocol (“PAN-OS 8.0 IPSec Cipher Suites”, 2019). Access to the Firewall is limited to a few network administrators. The firewall is a critical part of the network, so access to the administration portal is secured with a strong password in accordance with the password policy defined in the security policy.
    </td>
    <td>
        There are two areas where PKI will be used in the system architecture. The first one will serve external users and the second one will serve internal users, computers and applications. Sectigo, formerly Comodo will be used as the external root CA to generate a certificate to use with the web server. An internal PKI implementation consisting of a two- tier hierarchy with a root CA that is o#ine and a subordinate Issuing CA that is online. The root CA and Issuing CA are separated to provide an increased level of security.
    </td>
</tr>
</table>

## Reflection

I chose the final project as my artifact because it demonstrates how to design and implement cryptographic and non-cryptographic techniques to safeguard the ePHI data that the company creates, receives, maintains, or transmits against reasonably anticipated threats, hazards and unauthorized user.

This course helped me reinforce my knowledge of block ciphers, hash functions, message authentication codes (MAC), key distribution protocols, Kerberos, and public key infrastructure (PKI). In my professional and personal life, I use encryption daily and always thought by using strong encryption is good enough to protect the data. I haven’t considered all the non- cryptographic ways an attacker can compromise my system and gain access to the data. I have learned that attackers always look for the least resistant path to gain access to sensitive data. They can steal the key using techniques such as social engineering, SSL MITB attacks, or Key Hijacking. I think it is much simpler for an attacker to gain access to a server using multiple vulnerabilities already present in the system to compromise it and gain access to the private key.

It is the moral and ethical duty of every individual that is entrusted with confidential information such as client data, nonpublic business strategies, trade secrets in this case with cryptographic keys, to protect the confidentiality and integrity of the organization’s data.

## References

- Ahirwal, R.R., & Ahke, M. (2013). Elliptic Curve Di!e-Hellman Key Exchange Algorithm for Securing Hypertext information on Wide Area Network. Retrieved from http://citeseerx.ist.psu.edu/viewdoc/download? doi=10.1.1.299.9663&rep=rep1&type=pdf

- Lee, J. (2019, June 14). What is ePHI? Examples, Compliance, Laws, and More. Retrieved from https://learn.g2.com/ephi

- Olzak, T. (2012, June 11). Chapter 7: The role of cryptography in information security. Retrieved from https://resources.infosecinstitute.com/role-of-cryptography/#gref PAN-OS 8.0 IPSec Cipher Suites. Retrieved from https://docs.paloaltonetworks.com/compatibility-matrix/supported- cipher-suites/cipher- suites-supported-in-pan-os-8-0/cipher-suites- supported-in-pan-os-8-0-ipsec

- Polk, T., McKay, K., & Chokhani, S. (2014, April). Guidelines for the Selection, Configuration, and Use of Transport Layer Security (TLS) Implementations. Retrieved from https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800- 52r1.pdf

- Scholl, M., Stine, K., Hash, J., Bowen, P., Johnson, A., Smith, C., & Steinberg, D. (2008, 22 October). An Introduction Resource Guide for Implementing the Health Insurance Portability and Accountability Act (HIPAA) Security Rule. Retrieved from https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800- 66r1.pdf
Cryptography Related Links

## Cryptography Related Links

- [An Introductory Resource Guide for Implementing the Health Insurance Portability and Accountability Act (HIPAA) Security Rule](https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-66r1.pdf)
- [Certificate Revocation (CRL vs OCSP)](https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-66r1.pdf)
- [CIS Controls Security Best Practices to Improve their Cyber Defense. V7.1](https://learn.cisecurity.org/cis-controls-download)
- [Deploy A PKI on Windows Server 2016](https://timothygruber.com/pki/deploy-a-pki-on-windows-server-2016-part-4/)
- [Elliptic Curve Di!e-Hellman key Exchange Algorithm for Securing Hypertext Information on Wide Area Network](https://www.cysecops.com/wp-admin/post.php?post=397&action=edit)
- [Guideline for Using Cryptographic Standards in the Federal Government – NIST SP 800-175A](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-175A.pdf)
- [Microsoft Kerberos for the Busy Admin](https://docs.microsoft.com/en-us/archive/blogs/askds/kerberos-for-the-busy-admin)
- [Protecting Controlled Unclassified Information in Nonfederal Systems and Organizations](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-171r2.pdf)