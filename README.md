# SIEM-Honeypot-Lab-Using-Azure
## 1. Introduction
The goal of this project is to create a honeypot in the Azure cloud environment and observe live attacks from around the world. As the honeypot we will use a virtual machine and log any interesting data using a Log Analytics Workspace. Then finally we will use Azre Sentinel to visualize the oncoming attacks.

## 2. Creating the Virtual Machine
First we will need to setup a virtual machine to act as the honeypot

### 2.1 Basics 

![image](https://github.com/m1k4x00/SIEM-Honeypot-Lab-Using-Azure/assets/142576207/94a34509-a361-4ee5-b6c9-6d100bce4296)


### 2.2 Networking
We want to allow all inbound traffic on all ports so we create a new security group, delete any existing rules and create our new rule.

![image](https://github.com/m1k4x00/SIEM-Honeypot-Lab-Using-Azure/assets/142576207/a8bb350a-3228-4352-918c-b5cdb1c191c2)


## 3. Creating the Log Analytics Wrokspace

![image](https://github.com/m1k4x00/SIEM-Honeypot-Lab-Using-Azure/assets/142576207/2d5a94fe-4d93-41c1-919b-522104cb2464)


## 4. Enabling Log Gathering in Microsoft Denfedner for Cloud

## 4.1 Turning on Servers

![image](https://github.com/m1k4x00/SIEM-Honeypot-Lab-Using-Azure/assets/142576207/3c810335-8c71-43b0-a48e-961da5ff01c1)


## 4.2 Turning on Data Collection
We want to log all events in this case.

![image](https://github.com/m1k4x00/SIEM-Honeypot-Lab-Using-Azure/assets/142576207/9431e758-7c39-47b2-aa90-c19af86ea1fb)


## 5. Connecting Log Analytics to the Virtual Machine
Pressing connect will connect the VM to the workspace

![image](https://github.com/m1k4x00/SIEM-Honeypot-Lab-Using-Azure/assets/142576207/c084cc90-85a5-46d6-b7aa-5aa6d135411b)


## 6. Setting up Azure Sentinal
Adding Sentinel to the workspace

![image](https://github.com/m1k4x00/SIEM-Honeypot-Lab-Using-Azure/assets/142576207/634b6d57-d8b7-436a-b41b-ce9e3d268de7)


## 7. Connecting to the VM Using Remote Desktop
We will connect to the virtual machine via Windows RDP using the credentials set up in chapter 2.1 with the ip found in the Virtual Machines tab

## 8. Turning Off the Firewall
We turn off domain, public and private firewalls since we want the adveseries to be able to attack our virtual machine.
![image](https://github.com/m1k4x00/SIEM-Honeypot-Lab-Using-Azure/assets/142576207/ed480b51-10b1-43e0-b9ce-c65593877adc)


## 9. Exporting logs
To export the logs from Windwos Event Viewer we will use the Log_Exporter.ps1 powershell script. The script filters through the Windows Event Viewer logs and picks all the failed RDP logins and feeds the ip to the ipgeolocation api. The API gives us the geolocation of the attacker (Latitude, Longitude, State, Country).

## 10. Adding Custom Log to the Workspace
First we transfer the log file created by the powershell script from the VM and then add it to the log file prompt. 

![image](https://github.com/m1k4x00/SIEM-Honeypot-Lab-Using-Azure/assets/142576207/242bf813-6a95-4057-ace0-d50f668b0631)


## 11. Extracting Fields from Raw Logs
Now we can see that Custom Log works

![image](https://github.com/m1k4x00/SIEM-Honeypot-Lab-Using-Azure/assets/142576207/a9b5f261-cf88-43c9-84d9-7722bf15fa7d)


Now we need to parse the data as follows
![image](https://github.com/m1k4x00/SIEM-Honeypot-Lab-Using-Azure/assets/142576207/ff152367-ab8a-4870-afeb-282e9a05360d)


## 12. Adding a Query to Sentinel and Creating the World map
We select map from the visualization tab and configure the settings accordingly. 

![image](https://github.com/m1k4x00/SIEM-Honeypot-Lab-Using-Azure/assets/142576207/0c387161-aa55-4d68-a939-94e71b4215c2)


Now we can see the map.

## 13. Results
![image](https://github.com/m1k4x00/SIEM-Honeypot-Lab-Using-Azure/assets/142576207/2650e015-c9c0-49a8-8a4d-a840af5a569e)


Here we can see that a brute force rdp login attempt was attempted from Mexico. There also seems to be a lone password spray attack from the United Kindom. Because of the use of VPNs and proxies we can't be sure where these attacks are administered from. If we wanted to analyze different attacks we could run the script longer.


