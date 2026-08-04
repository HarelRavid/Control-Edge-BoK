---
episode: 5
language: en
title: "Motors, VFDs, Servos and Motion Control"
target_duration: "42-45 minutes"
status: completed
extracted_from: docx
---

> CONTROL EDGE \| EPISODE 5<br>Motors, VFDs, Servos and Motion Control<br>From speed regulation to precise, coordinated machine motion<br>Induction motors \| vector control \| servo loops \| motion profiles \| safe motion \| regenerative energy

| Audience | Mechanical, process, manufacturing, instrumentation and automation engineers |
| --- | --- |
| Target duration | 42-45 minutes |
| Format | Yael - young mechanical engineer; Amir - senior process and control engineer |
| Core example | Indexing conveyor overshoots position and trips the drive on DC-bus overvoltage during deceleration |
| Deliverable | Full script + NotebookLM prompt + decision maps + commissioning checklist + sources |

Educational material. It does not replace motor/drive sizing, electrical design, risk assessment, safety validation, manufacturer instructions or applicable adopted standards.

# 1. Pre-production alignment check

- The episode continues directly from Episode 4: from generic actuators to the dominant industrial actuation system - the electric power drive.

- The structure separates motor physics, power electronics, control mode, feedback, mechanics and machine-level motion software.

- Vendor terms are treated as implementation labels, not universal engineering categories.

- Functional safety is explained through drive safety functions, without pretending that a certified drive alone makes a machine safe.

- The ending bridges to the next episode on industrial communication and deterministic networks.

> Freshness check<br>The source map was checked against current official IEC, ISO and PLCopen pages. It reflects IEC 60034-1:2026, IEC 60034-30-1:2025, IEC 61800-9-2:2023+A1:2025 and IEC 62061 Amendment 2:2026. Always verify the edition adopted by contract and jurisdiction.

# 2. Episode objectives

- Draw the complete chain from motion requirement to motor, drive, feedback, mechanics and process effect.

- Distinguish speed control, torque control, position control and coordinated motion.

- Compare induction, permanent-magnet, synchronous-reluctance, stepper and servo solutions at an engineering level.

- Size a drive system using torque-speed demand, inertia, duty, thermal limits, overload and regenerative energy.

- Explain scalar, sensorless-vector and closed-loop vector control without turning the episode into a power-electronics course.

- Recognize drive-motor-cable integration risks: PWM stress, motor cooling, EMC, reflected waves and bearing currents.

- Use motion profiles, feedback, diagnostics and safety functions deliberately.

# 3. Timing and segment plan

| Time | Segment | Purpose |
| --- | --- | --- |
| 00:00-03:00 | Cold open | A positioning fault and an overvoltage trip reveal that motion is a system problem. |
| 03:00-06:30 | Power-drive chain | Map requirement, mechanics, motor, converter, feedback and controller. |
| 06:30-10:30 | Motor families | Induction, PM, synchronous reluctance, stepper and servo concepts. |
| 10:30-14:30 | Torque, speed and sizing | Continuous/peak torque, inertia, duty and thermal margin. |
| 14:30-19:00 | VFD control modes | V/f, sensorless vector, closed-loop vector and torque control. |
| 19:00-23:00 | Integration and EMC | PWM, cable, insulation, cooling, bearing currents and grounding. |
| 23:00-28:00 | Servo architecture | Nested loops, encoder feedback, following error and tuning. |
| 28:00-32:00 | Motion profiles | Trapezoidal and S-curve moves, jerk, homing and mechanics. |
| 32:00-36:00 | Coordinated motion | Electronic gearing, camming, interpolation and deterministic updates. |
| 36:00-39:30 | Safe motion | STO, SS1, SOS, SLS, braking and restart behavior. |
| 39:30-42:00 | Energy and diagnostics | System efficiency, regeneration, trends and commissioning evidence. |
| 42:00-45:00 | Fault resolution | Resolve the indexing fault and bridge to industrial networks. |

# 4. Power-drive and motion architecture map

