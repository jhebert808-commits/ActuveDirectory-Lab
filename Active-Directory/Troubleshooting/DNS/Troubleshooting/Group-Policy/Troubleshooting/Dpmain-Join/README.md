# Domain Join Troubleshooting

This folder contains notes and fixes for issues related to joining Windows clients to an Active Directory domain.
Domain join failures are almost always caused by DNS, credentials, network issues, or time sync problems.

## Cannot Contact Domain Controller
Symptoms:
- "The domain controller cannot be contacted"
- "The specified domain does not exist"
- Domain join fails immediately

Checks:
- DNS must point to the Domain Controller IP
- Ping the DC by IP
- Ping the DC by hostname
- Run nslookup <domain>

Fix:
- Set DNS to the DC IP
- Flush DNS with ipconfig /flushdns
- Reboot client

- ## Incorrect Domain Name
Symptoms:
- "The domain does not exist"
- Typing the domain but Windows cannot find it

Checks:
- Verify the exact domain name (example: lab.local)
- Try joining using the FQDN instead of NetBIOS

Fix:
- Enter the correct domain name

- ## Wrong Credentials
Symptoms:
- "Access denied"
- Domain join starts but fails at the credential step

Checks:
- Use a domain admin account
- Make sure the password is correct
- Ensure the account is not locked or disabled

Fix:
- Use correct domain admin credentials

- ## Computer Account Issues
Symptoms:
- Domain join fails even with correct DNS and credentials
- Computer was previously joined to the domain

Checks:
- In Active Directory Users and Computers, look for the computer object
- Check if the object is disabled or corrupted

- ## Time Sync Problems
Symptoms:
- Kerberos errors
- "The time difference between the client and server is too great"

Checks:
- Compare client time vs DC time

Fix:
- Run w32tm /resync /force

- ## Network Connectivity Issues
Symptoms:
- Client cannot reach the DC
- Ping fails
- Domain join hangs or times out

Checks:
- Verify client and DC are on the same network
- Check firewall settings
- Confirm the DC is powered on

Fix:
- Fix network connection
- Allow required ports if firewall is blocking

- ## How I Document Domain Join Issues
Each entry includes:
- What happened
- What I thought the cause was
- Steps I tried
- What fixed it
- Lessons learned

Fix:
- Reset the computer account in AD
- Or delete the old computer account and try again
