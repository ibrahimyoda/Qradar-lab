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
Virtual scanner installation and personalization: <br/>
<img width="690" alt="importing the ova file 2" src="https://github.com/ibrahimyoda/Qualys-vulnerability-scanning-lab/assets/119984086/d8dcc7e7-da5c-4b04-bad9-950db8b4d9a6"/>
<br />
<br />
<img <img width="578" alt="personalization code " src="https://github.com/ibrahimyoda/Qualys-vulnerability-scanning-lab/assets/119984086/ff803d0e-35b7-456b-b53c-e737dc5edfe3"/>
<br />
<br/>
<img width="395" alt="pinguins" src="https://github.com/ibrahimyoda/Qualys-vulnerability-scanning-lab/assets/119984086/3a3cc431-0ee2-4072-a579-0a9bd84a3492"/>
<br />
<br/>
<img width="405" alt="personnalization code" src="https://github.com/ibrahimyoda/Qualys-vulnerability-scanning-lab/assets/119984086/ce3b9d45-c25d-43f5-bf4f-c6ead67d4c85"/>
<br />
<br />
<br/>
<img width="405" alt="personnalization code entered" src="https://github.com/ibrahimyoda/Qualys-vulnerability-scanning-lab/assets/119984086/aa329c7a-c207-4762-ab6f-0bd7fb83a1c6"/>
<br />
<br />
<br/>
<img width="404" alt="qualys virtual scanner IP" src="https://github.com/ibrahimyoda/Qualys-vulnerability-scanning-lab/assets/119984086/70a6def4-a272-4a2a-99a4-8f8c091a7d39"/>
<br />
<br />
<img width="1246" alt="appliance is ready" src="https://github.com/ibrahimyoda/Qualys-vulnerability-scanning-lab/assets/119984086/525cbe3a-4dd8-4bae-a9e8-e98cf7e2144d"/>
<br />
<br />
Qualys virtual scanner in virtualbox : <br/>
<img width="635" alt="redhat virtual scanner and windows box" src="https://github.com/ibrahimyoda/Qualys-vulnerability-scanning-lab/assets/119984086/898f656e-d624-4640-a3d9-4806e1095959"/>
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