| Stage | Engineering decision | Typical failure |
| --- | --- | --- |
| 1. Motion requirement | Define speed range, accuracy, repeatability, cycle time, force/torque, stopping and holding. | Selecting a motor from nameplate power alone. |
| 2. Load and mechanics | Quantify inertia, friction, gravity, gearbox, screw, belt, compliance and backlash. | Ignoring reflected inertia or resonance. |
| 3. Motor | Convert electrical energy into torque across the required speed and duty. | Thermal overload, demagnetization, poor low-speed cooling or wrong brake. |
| 4. Power converter / drive | Supply controlled voltage, current and frequency; manage limits and regeneration. | Undersized current, overvoltage on deceleration, harmonics or overheating. |
| 5. Feedback | Measure rotor position, speed, current, load position or process response. | High encoder resolution mistaken for machine accuracy. |
| 6. Motion controller | Generate profiles, synchronize axes, handle states and coordinate machine logic. | Non-deterministic updates, ambiguous ownership or hidden mode changes. |
| 7. Safety and lifecycle | Stop, hold, restart, test, maintain and preserve configuration evidence. | STO treated as electrical isolation or tuning changes left undocumented. |

# 5. Technology decision map

| Technology | Typical use | Selection questions |
| --- | --- | --- |
| Across-the-line motor | Fixed-speed loads with acceptable inrush and simple control. | Starting current, process shock, protection, starting torque and energy use. |
| VFD with scalar V/f | Pumps, fans and simple conveyors where speed accuracy and low-speed torque demands are modest. | Speed range, boost, slip, cooling, minimum frequency and process curve. |
| Sensorless-vector drive | Wide speed range and improved torque control without encoder feedback. | Motor identification, zero-speed requirement, load changes and estimation limits. |
| Closed-loop vector drive | Accurate speed/torque, low-speed operation, hoists, winders and demanding machines. | Encoder type, feedback integrity, overspeed, brake coordination and tuning. |
| Servo system | High-dynamic position control, indexing, registration, robotics and coordinated axes. | Peak/continuous torque, inertia, resonance, repeatability, mechanics and bus cycle. |
| Stepper system | Low-cost incremental motion with predictable load and moderate dynamics. | Missed steps, resonance, heating at standstill, torque-speed falloff and homing. |
| Regenerative drive / shared DC bus | Frequent braking, overhauling loads or energy exchange between axes. | Grid interface, common-bus protection, fault propagation and braking strategy. |

> Core principle<br>Choose the control architecture from the required physical behavior and failure response. Do not select a motor, drive or servo family from power rating or marketing terminology alone.

# 6. NotebookLM production prompt

> Paste-ready instruction<br>Create an English-only engineering podcast episode of 42-45 minutes using only this document.<br><br>Hosts:<br>- Yael: a young mechanical engineer. Curious, technically strong, willing to challenge vague automation language. She asks from the viewpoint of mechanics, loads, shafts, gearboxes and machine behavior.<br>- Amir: a senior process and control engineer who began in machinery and drives. Calm, evidence-driven and practical. He explains trade-offs, failure modes and commissioning logic without sounding like a lecturer.<br><br>Conversation rules:<br>1. Keep a natural two-person conversation, approximately 45% Yael and 55% Amir.<br>2. Use the indexing-conveyor fault as a thread throughout the episode; do not reveal the final diagnosis until the closing segment.<br>3. Distinguish command, motor response, load response and process result every time these could be confused.<br>4. Explain equations verbally and intuitively. Do not read tables or source lists aloud.<br>5. Avoid vendor promotion. Vendor-specific terms may be mentioned only as examples of implementations.<br>6. Make safety boundaries explicit: STO is not electrical isolation; a certified drive does not certify the machine.<br>7. Use one short recap near the middle and one engineering checklist at the end.<br>8. Preserve the timing and section order. Do not invent technical claims beyond the document.<br>9. Pronounce abbreviations once in full: variable-frequency drive, safe torque off, electromagnetic compatibility, and so on.<br>10. End with a clear bridge to industrial networks and deterministic communication.

# 7. Full episode script

## 00:00-03:00 | Cold open - the axis that arrives, but not where it should

Yael: The indexing conveyor has a simple job: move a tray exactly four hundred millimetres, stop, and let the robot pick. Yet every twentieth cycle it overshoots by two millimetres. Yesterday the drive also tripped on DC-bus overvoltage during deceleration. Maintenance wants to increase the position gain. Production wants a larger motor. The programmer says the command position is perfect. Where do we start?

Amir: We start by refusing all three proposed fixes until we know which physical quantity is wrong. A perfect position command proves only that the motion planner generated the intended number. It does not prove the drive followed it, the motor produced the expected torque, the gearbox transmitted it, or the tray reached the commanded location.

Yael: So this is the motor-control version of the principle from the last episode: command is not state, and state is not effect.

Amir: Exactly. In a motion system we add another layer: the motor shaft can follow perfectly while the load is wrong because of backlash, belt stretch, compliance, slip or a sensor mounted on the wrong side of the mechanism.

