# Windows Commands (Detailed Explanations)

This page explains Windows commands in a way that a complete beginner can understand.  
Each command includes:
- What it does
- When to use it
- Why it fixes problems
- How to type it correctly
- Common mistakes
- Real examples

- ## ipconfig /all

### What it does
Shows every network setting on the computer:
- IP address
- DNS server
- Default gateway
- MAC address
- DHCP info
- Domain info

### When to use it
Use this command FIRST when:
- You cannot join the domain
- Internet is not working
- DNS is wrong
- The PC cannot find the domain controller

### Why it fixes things
It doesn’t “fix” anything — it **reveals the truth** about the network.  
It tells you EXACTLY what the computer thinks its network settings are.

### How to type it
ipconfig /all

### Common mistakes
- Forgetting the space → WRONG: ipconfig/all
- Using ALL CAPS → Works fine, Windows doesn’t care

### Example
If DNS does NOT show your Domain Controller’s IP,  
**the computer will NEVER join the domain.**

## ipconfig /flushdns

### What it does
Clears the computer’s DNS cache (old saved DNS results).

### When to use it
Use this when:
- The computer is resolving the wrong IP
- You changed DNS settings
- You fixed DNS on the server but the client still fails

### Why it fixes things
Windows saves DNS results for speed.  
If those results are wrong, the computer keeps using them.  
Flushing forces Windows to forget the old info.

### How to type it
ipconfig /flushdns

### Common mistakes
- Thinking it fixes DNS server issues (it only fixes the client)

- ## ipconfig /registerdns

### What it does
Forces the computer to register itself with the DNS server.

### When to use it
Use this when:
- The computer is missing from DNS
- Domain join works but GPO fails
- You renamed the computer
- You moved the computer to a new network

### Why it fixes things
Active Directory relies on DNS.  
If the computer doesn’t register itself, the DC can’t find it.

### How to type it
ipconfig /registerdns

## gpupdate /force

### What it does
Forces the computer to immediately apply Group Policy.

### When to use it
Use this when:
- You changed a GPO
- You moved a user or computer to a new OU
- Settings are not applying
- Login scripts aren’t running

### Why it fixes things
Normally GPO refreshes every 90 minutes.  
This command forces it to refresh **right now**.

### How to type it
gpupdate /force

### Common mistakes
- Expecting it to fix DNS or domain join issues (it won’t)

- ## gpresult /r

### What it does
Shows which GPOs applied to the computer and user.

### When to use it
Use this when:
- A GPO is not applying
- You want to confirm OU placement
- You want to see if a GPO is being blocked

### Why it fixes things
It tells you:
- Which GPOs applied
- Which GPOs did NOT apply
- Why they didn’t apply

This is the #1 tool for GPO troubleshooting.

### How to type it
gpresult /r

### Tip
Run it in an **elevated** Command Prompt for full results.

## w32tm /resync /force

### What it does
Forces the computer to sync its time with the domain controller.

### When to use it
Use this when:
- Login fails with Kerberos errors
- “Time difference is too great”
- Domain join fails randomly

### Why it fixes things
Kerberos (domain authentication) requires the time to be within 5 minutes.  
If the time is off, authentication fails.

### How to type it
w32tm /resync /force
