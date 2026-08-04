---
episode: 8
language: en
title: "HMI and Operator Interface Design"
target_duration: "40-45 minutes"
status: completed
extracted_from: docx
---

> CONTROL EDGE \| EPISODE 8<br>HMI and Operator Interface Design<br>From displaying data to situational awareness and safe action<br>hierarchy \| high-performance graphics \| commands \| trends \| alarms \| validation

| Audience | Mechanical, process, manufacturing, instrumentation, electrical and automation engineers |
| --- | --- |
| Target duration | 40-45 minutes |
| Format | Dialogue between Yael, a young mechanical engineer, and Amir, a senior process and controls engineer |
| Core example | An HMI shows a pump as RUNNING although no flow exists; an alarm flood hides the initiating failure |
| Deliverable | Full script + NotebookLM prompt + design map + checklist + sources |

Educational material. It does not replace engineering design, human-factors analysis, safety assessment, manufacturer instructions, usability testing or the contractually adopted editions of applicable standards.

# 1. Pre-production alignment check

- The episode continues directly from Episode 7: well-structured control software still needs an interface that exposes physical truth and supports correct human action.

- It covers both machine-mounted HMI and control-room interfaces while making their different operating contexts explicit.

- Alarm presentation and operator response are covered here; the complete alarm-management and SCADA lifecycle will be deepened in the next system-level episode.

- The episode avoids vendor-specific visual fashion and uses requirements that can be measured, tested and maintained.

- The ending bridges to Episode 9 on SCADA, DCS, historians and plant data infrastructure.

> Standards freshness check - August 2026<br>IEC 63303:2024 is the current international standard for HMI in process automation. ISA continues to list ISA-101.01-2015 together with ISA-TR101.01-2022 and ISA-TR101.02-2019. Alarm management uses IEC 62682:2022, and automation-system acceptance testing is mapped to IEC 62381:2024.

# 2. Episode objectives

- Define HMI boundaries relative to controllers, SCADA, historians and safety systems.

- Translate user tasks and abnormal scenarios into display hierarchy and navigation.

- Explain high-performance graphics, disciplined color and deviation-to-target presentation.

- Design commands, setpoints, modes, ownership and feedback so request is not confused with result.

- Present alarms, events, trends and data quality to support diagnosis and response.

- Adapt interfaces for machinery, maintenance, touch, localization and remote access.

- Build an HMI philosophy, style guide, object library, validation process and change lifecycle.

# 3. Timing and segment plan

| Time | Segment | Purpose |
| --- | --- | --- |
| 00:00-03:00 | Cold open: green pump, dry pipe | Show how a visually active HMI can hide the physical truth. |
| 03:00-06:30 | What an HMI is - and is not | Separate interface, control logic, safety function, SCADA and historian roles. |
| 06:30-10:30 | Start with operator tasks | Use task analysis and abnormal-situation questions before drawing screens. |
| 10:30-14:30 | Hierarchy and navigation | Build overview, unit, detail and support displays with predictable navigation. |
| 14:30-19:00 | High-performance graphics | Use hierarchy, shape, trends and restrained color to expose deviation. |
| 19:00-23:00 | Commands, modes and feedback | Design safe interaction, ownership, confirmation and command-result visibility. |
| 23:00-27:30 | Alarm presentation | Distinguish alarm, event and status; survive floods and prioritize response. |
| 27:30-31:30 | Trends and data quality | Make time, quality, scale and context visible. |
| 31:30-35:00 | Machine and maintenance HMI | Address line of sight, touch, setup, jog, permissions and troubleshooting. |
| 35:00-38:00 | Remote access and security | Treat identity, session, audit and remote command as engineered functions. |
| 38:00-42:00 | Lifecycle and validation | Create philosophy, style guide, libraries, scenario tests and change control. |
| 42:00-44:30 | Redesign and checklist | Turn the opening failure into a reusable engineering method. |

# 4. HMI hierarchy map

