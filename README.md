# Wazuh-IDS-lab
Intrusion detection and active response

Project Description

This project demonstrates the endpoint detection and response (EDR) capabilities of Wazuh, an open-source security monitoring platform. The Wazuh server and dashboard are installed on Kali Linux (VMware), while a Wazuh agent is deployed on Ubuntu (VMware) to monitor system activities.
To test the setup, a Hydra brute force attack is launched from Kali against the Ubuntu machine, and Wazuh successfully detects the intrusion attempts in real time.

Setup

1- Setting up Ubuntu on VMware
Ubuntu will act as the agent machine in our project. First, we need to install Ubuntu on VMware.
Steps:
2. Download Ubuntu ISO
  Download the Ubuntu Desktop ISO 
  👉 https://ubuntu.com/download/desktop/thank-you?version=24.04.3&architecture=amd64&lts=true

3.Open VMware Workstation / Player
 - Click on Create a New Virtual Machine.
 - Select Installer disc image (ISO) and browse the downloaded Ubuntu ISO.

 4.Configure VM Settings
-Name the VM (e.g., Ubuntu-Agent).
-Allocate at least:

 2GB RAM (better 4 GB)
-2 CPUs
-25 GB Disk Space

 4.Install Ubuntu
-Start the VM and follow on-screen instructions.
-Choose Normal Installation.
-Set up your username and password 

Post-Installation Setup
-Once Ubuntu boots up, update the system:
-sudo apt update && sudo apt upgrade -y

<img width="1800" height="888" alt="ubuntu" src="https://github.com/user-attachments/assets/5e138fb1-a1eb-4f35-8108-9531c198b2a6" />

Install VMware Tools (for smooth clipboard & resolution).
✅ Now Ubuntu is ready as the agent machine, where we will install the Wazuh agent later.

STEP 1 - Installing Wazuh 

1: Update Kali
-sudo apt update && sudo apt upgrade -y

2: Download and run Wazuh installation assistant
curl -sO https://packages.wazuh.com/4.12/wazuh-install.sh && sudo bash ./wazuh-install.sh -a

3: Wait for setup to finish. At the end, it will show:
INFO: --- Summary ---
INFO: You can access the web interface https://<KALI_IP>
      User: admin
      Password: <ADMIN_PASSWORD>
INFO: Installation finished.

Step 4: Open browser in Kali → Go to
https://<KALI_IP> 

<img width="1234" height="569" alt="dashboard" src="https://github.com/user-attachments/assets/2364a3b8-b0dc-435a-9f7e-cc0194f4050b" />


STEP-2  ( Installing Wazuh Agent on Ubuntu VM )

 From the Wazuh GUI interface, proceed to Agents > Deploy new agents

<img width="1450" height="481" alt="AGENT" src="https://github.com/user-attachments/assets/351a3cc9-a273-4870-81f0-e33dc954de67" />

Next, select the correct architecture and Wazuh server address.

<img width="1266" height="910" alt="SYSTEM" src="https://github.com/user-attachments/assets/7ef7ca4d-3fce-4194-9b69-997f0ed35454" />

Next, you will be presented with commands to download, install, and start the Wazuh agent. Copy the commands and run them in the Ubuntu Server you just installed. 

<img width="1590" height="830" alt="command" src="https://github.com/user-attachments/assets/0d66f2ad-36ee-431d-a5da-97651d1e5e44" />

After installing and starting the wazuh agent, check the status to make sure it is active.

<img width="1339" height="761" alt="status" src="https://github.com/user-attachments/assets/81f7eaa9-ca60-4bc4-84af-0ce88696dc9e" />

From the Wazuh Gui interface, you’ll see that a new agent has been added.

<img width="1894" height="737" alt="added" src="https://github.com/user-attachments/assets/ad9bc598-bf06-4b5c-9528-1f2379c86b71" />

Step 3: Perform SSH brute force attack from Kali

We will use Hydra to perform the brute force attack. Hydra is a popular and versatile password-cracking tool that supports various protocols for online attacks. Hydra supports a multitude of protocols, including SSH, FTP, HTTP, HTTPS, Telnet, and many more. This versatility allows security professionals to test various services and applications.

hydra -l <Username> -P <password_list.txt> <Ubuntu_Server_IP_Address> ssh

Visualize alerts
From the Wazuh interface we can visualize the alerts of the brute force attack.

<img width="1916" height="864" alt="Screenshot 2025-08-13 225101" src="https://github.com/user-attachments/assets/28f24fe1-2399-491a-9104-7f0408eb5b11" />

