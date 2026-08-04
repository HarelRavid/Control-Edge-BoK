---
episode: 1
language: en
title: "From Physics to Software - An Introduction to Machine and Industrial Control"
target_duration: "35-42 minutes"
status: completed
extracted_from: docx
---

CONTROL EDGE

> EPISODE 1<br>From Physics to Software<br>An Introduction to Machine and Industrial Control

| Audience | Mechanical, process and manufacturing engineers; automation integrators |
| --- | --- |
| Target duration | 38-42 minutes |
| Format | Dialogue between Yael, a young mechanical engineer, and Amir, a senior process and controls engineer |
| Deliverable | Full script, NotebookLM direction, concept map, glossary and references |
| Version | 1.0 \| August 2026 |

Educational material. It does not replace engineering design, risk assessment, manufacturer instructions, or the contractually applicable editions of relevant standards.

# 1. Pre-production alignment check

> Master-plan check<br>This episode remains introductory and establishes vocabulary for Episodes 2-20. It deliberately explains the whole control chain without attempting to teach PLC programming, network selection, PID tuning or HMI design in depth. Those topics are previewed and reserved for later episodes.

- Audience remains mechanical and process engineers, not only automation specialists.

- The episode links physical design choices to control behaviour and software architecture.

- Standards are introduced as frameworks and signposts, not quoted as project-specific legal requirements.

- The worked example is a process skid so that the machine and process perspectives meet in one system.

- Target delivery is a two-host conversation suitable for NotebookLM Audio Overview or a human recording session.

# 2. Episode objectives

- Define industrial control, open-loop control, closed-loop control, sequences, permissives, interlocks and trips.

- Distinguish machine control, process control and supervisory control.

- Map sensors, I/O, controllers, networks, HMI, SCADA, historians, operations systems and enterprise systems.

- Explain why timing, availability, diagnostics and failure behaviour matter as much as nominal functionality.

- Separate basic control, functional safety and industrial cybersecurity.

- Describe the engineering lifecycle from requirements through FAT, SAT, commissioning and operational change.

# 3. Timing and segment plan

| Time | Segment | Purpose |
| --- | --- | --- |
| 00:00-02:00 | Cold open: a pressure-control incident | Create urgency and show that control is a physical engineering discipline. |
| 02:00-05:00 | Hosts, audience and series promise | Set expectations and define the two perspectives. |
| 05:00-10:00 | What “control” actually means | Explain command, measurement, decision, action and verification. |
| 10:00-15:00 | Machine, process and supervisory control | Separate discrete, continuous and plant-wide problems. |
| 15:00-22:00 | The automation architecture | Map field devices, controllers, HMI/SCADA, operations and enterprise layers. |
| 22:00-30:00 | Walk-through: an automated process skid | Follow one requirement from sensor to software and final element. |
| 30:00-35:00 | OT versus IT | Explain determinism, availability, lifecycle and change control. |
| 35:00-39:00 | Control, safety and cybersecurity | Clarify three related but distinct engineering responsibilities. |
| 39:00-42:00 | Lifecycle, roles and closing | Connect design, FAT/SAT, commissioning and the next episode. |

# 4. Two maps to keep in mind

## 4.1 The control chain

| Process | → | Sensor | → | Input | → | Logic | → | Output | → | Actuator | → | Process |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

The chain is circular, not linear: the process changes, sensors report the change, the controller decides, an actuator influences the process, and the new process state is measured again.

## 4.2 The automation architecture

| Level | Typical contents | Key question |
| --- | --- | --- |
| 4 - Enterprise | ERP, planning, supply chain and management reporting | What should be produced, when and at what cost? |
| 3 - Site operations | MES/MOM, batch, quality, maintenance and site historians | How is the plant managed across a shift, day and month? |
| 2 - Area supervision | HMI, SCADA, alarm and trend servers, operator stations | What is happening now, and what needs attention? |
| 1 - Basic control | PLC, PAC, DCS controllers, safety controllers and remote I/O | What decision must be executed in the next control cycle? |
| 0 - Physical process | Sensors, valves, motors, pumps, cylinders, material and energy | What is actually happening in the physical world? |

