# Account Takeover via Prototype Pollution in NodeBB

### N-Day Details

This vulnerability is mentioned in GitHub Advisory GHSA-rf3g-v8p5-p675/CVE-2022-46164:

### CVSS Score
9.4 (Critical)
CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:L

### Impact
Due to a plain object with a prototype being used in socket.io message handling a specially crafted payload can be used to impersonate other users and takeover accounts.

### Patches
Patched in 2.6.1

Workarounds
Site maintainers can cherry-pick 48d1439 into their codebase to patch the exploit.

### References
A writeup is pending

## Your Tasks
- Set up a debugging environment for you to perform testing against the vulnerable version
	- You should also set up a debugging environment against the non-vulnerable version as well
- A report on the n-day vulnerability containing the following information:
	- Brief description of the vulnerability (somewhat like a CVE description)
	- CVSS Score/String
	- Affected & tested versions
	- Root cause analysis
	- Reproduction Steps
	- Patch Analysis
	- A proof-of-concept exploit script on how to exploit the vulnerability

### Don’ts
Usually when doing n-day, it’s also a viable strategy to research into the reporter to find additional information.

But since the reporter made full disclosure of the details already, then it defeats the purpose for you to do this n-day analysis if you read it.

As such, you are not allowed to read or use information from any of the following links:

- Reporter’s writeup: https://thegreycorner.com/2023/01/04/CVE-2022-46164-writeup.html and https://github.com/stephenbradshaw/stephenbradshaw.github.io
- Reporter’s PoC: https://github.com/stephenbradshaw/CVE-2022-46164-poc/
- My tweet: https://twitter.com/Creastery/status/1610530947778371588

You are to assume that no public information is made regarding this vulnerability, and all you have is that redacted advisory.