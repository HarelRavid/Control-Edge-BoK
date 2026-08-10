---
episode: 11
language: en
title: "Software Quality, Simulation and Validation - Proving Industrial Control Software Before It Reaches the Plant"
target_duration: "42-46 minutes"
status: completed
---

# CONTROL EDGE - EPISODE 11
## Software Quality, Simulation and Validation
### Proving industrial control software before it reaches the plant

**Audience:** Mechanical, process, manufacturing and automation engineers  
**Target duration:** 42-46 minutes  
**Format:** Dialogue between Yael, a young mechanical engineer, and Amir, a senior process and controls engineer  
**Core case:** A transfer skid passes normal FAT but resumes from a retained state after a temporary remote-I/O fault, allowing a pump command before a valve is fully open  
**Version:** 1.0 | August 2026

Educational material. It does not replace project-specific engineering, risk assessment, contractual test specifications, manufacturer instructions or the applicable edition of any standard.

# 1. Pre-production alignment check

This episode directly continues Episode 10. Episode 10 ended by asking how we prove that control logic and tuning behave correctly during startup, shutdown, faults, restarts and future changes. Episode 11 answers that question by building a software-quality and test lifecycle around the control system.

Scope boundaries:
- Basic-control software quality, testing and acceptance are the main subject.
- Safety-related software evidence is introduced only to define the boundary; detailed functional safety remains Episode 13.
- Secure-development implications are introduced only as the bridge to Episode 12 on industrial cybersecurity.
- Simulation and digital twins are treated as engineering tools whose fidelity must be defined, not as marketing labels.
- The episode is vendor-neutral and applicable across PLC, PAC, DCS and industrial-PC environments.

# 2. Learning objectives

By the end of the episode, a listener should be able to:
1. Distinguish verification, validation and acceptance in practical engineering terms.
2. Rewrite a vague functional statement into a testable requirement.
3. Build traceability from requirement to implementation and test evidence.
4. Separate unit, integration, system and acceptance test purposes.
5. Design tests for boundaries, state transitions, faults, recovery, persistence, timing and concurrency.
6. Explain the difference among forcing, software-in-the-loop, hardware-in-the-loop and virtual commissioning.
7. Explain why a simulation model itself needs a defined scope and fidelity.
8. Distinguish FAT, FIT, SAT and SIT and describe what each should demonstrate.
9. Build a risk-based regression and release process for future changes.
10. Recognize where general control testing ends and functional-safety validation begins.

# 3. Timing and segment plan

| Time | Segment | Purpose |
|---|---|---|
| 00:00-03:00 | Cold open - the reset nobody tested | Show why happy-path testing misses dangerous transitions. |
| 03:00-07:00 | What software quality means | Define quality as lifecycle evidence, not code aesthetics. |
| 07:00-12:00 | Testable requirements | Connect requirements, states, cause-and-effect and traceability. |
| 12:00-17:00 | Reviews and static checks | Catch defects before dynamic execution. |
| 17:00-23:00 | Test architecture | Unit, integration, system, acceptance, boundaries and faults. |
| 23:00-26:00 | Timing and data quality | Add temporal behavior, timestamps, forces and stale data. |
| 26:00-31:00 | Simulation and virtual commissioning | Build the fidelity ladder from signal injection to HIL. |
| 31:00-36:00 | FAT, FIT, SAT and SIT | Clarify acceptance-test responsibilities and scope. |
| 36:00-38:00 | Defect control | Turn failed tests into traceable engineering evidence. |
| 38:00-41:00 | Regression and release control | Make future changes reproducible and reversible. |
| 41:00-44:00 | Safety-related software boundary | Explain why safety validation requires a stricter lifecycle. |
| 44:00-46:00 | Checklist and bridge | Close with release questions and transition to cybersecurity. |

# 4. Quality-evidence chain

| Engineering layer | Main artifact | Main question | Typical evidence |
|---|---|---|---|
| Need | User / operational requirement | What outcome is required? | URS, operating scenarios |
| System behavior | Functional requirements | What shall the system do? | FDS, sequence descriptions, cause-and-effect |
| Architecture | Modules and interfaces | Who owns each responsibility? | software architecture, interface map |
| Implementation | PLC/DCS/HMI code | Was it implemented as designed? | code review, static analysis, unit test |
| Integration | Interacting subsystems | Do interfaces behave together? | integration test, SIL/HIL |
| System | Complete control application | Does the system handle modes and faults? | system simulation, regression suite |
| Acceptance | Contractual demonstration | Does it meet agreed acceptance criteria? | FAT/FIT/SAT/SIT evidence |
| Operation/change | Released baseline | Can we change it without losing known behavior? | version control, impact analysis, regression, rollback |

# 5. Canonical production assets