Yael: And the overvoltage trip during stopping suggests the load is returning energy to the drive.

Amir: It may. A rotating mass that is decelerated becomes a generator. That energy must go somewhere: into the DC bus, a braking resistor, another axis on a common bus, a regenerative front end, mechanical losses, or back to the grid. If the destination is inadequate, DC-bus voltage rises and the drive protects itself.

Yael: So one symptom points toward mechanics and control; the other toward energy flow. Today we need the whole system.

Amir: Yes. By the end of the episode we will know when a VFD is enough, when a servo is justified, how to think about torque and inertia, and why tuning cannot compensate for a badly understood machine.

## 03:00-06:30 | The power-drive chain

Yael: Let us define the object. Is the VFD the controller, the actuator, or the power supply?

Amir: Depending on the architecture, it contains pieces of all three. The power-drive system includes the power converter, its control and protection, the motor, and their interfaces. At machine level we should draw a longer chain: motion requirement, load mechanics, motor, drive, feedback, motion controller, safety functions and process effect.

Yael: Why begin with the requirement rather than the motor?

Amir: Because “a five-kilowatt motor” says almost nothing about the move. A pump may need continuous torque near one operating speed. An indexer may need high peak torque for a fraction of a second and little average power. A hoist needs controlled torque at zero or low speed plus a brake strategy. A winder needs torque to regulate web tension while diameter changes.

Yael: The mechanical model is force, torque, inertia and speed.

Amir: And time. Torque accelerates inertia. Power is torque multiplied by angular speed. The same torque at higher speed means more power. A move that is easy in two seconds may be impossible in two tenths of a second because acceleration torque and regenerative energy grow sharply.

Yael: Where does the PLC sit?

Amir: For a simple VFD, the PLC may command run and speed while the drive closes the motor current and speed-related loops. In a servo system, the motion controller generates position trajectories and synchronized setpoints, while the servo drive closes fast current, speed and often position loops. Some platforms integrate PLC, motion and safety in one controller; the engineering responsibilities still need to remain visible.

Yael: So the architecture diagram should show who owns enable, speed, torque, position, limits, homing, braking and safe stop.

Amir: Yes. Ambiguous ownership creates dangerous surprises, especially during mode changes, communication loss and restart.

## 06:30-10:30 | Motor families - names are not control strategies

Yael: Most plants still use induction motors. Why are they so dominant?

Amir: They are robust, mature, widely available and well suited to direct-on-line or converter operation. The rotor has no permanent magnets and no electrical connection in a squirrel-cage design. With an appropriate VFD, an induction motor can provide excellent speed and torque performance for a large range of industrial loads.

Yael: What changes with permanent-magnet synchronous motors?

Amir: The rotor field comes from magnets, so rotor losses can be lower and torque density and dynamic response can be attractive. But the drive must know rotor position well enough to control current relative to the magnetic field. At high speed, voltage limits, field weakening and potential demagnetization under abnormal current or temperature matter.

Yael: And synchronous-reluctance motors?

Amir: They produce torque because the rotor prefers to align along a low-reluctance magnetic path. They avoid rotor magnets and can achieve high system efficiency with a matched drive. They are a reminder that “motor efficiency” and “drive compatibility” should be evaluated as a system, not as unrelated components.

Yael: Where does a stepper fit?

Amir: A stepper advances through discrete electromagnetic positions. In open-loop use the controller assumes each commanded step occurred. That is economical and effective when load and acceleration are predictable, but a missed step can remain hidden until a home routine or quality check reveals it. Closed-loop steppers add feedback, yet their torque-speed and resonance behavior still differ from a servo.

Yael: People often call the motor itself a servo.

Amir: The useful engineering definition is broader: a servo system is a closed-loop actuation system designed to make a controlled variable - usually position, speed or torque - follow a command with specified dynamics and accuracy. It includes motor, drive, feedback, control loops and mechanics. A premium motor on a flexible mechanism is not a precise servo axis.

Yael: What about brakes?

Amir: A holding brake is usually for holding a stopped load, not for repeatedly stopping full kinetic energy unless designed for that duty. Brake release and application must be coordinated with torque production and verified feedback, particularly on vertical axes.

## 10:30-14:30 | Torque-speed demand and sizing

Yael: How do we size correctly without drowning in formulas?

Amir: Start with the load profile over time. For each phase - accelerate, run, decelerate, dwell and hold - estimate speed, load torque and acceleration torque. Acceleration torque depends on total inertia reflected to the motor shaft. A gearbox changes both torque and reflected inertia, approximately by the square of the ratio, while adding efficiency losses and backlash.

