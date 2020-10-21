# PRAC-6 
Aim: Configure NTP, Install and Configure NTP Server, Configure NTP Client.

• Description:

> NTP- (Port number - 123)
  NTP stands for Network Time Protocol, and it is an Internet protocol used to synchronize the clocks of computers to some time reference. 
  NTP is an Internet standard protocol.
  NTP time servers work within the TCP/IP suite and rely on User Datagram Protocol (UDP) port 123. 

> SNTP-
  SNTP (Simple Network Time Protocol) is basically also NTP,
  As a full implementation of the NTP protocol seemed too complicated for many systems, a simplified version of the protocol, namely SNTP had been defined.


> Should Time be synchronized?

  Time usually just advances. If you have communicating programs running on different computers, time still should even advance if you switch from one computer to another. 
  Obviously if one system is ahead of the others, the others are behind that particular one. From the perspective of an external observer, 
  switching between these systems would cause time to jump forward and back, a non-desirable effect.

  As a consequence, isolated networks may run their own wrong time, but as soon as you connect to the Internet, effects will be visible. 
  Just imagine some EMail message arrived five minutes before it was sent, and there even was a reply two minutes before the message was sent.


> FEATURES:

a. NTP needs some reference clock that defines the true time to operate. All clocks are set towards that true time.

b. NTP uses UTC as reference time.

c. NTP is a fault-tolerant protocol that will automatically select the best of several available time sources to synchronize to. 

d. NTP is highly scalable:- A synchronization network may consist of several reference clocks. 
   Each node of such a network can exchange time information either bidirectional or unidirectional. 

e. Having available several time sources, NTP can select the best candidates to build its estimate of the current time. 
   The protocol is highly accurate, using a resolution of less than a nanosecond (about 2^-32 seconds). 


• Steps and Commands:

1. We need update:
   rumpa@kali:~$ sudo apt update -y

2. To check kali version:
   rumpa@kali:~$ uname -a

3. Command to install NTP:
   rumpa@kali:~$ sudo apt install ntp

4. Command to install SNTP:
   rumpa@kali:~$ sudo apt install sntp

5. To check the version:
   rumpa@kali:~$ sudo sntp --version
   rumpa@kali:~$ cd /etc
   rumpa@kali:~$ ls -lrth *ntp.conf*

6. Then start the service: 
   rumpa@kali:~$ sudo systemctl start ntp

7. To check the status:
   rumpa@kali:~$ sudo systemctl status ntp

8. Now we need to configure NTP:
   rumpa@kali:~$ sudo vim /etc/ntp.conf

- [Refer Practical_Output Folder]
- After opening ntp.conf file scroll down and see-
  # You need to talk to an NTP server or two (or three)

- Below this line write:
  server localhost

9. To check the conf file:
   rumpa@kali:~$ cat ntp.conf

10. Then restart the service: 
    rumpa@kali:~$ sudo systemctl restart ntp

11. To check the status:
    rumpa@kali:~$ sudo systemctl status ntp

12. Now to query NTP and check it's connection:
    rumpa@kali:~$ sudo ntpq -p