| Layer | User question | Recommended content |
| --- | --- | --- |
| Overview | Is operation healthy and where is attention required? | Operating objectives, constraints, deviation, area state, major alarms and path to cause. |
| Unit | Which subsystem is creating the deviation? | Major equipment, loops, flow paths, modes, permissives and process measures. |
| Detail / faceplate | What was commanded, what was achieved and why did it fail? | Command, state, feedback, interlocks, quality, trends and diagnostics. |
| Support | How is the condition verified and maintained? | Raw I/O, calibration, overrides, versions, procedures, audit and maintenance data. |

> Design rule<br>The HMI must remain truthful when commands are rejected, feedback fails, communication is lost, data become stale or equipment enters an unexpected mode.

# 5. NotebookLM production prompt

Create an English-only audio episode of 40-45 minutes using only the uploaded source pack and this document. Use two hosts: Yael, a young mechanical engineer who challenges design assumptions and asks practical questions; and Amir, a senior process and controls engineer who explains architecture, human factors, failure modes and lifecycle trade-offs. Make the exchange sound like two engineers conducting a design review of a real screen, not a lecture split between voices.

Use the continuous case of a cleaning skid whose HMI shows a pump in green as RUNNING although there is no flow, followed by an alarm flood. Give Yael about 45% of speaking time and Amir 55%. Yael should challenge vague phrases such as “intuitive screen,” “standard colors,” “important alarm” and “secure access.” Amir should answer with user tasks, failure states, measurable performance and verification methods.

Expand every acronym the first time it appears. Distinguish international standards, ISA standards, industry guidance and vendor implementation. Do not invent clause numbers, exact color mandates, response times, certifications or product features not present in the source pack. State that color alone is not sufficient coding and that a graphical red button is not an emergency-stop safety function without the required safety architecture.

The episode must cover HMI boundaries; task analysis; display hierarchy; navigation; high-performance graphics; color, contrast and accessibility; commands, setpoints, modes and ownership; alarm versus event; alarm floods; trends, time and data quality; machine and maintenance HMI; remote access; HMI philosophy; style guide; libraries; FAT/SAT and scenario testing. End with a ten-question review checklist and a clear transition to SCADA, DCS and historian architecture.

# 6. Full episode script

## 00:00-03:00 | Cold open - green pump, dry pipe

Amir: It is two in the morning on a cleaning skid. The HMI shows the circulation pump in bright green with the word RUNNING. The operator hears the motor, so the picture feels credible. But the flow transmitter reads almost zero, the discharge valve is still closed, and the pump is heating a dead-headed line.

Yael: Then the green pump symbol is not merely unattractive. It is making a false claim.

Amir: Exactly. Green is being driven by the command bit, not by proven operation. Within forty seconds the screen produces a low-flow alarm, a high-pressure alarm, a motor-current warning, two valve mismatch alarms and several downstream quality alarms. The alarm banner fills. The operator acknowledges the newest message and misses the earliest useful clue: the valve never proved open.

Yael: So the controller may be executing the revised state machine correctly, yet the human interface still prevents a good decision.

Amir: That is why HMI engineering is not decoration after the control code is finished. It is part of the control system lifecycle. The interface must help a person perceive what is happening, understand why it matters, and choose an effective action under normal, degraded and abnormal conditions.

Yael: Today we redesign that screen, but we also need rules that work for a packaging machine, a reactor skid and a plant control room.

Amir: Yes. We will separate status from command, create a display hierarchy, use color for meaning rather than entertainment, design commands with feedback, place alarms in a lifecycle, and test the interface with operators before startup.

## 03:00-06:30 | What an HMI is - and is not

Yael: Let us begin with the boundary. People call a local touch panel, a SCADA workstation and sometimes the entire control system “the HMI.”

Amir: Human-machine interface describes the means by which a human receives information from and interacts with an automated system. On a small machine it may be one panel mounted on the enclosure. In a process unit it may be several operator consoles, large displays, keyboards, pointing devices and alarm annunciation. A web client or mobile device can also be an HMI, but the environment and permitted actions change the engineering requirements.

Yael: And the HMI should not be the place where essential control logic secretly lives.

Amir: Correct. Basic control, interlocks and sequences belong in the controller architecture we discussed in Episode 7. An HMI may validate an entry, request a mode change, display state and record user action. But if closing a browser tab removes a critical permissive, the architecture is wrong.