Yael: Then compare peak and continuous values?

Amir: Yes. Peak torque must cover the worst short event with margin, while root-mean-square torque over the duty cycle must stay within motor thermal capability. The drive must supply the required current and overload duration. The motor speed must remain inside its mechanical and electrical limits, including any field-weakening region.

Yael: Why is nameplate power misleading for positioning?

Amir: Because power can look modest while peak torque is high at low speed. Conversely, a spindle may need high power at high speed but modest torque. Sizing from average power can miss acceleration current, while sizing only from peak torque can produce an oversized motor with excessive inertia that makes the axis harder to control.

Yael: That sounds counterintuitive: a larger motor can make the motion worse.

Amir: Certainly. Larger rotor inertia increases the energy to accelerate and brake. It can worsen the inertia ratio and require a larger drive and braking system. The best selection balances torque margin, thermal capacity, inertia, speed range, mechanical fit and lifecycle availability.

Yael: What environmental questions belong in the selection?

Amir: Ambient temperature, altitude, enclosure, contamination, washdown, hazardous area classification, vibration, mounting, bearing load, cable length and cooling. At low speed, a shaft-mounted fan moves less air, so a continuously high-torque motor may require independent ventilation or derating.

Yael: For our indexer we therefore need the tray mass, belt and pulley inertia, gearbox ratio, friction, move time and dwell, not only the motor label.

Amir: Correct, plus the actual motion profile and whether the load can drive the motor during deceleration.

## 14:30-19:00 | VFD control modes

Yael: What does a basic VFD actually control?

Amir: It rectifies or otherwise converts incoming power to a DC link and synthesizes motor voltage with semiconductor switching. By controlling output frequency and voltage - and in advanced modes, current components - it controls motor flux and torque.

Yael: Start with scalar volts-per-hertz control.

Amir: It maintains an approximate voltage-to-frequency relationship to preserve motor flux. It is simple and robust for many pumps, fans and conveyors. But it does not explicitly decouple torque and flux, and speed changes with slip and load. Low-speed torque and fast dynamics are limited unless compensation is added.

Yael: Sensorless vector sounds like a servo without encoder.

Amir: That description is too generous. Sensorless vector control uses motor models and measured electrical quantities to estimate flux, speed or rotor position sufficiently for improved torque control. It can perform very well, but estimation becomes harder near zero speed and under rapidly changing or poorly identified conditions. The requirement must decide whether the remaining uncertainty is acceptable.

Yael: Closed-loop vector control adds encoder feedback.

Amir: Yes. Feedback improves actual speed and rotor-position knowledge, allowing accurate low-speed torque and faster response. But the encoder, cable, mounting, scaling and feedback plausibility become part of the reliability and safety story.

Yael: And torque mode?

Amir: In torque mode, the drive regulates torque-producing current to follow a torque command, within speed and current limits. It is useful for tension, winding, load sharing and some force-control tasks. The machine controller must still prevent unintended acceleration because a free load under torque command can continue to speed up.

Yael: What does auto-tune do?

Amir: It identifies electrical motor parameters, and sometimes mechanical characteristics, to improve the internal model and loop settings. It is not magic. The correct motor data, safe test conditions, connected load state and chosen tune method matter. Replacing the motor without updating parameters can degrade performance or protection.

Yael: So a control-mode selection should be written as a requirement: speed accuracy, zero-speed torque, dynamic response, encoder tolerance and failure behavior.

Amir: Exactly. Do not choose vector control because the menu sounds advanced. Choose it because the load needs what it provides.

## 19:00-23:00 | The drive, motor and cable are one electromagnetic system

Yael: Why can a motor that runs perfectly from the mains fail when connected to a drive?

Amir: Because a PWM drive does not present a pure sine wave at the motor terminals. Fast voltage edges interact with cable impedance and motor insulation. Long cables can create reflected-wave peaks. Common-mode voltage can drive currents through bearings and grounding paths. Switching creates conducted and radiated electromagnetic interference.

Yael: What are the practical mitigations?

Amir: Use a motor suitable for converter duty and the actual voltage and cable conditions. Follow manufacturer limits for cable length and switching frequency. Use appropriate shielded motor cable and correct shield termination. Consider output reactors, dv/dt filters or sine filters where required. Address bearing currents with insulated bearings, shaft grounding or common-mode mitigation based on the machine design.

Yael: Can we solve EMC by grounding the shield at one end?

