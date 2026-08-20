Healthcare Infrastructure Security & Threat Response

A Security Operations Center (SOC) project focused on strengthening the cybersecurity posture of MediCore Health Systems through network segmentation, firewall enforcement, threat simulation, and continuous security monitoring. The project uses a simulated healthcare environment to identify suspicious activity, reduce lateral movement, improve visibility, and protect sensitive Electronic Health Record (EHR) systems and other critical assets.

Table of Contents

Project Overview
Network Topology
Tools and Technologies
Configuration Steps
Results and Findings
Author


Project Overview
The purpose of this project was to design and implement a more secure healthcare network for MediCore Health Systems after identifying security concerns related to insufficient network segmentation, suspicious internal traffic, and limited monitoring capabilities.

The project simulated the responsibilities of a SOC analyst by:

Designing a segmented WAN, LAN, and DMZ network architecture
Isolating the public-facing patient portal from internal clinical systems
Configuring pfSense firewall rules and access controls
Simulating reconnaissance, unauthorised access attempts, and lateral movement using Kali Linux
Capturing and analysing network traffic with Wireshark
Deploying Wazuh on an Ubuntu Server for centralised security monitoring and alerting
Analysing firewall logs, security events, and packet captures to evaluate the effectiveness of the implemented controls.

The overall goal was to improve threat detection, reduce unnecessary communication between network zones, limit unauthorised access, and strengthen the protection of sensitive healthcare information.

Network Topology

The simulated infrastructure was built around a segmented network architecture consisting of WAN, LAN, and DMZ zones, with pfSense acting as the central firewall and router.

WAN / Internet: 192.168.110.0/24
LAN: 192.168.120.0/24
Clinical staff workstations
Administrative workstations
SOC workstation
Wazuh Server
Medical Devices (IoMT)
Internal clinical resources

DMZ: 192.168.130.0/24
Patient portal
Telehealth server

Security Layer:
pfSense Firewall

Attacker Environment:
Kali Linux

The architecture was designed to isolate the publicly accessible patient portal from the trusted internal network and restrict unnecessary communication between network segments. A default-deny firewall approach was used, with only explicitly authorised traffic permitted between zones.


Tools and Technologies:
Draw.io — Network topology and infrastructure design
Oracle VirtualBox — Virtualised simulation environment
pfSense — Firewall, routing, NAT, and network segmentation
Wazuh — Centralised security monitoring, SIEM, and alerting
Kali Linux — Simulated attacker platform and security testing
Ubuntu Server — Hosting platform for the Wazuh monitoring infrastructure
Wireshark — Network traffic capture and packet analysis
Nmap — Network reconnaissance and host discovery
SSH — Remote administration and authentication testing
Virtual LAN and network segmentation controls — Separation of critical network zones and systems.


Configuration Steps
Designed a logical healthcare network architecture using Draw.io, separating external, internal, and publicly accessible services.
Created a virtualised environment using Oracle VirtualBox to simulate workstations, servers, monitoring systems, and an attacker machine.
Configured pfSense with separate WAN, LAN, and DMZ interfaces using the following network ranges:
192.168.110.0/24 for WAN
192.168.120.0/24 for LAN
192.168.130.0/24 for DMZ

Implemented firewall controls based on network segmentation, stateful packet inspection, default-deny policies, controlled routing, and restricted administrative access.
Isolated the patient portal and telehealth services within the DMZ to limit direct exposure of internal clinical systems and EHR resources.
Deployed Wazuh Manager on an Ubuntu Server and installed Wazuh agents on selected systems to collect authentication events, system activity, and suspicious behaviour.
Configured security monitoring and alerting for events such as repeated authentication failures, network scanning, unauthorised access attempts, and privilege escalation activity.
Used Kali Linux to simulate controlled security testing, including network reconnaissance, host discovery, port scanning, and attempts to access protected network resources.
Performed network reconnaissance using commands including:
nmap 192.168.120.0/24
nmap -sn 192.168.120.0/24
nmap -sS 192.168.120.1
nmap -sV 192.168.120.1
nmap -sU 192.168.120.1
Captured and analysed network traffic using Wireshark, including the filter tcp.port == 22 to focus on SSH-related traffic.
Correlated Wazuh alerts with firewall activity and Wireshark packet captures to investigate suspicious activity from multiple sources.
Evaluated the effectiveness of segmentation, firewall rules, monitoring, and detection capabilities based on the evidence collected during the simulated attack scenarios.


Results and Findings
The project demonstrated that improved network segmentation, firewall enforcement, and centralised monitoring can strengthen the security posture of a healthcare environment.

Key findings included:

The original environment lacked sufficient segmentation between user workstations, clinical systems, administrative resources, and medical devices.
Limited monitoring reduced the ability to quickly identify suspicious behaviour and respond to potential incidents.
The segmented network design reduced unnecessary communication paths and restricted opportunities for lateral movement.
Simulated security activity generated events that could be identified through Wazuh, while Wireshark and firewall logs provided additional evidence for investigation.
Centralised monitoring improved visibility into authentication activity, system events, network scanning, and unauthorised access attempts.
The project reinforced the importance of least privilege, regular firewall rule reviews, vulnerability assessments, security monitoring, and cybersecurity awareness training.

The assessment concluded that combining preventative controls, such as segmentation and firewall policies, with detective and responsive controls, such as Wazuh monitoring and traffic analysis, creates a stronger foundation for protecting sensitive healthcare systems and patient information.

Author
Name: Olajumoke Olaniyan
Role: Security Operations Center (SOC) Analyst
Organisation: MediCore Health Systems
