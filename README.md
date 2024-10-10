# L2sec_for_IOTA2P0
Implementation for L2sec Protocol on IOTA 2.0 using STM32 

## Introduction
This project is an open-source initiative to migrate the existing X-CUBE-IOTA1 repository from the IOTA 1.0 mainnet to the IOTA 2.0 mainnet. IOTA 2.0 introduces significant improvements, including **Decentralized Identity (DID)**, enabling secure, self-sovereign identities for IoT devices. By leveraging IOTA 2.0’s decentralized, feeless ledger, this project aims to build scalable IoT communication with integrated identity management.

## Purpose
The goal of this project is to adapt and enhance the original IOTA 1.0-based codebase to IOTA 2.0. The inclusion of **DID** ensures that devices can securely authenticate, interact, and manage data without centralized control, creating a more robust and flexible IoT ecosystem.

## Board Description: B-U585I-IOT02A

The **B-U585I-IOT02A** Discovery kit is an advanced evaluation board by STMicroelectronics designed to help developers prototype IoT applications. It is based on the **STM32U585AI** microcontroller, which offers high-performance, ultra-low-power operation. The board features multiple connectivity options, including Wi-Fi, Bluetooth, and various sensors (temperature, humidity, gas, pressure), making it ideal for IoT, sensor, and secure communication applications.

### Key Features:
- **Microcontroller**: STM32U585AI ARM Cortex-M33 with TrustZone.
- **Connectivity**: Wi-Fi, Bluetooth 5.0.
- **Sensors**: Temperature, humidity, gas, and pressure sensors.
- **Security**: Integrated secure element for enhanced security.

## Project Introduction

For this project, I will be using the **B-U585I-IOT02A** evaluation board to modify the **IOTA-Client** code, focusing on adapting it for compatibility with **IOTA 2.0 transactions**. Specifically, I will implement the **L2Sec protocol** within the IOTA 2.0 framework to ensure secure, feeless IoT transactions using this hardware.

---


### IOTA 1.0 and 2.0 Code Analysis (Focusing on Transaction Interface & DataType)

#### Step 1. IOTA 1.0, 2.0 Code Analysis (Focusing on Transaction Interface & DataType) (~25.03)

To analyze IOTA 1.0 and 2.0 from a transactional and datatype perspective, you can:

##### A. Understand the Transaction Structure
- In **IOTA 1.0**, transactions are mainly modeled around a **"bundle"** concept. A bundle contains multiple transactions with inputs and outputs, signed together as an atomic unit. This structure defines how the transaction is formed and verified on the Tangle.
  
- **IOTA 2.0** introduces a major shift with the **"Tangle 2.0"** (Coordicide) and changes the nature of transactions to improve scalability and remove centralization. Transactions are directly validated by referencing other transactions in a DAG (Directed Acyclic Graph) without needing bundles.

##### B. Transaction Interface:
- Explore the transaction interface, looking for how the transaction is created, validated, and broadcasted in both versions:
  - Look at transaction classes, methods, or structs that handle the core logic for defining transaction payloads, signatures, and validation rules.
  
- Key aspects to investigate:
  - How **inputs** and **outputs** are structured.
  - Handling of **addresses**, **signatures**, and **metadata**.
  - Changes to the **consensus rules** in transaction validation between 1.0 and 2.0.

##### C. Data Types:
- Investigate the core data types related to transactions:
  - In IOTA 1.0, you will see types for **trits** and **trytes**, which are used to encode data in a ternary (base-3) system.
  - IOTA 2.0 moves to a **binary** system, aligning more with traditional computer architectures. Data types evolve, optimizing how transactions are processed and validated.

---

#### Step 2. Code Analysis of [iota-core GitHub Repo](https://github.com/iotaledger/iota-core) (~25.06)

The IOTA Core repository on GitHub hosts the main code for IOTA 2.0. To analyze it:

##### A. Start by exploring the core modules:
- **`src/` directory** contains the core logic:
  - **Transaction modules**: Check files dealing with transaction creation, validation, and processing.
  - **Tangle modules**: Analyze how transactions are integrated into the Tangle's DAG structure.
  
- Explore the **`types/`** or **`models/`** folder for transaction-related data types.

##### B. Transaction Lifecycle:
- Look for functions or classes that define the **creation**, **validation**, and **propagation** of transactions. Focus on how inputs and outputs are managed, signatures are created, and validation rules are applied.

- **Validation and Consensus**: Analyze the consensus mechanism, especially in IOTA 2.0, where the Coordicide framework eliminates the coordinator and establishes a fully decentralized protocol.

