---
description: >-
  Introduction to Wireless Security Protocols and Cryptography: Recovery
  (Remove) the FUD, OSI Model, OSI Simplified, Internet Model, Wireless LAN
  Security Protocols, Cryptography, SSL.. (Tq NotebookLM)
---

# Unit 2

## Syllabus

UNIT II: **Introduction to Wireless Security Protocols and Cryptography:** Recovery(removing) the FUD, OSI Model, OSI Simplified, Internet Model, Wireless LAN Security Protocols, Cryptography, SSL/TLS,Secure Shell Protocols, Terminal Access and File Transfer, Port Forwarding a Word of Caution, Man-in-the-Middle of SSL/TLS and SSH, WTLS, WEP,802.1x, IP Security

## FUD : Fear Uncertainty Doubt

This chapter aims to eliminate the **FUD** (fear, uncertainty, and doubt) surrounding wireless security. The threats discussed in Chapter 2 are often not unique to wireless technology; they are problems that information security professionals have already spent significant time and resources tackling for the **commercial Internet**.

Instead of reinventing security solutions, we will **apply existing, proven Internet and office-based security technologies and applications** to mitigate these threats.

We will begin by briefly reviewing the **Open System Interconnection (OSI) model** to identify the layer at which traditional security mechanisms are implemented. Following this, we will discuss common security technologies applicable to securing a wireless network. **Chapter 8** will cover actual implementations and design concepts.

## OSI

The seven layers, from top to bottom, are:

1. **Application Layer:** The user interface for communications (browsers, email).
2. **Presentation Layer:** Negotiates data syntax.
3. **Session Layer:** Coordinates and tracks communications.
4. **Transport Layer:** Provides reliability and ordering; organizes data into _segments_.
5. **Network Layer (Internet Layer):** Handles routing and logical addressing; organizes data into _packets_.
6. **Data Link Layer:** Manages physical addressing (like MAC addresses); organizes data into _frames_.
7. **Physical Layer:** Responsible for the actual communication, converting data into radio signals or voltages.

<figure><img src="../.gitbook/assets/Unit 2-1763821312960.webp" alt=""><figcaption></figcaption></figure>

#### OSI Simplified

<figure><img src="../.gitbook/assets/Unit 2-1763821343629.webp" alt=""><figcaption></figcaption></figure>



## Wireless Local Area Network (LAN) Security Protocols

This topic is addressed in **Chapter 3: Introduction to Wireless Security Protocols and Cryptography**. This section explains where these protocols reside within the networking stack and introduces the key technologies used to secure WLANs.

#### Protocol Location and Challenges

* In developing the 802.11 standard (Wireless Ethernet), developers followed the OSI model.
* Wireless Ethernet was designed as a drop-in replacement for wired Ethernet, meaning the entire protocol exists on the **Physical Layer and the Data Link Layer** of the OSI model.
* Historically, very few security implementations were designed below the Network Layer. Because of this, new security mechanisms had to be created specifically for the physical and data link layers.
* Unfortunately, these initial new security mechanisms were found to be **"less than effective"**.

#### Key Wireless LAN Security Protocols

The source materials discuss two major protocols relevant to WLAN security: WEP and 802.1x.

1. Wired Equivalent Privacy (WEP)

* WEP is the **security mechanism included in the 802.11 standard**.
* It was designed to provide **confidentiality and authentication services**, aiming to offer the same level of security found in a wired network.
* WEP is based on the **RC4 stream cipher algorithm**. Packets are encrypted by generating an RC4 stream using a combination of a shared key and a 24-bit initialization vector (IV).
* **Vulnerabilities:** Due to implementation flaws and key management issues, WEP has been proven to be almost useless for providing authentication and confidentiality on a wireless network. Weaknesses have been exposed that allow an attacker to recover the WEP key in a number of hours after capturing minimal network traffic.
* **Key Management Problems:** WEP typically uses a single static key for all users, making it very difficult to protect and requiring frequent changes. However, some later implementations bundle WEP key negotiation and rekeying with 802.1x functionality.

2. 802.1x

* This is a standard (Layer 2 protocol) designed to increase network security _before_ Layer 3 protocols (such as IP) are established.
* Its basic purpose is to **authenticate users** and optionally establish encryption keys.
* It utilizes the **Extensible Authentication Protocol (EAP)** for authentication, often sending user login information (like username and password) to the access point.
* The technology is not specific to 802.11 and can be used on Ethernet and Token Ring networks, among others.

