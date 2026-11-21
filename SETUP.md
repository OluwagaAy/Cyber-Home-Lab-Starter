# 🛠️ Setup: Build the Lab

Follow these steps in order. Take screenshots as you go, they become your proof later.

## 1. Install VirtualBox

1. Download VirtualBox for your operating system from [virtualbox.org](https://www.virtualbox.org/wiki/Downloads).
2. Install it with the default options.
3. If VirtualBox says virtualisation is disabled, restart your laptop, enter the BIOS (usually F2, F10 or Del), and turn on **Intel VT-x** or **AMD-V / SVM**.

## 2. Create a private lab network

This keeps your vulnerable machine away from the internet and your home Wi-Fi.

1. In VirtualBox, open **File > Tools > Network Manager**.
2. Under **Host-only Networks**, click **Create**.
3. Note the network address it gives you (often `192.168.56.0/24`). Every lab machine will live here.

## 3. Set up Kali Linux (your attacker / analyst machine)

1. Go to [kali.org/get-kali](https://www.kali.org/get-kali/#kali-virtual-machines) and download the **pre-built VirtualBox image**.
2. Extract it, then double-click the `.vbox` file to add it to VirtualBox.
3. Open the VM's **Settings > Network**:
   - **Adapter 1:** NAT (so Kali can reach the internet for updates)
   - **Adapter 2:** Host-only Adapter (so Kali can reach your lab)
4. Start it and log in with the default credentials listed on the Kali download page. **Change the password straight away** with `passwd`.
5. Update everything:
   ```bash
   sudo apt update && sudo apt full-upgrade -y
   ```

## 4. Set up Metasploitable 2 (your target)

> ⚠️ Metasploitable is deliberately insecure. **Never** connect it to NAT, Bridged or any network with internet access.

1. Download Metasploitable 2 from [SourceForge](https://sourceforge.net/projects/metasploitable/).
2. In VirtualBox, create a **New** VM: type **Linux**, version **Ubuntu (64-bit)**, 1GB RAM.
3. At the disk step, choose **Use an existing virtual hard disk file** and select the `.vmdk` from the download.
4. Open **Settings > Network** and set **Adapter 1** to **Host-only Adapter**. Disable every other adapter.
5. Start it. The default login is shown on the login screen.
6. Find its IP address:
   ```bash
   ip a
   ```

## 5. Check the lab works

From Kali, ping the target (replace the IP with yours):
```bash
ping -c 4 192.168.56.101
```
If you get replies, your lab is ready. 🎉

## 6. (Optional) Add a SIEM with Wazuh

Only do this if your laptop has **16GB RAM or more**.

1. Download the Wazuh **virtual machine (OVA)** from the [Wazuh documentation](https://documentation.wazuh.com/current/deployment-options/virtual-machine/virtual-machine.html).
2. In VirtualBox, choose **File > Import Appliance** and select the OVA.
3. Set its network adapter to **Host-only Adapter**.
4. Start it, then open the Wazuh dashboard from Kali's browser using the IP shown on the console.
5. Follow Wazuh's guide to install an agent on Kali, so attacks in the lab show up as alerts.

No 16GB? No problem. Practise the defender side on [LetsDefend](https://letsdefend.io/) or TryHackMe's SOC Level 1 path instead.

## ✅ Done? Next step: [LABS.md](LABS.md)
