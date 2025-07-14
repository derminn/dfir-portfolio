# 🛡️ DFIR Report – Network Traffic Analysis  
**Analyst:** Dharmin Panchal  
**Date:** July 14, 2025  
**Case ID:** DFIR-2025-001  
**Tool Used:** Wireshark  
**Capture File:** network-capture.pcapng  

---

## 🎯 Objective
Capture and analyze live network traffic using Wireshark. Focus on identifying key packet types such as DNS queries, TCP handshakes, HTTP/TLS communication, and interpreting packet structure as part of a simulated digital forensics scenario.

---

## 🧪 Lab Setup

| Item           | Value |
|----------------|-------|
| Operating System | Windows 10 |
| Network Interface | Wi-Fi |
| Tools Used       | Wireshark v4.x |
| Capture Duration | ~3 minutes |
| Sites Visited    | google.com, teams-ring.msedge.net |

---

## 📦 Protocol Summary

| Protocol | Purpose            | Notes |
|----------|--------------------|-------|
| DNS      | Domain Resolution  | Query to `www.google.com` |
| TCP      | Transport Protocol | Used to initiate secure connections |
| TLS      | Encrypted Traffic  | TLSv1.3 Client Hello captured |

---

## 🔍 Key Observations

### 🔹 1. DNS Query

| Field         | Value |
|--------------|-------|
| **Query Domain** | `www.google.com` |
| **Source IP**    | `fe80::5cdd:968c:97d6:8ac5` |
| **Destination IP** | `fe80::a291:caff:fe1f:4291` |
| **Protocol**     | DNS (UDP) |
| **Port**         | 53 |
| **Packet #**     | 16404 |

---

### 🔹 2. TCP Stream (HTTPS)

| Field            | Value |
|------------------|-------|
| **Domain**       | `teams-ring.msedge.net` |
| **Connection Type** | TLS (HTTPS) |
| **Client Packets** | 8 |
| **Server Packets** | 13 |
| **Stream Size**     | 10 KB |
| **Port**         | 443 |
| **Method**       | HTTP/2 GET Request |
| **TCP Stream #** | 50 |

---

### 🔹 3. TLS Handshake (Client Hello)

| Field             | Value |
|-------------------|-------|
| **Packet #**      | 15148 |
| **Source IP**     | `192.168.1.9` |
| **Destination IP**| `192.168.1.8` |
| **Protocol**      | TLS |
| **Version**       | TLS 1.3 (Negotiated via Client Hello) |
| **SNI**           | *(Not visible in screenshot; likely not set)* |

---

## 📸 Screenshots

- DNS Query to `www.google.com`  
  ![dns-query](screenshots/dns-query.png)

- TCP Stream with `teams-ring.msedge.net`  
  ![tcp-stream](screenshots/tcp-stream.png)

- TLS Handshake (Client Hello)  
  ![tls-handshake](screenshots/tls-handshake.png)

---

## 🧰 Filters & Tools Used

### ✅ Wireshark Filters:
- `dns`
- `tcp.flags.syn == 1`
- `tcp.port == 443`
- `http`
- `tls.handshake.type == 1`

### ✅ Other Tools:
- `ipconfig`, `tracert`, `ping`

---

## ✅ Conclusion

Successfully captured and analyzed live network traffic using Wireshark.  
This analysis covered:
- Domain resolution via DNS
- Encrypted communication over HTTPS
- TCP 3-way handshakes
- TLS Client Hello inspection

The packet inspection confirms clean communication behavior and demonstrates capability to identify and filter core protocols using Wireshark for digital forensics.

---

## 📁 Artifacts

- `network-capture.pcapng` – Original capture file  
- `report.md` – This markdown report  
- `screenshots/` – Supporting analysis screenshots

