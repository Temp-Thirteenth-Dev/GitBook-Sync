# Unit 4

## CDPD

The Cellular Digital Packet Data (CDPD) network standard was developed in the United States in the early 1990s through a collaborative effort among the country's regional phone companies, often referred to as Baby Bells. CDPD was created to offer wireless data services by utilizing the existing Advanced Mobile Phone Service (AMPS) infrastructure.

#### CDPD Architecture

CDPD is a packet-switched network, making it compatible with the Internet because it is based on the Transmission Control Protocol/Internet Protocol (TCP/IP). It was capable of up to **19.2 Kbps throughput**, which was significantly faster (twice the speed) than many other competing alternatives available at the time, such as circuit-switched data over Global System for Mobile Communications (GSM) networks. A key benefit of CDPD is its **quick call setup**, as it does not require time to establish a dedicated circuit.

The architecture of CDPD networks is similar to wireless voice networks and includes several key components:

* **Mobile End System (M-ES):** These are the client devices, such as a PDA, cell phone, or laptop PC equipped with a wireless modem.
* **Mobile Database Station (MDBS):** The MDBS is located within each specific cell site and is the component that a CDPD mobile device connects to.
* **Mobile Data Intermediate System (MD-IS):** This system is responsible for most of the network's administrative functions and manages the roaming users.
* **Fixed End System (F-ES):** The F-ES is the component that interfaces the CDPD network with external networks, such as the Internet.

CDPD was designed to transmit data packets on cellular voice channels only when those channels were not actively in use, for example, during call setup. The ability to utilize the existing AMPS network hardware meant that operators could offer these wireless data services quickly and affordably.

#### CDPD Security

The security framework for CDPD prioritizes data encryption over the air and measures to prevent fraud and device cloning. The security process resembles the Code Division Multiple Access (CDMA) architecture because CDPD devices lack a tamper-resistant module, such as the GSM Subscriber Identity Module (SIM) card.

**Authentication and Encryption Process:**

1. **Unique Identifier:** CDPD devices are pre-programmed at the time of manufacture with a unique numeric value called the **Network Entity Identifier (NEI)**, which is stored locally in the device's memory and is used for authentication.
2. **Encrypted Channel First:** Unlike voice networks that authenticate over an unencrypted channel, CDPD establishes an encrypted channel _before_ initiating the formal authentication process.
3. **Diffie-Hellman Key Exchange:** The initial establishment of the encrypted channel relies on the **Diffie-Hellman key exchange**, an early use of asymmetric cryptography. This protocol allows two unknown parties (the device and the network) to securely exchange public keys to generate a shared secret session key, even over an insecure link.
4. **Ciphering Keys and Encryption:** After the Diffie-Hellman exchange provides a shared secret, the M-ES and MD-IS generate two ciphering keys. CDPD encryption relies on the **RC4 stream cipher**, an algorithm developed by RSA Data Security, with key sizes typically ranging between **40 and 128 bits**.
5. **Device Authentication:** To authenticate, the mobile device transmits its NEI and other unique identifiers to the MD-IS, which compares this information with an authentication server (similar to the Authentication Center in GSM networks).
6. **Spoofing Prevention:** CDPD utilizes a **Shared History Record (SHR)**, which functions like a call counter. This value is updated and synchronized every time a device connects, helping to prevent spoofing by rejecting out-of-sync SHR values.

**Vulnerabilities:**

CDPD networks share similar vulnerabilities with other wireless voice networks:

* **No Mutual Authentication:** The network does not authenticate itself to the device, only the device to the network. This security flaw allows for the possibility of a bogus base station appearing legitimate to the user and potentially retrieving keys and sensitive information.
* **Local Key Storage:** Due to the absence of a tamper-resistant hardware module, like a SIM card, the unique identifiers (NEI) are stored locally on the CDPD device, raising the possibility that a hacker could retrieve this sensitive information.

The long-term outlook for CDPD is uncertain, as carriers like AT\&T Wireless are migrating existing networks toward technologies such as General Packet Radio Service (GPRS), which supports faster data rates.

## Mobitex

Mobitex is a wireless data technology initially developed by Ericsson in the mid-1980s. It is a packet-based switching technology that is capable of achieving throughput rates up to **8 Kbps**. Mobitex transmits data in **512-byte blocks**.