> Architectural caution<br>The levels are a reference model. They do not by themselves create cybersecurity boundaries, guarantee independence or define response time. Each project must document where functions execute, what they depend on and what happens when communication fails.

# 5. NotebookLM production prompt

> Paste-ready instruction<br>Create an English-only podcast episode of 38-42 minutes, grounded exclusively in the uploaded sources and the Episode 1 document. Do not add facts, standard clauses, figures or examples that cannot be supported by the sources.<br><br>Hosts:<br>- Yael: a young mechanical engineer. She is sharp and curious, asks practical questions, and connects control to mechanics, motion, equipment reliability and maintenance.<br>- Amir: a senior process and controls engineer. He explains from industrial experience, distinguishes control, safety and cybersecurity, and avoids presenting vendor preferences as universal truth.<br><br>Conversation rules:<br>1. Approximate speaking split: Amir 55%, Yael 45%.<br>2. Keep turns relatively short: one to four sentences. Avoid long lectures.<br>3. Open with the pressure-rise scenario on a circulation skid, followed by a short theme cue.<br>4. Expand every acronym on first use: PLC, PAC, DCS, HMI, SCADA, OT, IT, PV, SP, I/O, VFD, FAT and SAT.<br>5. Use analogies only when technically accurate, and immediately reconnect each analogy to the engineering term.<br>6. Do not invent clauses from standards. Say “the standard provides a framework” rather than “the standard requires” unless the contractual or regulatory context is explicit in the sources.<br>7. Emphasize that a safe state is derived from risk assessment and is not always stop or close.<br>8. At each topic transition, Yael summarizes her understanding in one sentence and Amir corrects it if needed.<br>9. Use only a few professional stage cues in square brackets: [theme], [pump sound], [short pause].<br>10. Avoid vendor promotion. Company names may appear only as neutral examples supported by sources.<br>11. Close with the seven-question checklist for assessing an unfamiliar system and a teaser for Episode 2 on PLCs and PACs.<br>12. End with an engineer’s note: the content is educational and does not replace engineering design, risk assessment, manufacturer instructions or the applicable edition of any standard.<br><br>Timing structure:<br>00:00-02:00 scenario; 02:00-05:00 introductions; 05:00-10:00 what control means; 10:00-15:00 machine versus process; 15:00-22:00 architecture; 22:00-30:00 worked skid example; 30:00-35:00 OT versus IT; 35:00-39:00 safety and cybersecurity; 39:00-42:00 lifecycle and closing.

# 6. Full episode script

## 00:00-02:00 | Cold open - when pressure rises

[Cold open. Low industrial ambience: a pump, a contactor, and a short alarm tone. Fade under the voices.]

Amir: Imagine a liquid-circulation skid. The operator requests forty litres per minute. The pump starts, the flow rises, and everything looks normal. Then a downstream valve begins to close. Pressure climbs. The pump is still being told to run. The question is not whether the system contains a PLC. The question is whether the system can understand what is happening quickly enough, make the right decision, and move the process to a safe state.

Yael: And that sounds like a controls problem, but also a piping problem, a mechanical problem, a process problem and a safety problem.

Amir: Exactly. Industrial control sits at the point where all of those disciplines meet. Software does not control an abstract diagram. It controls energy, motion, pressure, temperature, chemistry and people’s interaction with equipment.

[Theme sting - five seconds, then clean studio sound.]

## 02:00-05:00 | Who this series is for

Yael: Welcome to Control Edge, a podcast for mechanical and process engineers who want to understand how industrial machines and process systems are actually controlled. I am Yael, a mechanical engineer. I know how to size shafts, select bearings, think about tolerances and read a P&ID - but I want to become fluent in the logic that makes the equipment behave.

