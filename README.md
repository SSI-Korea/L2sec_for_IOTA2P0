# L2sec_for_IOTA2P0
Implementation for L2sec Protocol on IOTA 2.0 using STM32 

## Introduction
This project is an open-source initiative to migrate the existing X-CUBE-IOTA1 repository from the IOTA 1.0 mainnet to the IOTA 2.0 mainnet. IOTA 2.0 introduces significant improvements, including **Decentralized Identity (DID)**, enabling secure, self-sovereign identities for IoT devices. By leveraging IOTA 2.0’s decentralized, feeless ledger, this project aims to build scalable IoT communication with integrated identity management.

## Purpose
The goal of this project is to adapt and enhance the original IOTA 1.0-based codebase to IOTA 2.0. The inclusion of **DID** ensures that devices can securely authenticate, interact, and manage data without centralized control, creating a more robust and flexible IoT ecosystem.

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