The complete spoken dialogue is maintained in [`script.en.txt`](script.en.txt). The paste-ready NotebookLM direction is in [`notebooklm_prompt.en.txt`](notebooklm_prompt.en.txt), and the standards/source map with official links is in [`standards_and_sources.en.md`](standards_and_sources.en.md).

The canonical script covers:
- the reset/recovery fault narrative;
- verification vs validation vs acceptance;
- testable requirements and requirement IDs;
- V-model as an engineering pattern rather than a mandatory lifecycle;
- design review, code review and static analysis;
- unit, integration, system and acceptance tests;
- boundary values, state transitions, fault injection, persistence and concurrency;
- test oracles, requirements coverage and cautious use of code coverage;
- timing, determinism, data quality, forces and overrides;
- software-in-the-loop, hardware-in-the-loop and virtual commissioning;
- model fidelity and why the model itself needs validation;
- FAT, optional FIT, SAT and SIT;
- defect records, deviations and retest;
- impact analysis, regression suites, baselines, release IDs and rollback;
- the boundary between general control testing and functional-safety validation;
- a 12-question pre-release checklist and bridge to Episode 12.

# 6. Practical test-design matrix

| Test family | Example on the transfer skid | Why it matters |
|---|---|---|
| Nominal | Start transfer with all permissives healthy | Confirms intended production behavior |
| Boundary | Level exactly at minimum start limit | Finds comparison errors |
| State transition | Stop during valve travel, then reset | Exposes incomplete transition logic |
| Fault injection | Lose valve I/O quality for 3 s | Tests abnormal detection and recovery |
| Persistence | Power cycle during transfer | Verifies retained vs reinitialized state |
| Concurrency | Two sequences request shared pump | Finds ownership/arbitration defects |
| Timing | Delayed feedback near timeout limit | Tests timer assumptions and race conditions |
| Communication | Drop controller-to-remote-I/O link | Tests stale/bad data handling |
| Operator action | Manual command during auto fault | Tests mode ownership and authorization logic |
| Regression | Rerun all above after valve-block change | Detects unintended effects of maintenance |

# 7. Twelve-question release checklist

1. Are requirements observable and testable?
2. Is each important requirement traceable to code and test evidence?
3. Have restart, retained data and mode transitions been tested?
4. Have negative and recovery paths been tested?
5. Has an independent engineer reviewed architecture and code?
6. Are test environment and software versions recorded?
7. Is simulation-model fidelity documented and validated where required?
8. Are unit, integration, system and acceptance tests separated by purpose?
9. Did FAT include failures and recovery, not only normal operation?
10. Did SAT/SIT re-verify installed wiring, actuators, networks and interfaces?
11. Does every change have impact analysis, regression evidence and rollback capability?
12. Are safety-related functions handled under their applicable safety lifecycle?

# 8. Technical glossary

| Term | Meaning in this episode |
|---|---|
| Verification | Evidence that specified design or implementation requirements have been correctly met. |
| Validation | Evidence that the integrated system satisfies intended use / operational needs in context. |
| Acceptance | Contractual or project agreement that demonstrated criteria have been met. |
| Test oracle | The documented expected result used to judge pass/fail. |
| Regression test | Re-execution of previously passed tests to detect unintended effects after change. |
| SIL | Software-in-the-loop in this episode's simulation context; do not confuse with Safety Integrity Level. |
| HIL | Hardware-in-the-loop - real controller hardware against a simulated plant. |
| Virtual commissioning | Pre-site commissioning of automation behavior against a virtual machine/process model. |
| Model fidelity | How accurately the model represents characteristics relevant to the test objective. |
| FAT / FIT / SAT / SIT | Factory Acceptance / Factory Integration / Site Acceptance / Site Integration testing layers. |
| Traceability | Ability to link needs, requirements, implementation and test evidence. |
| Baseline | Identified, controlled version of software/configuration used as a reference. |
| Impact analysis | Evaluation of what may be affected by a proposed change. |

# 9. Standards and sources

See [`standards_and_sources.en.md`](standards_and_sources.en.md). Primary anchors include IEC 62381:2024, IEC 61131-3:2025, PLCopen Software Construction Guidelines and Software Quality Metrics, ISO/IEC/IEEE 29119-1/-2, IEC 61508-3, ISO 13849-1/-2, IEC 62061, IEC 62832 and ISO 23247.

# 10. Episode quality gate

- Happy-path FAT is explicitly shown as insufficient.
- Requirements, implementation and test evidence are connected through traceability.
- Static review and dynamic testing are clearly distinguished.
- Simulation levels are differentiated without marketing overstatement.
- FAT/FIT/SAT/SIT have separate engineering purposes.
- Regression testing is tied to version control, impact analysis and rollback.
- Functional-safety standards are presented as a stricter lifecycle boundary, not as generic PLC test rules.
- The closing creates a direct bridge to Episode 12 on industrial cybersecurity.
