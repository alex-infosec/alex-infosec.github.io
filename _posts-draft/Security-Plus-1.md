
I will be studying for the COMPTIA Security + Certification. My first real certification that I intend to take in 2 months. I plan to alot on average 2.5 hours everyday to studying for it and learning key Cybersecurity principals while immersing myself in the domain.

# .1.0 General Security Concepts
## Compare and contrast various types of security controls
__Categories__
* _Technical_ - controls implemented using systems. Operating system controls that allow or dont allow things. Firewalls, anti-virus
* _Managerial_ - Administrative controls associated with security design and implementation. Security polices, standard operating procedures.
* _Operational_ - (people) controls implemented by people instead of systems. Security guards, awareness programs
* _Physical_ - Limit physical access to a building room device etc. Fences locks. Badge readers.

__Control Types__
* _Preventative_ - Block access to a recources, Firewall rules follow secuity polic. Door locks.
* _Deterrent_ - Discourage an intrusion attempt. Does not directly prevent access.
* _Detective_ - Identify and log an intrusion attempt. May not prevet access.
* _Corrective_ - Apply a control after an event has been detected. Attempts to reverse the impact of an event, to continue operating with minimal downtime.
* _Compensating_ - A security event has occured but you dont have the means to work with it. May be temporary if controls arent sufficient.
* _Directive_ - irect a subject towards security compliance. A relatively weak security control.

| **Category**  | **Preventive**         | **Deterrent**       | **Detective**            | **Corrective**                | **Compensating**                | **Directive**                  |
|---------------|-------------------------|----------------------|---------------------------|--------------------------------|---------------------------------|--------------------------------|
| **Technical** | Firewall               | Splash screen        | System logs              | Backup recovery                | Block instead of patch          | File storage policies          |
| **Managerial**| On-boarding policy     | Demotion            | Review login reports     | Policies for reporting issues  | Separation of duties             | Compliance policies            |
| **Operational** | Guard shack          | Reception desk       | Property patrols         | Contact authorities            | Require multiple security staff  | Security policy training       |
| **Physical**  | Door lock              | Warning signs        | Motion detectors         | Fire extinguisher              | Power generator                 | Sign: Authorized Personnel Only |

## .1.1 Summarize fundamental security concepts
### The CIA Triad
sometimes referenced as teh AIC Triad, its the fundamentals of security

__Confidentiality__ - prevent disclosure of information to unauthorized individuals or systems
* Encryption - encode messages so only certain people can read it
* Access Controls - Selectively restrict access to a resource
* Two-factor authentication

__Integrity__ - Messages cant be modified without detection. Ddata is stored and transferred as intended
* Hashing - Map data of an arbitrary length to data of a fixed length. The recipient and sender should have same Hashing
* Digital signatures - Encrypted hash
* Certificates - combine with a digital signature to verify an individual
* Non-reprudiation - Provides proof of integrity, can be asserted to be genuine

__Availability__ Systems and networks must be up and running
* Redundancy - Biild services will always be available
* Fault tolerance - System will continue to run, even when a failure occurs
* Patching - stability, and close security holes

### Non-reprudiation
Similar to a signature. We use
__Proof of integrity__ - verify data does not change. We use a hash, sometimes reffered to as a message digest, like a fingerprint. Doesnt necessarily associate data with an individual. If the hash is different, something has changed.
__Proof of origin__ - Sometimes called authentification. Make sure the signature isnt fake. Usually sign with a private key. We use a public key assocciated with the private key to authenticate whether it was the same person. 

### Authentication, Authorization, and Accounting
AAA Frameword\key
Authentication - Prove you are whou you say you are
Authorization - based on your identification and authentication, what access do you have
Accounting - logging recources used
In order to tryly authinticate a device, you put a digital;ly signed certificate on the device. 
- Access to the VPN from authorized devices
- Management software can validate the end device
* An organization has a trusted __Certificate Authority__ (CA), most organizations maintain their own CA< they digitally sign the certificate with the organizations CA. The CA's digital signature is used to validate the certificate *Similar to a ticket to a game*
- Associating individual users to access rights does not scale, thats why most organizations use an authorization model
Sometimes the authorization model is reffered to as an abstraction
Administration is streamlined. 

### Gap analysis
Where you are compared to where you want to be *The "gap" between the two*
Can take weeks or months, extensive study with numerous participants. Takes emails, data gathering, and technical research
Baseline 
* Work towards the internal set of goals
* Some organizations use formal standards
* May Use NIST or ISO all for figuring out baselines
* Get a baseline of employees - formal experience, current rtraining, knowledge of security policies and procedures
* Evaluate existing IT systems
Compare the existing systems, and identify weaknesses, usually with your baseline
The detailed analysis will be examining broad security categories, and then breaking those down into smaller segments
Neee a path to get from the current security to the end goal, will take time, money, and lots of change control

