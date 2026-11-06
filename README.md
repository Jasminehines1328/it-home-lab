# Pinecrest Media IT Home Lab

## Overview
A home lab where I run IT for Pinecrest Media, a made-up company with 12 employees.
All users and data are fake. I built this lab to practice real help desk and IT support work.

## Week 1: Identity, accounts, and help desk

### Microsoft 365
- Set up a Microsoft 365 Business Premium tenant for Pinecrest Media
- Created 12 employee accounts plus a backup admin account, all with Business Premium licenses
- Built 4 department groups with their own email addresses: Sales, Finance, Marketing, and IT
- Turned on multifactor authentication (MFA) for every user

![Users with Business Premium licenses](01-users.png)
![Department groups and email addresses](groups-02.png)
![MFA status for each user](mfa-03.png)

### Jira Service Management
- Built a help desk called Pinecrest IT Help Desk
- Set up request types for password resets, access requests, hardware issues, and software issues
- Added employees as customers so they can submit requests through the portal
- Worked and resolved the first ticket, a password reset for a locked-out user

![Request types](jira-request-types.png)
![Customers list](jira-customers.png)
![Ticket from the agent view](jira-queue.png)
![Internal notes on the ticket](jira-comments.png)
![Ticket from the employee's view](jira-portal.png)

## Ticket highlight: PIHD-1, locked out after vacation
- **Request type:** Password reset
- **First response:** within minutes, well inside the 12-hour target
- **Result:** resolved, with the employee kept updated through the portal

## What I learned
Jira didn't have a "start work" button, which confused me at first. I learned that tickets move forward by changing their status, from In Progress to Resolved, and that internal notes keep my steps hidden from the employee.

### Active Directory on AWS
- Launched a Windows Server 2022 server on AWS EC2 to act as the company's domain controller
- Locked Remote Desktop access to my own IP address only, instead of the whole internet
- Set a $10 monthly budget alert to keep cloud costs in check
- Built the pinecrest.local domain with Active Directory and DNS

![Server running on AWS EC2](aws-01-instance-running.png)
![Remote Desktop allowed from one IP only](aws-02-rdp-rule-my-ip.png)
![Monthly budget alert](aws-03-budget-alert.png)
![Server Manager showing AD DS and DNS roles](aws-04b-rdp-connected.png)
![Domain confirmed with Get-ADDomain](ad-01-domain-live.png)

### Users and groups
- Created department folders (OUs) for Sales, Finance, Marketing, and IT
- Added 11 employees and 4 department security groups with PowerShell
- Changed user details and created and deleted test accounts with PowerShell
- Did the same tasks in Active Directory Users and Computers

![All users with titles and departments](ad-02-users-created.png)
![Updating a user and deleting test accounts in PowerShell](ad-03-change-delete-powershell.png)
![Department folders](ad-04-ou-overview.png)
![Finance folder with users and group](ad-05-finance-ou.png)
![Changing a job title in the app](ad-07-change-title-app.png)
![Deleting a test user in the app](ad-08-delete-user_app.png)
![IT folder after the test user was removed](ad-09-user-deleted.png)

### Account lockout and password reset
- Turned on an account lockout policy of 5 failed sign-ins
- Locked a test user out on purpose, then found the account with Search-ADAccount
- Unlocked the account and reset the password, requiring a new one at next sign-in
- Repeated the fix in the app and confirmed the account was unlocked

![Failed sign-ins locking the account](ad-10-account-locked.png)
![Unlock and reset in PowerShell](ad-11-unlock-reset-powershell.png)
![Locked again, fixed in the app, and verified](ad-13-unlocked-app-verified.png)

### Troubleshooting along the way
- **Couldn't connect with Remote Desktop:** the firewall rule had saved an IPv6 address, but the server only had IPv4. Replaced it with an IPv4 rule for my IP.
- **Server too slow:** the first size only had 1GB of memory. Moved to a 4GB size that the free plan allows.
- **Domain setup kept failing on Windows Server 2025:** checked the version, then rebuilt on Windows Server 2022, and the domain installed cleanly.