Although Mobitex is considered an open, nonproprietary system, its specification, known collectively as the **Mobitex Interface Specification (MIS)**, is copyrighted and available under a royalty-free license. As of the time of the sources' publication, there were over 30 Mobitex networks operating across 23 countries globally, utilizing one of four frequency families: 80 MHz, 400 MHz, 800 MHz, or 900 MHz.

#### Mobitex Architecture

The Mobitex network design shares similarities with traditional cellular voice networks:

* Each Mobitex hand-held device (client) connects to a **base station**.
* The base station then connects to a **local switch**.
* The local switch connects to the Mobitex operator’s network backbone and can also interface with **external networks**, such as a corporate Local Area Network (LAN) or a gateway.
* The network infrastructure also utilizes **regional switches**, which manage a set of local switches.
* The **Network Control Center (NCC)** handles billing, monitors usage, and oversees overall network performance.

A unique architectural feature of Mobitex is its **peer-to-peer communication** capability. This allows two Mobitex devices to communicate directly without involving the entire network infrastructure. The base station coordinates the communication, minimizing **back-haul network traffic**. This contrasts with a cellular voice environment, where two cell phones in the same cell must communicate all the way back to the Visitor Location Register (VLR), which can cause congestion and dropped calls during high usage.

#### Mobitex Security Architecture

The Mobitex security architecture is generally considered secure, although its specifications are **not as widely published** as other standards, nor have they been subjected to the same level of scrutiny.

The security model utilizes the same general authentication principles found in cellular networks:

* Each Mobitex device contains a unique **serial number** and a **Mobitex Access Number (MAN)**.
* These values are stored locally on the hand-held device.
* The serial number and MAN are transmitted over the air to the base station, which forwards them to the NCC for authentication.
* The specific underlying algorithms utilized for encryption are not publicly disclosed.

Mobitex shares some security weaknesses with other standards, such as Cellular Digital Packet Data (CDPD):

1. **Lack of mutual authentication:** The authentication process is one-way, meaning the device authenticates to the network, but the network does not authenticate itself back to the device.
2. **Local key storage:** Devices store the unique serial number and MAN locally, which poses a risk if a hacker were to retrieve these identifiers from the device itself, as Mobitex devices lack a tamper-resistant module (like the GSM Subscriber Identity Module or SIM card).

For users concerned about these security issues, **enhancements are available** since Mobitex is a packet-based network and can support application layer encryption similar to that used in wired networks.

For example, the **Blackberry wireless e-mail pager** (offered by Research in Motion or RIM) operates on Mobitex networks and utilizes a detailed security architecture, which helped it overcome security objections from enterprise customers. This involves using an email redirector (desktop or server-based) that employs **symmetric Triple DES (TDES) encryption** to secure messages end-to-end between the PC/server and the handheld device.

Another example is the **Palm VII wireless handheld**, which operates on Mobitex and conducts a **Diffie-Hellman key exchange** to create a pair of DES-X keys for establishing an encrypted session.

### RIM

The RIM (Research in Motion) security architecture is built around providing **end-to-end encryption** for its wireless e-mail solution, primarily utilizing its **Blackberry** interactive pager device.

Key aspects of the security architecture include:

1. **Components and Function:** The solution consists of the **hand-held device** and **e-mail redirector software**, which can be deployed in either a desktop or server-based mode. These devices generally operate on **Mobitex networks** in North America. The system functions as a proxy for a user's PC-based e-mail account, forwarding incoming messages to the wireless device.
2. **Encryption Mechanism:** The core of the security relies on a **unique symmetric Triple DES (TDES) key** to encrypt messages. This security model contributed directly to RIM’s success with enterprise customers by helping them overcome security objections.
3. **Key Distribution:** The symmetric TDES key is created during the initial installation of the RIM desktop redirector software and is subsequently transferred to the RIM handheld via the **protected serial port link** between the PC and the handheld.
4. **Data Flow and Protection:**
   * In the **desktop redirector** model, the user’s PC retrieves, compresses, encrypts the message using the symmetric key, and then redirects it wirelessly to the handheld.
   * In the **server redirection** architecture, the Blackberry Enterprise Server automatically redirects and encrypts the e-mail to the handheld, using the shared symmetric key.
   * This symmetric key model prevents potential attacks against an individual PC because a hacker must have knowledge of the TDES key. It ensures that data is not decrypted until it reaches the authenticated Blackberry device.

RIM has also pursued expanding the architecture, planning to support faster data networks like **GPRS** in future handsets.

