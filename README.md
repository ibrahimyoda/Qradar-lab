<h1>Qradar siem installation and logs transfer</h1>

<h2>Description</h2>
This lab consists of installing a Qradar siem in virtualbox and setting up logs transfer from kali linux and windows clients.
<br />

<h2>Environments Used </h2>

- <b>Windows 11 </b> 
- <b>linux redhat</b>
- <b>kali linux</b>
- <b>Qradar platform(console)</b> 

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
First issue arised after running ./setup script. Qradar failed insatlling.After inspecting the issue we found out it was the dhcp failing to attribute an ipv4 to the qradar box.We had to manually configure the qradar box ipv4 using th the network management text user interface (nmtui command) and set the ipv4 192.168.1.18 to the qradar box </br>

<img width="359" alt="ipv4 issue" src="https://github.com/ibrahimyoda/Qradar-lab/assets/119984086/e08d9f52-8198-4d7f-a186-5e20c87013a4">
<br />
<br/>
<img width="362" alt="static ip adrress 192 168 1 18" src="https://github.com/ibrahimyoda/Qradar-lab/assets/119984086/11ccebf8-cf8c-4599-b103-3b7a15b7540f">
<br />
<br />
<br/>
<img width="1271" alt="7 qradar dashboard" src="https://github.com/ibrahimyoda/Qradar-lab/assets/119984086/167c3d5c-5dbb-4d27-a0e9-e0f81e37cb27">
<br />
<br />
Setting up logs forwarding from kali linux 192.168.1.67 to Qradar 192.168.1.18.Rsyslog was not installed so we had to do that first running these commands 
sudo apt-get update & sudo apt-get -y install rsyslog and then edit /etc/rsyslog.conf to add the Qradar server ip address 192.168.1.18 to send all the kali linux logs.After restarting the rsyslog service with the next command service rsyslog restart the logs should have started being sent to qradar and it wasn't the case.I've investaigated the issue ans found out that qradar community edition had a license issue that neede to be troubleshoot with a command provided by ibm.I had to ssh into the qradar box then run the command and wait 5 minutes but before all this i also had to troubleshoot my ssh connection because it was failing and i needed to reset the password for it to work again so its really important to mention it. Unfortunately logs transfer was still failing and i had to manually add the linux client to the Qradar platform log sources before seing some success. </br>
<img width="288" alt="rsyslog conf file" src="https://github.com/ibrahimyoda/Qradar-lab/assets/119984086/f0a6698a-30fb-41ce-8fef-da23da6c1744">
<br />
<br />
<img width="912" alt="log sources" src="https://github.com/ibrahimyoda/Qradar-lab/assets/119984086/a3e0e371-7b3a-4d70-8af3-0f8b1684da56">
<br />
<br />
Qradar log activity : <br/>
<img width="1262" alt="qradar-logs" src="https://github.com/ibrahimyoda/Qradar-lab/assets/119984086/99fcbbd3-21b9-4624-952c-60cad85f949d">
<br/>
<br/> 
Virtual scanner appliance configuration in cloud platform: <br/>
<img width="1130" alt="ip for scanning" src="https://github.com/ibrahimyoda/Qualys-vulnerability-scanning-lab/assets/119984086/ffde1eb4-a0b8-4fb9-877a-294824dbd810"/>
<br />
<br />
<img width="1124" alt="assets added " src="https://github.com/ibrahimyoda/Qualys-vulnerability-scanning-lab/assets/119984086/753ff578-faa7-4091-8208-cdb2af15a06b"/>
<br />
<br/>
<img width="748" alt="option profile" src="https://github.com/ibrahimyoda/Qualys-vulnerability-scanning-lab/assets/119984086/c7efd33b-6942-4b7a-b45f-9ca192979475"/>
<br/>
<br/>
<img width="745" alt="box to be scanned" src="https://github.com/ibrahimyoda/Qualys-vulnerability-scanning-lab/assets/119984086/fd211e7b-8dba-4a2b-812b-f592c33ade67"/>
<br />
<br />
Windows box installation and configuration: <br/>
<img width="635" alt="redhat virtual scanner and windows box" src="https://github.com/ibrahimyoda/Qualys-vulnerability-scanning-lab/assets/119984086/05487f86-1f5e-4aef-98e0-d4ccfa58a613"/>
<br />
<br />
<img width="517" alt="install old version of firefox abd vlc on windows" src="https://github.com/ibrahimyoda/Qualys-vulnerability-scanning-lab/assets/119984086/a4437926-8f38-4602-9a13-e83bc51e327c"/>
<br />
<br />
Setting up static ip address 192.168.1.17 on windows 10 box: <br/>
<img width="514" alt="static ip setting " src="https://github.com/ibrahimyoda/Qualys-vulnerability-scanning-lab/assets/119984086/f8193bde-cd95-4652-9409-afca3210812b"/>
<br />
<br />
Turning off firewall on windows 10 box: <br/>
<img width="509" alt="firewall off" src="https://github.com/ibrahimyoda/Qualys-vulnerability-scanning-lab/assets/119984086/a510c9bd-3109-4847-90d5-3b46228c8438"/>
<br />
<br />
Running an unautheticated scan on the windows(Ip.addr = box 192.168.1.17): <br/>
<img width="931" alt="qualys undcerdential scan" src="https://github.com/ibrahimyoda/Qualys-vulnerability-scanning-lab/assets/119984086/fd942568-3762-40d4-a510-60c1001acba4"/>
<br />
<br />
Scan result: <br/>
<img width="611" alt="scan result screenshot" src="https://github.com/ibrahimyoda/Qualys-vulnerability-scanning-lab/assets/119984086/405c18fd-632d-4f0f-b2bd-5ffaa0652d2f"/>
<br />
<br />
Setting up remote access on windows box: <br/>
<img width="516" alt="dword value set to 1 " src="https://github.com/ibrahimyoda/Qualys-vulnerability-scanning-lab/assets/119984086/13721a4a-705d-437c-917e-3343dc13b234"/>
<br />
<br />
Setting up authentication for windows 10 in qualys cloud plaform: <br/>
<img width="754" alt="authentication info configuration" src="https://github.com/ibrahimyoda/Qualys-vulnerability-scanning-lab/assets/119984086/ef60ac86-dd86-46f5-b1eb-cbe2bc96c59f"/>
<br />
<br />
<img width="908" alt="authentication display page" src="https://github.com/ibrahimyoda/Qualys-vulnerability-scanning-lab/assets/119984086/4e5b1eab-f3de-4824-a3cc-66af78169bcb"/>
<br />
<br />
Authenticated scan: <br/>
<img width="926" alt="scans result page" src="https://github.com/ibrahimyoda/Qualys-vulnerability-scanning-lab/assets/119984086/b85084e4-52d3-4597-96dd-c32127f84a96"/>
<br />
<br />
Scan restult: <br/>
<"/>
<br />
<br />


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
