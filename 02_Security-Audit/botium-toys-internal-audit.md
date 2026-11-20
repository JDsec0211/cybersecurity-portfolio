# Botium Toys – Internal Security Audit Checklist

**Frameworks:** PCI DSS, GDPR, SOC  **Source:** Google Cybersecurity Professional Certificate

## 📋 Scenario
Botium Toys is a small U.S. toy company with a physical store, a warehouse, and a growing online store that serves customers worldwide, including in the EU. As the business grew, its IT department asked for an internal audit to understand its security risks and compliance gaps before they turned into real problems.

## Audit Objective
Evaluate Botium Toys’ current security controls and compliance posture to identify risks and improvement areas.

---

# 🔐 Controls Assessment Checklist

## Administrative Controls

- [ ] Least Privilege implemented  
- [ ] Separation of Duties enforced  
- [ ] Strong Password Policy meeting modern complexity standards  
- [ ] Centralized Password Management System  
- [ ] Disaster Recovery Plan established  
- [ ] Backups of critical data performed and tested  
- [ ] Formal Asset Inventory and Classification process  
- [ ] Scheduled monitoring and intervention procedures for legacy systems  

---

## Technical Controls

- [x] Firewall configured with defined security rules  
- [x] Antivirus software installed and monitored  
- [ ] Intrusion Detection System (IDS) deployed  
- [ ] Encryption implemented for cardholder data and customer PII/SPII  
- [x] Data integrity controls implemented  
- [ ] Restricted access to cardholder data (authorized users only)  

---

## Physical Controls

- [x] Locks securing offices, storefront, and warehouse  
- [x] Closed-circuit television (CCTV) surveillance  
- [x] Fire detection and prevention systems  

---

# 📜 Compliance Checklist

## PCI DSS (Payment Card Industry Data Security Standard)

- [ ] Access to credit card data limited to authorized users  
- [ ] Credit card data stored and processed in a secure environment  
- [ ] Encryption procedures implemented for cardholder data  
- [ ] Secure password management policies enforced  

---

## GDPR (General Data Protection Regulation)

- [ ] EU customer data fully secured and access restricted  
- [x] 72-hour breach notification plan in place  
- [ ] Data properly classified and inventoried  
- [x] Privacy policies and procedures documented and enforced  

---

## SOC (System and Organization Controls)

- [ ] User access policies properly established and enforced  
- [ ] Sensitive data (PII/SPII) kept confidential and restricted  
- [x] Data integrity controls implemented  
- [ ] Data access restricted to authorized individuals  

---

# 📊 Risk Summary

- Overall Risk Score: **8/10 (High Risk)**
- Major gaps: Lack of encryption, missing least privilege, no backups, no IDS, weak password enforcement.
- Compliance risk: High risk of PCI DSS violations and partial GDPR compliance.

---

# 🚨 Priority Recommendations

1. Implement least privilege and separation of duties.
2. Encrypt all sensitive data (cardholder data and PII/SPII).
3. Deploy an IDS for improved monitoring.
4. Establish tested backups and disaster recovery procedures.
5. Strengthen password policy and implement centralized password management.
6. Improve asset inventory and classification.

---

## 🛠️ Skills Demonstrated
- Assessing administrative, technical, and physical security controls
- Mapping controls to compliance requirements (PCI DSS, GDPR, SOC)
- Risk scoring and prioritizing remediation
- Writing clear audit findings and recommendations