## Mobitex vs CDPD

Both **Mobitex** and **Cellular Digital Packet Data (CDPD)** are wireless data technologies that emerged in the mid-1980s to early 1990s, but they differ significantly in origin, architecture, and deployment strategy.

| Feature                 | Mobitex                                                                                                                                                                                                                                                | CDPD                                                                                                                                                                                 |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Origin/Development**  | Developed by **Ericsson** in the mid-1980s.                                                                                                                                                                                                            | Developed in the US by the **Baby Bells** in the early 1990s.                                                                                                                        |
| **Data Throughput**     | Capable of rates up to **8 Kbps**.                                                                                                                                                                                                                     | Capable of rates up to **19.2 Kbps**.                                                                                                                                                |
| **Technology Base**     | Packet-based switching technology.                                                                                                                                                                                                                     | Packet-switched and **Transmission Control Protocol/Internet Protocol (TCP/IP) based**.                                                                                              |
| **Infrastructure Cost** | Required entirely **new infrastructure and hardware**. This higher initial investment motivated operators to keep the networks running.                                                                                                                | Designed to run on the **legacy Advanced Mobile Phone Service (AMPS) network hardware**, resulting in low initial infrastructure costs.                                              |
| **Architecture**        | Networks are structured with base stations connected to local and regional switches, overseen by a Network Control Center (NCC).                                                                                                                       | Transmits data packets on the cellular network’s **voice channels when they are not in use**.                                                                                        |
| **Security**            | Security details are not widely published, but the architecture is generally considered secure.                                                                                                                                                        | Uses a **Diffie-Hellman key exchange** to establish an encrypted channel before authentication.                                                                                      |
| **Unique Feature**      | Offers **peer-to-peer communication** capability between two devices, which minimizes back-haul network traffic. Mobitex has achieved **greater geographic coverage** beyond the U.S. and benefits from a strong industry association led by Ericsson. | Utilizes quick call setup.                                                                                                                                                           |
| **Future Outlook**      | Although usage may wane due to competition from faster services, the investment in proprietary infrastructure suggests it will likely **outlast CDPD**.                                                                                                | The prognosis is unclear, as operators sought to eliminate legacy AMPS hardware (which CDPD runs on), making maintenance difficult to justify in favor of faster services like GPRS. |

RIM's (Research in Motion) successful **Blackberry** interactive pager solution operated on **Mobitex networks** in North America.

## General Packet Radio Service (GPRS) overview

Intro How Does GPRS Achieve Higher Throughput GPRS Architecture GPRS Security Issues GPRS Security

The General Packet Radio Service (GPRS) is a foundational step in the evolution of cellular networks toward higher data speeds, often referred to as **2.5G**.

#### Intro

GPRS is a new specification for **high-speed wireless data** developed by GSM operators. It was created because earlier second-generation (2G) GSM networks were entirely **circuit switched** and thus were not optimized for high-speed data, resulting in slow (less than or equal to 14.4 Kbps) and expensive wireless data.

As a **mobile wireless packet-data-based architecture**, GPRS offers several key advantages:

* **Compatibility with the Internet** GPRS provides an easy connection with Internet-based data because the Internet utilizes the Internet Protocol (IP).
* **Always-on connection** Packet switching eliminates the need to open a dedicated physical link (or circuit) for data transfer. This allows users to receive information only when they need to, without establishing a circuit-switched connection for every individual call.
* **Efficient networks** Radio spectrum is only utilized during the transmit or receive mode, allowing multiple users to share the same spectrum in a given area.

The costs of building GPRS-capable networks were relatively **minor** compared to true 3G networks, as GPRS did not require additional radio spectrum. For example, AT\&T Wireless estimated the GPRS upgrade cost at $300 to $400 million, while the 3G upgrade cost was at least $1 billion. The first GPRS networks were launched in Europe in the spring of 2001.

GPRS users achieve significantly higher data throughput for accessing the Internet and for receiving and sending e-mail. GPRS-enabled **handsets** are categorized into three classes:

* **Class A** terminals support GPRS and GSM and the simultaneous operation of both.
* **Class B** terminals support GPRS and GSM but cannot process both simultaneously.
* **Class C** terminals support only GPRS (such as a PC card).

#### How Does GPRS Achieve Higher Throughput

