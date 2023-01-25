# Content
- Wireless Security Issues.
- Mobile Device Security - Threats & Countermeasures.
- IEEE 802.11 (Wi-Fi).
- IEEE 802.11i (WLAN Security).


---

# Wireless Security Issues

**Why are WLANs Less Secure?**
1. Channel : 
   - broadcasting through the air -> susseptable to both passive (eavesdropping and jamming) and active attacks.
2. Mobility : devices move around (less physical security).
3. Resources :
   - some wireless devices don't have enough resources to deal with attacks. 
4. Accessibility :
   - devices like robots/sensors left in remote areas (less physical security).


***WLAN* Components:**
1. Endpoint
2. Access Point
3. Wireless Medium


## Wireless Network Threats
1. Acidental association : due to overlapping transmission ranges.
2. Malicious association : hacking device appears as an access point.
3. Ad hoc networks : 
   - Ad hoc (latin for 'for this situation') : peer-to-peer networks between wireless devices with no access point between them.
   - lack of a central point of control = security risk.
4. Nontraditional networks.
5. Identity theft (MAC spoofing) : Attacker identifies the MAC of an admin using eavesdropping.
6. Man-in-the middle attacks.
7. Denial of service (DoS).
8. Network injection : if the AP doesn't use filters -> send it configuration protocol messages to make it use weaker security.


## Dealing with Threats

1. Securing the Transmission Medium against: (1) Eavesdropping and (2) Message Altering & Insertion

| Eavesdropping                                                                                                                                                                                                                                                                                                                    | Message Altering and Insertion |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------- |
| **Signal-hiding techniques:**<br> - turning off service set identifier (SSID) broadcasting by AP.<br> - assigning cryptic names to SSIDs.<br> - reducing signal strength to minimum requirements.<br> - keeping APs away from windows and in centeral locations.<br> - use of directional antennas.<br> - signal-shielding techniques. | Encryption       | Encryption        |
| Encryption                                                                                                                                                                                                                                                                                                                             | Authentication Protocols                 |                   |


2. Securing the Access Point against: (1) unauthorized access to the network
	- using the IEEE 802.1X port-based network access control.


3. Securing the Network
	1. Encryption : routers have built in encryption for router-to-router traffic. 
	2. Antivirus, antispyware, firewall.
	3. Turn off identifier broadcasting.
	4. Change the router's identifier from the default.
	5. Change the router's admin password from the default.
	6. Allow only specific devices to access, block the rest.


---

# Mobile Device Security

## Security Threats:
1. Lack of Physical Security : device can be stolen.
2. Untrusted Devices.
3. Untrusted 3rd-Party Apps.
4. Untrusted Content : Mobile Devices can scan QR codes while other devices can't. 
5. Untrusted Networks.
6. Interactions with other Systems : cloud synchronization.
7. Location Services.


## Securing the Device:
1. Enable Auto-lock.
2. Enable password or PIN protection.
3. Disable Auto-complete features.
4. Enable remote wipe.
5. Enable SSL protection.
6. Keep everything up to date.
7. Antivirus.
8. Sensetive data is either (1)prohibited or (2)must be encrypted.
9. IT staff can:
	1. remotely access devices.
	2. wipe the device of all data.
	3. disable the device in the event of loss or theft.
10. No 3rd-Party Apps.
11. No cloud sync.
12. Training of personnel on the risks inherent in untrusted content.
13. Disable Location services.


## Securing the Traffic:
1. Authentication.
2. Encryption.

## Securing the Network:
1. Firewall Policies.
2. Intrusion detection + prevention systems.

---

# IEEE 802.11 (Wi-Fi)

## Terminology

1. Station : any device with an IEEE 802.11 MAC and Physical Layer.
2. AP (Access Point).
3. BSS (Basic Service Set) : *stations controlled by the same coordination function*.
4. Coordination Function : decide on which station is able to transmit.
5. DS (Distribution System) : connects multiple BSS.
6. ESS (Extended Service Set) : group of BSSs connected by a DS, they all appear as a single BSS to the LLC of stations inside this ESS.
7. MPDU (MAC Protocol Data Unit).
8. MSDU (MAC Service Data Unit).