Yael: What about safety? Can a red button on the screen be an emergency stop?

Amir: A graphical red button is not automatically a safety-related control. A safety function requires an engineered safety lifecycle, suitable hardware, diagnostics and validated behavior. The HMI can display safety status and may participate in specific safety architectures only when explicitly designed and assessed. Do not let a familiar icon borrow a claim the system cannot support.

Yael: Then SCADA is a larger supervisory environment, historian stores time-series data, and HMI is the interaction layer.

Amir: That is a useful working distinction. Products often combine those functions, but the requirement should still state which function is needed: direct machine operation, plant supervision, alarm handling, historical analysis, maintenance, reporting or remote support.

## 06:30-10:30 | Start with operator tasks, not graphic objects

Yael: Many projects start by opening the vendor graphics library and dragging pumps and valves onto a page.

Amir: That is equivalent to designing a machine by opening a catalogue of bearings before defining loads. Start with users, tasks and operating context. Who uses the interface? Operator, technician, process engineer, supervisor, quality specialist, integrator? What decisions must each person make, how often, under what time pressure, with what training and from what physical position?

Yael: For our cleaning skid, the operator needs to know whether the route is ready, whether circulation is proven and whether chemistry and temperature are within the recipe window.

Amir: Good. During startup the operator needs readiness and next-step information. During normal operation the need is deviation detection. During a trip the need becomes cause, consequence and recovery. During maintenance the technician needs raw I/O, device diagnostics and safe test functions. One screen rarely serves all those tasks well.

Yael: So we write scenarios before screens.

Amir: Yes. Normal startup, product change, sensor failure, loss of air, communication loss, power recovery, alarm flood, manual intervention, maintenance bypass and emergency shutdown. Ask: what must the person notice first? What information confirms the diagnosis? What action is permitted? What could be misunderstood?

Yael: That sounds like human factors engineering rather than graphic design.

Amir: It is. IEC 63303 and ISA-101 frame HMI as a lifecycle, not a collection of pictures. ISO 11064 adds ergonomic principles for workstations, displays and controls. The screen is only one part of the work system; lighting, viewing distance, noise, workload, shift handover and procedures matter too.

Yael: A useful design test would be: can a competent operator answer “what is abnormal, how serious is it, and what should I inspect next” without hunting through six pages?

Amir: Exactly. That is a performance requirement we can test.

## 10:30-14:30 | Display hierarchy and predictable navigation

Yael: How do we stop the interface from becoming hundreds of unrelated pages?

Amir: Use a hierarchy tied to operational decisions. A common pattern has an overview level for the area or machine line, a unit level for major equipment and control objectives, a detail level for one equipment module or loop, and support displays for diagnostics, configuration, maintenance and procedures. The names and number of levels can vary, but the navigation logic must be stable.

Yael: What belongs on the overview?

Amir: Not every valve. The overview should reveal whether the operation is healthy, where attention is required, which production or process objective is at risk, and how to navigate to the cause. For the skid, show route readiness, circulation status proven by flow, temperature and conductivity relative to targets, active phase, remaining time, major constraints and the highest-priority abnormal conditions.

Yael: The unit display then exposes the pump, heat exchanger, valves and key loops.

Amir: Yes, while the detail display may show pump command, motor feedback, flow, pressure, valve positions, interlocks, trends and maintenance diagnostics. Support pages can show raw channels and calibration data, but they should not be the normal operating path.

Yael: Navigation should be boring in the best sense.

Amir: Predictable home location, persistent area context, clear selected-object indication, consistent back behavior and a visible alarm path. Avoid hidden gestures as the only route to critical information. Avoid popups that cover the value the user is trying to diagnose. A popup is useful for a compact faceplate; it is harmful when several overlapping windows obscure the process.

Yael: And the operator should know whether the page is live, stale or disconnected.

Amir: Absolutely. Communication quality, simulation state, maintenance override and stale data require conspicuous but controlled indication. A frozen trend that looks calm is more dangerous than a visible communication alarm.

## 14:30-19:00 | High-performance graphics and disciplined color

Yael: High-performance HMI is often summarized as grey screens. That sounds too simple.

