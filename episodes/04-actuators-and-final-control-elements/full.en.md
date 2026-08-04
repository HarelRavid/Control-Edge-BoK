---
episode: 4
language: en
title: "Actuators and Final Control Elements"
target_duration: "40-44 minutes"
status: completed
extracted_from: pdf-text-extraction
---

Actuators and Final Control Elements
How software commands become force, motion, heat and flow
Solenoids, pneumatics, hydraulics, control valves, heating, fail-safe design and diagnostics
Audience
Mechanical, process, manufacturing, instrumentation and
automation engineers
Target duration
40-44 minutes
Format
Yael - young mechanical engineer; Amir - senior process and
control engineer
Core example
Cooling valve commanded to 80% but failing to deliver cooling
Deliverable
Full script + NotebookLM prompt + checklist + sources
Educational material. It does not replace engineering design, risk assessment, sizing, manufacturer
instructions or applicable adopted standards.
# 1. Pre-production alignment check
- The episode continues directly from Episode 3: from the signal received by the controller to the physical
effect produced by the system.
- It is not a product catalogue; each actuator is evaluated by energy, load, dynamics, feedback and failure
mode.
- Control valves receive added depth because they join mechanics, fluid mechanics and loop behavior.
- Functional safety is presented as a lifecycle boundary without detailed SIL or PL calculations.
- The ending bridges directly to Episode 5 on motors, VFDs, servos and motion control.
Freshness check
The source map was checked against IEC, ISO and ISA. The episode uses IEC 60534-1:2023, ISO 13849-1:2023 and the
new IEC 61514:2026 edition for valve positioners.
# 2. Episode objectives
- Map the complete actuation chain from software command to physical effect and feedback.
- Distinguish command, actuator state and process effect.
- Compare electrical switching, solenoids, pneumatic, hydraulic, electric and thermal actuators.
- Explain control-valve sizing, characteristic, actuator sizing, positioners and common mechanical
nonlinearities.
- Design fail-safe behavior around loss of power, air, communication and stored energy.
- Separate normal control from safety-related final-element functions.
- Use diagnostics, proof testing and maintenance evidence to sustain performance.
# 3. Timing and segment plan
Time
Segment
Purpose
00:00-03:00
Cold open
Command is not motion; motion is not effect.

Time
Segment
Purpose
03:00-06:30
Actuation chain
Map energy, interface, actuator, load and
feedback.
06:30-10:30
Electrical switching
Coils, relays, contactors, SSRs and solenoids.
10:30-15:00
Pneumatics
Force, speed, compressibility and loss of air.
15:00-19:00
Hydraulics
Force density, contamination and stored
energy.
19:00-25:30
Control valves
Sizing, characteristics, actuators and
positioners.
25:30-29:30
Electric mechanisms
Brakes, clutches, steppers and transmissions.
29:30-33:30
Heating
Power interfaces and independent protection.
33:30-38:00
Fail-safe
Safe state and functional-safety boundaries.
38:00-41:30
Diagnostics
Feedback, testing and maintenance.
41:30-44:00
Resolution
Troubleshoot the cooling valve and bridge to
motors.
# 4. Actuation-chain map
Stage
Engineering decision
Typical failure
# 1. Required effect
Define flow, force, motion, holding, stopping or
heat transfer.
Selecting a device before defining the real
outcome.
# 2. Energy source
Electrical power, compressed air, hydraulic
pressure, spring or stored energy.
Loss, contamination, insufficient capacity or
hazardous residual energy.
# 3. Power interface
Relay, contactor, SSR, drive, solenoid pilot, I/P
or valve positioner.
Inrush, leakage, welded contacts, transients,
wrong pressure or bandwidth.
# 4. Actuator
Convert energy into linear/rotary motion, force,
torque or heat.
Undersizing, stall, friction, seal wear,
overheating.
# 5. Transmission and load
Linkage, gearbox, screw, valve trim, gripper,
brake or heater surface.
Backlash, looseness, jam, wear, local
overheating.
# 6. Feedback and validation
Confirm position, pressure, current, speed,
force or process effect.
Displaying command as if it were actual state.
# 7. Safe state and lifecycle
Define response to failures, test, maintain and
document.
Uncontrolled restart, trapped energy, untested
dormant failure.
# 5. Actuator decision map
Technology
Typical use
Selection questions
Solenoid / relay output
Fast discrete switching, pilot control, isolation.
Voltage, current, inrush, suppression, leakage,
duty, response time.
Pneumatic cylinder
Fast linear motion, clamping, sorting, simple
positioning.
Force margin, speed, cushioning, air quality,
loss-of-air behavior.
Hydraulic cylinder or motor
High force or torque, controlled load motion.
Pressure, filtration, heat, leakage, hose failure,
load holding.
Control valve
Continuous regulation of process flow or
pressure.
Cv/Kv, DP, fluid state, cavitation, noise,
rangeability, shutoff.
Electric linear/rotary actuator
Remote positioning, low air availability, slow
high-torque duty.
Torque profile, speed, duty, gearbox, manual
override, fail action.
Brake / clutch / latch
Hold, stop, couple or release mechanical
Service vs holding duty, wear, diagnostics,