GPRS achieves significantly higher throughput than circuit-switched data by utilizing **many time slots in parallel**. Since GPRS is packet-based, data can be split into chunks and sent simultaneously on multiple channels to a handset, which then reassembles the data into the appropriate order.

GPRS itself does **not increase the capacity** of existing cellular networks; it is a technology upgrade that allows packet data to be utilized alongside circuit-switched voice traffic within the existing radio spectrum.

Initial data suggested that **circuit-switched voice** would continue to receive priority on GPRS networks. However, the bursty nature of GPRS allows data to be sent even in congested cells, as the phones continually retry sending the data automatically without user intervention (unlike manually redialing in the circuit-switched environment).

#### GPRS Architecture

The GPRS network architecture utilizes the existing **GSM architecture** components (such as base stations, Mobile Switching Centers \[MSCs], and Home Location Registers \[HLRs]) but adds two crucial new components:

1. **SGSN (Serving GPRS Support Node)**: This is essentially a **data router** that controls data delivery within a geographic area. The SGSN handles **GPRS authentication and encryption**.
2. **GGSN (Gateway GPRS Support Node)**: This serves as the **interface (gateway) to external data networks** like the Internet. The GGSN is responsible for **IP address allocation** to mobile stations.

The SGSN and GGSN can be combined into a single GPRS Support Node (GSN), but this deployment scenario is uncommon.

GPRS also requires several other network components:

* A **Charging gateway** tracks GPRS data usage for billing.
* A **Border gateway** communicates with other operators, enabling intranetwork GPRS roaming.
* A **Lawful interception gateway** provides functionality for authorities to wiretap GPRS mobile data traffic.
* A **Domain Name Server (DNS)** converts hostnames into numeric IP addresses.

#### GPRS Security Issues

Because GPRS connects the wireless network to **public networks** such as the Internet, it introduces new security threats that must be addressed. Previous wireless voice-only networks were closed, making access more difficult.

Since GPRS is **packet and IP based**, it is susceptible to the same security threats faced by the wired Internet:

* **Denial of Service (DoS)** This attack involves overwhelming a resource to prevent it from providing service. In GPRS, a DoS attack could potentially be launched against the **GGSN** (stopping all GPRS service for subscribers) or even against an individual mobile phone to stop it from operating.
* **IP address spoofing** A hacker determines a valid numeric IP address and creates genuine-appearing data packets to send to unsuspecting users, potentially retrieving sensitive data such as passwords and credit-card numbers.

#### GPRS Security

GPRS security utilizes the same underlying security infrastructure as traditional GSM, including SIM cards and associated algorithms, to address two fundamental issues: **subscriber authentication and data encryption**.

**Subscriber Authentication** GPRS authentication follows the traditional GSM subscriber authentication process, but the **SGSN acts as the VLR**. The SGSN retrieves the 32-bit random number (RAND), the subscriber's secret key (Ki), and the signed response (SRES). The handset and SGSN complete simultaneous calculations to generate the SRES, and if the results match, authentication is successful.

**Data Encryption** After successful authentication, data encryption can be used. A **ciphering key (Kc)** is generated using the SRES, RAND, and Ki, and this key is used to establish **encrypted data communication between the handset and network**.

* GPRS packets are encrypted from the **handset to the SGSN**.
* Base stations **cannot decrypt GPRS traffic** because they lack the capability to arrange packets from different time slots into the correct order, which protects against eavesdropping even if a base station is compromised.
* It is critical that the **SGSNs are properly protected**, as their compromise could jeopardize the entire GPRS system.

The IP architecture of GPRS enables the use of new security measures, particularly **Virtual Private Networks (VPNs)**. However, VPN implementation is complicated because GPRS operators typically allocate IP addresses on a **dynamic, per-session basis**, meaning a user's IP address changes frequently. This conflicts with VPNs, which usually require a static IP address.

In the interim, solutions include creating a VPN tunnel between the **GGSN and the corporate network**. This solution, however, is not true end-to-end security because data is **unencrypted between the SGSN and GGSN**, and it requires mutual trust and investment between the enterprise and the mobile operator.

## Wireless Application Protocol (WAP)

The WAP Device The WAP Gateway WAP Security Model Key Points about the WAP Gap and WTLS

The Wireless Application Protocol (WAP) is a specification designed by GSM operators to create a common architecture for accessing the wireless Internet. Although it is widely supported by industry players, the WAP architecture is **not a technology standard recognized by major standards bodies** like the Internet Engineering Task Force (IETF).

