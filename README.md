# SOAR and EDR Project 

## Summary
In this project we will configure a SOAR using Tines and LimaCharlie as the EDR tool. This project will show how to automate security workflows, and enhance your cybersecurity posture effectively. It will guide us through the configuration process and show how these tools work together to provide real-time security insights and responses.

### What is SOAR?
SOAR stands for Security Orchestration, Automation, and Response. It is a cybersecurity toolset that helps organizations manage security threats by automating incident response, orchestrating workflows across different tools, and providing centralized incident management. SOAR platforms enhance efficiency, reduce response times, and improve threat handling by automating repetitive tasks and providing actionable insights.

### What is EDR?
Endpoint Detection and Response is a cybersecurity solution designed to detect, investigate, and respond to threats on endpoints such as laptops, desktops, and servers. EDR solutions are a critical component of modern cybersecurity strategies, providing real-time monitoring and detailed visibility into endpoint activities.

### What is a Playbook?
A playbook is a predefined set of steps, actions, or workflows designed to guide security teams in responding to specific threats or incidents. It helps standardize responses, improve efficiency, and ensure consistency in handling security events. Playbooks often include automated processes in SOAR platforms to address scenarios like phishing, malware detection, or unauthorized access.

## System Requirements
We will create a Windows 10 VM as the endpoint for this project. The VM will be installed on VMware Workstation. Therefore minimum requirement for the host machine will be:

- RAM: 16GB 
- Disk Space: 60 GB free space. 
- The documentation to install Vmware Workstation is provided <a href="https://knowledge.broadcom.com/external/article/344595/downloading-and-installing-vmware-workst.html">here.</a>

## Logical Diagram
<img src="https://github.com/anandu106/soar_edr_project/blob/39f66e07ff2ab2bcb86e1b4b891c010b178685e4/Images/SOAR1.png" width="500">

## Steps
### Install Windows 10 in VMware

- Go to the Windows 10 download page here.
- Click Download Tool Now
- In Setup, select Create Installation Media, customize options and then select ISO file.
- Go to VMware. Click New Virtual Machine.
- Select Typical.
- Select Installer Disc Image file and add the downloaded Windows 10 iso file.
- Select Microsoft Windows as Guest Operating System.
- Name the Virtual Machine and select the location to store the VM files.
- Allocate 60GB size and select Split virtual disk into multiple files.
- Open the created VM and start Installing Windows.

### Install and Setup LimaCharlie

- Go to LimaCharlie website <a href="https://limacharlie.io/">here</a> and sign up with your preferred valid email.
- Answer the following questions when prompted and click "Get Started"
- Click "Create Organization" and fill the "Name", "Data Residency Region"
- Create an installation key as shown below. I have already created one called SOAR_EDR-Lab
  
<img src="https://github.com/anandu106/soar_edr_project/blob/d5bdd8234db702521249da998bc6e426125f6e48/Images/Install_key.png" width="750">

- Scroll down and download "Windows 64 bit" to the VM.
   
<img src="https://github.com/anandu106/soar_edr_project/blob/864839b925d3c514e8981a7898d62b5acbd10764/Images/Sensor_download.png" width="500">
