The following sources were checked for this episode. Standards and technical reports are periodically revised and can be adopted differently by sector, country and contract. Verify the project-applicable edition before design or commissioning.

1. **ISA-TR5.9-2023, Proportional-Integral-Derivative (PID) Algorithms and Performance.** Documents common industrial PID forms, implementation options and performance measures. ISA states that the report was intended to lay groundwork because a single standard covering PID fundamentals and special functions did not previously exist. Official ISA pages: https://www.isa.org/standards-and-publications/isa-standards/isa-5-standard and https://www.isa.org/standards-and-publications/isa-standards/isa-standards-committees/isa5-9

2. **ANSI/ISA-5.1-2024, Instrumentation and Control - Symbols and Identification.** Relevant to consistent loop and instrument identification on engineering documents. Official ISA committee page: https://www.isa.org/standards-and-publications/isa-standards/isa-standards-committees/isa5

3. **IEC 61131-3:2025, Programmable controllers - Part 3: Programming languages.** Defines programming-language syntax and semantics for programmable controllers; it does not prescribe a universal PID tuning method. Official IEC page: https://webstore.iec.ch/en/publication/68533

4. **Rockwell Automation Studio 5000 PID/PIDE documentation.** Vendor-specific examples of dependent/independent gains, output limits, derivative smoothing, anti-reset windup, tracking and bumpless transfer. These examples illustrate implementation differences and are not universal requirements. https://www.rockwellautomation.com/en-us/docs/studio-5000-logix-designer/37-00/contents-ditamap/studio-5000-logix-designer/pid-configuration-dialog-box---configuration-tab-o.html and https://www.rockwellautomation.com/en-pr/docs/studio-5000-logix-designer/38-02/contents-ditamap/instruction-set/special-instructions/proportional-integral-derivative--pid-/anti-reset-windup-bumpless-transfer-manual-auto--p.html

5. **J. G. Ziegler and N. B. Nichols, "Optimum Settings for Automatic Controllers," 1942.** Historical foundation for process-reaction and ultimate-gain tuning rules. DOI: https://doi.org/10.1115/1.4019264

6. **Sigurd Skogestad, "Simple analytic rules for model reduction and PID controller tuning," Journal of Process Control 13 (2003) 291-309; corrected/open version in Modeling, Identification and Control 25(2), 2004.** Model-based IMC/SIMC tuning rules and process-model reduction. Author page: https://skoge.folk.ntnu.no/publications/2003/tuningPID/README.html

7. **E. Sundström, M. Bauer, J. L. Guzmán, T. Hägglund and K. Soltesz, "A Practical Guide to PID Controller Implementation," 2026 preprint.** Recent implementation-focused discussion of actuator constraints, measurement noise, bumpless transfer and sampling-time issues. https://arxiv.org/abs/2604.15918

8. **IEC 61511 series, Functional safety - Safety instrumented systems for the process industry sector.** Used only to maintain the boundary between ordinary regulatory control and safety instrumented functions. Project applicability must be established separately.