WAP was developed due to the limitations of earlier cellular networks, which were constrained by data connection speeds as low as 9.6 Kbps and wireless handsets with small monochrome displays and minimal processing capabilities.

#### The WAP Device

WAP devices, such as multipurpose phones or Personal Digital Assistants (PDAs) with WAP capabilities, contain a **WAP microbrowser**.

* The microbrowser contains the **WAP protocol stack**, which is analogous to the standard TCP/IP stack but is optimized for wireless performance to deal with high packet loss and slow bandwidth.
* Content is presented in **Wireless Markup Language (WML)**, a format related to HTML.
* WAP microbrowsers can execute scripts via the **WMLScript** programming language.
* Devices are categorized as "multipurpose phones" or browsers developed for PDAs (like Palm and PocketPC) that access WAP data via an external wireless modem or infrared port.

#### The WAP Gateway

The WAP Gateway is an essential server component that sits between the wireless handset and the web server, designed to simplify the transition from the wired Internet to the wireless world. In initial rollouts, the WAP Gateway was typically managed and maintained by the network operator.

The WAP Gateway serves several key functions:

* **Protocol Converter** It translates WAP protocols (such as Wireless Transport Layer Security \[WTLS]) into wired protocols (such as Transport Layer Security/Secure Sockets Layer \[TLS/SSL] or TCP).
* **Content Converter** It translates HTML web pages into WML-compatible content.
* **Performance Optimization** It is designed to compress data as much as possible and reduce the protocol overhead and the number of roundtrips between the client and the content server.

#### WAP Security Model

The WAP security model uses **Wireless Transport Layer Security (WTLS)**, rather than traditional SSL, because SSL was unsuitable for early wireless networks due to performance limitations related to processing power and battery supply on handsets. WTLS provides **authentication, data encryption, and privacy**.

The WAP specification defines three classes of authentication:

1. **Class 1:** Anonymous authentication, where neither the client nor the gateway authenticates the other.
2. **Class 2:** Server authentication only (similar to SSL links in wired browsers).
3. **Class 3:** Both client and server authentication, which requires the use of a Public Key Infrastructure (PKI).

The WAP model also introduced the concept of the **Wireless Identity Module (WIM)** to securely store cryptographic keys and information necessary for WAP services, analogous to the SIM card used for voice authentication. WAP supports digital signing for transactions using a WMLScript function called **SignText**.

#### Key Points about the WAP Gap and WTLS

The most criticized aspect of the WAP security model was the **WAP Gap**.

* **The Nature of the Gap:** WTLS only encrypts data between the wireless handset and the WAP Gateway. Because the connection from the WAP Gateway to the external web server typically uses standard SSL, the data must be converted from WTLS to SSL protocols at the Gateway. During this conversion, the data is momentarily **unencrypted** (in cleartext).
* **Practical Risk:** Despite the negative publicity, the practical risks of taking advantage of the WAP Gap were considered **extremely minor** because WAP Gateways are usually deployed in secure, firewalled, and physically protected environments.
* **Mitigation:** Enterprises concerned about this vulnerability had the option to **host the WAP Gateway themselves** behind their corporate firewall, ensuring that the critical decryption process occurred within the secured corporate network.
* **Evolution:** WTLS was always designed to evolve. The WAP Forum planned to migrate to a **TLS-centric design in WAP v2.0**, which is expected to eliminate the WAP Gap entirely, aligning with the development of faster networks and handsets capable of handling the associated cryptographic processing.

The WAP Gap problem highlights a fundamental challenge in security implementation: even if a vulnerability is theoretically low-risk, public perception can severely delay consumer adoption, particularly for sensitive services like banking.

## Wireless Standards and Technologies

## Current and Future Technologies

Infrared Radio Spread Spectrum OFDM

#### Infrared (IR)

Infrared radiation (IR) involves **electromagnetic waves located in the spectrum just below visible light**.

* **Properties:** Like visible light, infrared **travels in straight lines and bounces off objects**, but it **cannot penetrate physical or opaque objects**.
* **Transmission:** Data is transmitted by **pulsing the radiation** (turning it on or off), similar to how light is used in fiber optics.
* **Usage:** IR is the type of technology used in many **remote control units for TVs, VCRs, and similar devices**. The 802.11 standard also defines diffuse infrared as a physical layer transmission method.

#### Radio

Radio uses **electromagnetic waves** that are emitted when an alternating current is input to an antenna. It is the **most widely used technology for wireless communications**.