Amir: That rule is often misapplied. For high-frequency drive currents, low-impedance bonding and circumferential shield termination are commonly important. The correct arrangement depends on the EMC design, equipotential bonding and manufacturer instructions. Signal-cable shielding practices are not automatically the same as motor-cable practices.

Yael: What about input-side effects?

Amir: The rectifier and DC link draw non-sinusoidal current, producing harmonics and affecting power quality. Line reactors, DC chokes, multipulse or active front ends may be used depending on the installation. Protection, short-circuit rating, leakage current, residual-current devices and disconnecting means must be coordinated with the drive documentation and applicable electrical standards.

Yael: And thermal issues?

Amir: Drive losses depend on load, switching, ambient and enclosure cooling. Motor losses change under converter supply. Low-speed self-cooling may be poor. A motor temperature sensor and drive thermal model are useful, but their assumptions and reset behavior must be understood.

Yael: This explains why replacing a two-metre cable with forty metres is an engineering change.

Amir: Yes. So is raising switching frequency to make the motor quieter. Acoustic improvement can increase drive loss, motor stress and EMC burden.

## 23:00-28:00 | Servo architecture and nested loops

Yael: Let us open the servo block diagram.

Amir: At the inside is a current or torque loop, typically the fastest. Outside it is a speed loop. Outside that may be a position loop. The motion controller provides a trajectory that defines where the axis should be at each instant, not merely the final destination.

Yael: Why nested loops?

Amir: The inner loop must respond faster than the outer loop it supports. The torque loop makes electrical current follow quickly. The speed loop uses torque to correct velocity error. The position loop uses velocity to correct position error. If bandwidths are poorly separated or mechanics resonate, aggressive gains amplify noise and vibration rather than improving accuracy.

Yael: What is following error?

Amir: The difference between commanded and actual position. It is a valuable diagnostic, but it must be interpreted with the trajectory. Some following error during acceleration is expected. Excessive, asymmetric or growing error can indicate torque saturation, friction, incorrect feed-forward, feedback problems, compliance or mechanical obstruction.

Yael: Feed-forward sounds like cheating.

Amir: It is prediction, not cheating. Velocity feed-forward supplies the command expected to produce the requested speed; acceleration feed-forward supplies torque expected for inertia. Feedback then corrects model errors and disturbances. Good feed-forward reduces error without requiring dangerously high feedback gain.

Yael: Does a higher-resolution encoder always improve positioning?

Amir: It improves measurement granularity, but machine accuracy also depends on encoder placement, mechanical transmission, thermal growth, backlash, compliance, calibration and load-side disturbances. A motor encoder cannot directly see belt slip or gearbox lost motion. A load-side encoder can close that gap, but dual-loop control needs careful tuning.

Yael: And absolute versus incremental feedback?

Amir: Incremental encoders measure change and usually need a reference after power loss. Absolute encoders retain or communicate position within their defined range. Neither eliminates the need to define machine zero, safe travel limits and plausibility checks.

Yael: What should a commissioning engineer trend?

Amir: Commanded and actual position, velocity and torque; following error; current limit status; DC-bus voltage; brake state; encoder status; and the machine event timeline. Without synchronized data, people tune by sound and memory.

## 28:00-32:00 | Motion profiles, jerk and mechanics

Yael: Our indexer could move with a trapezoidal velocity profile: constant acceleration, constant speed, constant deceleration.

Amir: Yes, but instantaneous changes in acceleration create infinite mathematical jerk and real mechanical shock. An S-curve profile limits jerk by ramping acceleration. That can reduce vibration, belt excitation, product movement and peak torque, though it may lengthen the move or require a different peak velocity.

Yael: So “same distance and same time” does not imply the same load.

Amir: Correct. Profile shape changes peak acceleration, torque, settling and regenerative power. Mechanical natural frequencies also matter. If the command excites a resonance, the axis can oscillate after the motor has nominally arrived.

Yael: Where does backlash enter?

Amir: Backlash creates a range in which motor movement does not move the load when torque reverses. Compensation can improve commanded positioning in repeatable conditions, but it cannot restore stiffness or eliminate impact. Mechanical correction is often the better control strategy.

Yael: What about compliance?

Amir: Belts, long shafts, couplings and frames behave like springs. The motor and load can form a two-mass resonant system. Notch filters and tuning tools help, but first verify mechanical integrity, preload, alignment and mounting stiffness.

Yael: Homing is also more than moving until a switch changes state.

Amir: Yes. A homing procedure defines approach direction, speed stages, switch edge, encoder index if used, offset, timeout and failure response. Repeatability depends on sensor mechanics and direction. Safety limits and normal home sensors have different responsibilities.