Because WEP proved inadequate, most modern applications require using security protocols that operate at the Network Layer (Layer 3) and above, such as IPSec, SSL/TLS, and SSH, which are discussed immediately following the WLAN protocols in Chapter 3.

## Cryptography

Cryptography is a foundational topic addressed in **Unit II: Introduction to Wireless Security Protocols and Cryptography**. It is commonly defined as the **process or skill of communicating in or deciphering secret writings or ciphers**.

Historically, cryptographic methods date back to ciphers like the **Caesar Cipher**, which relied on a simple substitution of letters. Much of modern cryptography is based on research that was originally performed to keep **government information safe during times of war**.

While encryption systems offer significant protection, implementing them successfully requires careful planning beyond just the algorithm itself. Overall security is impacted by choosing the correct **encryption process or algorithm** and ensuring the **best protection for cryptographic keys**.

Cryptography is utilized to solve three primary security problems:

1. **Authentication:** Used to **reliably determine someone or something’s identity**, which helps prevent an attacker from impersonating a legitimate user or resource.
2. **Encryption (Confidentiality Service):** This is the process of **encoding data** to prevent eavesdropping, thereby keeping the data safe from unintended listeners. The core strength of an encryption system rests on the **size of the encryption key**.
3. **Integrity:** Ensures that the message received is the message that was sent, guaranteeing that the data **has not been modified**.

#### Classes of Encryption Algorithms

* **Symmetric (Private Key):** Both the sender and recipient use the **same key** for encrypting and decrypting the data. Since the same key is used by both parties, securing the distribution of this key can be problematic. Examples of symmetric systems include the **Data Encryption Standard (DES)**. These algorithms can operate as **block algorithms** (transforming blocks of data, typically 64 bits or more) or **stream algorithms** (transforming individual bits).
* **Asymmetric (Public Key):** Different keys are used for encryption and decryption. The key used for encryption can be made **public**, which greatly simplifies the key distribution process. Asymmetric algorithms are typically computationally intensive, so they are not usually used for transferring large amounts of data; instead, they are often utilized to establish a shared session key for a symmetric algorithm.







<details>

<summary>Hierarchy or relation or connection between these: SSL/TLS, Secure Shell Protocols, WTLS, WEP , 802.1x , IP sec, WAP</summary>

As the various protocols and standards in wireless networking often interact or replace one another, leading to significant confusion. These technologies relate based on their primary function (standard vs. protocol), their security function (authentication vs. encryption), and the network layer at which they operate.

Here is an overview of the hierarchy, relation, and connection between the protocols and standards you listed:

#### 1. Architectural Frameworks and Standards

The list you provided includes major standards or architectural frameworks that define how the network is built and accessed: **WAP** and **802.1x** (a specific network access standard).

| Technology                              | Type                              | Purpose & Connection                                                                                                                                                                                                                                                                          |
| --------------------------------------- | --------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **WAP** (Wireless Application Protocol) | Specification/Framework           | **WAP is an architecture** for accessing the wireless Internet from devices like mobile phones and PDAs. Because traditional Internet protocols like TCP/IP and SSL were not suitable for the constraints of early mobile devices, **WAP introduced WTLS** as its specialized security layer. |
| **802.1x**                              | Network Access Standard (Layer 2) | This is an **approved IEEE standard** that provides network port authentication. It can be used on wired networks (Ethernet) but is frequently used to **enhance the security of 802.11 wireless LANs** by providing strong user authentication and managing encryption keys.                 |

#### 2. Wireless LAN Security (802.11 specific)

These protocols are specifically associated with Wireless Local Area Networks (WLANs), defined primarily by the IEEE **802.11** standard.

| Technology                         | Relation to 802.11          | Status & Function                                                                                                                                                                                                                                                                                                                                        |
| ---------------------------------- | --------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **WEP** (Wired Equivalent Privacy) | **Default 802.11 Security** | WEP is the security mechanism included in the **802.11 standard** and was designed to provide confidentiality and authentication services. **Connection:** WEP operates at the physical and data link layers (Layers 1 and 2). However, WEP has been proven to have **implementation flaws and security weaknesses**, making it unreliable for security. |
| **802.1x**                         | **WEP Enhancer**            | **Connection:** 802.1x is often implemented with 802.11 networks to address WEP’s flaws. It dynamically negotiates WEP keys and manages authentication, eliminating the need for a static shared WEP key.                                                                                                                                                |

