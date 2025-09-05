# Linux Privilege Escalation (TryHackMe)

## 🎯 Objective
Identify misconfigurations and vulnerabilities on a Linux target machine and escalate privileges to root.

---

## 🔍 Enumeration
- Used basic commands (`uname -r`, `lsb_release -a`, `cat /etc/issue`) to gather OS and kernel information.  
- Collected environment variables with `env` to look for potential sensitive data.  
- Listed files and permissions with `ls -la` to detect hidden files and unusual permission settings.  
- Mapped network routes with `ip route` to understand the target’s connectivity.  

**Finding:**  
The kernel version was **3.13.0-24-generic**, which is known to be vulnerable to a kernel-level privilege escalation (OverlayFS bug).

---

## 🧭 Vulnerability Research
- Matched the kernel version to **CVE-2015-1328 (OverlayFS Local Privilege Escalation)**.  
- Verified exploit availability using Exploit-DB (reference: exploit 37292).  

---

## 🔄 Exploit Transfer
- Since the target system had no internet access, I prepared the exploit on my attack machine.  
- Hosted the file using Python’s HTTP server and pulled it to the target with `wget`.  

---

## ⚙️ Exploitation
- Compiled the downloaded exploit with `gcc`.  
- Executed the binary, which successfully leveraged the OverlayFS vulnerability.  

**Result:** Escalated privileges from a normal user to **root**.

---

## ✅ Outcome
- Demonstrated Linux privilege escalation through kernel exploitation.  
- Practiced working with offline environments (transferring files without internet).  
- Reinforced the importance of patching outdated kernels to mitigate security risks.  

---

## 🧩 Key Skills Demonstrated
- Linux enumeration techniques  
- CVE research and mapping  
- Offline file transfer methods (`python3 -m http.server` + `wget`)  
- Exploit compilation and execution  
- Professional documentation of security testing process