Technology
Typical use
Selection questions
energy.
residual motion.
Heater / power controller
Add controlled thermal power.
Load type, current, switching, heat removal,
independent high limit.
Core principle
Command, actual state and process effect must be identified separately in I/O, code and HMI.
# 6. NotebookLM production prompt
Paste-ready instruction
Create an English-only podcast episode of 40-44 minutes using only this document.
Hosts: Yael, a sharp and curious young mechanical engineer; Amir, a calm senior process and control engineer. Use
approximately 45% Yael and 55% Amir.
Use the cooling valve commanded to 80% without delivering cooling as the narrative thread, and resolve it only at the end.
Repeatedly distinguish command, state and effect. Keep a natural technical dialogue rather than a read lecture. Do not read
URLs or clauses. Do not invent Cv, torque, SIL, PL or response-time requirements. Present fail-safe as a result of risk
assessment, not a universal rule. Emphasize stored energy and maintenance boundaries.
Required structure: opening; actuation chain; switching and solenoids; pneumatics; hydraulics; control valves; electric
actuators and brakes; heating; fail-safe; diagnostics; resolution and bridge to motors. Use the full script as the factual
framework, allowing only short natural reactions that do not change meaning.
# 7. Full episode script
## 00:00-03:00 | Cold open - the valve that obeyed and still failed
Amir: A reactor cooling valve receives a command to open to eighty percent. The HMI shows eighty percent.
The controller output is eighty percent. Yet the reactor temperature keeps rising. Operations conclude that
the control loop is badly tuned.
Yael: But the command is not the same as physical motion, and physical motion is not the same as flow.
Amir: Exactly. The positioner may be starved of air, the stem may be sticking, the linkage may be loose, the
valve may be undersized, the trim may be damaged, or the differential pressure may be far from the design
case. A perfect software command can end at a weak, slow or failed final element.
Yael: So today we follow the opposite direction from Episode 3. The sensor converted physics into
information; now the actuator converts information into force, motion, heat or flow.
Amir: And we will keep one rule throughout the episode: command, state and effect are three different things.
Good automation must know which of the three it is displaying and protecting.
Yael: We will cover solenoids, pneumatic and hydraulic cylinders, control valves, heaters, brakes, clutches
and other loads, then finish with fail-safe design and the cooling-valve fault.
## 03:00-06:30 | The actuation chain
Yael: What is the complete chain between a PLC bit and a moving mechanism?

