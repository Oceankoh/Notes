# Terms

## Common Vulnerabilities and Exposures (CVE)

List of disclosed computer security flaws in consumer software and hardware. Maintain by the MITRE Corporation. For a vulnerability to qualify as a CVE, it must meet a certain set of critieria. 

1. You must be able to fix the vulnerability independently of other issues
2. Acknowledged by the vendor
3. Vulnerability has evidence of security impact that violates the security policies of the vendor
4. Each product vulnerability gets a separate CVE

## Common Weakness Enumeration (CWE)

List of Software and Hardware Weaknesses. 

#### Difference between Weakness and Vulnerability

Weakness is an error or bug that may be escalated to a vulnerability in cases where it can be exploited to perform a malicious action. 

`weakness -> vulnerability -> exploit -> security breach`

## Common Vulnerability Scoring System (CVSS)

Set of standards to measure the impact of vulnerabilities. [Online calculator by NIST](https://nvd.nist.gov/vuln-metrics/cvss/v3-calculator). Metrics grouped into,

### Base Score Metrics

#### Exploitability Metrics
1. Attack Vector
2. Attack Complexity
3. Privileges Required
4. User Interaction
5. Scope

##### Impact Metrics
1. Confidentiality Impact
2. Integrity Impact
3. Availability Impact

### Temporal Score Metrics

1. Exploit Code Maturity
2. Remediation Level
3. Report Confidence

### Environment Score metrics

These metrics enable help to customize the score depending on the importance of the affected IT asset to the user's oragnaization. They follow the same metrics as the Base Score and effectively assigns each of them a weight. 

## National Vulnerbility Database

U.S. government repository of standards based vulernability management data represented using the Security Content Automation Protocol. The NVD include databases of security checklist references, security-related softawre flaws, misconfigurations, product names, and impact metrics. 

## Advisory

Public announcement for reported security vulnerabilities that document remediation steps. 

# CNA

Short for CVE Numbering Authority. A manufacturer can but might not necessarily be a CNA. A manufacturer that is not a CNA will need to approach a CNA with the vulnerability to obtain a CVE. 

# Bug Brokers

Middlemen who faciliate the bug bounties. They buy your bug and disclose it to the partnered organisations.