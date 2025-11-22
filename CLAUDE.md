# CLAUDE.md - AI Assistant Guide

## Repository Overview

This repository contains the **complete specification** for an automated, AI-driven pipeline that generates fully containerized, self-hosted cyber ranges for university-level Capture-the-Flag (CTF) competitions.

**Current State:** This is a specification-only repository. The actual implementation has not yet been built.

**Purpose:** The README.md file serves as a comprehensive design document intended to be consumed by downstream LLM agents to design, implement, and generate components of the cyber range system.

---

## Project Vision

This system enables the automated generation of complete, realistic CTF scenarios where:

- **Three attacker teams** compete in king-of-the-hill style competitions
- Each event features a **new fictional organization** with unique network topology
- All components are **fully containerized** and **self-hosted** (no cloud dependencies)
- The entire environment is **safe, legal, and isolated** within an on-premises setup
- Every CTF event is **regeneratable** with fresh content and challenges

**Total bounty points per scenario:** Exactly 15,000 points distributed across employee targets

---

## Repository Structure

### Current Structure
```
/
├── .git/               # Git repository metadata
├── README.md           # Complete specification document
└── CLAUDE.md          # This file - AI assistant guide
```

### Planned Structure (Once Implemented)
```
/
├── agents/                    # Multi-agent AI pipeline implementation
│   ├── organization_builder/  # Fictional org & employee generator
│   ├── network_architect/     # Network topology designer
│   ├── vulnerability_designer/# Challenge & attack path creator
│   ├── container_builder/     # Docker infrastructure builder
│   ├── data_seeder/          # Content population agent
│   ├── orchestrator/         # Cyber range compiler
│   ├── scoring_engine/       # Scoring system generator
│   ├── safety_validator/     # Safety & validation checks
│   ├── deployment_coordinator/# Deployment manager
│   └── cleanup_agent/        # Post-event cleanup
│
├── scenario/                  # Generated scenario artifacts
│   ├── ORGANIZATION.md
│   ├── NETWORK_TOPOLOGY.md
│   ├── CHALLENGE_DESIGN.md
│   ├── EMPLOYEE_CREDENTIALS.json
│   ├── SEEDING_PLAN.md
│   ├── SCORING_LOGIC.md
│   └── SAFETY_VALIDATION_REPORT.md
│
├── build/                     # Build artifacts
│   ├── Dockerfiles/
│   ├── service_configs/
│   ├── seed_data/
│   ├── docker-compose.yml
│   └── manifest.json
│
├── runtime/                   # Runtime components
│   ├── scoring_engine/
│   ├── dashboard/
│   ├── logs/
│   └── deployment_instructions.md
│
├── tests/                     # Test suites
├── docs/                      # Additional documentation
├── examples/                  # Example scenarios
└── README.md                  # Specification document
```

---

## Multi-Agent Architecture

The system is designed around **12 specialized AI agents** that work in sequence:

### 1. Fictional Organization Builder Agent
- **Input:** User scenario description
- **Output:** `ORGANIZATION.md`, `EMPLOYEE_CREDENTIALS.json`
- **Responsibility:** Creates complete fictional organization with employees, credentials, and digital identities
- **Critical Requirement:** Total employee bounty points must equal exactly 15,000

### 2. Network Architect Agent
- **Input:** `ORGANIZATION.md`
- **Output:** `NETWORK_TOPOLOGY.md`
- **Responsibility:** Designs network architecture with DMZ, LAN, services
- **Constraint:** All components must be open-source, self-hostable, Docker-compatible

### 3. Vulnerability & Challenge Designer Agent
- **Input:** `ORGANIZATION.md`, `EMPLOYEE_CREDENTIALS.json`, `NETWORK_TOPOLOGY.md`
- **Output:** `CHALLENGE_DESIGN.md`
- **Responsibility:** Defines vulnerability concepts and attack paths
- **Note:** Defines concepts, not exploit code