### Zero trusted
Many networks are relatively open on the inside, once youre through the Firewall
Zero trust - a holistic approach to network security, covers every device, process, and Personnel
__Planes of operation__ Split the network into funcitonal planes, applies to physical, virtual, and cloud components
* Data plane 
- Process the frames, packets, and network data
- Processing, forwarding, trunking, encrypting, NAT

* Control Plane
- Manages the actions of the data plane
- Define policies and rules
- Determine how packets should be forwarded 

Adaptive identity
- consider the source and the requested resources
- multiple risk indicaters - relationship to the organization, physical location, type of connection, IP address, etc.
- make the authentification stronger, if needed
Threat scope reduction
- Decrease the number of possible entry points (Only building vpn)
Policy driven access control
- combine the adaptive identity with a predefined set of rules
Security Zones
- security is more than a one-to-one relationship
- Where are you coming from and where are you going

*Upon further thinking I realized the more efficient way to study for SEC+ would be to frontload the information, getting a mental "Lay of the land" so to speak, and coming back later to make the pathways and road. This means my notes will become more sparse*

Policy Enforcement Piont (PEP)
- the gatekeeper, all traffic going through the network has to go through the pep to see if the traffic is allowed. Its usually multiple devices working together.

Policy Decision Point 
- dont know the difference tbh
- **Policy Engine**  The final Judge. Grant deny or revoke.
- **Policy Administrator** Complex Judge, communicatetes with PEP 

Honey Pot
- attrack bad guys to see what their strats are
- honey nets, larger deception network
- honey files, fake information that alert is sent if file is accessed
- honey token, traceable data if its stolen to see where it cam fom

### Managerial Change
When a system updates is one of the most common risks in the enterprise. Need policy on changes
Change approval process
- ownership, this ones weird but its the owner of the application and theyre usually not the ones doing the changing just verifying it happened
- Stakeholders, impacted by the change 
- Impact analysis, usually a risk value
- test results, like with a sandbox testing environment
- **Backout plan**  Way to return to original state if something goes wrong
- Maintenance Window
- Apart of Standard Operating Procedures, should be well documented

From the perspective of the technicial implementation of change
- Allow list/ deny list
- Restricted Activities "Scope of change"
- Downtime, want to reduce this so usually lose 2 different versions to try and make changes
- Restarts
- Legacy applications (here before you arrived might be there when u leave) u become the support. U must become the expert.
- **Dependencies** can complicate things. Must complete A for B.
- Documentation is pivotal in doing this
- Version control, tracking the changes to a file over time

## 1.4
### Public Key Infrastructure (PKI)
**Symmetric Encryption** Encrypt and decrypt with the same key. Single shared key
**Asymmetric engryption** Two or more mathmatically related keys. Private and public key. 
**Key excrow** 3rd party key or personal key holder, like Hagrid from Harry Potter.
(EFS) Windows Encrypting File Systems
Mac Linux use 3rd party but sometimes we need to encrypt all stored data at rest.
Database encryption
* Transparent encryption - encrypts all database information with a symmetric key
* Record-level Encryption - encrypts individula columns with separate symmetric keys.

Transport Encryption
* Data across the network
* VPN Virtual Private Network is an encrypted tunnel

Key stretching due to increased processor strength. Hashing the hash of a hash of a password lol.

**Key Exchange**

In band key exchange, on the network protects teh key with additional encryption, use asymmetric encryption to deliver a symmetric key. Called a session key

**Trusted Platform Module (TPM)**

Cryptograhic hardware on a device. Random number generator key generator. Persistent memory , burned in during manufacturing

**Hardware Security Module**

TPM but for data centers. Used in large environments. Securely stores thousands of cryptographic keys.
Designed fro very fast cryptographic functions.

There is a Key Management System (similar to a wireshark just an applciation yk)

**Secure Enclave**, a separate security processor built into the phone laptop etc. Given different names

* Obfuscate - making somethin unclear
* Steganography - hiding data in an image. The image is called the "Coverimage"
* Tokenization - Paying with a credit card
* Data Masking -  ************345
* Hash - only the fingerprint just to make sure its not changed
* Collision - when hashing two different inputs makes the same hash, Do not use MD5 (old hashing algo) as a result of that 
* Use hashing to verify downloads
* Salted Hash, randoom data added to a password when hashing.
* Rainbow tables wont work with salted hashes for common hashes
* Blokcchain - a distributed ledger, keeps track of things needed to be monitored. Bitcoin is common. Due to blockchain it keeps people from going in and messing it up since its kept alive by adding blocks so u cant fake the blocks because theyre built on top of each other.

### Digital Certificates

Public Key Certificate - CA signs it with the person digital signature
Web of trust - use others for additional trust
Websites use a X.50- the standardized format of a digital certificate
Wildcard certificates: Subject ALternative Name (SAN) its an extention to the X.509 certificate allows a certificate to support many different domain names
Key Revolcation List (CRL) also maintained by the Certificate Authority
OCSP - online certificate status protocal modernish website ca approval being stapled and that staple is verified by CA