* **Spectrum Allocation:** Because there is only a **limited amount of usable radio frequencies**, most spectrum has been **allocated for specific uses by different regulatory bodies** such as the Federal Communications Commission (FCC) in the United States.
* **Unlicensed Use:** Some frequencies are available without a license, notably the **Industrial, Scientific, and Medical (ISM) band**. If regulatory requirements (like transmission power restrictions) are met, this spectrum can be used for other purposes.
  * The **2.4 GHz range** typically has the most unlicensed usage, but the ISM band also includes some of the 900 MHz range in the U.S..
  * The **Unlicensed National Information Infrastructure (UNII) band** in the U.S. (5.15 to 5.35 GHz and 5.725 to 5.825 GHz) has also been specifically allocated for wireless LAN use.

#### Spread Spectrum

Spread spectrum is a method that involves **dividing data and sending it over a "spread" or wideband of different frequencies**.

* **Coexistence:** Spread spectrum signals appear to be **radio noise to narrowband devices**. This allows narrowband and wideband devices to coexist because the noise can be easily filtered out.
* **Types of Methods:** Common spread spectrum methods include:
  * **Frequency Hopping Spread Spectrum (FHSS):** The transmitter and receiver **hop from one frequency to another in prearranged synchronized patterns**. This quick hopping reduces the possibility of interference.
  * **Direct Sequence Spread Spectrum (DSSS):** Data is encoded by combining it with a multibit pattern (pseudo-noise code). This process, which can turn 1 bit of data into 11 bits, makes the data highly redundant and **more resilient to air loss**.

#### OFDM (Orthogonal Frequency Division Multiplexing)

OFDM is a **multicarrier modulation method** that enhances data transmission efficiency and reliability.

* **Mechanism:** It **divides a communications channel into a number of equally spaced frequency bands**. Each band transmits a portion of the user information, and each band is **independent of, or orthogonal, to every other band**.
* **Benefits:** This approach helps to **reduce multipath problems**—where reflected radio signals bounce back with slightly different timing—and thereby **increases the performance and data throughput**. The **802.11a** standard utilizes OFDM.

### Current and Future Standards

### IEEE 802

The Institute of Electrical and Electronics Engineers (IEEE) is a non-profit association that develops standards across various electrical and electronic fields. The **802 Local and Metropolitan Area Networks Standards Committee (LMSC)** defines the specifications related to Local Area Networks (LANs).

The IEEE 802 committee has been instrumental in creating and evolving several foundational wireless networking standards:

1. IEEE 802
   1. 802.11
   2. The ABCs of 802.11
      1. 802.11b
      2. 802.11a
      3. 802.11g
      4. 802.11j
      5. 802.11h and 5GPP
      6. 802.11e
      7. 802.11i
      8. 802.11f
   3. IEEE 802.15
   4. IEEE 802.16
   5. IEEE 802.1x The specifications you listed fall under the Institute of Electrical and Electronics Engineers (IEEE) 802 standards family, which governs local area networks (LANs), metropolitan area networks (MANs), and related security protocols. These standards are developed to ensure interoperability between vendors' products.

Here is an overview of the standards and associated task groups described in the sources:

#### IEEE 802 Standards Overview

* **IEEE 802:** This committee defines specifications for **Local and Metropolitan Area Networks (LMSC)**.
* **IEEE 802.11:** This workgroup was established in 1990 to develop a **wireless LAN standard**. The initial standard was completed in 1997, providing mandatory 1 Mbps and optional 2 Mbps data transfer rates using the **2.4 GHz ISM radio band**. The protocol exists entirely on the Physical (PHY) and Data Link (MAC) layers of the OSI model. The standard defines three transmission types (diffuse infrared, DSSS radio, and FHSS radio) and specifies the optional use of **Wired Equivalent Privacy (WEP)** encryption.

#### IEEE 802.11 Task Groups (The ABCs of 802.11)

The letter following "802.11" indicates the order in which the task group was proposed, investigating specific areas like higher speeds or security solutions.

