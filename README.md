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