Amir: And I am Amir, a process and controls engineer. I came into automation through machines, utilities and process plants, which means I tend to ask two questions: what does the physics want to do, and what must the control system do about it?

Yael: This first episode is our common language. We are not going to teach a specific PLC platform yet, and we are not going to bury the listener in protocol names. We are going to build the mental model that the rest of the series will use.

Amir: By the end, you should be able to look at a machine or a process skid and identify the controlled variables, the sensors, the decision layer, the actuators, the operator interface, the safety layer and the data path. You should also understand why the same architecture can behave very differently depending on timing, failure modes and software quality.

## 05:00-10:00 | What control means

Yael: Let us start with the most basic question. What is control?

Amir: Control is purposeful influence over a physical system. We define a desired condition, observe the actual condition, decide what action is needed, apply that action and verify the result. In its simplest form, that is command, measurement, decision, actuation and feedback.

Yael: So a start button connected directly to a motor contactor is control?

Amir: Yes. It is a very simple open-loop control action. The operator gives a command and the motor receives power, but the system may not know whether the motor actually rotated, whether the conveyor moved, or whether the load jammed. Open-loop control can be perfectly valid when the consequence of uncertainty is low and the physical behaviour is predictable.

Yael: Closed-loop control adds measurement.

Amir: Measurement and correction. Suppose we want a vessel at sixty degrees Celsius. A temperature sensor measures the process variable, usually abbreviated PV. The operator or recipe provides a setpoint, SP. The controller compares PV with SP, calculates an error and changes a manipulated variable - perhaps heater power or a steam-valve position. The loop repeats continuously.

Yael: That sounds like PID, which we will cover later.

Amir: PID is one common way to calculate the correction, but closed-loop control is the broader concept. A position servo, a pressure regulator, a speed controller and a camera-guided robot all close loops. Some loops run every few milliseconds. Others act over minutes or hours.

Yael: And not every decision is continuous. A machine often asks yes-or-no questions.

Amir: Right. Industrial control includes continuous regulation, discrete logic and sequences. A permissive is a condition that must be true before an action is allowed. An interlock prevents or stops an action when conditions are incompatible. A trip drives the system to a defined protective state. A sequence or state machine coordinates steps: clamp the part, confirm position, start the spindle, feed, retract, unclamp.

Yael: I want to pause on the word “defined.” Engineers often say “fail safe,” but safe is not the same for every device.

## 10:00-15:00 | Machine control, process control and supervisory control

Amir: That is a critical observation. For one valve, loss of power should close it. For another, closing it could trap thermal expansion and create a pressure hazard, so the safer state may be open or hold-last-position. A vertical axis may need a brake. A mixer may need to stop, while a cooling pump may need to continue. Safe state comes from hazard analysis and process understanding, not from a universal rule.

Yael: Now separate machine control from process control.

Amir: Machine control is often dominated by discrete events, motion and short cycle times: packaging, assembly, presses, conveyors, robots and machine tools. The logic cares about states, positions, timing, coordination and repeatability. Process control is often dominated by continuous variables and material or energy balances: flow, level, pressure, temperature, concentration, pH and composition.

Yael: But the distinction is not clean.

Amir: Not at all. A filling machine has servo motion and a flow-control problem. A chemical skid has valves, pumps and sequential steps. A battery line has recipes, temperature loops, robots and quality data. Modern systems are hybrid, so the engineer must understand both worlds.

Yael: Where does supervisory control fit?

Amir: Supervisory control sits above the immediate loop. It selects operating modes, coordinates units, manages recipes, displays trends, handles alarms, records history and may optimize setpoints. A local controller should normally keep essential control running even if the supervisory screen or business network is unavailable.

Yael: That sentence contains an architectural principle: do not make a fast or safety-critical function depend unnecessarily on a higher, slower or less reliable layer.

## 15:00-22:00 | The industrial control architecture

Amir: Exactly. Put the decision where the required response time, availability and failure containment can be achieved.

Yael: Let us map those layers from the physical process upward.

