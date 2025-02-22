## Information
A valid API Token for XSOAR from Recorded Future needed to fetch information.
[Get help with Recorded Future for Cortex XSOAR](https://www.recordedfuture.com/integrations/palo-alto).

---

## Configuration
| Parameter                                      | Description                                                                                                                                                                                                                                 |
|------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Server URL                                     | The URL to the Recorded Future ConnectAPI.                                                                                                                                                                                                  |
| API Token                                      | Valid API Token from Recorded Future.                                                                                                                                                                                                       |
| Classifier                                     | Select "Recorded Future - Classifier".                                                                                                                                                                                                      |
| Mapper (Incoming)                              | Select "Recorded Future - Incoming Mapper".                                                                                                                                                                                                 |
| IP/Domain/URL/File/CVE/Vulnerability Threshold | Minimum risk score from Recorded Future needed to mark IOC as malicious when doing reputation or intelligence lookups.                                                                                                                      |
| Trust any certificate (not secure)             | -                                                                                                                                                                                                                                           |
| Use system proxy settings                      | -                                                                                                                                                                                                                                           |
| First fetch time                               | This threshold will be used during first fetch of the incidents.                                                                                                                                                                            |
| Rule names to fetch alerts by                  | Rule names to fetch alerts by, separated by semicolon. If empty, all alerts will be fetched.                                                                                                                                                |
| Alert Statuses to include in the fetch         | Alert Statuses to include in the fetch, separated by a comma. If empty, the default value of 'no-action' will be used. The value should be comma-separated alert statuses (e.g. "unassigned,assigned,pending,actionable,no-action,tuning"). |
| Update alert status on fetch                   | If selected, alerts with a status of 'no-action' will be updated to 'pending' once fetched by the integration.                                                                                                                              |
| Turn on "Incident Sharing"                     | Turning on "Incident Sharing" shares anonymized correlations from playbooks with Recorded Future to improve intelligence quality.                                                                                                           |
| Maximum number of incidents per fetch          | -                                                                                                                                                                                                                                           |
| Incidents Fetch Interval                       | -                                                                                                                                                                                                                                           |
| Indicator Expiration Method                    | -                                                                                                                                                                                                                                           |
| Source Reliability                             | Reliability of the source providing the intelligence data.                                                                                                                                                                                  |

---

## Available Actions
* Reputation actions
    * Using the new Recorded Future SOAR Enrichment API.
    * Available actions: ip, domain, url, file(hashes), cve.
* Intelligence action
    * Fetches full information for the entity.
    * Supports IPs, Domains, URLs, Files(hashes), Vulnerabilities(cve), Malwares.
* Malware search action
* Alert actions
    * Fetch alerting rules defined at Recorded Future.
    * Fetch alert summaries from one or more alerting rules.
    * Set alert status in Recorded Future
    * Set alert note in Recorded Future
* Threat assessment action
    * Takes a context, such as phishing or malware and one or more IOC as input.
    * Outputs a verdict (true/false) and related evidence (risk rules) for this context.

Copyright 2020-2022 Recorded Future, Inc.
