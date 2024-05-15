# README

This code does not promote or encourage any illegal activities. The content in this document is provided solely for
educational purposes and to create awareness.

# Set remote/local proxy server

This script automates the setup of a remote proxy for Man-in-the-Middle (MITM) attacks on Windows systems. It has been tested on Windows 10 and Windows 11. The script performs the following tasks:

1. Starts Windows Terminal as an administrator.
2. Downloads and installs the Burp Suite CA certificate. (Or other proxy CA))
3. Configures the system proxy to use a specified remote proxy server.
4. Cleans up by terminating all active Windows Terminal and PowerShell processes.

Requirements:

- CA Root certificate for your proxy sever and remote webserver to download it
- A remote or local forward proxy server like Burpsuite to intercept traffic

## 1- ducky script and execute

When your proxy server is running and the CA can be downloaedd change the variables in the script:

- LINE 28 === Webserver
  Change "http://yourwebserver/ca.der" to your own webserver where the certificate can be obtained.
- LINE 48 === Proxyserver
  Change "your.proxy.server:port" to your own remote of local IP-address where the proxy server is listening and add the tcp port.

When the payload executed you can remotely sniff unencrypted traffic and interceps passwords or session cookies to bypass MFA.
