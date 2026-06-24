# reticulum

cryptography-based networking stack for building autonomous, distributed networks with readily available hardware. operate over LoRa, packet radio, WiFi, serial, TCP, or any custom interface. supports high-latency, low-bandwidth scenarios with end-to-end encryption, multi-hop routing, and no central authority.

## core principles

- **no IP dependency** — complete networking stack built on cryptographic principles, not TCP/IP
- **multi-hop, auto-routing** — coordination-less globally unique addressing; mesh networks self-configure
- **initiator anonymity** — no source addresses in packets
- **forward secrecy** — per-packet and per-link ephemeral key derivation (X25519 ECDH)
- **unforgeable confirmations** — delivery proof via Ed25519 signatures
- **efficient** — link setup in 3 packets (297 bytes); link keep-alive at 0.44 bits/sec

## encryption & identity

- **identities** — 512-bit Elliptic Curve keysets (X25519 + Ed25519)
- **per-packet keys** — ephemeral ECDH + AES-256-CBC + HMAC-SHA256
- **link keys** — forward-secret session channels with sequencing

## architecture

Python reference implementation. extensible interface system — built-in types for LoRa/RF/serial/TCP; create custom interfaces for any medium.

| **type** | **use case** |
|----------|-------------|
| LoRa | long-range, low-bandwidth mesh |
| Packet Radio | 9k6 AFSK, D-STAR, P25, etc. |
| Serial | direct wired or RF modem link |
| TCP/UDP | tunnel through IP networks |
| Ethernet | backbone for high-bandwidth |

## transmission models

- **Packet** — single unreliable datagram
- **Link** — encrypted, sequenced, bidirectional; keeps-alive indefinitely
- **Channel** — reliable, ordered file/stream transfer with CRC32 + compression
- **Request/Response** — lightweight RPC with timeout/retry

## lineage

upstream OSS project: https://github.com/markqvist/Reticulum

vendored here for decentralized RF/mesh networking — LoRa and packet radio without traditional ISPs.
