# Content
- Overview of network access control systems (princible elements and techniques).
- Extensible Authentication protocol (EAP)
- IEEE 802.1X
- Cloud Security

---

# NAC
*Network Access Control*

- umbrella term
- Authenticates users (and checks their devices), then determines their authorized actions.

**NAC Deals with 3 catagories of components:***
1. Access Requester (*AR, Supplicant, client*).
2. Policy Server.
3. Network Access Servers (*NAS, Media Gateway, Remote Access Server RAS, Policy Server*): may include its own authentication server or rely on the policy server to authenticate users.

![[NAC Model.png]]

**Common NAC Enforcement Methods:**
- IEEE 802.1X : occurs at the *Data Link* layer
- DHCP Management : occurs at the IP Layer (Network Layer)
- VLANs 
- Firewall

---


# EAP
*Extensible Authentication Protocol*

- Framework for the exchange of authentication information between client and authentication server.
- The basic EAP transport service is extended by using a specific authentication protocol/method

![[EAP Layered Context.png]]


## EAP Methods
**Commonly Supported EAP Methods:**
1. EAP-TLS
2. EAP-TTLS
3. EAP-GPSK
4. EAP-IKEv2


### EAP-TLS
- uses the handshake protocol in TLS, not its encryption method.
- Client and server authenticate each other using digital certificates.
- client generates pre-master secret key (*PMSK*) -> sends it encrypted with the server's PK -> client and server generate a secret key from (*PMSK*).

### EAP-TTLS
*EAP - Tunneled TLS*

- similar to TLS, but the server has a certificate to authenticate itself to the client first.
- Tunnel is established with a secret key, then used to continue the authentication using another EAP method.


### EAP-GPSK
*EAP - Generalized Pre-Shared Key*

