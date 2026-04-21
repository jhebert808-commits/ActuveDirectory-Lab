# Active Directory Troubleshooting 
This folder contains logs and notes I encountered while working with Active DirectoryDomain Services
Below are common AD issues and how to diagnose them

## DNS Misconfiguration
Symptoms:
- Cannot join domain
- Domain controller cannot be contacted
- nslookup fails

Checks:
- Make sure client DNS = Domain Controller IP
- Run ipconfig /all
- Test with ping <DC IP>
- Test with nslookup <domain>

Fix:
- Correct DNS settings
- Restart netlogon service if needed
- Reboot client

- ## Time Sync Issues
Symptoms:
- Kerberos authentication failures
- Time difference errors

Checks:
- Compare client time vs DC time
- Run w32tm /query /status

Fix:
- Run w32tm /resync /force

- ## OU or GPO Problems
Symptoms:
- GPOs not applying
- Login scripts not running

Checks:
- Verify the user or computer is in the correct OU
- Check GPO link order

Fix:
- Move object to correct OU
- Run gpupdate /force

- ## Domain Join Failures
Symptoms:
- Cannot contact domain
- Access denied
- Domain does not exist

Checks:
- DNS pointing to DC
- Network connectivity
- Correct domain name
- Using domain admin credentials

Fix:
- Fix DNS
- Reset computer account in AD
- Try joining again

- ## How I Document Troubleshooting
Each issue includes:
- What happened
- What I thought the cause was
- Steps I tried
- What fixed it
- Lessons learned