Amir: At the bottom is the process itself: material, motion and energy. Sensors convert physical conditions into information. Actuators convert commands into physical action. Between them are signal conditioning and I/O modules. Above the I/O is the controller: a PLC, PAC, DCS controller, industrial PC or embedded controller, depending on the application.

Yael: Then the operator interface.

Amir: Yes. HMI is the local or system-level human-machine interface. SCADA is a supervisory platform that can collect data from many controllers or remote sites. Historians store time-series data. Manufacturing-operations systems manage production context such as batches, genealogy, quality and work orders. Enterprise systems deal with planning, purchasing, inventory and finance.

Yael: People often call this the automation pyramid or the Purdue model.

Amir: Those are useful reference models, but they are not laws of nature. ISA-95 and IEC 62264 formalize interfaces between enterprise and manufacturing-control activities. The Purdue-style levels are also widely used when discussing OT architecture and cybersecurity. Real systems may flatten, virtualize or distribute functions, but the questions remain: who owns the data, where does the decision execute, what happens if a link fails, and how is trust separated?

Yael: Let us go component by component, but from the viewpoint of an engineer selecting and integrating the system.

Amir: Start with sensors. A sensor is not simply “a value.” It has a measuring principle, range, accuracy, repeatability, response time, drift, environmental limits and failure behaviour. A pressure transmitter may output four-to-twenty milliamps, a temperature element may be an RTD or thermocouple, an encoder may produce pulses or a digital position word, and a smart instrument may communicate diagnostics over a field protocol.

Yael: The control program must know what the signal means.

Amir: Correct. Raw counts from an analog input card must be scaled into engineering units. The software should detect underrange, overrange, broken wire, stale data or implausible rate of change where appropriate. A value of zero can mean zero process, loss of power or a failed sensor. Context matters.

Yael: Then I/O.

## 22:00-30:00 | Worked example - a circulation and temperature-control skid

Amir: I/O is the boundary between controller logic and field wiring. Digital input reads states. Digital output switches devices. Analog input measures continuous signals. Analog output commands a continuous value. High-speed counters, motion interfaces, safety I/O, thermocouple modules and distributed remote I/O exist because not all signals have the same timing, isolation or diagnostic needs.

Yael: What does the controller actually do each cycle?

Amir: A traditional explanation is: read inputs, execute logic, perform communications and diagnostics, then update outputs. Modern controllers may have multiple tasks with different rates, event-driven interrupts, synchronized motion tasks and distributed clocks. The important point is that the program executes under a defined timing model. If the process changes faster than the control system can observe and react, the design is wrong even if the logic looks correct on screen.

Yael: And actuators are where software becomes force.

Amir: Exactly. Relays and contactors switch power. Variable-frequency drives control motor speed and torque. Servo drives close fast position and velocity loops. Solenoid valves route pneumatic or hydraulic energy. Control valves regulate flow. Electric cylinders, heaters, brakes and robotic axes all have different command interfaces and different stored-energy hazards.

Yael: What about communication networks?

Amir: They carry cyclic I/O, motion synchronization, diagnostics, configuration and supervisory data. Some applications need deterministic timing and bounded latency. Others mainly need interoperability and data modelling. In later episodes we will compare serial fieldbuses, industrial Ethernet, OPC UA and publish-subscribe approaches. For now, remember that a network is part of the control loop whenever the loop depends on it.

Yael: And the HMI is not decoration.

Amir: Correct. It is an operational instrument. A good HMI helps the operator perceive state, detect abnormal conditions, understand cause and take the correct action. A bad HMI can hide degradation behind animation, flood the operator with alarms or allow commands without enough context. ISA-101 and the ISA-18.2 alarm-management framework will be central later in the series.

Yael: Let us make this concrete with one system.

Amir: Consider a skid that circulates a heated liquid through a process module. The engineering requirement says: maintain flow between thirty-eight and forty-two litres per minute; keep supply temperature at thirty-five degrees Celsius; prevent pump operation with insufficient tank level; protect the equipment against high discharge pressure; and provide local and remote operation.

