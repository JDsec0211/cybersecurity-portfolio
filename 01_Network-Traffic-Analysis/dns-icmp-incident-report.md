# DNS & ICMP Traffic Analysis – Incident Report

**Tools:** tcpdump  **Protocols:** DNS, UDP, ICMP  **Source:** Google Cybersecurity Professional Certificate

---

## 📋 Scenario

I worked as a cybersecurity analyst at a company that provides IT services to clients. Several customers reported that they couldn't reach the client website **www.yummyrecipesforme.com**. After the page tried to load, they got the error `destination port unreachable`.

I got the same error when I tried the site. To troubleshoot, I ran **tcpdump** and loaded the page again. To load a page, the browser first sends a DNS query over UDP to look up the site's IP address, then sends an HTTPS request to that address. The capture showed that every UDP packet sent to the DNS server came back with an ICMP error: `udp port 53 unreachable`.

---

## 🔍 Part 1: Summary of the Problem

The tcpdump log shows the client sending DNS queries over **UDP to port 53** on the DNS server. Instead of a DNS response, the client got **ICMP error messages** saying `udp port 53 unreachable`. That means the DNS request couldn't be delivered because nothing was available on port 53.

**Protocols involved:**
- **DNS:** resolves the domain name to an IP address
- **UDP:** carries the DNS query
- **ICMP:** reports the error back to the client

Because the ICMP errors kept repeating, the DNS service was clearly unavailable. The domain name couldn't be resolved, so users couldn't reach the website.

---

## 🧪 Part 2: Analysis and Possible Cause

The problem was first reported when users couldn't reach www.yummyrecipesforme.com and saw `destination port unreachable`.

I used tcpdump to capture network traffic during the investigation. The logs showed DNS queries going out over UDP port 53, and the DNS server answering with ICMP messages saying port 53 was unreachable. With no DNS resolution, the browser never got an IP address, so it couldn't load the site.

### Findings
- DNS requests were sent correctly
- UDP port 53 was used
- ICMP returned "port unreachable"
- DNS resolution failed

### Suspected Root Cause
The DNS server was **not listening on UDP port 53**. Possible causes:
- The DNS service was stopped
- A firewall was blocking port 53
- The DNS server was misconfigured

### Next Steps
1. Verify the DNS service is running
2. Review firewall rules for UDP port 53
3. Confirm port 53 is open and listening
4. Test DNS resolution again

---

## 🛠️ Skills Demonstrated
- Network traffic analysis with tcpdump
- Packet inspection and log interpretation
- DNS troubleshooting
- Understanding how UDP and ICMP interact
- Writing a cybersecurity incident report
