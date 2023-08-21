# SIEM-Lab-Using-Azure-Sentiel
## 1. Introduction
The goal of this project is to create a honeypot in the Azure cloud environment and observe live attacks from around the world. As the honeypot we will use a virtual machine and log any interesting data using a Log Analytics Workspace. Then finally we will use Azre Sentinel to visualize the oncoming attacks.

## 2. Creating the Virtual Machine
First we will need to setup a virtual machine to act as the honeypot

### 2.1 Basics 

![image](https://github.com/m1k4x00/SIEM-Lab-Using-Azure-Sentiel/assets/142576207/3474fb5f-58de-42e8-8b3c-64cc6bb02c14)

### 2.2 Networking
We want to allow all inbound traffic on all ports so we create a new security group, delete any existing rules and create our new rule.

![image](https://github.com/m1k4x00/SIEM-Lab-Using-Azure-Sentiel/assets/142576207/67921d5a-8617-4c53-86bb-ef08efebeffc)

## 3. Creating the Log Analytics Wrokspace

![image](https://github.com/m1k4x00/SIEM-Lab-Using-Azure-Sentiel/assets/142576207/3415eff6-fdb3-43a1-9a83-ec8732af548f)

## 4. Enabling Log Gathering in Microsoft Denfedner for Cloud

## 4.1 Turning on Servers

![image](https://github.com/m1k4x00/SIEM-Lab-Using-Azure-Sentiel/assets/142576207/65f322a3-4cc4-44de-a3bc-229d3de8013a)

## 4.2 Turning on Data Collection
We want to log all events in this case.

![image](https://github.com/m1k4x00/SIEM-Lab-Using-Azure-Sentiel/assets/142576207/dc70e036-fdd7-46c2-8bba-6a4dab004500)

## 5. Connecting Log Analytics to the Virtual Machine
Pressing connect will connect the VM to the workspace

![image](https://github.com/m1k4x00/SIEM-Lab-Using-Azure-Sentiel/assets/142576207/98cd458d-69f8-494e-bbf4-050aefc678d5)

## 6. Setting up Azure Sentinal
Adding Sentinel to the workspace

![image](https://github.com/m1k4x00/SIEM-Lab-Using-Azure-Sentiel/assets/142576207/71302c6b-09b8-4284-9228-baa73bb6048b)

## 7. Connecting to the VM Using Remote Desktop
We will connect to the virtual machine via Windows RDP using the credentials set up in chapter 2.1 with the ip found in the Virtual Machines tab

## 8. Turning Off the Firewall
We turn off domain, public and private firewalls
![image](https://github.com/m1k4x00/SIEM-Lab-Using-Azure-Sentiel/assets/142576207/05a4091f-50ad-41f8-8bdb-e18531a18b1b)