Amir: Grey is not the objective. The objective is perceptual hierarchy. Normal conditions should not compete visually with abnormal conditions. Backgrounds, equipment outlines and static structure are usually neutral. Strong saturated color is reserved for information requiring attention or carrying a defined meaning.

Yael: So a running pump does not have to turn bright green.

Amir: Correct. Motion or state can be shown with text, shape, line style, a small state indicator or an analog measure such as flow. If green is used everywhere for running, then color no longer highlights what matters. More importantly, color must not be the only encoding. Use labels, symbols, position, pattern or shape so a color-vision deficiency or poor display does not erase the message.

Yael: What makes process values easy to interpret?

Amir: Show relationship to limits and targets, not only digits. A temperature of 72.4 means little without the operating range. A deviation bar, analog scale, trend sparkline or target marker can reveal direction and margin. But every graphic must earn its space. Decorative pipes, 3D vessels and animated liquid surfaces often consume attention without improving a decision.

Yael: Can mimic diagrams still be useful?

Amir: Certainly. Spatial relationships and flow paths matter. The question is whether the mimic communicates process state and causality or merely copies the P and ID. A control display is not an electronic drawing. It can omit construction detail and add operating information such as constraint, deviation, mode, quality and time.

Yael: And color meanings must be written in the style guide.

Amir: Yes. IEC 60073 and IEC 61310-1 provide coding principles for indicators and safety-related signals. Project conventions must align with applicable requirements and be consistent. Do not improvise red, yellow, blue and green independently on every screen. Define background, foreground, alarm priorities, bad quality, manual mode, bypass, simulation, disabled equipment and selection states.

Yael: What about dark mode?

Amir: Choose based on environment, luminance and tested readability, not fashion. A control room used continuously differs from an outdoor panel in sunlight. Verify contrast, glare, viewing angle, night operation and printed or remote representations. Consistency and detectability matter more than a fashionable palette.

## 19:00-23:00 | Commands, modes, ownership and result feedback

Yael: The HMI is not only display. It changes the machine. Where do interaction designs fail?

Amir: A common failure is confusing a command request with achieved state. The operator presses OPEN; the button changes color immediately; the valve never moves. The interface must distinguish requested command, controller acceptance, movement or transition, proven state and failure.

Yael: For the pump we need at least command, motor-run feedback and process proof such as flow.

Amir: Exactly. And we need mode and ownership. Is the pump in automatic, manual, local, remote, maintenance or out-of-service? Which layer owns the command: sequence, local panel, HMI manual control, safety system or external package? Episode 7 gave every physical output one software owner. The HMI must expose that ownership so the operator does not fight an invisible controller.

Yael: Should every command have an “Are you sure?” dialog?

Amir: No. Confirmation fatigue is real. Routine reversible actions should be direct, provided the context and control are clear. Use stronger confirmation for consequential, infrequent or difficult-to-reverse actions: clearing accumulated totals, changing recipe family, overriding an interlock, stopping a critical utility or commanding equipment outside the operator’s line of sight.

Yael: Setpoint entry needs engineering too.

Amir: Show units, valid range, current value and source. Validate syntax and range before sending. Distinguish requested value from value accepted by the controller. Handle decimal separators, negative values, time zones and language. For a bilingual Hebrew-English system, test right-to-left labels beside left-to-right tags, units and numbers; do not assume a translation is only a string replacement.

Yael: What about touch targets and sliders?

Amir: Touch targets must suit gloves, vibration and screen size. Sliders are poor for precise or safety-significant entry unless bounded and supplemented. Prevent accidental double activation and edge touches. After a command, provide immediate acknowledgement that the request was received, then separate feedback showing whether the physical result occurred.

## 23:00-27:30 | Alarm presentation: from noise to actionable abnormality

Yael: Our opening case became an alarm flood. What qualifies as an alarm?

Amir: An alarm should indicate an abnormal condition requiring a timely operator response. A status is information about state. An event records that something happened. A prompt asks the user to complete a workflow. If every transition and diagnostic is called an alarm, the operator cannot tell what requires action.

Yael: Then priority is not the preference of the programmer.