Amir: Start with the demanded process or machine effect: stop a shaft, clamp a part, meter steam, lift a load
or add heat. The controller calculates a command. An output module or network transmits it. A power
interface provides the required voltage, current, pressure or flow. The actuator converts energy into motion or
heat. The transmission mechanism applies it to the load. Feedback confirms state, and the process
responds.
Yael: So a digital output is rarely driving the real load directly.
Amir: Correct. It may energize an interposing relay, contactor, solid-state relay, solenoid coil, drive enable or
valve positioner. The interface must handle inrush current, inductive energy, switching frequency, isolation
and fault detection. A relay contact is not an infinite-life logic symbol.
Yael: And every layer has a different failure mode.
Amir: Yes. The PLC can command ON while a fuse is open. The contactor can pull in while one power pole is
damaged. A solenoid can energize while the spool is stuck. A cylinder can move while the load is
mechanically jammed. Feedback must be chosen around the actual hazard and required effect.
## 06:30-10:30 | Discrete electrical actuators and switching
Yael: Let us start with simple outputs: coils, relays, contactors and solenoids.
Amir: A coil is an inductive load. When current is interrupted, the magnetic field collapses and generates a
voltage transient. Suppression protects the output but changes release time. A diode gives strong
suppression on DC coils but can slow dropout; other suppressors trade voltage for speed. That matters when
a fast release is part of a safety or cycle-time requirement.
Yael: What must be checked before assigning a PLC output?
Amir: Steady current, inrush, leakage current, minimum load, switching frequency, short-circuit behavior,
common grouping, diagnostic coverage and whether the load is AC or DC. Also check whether a de-
energized output truly removes energy or only removes a command while stored energy remains.
Yael: Mechanical relays versus solid-state relays?
Amir: Mechanical relays provide galvanic separation and tolerate many load types, but contacts wear,
bounce and can weld. Solid-state devices switch quickly and silently, yet have leakage, voltage drop, heat
dissipation and characteristic failure modes. For heaters, an SSR may provide frequent proportional time
control, while a contactor may serve isolation or backup shutdown. The architecture comes from the risk and
duty cycle.
Yael: A solenoid valve is also not just a coil.
Amir: Right. The coil creates magnetic force, but the valve has an armature or pilot stage, seals, orifices and
flow limits. Pilot-operated valves may not shift below a minimum differential pressure. Contamination,
moisture, exhaust restriction and wrong porting can defeat the command.
## 10:30-15:00 | Pneumatics - fast, clean and compressible
Yael: Why are pneumatic cylinders so common in machines?
Amir: They are simple, fast, tolerant of overload and easy to distribute across a factory. But air is
compressible. Position stiffness, speed stability and force depend on pressure, flow, volume, cushioning,
friction and load. A cylinder sized only from bore times supply pressure ignores losses, rod area, breakaway
friction, pressure drop and dynamic margin.
Yael: How should speed be controlled?
Amir: Usually by controlling exhaust flow - meter-out - because the compressed air on the exhausting side
provides damping. Meter-in can become unstable with overrunning loads. The correct choice depends on

load direction and motion. Cushioning, shock absorbers and mechanical stops must handle kinetic energy;
the end sensor should not be used as the physical stop.
Yael: What happens during loss of air?
Amir: That is a design question, not a universal answer. A vertical axis may fall unless mechanically held. A
gripper may release or remain trapped by check valves. A directional valve may spring to a defined position,
hold the last position or vent. The safe state must consider trapped pressure, gravity, maintenance and
restart. Dumping a manifold can itself create hazardous motion.
Yael: Which standards form the baseline?
Amir: ISO 4414 provides general rules and safety requirements for pneumatic systems on machinery. ISO
15552 standardizes important mounting dimensions for a common cylinder series, but dimensional
interchangeability does not guarantee equivalent dynamics, seals or lifetime.
## 15:00-19:00 | Hydraulics - force density and stored energy
Yael: Hydraulics give much higher force density.
Amir: Yes, with relatively incompressible fluid, high pressures and precise force control. But leakage,
contamination, temperature, hose failure, injection injury and stored energy become central. Accumulators
and suspended loads can remain hazardous after electrical power is removed.
Yael: What is commonly missed in control design?
Amir: Valve overlap, pressure compensation, load-induced motion, cavitation, thermal expansion of trapped
fluid and the difference between commanding a directional valve and controlling velocity. Servo and
proportional valves need clean fluid, suitable filtration and stable supply. A cylinder may creep because of
internal leakage or load, not software.
Yael: How do we stop a vertical hydraulic load safely?
Amir: Often with load-holding valves, counterbalance valves, pilot-operated checks or a mechanical brake,
selected and validated for the hazard. Closing a directional valve at the manifold may not prevent hose-failure
motion. ISO 4413 establishes general safety requirements, and the machinery risk assessment determines
the protective architecture.
Yael: So isolation requires dissipation and verification of pressure, not just an OFF command.
Amir: Exactly. Lockout must address every energy source and stored-energy location.
## 19:00-25:30 | Control valves - where loop theory meets mechanics
Yael: Let us return to process control valves. What makes them more than a pipe component?
Amir: A control valve is a variable restriction assembled from body, trim, actuator and usually a positioner.
Selection combines fluid mechanics, materials, pressure boundary, actuator thrust or torque, dynamic
response, leakage requirements and maintainability. IEC 60534 is the central international series for
industrial-process control valves; ISA-75 provides closely related standards and practices.
Yael: Why can a valve with the correct line size still control badly?
Amir: Because line size is not valve capacity. The valve is sized for required flow, pressure drop, fluid
properties, choked flow, cavitation or flashing risk, noise and operating range. An oversized valve may
operate near the seat where small movements create large flow changes, worsening resolution and wear. An
undersized valve saturates fully open.
Yael: And inherent characteristic is not installed characteristic.
Amir: Correct. Linear, equal-percentage and quick-opening describe inherent flow behavior under specified
test conditions. In the installed system, pump curve and piping losses change the pressure drop across the