#### 3. Transport and Tunneling Security Protocols

These protocols operate higher up the network stack (Transport/Network layers) and are often used to create secure tunnels, either universally across the internet or specifically for remote access/VPNs.

| Technology                                                  | Network Layer         | Primary Use & Relation                                                                                                                                                                                                                                                                                                                                                                                                 |
| ----------------------------------------------------------- | --------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **SSL/TLS** (Secure Sockets Layer/Transport Layer Security) | Transport/Application | The most widely implemented security protocol on the wired Internet, used for **secure web traffic (HTTPS)**. **Connection:** SSL/TLS serves as the model for **WTLS**, which is the adapted version used in WAP.                                                                                                                                                                                                      |
| **WTLS** (Wireless Transport Layer Security)                | Transport/Application | WTLS is based on **SSL/TLS** but uses **UDP** instead of TCP, making it suitable for bandwidth-constrained **WAP** devices. **Hierarchy/Relation:** WTLS encryption runs from the wireless device to the WAP gateway, where data is converted and typically re-encrypted using **SSL/TLS** for the transmission to the web server, creating the controversial **"WAP Gap"**.                                           |
| **Secure Shell (SSH)**                                      | Application/Session   | A versatile protocol developed to replace insecure protocols like telnet and FTP, providing **strong authentication and encrypted sessions**. **Connection:** Like SSL/TLS and IPsec, SSH can be used to tunnel applications over an insecure medium (like a wireless LAN).                                                                                                                                            |
| **IPsec** (IP Security)                                     | Network (Layer 3)     | A set of protocols designed to provide encryption (ESP) and authentication (AH) at the **IP layer**. **Hierarchy/Relation:** IPsec is the enabling technology behind most **Virtual Private Networks (VPNs)**. It operates lower in the protocol stack than SSL/TLS or SSH, often providing a robust, full-packet encryption solution that can secure all traffic over a wireless link, regardless of the application. |

***

#### Summary of Key Connections

The protocols can be mentally grouped based on the environment they protect:

1. **Wired Internet Foundation:** **SSL/TLS** and **SSH** are foundational security protocols primarily developed for the wired Internet.
2. **Wireless Standards and Their Native Security:**
   * **WAP** uses **WTLS** (an adaptation of SSL/TLS) as its security layer.
   * **802.11 WLANs** rely on **WEP** for native security, although WEP is flawed.
3. **Security Enhancement/Alternative:**
   * **802.1x** is an authentication mechanism layered on top of the 802.11 standard, often fixing the key management issues of **WEP**.
   * **IPsec** provides a robust, layer-3 security alternative (VPN tunneling) that can be used on top of insecure lower layers (like WEP or open 802.11), providing confidentiality and integrity for all application traffic.

In terms of the OSI model, IPsec sits below SSL/TLS, SSH, and WTLS. Meanwhile, WEP and 802.1x sit at the bottom, dealing directly with physical link security and access control.

| Network Layer                                     | Technologies       | Role                                                                                      |
| ------------------------------------------------- | ------------------ | ----------------------------------------------------------------------------------------- |
| **Layers 5–7 (Session/Presentation/Application)** | SSL/TLS, SSH, WTLS | Application-aware security, securing data streams (e.g., web transactions, remote login). |
| **Layer 3 (Network)**                             | IPsec              | Full network packet encryption (VPN tunneling).                                           |
| **Layer 2 (Data Link)**                           | 802.1x, WEP        | Access control and link-layer encryption for local area networks (WLANs).                 |

This means that a modern, secure wireless LAN deployment might utilize **WEP** (as a basic barrier) augmented by **802.1x** (for strong authentication), with users running **IPsec** (to encrypt traffic end-to-end via a VPN tunnel) or **SSL/TLS/SSH** (to secure specific applications) over the link. The choice of protocol depends heavily on the security requirements of the application being used.

</details>

## SSL/TLS

The Secure Sockets Layer (SSL) protocol, and its successor, Transport Layer Security (TLS), are key protocols in wireless security, covered in **Unit II: Introduction to Wireless Security Protocols and Cryptography**.

#### Purpose and History

