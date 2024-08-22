# Network-Analysis-Wireshark

In the first part of this project I will be analysing a .pcap file from a CTF(Capture The Flag) that I participated and the CTF is conducted by RedTeam Hacker Academy, Kochi. In the second part I will capture the network traffic between the Kali linux (attacker machine) and the metasploitable 2 machine (target machine) that has been configured from the previous project.


## Objective

This lab focuses on building skills in network analysis using Wireshark by capturing and analyzing traffic in a controlled environment. It aims to provide practical experience in understanding protocols, detecting security threats, and investigating network-based attacks, enhancing expertise in traffic inspection and network security monitoring.

### Skills Learned

- **Network Traffic Analysis:** Capture and analyze network traffic using Wireshark.
- **Protocol Understanding:** Study protocols like TCP/IP, HTTP, DNS, ARP, and more.
- **Traffic Filtering:** Apply Wireshark filters to isolate and focus on specific traffic types.
- **Attack Detection:** Identify network attacks such as ARP spoofing, brute-force attempts, and DoS.
- **Packet Inspection:** Examine packet details for anomalies or malicious behavior.
- **Report Generation:** Document findings with detailed analysis and visualizations.
- **Network Security Monitoring:** Monitor network traffic for potential threats and suspicious activity.

### Tools Used

- **Wireshark:** For capturing and analyzing network traffic.
- **Kali Linux:** For generating network traffic and simulating attacks.
- **Metasploitable 2:** A vulnerable virtual machine used as a target for traffic analysis.
- **tcpdump:** A command-line tool for capturing network packets before analyzing them in Wireshark.

## Steps
### Step 1: Download and open the .pcap file into wireshark
-What is Wireshark? 
  Wireshark is a free and open-source packet analyzer. It is used for network troubleshooting, analysis, software and communications protocol development, and education. It is in-built applcation in Kali Linux.
  For other Operating Systems use, https://www.wireshark.org/download.html
- Identity_Trail.pcap is the .pcap (Packet capture) that is to be analysed for Identifying the missing person name. It is uploaded in the files/upload section.
![Screenshot (349)](https://github.com/user-attachments/assets/a73c40ea-760b-4e92-9c3c-52c068d720d0)
Ref 1: Selecting .pcap file from terminal window

![Screenshot (350)](https://github.com/user-attachments/assets/957e3f63-4b45-49eb-aa06-e34584c45664)

Ref 2: Identity_Trail.pcap file is opened using Wiresark

## Step 2: Some Wireshark filters
 -To get desired results that we are looking for wireshark uses filters. By understanding of the TCP/IP or OSI conceptual communication model and ports and protocols, it is done. Every communication leaves the trace of network traffic.
 Some wireshark filters from the official documentation, https://www.wireshark.org/docs/man-pages/wireshark-filter.html

### Step 3: Find the identity trail 
  -One of the most common wireshark filter is 'tcp.port == 80' is to filter out only the tcp (transmission control protocol) with port 80 (port 80 is the default insecure port for http [Hyper tex transfer protocol] which insecure web communication that is not encrpted).
  #### A man-in-the-middle (MITM) attack is a form of cyberattack in which criminals exploiting weak web-based protocols insert themselves between entities in a communication channel to steal data. Estimates show that 35% of exploitation activity involves man-in-the-middle attacks.

-Look at the packet number 77, there is a hint, a conversation going on.
![Screenshot 2024-08-22 225648](https://github.com/user-attachments/assets/eee69fcf-a9b5-495a-bec1-f6b9609824ac)
Ref 3: Got a hint
 -Right click on the packet and then click on the 'Follow' option and then click on the 'TCP stream' option this procedure gives the similar output based on the packet number 77, which is very helpful scenarios like this.
 
 -The result is, got the complete conversation between the users. 
 ### The confidentiality of the CIA triad (Confidentiality, Integrity and Availability) is compromised here.

 ![Screenshot (352)](https://github.com/user-attachments/assets/1babfbab-c819-4a56-910c-6c3f55affda1)
 Ref 4: Got it !

 #### The CTF mission was to find the identity/name of the user. Name of the user is Sajith. 
The protocol that can be seen in the convsersation is Telent. TELNET stands for Teletype Network. It is a client/server application protocol that provides access to virtual terminals of remote systems on local area networks or the Internet. The local computer uses a telnet client program and the remote computers use a telnet server program. Telnet will use port 23 by default.

