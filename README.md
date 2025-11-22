---

# **Automated Cyber Range Generation Pipeline**

## **Purpose**

This repository defines the **complete specification** for an automated, AI-driven pipeline that generates fully containerized, self-hosted cyber ranges for university-level Capture-the-Flag (CTF) competitions.

Each CTF event features a **new fictional organization**, a fresh network topology, unique vulnerability pathways, realistic fictional employees, and a scoring engine. This system is fully **local**, ensuring that all penetration testing remains safe, legal, and isolated within an on-premises environment.

This document is intended to be consumed by downstream LLM agents to design, implement, or generate components of the cyber range.

---

# **System Overview**

Three attacker teams compete in a king-of-the-hill style CTF. They scan, attack, pivot, and take control of hosts inside a fully containerized cyber range.

A multi-agent AI pipeline automatically builds an entirely new cyber range, end-to-end:

1. User describes a fictional organization
2. Agents generate:

   * The organization
   * Its employees and credential ecosystem
   * The network topology
   * High-level vulnerabilities
   * Dockerized systems
   * Seeded data and internal documents
   * A scoring engine
   * Deployment infrastructure

Each event results in a fresh, realistic, gameplay-ready CTF scenario.

---

# **Pipeline Workflow**

Below is the complete cyber range generation workflow, including all required agents, artifacts, and outputs.

---

# **1. User Input — Scenario Requirements**

The pipeline begins with a description provided by the user:

* Industry/theme of the organization
* Size, complexity, and style
* Optional constraints or story elements
* Difficulty level

This seed becomes the foundation for the entire cyber range.

---

# **2. Fictional Organization Builder Agent**

**Input:** User scenario description
**Outputs:**

* `ORGANIZATION.md`
* `EMPLOYEE_CREDENTIALS.json`

This agent constructs a complete fictional organization.

## **Contents of `ORGANIZATION.md`**

### **2.1 Organization Overview**

Description of company theme, purpose, industry, and internal culture.

### **2.2 Size & Structure**

Organizational chart, departments, roles, personnel distribution.

### **2.3 Staff Directory**

Fictional employee roster including titles and reporting hierarchy.

### **2.4 Employee Background Profiles**

Safe, fully fictional personal biographies, hobbies, interests, and notes.

### **2.5 Mission & Business Model**

Strategic goals, services offered, operational focus, fictional revenue models.

### **2.6 Employee Bounty System**

Each employee receives a point value representing their importance, used for scoring.
**Total bounty points across all employees must equal exactly 15,000.**

---

## **2.7 Employee Digital Identity Profiles (NEW)**

Output: `EMPLOYEE_CREDENTIALS.json`

The Organization Builder must generate a detailed digital identity for every fictional employee, including:

* Work usernames
* Personal usernames
* Work email addresses
* Personal email addresses
* Multiple work passwords (historical + current)
* Multiple personal passwords
* Password patterns derived from their biography (e.g., pets, hobbies)
* Optional fictional MFA status
* Account hints and common mistakes
* Credential reuse tendencies
* Weak or guessable passwords (for downstream challenge design)

**These credentials are NOT used directly as implants or vulnerabilities**
— they are simply a realistic data corpus for downstream agents.

---

# **3. Network Architect Agent**

**Input:** `ORGANIZATION.md`
**Output:** `NETWORK_TOPOLOGY.md`

This agent translates the fictional organization into a full network architecture.

## **Contents of `NETWORK_TOPOLOGY.md`**

### **3.1 Complete Network Architecture**

Network segments (DMZ, LAN, restricted zones), routing, segmentation.

### **3.2 Forward-Facing Infrastructure**

Exposed services such as:

* Web portals
* Email gateways
* VPN entrypoints
* Public APIs

### **3.3 Internal Infrastructure**

File servers, authentication servers, application servers, internal web portals, shared drives, etc.

### **3.4 Open-Source, Local-Only Components**

Every service must be:

* Open-source
* Self-hostable
* Docker-compatible
* Free to use

### **3.5 Containerization Mapping**

All hosts mapped to Docker images, including networking, volumes, and interdependencies.

### **3.6 Implementation-Ready Structure**

Downstream agents must be able to use this file to generate:

* Dockerfiles
* Compose files
* Network definitions
* Config files

---

# **4. Vulnerability & Challenge Designer Agent**

**Inputs:**

* `ORGANIZATION.md`
* `EMPLOYEE_CREDENTIALS.json`
* `NETWORK_TOPOLOGY.md`

**Output:** `CHALLENGE_DESIGN.md`

This agent defines the **intended challenge structure** for the CTF.

## **Contents of `CHALLENGE_DESIGN.md`**

### **4.1 High-Level Vulnerability Design**

Defines the *concepts* of vulnerabilities, without exploit code.
Examples:

* Weak credential policy
* Password reuse
* Misconfigured web service
* Faulty access control
* Internal information exposure

### **4.2 Attack Path / Pivot Structure**

Defines how attackers move from:
External → Foothold → Internal Discovery → Lateral Movement → HVTs

