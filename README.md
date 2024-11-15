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

- Once created copy the installation key. 
- Scroll down and download "Windows 64 bit" to the VM.
   
<img src="https://github.com/anandu106/soar_edr_project/blob/864839b925d3c514e8981a7898d62b5acbd10764/Images/Sensor_download.png" width="250">

- In the VM, open Powershell as administrator and navigate to the directory where above mentioned file was downloaded to
- Type ".\{downloaded file name} -i {copied installation key}" and hit enter
- If done correctly you should see whats shown below

<img src="https://github.com/anandu106/soar_edr_project/blob/90e4a888b7edee23e428b2a123632c449479bda8/Images/Lima_success.png" width="250">

- You should also see the device under the Sensors List.
  
<img src="https://github.com/anandu106/soar_edr_project/blob/2c6bcfd1bcd6ccdb075ffa25a4d29bd358f59db4/Images/Sensors_list1.png" width="750">

### Generate Telemetry 

- Download the Lazagne executable to the VM from <a href="https://github.com/AlessandroZ/LaZagne/releases/tag/v2.4.6">here.</a> Make sure Real-time Protection is switched off in Windows Security.
- Run the executable from Powershell
- In LimaCharlie, under Timeline yyou can see the event captured from the VM.

<img src="https://github.com/anandu106/soar_edr_project/blob/de5dd38e761a24ac0819467cb593d752daf65123/Images/timeline.png" width="750"> 

### Create Detection and Response rule

- Go to D&R Rules under Automation Tab and click on "New Rule"

<img src="https://github.com/anandu106/soar_edr_project/blob/7b0081dc2bfa667c799d13d592fd8f8bd7ec0d9a/Images/new_rule.png" width="750">

- To create this specific rule type the following information in the Detect and Response field as shown below. Make sure to copy the hash value from the event generated. And click "Save Rule"

<img src="https://github.com/anandu106/soar_edr_project/blob/16eda4f5cac2c02abf4c53b9bf96dc75e5f8e5a3/Images/rule.png" width="500">

- Run the Lazagne executable again on the VM and this time the detection should capture it.

<img src="https://github.com/anandu106/soar_edr_project/blob/06571eec98461d9da95e876ca097eee5778691b2/Images/detection1.png" width="750">  

### Setup Tines

- Create an account on <a href="https://www.tines.com/">Tines</a> with a valid email.
- Playbook, in Tines is called as "Story"
- Create a Story using Webhook, Trigger, HTTP Request and Send Email. For a detailed explanation, refer <a href="https://www.youtube.com/watch?v=RR4tfMMkIPY">here</a>
- Finally when the playbook is created it should look something like this.......




https://github.com/user-attachments/assets/0861fc39-1169-4662-886a-bf65b11d7d7e