---

#### 3. IOTA 2.0 Compatible Transaction Interface Implementation (~25.09)

To implement IOTA 2.0-compatible transaction interfaces using the **Client code from [STMicroelectronics IOTA-Client](https://github.com/STMicroelectronics/x-cube-iota1/tree/main/Projects/B-U585I-IOT02A/Applications/IOTA-Client)**, specifically focusing on making the **L2Sec protocol** compatible with IOTA 2.0 transactions, follow these steps:

##### A. Adapt the Client Code for IOTA 2.0:
- Modify the existing **IOTA-Client** to support the transaction structure and validation requirements of **IOTA 2.0**.
  - Update the handling of **inputs and outputs** to align with the new binary-based transaction structure in IOTA 2.0.
  - Ensure that the **Tangle 2.0 (Coordicide)** model is reflected in the client’s transaction processing logic.
  
- The key modification will involve making the **L2Sec protocol** function within the IOTA 2.0 transaction framework:
  - Adapt the **security layer** provided by L2Sec to handle transaction signing, verification, and validation according to the decentralized protocol of IOTA 2.0.
  - Ensure that L2Sec’s security mechanisms are compatible with the **binary** encoding used in IOTA 2.0.

##### B. Integrating L2Sec Protocol with IOTA 2.0:
- Extend the L2Sec protocol to work within the **IOTA 2.0 transaction lifecycle**, which removes the need for the coordinator and introduces a new consensus mechanism.
  
- Ensure that:
  - **Data encryption**, **authentication**, and **integrity checks** provided by L2Sec are maintained or enhanced for IOTA 2.0.
  - The protocol continues to support secure peer-to-peer communication while leveraging the new **Tangle** structure.

##### C. Testing and Validation:
- After adapting the client code and L2Sec protocol, thoroughly test the implementation:
  - Verify that transactions created by the IOTA-Client are fully compatible with IOTA 2.0’s Tangle.
  - Ensure that L2Sec successfully encrypts, signs, and validates IOTA 2.0 transactions.
  
- Run both unit tests and integration tests to ensure that the client operates securely and efficiently under IOTA 2.0’s new architecture.




## Reference
This project builds upon the [X-CUBE-IOTA1](https://github.com/STMicroelectronics/x-cube-iota1) repository, originally developed for IOTA 1.0. Our migration utilizes the latest IOTA 2.0 features, including **Decentralized Identity (DID)**, as outlined in the [IOTA 2.0 documentation](https://wiki.iota.org).

## Contribution Guidelines
We welcome contributions from the community! Please follow these guidelines:

1. **Fork the repository**: Create your own branch from `main`.
2. **Write clear commit messages**: Follow conventional commit standards (e.g., `fix:`, `feat:`).
3. **Submit Pull Requests (PRs)**: Ensure your PR is focused, well-documented, and tested.
4. **Code of Conduct**: Be respectful and inclusive. All contributors must follow our [Code of Conduct](link to code of conduct).
5. **Issue Reporting**: Before opening an issue, ensure it hasn’t been addressed by others. Provide detailed steps to reproduce the issue.
6. **Testing**: Contributions should include appropriate tests to ensure stability across IOTA 2.0 features.



## Review X-CUBE-IOTA1: Secure IoT Data Exchange with IOTA

### Overview
The X-CUBE-IOTA1 software package integrates IOTA’s Distributed Ledger Technology (DLT) with STM32 microcontrollers. It provides middleware to enable secure, scalable communication for IoT devices, leveraging the IOTA Tangle. This package offers sample applications that demonstrate secure messaging and data retrieval, optimized for resource-constrained IoT environments.

### Purpose
This project provides a secure data exchange solution for IoT devices using the IOTA Tangle, addressing the limitations of traditional protocols like TLS/DTLS. By utilizing IOTA's DLT, this project ensures data integrity, confidentiality, and scalability in IoT systems with minimal resource consumption.

### Key Features

1. **IOTA Tangle Integration**:  
   IOTA's Tangle is a fee-free, scalable distributed ledger that ensures secure, fast, and cost-effective data exchange. Each transaction validates two prior transactions, enabling the network to scale as it grows—ideal for IoT devices that need minimal transaction costs.

2. **L2Sec Cryptographic Protocol**:  
   L2Sec is a lightweight protocol tailored for IoT devices. It operates at Layer 2 and secures data transmissions by organizing them into encrypted, verifiable data streams, ensuring both confidentiality and integrity of the exchanged data.

3. **Hardware Security**:  
   Integration with the STSAFE-A110 secure element improves security by handling cryptographic operations (encryption, signing, etc.) in hardware, protecting against software vulnerabilities and offering hardware-based tamper resistance.

4. **Secure Data Stream**:  
   Data transmitted using L2Sec is structured into chained, encrypted messages anchored on the IOTA Tangle. This ensures an immutable, verifiable data stream with robust end-to-end security for real-time sensor applications.

### Main Components

1. **Secure Data Storage**:  
   Data is securely stored and anchored on the IOTA Tangle using indexation payloads. The immutable nature of the Tangle, combined with L2Sec’s encryption, ensures that stored data cannot be altered or tampered with.

2. **Authenticated Encryption**:  
   L2Sec employs Authenticated Encryption with Associated Data (AEAD) to protect both the confidentiality and authenticity of messages. This ensures that the data can’t be tampered with during transmission, while remaining lightweight enough for IoT constraints.

3. **STM32 Compatibility**:  
   X-CUBE-IOTA1 is optimized for STM32 MCUs, ensuring efficient performance in constrained environments. The lightweight nature of the L2Sec protocol allows it to run smoothly on devices with limited computational power and memory resources.

4. **Hardware Root-of-Trust**:  
   The integration of STSAFE-A110 provides a hardware root-of-trust, ensuring secure cryptographic operations like key generation and encryption. This makes the system resilient to physical and side-channel attacks, enhancing overall security for IoT applications.

### Implementation
The system works by encapsulating IoT data into a cryptographically secure structure using L2Sec, a protocol developed in C for efficient resource use. The project leverages STM32L4+ MCUs and the STSAFE-A110 secure element for enhanced security.

#### Main Components:
- **Secure Data Storage**: Data is anchored on the IOTA Tangle using secure indexation messages.
- **Authenticated Encryption**: Messages are encrypted and authenticated to prevent tampering or unauthorized access.
- **STM32 Compatibility**: Optimized for STM32 microcontrollers, ensuring efficient operation in resource-constrained environments.

### Use Case Example
A typical use case includes a constrained IoT device transmitting sensor data over the Tangle. The data is wrapped using L2Sec, encrypted, signed, and transmitted via a Wi-Fi module to an IOTA node. Any authorized device can retrieve, verify, and decrypt the data from the Tangle.

### Getting Started
1. Clone the repository:
    ```bash
    git clone https://github.com/STMicroelectronics/x-cube-iota1
    ```
2. Install the required dependencies and configure your STM32Cube environment.

3. Flash the STM32 MCU with the provided examples to start transmitting secure data over the IOTA Tangle.

### References
This project is based on the research paper "[Enabling Secure Data Exchange through the IOTA Tangle for IoT Constrained Devices](https://doi.org/10.3390/s22041384)" which introduces the L2Sec protocol and details the integration of IOTA with STM32 for secure IoT communication. 

### What is IOTA? 

# Introduction to IOTA

IOTA is an open-source distributed ledger technology (DLT) designed specifically for the Internet of Things (IoT). Unlike traditional blockchains, IOTA operates without the use of blocks or miners, which allows for feeless transactions, increased scalability, and faster confirmation times.

## Key Features of IOTA

1. **Tangle Technology**  
   IOTA's core innovation is the "Tangle," a unique type of directed acyclic graph (DAG). In the Tangle, each transaction must validate two previous transactions, ensuring that the network scales efficiently as more transactions are added.

2. **Feeless Transactions**  
   One of the most significant advantages of IOTA is that there are no transaction fees. This makes it ideal for IoT environments, where microtransactions are common, and paying fees on small transactions would be impractical.

3. **Scalability**  
   The more participants that use IOTA, the more scalable the network becomes. Since each transaction validates others, the system grows in efficiency as the number of transactions increases.

4. **Security and Decentralization**  
   IOTA aims for a highly decentralized network by removing miners and traditional validators. It uses a lightweight consensus mechanism, reducing power consumption and supporting secure interactions.

## Use Cases of IOTA

- **Smart Cities**: Enabling seamless, feeless microtransactions between smart devices and services.
- **Supply Chain Management**: Offering transparency and traceability across global supply chains.
- **eHealth**: Facilitating secure data sharing and transactions between medical devices.
- **Energy**: Supporting peer-to-peer energy trading in decentralized energy networks.

## IOTA's Vision

IOTA envisions a world where devices, machines, and people can exchange data and value securely and without intermediaries. With its scalable and feeless architecture, IOTA is positioned as a foundational technology for the evolving IoT landscape.

For more information, visit the [IOTA Wiki](https://wiki.iota.org/get-started/introduction/iota/introduction/).
