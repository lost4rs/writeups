# Traffic Analysis Essentials 💻👓
## Introduction  
This room covers the foundations of Network Security and Traffic analysis and introduce the essential concepts of these disciplines.  
This room is structured in 4 tasks:  
**Task 1: Introduction**  
Introduced the room and a little explain about Network Security.  
**Task 2: Network Security and Network Data**  
Theory about these two topics.  
**Task 3: Traffic Analysis**  
Theory about this topic and a simulator of traffic operation with a challenge to find the flags.  
**Task 4: Conclusion**  
  
In this space, I will focus about **Task 3**.  

## Traffic Analysis  
Traffic Analysis is a method of intercepting, recording/monitoring, and analysing network data and communication patterns to detect and respond to system health issues, network anomalies, and threats. The network is a rich data source, so traffic analysis is useful for security and operational matters.  
  
There are two main techniques used in Traffic Analysis:  
* **Flow Analysis:** Collecting data/evidence from the networking devices. This type of analysis aims to provide statistical results through the data summary without applying in-depth packet-level investigation.  
 Easy to collect and analyse but it doesn't provide full packet details to get the root cause of a case.  
* **Packet Analysis:** Collecting all available network data. Applying in-depth packet-level investigation (often called Deep Packet Inspection (DPI)) to detect and block anomalous and malicious packets.  
 It provides full packet details to get the root cause of a casebut equires time and skillset to analyse.  
  
Now, it's time to find the flags!  
I opened the static site to simulate a traffic analysis operation and find the flags.  
Once the simulation starts, we can see the packets traffic 

  
<img width="540" height="400" alt="image" src="https://github.com/user-attachments/assets/2bf95b49-d15b-409d-9f5f-003a73474bc9" />
  
I realized that there were two IP addresses that were sending bad traffic (identified by red dots): 10.10.99.99 and 10.10.99.62, so I filtered them with the IDS/IPS filter:     
  
<img width="594" height="450" alt="image" src="https://github.com/user-attachments/assets/b1919a0c-cb7f-4f92-af91-3cf70ed6dcec" />
  
Succesfull! The bad traffic was stopped and I found out the first flag: **THM{P----_M-----}.**  
We move on to the next challenge. This time, instead of identifying IP addresses, I had to select 3 destination ports to block the malicious packets.  
We have 2 tables that will help us identify the correct ports:  
  
<img width="637" height="245" alt="image" src="https://github.com/user-attachments/assets/2a697d74-4a51-4389-ab83-454237b881f4" />
  
1. Port 4444
We can easily identify the *Metasploit Traffic*, which has the port 4444. 
This port allows remote attackers to conduct cross-protocol scripting attacks. So this port needs to be blocked.  
2. Port 7777
This port allows *Bad Traffic*, so I decided to block it.
3. Port 2222
   Since it's important to stop *Suspicious ARP Beahviour*, the port 2222 needs to be blocked.  
Then, I filtered this ports:
  
  <img width="578" height="425" alt="image" src="https://github.com/user-attachments/assets/dafdf40c-137d-48e3-b2b0-d233e51750f5" />

The analysis was okay! So I found out the second flag: **THM{D--------_M-----}.** 
  
## Conclusions: Leasons Learned
This room reinforced my basic knowledge of Network Security and I discovered the world of Traffic Analysis with a very didactic simulator.  


