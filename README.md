# Fall2021_CyberSecurity

**Name:** Joshua Rechkemmer

**University:** Texas A&M University - San Antonio

**Instructor:** Professor Kevin Barton

**Class:** CSCI 3321-002

# Honeypot Assignment

**Time spent:** **15** hours spent in total

**Objective:** Create a honeynet using MHN-Admin. Present your findings as if you were requested to give a brief report of the current state of Internet security. Assume that your audience is a current employer who is questioning why the company should allocate anymore resources to the IT security team.

### MHN-Admin Deployment

**Summary:** Using the Google Cloud Platform, I created a VM instance and then cloned the MHN GitHub repository. After the download, I ran the installation script within the repository. To check if the admin VM was properly created, I entered the external IP address into a browser and saw if it had functionality.

<img src="/gif/mhn-admin_Setup1.gif">
<img src="/gif/mhn-admin_Setup2.gif">
<img src="/gif/mhn-admin_Setup3.gif">

### Dionaea Honeypot Deployment

**Summary:** Dionaea captures malware that exploits vulnerablities in network services and attempts to make a copy of it. The software uses chroot access to make it harder for malware to attack Dionaea itself and gain root access. Protocols that can be detected and captured by Dionaea are SMB, HTTP, FTP, TFTP, MSSQL, and VoIP by emulating these services, and Dionaea uses LibEmu to detect, measure, and execute shellcode

<img src="/gif/dionaea_honeypot.gif">

### Database Backup 

**Summary:** MHN uses MongoDB for its RDBMS, and the exported json file contains the id number of the attacks recorded, the source IP address, the protocol the attack uses, port that is attacked, time/date of attack, the honeypot that caught the attack, and some sort of identifier.

[Honeypot Attack DB](session.json)

### Deploying Additional Honeypot(s) (Optional)

#### Amun Honeypot

**Summary:** Amun captures malware that attack remote services by emulating many vulnerable servies, and since it is an emulation of the malware's intended target, the honeypot pretends to be exploited and is never actually exploited.

<img src="/gif/amun_honeypot.gif">

### Malware Capture and Identification

**Summary:** Unfortunately, I did not capture any malware according to my ClamAV scans

<img src="/gif/malware_Scan.gif">

## Notes

1. During the initial creation of the admin VM, I had some sort of error with the honeymap, so it wasn't capturing any attacks. To fix this, I just deleted the instance and created a new one. When I ran 

```
sudo supervisorctl status
```
It showed I had a FATAL error on the honeymap and said

```
/opt/honeymap/server/server
```

2. I had no idea on how to install or use ClamAV. In the malware section, I just installed the ClamAV on each of the honeypot VM instances and scanned them from the shell, but I do not know if this was how it is supposed to be done. I think there should be instructions on how to install and use ClamAV. I used the Ubuntu instructions on https://www.clamav.net/downloads#otherversions to install it.
3. There should also be instructions on how to get the file hash of a malware. Although I didn't catch one, I'm pretty sure I would be lost on how to get the data
