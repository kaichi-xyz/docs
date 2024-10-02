---
cover: ../.gitbook/assets/x-profile-bg.png
coverY: 0
layout:
  cover:
    visible: false
    size: full
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# P2P Direct Messaging

This article presents an overview of Kaichi's revolutionary Direct Message (DM) feature, emphasizing its decentralized nature, end-to-end encryption, and user-centric data ownership. Kaichi leverages the IPFS network and Solana blockchain to ensure secure and private messaging while empowering users to retain control over their own data. The concept of "PrivateLog" further decentralizes the messaging system, providing users with full ownership of their data. Additionally, the implementation of [Gossipsub](https://github.com/libp2p/specs/tree/master/pubsub/gossipsub) and [Messaging Layer Security (MLS)](https://messaginglayersecurity.rocks/) will enable scalability and enhanced group messaging capabilities. This post delves into the technical aspects of these features, highlighting the advantages they offer in terms of security, scalability, and data sovereignty.

## Introduction <a href="#introduction" id="introduction"></a>

Kaichi's DM feature introduces a paradigm shift in the world of communication platforms. Each user is uniquely identified by their IPNS address, derived directly from their Solana wallet. Messages are encrypted within the user's browser, transmitted through the IPFS network, and relayed across various nodes. The recipient retrieves the messages using their IPNS address and decrypts them using their Solana wallet signature, ensuring end-to-end encryption and secure message transmission.

## The Mechanism of Decentralized Messaging <a href="#the-mechanism-of-decentralized-messaging" id="the-mechanism-of-decentralized-messaging"></a>

The mechanism of Kaichi's DM hinges on the innovative integration of several technologies, including IPFS, IPNS, and Gossipsub. The system encrypts messages on the user's local browser before transmitting them via the IPFS network, which routes the encrypted messages through several nodes. The recipient subsequently listens to the IPFS network through various nodes to receive messages addressed to their IPNS address using Gossipsub, a publish/subscribe protocol.

Gossipsub's role in this system is vital for message propagation and handling. It operates on the basis of 'gossip,' where nodes randomly select a few other nodes and send them their message information. The selected nodes then repeat the process, rapidly disseminating the message across the network. By ensuring quick and robust propagation, Gossipsub mitigates common issues associated with network instability and node failures, and enables seamless communication between users while maintaining data integrity and security.

## End-to-End Encryption and Decentralization <a href="#end-to-end-encryption-and-decentralization" id="end-to-end-encryption-and-decentralization"></a>

The defining advantages of Kaichi's DM feature are its end-to-end encryption and decentralization. Unlike traditional messaging systems that rely on central servers, the Kaichi DM system leverages the decentralized IPFS network. This approach removes the necessity of trust in a central authority and ensures that messages remain private, accessible only by the sender and the intended recipient.

## Scalability: The Messaging Layer Security (MLS) Approach <a href="#scalability-the-messaging-layer-security-mls-approach" id="scalability-the-messaging-layer-security-mls-approach"></a>

Scalability, a paramount concern in communication systems, is addressed in Kaichi's DM feature through the integration of [Messaging Layer Security (MLS)](https://en.wikipedia.org/wiki/Messaging\_Layer\_Security). Unlike conventional encryption methods that cap group DMs at a maximum number of around 100 users, MLS can accommodate group DMs with hundreds of thousands of users. This leap in scalability is achieved through a continuous group key agreement protocol where updates to the group's key are made independently by members and securely propagated to the group.

## PrivateLog: A Unique Feature of Kaichi <a href="#privatelog-a-unique-feature-of-solcial" id="privatelog-a-unique-feature-of-solcial"></a>

A distinctive element of Kaichi's DM feature is the "PrivateLog", used to increase the decentralization and ownership of user data within the DM feature. In this design, users write encrypted messages to their personal 'outbox' inside a private log and notify the recipient of new messages via pubsub events. To read the messages, the recipient merges their private log with the sender's outbox log, effectively reconstructing the conversation without requiring a central server. Each user retains ownership of their data, by distributing encrypted payloads across the IPFS network, ensuring message persistence and retrieval efficiency through multiple node relays and IPFS pinning service providers.