* **Foundation for Web Security:** SSL was originally designed to solve security problems associated with web browsers. It significantly aided in the acceleration of e-commerce by providing a **universal secure method** for conducting business and transactions, thereby making the Web safe for commerce.
* **Wired Standard:** In the wired Internet, SSL became the standard security mechanism for transmitting sensitive information from a PC to a web server.
* **Standards Evolution:** SSL was initially a Netscape de facto standard (implemented in 1994) but was later adopted by the Internet Engineering Task Force (IETF) as TLS.
* **Basis for Others:** SSL/TLS has served as the foundation for other security protocols, including Microsoft’s Private Communications Technology (PCT), Secure Transport Layer Protocol (STLP), and Wireless Transport Layer Security (WTLS).

#### Functionality and Mechanism

* **Core Security Services:** SSL/TLS is used to **authenticate and encrypt a connection**. It provides a secure channel for the transmission of data.
* **Transparency:** The protocol is considered "transparent," meaning that the data arrives at its destination unchanged by the encryption/decryption process, making it suitable for many applications.
* **Layer Dependence:** SSL/TLS relies on the **Transmission Control Protocol (TCP)** as the reliable transport protocol and therefore does not include its own reliability mechanisms.
* **Cryptographic Methods:** It utilizes a combination of **symmetric and asymmetric algorithms**.
  * **Handshake:** The establishment of the connection relies on **public-key cryptography** (the handshake) to authenticate the server and optionally the client.
  * **Data Transfer:** The actual communication uses a symmetrical encryption algorithm because symmetric algorithms offer better performance for transferring large amounts of data (asymmetric algorithms are computationally expensive).
* **Usage:** While it has the capacity for mutual authentication, in most cases, only **server authentication** is actually performed. Its primary application is for web traffic (**HTTP**). HTTP over SSL/TLS is typically implemented over TCP port **443**, rather than standard HTTP port 80. SSL/TLS can also secure common TCP communications like e-mail, news, telnet, and FTP.

#### Threats and Weaknesses

* **MITM Susceptibility:** Some implementations of SSL/TLS are vulnerable to **Man-in-the-Middle (MITM) attacks**.
* **Attack Vector:** A malicious attacker can intercept the public-key handshake and replace the exchanged keys with counterfeit keys, thereby compromising the session. Tools exist for performing testing of MITM attacks against SSL/TLS.
* **Mitigation:** These attacks can be prevented by implementing a Public Key Infrastructure (PKI) or by holding key-signing parties. Users should be trained on what MITM error messages look like, as they are often disregarded.

#### Relevance to Wireless Security (WTLS and WAP Gap)

* **Initial Challenge:** When the wireless Internet emerged, the initial infrastructure lacked an equivalent SSL standard.
* **WTLS Creation:** SSL itself was deemed unsuitable for wireless networks due to the low-bandwidth and hardware limitations of cellular handsets. Therefore, the WAP Forum provided an SSL-like alternative called **Wireless Transport Layer Security (WTLS)**.
* **The WAP Gap:** The original WAP architecture (WAP 1.x) required two protocols: WTLS from the wireless handset to the WAP gateway, and SSL from the WAP gateway to the web server. During the necessary conversion from WTLS to SSL at the WAP gateway, the data was unencrypted and then reencrypted, leaving it momentarily in an exposed, unencrypted form. This critical vulnerability became known as the **WAP Gap**.

## SSH

The Secure Shell (SSH) protocol is a highly utilized security mechanism that falls under **Unit II: Introduction to Wireless Security Protocols and Cryptography**.

SSH was developed in 1995 following a password-sniffing attack on a university network, and its design goal was to secure communications that were previously handled by unsecured protocols. Due to its flexibility and ease of use, it is a highly used security protocol that is included in the standard installation of many operating systems.