Yael: For a vertical axis, the profile also interacts with gravity and brake timing.

Amir: Exactly. Upward and downward torque differ. On stop, the drive should establish holding torque before releasing the brake, and confirm conditions before removing torque. A brake output bit alone is not proof that the load is secured.

## 32:00-36:00 | Coordinated motion and software ownership

Yael: When do we leave single-axis control and enter motion control as a software discipline?

Amir: When axes must share a time base or geometric relationship. Electronic gearing makes one axis follow another by ratio. Electronic camming maps master position to follower position through a curve. Interpolation coordinates axes to follow a path. Registration adjusts motion to a product mark or measured event.

Yael: What makes the network important?

Amir: Distributed drives need cyclic setpoints and feedback with bounded timing. Clock synchronization, update period, jitter and loss behavior influence coordination. A fast average network is not enough if delivery time varies unpredictably.

Yael: PLCopen Motion Control gives common function-block concepts.

Amir: Yes: axis state machines and blocks for power, move, stop, home, gearing and coordinated functions. It improves conceptual portability, but implementation details, error codes and real-time behavior still differ between platforms. Engineers must understand the state machine rather than copy blocks mechanically.

Yael: How should machine logic interact with motion?

Amir: Use explicit states and ownership. A sequence requests a move; the motion layer validates prerequisites, executes and reports done, busy, aborted or error. Safety can remove torque or impose safe limits. Manual mode needs defined speed, direction and hold-to-run behavior. Recovery must not silently resume a move after an interruption.

Yael: And recipe data?

Amir: Units, limits, version and validation matter. A distance in millimetres must not be interpreted as revolutions because a gearbox parameter changed. Motion configuration belongs under change control, backup and restoration testing.

Yael: This is where a drive replacement becomes a software change.

Amir: Often yes. Parameter sets, motor identification, encoder scaling, safety signatures and network mappings all need controlled commissioning evidence.

## 36:00-39:30 | Safe motion is more than stopping power

Yael: Let us clarify Safe Torque Off.

Amir: STO prevents the drive from producing torque through the motor, within its specified safety architecture. It does not necessarily stop a moving load, hold a vertical load, disconnect electrical power or eliminate stored DC-bus energy. The machine risk assessment determines what additional functions and mechanical measures are required.

Yael: Then what is Safe Stop 1?

Amir: SS1 initiates and monitors a controlled deceleration, followed by STO according to the implemented variant. Safe Stop 2 performs a controlled stop followed by a safe operating stop, commonly associated with SOS, where position is safely monitored while torque remains available.

Yael: And Safely Limited Speed?

Amir: SLS monitors that speed remains below a safe limit, useful for setup or intervention modes when combined with guards, enabling devices and a validated risk-reduction concept. Other functions include safe direction, safe maximum speed, safe brake control and safe position-related functions, depending on the drive.

Yael: Does integrated safety reduce wiring?

Amir: It can reduce external components and enable more productive protective modes, but validation responsibility remains. Feedback architecture, fault exclusions, stopping time, brake performance, communication safety and restart behavior must be verified in the complete machine.

Yael: How do stop categories relate?

Amir: Electrical equipment standards describe stop categories such as immediate removal of power, controlled stop followed by power removal, and controlled stop with power retained. Drive safety functions provide tools to implement risk-based behavior; the names must not be used as substitutes for the machine-level stop strategy.

Yael: And maintenance isolation?

Amir: STO is not lockout. Electrical isolation, verification of absence of voltage, dissipation of stored energy and control of gravity or pressure follow the maintenance procedure and applicable law.

## 39:30-42:00 | Energy, diagnostics and commissioning evidence

Yael: Drives are often sold as energy-saving devices. When is that true?

Amir: For variable-torque loads such as many centrifugal pumps and fans, reducing speed can greatly reduce required power, although the real system curve, static head, efficiency and operating constraints must be considered. For constant-torque loads, speed reduction does not create the same cubic saving. A poorly selected drive can also add losses or move the process away from its efficient point.

Yael: Efficiency classes now include IE5 for line-operated motors in IEC 60034-30-1:2025.

Amir: Correct, but project decisions should examine the complete motor system and operating profile. IEC 61800-9-2 provides system-level methods for drive and motor efficiency. Energy during braking is another design choice: dissipate it in a resistor, share it on a DC bus or regenerate it.

Yael: What does a good commissioning baseline contain?

