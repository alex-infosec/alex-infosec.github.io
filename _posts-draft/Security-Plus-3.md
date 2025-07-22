

## 3.1
### Cloud responsibility matrix
Who is responsible for the security of cloud stuff. They usually im thinking AmazonWS when i was getting the amazonws cert they gave a matrix that says whos responsible. **Hybrid Cloud** - network protections must match even if one is public or one is private. Its hard to do different security monitoring.
* Infrastructure as a code, u can modify it easily usually aparrt of cloud computing
* Function as a Service this is serverless architecure, remember this is like server side logic we learned about this. 
* Microservices and APIs

### Network Infrastructure and other infrastructre ideas
* Physical isolation
* Physical segmentation separate devices where customers dont overlap
* Logical segmentation with VLANs
* SDN (Software Defined Networking) Planes of operation Data, Control, and management planes
* Data plane - network packets encrypting NAT
* Control - dynamic routing
* Application/Management - i honestly dont know really
* IOT , sensors smart watches wfacility automation, IOT manufacturers are not security proffessionals
* SCADA /ICS 
* HA (High availability) Industry term`
* Resilience is how we keep it chugging
* MTTR - mean time to repair
* Cost, installation maintenance
* Responsiveness
* Scalability / elasticity
* Ease of deployment
* Risk Transference - cybersecurity insurance
* Power
* Compute component

## 3.2
### Intrusion Prevention System (IPS)
* Watches the network traffic overtime.
* IDS is detection system, alerts but doesnt prevent
* IDS vs IPS is what this one was about

 Failure Modes 
 - Fail-Open: have backup version to allow app to work just no security
 - Fail-Closed: when fails data does not flow
 * Device Connections Active monitoring when system is connected "inline" internet -> firewall -> IPS -> Core Switch 
 * Passive montoring, not in line, data cannot be blocked in real time. Reffered to as "IDS design" even though often uses ips, but its not in line so it cant block. 
* Passive monitoring, a copu of the traffic is kept

### Network Appliances
**Jump Server** Access secure netwoork zones from outside, its highly secured... SSH/ Tunnel? VPN

**Proxies** Sits between the users recieves the user requests and sends the request on their behalf, Internet is big example
* Invisible Proxy (transparent)
* Explicit proxy, apps need to know how to use proxy
* NAT is simplest proxy
* Most proxies in use are application proxies
* Forward Proxy
* Reverse Proxy
* Open Proxy (third party uncontrolled proxy) usually blocked tbh
* load balancer
* Active/ Active load balancing, all servers are open, 
* Active/ Passive 
* Sensors and collector, used in SIEM

### Port Security
* EAP Extensible Authentication Protocol - authentication framework
* IEEE 802.1X is port based Network Access Control (NAC), you dont get access to the network until you authenticate
* EAP integrates with 802.1X
* Supplicant - the client (laptop)
* Authenticator - The device that provides access
* Authentication server - Validates the client credentials

### Firewall Types
* The universal Security Control 
* Please do not take smeagols precious away
* UTM / All-in-one security appliance (a firewall)-  only operate at layer 4
* NGFW Next generation firewall - the application layer (7)
* WAF Web Application Firewall

### Secure Communications
* VPN 
* SSL?TLS VPN (Secure Sockets Layer VPN) or (Transport Layer Security VPN)
* Site to Site IPsec VPN (this is the like school VPN or remote site to corporate network)
* SD-WAN Software Defined Networking in a wide area network
* SASE Secure Access Service Edge next-geration VPN

## 3.3
### DataTypes
* Regulated
* Trade Secrets
* IP Intellectual Property
* Legal Information
* Financial Infromation
* Human readable vs non human readable
* Sensativity levels
* Proprietary - unique to a company
* PII - Personally Identifiable Information
* PHI - Protected Health Information

### Protecting Data
* Hotsite exact replica of data center
* cold site - empty building
* warm site - some people on site
* platform diversity
* multicloud systems
* Continuity of operation planning (COOP)
* Capacity Planning - match sypply to people

## 3.4 
### Backups
* Frequency 
* Encryption
* Snapshots
* Recovery Testing
* Replication
* Journaling

**Power Resiliency** 
**UPS** Uninterruptible power supply
* Offline/standby UPS 
* Line interactive UPS
* online double conversion UPS