Yael: First, translate the requirement into controlled and monitored variables.

Amir: The main controlled variables are flow and temperature. Monitored variables include suction pressure, discharge pressure, tank level, motor current, valve position and perhaps conductivity or concentration. Each measurement needs a tag, units, range, normal band, alarm limits, quality status and sampling expectation.

Yael: For flow, we could manipulate pump speed with a VFD or a control valve.

Amir: Yes, and that is a process-design choice as much as a controls choice. Pump-speed control may save energy and reduce throttling, but the pump must remain within its allowable operating region. Valve control may provide a different dynamic response. The piping curve, minimum flow, cavitation margin and valve authority affect the control strategy.

Yael: Suppose we choose pump speed. The flow transmitter sends four-to-twenty milliamps to an analog input. The PLC scales it, compares it with the setpoint and sends a speed command to the VFD.

Amir: Good. Then add mode management. In automatic mode, the loop calculates speed. In manual mode, an authorized operator may command speed directly within limits. During startup, the sequence may hold a minimum speed until flow is proven. During shutdown, it may ramp down to avoid hydraulic shock. Mode transitions should be bumpless where practical, so the output does not jump unexpectedly.

Yael: Now the permissives.

## 30:00-35:00 | Operational technology versus information technology

Amir: The pump-start permissive might require: emergency stop healthy, safety circuit reset, adequate tank level, suction valve confirmed open, no high-high discharge pressure trip active, VFD ready, motor protection healthy and the selected route aligned. The exact list comes from the P&ID, cause-and-effect analysis, vendor data and risk assessment.

Yael: What happens if the level transmitter fails?

Amir: That depends on the failure-detection design. A separate low-low level switch may provide an independent protective input. The analog transmitter may provide process control and alarm information, while the switch protects the pump. Independence, diagnostics and proof testing become more important as the required risk reduction increases.

Yael: What about high discharge pressure?

Amir: There may be several layers. The normal flow controller should avoid excessive demand. A high-pressure alarm warns the operator. A high-high pressure trip may stop the pump or open a bypass. Mechanical relief may protect against blocked-in pressure independently of software. Control is one layer; protection is another.

Yael: And temperature?

Amir: A temperature loop may command a cooling valve, heater output or chiller setpoint. The control engineer must account for process delay. If the sensor is far downstream, the loop sees the effect late. Aggressive tuning can create oscillation. Sensor location is therefore a control-design decision, not only an instrumentation detail.

Yael: Now the HMI. What should the operator see?

## 35:00-39:00 | Basic control, functional safety and cybersecurity

Amir: At overview level: operating mode, running status, flow, temperature, tank level, pressure and any active abnormal condition. At detail level: permissive status, valve feedback, motor current, controller mode and output, alarm history and trends. The display should show whether a value is good, bad, stale, substituted or forced. It should not present a failed instrument as a trustworthy number.

Yael: And every event becomes data.

Amir: Potentially, but data has cost and meaning. Fast control data may be sampled every few milliseconds inside the controller, while the historian stores a compressed or periodic record. Events and alarms need timestamps. Engineering changes need version records. A useful data architecture preserves enough context to answer: what happened, in what order, under which software version and operating mode?

Yael: This example also shows why naming and documentation matter.

Amir: Yes. A tag such as FT-101 may identify the field transmitter. The control module may have a structured software name. The HMI label must be understandable to operators. The historian and maintenance system should map to the same asset. Inconsistent naming creates hidden integration work and makes troubleshooting slower.

Yael: Now OT versus IT. Both use processors, networks, operating systems and databases. Why is OT treated differently?

Amir: Because the primary consequence is different. In IT, confidentiality and data integrity are often dominant. In OT, availability, predictable timing, physical safety and process integrity may dominate. That does not make confidentiality unimportant; it means priorities must be balanced against physical consequences.

