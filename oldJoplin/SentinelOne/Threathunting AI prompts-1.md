Threathunting AI prompts

# Behavior

“Show me event viewer tampering and count events by user.”

“Find users trying to timestamp files or reset file timestamp TTP T1070.006 to blend in with the environment.”

“Show the top 10 endpoints with the most behavioral indicators broken down by Tactic and Technique.”

“Show lsass.exe credential dumping events.”“Show processes that touched more than 200 files in the past ten seconds.”

&nbsp;

# Threat Actor

“Am I being targeted by FIN12?”

“Find indicators for Andariel over the last 72 hours.”

“Find the SHA1 \[sha1 hash\] in my environment.”

“Are there any indicators of UNC1878 in my environment?”

“Check for Akira in my environment.”

&nbsp;

# Third Parties

“Find administrator accounts assigning privileges to non-admin users in my Okta logs.”

“Find users who failed to login to Okta at least 5 times in an hour.”

“Show all external connections from Palo Alto firewall logs that have originated from more than 100 unique sources.”

“Show the top senders of threat emails in Proofpoint logs.”

“Show documents that triggered data loss prevention (DLP) rule match events in Microsoft 365 logs.”

&nbsp;

# malware and ransonware

“Show renamed LOLBins that execute in my environment.”

“Show Powershell (or curl) connections to IPs outside of the US.”

“Show evidence of lateral movement over RDP or SMB.”

“Show me the last 5 events for username STARFLEET\\jeanluc. Make source process unique id the third column.”

&nbsp;

# Anomaly detection

“Show login network activity from my servers to or from non-US.”

“Find non-Windows processes that write files to the temp directory.”

“Show the last 5 events for \[username\] and group by computer name.”

&nbsp;

# Advanced Investigation

Analysts can chain queries to “pivot” investigations:

Start broad (e.g., “Show all abnormal logins for \[user\] in Okta over the past week.”)

Drill down (e.g., “Which of these logins came from new geographic regions?”)

Summarize & report (e.g., “Draft an email summarizing these events for my colleagues on the next shift in the SOC.”)