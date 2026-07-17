# GlobalBiz Solutions Inc. Incident Response Plan Recommendations

## Project Overview

This project presents incident response plan recommendations for **GlobalBiz Solutions Inc. (GBS)**, a fictional publicly traded international organization with offices in the United States, Europe, and Asia.

The review focuses on two major cybersecurity incidents:

- A third-party supply chain compromise through a trusted vendor connection
- Executive spear phishing that led to unauthorized remote access and payment fraud

The project recommends improvements to detection, containment, incident-response staffing, business continuity, performance measurement, and stakeholder communication.

---

## Project Objectives

- Identify the major incident types affecting GlobalBiz Solutions Inc.
- Recommend detection controls for vendor compromise and executive spear phishing.
- Recommend containment actions that limit damage while preserving business operations.
- Define incident-response roles and responsibilities.
- Explain how response roles support business continuity.
- Recommend a measurable incident-response performance metric.
- Develop a structured communication process for internal and external stakeholders.
- Align incident-response practices with NIST guidance.

---

## Skills Demonstrated

- Incident Response Planning
- Security Operations
- Supply Chain Incident Response
- Spear-Phishing Response
- SIEM and Network Monitoring
- Endpoint Detection and Response
- Incident Containment
- Business Continuity
- Incident Response Governance
- Stakeholder Communication
- After-Hours Security Coverage
- Performance Metrics
- Mean Time to Contain
- NIST Incident Response Concepts

---

## Organization Profile

GlobalBiz Solutions Inc. is a publicly traded S&P 500 company headquartered in San Francisco.

The organization:

- Employs more than 10,000 people
- Operates 25 offices worldwide
- Conducts business in the United States, Europe, and Asia
- Processes personally identifiable information
- Handles financial and payment-card data
- Stores protected health information
- Transfers information internationally
- Relies on several external vendors
- Operates a U.S.-based Security Operations Center during normal business hours

The organization’s international operations and limited after-hours SOC coverage create additional incident-response challenges.

---

## Incident 1: Third-Party Supply Chain Compromise

### Incident Summary

A compromised toner vendor server used an existing trusted connection to transfer malicious tools into an internal GBS server.

The attack involved:

- Cobalt Strike
- Mimikatz
- Credential theft
- Sensitive data leaving the internal environment
- Unauthorized traffic through a trusted vendor connection

### Contributing Weaknesses

- Generic bidirectional firewall rules
- Lack of formal vendor-security requirements
- Use of PPTP at international offices
- Excessive trust in vendor connections
- Limited continuous monitoring
- Vendor access to internal inventory systems

### Indicators of Compromise

The incident-response plan should treat the following as serious warning signs:

- Unexpected bidirectional vendor traffic
- Credential-dumping behavior
- Security tools entering the network
- Sensitive data leaving an internal server
- Known Cobalt Strike or Mimikatz activity
- Vendor traffic outside the approved business baseline

---

## Incident 2: Executive Spear Phishing and Remote Access

### Incident Summary

An attacker impersonated an international client and contacted the vice president for client relations about a refund.

The executive installed TeamViewer after receiving the message. The following morning, the corporate purchase card had reached its $150,000 limit.

### Contributing Weaknesses

- The phishing email was not quarantined.
- The message remained in the executive’s primary inbox.
- TeamViewer installation produced no automated alert.
- The executive had permission to install unapproved software.
- Payment validation procedures were not followed.
- No secondary approval prevented the fraudulent transactions.

### Indicators of Compromise

The incident-response plan should identify the following as possible warning signs:

- Unusual refund or payment requests
- External messages impersonating known clients
- Installation of unauthorized remote-access software
- Unexpected remote sessions
- Unusual payment activity
- Large or repeated card transactions
- Executive workstation activity outside normal patterns

---

## Detection Recommendations

### Detection for the Supply Chain Incident

GBS should use a network detection and response platform integrated with a centralized SIEM.

The monitoring system should collect:

- Firewall logs
- Network flow data
- Server events
- Authentication records
- Endpoint events
- Vendor connection activity
- Data-transfer records

The vendor connection should have a documented baseline that defines normal behavior.

Approved behavior may include inventory updates, but it should not include:

- Credential transfers
- Sensitive data leaving internal databases
- Security tools entering the environment
- Unapproved administrative access
- Unexpected bidirectional communication

The system should alert on:

- Cobalt Strike activity
- Mimikatz activity
- Credential dumping
- Unusual outbound transfers
- Vendor sessions outside approved times
- Connections to unauthorized internal systems

Monitoring should continue outside normal U.S. business hours.

---

### Detection for the Spear-Phishing Incident

GBS should integrate a secure email gateway with endpoint detection and response.

