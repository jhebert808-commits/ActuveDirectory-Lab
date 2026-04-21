# Windows Commands

## ipconfig /all
Shows full network configuration.  
Use when diagnosing DNS, DHCP, or NIC issues.

## ipconfig /flushdns
Clears DNS cache.  
Use when clients resolve old or incorrect IPs.

## ipconfig /registerdns
Re-registers the computer with DNS.  
Use when DNS records are missing or incorrect.

## gpupdate /force
Forces Group Policy refresh.  
Use after changing GPOs or OU placement.

## gpresult /r
Shows which GPOs applied to the user and computer.  
Use when GPOs are not applying.

## w32tm /resync /force
Forces time sync with the domain controller.  
Use when Kerberos or login issues occur due to time drift.
