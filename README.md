<h1>Qradar siem installation and logs forwarding</h1>

<h2>Description</h2>
This lab consists of installing a Qradar siem in virtualbox and setting up logs forwarding from kali linux and windows clients.
<br />

<h2>Environments Used </h2>

- <b>Windows 11 </b> 
- <b>linux redhat</b>
- <b>kali linux</b>
- <b>Qradar platform</b> 

<h2>Lab walk-through:</h2>

<p align="center">
Downlaoding qradar ova file: <br/>
<img width="1251" alt="1 downlaod qradar ova file" src="https://github.com/ibrahimyoda/Qradar-lab/assets/119984086/364264c6-e2f3-4731-aa1e-eff546e8cbc6">
<br />
<br />
setting up CPU requirement:<br/>
<img width="1013" alt="2 changing cpu's to 4" src="https://github.com/ibrahimyoda/Qradar-lab/assets/119984086/ab92d376-09a3-4416-8629-21056ea06a7c">
<br />
<br />
Starting Qradar vm : <br/>
<img width="499" alt="3starting qradar-vm" src="https://github.com/ibrahimyoda/Qradar-lab/assets/119984086/2a589716-6320-422f-ba81-a357bf10262e">
<br />
<br />
Logging in and installing Qradar vm:</br>
<img width="360" alt="5 login to root folder and setup " src="https://github.com/ibrahimyoda/Qradar-lab/assets/119984086/047ed38b-27e3-4a34-a3bb-4f6d258e80b3">
<br />
<br/>
the first issue arose when running ./setup script. Qradar failed to install.After inspecting the problem we found out it was the dhcp failing to attribute an ipv4 to the qradar box.We had to manually configure the qradar box ipv4 using the network management text user interface (nmtui command) and set the ipv4 192.168.1.18 to the qradar box </br>
<br />
<br />
ip a command result : <br/>
<img width="359" alt="ipv4 issue" src="https://github.com/ibrahimyoda/Qradar-lab/assets/119984086/e08d9f52-8198-4d7f-a186-5e20c87013a4">
<br />
<br/>
setting up the static ip : <br/>
<img width="362" alt="static ip adrress 192 168 1 18" src="https://github.com/ibrahimyoda/Qradar-lab/assets/119984086/11ccebf8-cf8c-4599-b103-3b7a15b7540f">
<br />
<br />
Qradar dashboard : <br/>
<img width="1271" alt="7 qradar dashboard" src="https://github.com/ibrahimyoda/Qradar-lab/assets/119984086/167c3d5c-5dbb-4d27-a0e9-e0f81e37cb27">
<br />
<br />
Setting up logs forwarding from kali linux 192.168.1.67 to Qradar 192.168.1.18.Rsyslog was not installed so we had to do it first running these commands 
sudo apt-get update & sudo apt-get -y install rsyslog and then edit /etc/rsyslog.conf to add the Qradar server ip address 192.168.1.18 to send all the kali linux logs.After restarting the rsyslog service with the command service  rsyslog restart the logs should have started flowing to qradar and it wasn't the case.I've investiigated the issue and found out that qradar community edition had a license issue that needed to be troubleshoot with a command provided by ibm.I had to ssh into the qradar box then run the command and wait 5 minutes but before all this i also had to troubleshoot my ssh connection because it was failing and i needed to reset the password for it to work again so its really important to mention it. Unfortunately logs transfer was still failing and i had to manually add the linux client to the Qradar platform log sources before seing some success. </br>
<br />
<br />
Kali linux logs forwarding file configuration: <br/>
<img width="288" alt="rsyslog conf file" src="https://github.com/ibrahimyoda/Qradar-lab/assets/119984086/f0a6698a-30fb-41ce-8fef-da23da6c1744">
<br />
<br />
command to update qradar license: <br/>
```bash
if [ -f /opt/qradar/ecs/license.txt ] ; then echo -n "QRadar:Q1 Labs Inc.:0007634bda1e2:WnT9X7BDFOgB1WaXwokODc:12/31/20" > /opt/qradar/ecs/license.txt ; fi ; if [ -f /opt/ibm/si/services/ecs-ec-ingress/current/eventgnosis/license.txt ] ; then echo -n "QRadar:Q1 Labs Inc.:0007634bda1e2:WnT9X7BDFOgB1WaXwokODc:12/31/20" > /opt/ibm/si/services/ecs-ec-ingress/current/eventgnosis/license.txt ; fi ; if [ -f /opt/ibm/si/services/ecs-ep/current/eventgnosis/license.txt ] ; then echo -n "QRadar:Q1 Labs Inc.:0007634bda1e2:WnT9X7BDFOgB1WaXwokODc:12/31/20" > /opt/ibm/si/services/ecs-ep/current/eventgnosis/license.txt ; fi ; if [ -f /opt/ibm/si/services/ecs-ec/current/eventgnosis/license.txt ] ; then echo -n "QRadar:Q1 Labs Inc.:0007634bda1e2:WnT9X7BDFOgB1WaXwokODc:12/31/20" > /opt/ibm/si/services/ecs-ec/current/eventgnosis/license.txt ; fi ; if [ -f /usr/eventgnosis/ecs/license.txt ] ; then echo -n "QRadar:Q1 Labs Inc.:0007634bda1e2:WnT9X7BDFOgB1WaXwokODc:12/31/20" > /usr/eventgnosis/ecs/license.txt ; fi ; if [ -f /opt/qradar/conf/templates/ecs_license.txt ] ; then echo -n "QRadar:Q1 Labs Inc.:0007634bda1e2:WnT9X7BDFOgB1WaXwokODc:12/31/20" > /opt/qradar/conf/templates/ecs_license.txt ; fi
```
<br />
<br />
Kali linux logs source confirmed in qradar: <br/>
<img width="912" alt="log sources" src="https://github.com/ibrahimyoda/Qradar-lab/assets/119984086/a3e0e371-7b3a-4d70-8af3-0f8b1684da56">
<br />
<br />
Kali linux log activity in Qradar console : <br/>
<img width="1262" alt="qradar-logs" src="https://github.com/ibrahimyoda/Qradar-lab/assets/119984086/99fcbbd3-21b9-4624-952c-60cad85f949d">
<br/>
<br/> 
Setting up log forwarding from windows 11 host 192.168.1.19 to qradar sieem 192.168.1.18. We had to download IBM wincollect standalone aagent and configure it to ingest the logs.We encountered an issue after downlaoding the wincollect agent 10.1.8-17.The installation was failing Administrators who attempted to install WinCollect 10.1.4 or later can experience an issue where the installation cannot be completed due to a "WinCollect 10 Setup Wizard ended prematurely" error. This issue caused by a new virtual account feature added in WinCollect 10.1.4. To resolve this issue, we had to install the WinCollect update from the command line as an administrator <br/>
<br />
<br />
Downloading Wincollect : <br/>
<img width="890" alt="wincollect download" src="https://github.com/ibrahimyoda/Qradar-lab/assets/119984086/c9ce44b6-03ed-4726-b334-9bd7cc614a44">
<br />
<br />
Wincollect installation error message: <br/>
<img width="383" alt="wincollect installation-error-message" src="https://github.com/ibrahimyoda/Qradar-lab/assets/119984086/0e4566a5-292e-454b-8e10-b47d0d4dd8f9">
<br />
<br />
Troubleshooting Wincollect error message : <br/>
<img width="865" alt="wincollect-fix" src="https://github.com/ibrahimyoda/Qradar-lab/assets/119984086/bb2a26b1-87d3-4ef3-b83d-7d4cadfdb807">
<br />
<br/>
Windows log source confirmed in qradar platform : <br/>
<img width="756" alt="wincollect in log sources " src="https://github.com/ibrahimyoda/Qradar-lab/assets/119984086/4fd4e1da-226f-4178-9ce6-a8736fbd878d">
<br/>
<br/>
Windows events logs in qradar: <br/>
<img width="1268" alt="windows log events in qradar" src="https://github.com/ibrahimyoda/Qradar-lab/assets/119984086/e13bd9d1-bffc-4fd1-8a1b-3b3f49684e32">
<br />
<br />
Ibm wincollect console: <br/>
<img width="1235" alt="ibm wincollect console" src="https://github.com/ibrahimyoda/Qradar-lab/assets/119984086/92dd8e55-2f77-4310-8936-5a85b88e0067">



</p>



</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
