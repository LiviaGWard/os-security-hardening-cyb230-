# Module Three Labs: Network Configuration & Firewall Rules
**CYB-230 | Operating System Security**

## Lab 1: Basic Network Configuration (Linux)

### Part A — Ubuntu NetworkManager Configuration
**Task:** Manually configure a network interface using the NetworkManager service on Ubuntu.

**Steps completed:**
- Accessed NetworkManager configuration files
- Manually assigned IP address, subnet mask, gateway, and DNS settings
- Restarted the NetworkManager service to apply changes
- Verified configuration by displaying the final interface output

---

### Part B — CentOS Network Interface Configuration
**Task:** Manually configure a network interface on CentOS using the Network service.

**Steps completed:**
- Edited the network interface configuration file directly
- Assigned IP address, subnet mask, gateway settings
- Restarted the network service to apply changes
- Verified the updated configuration file output

**Key question: Three name formats resolve to the same IP — which is most useful?**

The **Fully Qualified Domain Name (FQDN)** is the most useful. A short hostname or alias can be ambiguous — the same name might exist in multiple contexts or be confused with another system. An FQDN (e.g., `server.helioshealth.internal`) is explicit and unique, eliminating ambiguity especially when the same IP serves multiple services. This is particularly important in security contexts where misidentifying a system can lead to incorrect access controls or incident response errors.

---

## Lab 2: Windows Firewall with Advanced Security

**Task:** Configure Windows Firewall rules using Administrative Tools and explain stateful inspection behavior.

**Steps completed:**
- Opened Windows Firewall with Advanced Security via Administrative Tools
- Created and configured firewall rules for specific traffic types
- Verified rule application at the command line

**Key question: Why is no inbound rule needed for ICMP echo replies?**

Because Windows Firewall uses **stateful inspection**. When PC1 sends an ICMP echo request (ping) to another host, the firewall records this as an outgoing connection. When the ICMP echo reply comes back, the firewall recognizes it as part of the same established conversation and allows it through automatically — without requiring a separate inbound rule. Stateful firewalls track the state of connections, so return traffic for legitimate outbound connections is always permitted.

This is more secure than stateless (packet-filtering) firewalls, which would require explicit rules for both directions of every communication.

---

## Skills Demonstrated
`NetworkManager (Ubuntu)` `CentOS Network Configuration` `Network Interface Files` `FQDN vs Hostname` `Windows Firewall with Advanced Security` `Stateful Inspection` `ICMP` `Firewall Rule Configuration` `Linux CLI`