Amir: Motor and drive identification, nameplate data, parameter backup, autotune result, cable and filter configuration, current and thermal limits, direction and feedback polarity, low-speed and no-load checks, loaded cycle trends, stopping time, braking temperature, safety validation and a known-good fault log.

Yael: Which drive values are most useful during operation?

Amir: Actual speed, torque-producing current, total current, DC-bus voltage, temperature estimate, overload utilization, encoder quality, following error, current limiting, braking status and fault history with timestamps. Trend them with process variables and mechanical events.

Yael: So predictive maintenance should not begin with artificial intelligence.

Amir: It should begin with trustworthy signals and failure hypotheses. Rising torque at the same speed may indicate friction or load change. Increasing following error in one direction may indicate backlash or alignment. More overvoltage events may indicate a changed deceleration profile or braking path. Data becomes useful when linked to physics.

## 42:00-45:00 | Resolve the indexing fault and close

Yael: Back to the conveyor. What is the disciplined troubleshooting sequence?

Amir: First, freeze uncontrolled tuning changes and back up the drive and motion configuration. Second, trend commanded and actual motor position, load position if available, speed, torque, current, following error and DC-bus voltage on the same clock. Third, inspect mechanics: belt tension, pulley key, gearbox backlash, coupling, frame stiffness and tray slip.

Yael: Suppose motor following error is small, but the load encoder shows the two-millimetre overshoot.

Amir: Then increasing position gain at the motor can make the impact worse. The load is moving relative to the motor - perhaps belt compliance, slip or backlash. Correct the mechanics or use a justified load-feedback architecture.

Yael: And the DC-bus trip?

Amir: Compare the trip with deceleration and regenerated power. Verify actual inertia and move profile, braking resistor value, wiring, duty and thermal switch; confirm the braking chopper is enabled and compatible. If the machine frequently regenerates, evaluate a larger braking solution, shared bus or regenerative drive. Do not simply lengthen deceleration without checking cycle-time and safety consequences.

Yael: In our case, the trend shows a very sharp trapezoidal deceleration, the braking resistor parameter is set to the default even though a different resistor was installed, and the belt tensioner has excessive compliance.

Amir: Then the repair is systemic: correct and validate the resistor configuration, redesign the profile with a jerk-limited deceleration inside process and stopping constraints, repair the tensioner, retune after the mechanics are stable, and record the new baseline. A larger motor would have increased inertia; higher gain would have hidden nothing.

Yael: The final checklist is: requirement, load model, torque-speed duty, motor technology, drive current and regeneration, feedback location, mechanics, motion profile, EMC, cooling, safety, diagnostics and controlled commissioning.

Amir: Exactly. Motion control is where electrical, mechanical and software models meet. The system performs only as well as the weakest model.

Yael: In the next episode we follow the setpoint and feedback across the network: industrial Ethernet, fieldbus, deterministic timing, topology and what happens when communication is late rather than completely lost.

Amir: Until then, never tune a control loop to compensate for a loose machine.

# 8. Producer and host notes

- Keep torque, speed, position and process effect distinct throughout.

- Do not imply that servo always means more accurate; mechanics and feedback placement set the achievable result.

- Explain regenerative energy without suggesting one universal braking solution.

- Present V/f, vector and servo as requirement-driven choices, not a maturity ladder.

- Make the STO boundary explicit every time it is mentioned.

- Do not read standard numbers in the main dialogue except the two energy-efficiency examples near the end.

- Keep the final diagnosis hidden until the final segment.

# 9. Engineering motor-and-motion checklist

1. What physical motion or process effect is required, and with what accuracy, repeatability and cycle time?

1. What are the complete load torque, speed, inertia, friction, gravity and disturbance profiles?

1. What continuous and peak torque/current are required, for how long and at what ambient conditions?

1. What motor technology, cooling, enclosure, brake and bearing arrangement fit the application?

1. Which control mode is required: scalar speed, vector speed/torque, position servo or coordinated motion?

1. Where is feedback measured, and what mechanical errors remain outside the feedback loop?

1. What motion profile, jerk, settling time and resonance limits are acceptable?

1. Where does regenerated energy go during every stopping and overhauling condition?

1. Are the motor, drive, cable, filter, grounding and EMC design compatible as one system?

1. What happens on loss of command, network, encoder, power, brake feedback or cooling?

1. Which safe motion functions are required, and how are stopping time and holding validated?

1. How are parameters, autotune results, safety signatures and backups controlled?

1. Which synchronized trends and acceptance tests prove performance before release?

1. What changes trigger revalidation: motor, cable, gearbox, profile, firmware, resistor, encoder or load?