## 39:00-42:00 | Lifecycle, checklist and closing

Yael: A software update that is routine on an office laptop can be a production event in a plant.

Amir: Exactly. An OT asset may operate for fifteen or twenty years, have a narrow approved configuration and require a shutdown window for change. A patch can affect drivers, timing, vendor support or validated behaviour. Good OT cybersecurity therefore includes asset inventory, network segmentation, tested backups, controlled remote access, change management, recovery planning and compensating controls when immediate patching is not possible.

Yael: And determinism?

Amir: Determinism means that the timing behaviour is sufficiently predictable for the application. Average speed is not enough. A motion system may need synchronized updates with tightly bounded jitter. A temperature trend can tolerate much slower communication. Architecture should be based on required response time, not on the fact that everything has an Ethernet connector.

Yael: There is also the human issue. In IT, rebooting may be inconvenient. In OT, rebooting the wrong controller can stop cooling, ventilation or material handling.

Amir: Correct. Operational context must be part of every change. That is why controls, operations, maintenance, process safety and cybersecurity teams need shared procedures rather than independent assumptions.

Yael: Let us separate control, functional safety and cybersecurity, because people mix them together.

Amir: The basic control system makes the process perform its intended function. Functional safety reduces risk when the basic system or process deviates dangerously. Cybersecurity protects the system against intentional and unintentional compromise of its electronic functions. They interact, but one does not automatically satisfy the others.

Yael: For machinery, we will later discuss ISO 13849 and IEC 62061. For process industries, IEC 61511 builds on IEC 61508.

Amir: And for industrial automation cybersecurity, the ISA/IEC 62443 series provides lifecycle, organizational, system and component requirements. The practical lesson today is separation of responsibilities and explicit interfaces. A safety function needs defined sensors, logic solver and final elements, plus validation and lifecycle management. A cyber firewall is not a safety instrument. A standard PLC alarm is not necessarily an independent safety function.

Yael: But a cyber event can create a safety demand.

Amir: Yes. That is why modern engineering must consider security-informed safety and safety-informed security. If a remote account can change a trip setpoint, access control becomes part of protecting the safety lifecycle. If a safety system blocks all diagnostic visibility, incident response may suffer. The disciplines need coordinated design without destroying necessary independence.

Yael: We have described the running system. How does a project get there?

Amir: A disciplined lifecycle begins with requirements. What must the machine or process do? Under what modes? With what capacity, accuracy, response time, environmental conditions and failure response? Then come functional descriptions, I/O lists, cause-and-effect matrices, network architecture, software design, HMI philosophy, alarm philosophy and test plans.

Yael: Then implementation and review.

Amir: Yes. Code should be modular, named consistently, reviewed and version controlled. Hardware and software are tested during FAT - factory acceptance testing - using simulations or test rigs. On site, SAT and commissioning verify real wiring, instruments, rotation, valve action, communications, sequences, interlocks, alarms and operator procedures.

Yael: And commissioning is not the end.

Amir: Correct. The system enters an operational lifecycle: backups, calibration, proof tests, cybersecurity maintenance, management of change, incident learning and controlled upgrades. The best design is not merely one that starts successfully. It is one that can be understood, maintained and modified safely years later.

Yael: That sounds like a good definition of professional control engineering.

Amir: It is multidisciplinary engineering under time and consequence constraints. It requires physics, software, electrical design, instrumentation, human factors, safety and operational judgement.

Yael: Let us close with a checklist. When I stand in front of an unfamiliar machine, what should I ask?

Amir: Ask seven questions. One: what physical outcome is required? Two: what variables describe the state? Three: how are those variables measured and how can the measurements fail? Four: what actuators can change the state and what energy do they control? Five: where does each decision execute and how fast must it respond? Six: what does the operator need to know and do? Seven: what independent layers manage hazards and cyber risk?

Yael: And in the next episode, we open the controller cabinet.

