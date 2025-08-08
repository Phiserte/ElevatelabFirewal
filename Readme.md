## Understanding windows Firewall 
- '''Get-NetFirewallRule | Format-Table Name, DisplayName, Direction, Action''' . This powershell command lists all the rules in the form of table with the name of the rule and if it is outbound or
  or inbound rule allowed or not allowed
## Examples of Firewall rules
- TPMVSCMGR-Server-Out-TCP : This is the firewall rule that  is responsible for managing virtual smart cards, which are a form of authentication and data security that uses a computer's Trusted Platform Module (TPM). The rule ensures that the service can communicate with remote servers to perform tasks like provisioning or updating virtual smart cards.
- SNMPTRAP IN-UDB : This rule allows network devices (like routers, switches, or servers) to send alert messages, or "traps," to your computer. For example, if a network printer runs out of toner, it could send an SNMP trap to your machine
## BLOCK THE TELNET
- ''' New-NetFirewallRule -DisplayName "Block Telnet Port 23" -Direction Inbound -LocalPort 23 -Protocol TCP -Action Block''' . This command blocks the port 23
- Telnet is an old, unencrypted protocol. By default, it sends data, including login credentials, in plain text. A malicious user could easily intercept this information. You block port 23 to prevent this unsecure service from being used, forcing users to use a more secure alternative like SSH (Secure Shell).
- '''Remove-NetFirewallRule -DisplayName "Block Telnet Port 23''' This command will remove the rule
## Summary
- Inspection: The firewall inspects every data packet that attempts to cross its boundary. It examines key information within the packet, such as the source and destination IP addresses, the port number, and the protocol (e.g., TCP, UDP, or ICMP).

- Rule Matching: It then compares this packet information against its list of rules. These rules are configured by an administrator or are part of the operating system's default settings. Each rule specifies a condition (e.g., traffic from a specific IP address on a particular port) and an action.

- Action: Based on the rule that the packet matches, the firewall takes one of two actions:

  - Allow: If the packet matches an "allow" rule, the firewall lets it pass to its intended destination.

  - Block/Deny: If the packet matches a "block" or "deny" rule, or if it doesn't match any "allow" rule (following a "deny-all" policy), the firewall drops the packet and prevents it from     reaching its destination.