The secure email gateway should:

- Mark external messages
- Scan attachments
- Inspect links
- Quarantine suspicious messages
- Detect impersonation attempts
- Flag unusual payment requests
- Identify messages requesting software installation

The EDR platform should alert when:

- TeamViewer is downloaded
- Unauthorized remote-access tools are installed
- A new remote session begins
- Suspicious processes appear
- Credentials are accessed
- Unapproved software runs on an executive or payment workstation

Alerts should identify:

- The user
- The device
- The program
- The destination
- The related email
- The time of the activity

---

## Containment Recommendations

### Containment for the Supply Chain Incident

When a vendor compromise is suspected, GBS should:

1. Isolate the affected server without powering it off.
2. Block the vendor connection at the firewall.
3. Preserve volatile evidence and logs.
4. Block related indicators of compromise.
5. Disable or rotate credentials used by the vendor.
6. Review all traffic involving the vendor connection.
7. Confirm that the vendor removed the threat.
8. Replace broad firewall rules with vendor-specific allow rules.
9. Restore normal access only after validation.

The response should limit disruption to the affected server and vendor path rather than shutting down unrelated operations.

---

### Containment for the Spear-Phishing Incident

GBS should:

1. Use EDR to isolate the affected workstation.
2. Terminate the unauthorized remote session.
3. Disable active sessions for the compromised executive.
4. Reset exposed credentials.
5. Block the remote-access software.
6. Freeze the affected payment card or account.
7. Review payment and account activity.
8. Provide a known-good replacement device.
9. Provide an approved alternate payment method when necessary.
10. Preserve evidence for investigation.

Containment should begin immediately after the incident is confirmed.

---

## Alignment With Security and Business Goals

### Supply Chain Containment

Isolating the affected server and blocking only the compromised vendor connection would:

- Protect sensitive information
- Preserve evidence
- Reduce attacker access
- Keep unrelated offices operational
- Support compliance requirements
- Maintain business continuity

A controlled manual inventory process could be used while the vendor connection remains suspended.

### Spear-Phishing Containment

Isolating the executive workstation and suspending only the compromised credentials and payment account would:

- Reduce financial loss
- Protect customer and company data
- Prevent additional remote access
- Preserve unrelated business functions
- Allow the executive to continue essential work from a clean device

---

## Incident Response Roles

### Role 1: Incident Response Manager

GBS should establish a formal Incident Response Manager role.

Responsibilities should include:

- Declaring an incident
- Activating the response plan
- Classifying incident severity
- Assigning an incident lead
- Distributing response tasks
- Authorizing urgent containment actions
- Coordinating technical and business teams
- Maintaining the incident record
- Recording major decisions
- Coordinating legal and compliance activities
- Overseeing recovery
- Leading post-incident review

The manager should have written authority to disconnect systems, suspend vendor access, disable accounts, and request outside assistance.

---

### Role 2: Regional Incident Responder

GBS should place trained responders in major regions or obtain equivalent coverage from a contracted SOC.

Regional responders should:

- Monitor alerts outside U.S. business hours
- Validate incidents
- Collect initial evidence
- Isolate affected devices
- Disable compromised network ports
- Notify the Incident Response Manager
- Contact local business owners
- Document all actions
- Provide a detailed shift handoff
- Use the same case-management process as the U.S. SOC

This role would reduce reliance on network administrators whose main responsibility is not incident response.

---

## Business Continuity Support

### Incident Response Manager

The Incident Response Manager would support business continuity by:

- Limiting containment to the smallest affected scope
- Coordinating with business owners
- Identifying alternate service methods
- Prioritizing recovery
- Balancing security needs with operational availability
- Preventing the response from causing a larger outage than the incident

### Regional Incident Responder

Regional responders would:

- Act while the U.S. SOC is closed
- Contain threats before they spread to other offices
- Reduce the need for wider shutdowns
- Begin evidence collection sooner
- Support local business owners
- Provide updated information for recovery decisions
- Improve shift handoffs

---

## Incident Response Performance Metric

### Mean Time to Contain

GBS should use **Mean Time to Contain (MTTC)** as the primary incident-response metric.

MTTC measures the average time between incident validation and confirmed containment.

Examples of confirmed containment include:

- Isolating a compromised server
- Blocking a vendor connection
- Disabling unauthorized sessions
- Resetting exposed credentials
- Isolating an infected workstation
- Freezing a compromised payment account

### Formula

```text
MTTC = Total containment time for all incidents ÷ Number of contained incidents
```

### Recommended Reporting Categories

GBS should break down MTTC by:

- Incident severity
- Region
- Incident type
- Business hours
- After-hours
- Vendor-related incidents
- Endpoint-related incidents

