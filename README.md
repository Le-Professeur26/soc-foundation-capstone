SOC Foundation Capstone: Evidence Note

Project Overview
This project documents an investigation of suspicious authentication activity recorded in Windows and Linux system logs.

The purpose of the exercise was to examine authentication events, identify suspicious patterns, distinguish recorded facts from investigative assumptions, and explain what the available evidence could and could not establish.

Investigation Question
Did the Windows and Linux logs show suspicious authentication activity, what actions followed the successful logins, and what can the available evidence establish about the source devices and possible connection between the events?

Evidence Sources
The investigation used three main evidence sources:

Evidence file	Description
window.log	Windows Security events, including failed and successful logons, privilege assignments, account creation, and group membership changes.
auth.log	Linux SSH authentication, session, sudo, and user account activity.
dhcp.log	DHCP lease information used to investigate the possible identity and role of source devices.

Key Findings
1. Windows Activity
•	Six failed network logon attempts were recorded against different usernames between 14:02:11 and 14:02:21 UTC on March 14, 2026.
•	The attempts originated from 10.20.5.60.
•	A successful network logon for svc-backup was recorded at 14:02:24 UTC.
•	The same account was subsequently associated with creating helpdesk2 and adding it to the Administrators group.
•	A successful RemoteInteractive logon for helpdesk2 was recorded at 14:06:10 UTC.
2. Linux Activity
•	Six failed SSH password attempts were recorded from 198.51.100.77.
•	A successful password login for deploy followed at 14:11:30.
•	The deploy account used sudo to execute cat /etc/shadow.
•	A new Linux account named support was recorded as created at 14:13:02.

The Linux log does not contain a year. Its header states that the host clock is UTC.

3. Cross-Platform Comparison
The first recorded Windows failure occurred at 14:02:11, while the first Linux failure occurred at 14:10:01.

The difference was approximately 7 minutes and 50 seconds.

The events involved different source IP addresses and different target systems. The available evidence does not prove that the activities were carried out by the same person or operator.

Evidence Limitations
The investigation identified several limitations:
•	The logs do not identify the individual using the suspected Windows source device.
•	The DHCP IP-to-hostname mapping requires verification against the original lease information.
•	The Windows log transcription contains an incomplete field that requires checking against the original record.
•	The Windows logs do not reveal the actual passwords attempted.
•	The Linux logs do not establish whether the contents of /etc/shadow were copied or transmitted.
•	The logs do not independently establish who initiated the Linux account creation.
•	The available records do not prove that the Windows and Linux activities were connected.
•	The Linux authentication log does not specify the year.

Confidence Assessment
Overall assessment: Medium confidence.
There is reasonable evidence of suspicious authentication and subsequent account-management activity on both systems.

However, confidence in identifying the responsible individuals, proving unauthorized access, or establishing a connection between the Windows and Linux events is lower.

Additional endpoint, network, authentication, DHCP, and administrative records would help strengthen or weaken the assessment.

Repository Contents
•	README.md — Project overview and summary of findings.
•	Evidence-Note — Detailed evidence note in PDF.
•	Original-Logs — Original Windows, Linux, and DHCP log files used in the investigation.

Conclusion
This exercise demonstrates the importance of examining multiple log sources, correlating timestamps, identifying suspicious authentication patterns, and separating confirmed facts from assumptions.

The investigation also demonstrates why analysts must document evidence limitations and avoid making unsupported conclusions about attribution.

Project: SOC Foundation Capstone
Focus: Windows and Linux log analysis
Evidence date: March 14, 2026, where specified in the source records
