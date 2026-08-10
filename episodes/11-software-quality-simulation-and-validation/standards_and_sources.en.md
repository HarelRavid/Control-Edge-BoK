# Standards and source map - Episode 11

> Standards are revised and adopted differently by country, industry and contract. Confirm the project-applicable edition, amendments and legal status before using any statement as a requirement. The episode paraphrases concepts and does not reproduce normative text.

1. **IEC 62381:2024 - Automation systems in the process industry - Factory acceptance test (FAT), site acceptance test (SAT), and site integration test (SIT).** Current third edition. It defines requirements and checklists for FAT, optional Factory Integration Test (FIT), SAT and SIT and is a primary reference for the acceptance-test discussion in this episode.
2. **IEC 61131-3:2025 - Programmable controllers - Part 3: Programming languages.** Current fourth edition; defines syntax and semantics for ST, LD, FBD and SFC-related structuring elements. It is the programming-language foundation behind the PLC software discussed here, but it is not by itself a complete software-quality lifecycle standard.
3. **PLCopen Software Construction Guidelines** and **PLCopen Guideline on Software Quality Metrics (2023).** Industrial-automation guidance for structured software construction, rules, coding patterns, libraries and quality metrics in IEC 61131-3 / PLCopen environments.
4. **ISO/IEC/IEEE 29119-1:2022 - Software testing - Part 1: General concepts** and **ISO/IEC/IEEE 29119-2:2021 - Part 2: Test processes.** Generic software-testing concepts and test-process framework applicable across lifecycle models. These are not automation-sector-specific standards, but they provide useful vocabulary and process structure.
5. **IEC 61508-3:2010 - Functional safety ... Part 3: Software requirements.** Applies to software forming part of safety-related E/E/PE systems and includes lifecycle activities, validation information, modification control and requirements for supporting tools.
6. **ISO 13849-1:2023 - Safety of machinery - Safety-related parts of control systems - Part 1.** Includes software in the methodology for design and integration of machinery safety-related control systems.
7. **ISO 13849-2:2012 - ... Part 2: Validation.** Still the current published edition as of August 2026; a replacement draft is under development. It addresses validation by analysis and testing of safety functions and achieved performance level/category for SRP/CS.
8. **IEC 62061:2021 + AMD1:2024 + AMD2:2026 - Safety of machinery - Functional safety of safety-related control systems.** Current consolidated framework for machinery safety-related control systems, including design, integration, verification, validation and configuration-management topics.
9. **IEC 62832-1/-2/-3:2020 - Digital Factory framework.** Provides principles, model elements and lifecycle-information rules for digital representations of production systems across continuous, batch and discrete processes.
10. **ISO 23247 series - Digital twin framework for manufacturing.** Parts 1, 2 and 4 (2021) provide overview, reference architecture and information exchange; Parts 5 and 6 (2026) extend the framework with digital thread and digital-twin composition. Relevant to the distinction between a simulation model and a broader digital-twin architecture.

## Engineering literature and practice anchors

- V-model and staged verification are presented as engineering patterns, not as a mandatory lifecycle for every automation project.
- Unit testing, software-in-the-loop, hardware-in-the-loop and virtual commissioning are presented as layers of evidence with increasing system fidelity.
- Model fidelity must match the engineering question. A model used to test boolean sequencing does not need the same dynamic accuracy as a model used to tune a control loop.
- Requirements coverage, state-transition coverage and risk-based regression scope are emphasized over a single universal code-coverage percentage.

## Official source links
- IEC 62381:2024: https://webstore.iec.ch/en/publication/67572
- IEC 61131-3:2025: https://webstore.iec.ch/en/publication/68533
- PLCopen Software Construction Guidelines: https://www.plcopen.org/guidelines/software-construction-guidelines/
- PLCopen Guideline on Software Quality Metrics: https://www.plcopen.org/news/plcopen-guideline-on-software-quality-metrics/
- ISO/IEC/IEEE 29119-1:2022: https://www.iso.org/standard/81291.html
- ISO/IEC/IEEE 29119-2:2021: https://www.iso.org/standard/79428.html
- IEC 61508-3:2010: https://webstore.iec.ch/en/publication/5517
- ISO 13849-1:2023: https://www.iso.org/standard/73481.html
- ISO 13849-2:2012: https://www.iso.org/standard/53640.html
- IEC 62061:2021 + AMD1:2024 + AMD2:2026: https://webstore.iec.ch/en/publication/112847
- IEC 62832-1/-2/-3:2020: https://webstore.iec.ch/en/publication/65858
- ISO 23247 series: https://www.iso.org/standard/75066.html