### **4.3 Host-Specific Challenge Goals**

Describes what “control” means for each device.

### **4.4 Difficulty Tiering**

Beginner → Intermediate → Advanced challenges.

---

## **4.5 Credential-Based Challenge Definitions (NEW)**

The agent determines how employee credentials *become relevant* as gameplay elements.

It must select:

* Which work credentials are intentionally weak
* Which passwords are reused across services
* Which accounts should be brute-forceable
* Which logs or documents should contain credential hints
* Which personal accounts bridge into corporate accounts
* Which credentials appear in misconfigured services
* Which accounts are red herrings
* Which credentials lead to major pivot points

The raw credentials come from `EMPLOYEE_CREDENTIALS.json`
—but only this agent decides which become vulnerabilities.

---

# **5. Container & Image Builder Agent**

**Inputs:**

* `NETWORK_TOPOLOGY.md`
* `CHALLENGE_DESIGN.md`
* `EMPLOYEE_CREDENTIALS.json`

**Outputs:**

* `Dockerfiles/`
* `docker-compose.yml`
* Service configs
* System initialization scripts

This agent builds all infrastructure components:

* Host containers
* Service configurations
* User accounts (properly hashed passwords)
* Internal DNS setups
* Appropriate port mappings
* Network bridges

---

# **6. Data & Content Seeder Agent**

**Inputs:**

* Built containers
* `EMPLOYEE_CREDENTIALS.json`
* `CHALLENGE_DESIGN.md`

**Outputs:**

* `SEEDING_PLAN.md`
* `/seed_data/` directory with generated content

This agent populates each host with realistic internal data:

### **6.1 Seed Content**

* Fake work documents
* Emails (personal + work inboxes)
* System logs
* Configuration files
* Notes and memos
* Employee activity artifacts
* Password hint notes
* Browser history or saved passwords (if defined in `CHALLENGE_DESIGN.md`)

### **6.2 Credential Deployment (NEW)**

Credentials may appear as:

* Properly hashed user accounts
* Database entries
* Mail server user lists
* Plaintext notes *only if defined deliberately as a vulnerability*
* Brute-forceable login prompts
* Password patterns embedded in documents
* Authentication logs containing hints
* Password reuse across personal & work accounts

---

# **7. Cyber Range Compiler / Orchestrator Agent**

**Inputs:** All generated artifacts
**Outputs:**

* Final cyber range manifest
* Build-ready composition
* A unified deployable environment

This agent assembles the entire system:

* All containers
* Networks
* Volumes
* Configurations
* Initialization logic

---

# **8. Scoring Engine Generator Agent**

**Inputs:**

* `ORGANIZATION.md`
* `CHALLENGE_DESIGN.md`

**Outputs:**

* `SCORING_LOGIC.md`
* Scoring service container
* Scoreboard UI

Features:

* Points-per-minute king-of-the-hill scoring
* Team registration
* Host control tracking
* Real-time leaderboard

Employee bounty values determine the point assignments.

---

# **9. Safety & Validation Agent**

**Input:** Entire scenario
**Output:** `SAFETY_VALIDATION_REPORT.md`

This agent ensures:

* All content is fictional
* No real companies or people appear
* No harmful code or real-world exploits are generated
* No external network traffic occurs
* No credentials resemble real-world data
* All attacks are contained in a sandbox

---

# **10. Deployment Coordinator Agent**

**Inputs:** Finalized environment
**Outputs:**

* Running cyber range
* System validation
* `deployment_instructions.md`

Handles:

* Spinning up all containers
* Pre-CTF validation
* Connectivity instructions for attackers
* Reset and management operations

---

# **11. Optional Admin Dashboard Generator**

Generates a panel to manage:

* Range health
* Team scores
* Logs
* Restarts
* Overrides

---

# **12. Optional Post-Event Cleanup Agent**

Tears down and wipes the environment clean.

---

# **Directory Structure**

```
/scenario/
   ORGANIZATION.md
   NETWORK_TOPOLOGY.md
   CHALLENGE_DESIGN.md
   EMPLOYEE_CREDENTIALS.json
   SEEDING_PLAN.md
   SCORING_LOGIC.md
   SAFETY_VALIDATION_REPORT.md

/build/
   Dockerfiles/
   service_configs/
   seed_data/
   docker-compose.yml
   manifest.json

/runtime/
   scoring_engine/
   dashboard/
   logs/
   deployment_instructions.md
```

---

# **Design Requirements**

### ✔ Fully self-hosted

No cloud resources. No external scanning.

### ✔ Fully containerized

All services must run in Docker.

### ✔ Safe & fictional

All credentials, data, and actors must be invented and sandboxed.

### ✔ Regeneratable

A fresh organization, network, and challenge set for each CTF event.

### ✔ Structured outputs

Each agent must produce explicit, machine-readable artifacts.

---

# **CTF Gameplay Summary**

Attackers begin externally, identify exposed services, gain foothold, pivot laterally, compromise employees’ devices, and accumulate points based on host value.

Total possible points across all employees = **15,000**.

---
