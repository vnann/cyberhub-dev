---
layout: post
title: "Incident Response and Computer Network Forensics"
date: 2020-04-01
tags:
  - CSOL
author: Naveen
avatar: assets/img/favicon.ico
category: usdpaper
---

Every organization in today’s digital world experiences cyber incidents such as network intrusion, information leaks, and data breaches. The response to these incidents needs a structured process and security tools to quickly and safely extract evidence to identify how the intruders gained access to the system and what information they accessed. This course helped me to understand the challenges faced by incident responders and computer forensic investigators as well as the tools and techniques available to help them overcome some of those issues. For example, as a computer forensic investigator, there are significant legal issues, and ethical problems that you must deal with, failure to follow proper legal procedures will result in evidence being ruled inadmissible in court.

I have chosen my final project as an artifact to demonstrate my understanding of this course and the practical application of tools and techniques I learned. The final project can be found below.

## Reflection

In my final project, I was tasked to identify how M57.biz company’s confidential spreadsheet, which contained SSN and salary information of its employees were found on a competitor’s website. Jean, the CFO, said she emailed the spreadsheet to the president Alison Smith upon her request. The task was to identify how the spreadsheet was leaked. Jean’s laptop image file was provided by investigators, which I imported into Autopsy digital forensic software for analysis. In my analysis, I reviewed devices attached, encrypted files, web history, unallocated and slack space, chat history, deleted files, emails, installed programs, and web downloads. During my examination, I found several emails from an attacker spoofing Alison Smith’s email to try to trick Jean into sending him the information he wanted. Based on the evidence, I found Jean is a victim of email spoofing. The attacker spoofed Alison Smith’s email address and asked Jean to create a list of employee’s SSN and salary details. Jean sent the spreadsheet to the attacker without realizing that the request came from an attacker. There are several red flags about the emails she received. It is my opinion that Jean is not adequately trained in cybersecurity, so she should not be held responsible.
The knowledge I gain through this course will help me respond and preserve the evidence through the proper chain of custody (CoC) when a cybersecurity incident occurs in my organization.

## References

- Autopsy. (n.d.). Autopsy Digital Forensics. Retrieved from https://www.autopsy.com

- Fahey, R. (n.d.). Computer forensics code of ethics. Retrieved from (https://resources.infosecinstitute.com/category/computerforensics/introduction/areas- of-study/legal-and-ethical-principles/computer-forensics-code-of-ethics/#gref

## Incident Response and Computer Network Forensics Related Links

- [Autopsy Digital Forensic Software](https://www.autopsy.com/)
- [Becoming a Forensic Investigator](https://www.sans.org/reading-room/whitepapers/forensics/forensic-investigator-1453)
- [International Society of Forensic Computer Examiners](http://www.isfce.com/policies/CCE%20Certification%20Competencies.pdf)
- [NIST Computer Forensics Tools & Techniques Catalog](https://toolcatalog.nist.gov/index.php)
- [NIST Digital Evidence Resources](https://www.nist.gov/topics/digital-evidence)
- [NIST Special Publication 800-86: Guide to integrating Forensic Techniques into Incident Response](https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-86.pdf)
- [U.S Department of Justice – Forensic Examination of Digital Evidence: Guide for Law Enforcement](https://www.ncjrs.gov/pdffiles1/nij/199408.pdf)