| Standard             | Frequency Band        | Data Rate (Max) | Key Focus and Features                                                                                                                                                                |
| -------------------- | --------------------- | --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **802.11b**          | **2.4 GHz**           | **11 Mbps**     | The most widely recognized current standard; known as **WiFi**. Uses Complimentary Code Keying (CCK) with DSSS and is backwards compatible with earlier DSSS implementations.         |
| **802.11a**          | **5 GHz** (UNII band) | **54 Mbps**     | Uses Orthogonal Frequency Division Multiplexing (OFDM). Is **not backwards compatible** with 802.11b. Offers cleaner transmissions and more channels than the congested 2.4 GHz band. |
| **802.11g**          | **2.4 GHz**           | **54 Mbps**     | A draft standard designed to provide high rates (up to 22 Mbps using TI technology or 54 Mbps using OFDM) while maintaining **backwards compatibility** with 802.11b products.        |
| **802.11e**          | N/A                   | N/A             | Assigned to add **Quality of Service (QoS)** and multimedia capabilities to the MAC layer, benefiting all 802.11 versions.                                                            |
| **802.11i**          | N/A                   | N/A             | Formed to address serious 802.11 security issues, developing the **Temporal Key Integrity Protocol (TKIP)**. Recommendations include the mandatory use of **128-bit temporal keys**.  |
| **802.11f**          | N/A                   | N/A             | Developed the **Interaccess Point Protocol (IAPP)** to facilitate communication and **roaming** between access points.                                                                |
| **802.11h and 5GPP** | **5 GHz**             | N/A             | An adaptation of 802.11a features to meet European implementation requirements, adding **Transmit Power Control (TPC)** and **Dynamic Frequency Selection (DFS)**.                    |
| **802.11j**          | 5 GHz                 | N/A             | This task group was discontinued; its goal was to unify 802.11a and the European HiperLAN standards into a single global 5 GHz standard.                                              |

#### Other IEEE 802 Standards

* **IEEE 802.15 (Wireless Personal Area Network - WPAN):** This workgroup focuses on short-range wireless standards (roughly **10 meters** or less, known as the Personal Operating Space or POS). The focus is on low power consumption, size, and cost.
  * One task group (TG1) created a WPAN standard based on the **Bluetooth** 1.x specification.
  * Another task group (TG2) works specifically on providing **coexistence and interoperability** recommendations between 802.15 devices and 802.11 standards (as both often use the 2.4 GHz range).
* **IEEE 802.16 (Wireless Metropolitan Area Network - WirelessMAN):** This group is tasked with creating standards for **broadband wireless access**. The approved 802.16 standard operates in the **10 to 66 GHz range** with data rates up to 155 Mbps. The 802.16a group is extending the standard to cover the 2 to 11 GHz range, broadening the usable spectrum to 2 to 66 GHz.
* **IEEE 802.1x:** This is an **approved standard (June 2001)** that provides **network port authentication**. Its fundamental purpose is to authenticate users before higher-level protocols like IP are established. It utilizes the **Extensible Authentication Protocol (EAP)** and is often implemented via **RADIUS**. Crucially, it mandates the use of **128-bit keys for RC4 data encryption** and key rotation, and eliminates the need to distribute static WEP keys. This protocol is not limited to wireless, as it can be used on Ethernet and Token Ring networks.

## **IEEE 802.15**

It is the working group within the IEEE 802 Local and Metropolitan Area Networks Standards Committee (LMSC) tasked with creating **Wireless Personal Area Network (WPAN) standards**.

#### Focus and Scope

* WPANs are designed for wireless connectivity between fixed, portable, and moving devices that are located within or entering a **Personal Operating Space (POS)**.
* A POS is generally defined as a space of approximately **10 meters or less** around a person.
* The design priorities for 802.15 networks, in contrast to 802.11 networks, emphasize:
  * **Low power consumption**
  * **Small size**
  * **Low cost**

#### Task Groups

The IEEE 802.15 working group comprises four primary sub-task groups:

1. **TG1:** This group created a WPAN standard based on the **Bluetooth 1.x specification**. This standard defines both the Physical (PHY) and Media Access Control (MAC) layers, supporting a 1 Mbps data rate (with an actual throughput of about 700 Kbps). Devices intended for networking under this standard include computers, personal digital assistants (PDAs), printers, cellular phones, headsets, and pagers.
2. **TG2:** The objective of TG2 is to ensure **coexistence and interoperability** between 802.15 devices and 802.11 standards. This is particularly important because both standards often utilize the same **2.4 GHz radio frequency range**. TG2 is developing a recommended practice guide and proposing modifications to the 802.11 and 802.15 standards to enable these devices to successfully operate together.
3. **TG3:** This group aims to achieve **higher data rates of 20 Mbps or more** in WPANs, while still maintaining low power operation and cost.
4. **TG4:** The focus of this group is on achieving exceptionally low power consumption for 802.15 devices, targeting **battery lifetimes of months or years**. This task group focuses on low data rate applications (maximum of 200 Kbps) suitable for items like sensors, smart badges, remote controls, home automation, and interactive toys.