valve. Equal-percentage trim is common because it can compensate for changing system gain, but it is not
automatically best.
Yael: What does the actuator have to overcome?
Amir: Packing friction, seat load, pressure forces, unbalance, dynamic forces and required shutoff. Pneumatic
diaphragm and piston actuators are common; electric and hydraulic actuators are used when their
characteristics fit. The actuator must be sized for the worst credible pressure and failure mode, not only
normal modulation.
Yael: What does the positioner add?
Amir: It closes a local position loop around the actuator and valve. It improves positioning against friction and
pressure forces, converts command to pneumatic output, and modern devices provide diagnostics. But
position feedback does not prove flow. A detached stem connection can report actuator travel while the plug
does not move as intended.
Yael: Which mechanical problems appear in trends?
Amir: Deadband, hysteresis, stiction, backlash, air-supply limitation and slow response. The loop may
oscillate because the valve sticks and releases, not because PID tuning is aggressive. Step tests and
signatures can separate controller behavior from final-element dynamics.
## 25:30-29:30 | Electric actuators, brakes, clutches and mechanical transmission
Yael: Not every controlled movement deserves a full servo system.
Amir: True. Electric linear actuators, geared motors, stepper drives, brakes, clutches and latching
mechanisms cover many duties. The selection starts with force or torque versus speed, stroke or angle, duty
cycle, backlash, holding requirement, environment and what happens without power.
Yael: A brake is an actuator too.
Amir: Yes. A spring-applied, electrically released brake can hold a vertical axis after power loss, but its
stopping capability, wear, air gap, thermal capacity and diagnostic strategy must be engineered. A holding
brake is not always rated as a service brake. Likewise a clutch can fail to transmit or fail to release.
Yael: What about stepper motors losing position?
Amir: Open-loop steppers infer position from commanded steps. Excess torque demand, acceleration or
resonance can cause missed steps with no automatic awareness. Closed-loop feedback or homing can
detect or correct some faults, but mechanical couplings, belts and screws still require inspection. We will treat
motors and motion control in a dedicated episode.
## 29:30-33:30 | Heating and thermal final elements
Yael: Heating has no visible stem, so engineers sometimes treat it as easy.
Amir: Yet heaters combine high energy, thermal lag and fire or product-damage hazards. The controller may
switch a contactor, SSR, thyristor controller or power regulator. The load can be resistive, inductive or have
temperature-dependent resistance. Wiring, protection and heat removal must be designed for the real current
and ambient conditions.
Yael: How should protection be separated from temperature control?
Amir: The normal control loop regulates temperature. An independent high-temperature protective function
should detect a dangerous condition and remove or limit energy through an adequately independent path. A
welded SSR can remain conducting after the logic output turns off, so a separate contactor or other isolation
element may be required by the risk assessment.
Yael: And sensor placement matters again.

