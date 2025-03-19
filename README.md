# SOC176 - RDP Brute Force Detected

### Event Details

* Event ID: 4624 (Successfully Logged In)
* Source IP Address: 218.92.0.56
* Destination IP Address: 172.16.17.148
* Destination Hostname: Matthew
* Protocol: RDP
* Firewall Action: Allowed
* Alert Trigger Reason: Login failure from a single source with different non-existent accounts

<img src="https://i.imgur.com/YUn8JCe.png" width="800"> 


## Investigation Process

1. Start Playbook
The source IP address originated from an external source.

<img src="https://i.imgur.com/XUlUpmN.png" width="500">

<img src="https://i.imgur.com/lXrPzuM.png" width="500"> 

2. IP Reputation Check
We checked the IP on VirusTotal, and it was flagged as suspicious. See the image below for the VirusTotal report.

<img src="https://i.imgur.com/0uTQFyk.png" width="500">

3. Connection Attempts

* Is there a request from the Attacker IP address to the target server's SSH or RDP port?

  * Yes, we confirmed that the Attacker IP attempted to access port 3389 (RDP).
* Does the Attacker IP address try to establish an SSH/RDP connection with multiple servers/clients as the target?

  * No, the attacker was only attempting to access Host: Matthew.

### Confirmation of Attack
After verifying all information, we confirmed this was a successful brute force attack on the RDP service.

Confirmation Image:




Conclusion
### What We Did:

* We investigated an alert triggered by an RDP brute force attack (SOC176) based on multiple login failures from the same source IP with different non-existent accounts. The target machine, Host: Matthew, was found to be under attack.
  
* We conducted an IP reputation check using VirusTotal, which flagged the source IP address, confirming its suspicious nature.
  
*We verified the attacker's connection attempts to RDP port 3389 and confirmed that the attacker was targeting only Host: Matthew, not attempting to access multiple servers.

### What We Found:

* The source IP address, 218.92.0.56, was determined to be from an external source and was actively attempting a brute force attack against the RDP service.
  
* The attack was successful due to the brute force attempt, as confirmed through our investigation.
VirusTotal provided additional validation, further confirming the suspicious nature of the IP address.

### How We Solved It:

* After confirming the brute force attack, we decided to isolate Host: Matthew to prevent any further unauthorized access or potential compromise.
  
* The device was isolated from the network, and further monitoring was implemented to ensure that no other devices or services were targeted by similar attacks.