Amir: Priority should follow a documented philosophy and rationalization considering consequence, available response time and the operator action that prevents or mitigates the consequence. The same numeric deviation can have different priority in different operating modes. An alarm without a defined response is often only an event or maintenance notification.

Yael: How should the HMI present alarms?

Amir: Provide a persistent summary, clear priority and state, readable message, equipment context, time, status of acknowledgement, and a direct route to the relevant display or response guidance. Preserve first-out or sequence information when it is diagnostically meaningful. Do not use acknowledgement as a substitute for correction.

Yael: What tools help during floods?

Amir: Designed suppression by state, shelving with control and audit, grouping, first-out logic, rate limiting for chattering indications, and a rational alarm hierarchy. But those are not excuses to hide poor configuration. IEC 62682 and the ISA-18 lifecycle emphasize philosophy, identification, rationalization, detailed design, implementation, operation, maintenance, monitoring, audit and management of change.

Yael: In our skid, low flow is probably the primary operator alarm. Every downstream calculation does not need to alarm immediately.

Amir: Right. The closed-valve mismatch may be a direct diagnostic. Derived quality alarms can be delayed or suppressed while circulation is not established. The aim is to support response, not to produce a complete list of everything that became false.

## 27:30-31:30 | Trends, time and data quality

Yael: A good trend often explains more than a page of numbers.

Amir: If it is engineered. A trend needs meaningful time range, sample or compression behavior, units, scale, target and limit context. The user should know whether data are live, interpolated, substituted, bad quality or unavailable. Multiple pens need clear identity and comparable scales; otherwise visual correlation can be invented by the graph.

Yael: For the opening event, we would plot valve command and feedback, pump current, discharge pressure and flow on one synchronized time axis.

Amir: Yes, with event markers for the start command and alarms. That tells us whether pressure rose before flow failed, whether the valve feedback lagged, and whether the transmitter data were stale. Timestamp source matters when data come from different controllers or networks. Episode 6 showed that synchronized clocks are part of diagnosis.

Yael: Should every process value have a sparkline?

Amir: No. Use embedded trends where recent direction and rate matter: temperature approach, tank level, pressure stability, cycle-time drift. For binary devices, a state timeline may be more useful. A trend must answer a question, not decorate the page.

Yael: And fixed scales are sometimes better than automatic scaling.

Amir: Often. Auto-scaling can make noise look dramatic or hide a large change by expanding the axis. Provide well-chosen defaults and controlled zoom. Preserve the operator’s orientation when switching between live and historical views.

## 31:30-35:00 | Machine HMI, setup and maintenance

Yael: A machine-mounted panel differs from a control-room console.

Amir: Very much. The operator may be standing, wearing gloves, moving between stations and looking at the mechanism. Line of sight matters. A jog command may be safe only while a hold-to-run device is actuated and the user can see the hazard zone. Physical enabling devices, guards and safety circuits cannot be replaced by a touch-screen button.

Yael: Machine operation also has short setup workflows.

Amir: Recipe change, format adjustment, homing, tool change, cleaning and recovery after jam. The HMI can guide those tasks with step status, prerequisites and illustrations, but it must not mask the actual safety procedure. Distinguish production mode from setup and maintenance, and show the effects of each mode on speed, interlocks and available commands.

Yael: Technicians want raw I/O and force functions.

Amir: They need diagnostics, but dangerous tools require authorization, visibility and audit. Show whether an input is physically active, simulated, forced or overridden. A forced bit that looks normal on the operator screen is a hidden hazard. Provide an obvious global indication and a list of active overrides.

Yael: What about usability on small panels?

Amir: Prioritize. Do not shrink a control-room page until it fits. Build task-specific views, large targets, short labels, clear units and minimal typing. Test sunlight, glare, cleaning chemicals, condensation, vibration and the actual gloves. ISO 11064 is mainly control-centre oriented, but its human-factors principles remain useful; machinery signal requirements also connect to IEC 61310-1.

## 35:00-38:00 | Remote access, identity and cybersecurity

Yael: Modern HMI products are web based and remotely accessible. That improves support but changes the risk.

Amir: Correct. Remote observation and remote command are different capabilities. Define who can connect, from where, through which controlled path, with what authentication, authorization, session timeout, logging and approval. Do not expose an HMI directly to the internet because it has a password.

