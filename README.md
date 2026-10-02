# Support Ticket Priority Prediction and Automated Assignment System Using Agentforce

## Project Overview
This project presents an intelligent support ticket management system built on the Salesforce platform[cite: 1]. It automates ticket priority classification, assigns high-priority tasks, and streamlines agent workflows using Salesforce Autolaunched Flows and Agentforce AI Agent configurations[cite: 1, 3, 12].

## Business Value & Key Objectives
- **Faster Ticket Resolution**: Prioritizes critical issues automatically[cite: 1].
- **Reduced Manual Effort**: Replaces manual ticket review with automated backend logic[cite: 1].
- **Intelligent Workload Management**: Assigns high-priority tickets directly to senior support agents[cite: 1, 7].

---

## Custom Object Data Model
**Object Name**: Support Ticket Intelligence  
**API Name**: `Support_Ticket_Intelligence__c`[cite: 2]

| Field Label | API Name | Data Type | Description |
| :--- | :--- | :--- | :--- |
| Ticket Number | `Ticket_Number__c` | Auto Number | TKT-{0000}[cite: 2] |
| Customer | `Customer__c` | Lookup (Account) | Related Account[cite: 2] |
| Contact | `Contact__c` | Lookup (Contact) | Customer Contact[cite: 2] |
| Issue Type | `Issue_Type__c` | Picklist | Technical, Billing, General[cite: 2] |
| Description | `Description__c` | Long Text Area | Issue details[cite: 2] |
| Priority Level | `Priority_Level__c` | Picklist | Low, Medium, High[cite: 2] |
| Status | `Status__c` | Picklist | New, In Progress, Resolved[cite: 2] |
| Created Date | `Created_Date__c` | Date | Ticket Date[cite: 2] |
| Assigned To | `Assigned_To__c` | Lookup (User) | Support Agent[cite: 2] |
| SLA Breach Risk | `SLA_Breach_Risk__c` | Checkbox | Risk Flag[cite: 2] |

---

## Flow Architecture & Automation Logic
**Flow Type**: Auto-Launched Flow (No Trigger / Agentforce Integrated)[cite: 3]

1. **Get Account Records**: Fetches the Account details using `varAccountName`[cite: 3, 4].
2. **Get Support Ticket**: Retrieves the latest ticket associated with the Account ID[cite: 4, 5].
3. **Keyword Analysis Decision**:
   - **High Priority**: Contains keywords `"urgent"`, `"not working"`, or `"failure"`[cite: 5].
   - **Medium Priority**: Contains keywords `"issue"`, `"slow"`, or `"delay"`[cite: 5].
   - **Low Priority**: Default fallback path[cite: 5].
4. **Action & Task Assignment**:
   - Automatically creates a high-priority Task for senior agents when high-priority tickets are detected[cite: 6, 7].
   - Assigns output variables (`varPriorityLevel`, `varAssignedTo`, `varActionMessage`) for Agentforce response handling[cite: 4, 6, 7].

---

## Agentforce AI Configuration
- **Topic Label**: Support Ticket Priority Analysis[cite: 12]
- **API Name**: `Support_Ticket_Priority_Analysis`[cite: 12]
- **Classification**: Analyzes support ticket details, categorizes urgency based on keywords, and triggers backend Flow automation[cite: 12].
- **Agent Action**: `Support_Ticket_Intelligence_c`[cite: 16]
- **Reference Action**: Auto-launched Flow (`Support_Ticket_Intellegence`)[cite: 7, 16]
- **Input Parameter**: `varAccountName`[cite: 4, 16]
- **Output Parameters**: `varAccountId`, `varTicketId`, `varPriorityLevel`, `varAssignedTo`, `varActionMessage`[cite: 3, 4, 18]

---

## Proof of Functionality & Screenshots

### 1. Flow Debug Proof Log
![Flow Debug Proof](./Flow_Debug_Proof.png)

### 2. Support Ticket Intelligence Records Page
![Ticket Records Page](./Ticket_Records_page.png)

---

## Project Status
- **Salesforce Custom Object & Fields**: Completed & Verified[cite: 2]
- **Auto-Launched Flow Logic**: Completed, Debugged & Tested[cite: 7, 8]
- **Agentforce Integration Logic**: Fully Designed & Mapped[cite: 12, 16]
