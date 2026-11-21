# 🧪 Cyber Home Lab Starter

**Build your first cybersecurity home lab in one weekend, for free.**

A beginner's guide by **Coach AY** (Ayomide Oluwaga) for the people I mentor. No IT background needed. If you can install an app, you can do this.

> Employers keep asking for "hands-on experience". This lab is how you get it before your first job, and how you prove it on your CV.

## 🗺️ What you'll build

| Machine | What it is | Why you need it |
|---|---|---|
| **VirtualBox** | Free virtualisation software | Runs all your lab machines on one laptop |
| **Kali Linux** | The attacker / analyst machine | Comes with Nmap, Wireshark, Metasploit and more |
| **Metasploitable 2** | A deliberately vulnerable target | Something safe and legal to practise on |
| **Wazuh** *(optional)* | A free SIEM | Lets you see attacks from the defender's side |

All machines sit on a **private host-only network**, so nothing vulnerable is exposed to the internet.

## ✅ Before you start

- A laptop with **8GB RAM minimum** (16GB if you want the Wazuh SIEM too)
- About **60GB free disk space**
- Virtualisation (VT-x / AMD-V) switched on in your BIOS
- One weekend and a cup of tea ☕

## 📂 The guide

| Step | File | Time |
|---|---|---|
| 1 | [SETUP.md](SETUP.md): install VirtualBox, Kali and Metasploitable, and wire up the network | ~3 hours |
| 2 | [LABS.md](LABS.md): 10 hands-on exercises, from your first scan to writing a findings report | ~1 day |
| 3 | [Put it on your CV](#-put-it-on-your-cv) | 30 mins |

## ⚠️ The golden rule

**Only test machines you own or have written permission to test.** Everything in this guide stays inside your own lab. Scanning or attacking anyone else's systems is illegal in Nigeria (Cybercrimes Act 2015) and almost everywhere else.

## 📝 Put it on your CV

Add a **Projects / Home Lab** section. For example:

> **Cybersecurity Home Lab** (VirtualBox, Kali Linux, Metasploitable 2, Wireshark, Nmap)
> - Built an isolated virtual lab to practise vulnerability assessment and network analysis
> - Identified and documented 5+ vulnerabilities, including a backdoored FTP service and default credentials
> - Captured and analysed cleartext credentials in network traffic with Wireshark
> - Wrote a findings report with risk ratings and remediation steps

Then post your report on LinkedIn or GitHub. Proof of effort beats empty claims every time.

## 📚 Keep going

- [TryHackMe Pre Security path](https://tryhackme.com/path/outline/presecurity) (free)
- [Professor Messer's Security+ course](https://www.professormesser.com/) (free)
- [LetsDefend](https://letsdefend.io/) for SOC practice
- My other repos: [Tech-Jobs-Desk](https://github.com/OluwagaAy/Tech-Jobs-Desk), [SOC-Analyst-Training](https://github.com/OluwagaAy/SOC-Analyst-Training), [SecurityPlus-Labs](https://github.com/OluwagaAy/SecurityPlus-Labs)

## 🤝 Connect

- LinkedIn: [Ayomide Oluwaga](https://www.linkedin.com/in/ayomideoluwaga/)
- X: [@oluwaga_ayomide](https://x.com/oluwaga_ayomide)

⭐ If this helped you, star the repo so other beginners can find it.