---
## History
- 1990 : IEEE 802 Committe created IEEE 802.11 working group.
- 1999 : IEEE 802.11b becomes the first standard to gain industry acceptence from the IEEE 802.11 group.
- 1999 : WECA (Wireless Ethernet Compatibility Allience), later called Wi-Fi, is formed.

*the term ***Wi-FI** was used to identify the IEEE 802.1b products, then extended to cover IEEE 802.1g.

*Now we have the following names:*
-   **WiFi 6** to identify devices that support 802.11ax (released 2019)
-   **WiFi 5** to identify devices that support 802.11ac (released 2014)
-   **WiFi 4** to identify devices that support 802.11n  (released 2009)
-   **WiFi 3** to identify devices that support 802.11g (released 2003)
-   **WiFi 2** to identify devices that support 802.11a (released 1999)
-   **WiFi 1** to identify devices that support 802.11b (released 1999)
---

## Protocol Stack

| Layer                | Normal Functionality                                                                                                              | IEEE 802.11 Additions                      |
| -------------------- | --------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------ |
| Physical             | Encoding/decoding<br>Bit Transmission<br>Transmission Medium Characteristics                                                      | frequency bands<br>Antenna Characteristics |
| Media Access Control | Error Detection<br>Control Access to media<br> - Recieves MSDU from LLC.<br> - Creates MPDU with address & Error detection fields |                                            |
| Logical Link         | keeps track of successfully recieved frames                                                                                       |                                            |


**IEEE 802.11 MPDU Format:**
![[MPDU Format.png]]


## IEEE 802.11 Services
1. Association
2. de-Aassociation
3. re-Association
4. Authentication
5. de-Authentication
6. Integration :
   - transfer of data between 802.11 WLAN and 802.x Integrated (wired) LAN.
7. Distribution
   - when MPDU must travel between BSSs
8. MSDU delivery
9. Privacy

***These 9 Services can be catogorized According to:***
1. Provider:
	1. station: authentication & de-authentication, MSDU delivery, Privacy.
	2. DS: others.
2. purpose:
	1. support LAN Access and security : authentication & de-authentication, Privacy.
	2. support MSDU delivery : others.



***Transition Types (based on mobility):***
1. No Transition.
2. BSS Transition.
3. ESS Transition : disruption of service is likely to occur.

**Association Services:**
1. association
2. re-association
3. disassociation

---

# IEEE 802.11i (WLAN Security)
*security only between a station and AP*

**Security Mechanisms for LANs**
| Mechanism                          | Details                                                    |
| ---------------------------------- | ---------------------------------------------------------- |
| WEP<br>Wireless Equivalent Privacy | Privacy part of 802.11<br> has major weaknesses            |
| WPA<br>Wi-Fi Protected Access      | based on 802.11i<br>Elemenated weaknesses of WEP           |
| RSN<br>Robust Security Network     | final form of 802.11i<br>WPA2 certifies the use of 802.11i |

----

## RSN Overview


----


## IEEE 802.11i Phases of Operation
1. Discovery phase: 
   - *AP* advertises with Beacons, *Station* probes and decides on the cipher suite and authentication mechanism.
   - 3 Message types:
	   1. Probe request/response.
	   2. Open system authentication request/response : for backwards compatibility.
	   3. association request/response.


2. Authentication phase:
   - done using EAPOL - IEEE 802.1X from [[5 - Network Access Control & Cloud Security#^43a29f]]


3. Key-managemene phase:
   - using 4-way handshake for distributing pairwise keys.

![[pairwise key hierarchy.png]]
![[Group key hierarchy.png]]

4. Protected data transfer
   - IEEE 802.11i has 2 methods for protecting the data:
	     1. TKIP (Temporal Key Integrity Protocol) : only requires software changes to devices already working with WEP.
	     2. CCMP (Counter-mode CBC MAC protocol) : requires hardware support, made for new devices.

5. Connection Termination