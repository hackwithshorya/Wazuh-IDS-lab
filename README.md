# Wazuh-IDS-lab
Intrusion detection and active response

Project Description

This project demonstrates the endpoint detection and response (EDR) capabilities of Wazuh, an open-source security monitoring platform. The Wazuh server and dashboard are installed on Kali Linux (VMware), while a Wazuh agent is deployed on Ubuntu (VMware) to monitor system activities.
To test the setup, a Hydra brute force attack is launched from Kali against the Ubuntu machine, and Wazuh successfully detects the intrusion attempts in real time.

Setup

1- Setting up Ubuntu on VMware
Ubuntu will act as the agent machine in our project. First, we need to install Ubuntu on VMware.
Steps:
1. Download Ubuntu ISO
  Download the Ubuntu Desktop ISO 
  👉 https://ubuntu.com/download/desktop/thank-you?version=24.04.3&architecture=amd64&lts=true

2.Open VMware Workstation / Player
 - Click on Create a New Virtual Machine.
 - Select Installer disc image (ISO) and browse the downloaded Ubuntu ISO.

 3.Configure VM Settings
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

Install VMware Tools (for smooth clipboard & resolution).
✅ Now Ubuntu is ready as the agent machine, where we will install the Wazuh agent later.

