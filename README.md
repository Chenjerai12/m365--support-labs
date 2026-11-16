# m365-support-labs
M365 L2 Endpopint Labs I Entra ID , Exchange , Intune, Teams, One drive, Conditional access, MFA IKQL, Service health, Autopilot I 8 plus production tickets fixed
# M365 & Azure L2 Support Labs | 8+ Production Tickets

**Endpoint Support | Entra ID | Intune | Exchange Online | Conditional Access | KQL**
*Lab by Chenjerai - Kimberley, aiming for L2 Support JHB - R22k*

## What This Repo Proves
I can fix real M365 tickets end-to-end: Scope > Sign-in Logs > KQL > Fix > Verify > ITSM Documentation

## Tickets Fixed (M365 Endpoint)

### Layer 2: Identity & Access - Entra ID [CORE]
| Ticket | Issue | Fix | Tech |
| :--- | :--- | :--- | :--- |
| INC001001 | Outlook sign-in failure | Service Health + Sign-in Logs + Desktop vs Web isolation | Entra ID, MFA, Service Health, KQL |
| INC001002 | Account Locked | Error 50053, Unlock via Entra ID, Reset password | Entra ID, SigninLogs |
| INC001003 | MFA Failure | Conditional Access block, Authentication methods | Conditional Access, MFA |

### Layer 1: Apps - Exchange, Teams, OneDrive
| Ticket | Issue | Fix |
| :--- | :--- | :--- |
| INC001004 | Outlook disconnected / Unlicensed | License check M365 Admin, Credential Manager |
| INC001005 | Teams login loop | Teams Admin, Clear cache, CA policy |
| INC001006 | OneDrive not syncing | OneDrive Admin, Intune compliance |

### Layer 3: Device - Intune
| Ticket | Issue | Fix |
| :--- | :--- | :--- |
| INC001007 | Device Non-Compliant | Intune > Compliance > BitLocker, Defender |
| INC001008 | Autopilot Failure | Intune > Autopilot profile, Device enrollment |

## KQL Queries 
```kql
// Failed sign-ins
SigninLogs
| where Result != 0
| project TimeGenerated, UserDisplayName, ResultDescription, IPAddress

// Conditional Access failures
SigninLogs
| where ConditionalAccessStatus == "failure"

// Password resets audit
AuditLogs
| where OperationName == "Reset password"