### 4. Container & Image Builder Agent
- **Input:** `NETWORK_TOPOLOGY.md`, `CHALLENGE_DESIGN.md`, `EMPLOYEE_CREDENTIALS.json`
- **Output:** Dockerfiles, docker-compose.yml, service configs
- **Responsibility:** Builds all infrastructure components

### 5. Data & Content Seeder Agent
- **Input:** Built containers, `EMPLOYEE_CREDENTIALS.json`, `CHALLENGE_DESIGN.md`
- **Output:** `SEEDING_PLAN.md`, `/seed_data/` directory
- **Responsibility:** Populates hosts with realistic internal data

### 6. Cyber Range Compiler / Orchestrator Agent
- **Input:** All generated artifacts
- **Output:** Final deployable environment
- **Responsibility:** Assembles the complete system

### 7. Scoring Engine Generator Agent
- **Input:** `ORGANIZATION.md`, `CHALLENGE_DESIGN.md`
- **Output:** `SCORING_LOGIC.md`, scoring service, scoreboard UI
- **Responsibility:** Implements king-of-the-hill scoring system

### 8. Safety & Validation Agent
- **Input:** Entire scenario
- **Output:** `SAFETY_VALIDATION_REPORT.md`
- **Responsibility:** Ensures all content is fictional, safe, and sandboxed

### 9. Deployment Coordinator Agent
- **Input:** Finalized environment
- **Output:** Running cyber range, deployment instructions
- **Responsibility:** Handles deployment and validation

### 10-12. Optional Agents
- Admin Dashboard Generator
- Post-Event Cleanup Agent

---

## Key Development Principles

### Security & Safety First
1. **All content must be fictional** - No real companies, people, or credentials
2. **Fully isolated environment** - No external network traffic
3. **Safe vulnerability design** - No real-world exploits or harmful code
4. **Sandboxed execution** - All attacks contained within Docker environment

### Technical Constraints
1. **Fully self-hosted** - No cloud resources or external dependencies
2. **Fully containerized** - All services must run in Docker
3. **Open-source only** - All components must be free, open-source software
4. **Regeneratable** - System must support generating fresh scenarios on demand

### Design Standards
1. **Structured outputs** - Each agent produces explicit, machine-readable artifacts
2. **Modular architecture** - Agents work independently with clear interfaces
3. **Validation at each step** - Safety checks throughout the pipeline
4. **Documentation-driven** - All agents consume and produce markdown/JSON artifacts

---

## Workflow for AI Assistants

### When Adding New Features or Agents

1. **Read the specification first** - Always review README.md:1-449 for complete context
2. **Maintain artifact structure** - Follow the defined output formats for each agent
3. **Ensure safety compliance** - All generated content must pass safety validation
4. **Preserve modularity** - Agents should have clear inputs/outputs
5. **Update documentation** - Keep specification in sync with implementation

### When Implementing an Agent

1. **Identify agent responsibility** from README.md specification
2. **Define input/output contracts** clearly
3. **Implement safety checks** appropriate to the agent's function
4. **Generate structured artifacts** in the specified formats (Markdown/JSON)
5. **Include validation logic** to ensure output quality
6. **Write tests** to verify agent behavior

### When Generating Scenarios

1. **Start with user input** - Capture scenario requirements
2. **Follow the pipeline sequence** - Agents must execute in order (1→12)
3. **Validate intermediate outputs** - Each artifact feeds the next agent
4. **Check bounty point totals** - Must equal exactly 15,000
5. **Run safety validation** - Before deployment
6. **Test deployment** - Ensure all containers start correctly

### Credential Handling

**Critical Understanding:** The `EMPLOYEE_CREDENTIALS.json` file contains a realistic corpus of fictional credentials, but:

