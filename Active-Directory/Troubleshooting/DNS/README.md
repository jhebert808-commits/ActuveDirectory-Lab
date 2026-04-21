# DNS Troubleshooting
This folder contains notes and fixes for DNS issues encountered while building my Sysadmin Lab.
DNS problems are one of the most common causes of domain join failures, GPO issues, and authentication errors.

## DNS Not Pointing to the Domain Controller
Symptoms:
- Cannot join domain
- Domain controller cannot be contacted
- GPOs not applying
- nslookup fails

Checks:
- Run ipconfig /all
- Verify DNS = Domain Controller IP
- Ping the DC by IP
- Ping the DC by hostname

Fix:
- Set DNS to the DC IP
- Flush DNS with ipconfig /flushdns
- Reboot client

- ## Incorrect Forward Lookup Zone
Symptoms:
- nslookup returns incorrect results
- Clients resolve wrong IPs
- Domain join fails

Checks:
- Open DNS Manager
- Verify the forward lookup zone matches the domain name
- Check A records for the DC

Fix:
- Correct the zone name
- Add or fix A records

- ## Missing or Broken SRV Records
Symptoms:
- Clients cannot locate domain controller
- Kerberos errors
- GPOs not applying

Checks:
- In DNS Manager, expand _msdcs
- Verify SRV records exist for LDAP, Kerberos, GC

Fix:
- Restart netlogon service on the DC
- Re-register DNS with ipconfig /registerdns

- ## DNS Cache Problems
Symptoms:
- Old IPs still resolving
- Domain join works on some clients but not others

Checks:
- Run ipconfig /displaydns

Fix:
- Run ipconfig /flushdns
- Restart DNS Client service

- ## How I Document DNS Issues
Each entry includes:
- What happened
- What I thought the cause was
- Steps I tried
- What fixed it
- Lessons learned