- based on Pre-Shared key only (*no asymmetric keys*).
- Advantage: Efficient in message flows and computational costs.
- Disadvantage: requires the existance of a Pre-Shared key between each peer and the EAP server (*this is set up during the peer's registeration proccess with the server*).
- EAP Exchange requires a minimum of 4 messages.


### EAP-IKEv2
*EAP - Internet Key Exchange version 2*

- supports mutual authentication and session key establishment.

----

## EAP Protocol Exchange

**EAP Echange Components:**
1. EAP Peer : Client
2. EAP Authenticator : an access point or NAS (*needs authentication to allow access*)
3. EAP Authentication Server: authenticates client, and is typically a *Remote Authentication Dial-In User Service (RADIUS) server*.


**EAP Pass-through Mode:** (*Common*)
- Authentication Server authenticates the user, then based on that -> the authenticator decides to allow access or not
**(*Less Common*)**: 
- the authenticator also does the role of the authentication server, so only a client and an authenticator are involved in the EAP Exchange.



***HOW DOES THE EXCHANGE WORK?***
![[EAP Protocol Exchanges.png]]

![[EAP Message Flow in Pass-Through Mode.png]]
- before the *EAP-Request/Identity* there's a lower level call (using PPP or IEEE 802.1X) to establish the need for an EAP exchange.
- Right after the Authentication Server recieves the identity, it decides which EAP method to use, and send it in the next *EAP-Request/Auth*
- if the *EAP Peer* doesn't support the method, it responds with (*NAK*)

![[EAP Frame Format.png]]

---

# IEEE 802.1X
*Port-based Network Access Control*

## Terminology
| EAP                   | IEEE 802.1X          |
| --------------------- | -------------------- |
| Peer                  | Supplicant           |
| Authenticator         | Network Access Point |
| Authentication Server | Authentication Server                     |

- before Authentication: 
| Channel | port type    | Status    |
| ------- | --- | --------- |
| Control |   uncontrolled  | unblocked |
| data    |   controlled  | blocked   |

- after Authentication: 
| Channel | port type  | Status    |
| ------- | --- | --------- |
| Control |  uncontrolled   | unblocked |
| data    | controlled    | unblocked |

- *ports are used to exchange PDUs (Protocol Data Units)*

----

## EAPOL
*EAP Over LAN* ^43a29f

- Operates at the Network Layer
- uses IEEE 802 LANs at the Link Layer (like Ethernet, Wi-Fi).

### EAPOL Packet/Frame Types
1. EAPOL-Start.
2. EAPOL-EAP: (Encapsulates EAP Requests).
3. EAPOL-Key: (For exchanging keys after Authentication).
4. EAPOL-Logoff.


***HOW IT WORKS?***
![[EAPOL Exchange.png]]

![[EAPoL Packet format.png]]


---

# Cloud Computing

**Cloud Elements:**
1. Deployment Models (4) : *Public, Private, Hybrid, Community*.
2. Service Models (3): *IaaS, PaaS, SaaS*.
3. Essential Characteristics (5): *Broad Network Access, Rapid Elasticity, Measured Service, On-Demand Self Service, Resource Pooling*.


## cloud computing reference architecture
![[Cloud Computing Reference Architecture.png]]

**Cloud Carrier:**
- a networking facility that provides connectivity and transport of cloud services between cloud consumers and CPs.
- can provide dedicated and secure connections between cloud consumers and CPs.


**Cloud Broker:**
- Cloud Broker Provides The Following Support Areas: 
	1. Service Intermediation: (value-added services: like *identity management, performance reporting, and enhanced security*).
	2. Service Aggregation: combining multiple cloud services to meet consumer needs.
	3. Service Arbitrage: similar to *Service Aggregation* (Except that a broker has the flexibility to choose services from multiple agencies).


**Cloud Auditor:**
* independent entity that assures that the CP conforms to a set of standards, and evaluates the services provided by a CP in terms of:
	1. security.
	2. privacy.
	3. performance.


## Risks & Countermeasures

***Cloud Security Allience*'s Top Cloud Security Threats & Countermeasures:**
| #   | Risk                                       | Countermeasure                                                                                                                                                                                                                                                                                                                                                |
| --- | ------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | Abuse and nefarious use of cloud computing | (1) stricter initial registration and validation processes; (2) enhanced credit card fraud monitoring and coordination (3) comprehensive introspection of customer network traffic; and (4) monitoring public blacklists for one’s own network blocks.                                                                                                        |
| 2   | Malicious insiders                         | (1) enforce strict supply chain management and conduct a comprehensive supplier assessment; (2) specify human resource requirements as part of legal contract; (3) require transparency into overall information security and management practices, as well as compliance reporting; and (4) determine security breach notification processes.                |
| 3   | Insecure interfaces and APIs               | (1) analyzing the security model of CP interfaces; (2) ensuring that strong authentication and access controls are implemented in concert with encrypted transmission; and (3) understanding the dependency chain associated with the API.                                                                                                                    |
| 4   | Shared technology issues                   | (1) implement security best practices for installation/configuration; (2) monitor environment for unauthorized changes/activity; (3) promote strong authentication and access control for administrative access and operations; (4) enforce SLAs for patching and vulnerability remediation; and (5) conduct vulnerability scanning and configuration audits. |
| 5   | Data loss or leakage                       | (1) implement strong API access control; (2) encrypt and protect integrity of data in transit; (3) analyze data protection at both design and run time; and (4) implement strong key generation, storage and management, and destruction practices.                                                                                                           |
| 6   | Account or service hijacking               | (1) prohibit the sharing of account credentials between users and services; (2) leverage strong two-factor authentication techniques where possible; (3) employ proactive monitoring to detect unauthorized activity; and (4) understand CP security policies and SLAs.                                                                                       |
| 7   | Unknown risk profile                       | (1) disclosure of applicable logs and data; (2) partial/full disclosure of infrastructure details (e.g., patch levels and firewalls) and (3) monitoring and alerting on necessary information.                                                                                                                                                                                                                                                                                                                                                              |


## Data Protection in the Cloud

- ***NIST*'s Guidelines on Security and Privacy Issues**

- **Database environments used in cloud computing:**
	1. multi-instance model: provides a unique DBMS running on a virtual machine instance for each cloud subscriber, giving them complete control.
	2. multi-tenant model: provides a predefined environment for the cloud subscriber that is shared with other tenants (via tagging with subscriber identifiers).


- **Data must be secured while at rest, in transit, and in use**
	1. in transit: client employs encryption, server handles key management or other encryption-related work.
	2. in rest: client stores data encrypted in the cloud, without the CP having access to the keys (*inflexible*).
	3. 


## SecaaS
*Security as a Service*

- a package of security services offered by a service provider, it takes over the responsibility of providing security for the user.

- SecaaS categories of service (by *Cloud Security Allience*): 
	1. Identity and access management (IAM).
	2. Data loss prevention (DLP).
	3. Web security.
	4. Email security.
	5. Security assessments: (third-party audits of cloud services).
	6. Intrusion management: includes detection systems (IDS) and prevention systems (IPS).
		- *IDS: a set of automated tools designed to detect unauthorized access to a host system.*
	7. Security information and event management (SIEM): aggregates (via push or pull mechanisms) log and event data.
	8. Encryption.
	9. Business continuity and disaster recovery.
	10. Network security.

---