A declining MTTC would indicate stronger detection, staffing, authority, and containment processes.

A rising MTTC may indicate:

- Insufficient staffing
- Delayed approval
- Weak automation
- Poor after-hours coverage
- Inadequate training
- Unclear procedures

GBS should establish a baseline before setting a formal target.

---

## Stakeholder Communication Plan

### Before an Incident

Senior leadership should approve a controlled copy of the incident-response plan.

The plan should include:

- Notification matrix
- Current contact information
- Incident severity definitions
- Authority levels
- Approved communication methods
- Alternate contacts
- Escalation procedures
- Regulatory notification responsibilities
- Media communication procedures

Personnel with assigned responsibilities should:

- Receive the relevant part of the plan
- Acknowledge their responsibilities
- Complete role-based training
- Participate in tabletop exercises

---

### During an Incident

The Incident Response Manager should:

- Use the notification matrix
- Contact stakeholders based on severity
- Create a secure incident channel
- Maintain one central case record
- Record evidence and decisions
- Track assigned actions
- Provide concise leadership updates
- Coordinate with legal and compliance
- Prevent conflicting public statements

Leadership updates should address:

- Business impact
- Containment status
- Critical decisions
- Current risks
- Required approvals
- Next steps

Legal and compliance personnel should determine whether notification is required for:

- Regulators
- Law enforcement
- Customers
- Employees
- Vendors
- Business partners

The public relations team should manage public and media statements.

---

### After an Incident

GBS should conduct an after-action review involving all relevant personnel.

The review should identify:

- What happened
- How the incident was detected
- What delayed the response
- What worked well
- What failed
- Which controls need improvement
- Which procedures need revision
- Which training gaps were discovered

Approved changes should be added to the controlled response plan and tested during the next exercise.

---

## Incident Response Recommendations Summary

| Security Area | Recommended Improvement |
|---|---|
| Vendor Monitoring | Baseline and continuously monitor vendor traffic |
| Network Detection | Deploy NDR and SIEM correlation |
| Email Security | Use a secure email gateway |
| Endpoint Security | Deploy EDR to detect unauthorized remote-access tools |
| Supply Chain Containment | Isolate the server and block only the affected vendor path |
| Phishing Containment | Isolate the endpoint and suspend compromised access |
| Leadership | Establish an Incident Response Manager |
| Global Coverage | Add regional responders or contracted after-hours SOC coverage |
| Business Continuity | Limit containment to the smallest affected scope |
| Performance Measurement | Track Mean Time to Contain |
| Communication | Use a notification matrix and central case record |
| Lessons Learned | Require after-action reviews and plan updates |

---

## Project Files

Because this project is a written incident-response assessment, the repository does not require screenshots or an images folder.

Suggested repository structure:

```text
GlobalBiz-Incident-Response-Plan-Recommendations/
│
├── README.md
└── docs/
    └── GlobalBiz-Incident-Response-Plan-Recommendations.pdf
```

### Documentation

- **[Full Incident Response Plan Recommendations](https://github.com/user-attachments/files/30113724/GlobalBiz.Solutions.Inc.Task.2.docx)**
- **[D832 Case Study 5.pdf](https://github.com/user-attachments/files/30113723/D832.Case.Study.5.pdf)**

---

## Key Takeaways

GlobalBiz Solutions Inc. needs an incident-response plan that directly addresses vendor compromise, spear phishing, unauthorized remote access, payment fraud, and limited after-hours security coverage.

Network detection, SIEM correlation, secure email controls, and EDR would improve detection. Targeted containment would reduce damage without unnecessarily disrupting unrelated business operations.

An Incident Response Manager, regional response coverage, MTTC reporting, and a controlled communication process would give GBS clearer authority, faster containment, stronger business continuity, and more consistent incident handling.

---

## References

- Nelson, A., Rekhi, S., Souppaya, M., & Scarfone, K. (2025). *Incident Response Recommendations and Considerations for Cybersecurity Risk Management: A CSF 2.0 Community Profile*. NIST Special Publication 800-61 Revision 3.
- Scarfone, K., & Hoffman, P. (2009). *Guidelines on Firewalls and Firewall Policy*. NIST Special Publication 800-41 Revision 1.
- Swanson, M., Bowen, P., Phillips, A., Gallup, D., & Lynes, D. (2010). *Contingency Planning Guide for Federal Information Systems*. NIST Special Publication 800-34 Revision 1.
- Western Governors University. *D832 Case Study 5: GlobalBiz Solutions Inc.*

---

## Author

**Dontrell Wilson**  
Cybersecurity and Information Assurance Student  
CompTIA A+ | Network+ | Security+ | ITIL 4 Foundation