***

**Analogy:** If the IEEE 802.11 standards govern the security of a large corporate office floor (a Local Area Network), **IEEE 802.15** governs the security and operation of the small, personal "bubble" of devices immediately surrounding an individual, such as a phone connecting to a printer, much like a person managing the interaction of all the gadgets in their backpack..

## ETSI, Home RF, Ultra-wide band Radio (UWB)

#### ETSI (European Telecommunications Standards Institute)

ETSI is the **European counterpart to IEEE**. It is a **nonprofit standards organization** that creates telecommunications standards for deployment throughout Europe. ETSI comprises 789 members from 52 countries, both inside and outside of Europe.

ETSI has developed two key wireless LAN standards:

* **HiperLAN/1:**
  * Developed by the Subtechnical Committee RES10 in 1991 and **approved in 1996**.
  * It defines the Physical (PHY) and Media Access Control (MAC) specifications for wireless high-speed communications.
  * It uses **gaussian minimum shift keying (GMSK)** and specifies data rates up to **20 Mbps** between portable devices.
  * It operates in a dedicated European bandwidth (5.1 to 5.3 GHz) and therefore does not require spread spectrum technologies to coexist with other radio usage, unlike the 2.4 GHz ISM range.
  * It includes optional encryption and power savings.
  * A notable feature is **ad-hoc routing**, where intermediate nodes automatically forward data if the destination is out of reach, making it totally ad hoc and requiring no central controller.
  * However, **very few HiperLAN/1 products are commercially available**.
* **HiperLAN/2:**
  * Developed by the Broadband Radio Area Network (BRAN) group, it was **approved in February 2000**.
  * It is a redesign of HiperLAN/1 and was the **first standard to use Orthogonal Frequency Division Multiplexing (OFDM)**.
  * HiperLAN/2 and IEEE 802.11a are similar as both use the 5 GHz band and OFDM to reach data rates as high as **54 Mbps**.
  * A key difference is that HiperLAN/2 uses **Time Division Multiplexing (TDM)** in the MAC portion, enabling it to provide **Quality of Service (QoS)**, and is regarded as wireless Asynchronous Transfer Mode (ATM).
  * A major drawback is the current **lack of shipping products**, with commercial availability not expected until 2003. There were efforts (the 5 GHz Unified Protocol or 5-UP project) to create a single joint standard between ETSI and IEEE for the 5 GHz range.

#### HomeRF (Home Radio Frequency)

HomeRF is a technology label adopted by a group of manufacturers in 1998 to develop a standard for **wireless connectivity between personal computers and electronic devices**.

* The resulting standard is the **Shared Wireless Access Protocol (SWAP)**.
* SWAP enables both **voice and data transmission** with data rates up to **1.6 Mbps**.
* It targeted the **home market**, based on the premise that 802.11 devices would be too complex and costly for consumers.
* The popularity of 802.11 devices has somewhat **displaced HomeRF's market share**.
* HomeRF planned to release **SWAP 2.0**, which would use **wideband frequency hopping (WBFH)** to increase the data rate.
* The organization aimed to differentiate itself by promoting its standard for wireless communication encompassing **data, voice, and multimedia devices**.

#### Ultra-wide band Radio (UWB)

UWB is a relatively new transmission technology that utilizes a **very large frequency band**.

* In February 2002, the **FCC approved the use of UWB radio in the 3.1 through 10.6 GHz band**, paving the way for the use of radio impulse technology in wireless LANs.
* Unlike traditional sine waves, UWB transmits information using **digital pulses** timed very precisely across a very wide spectrum simultaneously.
* The high precision required means the transmitter and receiver must be coordinated to send and receive pulses with an accuracy of **trillionths of a second**.
* This transmission method helps **sidestep the multipath issues** typically associated with radio signals.
* Due to power restrictions mandated by the FCC, UWB signals appear as **radio noise to other frequency users**, which is why its use was approved in the 3.1 to 10.6 GHz range.
* UWB also features **low power consumption**, making it highly desirable for **portable wireless applications**.