# 10. Glossary

| Term | Meaning in this episode |
| --- | --- |
| VFD / variable-frequency drive | Power electronic drive that controls motor operation by varying electrical output, commonly frequency, voltage and current. |
| Power drive system (PDS) | Drive module, control/protection, motor and defined interfaces considered as a system. |
| Scalar V/f control | Control based mainly on voltage-to-frequency relationship rather than explicit torque/flux decoupling. |
| Vector control | Control that regulates current components associated with motor flux and torque using a motor model and optionally feedback. |
| Servo system | Closed-loop motor-drive-feedback-mechanics system designed for specified dynamic tracking of position, speed or torque. |
| Continuous torque | Torque sustainable thermally for the specified operating conditions. |
| Peak torque | Higher torque available for a limited duration within motor and drive constraints. |
| Reflected inertia | Load inertia transformed through the transmission to the motor shaft. |
| Following error | Difference between commanded and measured position. |
| Jerk | Rate of change of acceleration. |
| Regeneration | Energy flow from the mechanical load back toward the drive DC bus or supply. |
| STO | Safety function that prevents torque production; not an electrical isolating function. |
| SS1 | Safety function that performs a controlled deceleration followed by a torque-off state. |
| SLS | Safety function that monitors speed against a safe limit. |
| PWM | Pulse-width modulation used by the drive to synthesize controlled motor voltage/current. |

# 11. Standards and source map

> Use note<br>For every project, verify the standard edition adopted by contract, jurisdiction, sector and manufacturer, including amendments and national deviations.

1. IEC 60034-1:2026 - Rotating electrical machines: rating and performance. Official: https://webstore.iec.ch/en/publication/89961

2. IEC 60034-30-1:2025 - Efficiency classes of line-operated AC motors; edition introduces IE5 nominal limits. Official: https://webstore.iec.ch/en/publication/91195

3. IEC 60034-2-3:2024 - Test methods for determining losses and efficiency of converter-fed AC motors. Official: https://webstore.iec.ch/en/publication/67758

4. IEC TS 60034-25:2022 - AC electrical machines used in power drive systems; converter duty, shaft currents and derating guidance. Official: https://webstore.iec.ch/en/publication/66456

5. IEC 61800-2:2021 - Rating specifications for low-voltage adjustable-speed AC power drive systems. Official: https://webstore.iec.ch/en/publication/62105

6. IEC 61800-3:2022/COR1:2025 - EMC requirements and test methods for power drive systems and machine tools. Official: https://webstore.iec.ch/en/publication/65056

7. IEC 61800-5-1:2022 with corrigenda - Electrical, thermal, fire, mechanical and energy safety of power drive systems. Official: https://webstore.iec.ch/en/publication/62103

8. IEC 61800-5-2:2016 - Functional-safety requirements and recommendations for safety-related power drive systems. Official: https://webstore.iec.ch/en/publication/24556

9. IEC 61800-5-3:2021 - Functional, electrical and environmental requirements for safety-related encoders. Official: https://webstore.iec.ch/en/publication/28614

10. IEC 61800-7-1:2015 and related parts - Generic interfaces, drive profiles and network mappings. Official: https://webstore.iec.ch/en/publication/23757

11. IEC 61800-9-2:2023+A1:2025 - Energy-efficiency determination and classification for motor systems. Official: https://webstore.iec.ch/en/publication/111276

12. IEC 60204-1:2016+A1:2021 - Electrical equipment of machines and machine stop/control requirements. Official: https://webstore.iec.ch/en/publication/71256

13. ISO 13849-1:2023 - Design and integration of safety-related parts of machinery control systems. Official: https://www.iso.org/standard/73481.html

14. IEC 62061:2021+A1:2024+A2:2026 - Functional safety of safety-related machinery control systems. Official amendment page: https://webstore.iec.ch/en/publication/92835

15. PLCopen Motion Control - Axis state model and function-block specifications for single and coordinated motion. Official: https://www.plcopen.org/standards/motion-control/

# 12. Episode quality gate

- The listener can draw the complete requirement-to-motion chain.

- Speed, torque, position and process effect are not treated as synonyms.

- Motor and drive sizing includes inertia, duty, thermal and regenerative energy.

- PWM, cable, motor and grounding are treated as an integrated electromagnetic system.

- Servo accuracy is bounded by mechanics and feedback placement.

- Safe motion functions are presented within machine-level risk assessment and validation.

- The closing diagnosis resolves both the positioning and DC-bus symptoms.

- The ending creates a clean bridge to deterministic industrial communication.