!\[\[/Attachments of Obsidian Notes'/Unit 2-1763833569008.webp]]

<figure><img src="../.gitbook/assets/Unit 2-1763833569008.webp" alt=""><figcaption></figcaption></figure>

#### Core Functionality and Operation

1. It uses a **public-key exchange** to establish the secure initial connection.
2. It then negotiates a **symmetric key** for the high-performance data transfer during the session.
3. SSH can be configured to **authenticate both the server and the client**.

Common implementations include commercial SSH, OpenSSH, PuTTY for Windows platforms, and F-Secure ssh, all of which are designed to be interoperable.

#### Key Uses in Networking

* **Terminal Access and File Transfer:** SSH is most commonly used to replace insecure protocols like **Telnet**, which can be easily sniffed, hijacked, or subject to data injection. When properly implemented, SSH eliminates these security concerns. It also includes the capability to transfer files securely, replacing protocols like FTP, TFTP, and CIFS.
* **Port Forwarding (Tunneling):** This feature allows SSH to secure otherwise insecure applications such as Telnet, FTP, POP, or HTTP. This is accomplished by creating an SSH tunnel that forwards the traffic over the insecure network to the SSH server, which then sends the packets to the final destination (like an email server). This technique may be used by legitimate users or malicious attackers to **bypass firewall rules**.
* **Device Management:** SSH is recommended for managing network devices (such as access points) instead of cleartext protocols like Telnet or unencrypted HTTP and SNMP.

#### Security Considerations (MITM Attacks)

Like SSL/TLS, some implementations of SSH are susceptible to **Man-in-the-Middle (MITM) attacks**.

* A malicious attacker can intercept the public-key handshake and replace the exchanged keys with counterfeit keys, thereby compromising the session.
* Mitigation strategies include implementing a **Public Key Infrastructure (PKI)** or holding **key-signing parties** to verify key authenticity.
* Users must be trained on **what MITM error messages look like**, as they are often disregarded.

Finally, due to SSH's flexibility and ubiquitous access, great care must be taken during its implementation, as it is a tool commonly used by attackers. For wireless devices like laptops, SSH host keys (private keys) should be password-protected and revoked immediately if the laptop is lost or stolen.

## WTLS

**Wireless Transport Layer Security (WTLS)** is a security protocol that was based on **SSL/TLS**. It serves as the **security layer of the Wireless Application Protocol (WAP)**.

#### Functionality and Design Rationale

1. **Purpose:** WTLS was designed to provide **privacy, data integrity, and authentication** for WAP users.
2. **Necessity (Why not SSL/TLS?):** SSL/TLS was considered **unsuitable** for wireless networks due to the severe constraints of the cellular handsets, such as their **low bandwidth** and **hardware limitations**.
3. **Transport Difference:** WTLS differs from SSL/TLS primarily in the transport layer. SSL relies on the reliable **Transmission Control Protocol (TCP)**. However, WAP devices using WTLS only use the **User Datagram Protocol (UDP)**, which is connectionless. Therefore, reliability functions, such as the retransmission of lost or out-of-order packets, had to be **included within WTLS** itself.
4. **Handshake and Cryptography:** WTLS supports a combination of symmetric and asymmetric algorithms to authenticate and encrypt a connection. It can be used to secure other protocols, such as **Wireless Markup Language (WML)**.

#### Authentication Classes

WTLS defines three classes of authentication that can be negotiated during its handshake process:

* **WTLS Class 1:** Anonymous — no certificates are used, and neither the client nor the gateway authenticates the other. Used simply to set up an **encrypted channel**.
* **WTLS Class 2:** Server certificate only — the client (typically the handset) authenticates the server. Considered equivalent to shopping over an SSL link from a wired browser.
* **WTLS Class 3:** Client and server certificates — the most secure class, normally involving the implementation of a **Public Key Infrastructure (PKI)**.

<details>

<summary>The WAP Gap Vulnerability</summary>

WTLS is fundamentally linked to the **WAP Gap**, a critical security vulnerability found in the initial WAP architecture (WAP 1.x).

* **Architecture:** The WAP approach required two protocols: WTLS from the wireless handset to the **WAP gateway**, and SSL from the WAP gateway to the web server.
* **Vulnerability:** During the protocol conversion from WTLS to SSL at the WAP gateway, the data was **unencrypted and then reencrypted**, leaving the data **temporarily in an exposed, unencrypted form**.
* **Impact:** This vulnerability created a level of concern about wireless security that **delayed consumer adoption**. Due to the WAP Gap, many content providers focused initial WAP services only on information that did not require security, such as weather and news, and plans for mobile commerce requiring end-to-end security were scaled back.

The WAP Forum intended WTLS to evolve, and future versions of the WAP specification (WAP v2.0) are designed to migrate to a **TLS-centric design** to eliminate the WAP Gap entirely.

</details>

## WEP

WEP, or **Wired Equivalent Privacy**, is a critical topic in wireless security, as detailed in **Chapter 3: Introduction to Wireless Security Protocols and Cryptography**.

Here is a comprehensive overview of WEP based on the sources:

#### Design and Mechanism

* **Standard Inclusion:** WEP is the **security mechanism included in the 802.11 standard**.
* **Purpose:** It was designed to provide **confidentiality and authentication services**, specifically aiming to offer the same level of security found in a wired network.
* **Cryptographic Basis:** WEP is based on the **RC4 stream cipher algorithm**.
* **Encryption Process:** Packets are encrypted by generating an RC4 stream. This stream is generated using a combination of a shared key and a **24-bit initialization vector (IV)**. The IV is used to make the RC4 stream generated with the shared key different for many of the data transmissions. The data is then XORed with the generated stream and transmitted in a WEP frame with the IV in the header, allowing the receiver to generate the same RC4 stream for decryption.
* **Mandate:** The current security standard, 802.1x, includes the **mandatory use of 128-bit keys for RC4 data encryption**.

#### Vulnerabilities and Failures

* **Inadequacy:** Due to implementation flaws and key management issues, WEP has been proven to be **"almost useless"** for providing authentication and confidentiality on a wireless network. The new security mechanisms created for the physical and data link layers (like WEP) were found to be **"less than effective"**.
* **Key Recovery:** Weaknesses exposed in the WEP design allow an attacker to **completely recover the WEP key** after capturing minimal network traffic. Tools are freely available on the Internet that allow a skilled attacker to recover the key in a number of hours.
* **Key Management Issues:** A primary problem with WEP is that it typically uses a **single static key** for all users on a given wireless network, making the key **very difficult to protect** and requiring frequent changes. Controlling access to these keys and detecting compromises is nearly impossible.
* **Known Plaintext Attack:** The shared authentication scheme (used in 802.11) leaks WEP key information to attackers through known plaintext methods, meaning shared authentication should **never be used**; always use an open system instead.
* **Data Storage Risk:** Some wireless cards store WEP keys in the Windows registry in cleartext. If WEP must be relied upon for security (which is not recommended), a card that stores the WEP keys in nonvolatile random access memory (NVRAM) on the Personal Computer Memory Card International Association (PCMCIA) card should be chosen.

#### WEP in Practice and Mitigation

* **As a Deterrent:** WEP can be used as a **first line of defense** to slow attackers down, but it cannot be relied upon for security.
* **In conjunction with 802.1x:** Some later implementations of WEP, often bundled with 802.1x functionality upgrades, **negotiate a WEP key** at the time of initial authentication. Advanced implementations can also **rekey during the session** without the user's awareness. This dynamic key usage nullifies many of the original WEP weaknesses that relied on the unchanging nature of the key.
* **Key Hashing:** Many vendors have implemented **WEP key hashing**, which is the process of hashing the initialization vector (IV) and shared key before generating the RC4 stream. This is highly effective at preventing key recovery via passive attacks, but these features are currently **vendor proprietary and not interoperable**.

In essence, while WEP was intended to be the confidentiality solution for wireless networks, its foundational security flaws, particularly related to static key usage and the RC4 algorithm implementation, mean it is generally considered inadequate on its own for robust security. Protocols operating at or above the Network Layer, or enhancements like 802.1x, are necessary to achieve effective security.

## 802.1x

The **802.1x** standard is a critical security protocol addressed in **Chapter 3: Introduction to Wireless Security Protocols and Cryptography**. It is designed to enhance network security before higher-level Layer 3 protocols (such as IP) are established.

!\[\[/Attachments of Obsidian Notes'/Unit 2-1763833595403.webp]]

<figure><img src="../.gitbook/assets/Unit 2-1763833595403.webp" alt=""><figcaption></figcaption></figure>

#### Core Functionality and Location

* **Layer 2 Protocol:** 802.1x operates at the **Data Link Layer** of the OSI model.
* **Authentication Focus:** Its basic purpose is to **authenticate users**. When a connection is first established, only 802.1x traffic is permitted to pass; other protocols like DHCP and IP are blocked.
* **Key Establishment:** It can be optionally used to **establish encryption keys**.
* **Scope:** The technology is **not specific to 802.11** and can be used on other 802-based LANs, including Ethernet and Token Ring networks.

#### Mechanism and Implementation

* **EAP Usage:** 802.1x utilizes the **Extensible Authentication Protocol (EAP)** for user authentication. EAP authentication packets, often containing user login information like a username and password, are sent to the access point.
* **RADIUS Integration:** The access point typically authenticates the user via **Remote Authentication Dial-in User Service (RADIUS)**.
* **Connection Enablement:** Once the user is successfully authenticated (and optional encryption is established), communication is enabled, allowing other protocols like DHCP to pass.

#### Role in Wireless Security

* **Addressing WEP Flaws:** 802.1x is vital because it addresses many security shortcomings of the 802.11 standard's native security mechanism, **Wired Equivalent Privacy (WEP)**.
* **Dynamic WEP Keys:** Later implementations of WEP are often bundled with 802.1x functionality, enabling the system to **negotiate a WEP key** at the time of initial authentication. Advanced implementations can also **rekey during the session** without the user's awareness. This use of dynamic keys nullifies many weaknesses associated with WEP's static key reliance.
* **Mandatory Requirements:** The approved 802.1x standard includes the **mandatory use of 128-bit keys for RC4 data encryption**. It also mandates encryption key rotation and blocking network activity until authentication is successful.
* **Eliminating Static Keys:** With 802.1x, there is no need to distribute static WEP keys to stations.

#### Implementation Considerations

* **Dependencies:** Implementing 802.1x requires additional back-end equipment, notably a RADIUS server capable of 802.1x functionality. This extra management overhead should be factored into deployment plans.
* **Vendor Interoperability:** While 802.1x is an approved standard (June 2001), vendor interoperability was limited at the time the sources were written.
* **Vulnerabilities:** Published vulnerabilities exist with 802.1x, including a problem that allows an attacker within wireless range to **hijack a user's session**. Using encryption with dynamic keys helps to mitigate this issue.
* **Deployment Example:** An enterprise design using 802.1x successfully leveraged the standard for authentication and dynamic WEP key creation, implementing three-hour time-outs to force frequent key changes and utilizing key-hashing features.

## IPsec

**IP Security (IPSec)** is a set of protocols designed to provide security at the network layer, specifically the **IP layer**. It is lower in the protocol stack than protocols such as SSL/TLS, SSH, or WTLS. IPSec was developed by the IETF working group and continues to evolve.

IPSec is the foundational technology for most **Virtual Private Networks (VPNs)** currently utilized on the Internet. Due to its flexibility and wide application support, many organizations choose to use IPSec for securing their wireless applications.

!\[\[/Attachments of Obsidian Notes'/Unit 2-1763833613037.webp]]

<figure><img src="../.gitbook/assets/Unit 2-1763833613037.webp" alt=""><figcaption></figcaption></figure>

#### Core Functionality and Algorithms

IPSec provides security services through distinct components that can be implemented together or separately:

1. **Authentication Header (AH):** Provides data authentication. AH prevents tampering with data during transport and positively identifies the sender, but it does **not** provide confidentiality against sniffing.
2. **Encapsulated Security Payload (ESP):** Provides encryption. ESP provides confidentiality and basic authentication services. Many administrators choose to implement both AH and ESP.

IPSec employs various cryptographic algorithms for these purposes:

* **Common Encryption Algorithms (for ESP):** DES, **Triple DES (TDES)**, and **Advanced Encryption Standard (AES)**. The IPSec standard mandates that **AES** be implemented in all IPSec implementations.
* **Common Authentication Algorithms (for AH):** **MD5** and **SHA**.

#### Encapsulation Modes

IPSec supports two modes for encapsulating data:

* **Transport Mode:** Used primarily when communicating between two hosts. It encrypts only the data portion of the IP packet, leaving all header information unencrypted.
* **Tunnel Mode:** Encrypts the **entire IP packet, including the headers**. This mode is more flexible for Internet applications, particularly where private network addressing (RFC 1918) is used.

The most common implementation of IPSec is for **remote-access VPNs** over the Internet. In this scenario, users establish an IPSec tunnel (usually employing tunnel mode with ESP and AH) to a **VPN gateway** located on the corporate network perimeter.

#### Wireless Deployment Context

* **Wireless LANs (Enterprise Design 1):** IPSec appliances are commonly used to create the corporate VPN infrastructure, enabling remote and wireless access.
* **Point-to-Point Configuration:** For wireless links where both connection ends are static and known, traditional IPSec-based VPN tunneling software or appliances are easily used to protect all traffic. Best practices recommend using **IPSec tunnel mode** with strong encryption like **AES or TDES**, and rekeying the VPN frequently.

Note: While IPSec is an approved standard, vendor interoperability can be limited; many IPSec appliances fully interoperate only with equipment from the same vendor.
