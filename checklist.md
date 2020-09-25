# Threat Modeling
### Checklist

Each of the overarching items need to be reviewed, but every item is not necessarily applicable
Based in part on the [OWASP Threat Modeling Cheatsheet](https://cheatsheetseries.owasp.org/cheatsheets/Threat_Modeling_Cheat_Sheet.html) combined with industry experience.

A threat model should answer the following questions:

1. What is being built?
2. What can go wrong?
3. What is in place to prevent bad things?
4. Is it enough?

## System Design

Review documentation or interview stakeholders for:

- [ ] Application Purpose
- [ ] Technology Stack
- [ ] Audience
- [ ] Roles

## Data Elements

Possibilities may include:

- [ ] Financial Data
- [ ] Customer Private Information (PII)
- [ ] Intellectual Property
- [ ] Nonpublic Personal Information (NPI)
- [ ] Confidential Information
- [ ] Internal Use Only
- [ ] Public Information

## System Model

Identify application and infrastructure architecture components and review for basic security provisioning

- [ ] Trust Boundaries
- [ ] Application Actors
- [ ] Data flows
- [ ] Data sources and sinks
- [ ] Information Elements (and classifications)
- [ ] Application Entry Points
- [ ] Servers
- [ ] Network Security Controls
- [ ] Containers

## Attack Types

Utilizing Microsoft's STRIDE Model to classify possible attacks.

- [ ] Spoofing - Authenticity/Auditing
- [ ] Tampering - Integrity
- [ ] Repudiation - Non-repudiation/Auditing
- [ ] Information Disclosure - Confidentiality
- [ ] Denial of Service - Availability
- [ ] Elevation of Privilege - Authorization

## Possible Threat Agents

Use the system model to identify possible threat agents, the following are just suggestions. Reduce this list to applicable threats for the system.

- [ ] Anonymous External Attacker (AEA)
- [ ] Anonymous Internal Attacker (AIA)
- [ ] Malicious Internal User (MIU)
- [ ] Malicious External User (MEU)
- [ ] Malicious Employee (ME)
- [ ] Malicious System Administrator (MSA)
- [ ] Malicious Developer (MD)
- [ ] Nation State Actor (NSA)

## Attacker Focused Matrix

Threat Agent | Endpoint/Asset | Attack | Attack Type | Goal | Impact | Mitigation | Finding (if any)
------------ | -------------- | ------ | -------------- | ---- | ------ | ---------- | ----------------
AEA | Login Page | Brute-force Attack | Spoofing | Access User Account | High: Exposure of Client Data and App Functionality | Authentication Controls | None
AIA | Registration Page | User Enumeration | Information Disclosure | Determine Confidential Information (usernames) | Medium: Exposure of Known User Accounts | Out-of-band communications | Flow validates account by returning different page based on provided account existence

## Processed Focused Matrix

Goal | Asset | Threat Agent | Attack | Attack Type | Impact | Mitigation | Finding (if any)
------------ | -------------- | ------ | -------------- | ---- | ------ | ---------- | ----------------
Access User Account | Login Page | AEA | Brute-force Attack | Spoofing | High: Exposure of Client Data and App Functionality | Authentication Controls | None
Determine Confidential Information (usernames) | Registration Page | AIA | User Enumeration | Information Disclosure | Medium: Exposure of Known User Accounts | Out-of-band communications | Flow validates account by returning different page based on provided account existence

## Asset Focused Matrix

Asset | Threat Agent | Attack | Attack Type | Goal | Impact | Mitigation | Finding (if any)
------------ | -------------- | ------ | -------------- | ---- | ------ | ---------- | ----------------
Login Page | AEA | Brute-force Attack | Spoofing | Access User Account | High: Exposure of Client Data and App Functionality | Authentication Controls | None
Registration Page | AIA | User Enumeration | Information Disclosure | Determine Confidential Information (usernames) | Medium: Exposure of Known User Accounts | Out-of-band communications | Flow validates account by returning different page based on provided account existence
