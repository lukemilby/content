This playbook investigates a "Brute Force" incident by gathering user and IP information, and calculating the incident severity based on the gathered information and information received from the user. It then performs remediation.
This is done based on the phases for handling an incident as they are described in the SANS Institute â€˜Incident Handlerâ€™s Handbookâ€™ by Patrick Kral.

https://www.sans.org/reading-room/whitepapers/incident/incident-handlers-handbook-33901

The playbook handles the following use-cases:

* Brute Force IP Detected - A detection of source IPs that are exceeding a high threshold of rejected and/or invalid logins. 
* Brute Force Increase Percentage - A detection of large increase percentages in various brute force statistics over different periods of time.
* Brute Force Potentially Compromised Accounts - A detection of accounts that have shown high amount of failed logins with one successful login.

Used Sub-playbooks:
- IP Enrichment - Generic v2
- Account Enrichment - Generic v2.1
- Calculate Severity - Critical Assets v2
- Isolate Endpoint - Generic
- Block Indicators - Generic v2
- SANS - Lessons Learned

***Disclaimer: This playbook does not ensure compliance to SANS regulations.

## Dependencies
This playbook uses the following sub-playbooks, integrations, and scripts.

### Sub-playbooks
* IP Enrichment - Generic v2
* Calculate Severity - Critical Assets v2
* Account Enrichment - Generic v2.1
* Isolate Endpoint - Generic V2
* Block Indicators - Generic v2
* SANS - Lessons Learned

### Integrations
This playbook does not use any integrations.

### Scripts
* GenerateInvestigationSummaryReport

### Commands
* send-mail
* ad-expire-password
* setIncident
* closeInvestigation
* ad-enable-account
* ad-disable-account

## Playbook Inputs
---

| **Name** | **Description** | **Default Value** | **Required** |
| --- | --- | --- | --- |
| username | Username of the user who is suspected of the activity. | incident.username | Required |
| src | Source endpoint that triggered the incident. | incident.src | Required |
| traps_endpoint_id | Traps endpoint ID, used for endpoint isolation. | incident.agentid | Optional |
| logins_count_threshold | The threshold for number of logins, from which the investigation and remediation will start automatically without waiting for the user's reply. Default is 10. | 10 | Optional |
| severity_threshold | The threshold for the severity value from which an automatic remediation takes place. <br/>Specify the severity number \(default is Critical\):<br/>0 - Unknown<br/>0.5 - Informational<br/>1 - Low<br/>2 - Medium<br/>3 - High<br/>4 - Critical | 4 | Optional |
| internal_range | A list of internal IP ranges to check IP addresses against. The list should be provided in CIDR notation, separated by commas. An example of a list of ranges would be: "172.16.0.0/12,10.0.0.0/8,192.168.0.0/16" \(without quotes\). If a list is not provided, will use default list provided in the IsIPInRanges script \(the known IPv4 private address ranges\). |  | Optional |
| critical_users | Critical users, separated by comma. |  | Optional |
| critical_endpoints | Critical endpoints, separated by comma. |  | Optional |
| critical_groups | Critical groups, separated by comma. |  | Optional |
| CustomBlockRule | This input determines whether Palo Alto Networks Panorama or Firewall Custom Block Rules are used.<br/>Specify True to use Custom Block Rules. | True | Optional |
| AutoCommit | This input determines whether Palo Alto Networks Panorama or Firewall Static Address Groups are used.<br/>Specify the Static Address Group name for IP handling. | No | Optional |
| IPListName | This input determines whether Palo Alto Networks Panorama or Firewall External Dynamic Lists are used for blocking IPs.<br/>Specify the EDL name for IP handling. | Demisto Remediation - IP EDL | Optional |
| DAG | This input determines whether Palo Alto Networks Panorama or Firewall Dynamic Address Groups are used.<br/>Specify the Dynamic Address Group tag name for IP handling. |  | Optional |
| StaticAddressGroup | This input determines whether Palo Alto Networks Panorama or Firewall Static Address Groups are used.<br/>Specify the Static Address Group name for IP handling. |  | Optional |
| URLListName | URL list from the instance context with which to override the remote file. | Demisto Remediation - URL EDL | Optional |
| CustomURLCategory | Custom URL Category name. | Demisto Remediation - Malicious URLs | Optional |
| type | Custom URL category type. Insert "URL List"/ "Category Match". |  | Optional |
| device-group | Device group for the Custom URL Category \(Panorama instances\). |  | Optional |
| categories | The list of categories. Relevant from PAN-OS v9.x. |  | Optional |
| EDLServerIP | This input determines whether Palo Alto Networks Panorama or Firewall External Dynamic Lists are used:<br/>\* The IP address of the web server on which the files are stored.<br/>\* The web server IP address is configured in the integration instance. |  | Optional |
| DataCollection | Use a data collection task to answer lessons learned questions based on SANS. Specify 'True' to automatically send the communication task, and 'False'  to prevent it. |  | Optional |
| Email | Email address to which to send the questions. |  | Optional |

## Playbook Outputs
---
There are no outputs for this playbook.

## Playbook Image
---
![Brute Force Investigation - Generic - SANS](../doc_files/Brute_Force_Investigation_-_Generic_-_SANS.png)