Amir: Very much. A heater can overheat locally while the bulk sensor remains below setpoint. Flow proving,
low-level protection, surface temperature, overtemperature cutouts and cooldown logic may all be necessary.
The final effect is heat transfer, not simply electrical ON.
## 33:30-38:00 | Fail-safe, de-energize-to-trip and the meaning of safe state
Yael: People often ask whether a valve should fail open or fail closed.
Amir: That question is incomplete. Safe state depends on the hazard and the initiating failure. Cooling water
may fail open to protect temperature, but uncontrolled cooling can create another hazard. Fuel gas usually
tends toward isolation, but venting, trapped inventory and depressurization must be considered. Some
applications require fail-in-place or a controlled sequence rather than one static position.
Yael: How does spring return help?
Amir: It stores mechanical energy to drive the actuator toward a defined position when motive energy is lost.
But spring direction, available force, travel time, valve torque profile and common-cause failures must be
verified. Stored energy is useful for safety but can also be hazardous during maintenance.
Yael: Is de-energize-to-trip always safer?
Amir: It often reveals loss of power and allows a spring-return final element to move safe, but it is not
universal. Spurious trips, energized-to-trip applications, battery-backed systems and continuously powered
actuators require analysis. Functional safety standards treat the complete safety function from sensor
through logic solver to final element, including proof testing and failure data.
Yael: What is the difference between machine and process frameworks here?
Amir: For machinery, ISO 13849-1 and IEC 62061 provide methods for safety-related control systems across
electrical, pneumatic, hydraulic and mechanical technologies. For process SIS, IEC 61511 covers lifecycle
requirements. None of them allows us to label a single certified component and declare the full function safe.
## 38:00-41:30 | Diagnostics, testing and maintenance
Yael: How do we know an actuator will work when demanded?
Amir: Use appropriate feedback, diagnostics and periodic testing. End switches can confirm terminal position;
analog feedback can show travel; pressure switches can confirm supply; motor current can reveal load; smart
positioners can trend friction and travel deviation. But diagnostics must be independent enough to detect the
relevant fault.
Yael: What is partial-stroke testing?
Amir: For some shutdown valves, a small controlled movement is periodically commanded to reveal sticking
or actuator faults without fully interrupting the process. It improves diagnostic coverage for certain failures but
does not replace full proof testing and cannot reveal every failure. Test intervals and procedures belong to
the safety lifecycle.
Yael: Maintenance can change the control response.
Amir: Absolutely. Repacking a valve changes friction; replacing a cylinder changes cushioning; fitting a
different solenoid changes flow; changing suppressors changes release time. As-found and as-left evidence,
configuration control, spare equivalence and functional testing are part of control engineering.
## 41:30-44:00 | Resolve the cooling-valve fault and close
Yael: Back to the reactor cooling valve. What is the troubleshooting sequence?
Amir: First compare command, actual position and process effect on the same timeline. Second verify
instrument air pressure and flow during travel. Third perform a safe stroke or step test and observe response
time, deadband and friction. Fourth inspect linkage, stem, packing and travel calibration. Fifth verify valve