Yael: The interface itself should communicate security state.

Amir: It should show logged-in identity, role, session context and whether the view is read-only or command capable. Audit records need user, time, object, old value, new value and result where appropriate. Shared operator accounts may be convenient but destroy accountability; individual identification and practical shift workflows must be balanced.

Yael: How do we avoid locking the operator out during an emergency?

Amir: Security design must support operations. Apply least privilege, but make essential emergency actions available through the approved architecture. Design degraded operation when identity services or remote links fail. Cybersecurity is a lifecycle topic under IEC 62443, which we will treat in depth later. For this episode, remember that an HMI is both an information surface and a command surface.

Yael: And mobile screens?

Amir: Use them for tasks suited to mobility: inspection, acknowledgement where permitted, guided maintenance, read-only dashboards. Consider connection loss, small size, orientation, accidental touch, device custody, camera use, hazardous areas and whether the person can see the equipment being commanded.

## 38:00-42:00 | Philosophy, style guide, libraries and validation

Yael: How do we prevent every project engineer from inventing a new visual language?

Amir: Create an HMI philosophy and a style guide. The philosophy defines objectives, users, lifecycle, hierarchy, alarm principles, security, roles, performance and governance. The style guide turns those decisions into implementable conventions: colors, fonts, symbols, faceplates, navigation, commands, units, number formats, trend defaults and bad-quality behavior.

Yael: Then reusable object libraries implement the guide.

Amir: Yes, but library reuse is not enough. A bad faceplate can be replicated perfectly. Each object needs defined data contracts, states, quality behavior, command handling and testing. Version the library, document changes and control migration across applications.

Yael: What does HMI testing look like beyond checking that tags animate?

Amir: Start with design reviews and prototypes. Perform task-based usability tests with representative users. In FAT and site testing, run operational scenarios: startup, alarm, sensor failure, mode conflict, loss of communication, power recovery, language change and user-role change. Measure whether the user detects the abnormality, reaches the right page, understands the state and completes the correct action within the required time.

Yael: IEC 62381 can structure FAT, FIT, SAT and SIT, while HMI-specific acceptance criteria come from the project specification.

Amir: Exactly. Include performance limits: page load, update rate, alarm display latency, maximum stale-data indication time, login behavior and recovery. Validate with realistic tag counts and network load, not an empty development server.

Yael: After startup, audit and management of change continue.

Amir: Track nuisance alarms, frequently visited pages, navigation failures, operator workarounds, disabled objects, response times and change requests. A mature HMI is maintained like control software, not frozen like artwork.

## 42:00-44:30 | Redesigning the opening screen and closing checklist

Yael: Let us return to the green pump. What does the redesigned overview show?

Amir: The pump symbol is neutral. Beside it, the state reads START REQUESTED, then STARTING, then RUNNING - FLOW PROVEN. If motor feedback exists without flow, the state becomes RUNNING - NO FLOW and the unit display highlights the blocked route. The discharge valve shows command and proven position separately. The active recipe phase displays its permissives and the next expected transition.

Yael: The overview includes a small flow and pressure trend, route readiness and the one actionable high-priority alarm.

Amir: Yes. The alarm message states the condition and object clearly, links to the unit display and preserves the first-out valve mismatch. Downstream quality alarms are suppressed by design until circulation is established. An override banner appears if a technician forces any relevant signal.

Yael: Give us the final engineering questions.

Amir: One: which user decision is this display supporting? Two: does it distinguish command, accepted state, feedback and physical effect? Three: can abnormal conditions be detected without relying on color alone? Four: is navigation predictable from overview to cause? Five: are alarms actionable, prioritized and protected against flood? Six: do trends show time, scale, quality and context? Seven: are modes, ownership, overrides and permissions visible? Eight: has the interface been tested with representative users in realistic scenarios? Nine: are philosophy, style guide, library version and change history controlled? Ten: does the screen remain truthful when communication, data quality or equipment feedback fails?

Yael: Then the HMI is successful when it helps the operator build the correct mental model quickly.

