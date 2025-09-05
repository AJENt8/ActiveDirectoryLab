<h1>↗️ Privilege Escalation</h1>

<h2>Description</h2>
This project focuses on simulating attacker techniques in Linux environments to identify misconfigurations, escalate user privileges, and apply remediation strategies for hardening systems.<br />


<h2>Skills Learned</h2>

- <b>User and system enumeration techniques</b> 
- <b>Exploiting SUID/SGID binaries</b>
- <b>Leveraging misconfigured services and cron jobs</b>
- <b>Identifying and exploiting weak file permissions</b>
- <b>Password hunting and reuse detection</b>
- <b>Escalation via kernel exploits</b>
- <b>Applying least privilege principles and mitigation strategies</b>

<h2>Tools Used </h2>

- **Enumeration Tools:** `linPEAS`, `LinEnum`
- **Core Linux Utilities:** `sudo`, `find`, `cat`, `less`, `grep`, `strings`
- **File & Permission Tools:** `chmod`, `chown`, `ls -la`
- **Process & Network Tools:** `ps`, `netstat`, `lsof`
- **Archive & Binary Tools:** `tar`, `vim`, `nano`, `bash`
- **Exploit Execution:** Kernel exploit scripts (public PoCs)
- **Password Discovery:** Reviewing `history`, `.bashrc`, `/etc/shadow`, `/etc/passwd`

<h2>Project Walk-Through:</h2>

<p align="center">
Some Examples Commands for Enumeration: <br/>
 
 <br> Commands: `hostname` & `uname -a` </br>
<img src="https://i.imgur.com/WSJX1l3.png" height="80%" width="80%" alt="Enumeration Commands"/>

<br> Command: `env` </br>
<img src="https://i.imgur.com/nbDFTg5.png" height="80%" width="80%" alt="Enumeration Commands"/>

<br> Command: `ls -la` <br/>
 <img src="https://i.imgur.com/vIUFW5p.png" height="80%" width="80%" alt="Enumeration Commands"/>

<br> Command: `id` & `ip route` <br/>
 <img src="https://i.imgur.com/58AOD1t.png" height="80%" width="80%" alt="Enumeration Commands"/>

<br> Command: `netstat -s` <br/>
 <img src="https://i.imgur.com/AYqDzOo.png" height="80%" width="80%" alt="Enumeration Commands"/>

<br> The `find` command can also be used to seach the target system for more specific/important information and potential privilege escalation vectors. </br> 
<br />
<br />



## 🔍 Findings


The command `uname -a` was ultimately used to find a CVE vulnerability that would affect the kernel of the target system:  <br/>
<img src="https://i.imgur.com/WSJX1l3.png" height="80%" width="80%" alt="Enumeration Commands"/>
<br />
<br />

## 🧠 Key Skills Demonstrated
- Kernel & OS enumeration (`uname`, `lsb_release`, `/etc/*release`)
- Threat research via CVE/Exploit-DB
- **Offline** file transfer (Python HTTP server → `wget` on target)
- Safe screenshotting (redacting IPs/flags/user identifiers)
- Clear documentation of tactics/why they matter

---

## 🛠️ Environment (Lab)
- **Room:** TryHackMe — *Linux Privilege Escalation*
- **Target:** Ubuntu (`3.13.0-24-generic`)
- **CVE:** `CVE-2015-1328` (OverlayFS Local Privilege Escalation)
- **Exploit-DB Ref:** 37292

> ⚠️ *All screenshots are from an isolated training environment. Any sensitive items (flags, public IPs, unique usernames) are redacted.*

---

## 🔍 Enumeration Highlights

<table>
<tr>
<td width="50%">

**Kernel version**

  ```md
<table>
<tr>
<td width="50%">

**Kernel version**

<pre><code>uname -r
3.13.0-24-generic
</code></pre>

<img src="./assets/linux-pe/uname-r.png" alt="uname -r output" />

</td>
<td width="50%">

**Environment variables**

<pre><code>env | sort
# (redact tokens/secrets if present)
</code></pre>

<img src="./assets/linux-pe/env.png" alt="env output" />

</td>
</tr>
</table>