sizing and available pressure drop at the current operating condition. Sixth inspect trim for blockage or
damage. Only after that revisit PID tuning.
Yael: Suppose the HMI showed eighty percent because it was displaying command, not feedback.
Amir: Then the screen told the truth about the software and encouraged a false conclusion about the
machine. Rename it Output Command, add validated position feedback where justified, and make bad or
stale feedback visible.
Yael: The engineering checklist is therefore: required effect, energy source, actuator and transmission, force
and speed margin, feedback, failure position, stored energy, manual intervention, environment, maintenance
and proof of operation.
Amir: Exactly. The final element is where code becomes consequence. Design it with the same rigor as the
algorithm.
Yael: In Episode 5 we move into electric motors, VFDs, servos and motion control - how torque, speed and
position become coordinated machine behavior.
Amir: Until then, never confuse a green output bit with a completed physical action.
# 8. Producer and host notes
- Maintain a consistent distinction between command, feedback and effect.
- Do not turn technologies or vendors into commercial rankings.
- Stop before detailed control-valve sizing and refer to competent engineering and process data.
- Treat loss of power, air, hose integrity, communication and stored energy as separate scenarios.
- Do not describe partial-stroke testing as a replacement for full proof testing.
- Keep the fault resolution for the closing segment.
# 9. Engineering actuation-chain checklist
# 1. What physical effect is required in normal, upset and emergency states?
# 2. What is the energy source and its capacity, quality and isolation method?
# 3. What force or torque, speed, stroke, duty cycle and margin are required?
# 4. What inrush, transient, leakage, heat and switching-frequency limits apply?
# 5. What friction, backlash, compliance, cushioning and kinetic energy exist?
# 6. Which feedback proves state and which feedback proves effect?
# 7. What happens on loss of power, air, pressure, network or sensor?
# 8. What stored energy remains and how is it dissipated and verified?
# 9. What is the safe state, who defined it and how is it validated?
# 10. How are manual override, lockout and restart controlled?
# 11. Which acceptance, stroke, proof and periodic tests are required?
# 12. How are as-found/as-left evidence, spares and configuration maintained?
# 10. Glossary
Term
Meaning in this episode
Actuator
Device that converts supplied energy and a command into mechanical
motion, force, torque or another physical output.
Final control element
The part of a process control loop that directly changes the manipulated
variable, commonly a control valve or drive.
Final element
In functional safety, the subsystem that acts on the process to achieve or
maintain a safe state.
Stiction
Static friction behavior that prevents movement until force builds and the

Term
Meaning in this episode
mechanism breaks free.
Deadband
Range of input change that produces no corresponding output change.
Fail-safe
Designed behavior that moves or maintains the system in a defined safe
condition for specified failures.
De-energize-to-trip
Architecture in which removal of energy initiates the protective action.
Proof test
Periodic test intended to reveal dangerous hidden failures not detected
automatically.
Partial-stroke test
Limited valve movement used to detect some failures without executing a
full shutdown stroke.
Stored energy
Energy retained in springs, pressure, gravity, capacitance, rotating inertia
or heat after command or power removal.
# 11. Standards and source map
Use note
For every project, verify the edition adopted by contract, jurisdiction and sector, including amendments and manufacturer
requirements.
# 13. IEC 60534-1:2023 - Control valve terminology and general considerations. Official source
# 14. IEC 60534-2-4:2009 - Inherent flow characteristics and rangeability. Official source
# 15. IEC 60534-2-3:2015 - Flow-capacity test procedures for control valves. Official source
# 16. IEC 60534-4:2021 - Inspection and routine testing of control valves. Official source
# 17. IEC 60534-7:2010 - Control valve data-sheet requirements. Official source
# 18. IEC 61514:2026 - Performance evaluation of pneumatic-output valve positioners. Official source
# 19. ISA-75 series - Control valve design, sizing, testing, performance and diagnostics standards. Official
source
# 20. ISO 4414:2010 - General rules and safety requirements for pneumatic fluid power systems. Official
source
# 21. ISO 4413:2010 - General rules and safety requirements for hydraulic fluid power systems. Official source
# 22. ISO 15552:2018 - Interchangeability dimensions for a common pneumatic cylinder series. Official source
# 23. ISO 12100:2010 - Machinery risk assessment and risk reduction principles. Official source
# 24. ISO 13849-1:2023 - Safety-related parts of machinery control systems, including non-electrical
technologies. Official source
# 25. IEC 62061:2021+A1:2024 - Functional safety of safety-related machinery control systems. Official source
# 26. IEC 60204-1:2016+A1:2021 - Electrical equipment of machines, including power-drive and emergency-
stop requirements. Official source
# 27. IEC 61511-1:2016+A1:2017 - Safety instrumented systems lifecycle requirements for process industries.
Official source
# 28. ISA-84 series - Guidance and standards for SIS from sensor through logic solver to final element. Official
source
# 12. Episode quality gate
- The listener can draw a complete command-to-effect chain.
- Command, state and effect are not treated as synonyms.
- Pneumatics and hydraulics include stored energy and supply-loss behavior.
- Control valves are explained through sizing, dynamics, positioners and failure modes.
- Fail-safe is presented as a result of risk assessment.

- Functional safety stays within correct responsibility boundaries.
- The ending bridges directly to motors and motion control.