Amir: Exactly. The next episode moves above the local interface into SCADA, DCS and historians: how multiple controllers become an operational system and how data are stored, contextualized and trusted across a plant.

# 7. Engineering design and acceptance checklist

- Name the user role and the decision supported by every primary display.

- Distinguish command request, controller acceptance, equipment feedback and process effect.

- Provide an overview that exposes operational health, constraints and abnormal conditions.

- Use a stable display hierarchy and predictable navigation.

- Reserve strong color for defined attention states; never rely on color alone.

- Show units, limits, target, mode, ownership, quality and timestamp where they affect interpretation.

- Design command confirmation according to consequence, frequency and reversibility.

- Make active forces, overrides, bypasses, simulations and inhibited alarms globally visible.

- Define alarms through philosophy and rationalization; verify response, flood behavior and first-out needs.

- Engineer trends with fixed defaults, synchronized time, quality indication and meaningful context.

- Validate touch, glare, gloves, viewing distance, localization and accessibility in the real environment.

- Test realistic normal, abnormal, communication-loss and restart scenarios with representative users.

- Control HMI library versions, application changes, user permissions and audit records.

- Monitor post-startup usability, nuisance alarms, workarounds and navigation failures.

# 8. Glossary

| Term | Meaning |
| --- | --- |
| HMI | Human-Machine Interface - the information and interaction layer between people and an automated system. |
| Situational awareness | Ability to perceive relevant state, understand its significance and anticipate likely development. |
| Display hierarchy | Structured levels from operational overview to unit, detail and support information. |
| Faceplate | Reusable interaction object for one equipment item or control loop. |
| Command / state / effect | Requested action, achieved equipment condition and resulting physical process response. |
| Alarm | Abnormal condition requiring a timely operator response. |
| Event | Recorded occurrence that may not require operator action. |
| Shelving | Temporarily removing an alarm from normal presentation under controlled, time-bounded and audited rules. |
| Suppression | Preventing alarm presentation when a defined operating condition makes the alarm irrelevant or misleading. |
| Bad quality / stale data | Indication that a displayed value is invalid, uncertain, substituted or too old to be trusted. |
| HMI philosophy | Owner-level policy for lifecycle, users, hierarchy, alarm principles, security and governance. |
| Style guide | Implementation rules for graphics, navigation, symbols, colors, commands, units and object behavior. |

# 9. Standards and source map

The editions listed here were checked against official sources in August 2026. Always verify the edition adopted by contract, local regulation and owner requirements.

IEC 63303:2024 - Human machine interfaces for process automation systems. International lifecycle, functions and performance framework for process-automation HMI. Official source

ISA-101.01-2015 - Human Machine Interfaces for Process Automation Systems. ISA continues to list the 2015 edition while IEC 63303:2024 is now the international standard. Official source

ISA-TR101.01-2022 - HMI Philosophy. Practical guidance for creating the owner-specific philosophy that governs design and lifecycle decisions. Official source

ISA-TR101.02-2019 - HMI Usability and Performance. Guidance on specification, validation, audit and management of HMI performance. Official source

IEC 62682:2022 - Management of alarm systems for the process industries. Alarm lifecycle and operator-presentation framework. Official source

ISO 11064-5:2008 - Ergonomic design of control centres - Displays and controls. Requirements and recommendations for display/control interaction. Official source

ISO 11064-4:2013 - Ergonomic design of control centres - Workstation layout and dimensions. Official source

IEC 60073:2002 - Coding principles for indicators and actuators, including consistent meanings for visual, acoustic and tactile indications. Official source

IEC 61310-1:2007 - Safety of machinery - visual, acoustic and tactile signals at the human-machine interface. Official source

IEC 62381:2024 - Automation-system FAT, FIT, SAT and SIT requirements and checklists; useful for HMI acceptance and scenario testing. Official source

ISA-5.1-2024 - Instrumentation and Control - Symbols and Identification. Supports consistent tag naming and process representation. Official source

# 10. Bridge to the next episode

Episode 9 moves above the local interface into SCADA, DCS, historians and plant data infrastructure: how information is collected from many controllers, how quality and timestamps are managed, how availability and permissions are engineered, and how process data become trustworthy operational context.
