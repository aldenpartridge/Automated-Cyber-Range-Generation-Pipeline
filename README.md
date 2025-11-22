
# 🚀 **Automated Cyber Range Generation Pipeline**

### *AI-Driven • Fully Containerized • Self-Hosted • King-of-the-Hill CTF Environment*

![Static Badge](https://img.shields.io/badge/CTF-Automation-blue)
![Static Badge](https://img.shields.io/badge/Infrastructure-Docker-informational)
![Static Badge](https://img.shields.io/badge/Logging-ELK%20Stack-orange)
![Static Badge](https://img.shields.io/badge/Safe-Fictional%20Only-brightgreen)
![Static Badge](https://img.shields.io/badge/AI-Multi--Agent-lightgrey)
![Static Badge](https://img.shields.io/badge/Scoring-KOTH-yellow)

---

# 📌 **Overview**

This repository defines the **complete specification** for an AI-driven system that automatically generates a fully self-hosted cyber range for university-level Capture-the-Flag competitions.

Every CTF event includes:

* A freshly generated fictional organization
* Unique employee roster, credentials, and digital identities
* Full Docker-based network topology
* Optional simulated mobile devices (fictional MFA)
* High-level vulnerabilities and pivot paths
* King-of-the-Hill (KOTH) scoring
* Fully centralized logging
* Complete scenario reproducibility
* Safe & offline-only execution

This README is written to be consumed by **downstream LLM agents** responsible for designing, building, or generating the cyber range.

---

# 🧭 **Table of Contents**

* [Purpose](#-purpose)
* [Terminology](#-terminology)
* [Pipeline Workflow](#-pipeline-workflow)

  * [1. User Input](#1-user-input--scenario-requirements)
  * [2. Organization Builder](#2-fictional-organization-builder-agent)
  * [3. Network Architect](#3-network-architect-agent)
  * [4. Vulnerability & Challenge Designer](#4-vulnerability--challenge-designer-agent)
  * [5. Image Builder](#5-container--image-builder-agent)
  * [6. Data Seeder](#6-data--content-seeder-agent)
  * [7. Compiler / Orchestrator](#7-cyber-range-compiler--orchestrator-agent)
  * [8. Scoring Engine](#8-scoring-engine-generator-agent)
  * [9. Logging Subsystem](#9-centralized-logging-subsystem)
  * [10. Safety & Validation](#10-safety--validation-agent)
  * [11. Deployment Coordinator](#11-deployment-coordinator-agent)
  * [12. Admin Dashboard](#12-optional-admin-dashboard-generator)
  * [13. Cleanup](#13-optional-post-event-cleanup-agent)
* [Resource Constraints](#-resource-constraints)
* [Directory Structure](#-directory-structure)
* [Gameplay Summary](#-ctf-gameplay-summary)

---

# 🎯 **Purpose**

This pipeline builds a **fully automatic CTF scenario** with:

✔ A fictional organization
✔ Docker-based cyber-range infrastructure
✔ Per-host King-of-the-Hill scoring
✔ Realistic seeded content
✔ Optional mobile device challenges
✔ Full, centralized logging for debrief review
✔ Safe, high-level vulnerabilities only
✔ No real-world exploitation techniques

Everything runs **offline**, ensuring that all attacker activity happens inside a contained sandbox.

---

# 🧩 **Terminology**

| Term                  | Meaning                                                    |
| --------------------- | ---------------------------------------------------------- |
| **Host / Device**     | Any containerized workstation, service, or simulated phone |
| **Container**         | Docker container representing part of the org              |
| **Control Token**     | Token proving team control over a host                     |
| **Control Beacon**    | Small agent inside each host handling token state          |
| **Mobile Device**     | Pseudo-phone container used for fictional MFA flows        |
| **Logging Subsystem** | Centralized ELK / OpenSearch stack for monitoring          |
| **KOTH**              | King-of-the-Hill scoring model                             |

---

# 🔧 **Pipeline Workflow**

Each step is performed by a dedicated multi-agent AI component.
Every agent produces artifacts consumed by downstream agents.

---

# 1️⃣ **User Input — Scenario Requirements**

The pipeline begins with a description provided by the user:

* Organization theme & story flavor
* Industry
* Scale & complexity
* Difficulty
* Optional constraints

This becomes the seed for all subsequent generation.

---

# 2️⃣ **Fictional Organization Builder Agent**

**Outputs:**

* `ORGANIZATION.md`
* `EMPLOYEE_CREDENTIALS.json`

Generates a complete fictional organization:

### Organizational Components

* Overview & mission
* Structure & departments
* Staff directory
* Background profiles
* Business model
* **Employee bounty system totaling 15,000 points**

### Digital Identity Profiles (`EMPLOYEE_CREDENTIALS.json`)

For each employee:

* Work usernames & emails
* Personal usernames & emails
* Multiple passwords (work/personal)
* Password patterns tied to biography
* Credential reuse tendencies
* Fictional MFA status

### Credential Safety Requirements

* Purely fictional
* No real-world patterns
* Supports high-level challenges only

---

# 3️⃣ **Network Architect Agent**

**Output:** `NETWORK_TOPOLOGY.md`

Defines:

* Full network topology
* DMZ, LAN, restricted zones
* Public & internal services
* Authentication systems
* Docker network layout
* **Optional mobile device hosts**
* Implementation-ready container mapping

Everything must use open-source, local-only components.

---

# 4️⃣ **Vulnerability & Challenge Designer Agent**

**Output:** `CHALLENGE_DESIGN.md`

Defines safe, high-level vulnerabilities and gameplay paths:

### High-Level Concepts Only

* Weak credential policy
* Password reuse
* Log-based hints
* Misconfigured ACLs
* Insecure internal services

### Attack Path / Kill Chain

* External → foothold → lateral movement → HVT capture

### Credential & Host-Level Challenges

* Which accounts are weak
* Which credentials appear in documents
* Which hosts require pivoting
* Which hosts have high point values

### Optional Mobile MFA Challenges

* Phone-like container with a **fictional authenticator app**
* Fictional OTP seed & codes
* Required for HVT access
* No real MFA bypass techniques

---

# 5️⃣ **Container & Image Builder Agent**

**Outputs:**

* `Dockerfiles/`
* `docker-compose.yml`
* System initialization & configs

Builds everything specified in topology and challenge design:

* Workstations
* Servers
* Internal web apps
* Mobile pseudo-device containers
* User accounts with hashed passwords
* Control beacon installation
* Logging agent installation

---

# 6️⃣ **Data & Content Seeder Agent**

**Outputs:**

* `SEEDING_PLAN.md`
* `/seed_data/` directory

Populates hosts with:

* Fake emails
* Documents & PDFs
* Logs (fictional)
* Configs
* Intranet content
* Password hints
* Credential artifacts (as defined in challenge design)

### Mobile Device Data (Optional)

* Fake SMS logs
* Mock mobile authenticator
* Wallpapers / notes
* Fictional OTP data

---

# 7️⃣ **Cyber Range Compiler / Orchestrator Agent**

**Outputs:**

* Final scenario manifest
* Build-ready configuration

Assembles all components into a cohesive cyber range:

* All containers
* Networks
* Volumes
* Logging stack
* Control beacon setup

---

# 8️⃣ **Scoring Engine Generator Agent**

**Outputs:**

* `SCORING_LOGIC.md`
* Scoring engine container
* Web-based scoreboard

### King-of-the-Hill Scoring

Each host runs a **Control Beacon**.

A team captures a host by submitting its `control_token` to the scoring server.

### Lockout Mechanism

* Host becomes uncapturable for *e.g., 30 seconds*
* After lockout, other teams may reclaim

### Scoring

* Hosts give **points per minute**
* Employee bounty values determine worth
* Mobile devices count as hosts

---

# 9️⃣ **Centralized Logging Subsystem**

Every attacker action must be logged.

### Supported Stacks

* ELK (Elasticsearch + Logstash + Kibana)
* OpenSearch + FluentBit + Grafana
* Loki + Promtail + Grafana

### Logged Events

* Auth attempts
* Service access
* Web requests
* File events (high-level)
* Network metadata
* Score submissions
* Mobile device interactions

Logs used for post-event debrief.

---

# 🔟 **Safety & Validation Agent**

**Output:** `SAFETY_VALIDATION_REPORT.md`

Ensures:

* Everything is fictional
* No unsafe exploit code
* No real individuals
* Offline-only
* All content is ethical & thematic

---

# 1️⃣1️⃣ **Deployment Coordinator Agent**

**Output:**

* Running cyber range
* `deployment_instructions.md`

Runs:

* Sanity checks
* Dependency checks
* Logging connectivity
* Scoreboard availability
* Optional reset system

---

# 1️⃣2️⃣ **Optional Admin Dashboard Generator**

Controls:

* Host states
* Scores
* Logs
* Restarts
* Health checks

---

# 1️⃣3️⃣ **Optional Post-Event Cleanup Agent**

Tears down containers and wipes the environment.

---

# 🧮 **Resource Constraints**

To support student hardware:

* Max ~25–30 containers
* No heavy mobile emulators (use pseudo-device containers instead)
* Lightweight web UIs where possible
* Low CPU overhead

---

# 📁 **Directory Structure**

```
/scenario/
   ORGANIZATION.md
   EMPLOYEE_CREDENTIALS.json
   NETWORK_TOPOLOGY.md
   CHALLENGE_DESIGN.md
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
   logging/
   logs/
   deployment_instructions.md
```

---

# 🏆 **CTF Gameplay Summary**

Attackers must:

1. Recon the environment
2. Exploit high-level weaknesses
3. Pivot internally
4. Capture hosts via control tokens
5. Hold hosts for points
6. Optionally capture mobile pseudo-devices
7. Defend their captures from other teams
8. Review logs post-event for learning

Total scenario value = **15,000 points**.

---
