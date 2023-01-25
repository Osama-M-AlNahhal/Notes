# Content
- Remote User Authentication Principles
- Key Distribution using Symmetric Encryption.
- Kerberos
- Key Distribution using asymmetric encryption.
- X.509 Certificates
- PKI
- Federated Identity Management

----



---

# Key Distribution using asymmetric encryption
*by using public-key certificates*

- diffe-hellman has a disadvantage: it doesn't authenticate the users.
- Better Approach is using **Asymmetric Encryption.**
**How?** by sending the secret key (symmetric key) encrypted with the reciever's public key.

**Problem:** how do we know a public key is actually the reciever's key?
**A:** by using public-key certificates.

**How is a Public-Key Certificate used?**
![[Public-Key Certificate Use.png]]
- *X.509 is the standard for creating public key certificates.*

---

# X.509
*provides authentication using public-key certificates*

**Background:**
- ITU-T has a series of protocols called X.500.
- these protocols are for directory services, and X.509 is the protocol for user authentication.
- it uses the directory to store the certificates.
- X.509 doesn't FORCE you to use any algorithm, but it recommends RSA.


**Format:**
![[X.509 formates.png]]
* if the certificate has ***Issuer unique identifier*** or ***Subject unique identifier*** then it must be version 2.
* if it has any extensions then it must be version 3.
	* Extension format: (extension identifier) + (criticality identifier) + (value).
	* Extension types: 
		1. key and policy info
		2. subject and issuer attributes
		3. certification path constraints

| Key and policy info      | subject and issuer attributes | certification path constraints |
| ------------------------ | ----------------------------- | ------------------------------ |
| Authority key identifier | subject alternative name      | basic constraints              |
| subject key identifier   | issuer alternative name       | name constraints               |
| key usuage               | subject directoy attributes   | policy constraints                               |
| private-key usage period |                               |                                |
| certificate policies     |                               |                                |
| policy mapping           |                               |                                |
*policy mapping: only for certificates for CAs issued by other CAs.*


- only the CA that created the certificate can edit it, if anyone else edits it then they'll be detected, so its ok to keep the certificates in the directory without protection.
- directory of each CA has 2 types of certificates:
	1. Forward certificates: created by another CA to verify the current CA.
	2. Reverse certificates: created by the current CA to verify other CA's.


***When is a certificate revoked?***
1. user's private key is compromised.
2. user no longer certified by the CA for the following reasons:
	1. changed his name.
	2. newer certificate superceded the old one.
	3. certificate is against the CA's policy.
3. CA's certificate is compromised.

---

# PKI
*everything related/involved in dealing with Public-key certificates.*

**Components:**
1. End Entity : client
2. CA : issues certificates and CRL, but sometimes lets ***RA*** and ***CRL issuer*** do some of its work.
3. RA : (optional) registers users.
4. CRL issuer : (optional) issues ceritificate rejections and manages them.


***PKIX Management Functions:***
1. Registration.
2. Initialization.
3. Certification.
4. Key-pair update.
5. Key-pair recovery.
6. Revokation request.
7. Cross certification.

***Alternative Management Protocols:***
1. CMP : Certificate Management Protocols
2. CMC : Certificate Management messages over CMS

---

# Federated Identity Management
*Identity Management but for millions of devices across different domains*


**What is Identity Management?**
* a centeralized approach to allowing certified/authorized users to access resources.
* uses *Single Sign-on* (SSO) to let users access all resources.

| Principles of an Identity Management System | Services Provided by Federated Identity Management Systems |
| ------------------------------------------- | ---------------------------------------------------------- |
| Authentication                              | Point of contact : authentication                          |
| Authorization                               | Authorization                                              |
| Accounting                                  | Trust Services                                             |
| Provisioning                                | Provisioning                                               |
| Workflow automation                         | Identity Services                                          |
| Delegated administration                    | SSO Protocol Services                                      |
| password synchronization                    | Key services                                               |
| self-service password reset                 | Management (runtime configuration)                                                          |
| Federation                                  |                                                            |


***Identity Managment System components:***
1. Principle : user
2. Identity Provider.
3. Attribute Service : gives attributes to indicate the level of authorization, based on an administrator's decision.
4. Data Consumer : collects info (identity + attributes) for authorization or auditing.


***Why Federated Management Systems?***
1. SSO makes things better/easier.
2. standard way of representing attributes.
3. identity mapping across different domains.


***STANDARDS:***
1. XML : Extensible Mark-up Language
2. SOAP : Simple Object Access Protocol
	- uses XML over HTTP to invoke code.
	- gives applications XML-based requests/responses between each other.
3. WS-Security :
	- SOAP Extensions for confidentiality & message integrity on the web.
	- assigns security token to each message for authentication.
4. SAML : Security Assertion Mark-up Language
	- XML-based, used to exchange security info between businesses.


**Federated Identity Scenarios:**
1. Federation based on *Account-Linking*.
2. Federation based on *Role*.
3. *Document-based* Federation (Chained Web Services).