- **NOT all credentials become vulnerabilities**
- The Vulnerability Designer Agent (Agent #3) decides which credentials are intentionally weak
- The Data Seeder Agent (Agent #5) determines how/where credentials appear
- Credentials should be properly hashed when used as actual accounts
- Plaintext credentials only appear when deliberately designed as vulnerabilities

### File Naming Conventions

- **Specification documents:** UPPERCASE.md (e.g., `ORGANIZATION.md`)
- **Generated artifacts:** lowercase_with_underscores (e.g., `deployment_instructions.md`)
- **Code files:** Follow Python/language-specific conventions
- **Configuration files:** Use standard names (e.g., `docker-compose.yml`)

---

## Development Workflows

### Initial Implementation Phase

**Goal:** Build the agent infrastructure from scratch

```bash
# 1. Set up project structure
mkdir -p agents/{organization_builder,network_architect,vulnerability_designer,container_builder,data_seeder,orchestrator,scoring_engine,safety_validator,deployment_coordinator,cleanup_agent}
mkdir -p scenario build runtime tests docs examples

# 2. Implement agents sequentially
# Start with Organization Builder, then Network Architect, etc.

# 3. Create integration tests
# Test full pipeline end-to-end

# 4. Validate with example scenarios
# Generate sample CTF ranges
```

### Scenario Generation Workflow

**Goal:** Generate a new CTF cyber range

```bash
# 1. Provide user input
# Define organization theme, size, difficulty

# 2. Execute agent pipeline
# Run agents 1-9 in sequence

# 3. Review generated artifacts
# Check scenario/, build/, runtime/ directories

# 4. Deploy cyber range
# Use deployment coordinator output

# 5. Validate deployment
# Ensure all services running correctly
```

### Testing Workflow

**Goal:** Verify agent functionality

```bash
# Unit tests per agent
pytest agents/<agent_name>/tests/

# Integration tests
pytest tests/integration/

# End-to-end tests
pytest tests/e2e/

# Safety validation tests
pytest tests/safety/
```

---

## Common Tasks for AI Assistants

### Task: Implement a New Agent

1. Review agent specification in README.md
2. Create agent directory: `agents/<agent_name>/`
3. Implement core logic in `agents/<agent_name>/agent.py`
4. Define input schema
5. Define output schema
6. Add validation logic
7. Write unit tests
8. Update integration tests
9. Document agent in `agents/<agent_name>/README.md`

### Task: Modify Artifact Format

1. Update specification in README.md
2. Modify producer agent output format
3. Modify consumer agent input parsing
4. Update validation schemas
5. Update tests
6. Regenerate example artifacts

### Task: Add a New Service Type

1. Update Network Architect agent to support new service
2. Add Docker image configuration
3. Update Container Builder agent
4. Add seeding logic to Data Seeder agent
5. Update safety validation rules
6. Add service documentation
7. Test deployment

### Task: Debug a Generated Scenario

1. Check agent logs for errors
2. Validate artifact schemas
3. Verify bounty point totals (must equal 15,000)
4. Check Docker container logs
5. Validate network connectivity
6. Review safety validation report
7. Test scoring engine integration

---

## Important Constraints & Requirements

### Hard Requirements

- ✅ Employee bounty points **MUST** total exactly 15,000
- ✅ All services **MUST** be open-source and self-hostable
- ✅ All content **MUST** be fictional
- ✅ No external network access from containers
- ✅ All outputs **MUST** be structured (Markdown/JSON)

### Soft Guidelines

- Prefer realistic organization structures
- Balance difficulty levels (beginner/intermediate/advanced)
- Include multiple attack paths
- Create diverse credential patterns
- Generate authentic-feeling internal documents

---

## Git Workflow

### Branch Strategy

**Development Branch:** `claude/claude-md-miarx6sbytj464r7-01MNzWDGBNAWE3yaHfqAVUN3`

All development should occur on this branch.

### Commit Message Format

```
<type>(<scope>): <description>

[optional body]

[optional footer]
```

**Types:**
- `feat`: New feature or agent
- `fix`: Bug fix
- `docs`: Documentation updates
- `test`: Test additions or modifications
- `refactor`: Code refactoring
- `chore`: Maintenance tasks

**Examples:**
```
feat(org-builder): implement employee credential generator

docs(claude): add comprehensive AI assistant guide

fix(scoring): correct bounty point calculation

test(network-architect): add topology validation tests
```

### Push Protocol

```bash
# Always push to the designated development branch
git push -u origin claude/claude-md-miarx6sbytj464r7-01MNzWDGBNAWE3yaHfqAVUN3
```

---

## Technology Stack (Planned)

### Core Technologies
- **Python 3.11+** - Primary implementation language
- **Docker & Docker Compose** - Containerization
- **FastAPI** - API framework for agents
- **Pydantic** - Data validation
- **Jinja2** - Template generation

### Data Storage
- **JSON** - Credential and configuration storage
- **Markdown** - Human-readable artifacts
- **SQLite** - Scoring database (optional)

### Container Services (Examples)
- **Apache/Nginx** - Web servers
- **Postfix/Dovecot** - Mail servers
- **OpenLDAP** - Directory services
- **Samba** - File sharing
- **OpenVPN/WireGuard** - VPN services
- **MariaDB/PostgreSQL** - Databases
- **Nextcloud** - Collaboration platform

### Testing
- **pytest** - Test framework
- **pytest-docker** - Container testing
- **coverage** - Code coverage
- **black** - Code formatting
- **mypy** - Type checking

---

## Common Pitfalls to Avoid

### ❌ Don't Do This

1. **Generating real-looking credentials** that could match actual passwords
2. **Using cloud services** or external APIs
3. **Creating exploits** that work against real-world systems
4. **Hardcoding configuration** instead of using templates
5. **Skipping safety validation** before deployment
6. **Forgetting to validate bounty points** (must = 15,000)
7. **Creating non-fictional content** that references real entities
8. **Making containers accessible** from external networks

### ✅ Do This Instead

1. **Generate obviously fictional credentials** with clear patterns
2. **Use only self-hosted**, open-source alternatives
3. **Design vulnerability concepts** without actual exploit code
4. **Use configuration templates** and environment variables
5. **Always run safety validation** as part of the pipeline
6. **Validate bounty calculations** in the Organization Builder
7. **Create compelling but clearly fictional** scenarios
8. **Isolate containers** to Docker networks only

---

## Questions to Ask When Uncertain

### Before Implementing a Feature
- Does this maintain the self-hosted requirement?
- Is this component open-source and Docker-compatible?
- Does this preserve the modular agent architecture?
- Will this pass safety validation?

### Before Generating Content
- Is this content clearly fictional?
- Could this be confused with real data?
- Does this follow the difficulty progression?
- Are credential patterns intentionally designed?

### Before Deployment
- Have all safety checks passed?
- Do bounty points total exactly 15,000?
- Are all containers properly isolated?
- Is the scoring engine configured correctly?

---

## Resources & References

### Primary Documentation
- **README.md:1-449** - Complete system specification
- This file (CLAUDE.md) - AI assistant guide

### External Resources
- Docker documentation: https://docs.docker.com/
- Docker Compose: https://docs.docker.com/compose/
- CTF best practices (for design inspiration)
- Network security concepts (for realistic topology design)

---

## Support & Issues

When encountering issues:

1. **Review the specification** in README.md
2. **Check artifact schemas** for correctness
3. **Validate intermediate outputs** from each agent
4. **Review Docker logs** for container issues
5. **Run safety validation** to catch policy violations
6. **Check bounty point totals** for Organization artifacts

For implementation questions, refer to the agent-specific sections in README.md:43-388.

---

## Version History

- **v1.0** - Initial CLAUDE.md creation based on README.md specification
  - Complete repository analysis
  - Multi-agent architecture documentation
  - Development workflows and conventions
  - Safety and security guidelines

---

**Last Updated:** 2025-11-22
**Repository State:** Specification-only (implementation pending)
**Primary Document:** README.md (449 lines)