## IPFS: InterPlanetary File System <a href="#ipfs-interplanetary-file-system" id="ipfs-interplanetary-file-system"></a>

The [InterPlanetary File System (IPFS)](https://ipfs.tech/) is a protocol designed to create a permanent and decentralized method of storing and sharing data. In contrast to traditional file-sharing methods, IPFS uses a distributed file system that connects all computing devices with the same system of files, minimizing the potential for data loss and ensuring optimal data availability.

## Future Directions <a href="#future-directions" id="future-directions"></a>

The future development of Kaichi's DM feature includes enabling multiple Solana wallets to share a single IPNS key with distinct signatures. This capability would allow users to send DMs from different devices, such as desktops or mobile phones, by recovering the encryption key and IPNS publication and signing the messages with the corresponding Solana wallet. This multi-device support enhances user flexibility and convenience while maintaining the underlying security and ownership principles.

***

## Comparative Analysis: Kaichi DM vs. Existing Messaging Platforms <a href="#comparative-analysis-solcial-dm-vs-existing-messaging-platforms" id="comparative-analysis-solcial-dm-vs-existing-messaging-platforms"></a>

<figure><img src="../.gitbook/assets/spaces2F3CiOS7bcK0Alvva51mmv2Fuploads2FQJ0YGRN62EshhijiIOpG2Fkaichi20direct20messages.png" alt=""><figcaption><p>Overview of Kaichi's messaging feature to other messaging platforms</p></figcaption></figure>

While assessing Kaichi's DM feature in relation to established messaging platforms such as WhatsApp, Telegram, Signal, Keybase, WeChat, and Discord, distinct differences surface, highlighting the unique advantages and potential limitations inherent to its design.

## 1. Advantages of Kaichi DM <a href="#id-1-advantages-of-solcial-dm" id="id-1-advantages-of-solcial-dm"></a>

### **Decentralization:**

Unlike centralized platforms such as WhatsApp, WeChat, and Discord, which rely on servers for message relay and storage, Kaichi's DM feature employs a decentralized model using IPFS and IPNS. This ensures no single point of failure or control, enhancing privacy and data integrity.

### **Scalability:**

Kaichi outperforms platforms like Signal in scalability due to its implementation of Messaging Layer Security (MLS), which allows group conversations to scale up to hundreds of thousands of users. This contrasts with Signal's double ratchet encryption which supports a maximum of 100 users in group chats.

### **End-to-end Encryption:**

While platforms like WhatsApp and Signal also offer end-to-end encryption, Kaichi augments this feature by providing users with a unique "PrivateLog" functionality. Users write encrypted messages to their own private logs, and distribute their data themselves via the IPFS network, truly embodying data ownership.

### **Interoperability:**

Unlike most traditional platforms, Kaichi plans to enable multiple devices sharing the same IPNS key but signing with different Solana wallets. This will facilitate seamless messaging across devices while maintaining secure encryption.

## 2. Potential Limitations of Kaichi DM <a href="#id-2-potential-limitations-of-solcial-dm" id="id-2-potential-limitations-of-solcial-dm"></a>

### **Usability:**

Given its advanced decentralized technology, new users to Kaichi might initially find its interface and functionality less intuitive compared to the straightforward design of platforms like WhatsApp or WeChat.

### **Dependence on Solana Wallet:**

Kaichi's DM feature requires a Solana wallet for login and key derivation. This dependence may present a barrier for users unfamiliar with blockchain wallets.

## 3. Conclusion <a href="#id-3-conclusion" id="id-3-conclusion"></a>

In conclusion, Kaichi's DM offers a groundbreaking approach to messaging by focusing on decentralization, scalability, and user data ownership. Although facing challenges typical for any new technology, it presents promising potentials that can redefine the way we perceive and own our digital communication.

## Private Group Chats for Token Holders

When you buy someone's on Kaichi, not only you are economically incentivised in their success, but you will also have access to a private group chat with the other token holders of that user.

This allows for more interactions with users of the same interests, on top of also being economically invested in that account.

These group chats aren't decentralised like 1-to-1 direct messages at the moment, for user-experience reasons, to ensure the group chat dynamic is as fast as group chats of web2 platform. We will continue our tests and hope to decentralise this feature soon too.