Amir: We will examine PLCs and PACs: hardware architecture, scan cycles, tasks, memory, local and remote I/O, redundancy, engineering environments and the first look at IEC 61131-3 programming languages.

Yael: Until then, remember: software does not control pixels. It controls physics.

Amir: And good control begins by understanding both. Thanks for listening to Control Edge.

[Theme music up, then fade out.]

# 7. Producer and host notes

- Keep the overall pace calm and technically confident. Allow short pauses after the safe-state example and the separation of control, safety and cybersecurity.

- Pronounce acronyms in full the first time, then use the acronym consistently.

- Do not read the architecture table as a list. Use it as a conversational map and return to the worked skid example.

- Avoid saying that every plant uses exactly five levels or that every alarm is a safety function.

- When describing the example, stress that setpoints, trip values and permissives are illustrative, not design recommendations.

- Estimated spoken word count includes pauses and cues. Human recording may vary by approximately five minutes.

# 8. Technical glossary

| Term | Meaning in this episode |
| --- | --- |
| Actuator | A device that converts a control command into physical action, such as torque, force, heat or valve movement. |
| Closed loop | Control that measures the result and corrects the command based on the difference from the desired state. |
| DCS | Distributed Control System - an integrated control architecture common in continuous and batch process plants. |
| HMI | Human-Machine Interface - the operational display and command interface between people and the controlled system. |
| Historian | A time-series data system designed to store process values, events and context over time. |
| I/O | Input/Output - the electrical or network interface between field devices and controller logic. |
| Interlock | Logic that prevents or stops an action when incompatible or hazardous conditions exist. |
| OT | Operational Technology - systems that monitor or control physical processes and equipment. |
| PLC | Programmable Logic Controller - a rugged industrial controller for logic, sequencing, process and motion functions. |
| PV / SP / MV | Process Variable / Setpoint / Manipulated Variable - measured value, desired value and commanded influence. |
| SCADA | Supervisory Control and Data Acquisition - a platform for monitoring and coordinating controllers, often across a plant or distributed sites. |
| Trip | A protective action that drives equipment or a process to a defined state when a specified condition occurs. |

# 9. Standards and source map

> How to use this list<br>Standards are periodically revised and may be adopted differently by country, industry and contract. Confirm the edition and legal status that apply to the specific machine, plant and market. The episode paraphrases concepts and does not reproduce normative text.

1. NIST SP 800-82 Rev. 3, Guide to Operational Technology Security - OT characteristics, architectures, risk and security controls.

1. ISA/IEC 62443 series, Security for Industrial Automation and Control Systems - security lifecycle, organization, system and component perspectives.

1. ANSI/ISA-95 and IEC 62264 series, Enterprise-Control System Integration - activity models and interfaces between manufacturing operations and enterprise systems.

1. IEC 61131 series, Programmable Controllers - controller concepts and programming-language framework; Part 3 is covered in later episodes.

1. IEC 61508, Functional Safety of E/E/PE Safety-related Systems - generic functional-safety lifecycle and integrity framework.

1. IEC 61511, Functional Safety - Safety Instrumented Systems for the Process Industry Sector - process-industry application of the safety lifecycle.

1. ISO 13849-1 and IEC 62061 - safety-related control systems for machinery.

1. ANSI/ISA-101.01, Human Machine Interfaces for Process Automation Systems - HMI lifecycle and design framework.

1. ANSI/ISA-18.2, Management of Alarm Systems for the Process Industries - alarm-management lifecycle.

1. CISA Industrial Control Systems resources - public guidance and advisories for industrial control and operational technology.

# 10. Episode quality gate

- A listener can explain the full sensor-controller-actuator-feedback chain without naming a vendor.

- The episode distinguishes open loop, closed loop, sequence, permissive, interlock, alarm and trip.

- The worked example connects process design, mechanical limits, instrumentation, software and operator interaction.

- No standard clause, trip value or vendor capability is presented without project context.

- The ending creates a clear bridge to Episode 2: PLCs and PACs.
