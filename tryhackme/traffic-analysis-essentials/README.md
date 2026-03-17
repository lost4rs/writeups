# Traffic Analysis Essentials 💻👓
## Introduction  
This room covers the foundations of Network Security and Traffic analysis and introduce the essential concepts of these disciplines.  
This room is structured in 4 tasks:  
**Task 1: Introduction**  
Overview of Network Security concepts.  
**Task 2: Network Security and Network Data**  
Theoretical background on data types and security layers.    
**Task 3: Traffic Analysis**  
Core theory and a hands-on simulator to identify threats and find flags.  
**Task 4: Conclusion**  
  
In this space, I will focus on **Task 3**.  

## Traffic Analysis  
Traffic Analysis is a method of intercepting, recording/monitoring, and analysing network data and communication patterns to detect and respond to system health issues, network anomalies, and threats. The network is a rich data source, so traffic analysis is useful for security and operational matters.  
  
There are two main techniques used in Traffic Analysis:  
* **Flow Analysis:** Collecting data/evidence from the networking devices. This type of analysis aims to provide statistical results through the data summary without applying in-depth packet-level investigation.  
 Easy to collect and analyse but it doesn't provide full packet details to get the root cause of a case.  
* **Packet Analysis:** Collecting all available network data. Applying in-depth packet-level investigation (often called Deep Packet Inspection (DPI)) to detect and block anomalous and malicious packets.  
 It provides full packet details to get the root cause of a case but requires time and skillset to analyse.  
  
## Finding the Flags  
Now, it's time to find the flags!  
I opened the static site that simulate a traffic analysis operation and find the flags.  
The simulator uses the IDS/IPS (Intrusion Detection/Prevention System) control panel.  
This tool is crucial for filtering noise and focusing on events that match known attack signatures or policy violations.  
  
### Level 1: Identifying Malicious IPs  
Upon starting the simulation, we can observe the real-time packet flow.  
  
<img width="540" height="400" alt="image" src="https://github.com/user-attachments/assets/2bf95b49-d15b-409d-9f5f-003a73474bc9" />
  
A permissive network configuration was identified, Two IP addresses were generating malicious traffic (marked by red dots): 10.10.99.99 and 10.10.99.62.  
By applying filters in the IDS/IPS panel to block these IPs, the attack was mitigated and we can see it in the following image:     
  
<img width="594" height="450" alt="image" src="https://github.com/user-attachments/assets/b1919a0c-cb7f-4f92-af91-3cf70ed6dcec" />
  
Succesfull! The bad traffic was stopped and the first flag was revealed: **THM{P----_M-----}.**  
  
### Level 2: Identifying Malicious Ports
In the next challenge, the goal was to identify and block three specific destination ports based on the alert tables:  
  
<img width="637" height="245" alt="image" src="https://github.com/user-attachments/assets/2a697d74-4a51-4389-ab83-454237b881f4" />
  
1. **Port 4444:** Identified as **Metasploit Traffic**. This is the default port for reverse shells, allowing attackers to control a compromised system.  
2. **Port 7777:** Flagged as **Bad Traffic** (often associated with unauthorized applications).  
3. **Port 2222:** Identified as **Suspicious ARP Behaviour**. This is commonly a non-standard port, often used to bypass security controls.  
  
  <img width="578" height="425" alt="image" src="https://github.com/user-attachments/assets/dafdf40c-137d-48e3-b2b0-d233e51750f5" />

After filtering these ports in the firewall, the analysis was successful, revealing the second flag: **THM{D--------_M-----}.** 
  
## Conclusions: Lessons Learned
* The flags were obtained through an **active mitigation process**. Simply identifying the threats was not enough; it was necessary to implement firewall rules to block the specific IPs and ports. Once the system validated that the security posture was correct, the data was revealed.  
* This room reinforced my basic knowledge of Network Security and provided a practical perspective on how an analyst interacts with IDS/IPS systems to protect an infrastructure.    
