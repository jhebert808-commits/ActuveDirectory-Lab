# User Management Troubleshooting

This folder contains notes and fixes for issues related to creating, managing, and maintaining user accounts and groups in Active Directory.
User management problems usually involve permissions, group membership, OU placement, or account status.

## User Cannot Log In
Symptoms:
- Incorrect username or password
- "The user name or password is incorrect"
- Login works on one machine but not another

Checks:
- Verify the account is not locked
- Check if the password expired
- Confirm the user is in the correct OU
- Check if the account is disabled

Fix:
- Unlock the account
- Reset the password
- Enable the account if disabled

- ## User Lacks Access to Shared Folders
Symptoms:
- Access denied
- User cannot open mapped drives

Checks:
- Check group membership
- Verify the group has permissions on the folder
- Confirm the user is logged into the domain

Fix:
- Add user to the correct security group
- Re-log or reboot to refresh token

- ## Group Policy Not Applying to User
Symptoms:
- Login script not running
- Desktop restrictions missing

Checks:
- Verify user is in the correct OU
- Check GPO link order
- Confirm user is included in Security Filtering

Fix:
- Move user to correct OU
- Adjust GPO filtering
- Run gpupdate /force

- ## User Added to Group but Permissions Still Missing
Symptoms:
- User added to group but still denied access

Checks:
- Ask if the user logged out and back in
- Check if the group is the correct type (Security vs Distribution)
- Confirm the group is applied to the resource

Fix:
- Have user log out and back in
- Use a Security group instead of Distribution

- ## Account Keeps Locking Out
Symptoms:
- User repeatedly locked out
- Lockout happens quickly after reset

Checks:
- Check for saved credentials on another device
- Look for mapped drives using old credentials
- Check for services running under the user account

Fix:
- Clear saved credentials
- Update mapped drive credentials
- Update service credentials

- ## How I Document User Management Issues
Each entry includes:
- What happened
- What I thought the cause was
- Steps I tried
- What fixed it
- Lessons learned
