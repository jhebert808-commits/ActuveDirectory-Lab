# Group Policy Troubleshooting

This folder contains notes and fixes for issues related to Group Policy (GPO) in my Sysadmin Lab.
GPO issues are usually caused by DNS, OU placement, permissions, or replication delays.

## GPO Not Applying
Symptoms:
- Settings not changing on client
- Login script not running
- Desktop restrictions not applied

Checks:
- Run gpresult /r on the client
- Verify the computer or user is in the correct OU
- Check if the GPO is linked to the OU
- Confirm the GPO is enabled

Fix:
- Move object to correct OU
- Enable GPO if disabled
- Run gpupdate /force

- ## Wrong GPO Link Order
Symptoms:
- A GPO is being overridden
- Settings from another GPO take priority

Checks:
- Look at GPO link order in the OU
- Remember: lower number = higher priority

Fix:
- Adjust link order
- Re-run gpupdate /force

- ## Security Filtering Issues
Symptoms:
- GPO applies to some users but not others
- GPO applies to some computers but not others

Checks:
- Open GPO → Scope tab
- Check Security Filtering
- Verify the user or computer is in the allowed group

Fix:
- Add correct group to Security Filtering
- Remove groups that should not apply

- ## WMI Filter Problems
Symptoms:
- GPO applies only to certain machines
- GPO never applies even though it should

Checks:
- Check if a WMI filter is attached
- Verify the filter actually matches the client

Fix:
- Remove incorrect WMI filter
- Fix the filter query if needed

- ## Slow or Failed GPO Processing
Symptoms:
- Long login times
- GPOs apply inconsistently

Checks:
- Verify DNS is correct
- Check network connectivity to the DC
- Run gpresult /h report.html for detailed info

Fix:
- Fix DNS
- Ensure client can reach the DC
- Reboot client

- ## How I Document GPO Issues
Each entry includes:
- What happened
- What I thought the cause was
- Steps I tried
- What fixed it
- Lessons learned
