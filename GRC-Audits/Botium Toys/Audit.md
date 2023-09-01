# GRC Audit Write-Up: Botium Toys

**Date:** 8/31/2023

**Author:** Alan Garcia

**Organization:** Selidrium


## Introduction

In this write-up, we will cover the comprehensive GRC (Governance, Risk Management, and Compliance) audit conducted for Botium Toys. The purpose of this audit was to assess the organization's security posture, identify potential risks, and ensure compliance with relevant regulations and standards. This document outlines the audit process, checklist, findings, and mitigation plan.

## Audit Checklist

## 1. Identify the Scope of the Audit

  ### Goals
  
  - Implement the National Institute of Standards and Technology Cybersecurity Framework (NIST CSF)
  - Ensure Botium Toys adheres to required compliances and establishes better processes for compliance assurance
  - Identify assets, current controls, and required controls for implementation
  - Establish policies, procedures, and playbooks
  - Implement the principle of least privilege for user credential management


  ### Current Assets
  
  Assets managed by the IT Department include:
  
  - On-premises equipment for in-office business needs
  - Employee equipment: end-user devices (desktops/laptops, smartphones), remote workstations, headsets, cables, keyboards, mice, docking stations, surveillance cameras, etc.
  - Management of systems, software, and services: accounting, telecommunication, database, security, ecommerce, and inventory management
  - Internet access
  - Internal network
  - Vendor access management
  - Data center hosting services
  - Data retention and storage
  - Badge readers
  - Legacy system maintenance: end-of-life systems that require human monitoring
  
  ### Administrative Controls
  
  | Control Name | Control Type and Explanation | Needs to be Implemented (X) | Priority |
  |--------------|-----------------------------|----------------------------|----------|
  | Least Privilege | Preventative; reduces risk by ensuring limited access for vendors and non-authorized staff | X | High |
  | Disaster recovery plans | Corrective; ensures business continuity in case of incidents | X | High |
  | Password policies | Preventative; establishes password strength rules | X | High |
  | Access control policies | Preventative; increases confidentiality and integrity of data | X | High |
  | Account management policies | Preventative; reduces attack surface and limits impact | X | High/Medium |
  | Separation of duties | Preventative; prevents abuse of the system | X | High |
  
  ### Technical Controls
  
  | Control Name | Control Type and Explanation | Needs to be Implemented (X) | Priority |
  |--------------|-----------------------------|----------------------------|----------|
  | Firewall | Preventative; filters malicious traffic from entering internal network | NA | NA |
  | Intrusion Detection System (IDS) | Detective; identifies intrusions quickly | X | High |
  | Encryption | Deterrent; improves data security | X | High/Medium |
  | Backups | Corrective; supports ongoing productivity | X | High |
  | Password management system | Corrective; supports password management | X | High/Medium |
  | Antivirus (AV) software | Corrective; detects and quarantines threats | X | High |
  | Manual monitoring, maintenance, and intervention | Preventative/corrective; mitigates threats | X | High |
  
  ### Physical Controls
  
  | Control Name | Control Type and Explanation | Needs to be Implemented (X) | Priority |
  |--------------|-----------------------------|----------------------------|----------|
  | Time-controlled safe | Deterrent; reduces physical threats | X | Medium/Low |
  | Adequate lighting | Deterrent; limits hiding places | X | Medium/Low |
  | CCTV surveillance | Preventative/detective; reduces risk and aids investigation | X | High/Medium |
  | Locking cabinets (for network gear) | Preventative; prevents unauthorized access | X | Medium |
  | Signage indicating alarm service provider | Deterrent; discourages attacks | X | Low |
  | Locks | Preventative; secures physical and digital assets | X | High |
  | Fire detection and prevention | Detective/Preventative; prevents damage from fire | X | Medium/Low |


## 2. Complete a Risk Assessment

A risk assessment is used to evaluate identified organizational risks related to budget, controls, internal processes, and external standards (i.e., regulations).

For the identified assets, the following organizational risks have been evaluated:

### Administrative/Managerial Controls

- Least Privilege: Risk of unauthorized access and potential data breaches.
- Disaster recovery plans: Risk of extended downtime and loss of productivity in case of incidents.
- Password policies: Risk of weak passwords leading to unauthorized access.
- Access control policies: Risk of data exposure due to inadequate access controls.
- Account management policies: Risk of unauthorized access due to improper account management.
- Separation of duties: Risk of potential abuse or fraud.

### Technical Controls

- Firewall: Risk of unauthorized network access and potential cyber attacks.
- Intrusion Detection System (IDS): Risk of undetected intrusions and data breaches.
- Encryption: Risk of data exposure due to inadequate encryption.
- Backups: Risk of data loss and extended downtime without proper backups.
- Password management system: Risk of compromised accounts and unauthorized access.
- Antivirus (AV) software: Risk of malware infections and data compromise.
- Manual monitoring, maintenance, and intervention: Risk of undetected threats and vulnerabilities.

### Physical Controls

- Time-controlled safe: Risk of unauthorized access to valuable assets.
- Adequate lighting: Risk of security breaches due to insufficient visibility.
- CCTV surveillance: Risk of inadequate monitoring and potential security incidents.
- Locking cabinets (for network gear): Risk of unauthorized access to critical infrastructure.
- Signage indicating alarm service provider: Risk of reduced deterrence against physical threats.
- Locks: Risk of unauthorized access to physical assets.
- Fire detection and prevention: Risk of fire damage to inventory and equipment.
### Compliance 

The audit has identified compliance findings in the following areas:

### General Data Protection Regulation (GDPR)

- Explanation: Botium Toys' expansion plans include E.U. countries. Complying with GDPR is a top priority to avoid potential fines for mishandling E.U. citizens' data.

### Payment Card Industry Data Security Standard (PCI DSS)

- Explanation: Botium Toys' ecommerce operations involve handling credit card information, necessitating compliance with PCI DSS for secure transactions.

### System and Organizations Controls (SOC type 1, SOC type 2)

- Explanation: Botium Toys needs to adhere to SOC2 security principles for safeguarding customer payment info and PII.


## 3. Conduct the Audit

### Critical Findings (Must Be Addressed Immediately)

The following compliances need to be implemented:

- System and Organizations Controls (SOC type 1, SOC type 2): Required for protecting PII of personnel and customers
- Payment Card Industry Data Security Standard (PCI DSS): Required for handling payment data
- General Data Protection Regulation (GDPR): Applicable when Botium Toys does business in E.U. countries

High-priority security controls requiring immediate attention include implementing the principle of least privilege, creating a disaster recovery plan, setting up firewalls, and using Intrusion Detection Systems (IDS) and Security Information and Event Management (SIEM) tools.


### Findings (Should Be Addressed, But No Immediate Need)

Adhering to the NIST CSF will aid in achieving many desired security goals and compliances, allowing for further security framework implementation as Botium Toys grows.

Due to Botium Toys' rapid scaling, most security controls need immediate implementation. Some physical controls like safes, lighting, and signage are less time-sensitive than others.


## Conclusion

Botium Toys should address compliance issues with PCI DSS and GDPR promptly, as the company accepts online payments from customers worldwide, including the E.U. SOC1 and SOC2 guidance should be used to develop appropriate policies and procedures for user access policies and data safety. Disaster recovery plans and backups are crucial for business continuity in case of an incident. Integrating IDS and AV software into current systems can help identify and mitigate risks, and intrusion detection. Locks and CCTV should be used to secure assets and monitor potential threats. Using encryption, a time-controlled safe, adequate lighting, locking cabinets, fire detection and prevention systems, and signage indicating alarm service providers can further improve Botium Toys' security posture.

---

