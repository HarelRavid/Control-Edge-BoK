---
episode: 3
language: en
title: "Sensors and Measurement - From the Physical World to a Trustworthy Signal"
target_duration: "40-44 minutes"
status: completed
extracted_from: docx
---

> CONTROL EDGE \| EPISODE 3<br>Sensors and Measurement<br>From the physical world to a signal the controller can trust<br>Measurement chains, metrology, dynamics, 4-20 mA, HART, IO-Link, installation, calibration and diagnostics

| Audience | Mechanical, process, manufacturing, instrumentation and automation engineers |
| --- | --- |
| Target duration | 40-44 minutes |
| Format | Dialogue between Yael, a young mechanical engineer, and Amir, a senior process and control engineer |
| Core example | A false temperature jump during VFD acceleration on a circulation skid |
| Deliverable | Full script + NotebookLM prompt + engineering checklist + sources |

Educational material. It does not replace engineering design, risk assessment, manufacturer instructions, a calibration program, or the contractually applicable editions of relevant standards.

# 1. Pre-production alignment check

- The episode delivers the promise from Episode 2: the controller sees signals rather than the machine, so signal trustworthiness is now examined.

- The audience remains mechanical and process engineers; the explanation begins with physics and installation before moving to electrical interfaces and code.

- The episode does not become a sensor catalogue. Technologies are compared through physical principle, process conditions and failure modes.

- Metrology terms are handled carefully using VIM and GUM concepts without turning the episode into a laboratory course.

- SIL, machine safety and Ex topics remain boundary discussions; detailed calculations belong in dedicated later episodes.

- The ending creates a direct bridge to Episode 4 on actuators, valves, solenoids and converting software commands into physical action.

> Freshness check<br>In June 2026, new editions of IEC 61298-1/-2/-3 and IEC 62828-1 were published. This episode uses the updated scope split: IEC 62828 for industrial and process measurement transmitters, and IEC 61298 for other process instrumentation within its scope.

# 2. Episode objectives

- Explain the complete measurement chain from measurand and sensing element to controller tag, status and timestamp.

- Distinguish accuracy, precision, repeatability, hysteresis, linearity, drift, resolution, calibration and measurement uncertainty.

- Connect static sensor specifications with response time, bandwidth, sampling, filtering and total measurement latency.

- Compare common pressure, temperature, flow, level, presence, position, force and vibration sensing principles.

- Explain discrete interfaces, pulse and frequency signals, voltage, 4-20 mA, HART and IO-Link without treating any one interface as universal.

- Identify installation-driven errors including impulse lines, thermowells, mounting, cable routing, grounding, shielding and isolation.

- Design useful diagnostics, quality status, calibration records and failure responses.

- Recognize the boundary between ordinary measurement, safety instrumentation and hazardous-area design.

# 3. Timing and segment plan

| Time | Segment | Purpose |
| --- | --- | --- |
| 00:00-02:30 | Cold open: the temperature follows the drive | Show why a smooth signal is not necessarily a true signal. |
| 02:30-06:00 | The measurement chain | Define measurand, sensing, conditioning, transmission, I/O and semantics. |
| 06:00-10:30 | Metrology vocabulary | Separate accuracy, repeatability, uncertainty, calibration and verification. |
| 10:30-15:30 | Dynamic truth | Connect response time, bandwidth, sampling, aliasing and filtering. |
| 15:30-20:30 | Process sensors | Compare pressure, temperature, flow and level principles. |
| 20:30-25:30 | Machine sensors | Compare presence, position, force, weight and condition sensing. |
| 25:30-30:00 | Signal interfaces | Explain discrete, pulse, voltage, 4-20 mA, HART and IO-Link. |
| 30:00-34:30 | Installation and signal integrity | Trace grounding, shielding, isolation, scaling and data timing. |
| 34:30-38:30 | Calibration and diagnostics | Design quality status, maintenance evidence and fault response. |
| 38:30-41:30 | Safety and hazardous areas | Define IEC 61511 and IEC 60079 boundaries. |
| 41:30-44:00 | Worked example and checklist | Resolve the opening fault and bridge to actuators. |

# 4. Measurement-chain map

Use this table to prevent the common mistake of treating sensor accuracy as the performance of the complete measurement system.

| Stage | Engineering decision | Typical failure |
| --- | --- | --- |
| 1. Purpose and measurand | Define the physical quantity, location, operating state and why the value is needed. | Ambiguous “tank temperature”; measuring wall temperature instead of bulk liquid. |
| 2. Primary element and process interface | Select a physical principle and compatible connection, materials and protection. | Coating, plugging, poor immersion, vibration, side load, corrosion. |
| 3. Signal conditioning and transmitter | Excitation, amplification, compensation, linearization, damping and diagnostics. | Wrong sensor type, excessive damping, configuration drift, supply sensitivity. |
| 4. Transmission and wiring | Carry the signal with known electrical, timing and quality behavior. | Voltage drop, EMI, ground loop, shield error, stale network data. |
| 5. I/O and conversion | Acquire, isolate, digitize, time-stamp and scale raw data. | Wrong range, aliasing, insufficient resolution, inconsistent update time. |
| 6. Software validation and use | Apply units, quality, plausibility, alarms, control and historian semantics. | Clamping away fault codes, wrong units, frozen values, hidden substitution. |
| 7. Lifecycle evidence | Calibrate, verify, maintain, replace and assess out-of-tolerance impact. | No as-found record, wrong spare configuration, undocumented changes. |

# 5. Sensing-technology decision map

Representative vendors, without ranking, include Endress+Hauser, Emerson/Rosemount, Siemens, Yokogawa, Honeywell, VEGA and WIKA in process instrumentation; and SICK, ifm, Balluff, Pepperl+Fuchs, Keyence, Omron, Banner and Turck in machine sensing. Selection is based on requirements, compliance, local service and lifecycle rather than logo.

| Variable | Common principles | Selection questions |
| --- | --- | --- |
| Pressure | Gauge, absolute, differential; piezoresistive, capacitive, resonant and mechanical elements. | Pressure type, overpressure, static pressure, pulsation, impulse lines, seals, materials, elevation. |
| Temperature | RTD, thermocouple, thermistor, semiconductor, infrared. | Range, accuracy, response, immersion, thermowell, lead compensation, cold junction, emissivity. |
| Flow | DP, magnetic, Coriolis, vortex, ultrasonic, turbine, thermal. | Fluid properties, conductivity, density, gas/liquid, straight run, pressure loss, two-phase, turndown. |
| Level | Hydrostatic, radar, guided wave, ultrasonic, capacitance, displacer, point switch. | Density, vapor, foam, coating, internal structures, dead zone, interface, nozzle geometry. |
| Presence and distance | Inductive, capacitive, photoelectric, ultrasonic, magnetic, mechanical switch. | Target material, color, gloss, dust, moisture, angle, background, mounting, cycle rate. |
| Position and speed | Incremental/absolute encoder, resolver, linear scale, LVDT, laser. | Resolution versus accuracy, homing, coupling, backlash, update rate, cable and maximum speed. |
| Force, weight and torque | Strain gauge, piezoelectric, hydraulic/pneumatic, magnetoelastic. | Load path, side load, preload, temperature, overload, frame stiffness, dynamic versus static. |
| Condition monitoring | Acceleration, velocity, displacement, acoustic, temperature, current signature. | Mounting, bandwidth, sample rate, operating-state baseline, algorithm semantics and trend context. |

> Engineering caution<br>There is no context-free “accurate sensor.” There is a measurement chain that meets uncertainty, response, environment, diagnostic and maintenance requirements under defined conditions.

# 6. NotebookLM production prompt

> Paste-ready instruction<br>Create an English-only audio episode of 40-44 minutes using only this document.<br><br>Hosts:<br>- Yael: a young mechanical engineer, sharp and curious. She represents mechanical and process engineers who are not instrumentation specialists. She asks concrete questions, challenges assumptions and connects measurement to mechanical installation.<br>- Amir: a senior process and control engineer, calm and practical. He explains from commissioning, operations and troubleshooting experience without sounding superior.<br><br>Style:<br>- Natural, technically precise dialogue, not a read lecture and not a vendor advertisement.<br>- Approximately 45% Yael and 55% Amir.<br>- Use the false temperature jump during VFD acceleration as the narrative thread and resolve it only at the end.<br>- Explain each technical term in plain English on first use and then use it consistently.<br>- Leave short pauses after accuracy versus repeatability, after aliasing, and after the troubleshooting checklist.<br>- Do not read URLs, clause numbers or the source list aloud. Mention standards only when they clarify engineering responsibility.<br>- Do not invent accuracy values, failure-current limits or SIL requirements. All example numbers are illustrative.<br>- Do not describe IO-Link as a fieldbus, HART as replacing 4-20 mA, or calibration as necessarily including adjustment.<br>- End with a clear bridge to Episode 4 on actuators and valves.<br><br>Required structure:<br>Fault opening; measurement chain; metrology; dynamic response; process sensors; machine sensors; signal interfaces; installation and EMC; calibration and diagnostics; safety and Ex boundaries; resolution and checklist.<br><br>Use the full script as the required factual framework, while allowing short natural reactions that do not change the technical meaning.

# 7. Full episode script

## 00:00-02:30 | Cold open - the temperature that followed the drive

Amir: A circulation skid is running steadily at thirty-two degrees Celsius. The pump drive starts to accelerate, and the temperature transmitter jumps to thirty-seven. Five seconds later it falls back. The process engineer says the heater is unstable. The mechanical engineer suspects poor mixing. The automation engineer adds a filter and the trend becomes smooth.

Yael: That sounds like a successful fix, except the liquid probably never heated by five degrees in one second.

Amir: Exactly. A smooth lie is still a lie. The jump could come from electromagnetic coupling, a grounding problem, a poorly routed thermocouple cable, common-mode voltage, an input module range error, or an actual vibration effect on the probe. A filter may hide the symptom while adding delay to the control loop.

Yael: So today we are not asking only which sensor measures temperature. We are asking how the physical quantity becomes a trustworthy number in the controller.

Amir: That is the episode. Sensors, transmitters, wiring, sampling, calibration, diagnostics and installation. The controller from Episode 2 does not see pressure, flow or position. It receives electrical or digital representations that have a history, a bandwidth and failure modes.

Yael: And our opening rule is that no software correction can rescue a measurement chain we do not understand.

Amir: Well said. Let us follow the signal from the process to the code.

## 02:30-06:00 | The measurement chain, not just the sensor

Yael: People use sensor, transducer and transmitter as if they are the same word. How should an engineer think about them?

Amir: Start with the measurand: the quantity intended to be measured. It may be pressure at a nozzle, shaft position, liquid temperature at a defined point, mass flow, vibration acceleration or the presence of a cap. The primary sensing element interacts with that quantity. A transduction element converts the effect into another form, often resistance, voltage, capacitance, frequency or displacement. Signal conditioning then excites, amplifies, linearizes, compensates and converts the signal.

Yael: And a transmitter packages some of those functions and sends a standardized output.

Amir: Correct. A pressure transmitter may contain a diaphragm, a sensing bridge, temperature compensation, a microprocessor, diagnostics and a 4-20 mA plus HART interface. A simple inductive proximity switch performs sensing and conditioning but gives only an on-off output. An encoder produces pulses or a digital position word. The boundaries vary, so the useful object is the complete measurement chain.

Yael: Let me draw it verbally: measurand, process connection, sensing element, conditioning, transmission, I/O module, scaling into engineering units, validation, time stamp, and finally the logic or control loop.

Amir: Add the mechanical installation and the environment around every block. A pressure sensor with a perfect calibration can report the wrong vessel pressure because its impulse line is plugged. A thermocouple can be correct while the thermowell measures the wall rather than the fluid. An encoder can count perfectly while the coupling slips.

Yael: So the measurement location is part of the instrument specification.

Amir: Absolutely. “Temperature of the tank” is not a complete requirement. At what elevation, immersion depth, flow condition and response time? Is the value for control, protection, energy balance or quality records? The purpose determines the architecture.

Yael: This also explains why P and ID tags matter. A tag such as PT identifies a pressure transmitter, but the tag alone does not specify range, accuracy, material, hazardous-area rating or failure behaviour.

Amir: Yes. ISA-5.1 gives a common language for symbols and identification. The instrument index, data sheet, loop drawing, I/O list and cause-and-effect information carry the rest.

## 06:00-10:30 | Accuracy, precision, repeatability and uncertainty

Yael: Now the vocabulary that causes arguments. A brochure says plus or minus zero point one percent accuracy. What does that promise?

Amir: Not enough by itself. We need to know percent of what: calibrated span, full scale, reading, upper range limit, or a combination. We need reference conditions, temperature effects, static pressure effects, stability, mounting position, supply variation, digital resolution and whether the specification is typical or guaranteed.

Yael: How do you separate accuracy and precision without turning this into a metrology lecture?

Amir: Use a target. Precision describes how closely repeated indications cluster. A precise instrument can repeatedly hit the same wrong point. Trueness concerns closeness of the average to a reference. Accuracy is a qualitative concept associated with closeness to the true quantity value; in engineering data sheets, manufacturers often use “accuracy” as a packaged limit of error. We must read their definition rather than assume a universal formula.

Yael: Repeatability is then the spread under the same conditions over a short time.

Amir: Yes, while reproducibility considers changed conditions such as operator, location, method or time. Hysteresis is different: the indication depends on whether we approached the point from above or below. Linearity concerns deviation from a chosen straight-line relationship. Drift is change over time. Resolution is the smallest change the system can display or distinguish, but a display with many digits is not necessarily accurate.

Yael: And uncertainty?

Amir: Measurement uncertainty characterizes the dispersion of quantity values that could reasonably be attributed to the measurand, based on the measurement model and available information. It belongs to the result, not only to the sensor. The budget may include reference uncertainty, transmitter performance, ambient influence, installation, analog input, scaling, repeatability and process variability.

Yael: So calibration does not make uncertainty disappear.

Amir: Correct. Calibration establishes a relationship between reference values and instrument indications, with uncertainties. Adjustment is a separate action that changes the instrument. Verification checks whether defined requirements are met. People say “calibrate it” when they may mean any of the three.

Yael: Give a practical example.

Amir: Suppose a differential-pressure transmitter is ranged zero to one hundred kilopascals. Its reference accuracy may look excellent, but it is installed outdoors with long impulse lines, one leg exposed to sun, and the zero shifts with mounting. The total field performance can be dominated by installation, not electronics. A good specification therefore asks for required uncertainty at the process operating point and under actual influence conditions.

Yael: This is why oversizing the range is harmful. If the normal signal uses only ten percent of span, the effective error relative to reading may be much worse.

Amir: Exactly. Select range with credible upset margin, not maximum catalogue range by habit.

## 10:30-15:30 | Static specifications and dynamic truth

Yael: A sensor can be accurate in steady state and still be useless for control.

Amir: Yes. Control requires dynamic performance. Important terms include response time, time constant, rise time, settling time, bandwidth, dead time and update period. They are related but not interchangeable.

Yael: Let us use a thermowell.

Amir: A bare small RTD element can respond quickly, but installed inside a thick thermowell in slow-flowing liquid it may have a long thermal time constant. The transmitter may update every hundred milliseconds, yet the physical assembly takes tens of seconds to approach a step change. Software cannot recover information that the mechanical assembly never captured.

Yael: The reverse problem appears in vibration. A slow process input module may average away the frequencies we actually need.

Amir: Correct. For vibration, acoustic emission, torque ripple or fast registration, the entire chain needs appropriate bandwidth: sensor, mounting, cable, conditioner, anti-alias filter, sample rate, transport and algorithm. Sampling above twice the highest frequency is the theoretical minimum for an ideally band-limited signal; practical systems need filtering and margin.

Yael: Aliasing means a high-frequency component appears as a false lower frequency.

Amir: Yes. It is not ordinary noise that disappears by averaging after sampling. The anti-alias filter must act before the analog-to-digital conversion. Similarly, debouncing a mechanical switch is useful, but excessive debounce can make a fast event invisible.

Yael: Every filter buys smoothness with something.

Amir: Usually delay and attenuation. A first-order low-pass filter can reduce noise but adds phase lag. In a closed loop, that lag reduces stability margin. In alarm logic it can delay detection. Filters should be selected from the required bandwidth and response time, not from a desire for attractive trends.

Yael: What about sensor damping configured inside a smart transmitter?

Amir: It is part of the chain and must be documented. There may be damping in the sensor electronics, transmitter output, input module, PLC code, HMI trend and historian. Stacking several filters can create a system that looks calm but reacts late.

Yael: So a loop sheet should include update time and damping, not only range and units.

Amir: For critical loops, yes. Also define the time stamp source. A value that arrived now may represent a measurement captured earlier. Sequence-of-events and high-speed applications need known time semantics.

## 15:30-20:30 | Process measurements: pressure, temperature, flow and level

Yael: Let us tour the common process variables without pretending one technology wins everywhere.

Amir: Pressure first. Decide gauge, absolute or differential. Then consider range, overpressure, process temperature, wetted materials, pressure pulsation, vacuum, static-pressure effects and the mechanical connection. For differential pressure, the impulse lines, seals and elevation can create more error than the transmitter.

Yael: A liquid-filled capillary can protect the transmitter from temperature, but adds its own temperature and response effects.

Amir: Exactly. Remote seals solve one problem by introducing a designed measurement system with fill-fluid behaviour. Temperature next: RTDs offer stable resistance-based measurement over industrial ranges and are standardized by IEC 60751. Thermocouples cover wide and high-temperature ranges and are standardized by IEC 60584, but require correct alloy, extension cable and cold-junction compensation.

Yael: Two-wire, three-wire and four-wire RTD connections matter because lead resistance matters.

Amir: Yes. Four-wire measurement best separates lead resistance, three-wire compensates under assumptions, and two-wire includes lead resistance directly. But mechanical details still matter: sheath diameter, insertion depth, vibration, thermowell design, thermal conduction and maintainability.

Yael: Flow is even more dependent on process properties.

Amir: A differential-pressure element is mature and broadly applicable but introduces permanent pressure loss and depends on density and installation. Electromagnetic flowmeters require conductive fluid and good electrode contact. Coriolis meters directly measure mass flow and density but can be expensive and sensitive to installation stress or two-phase flow. Vortex meters need sufficient Reynolds conditions and can be affected by vibration. Ultrasonic technologies depend on geometry, fluid condition and acoustic path.

Yael: And level?

Amir: Hydrostatic level converts pressure to level and therefore depends on density and vapor pressure. Radar can be non-contact and robust, but antenna placement, internal structures, foam and dielectric properties matter. Guided-wave radar follows a probe and may handle interfaces differently. Capacitance, ultrasonic and point switches each have suitable and unsuitable media.

Yael: The unifying question is not “which sensor is best?” but “what physical principle remains valid in this process?”

Amir: Exactly. Include cleaning, coating, crystallization, gas bubbles, solids, viscosity, conductivity, corrosion, hygienic requirements and maintenance access. A technology selected from a catalogue picture may fail when the process touches it.

## 20:30-25:30 | Machine sensing: presence, position, speed, force and condition

Yael: Machine builders meet a different sensor landscape: inductive, capacitive, photoelectric, ultrasonic, magnetic and encoders.

Amir: Inductive proximity sensors are excellent for metallic targets, but nominal sensing distance depends on target material, size, mounting and environment. Capacitive sensors can detect non-metallic materials, but moisture and buildup may shift the threshold. Photoelectric sensors provide long ranges and flexible optics, yet target color, gloss, dust, alignment and background matter. Ultrasonic sensors are less dependent on color but depend on acoustic reflection, dead zones, air conditions and target angle.

Yael: A mechanical limit switch is old technology but still useful when a physical contact and clear state are desirable.

Amir: Yes, provided life, bounce, speed, sealing and mechanical wear are acceptable. Sensor choice is not a contest between old and smart. It is a fit between failure modes and the function.

Yael: Encoders deserve special attention. Incremental versus absolute?

Amir: An incremental encoder produces changes: pulses and often quadrature direction information. The controller establishes position from counts and usually needs a reference or homing strategy after power loss. An absolute encoder reports a position code, possibly single-turn or multi-turn. But “absolute” does not eliminate coupling slip, backlash, mounting eccentricity or loss of mechanical reference.

Yael: Resolution is counts per revolution, but accuracy includes graduation, eccentricity and mechanical errors.

Amir: Correct. Also specify maximum speed, output interface, update rate, cable length, electrical noise immunity and whether motion safety functions require a certified feedback architecture.

Yael: Force and weight use strain gauges or load cells. The mechanical load path is part of the measurement.

Amir: Absolutely. Side loads, binding, temperature gradients, preload, mounting torque and cable shielding can dominate. A load cell calibrated on a bench may be wrong once the frame distorts. For vibration and condition monitoring, mounting stiffness, sensor orientation, bandwidth and baseline operating condition are essential.

Yael: A smart vibration sensor that outputs one health number is convenient, but we should know how that number is created.

Amir: Yes. Is it RMS velocity, acceleration, envelope energy, temperature, a vendor model, or a combination? Which frequency band and time window? The diagnostic can be valuable, but the semantics must be documented.

## 25:30-30:00 | From switch contacts to 4-20 mA, HART and IO-Link

Yael: Now the interfaces. Start with discrete sensing.

Amir: A discrete sensor may be dry contact, PNP, NPN, two-wire electronic or a standardized proximity interface. The input circuit must match voltage, current, polarity, leakage and diagnostic expectations. “On” in software is meaningless until we define the electrical and process state it represents.

Yael: Analog voltage is simple but vulnerable to voltage drop and reference differences over distance.

Amir: That is why current loops are common in process plants. In a 4-20 mA loop, the measured value is represented by current. Four milliamps provides a live zero, allowing some distinction between a valid zero and certain open-circuit conditions. But not every fault is automatically detected, and failure signaling must be engineered.

Yael: NAMUR NE 43 addresses failure information for digital transmitters with analog output.

Amir: Yes. It standardizes the concept of signal levels outside the normal measurement range for failure indication and reliable detection. The actual system must configure transmitter, isolator, input card and logic consistently. A generic clamp at zero to one hundred percent can destroy the diagnostic information.

Yael: HART keeps the analog value and adds digital communication on the same wires.

Amir: Correct. HART superimposes frequency-shift-keyed two-way digital communication on the 4-20 mA loop. It can carry device identification, configuration, diagnostics and additional variables. But the host must actually collect and use that information; a HART-capable transmitter connected to a plain analog card may behave like an ordinary loop.

Yael: IO-Link is common closer to machines.

Amir: IEC 61131-9 standardizes the point-to-point SDCI interface known as IO-Link. It extends traditional sensor and actuator wiring with bidirectional process data, parameters, identification and diagnostics. It is not a fieldbus; the IO-Link master connects the devices to the higher-level network.

Yael: That enables automatic parameter replacement after a sensor swap, provided the engineering and device identity are managed.

Amir: Yes, and it also creates configuration and cybersecurity questions. Who may change thresholds? Which parameters are backed up? How are device revisions handled? Smart does not mean self-governing.

Yael: Pulse and frequency signals still matter for flow, speed and counting.

Amir: They do. Specify pulse width, maximum frequency, electrical interface, missed-pulse diagnostics, counter rollover and time base. The interface must preserve the information the sensor produces.

## 30:00-34:30 | Signal integrity, installation and sampling

Yael: Return to our temperature jump when the drive starts. What would you inspect before adding code?

Amir: First confirm whether the physical process changed with an independent measurement or thermal plausibility calculation. Then inspect cable routing, shield termination, grounding, separation from motor and drive cables, junctions, extension-wire type, transmitter power, input isolation and common-mode limits. Check whether the interference appears at the sensor, transmitter output, marshalling panel or I/O value.

Yael: The phrase “ground the shield at one end” is repeated as if universal.

Amir: It is a useful pattern in some low-frequency analog systems, not a universal law. The correct shield and grounding practice depends on cable construction, frequency, equipotential bonding, device manuals, hazardous-area design and EMC architecture. Follow the engineered scheme, not folklore.

Yael: What does IEC 61326 contribute?

Amir: It defines EMC requirements for measurement, control and laboratory equipment, including immunity and emissions. Product compliance helps, but system installation still determines exposure, cable coupling and grounding. A compliant transmitter and compliant drive can still be installed badly together.

Yael: Isolation can break ground loops, but it also has limits.

Amir: Yes. Specify channel-to-channel and channel-to-ground isolation, working voltage, surge environment, accuracy effects and failure mode. Barriers and isolators in hazardous areas must also satisfy the intrinsic-safety entity or system design, not merely provide generic isolation.

Yael: Then the software side: scaling.

Amir: Do not bury raw-to-engineering conversion in scattered arithmetic. Define raw range, engineering range, under-range, over-range, quality status and units in one controlled block. Preserve the raw value for diagnostics. Validate rate of change, plausibility and cross-sensor relationships where justified, but do not replace a real fault with a guessed value without a defined degraded mode.

Yael: Sample rate should reflect the physics and the control need.

Amir: Yes. A temperature loop may need modest rates, while registration or vibration needs high-speed acquisition. Faster is not always better: it increases noise visibility, data load and processing. The requirement is sufficient bandwidth, known latency and consistent timing.

Yael: And trends must not confuse sample rate with display refresh.

Amir: Exactly. An HMI that draws one point per second may display a value acquired every ten milliseconds, or it may only sample once per second. Historian compression can remove short events. For investigations, know each stage.

## 34:30-38:30 | Calibration, diagnostics and failure behavior

Yael: How should a plant manage calibration without turning it into a calendar ritual?

Amir: Begin with measurement criticality. Which instruments protect people, define product quality, control energy balance, satisfy regulation or merely provide convenience? Set acceptance limits from process requirements. Choose calibration or verification intervals from stability history, environment, manufacturer guidance and risk.

Yael: An as-found result tells us whether the instrument may have been outside tolerance before adjustment.

Amir: Yes. Preserve as-found and as-left data, reference standards, uncertainty, environmental conditions, technician, procedure and configuration. If an instrument is found out of tolerance, assess the impact on past operation or product. Do not merely adjust and close the work order.

Yael: Smart diagnostics can improve maintenance.

Amir: They can. NAMUR NE 107 organizes field-device status into four broad categories: failure, function check, out of specification and maintenance required. The value is not the icons themselves; it is consistent meaning from device through asset management, control system and operator response.

Yael: A diagnostic saying “sensor out of specification” should not automatically trip the process.

Amir: Correct. Response depends on the function, diagnostic coverage and risk. Some faults demand immediate safe action, others a maintenance request, redundancy vote change or quality flag. The cause-and-effect must be engineered.

Yael: What are common hidden failures?

Amir: Frozen value, biased value, slow response, intermittent connection, wrong range, reversed scaling, wrong units, duplicated tag, stale network data, sensor substituted without correct parameters, plugged impulse line, coating, loss of purge, encoder coupling slip and software forcing.

Yael: A frozen value is dangerous because it looks calm.

Amir: Yes. Detect it through expected variability, timestamps, device status, heartbeat, redundant comparison or active proof testing where appropriate. But beware of false alarms in genuinely steady operation.

Yael: This is also where data quality should travel with the value.

Amir: Exactly. A number without status and timestamp is incomplete. Modern systems should preserve good, uncertain, bad or substituted quality semantics instead of flattening everything into one floating-point tag.

## 38:30-41:30 | Safety and hazardous-area boundaries

Yael: When does an ordinary measurement become a safety instrument?

Amir: When it participates in a defined safety function, selection and lifecycle must follow the applicable risk-based standard. For process safety instrumented systems, IEC 61511 addresses specification, design, installation, operation and maintenance. The sensor subsystem includes the process connection, sensing element, transmitter, power, wiring, diagnostics and sometimes voting logic.

Yael: So buying a transmitter with a SIL certificate does not automatically make the loop SIL capable.

Amir: Correct. Certification evidence, failure rates, systematic capability, application limits, proof-test coverage, architecture, common-cause factors and the final element all matter. The normal control transmitter may or may not be sufficiently independent from the safety function.

Yael: Hazardous areas add another dimension.

Amir: IEC 60079-0 provides general requirements for Ex equipment, and IEC 60079-11 covers intrinsic safety. Selection requires area classification, gas or dust group, temperature class, equipment protection level, ambient limits and the complete circuit parameters. An intrinsically safe sensor is not installed by label recognition alone; associated apparatus, cable capacitance and inductance, grounding and documentation matter.

Yael: And maintenance must preserve the protection concept.

Amir: Yes. Substituting a connector, barrier or cable without checking the loop can invalidate the design. The correct local adoption and current interpretations or corrigenda must be checked. This episode gives the boundary, not a hazardous-area design course.

Yael: The same discipline applies to machine safety sensors such as interlock switches and light curtains.

Amir: Exactly. They require the relevant machine risk assessment, safety architecture and validation. A normal proximity sensor should not be quietly promoted into a personnel-protection function because the PLC logic is convenient.

## 41:30-44:00 | Worked example and closing checklist

Yael: Let us solve the opening problem. The temperature jumps when the VFD accelerates. What is our sequence?

Amir: One: define whether a five-degree change in one second is physically plausible from mass, heat capacity and power. Two: compare with an independent local instrument. Three: inspect the raw input and the transmitter output to locate where the jump enters. Four: verify sensor type, extension cable, cold-junction configuration, range and units. Five: inspect routing, shielding, bonding and separation from drive cables. Six: review input isolation, filter settings, task period and trend sampling. Seven: correct the root cause, then choose only the minimum filtering required by the process.

Yael: And document the result in the loop information so the next engineer does not rediscover it.

Amir: Exactly. Now the sensor-selection questions. What quantity and location define the measurand? What range, operating point, uncertainty and dynamic response are required? Which physical principle is compatible with the medium and mechanics? What process connection, materials, environmental and hazardous-area ratings are needed? What signal, diagnostics, power and update time are required? How will installation, calibration, proof testing and replacement be performed? What happens when the measurement is bad, stale or missing?

Yael: That is much stronger than “we need a pressure sensor zero to ten bar.”

Amir: It is an engineering specification rather than a shopping request.

Yael: Our takeaway: the sensor is not the truth. It is one element in a model of the physical world.

Amir: And trustworthy control begins by knowing the limits of that model. In Episode 4 we move from sensing to action: solenoids, pneumatic and hydraulic actuators, control valves, heaters and the ways software commands become force, motion and heat.

Yael: Until then, do not smooth a signal before asking why it moved.

Amir: Thanks for listening to Control Edge.

# 8. Producer and host notes

- Keep a calm professional pace. Do not rush the metrology segment; it supports the rest of the series.

- Whenever “accuracy” is used, remind listeners that the meaning depends on the manufacturer definition and reference conditions.

- For aliasing, a wagon-wheel-looking-backwards-on-camera analogy may be used, but identify it as an analogy.

- Do not turn the vendor examples into a ranking or commercial recommendation.

- Emphasize that mechanical installation, process connection and wiring are part of the measurement system.

- Do not read numerical NE 43 limits unless they are defined in the project specification; focus on the principle and coordinated loop configuration.

- In safety and Ex discussion, stop at responsibility boundaries and direct detailed design to competent specialists and applicable adopted editions.

- Keep the VFD fault unresolved until the closing segment to preserve the narrative arc.

# 9. Engineering measurement-chain checklist

1. What exactly is the measurand, location, process state and purpose of use?

1. What are the normal range, upset, overload, operating point and required turndown?

1. What system-level uncertainty, repeatability, stability and resolution are required?

1. What response time, bandwidth, sample rate, latency and timestamp behavior are required?

1. Which physical principle is compatible with the medium, mechanics and credible failure modes?

1. What process connection, wetted materials, sealing, cleaning, vibration and maintenance access are required?

1. Which temperature, ingress, EMC, hazardous-area and safety ratings apply?

1. What signal interface, power, isolation, wiring, shielding and diagnostics are required?

1. How are scaling, units, under/over-range, quality, plausibility and substitution handled?

1. How will calibration or verification be performed, what are the acceptance limits, and what as-found/as-left evidence is retained?

1. What happens when the value is bad, frozen, stale, missing or out of specification?

1. How are spares replaced, parameters restored, revisions managed and changes documented?

# 10. Glossary

| Term | Meaning in this episode |
| --- | --- |
| Measurand | The quantity intended to be measured, defined with enough detail to identify location and conditions. |
| Transducer | A device or element that converts a physical effect into another form suitable for use or measurement. |
| Transmitter | An instrument that converts a measured input into a standardized output and may add compensation, diagnostics and communication. |
| Accuracy | A qualitative concept associated with closeness to the true quantity value; data-sheet usage must be read from the manufacturer definition. |
| Precision | Closeness of agreement among repeated indications or measured values under specified conditions. |
| Repeatability | Precision under repeatability conditions: same procedure, system, operator/location and short time interval. |
| Measurement uncertainty | A non-negative parameter characterizing the dispersion of quantity values attributed to the measurand. |
| Hysteresis | Dependence of output on the direction from which an input value is approached. |
| Drift | Change of an indication or metrological characteristic over time. |
| Bandwidth | Frequency range over which the measurement chain meets a defined response criterion. |
| Aliasing | False representation of frequency content caused by inadequate sampling and pre-sampling filtering. |
| Live zero | A non-zero signal representing the lower measurement limit, such as 4 mA in a 4-20 mA loop. |
| Quality status | Metadata indicating whether a value is good, uncertain, bad, substituted or otherwise limited. |
| As-found / as-left | Calibration results before intervention and after adjustment or service. |

# 11. Standards and source map

> How to use this list<br>Standards are revised and adopted differently by country, sector and contract. Before design or procurement, verify the applicable edition, amendments, corrigenda, interpretation sheets and local regulatory requirements.

1. IEC 62828-1:2026 - Reference conditions and procedures for testing industrial and process measurement transmitters - general procedures for all transmitter types. Official source

1. IEC 61298-1:2026 - General methods and procedures for evaluating process instrumentation other than PMTs covered by IEC 62828. Official source

1. IEC 61298-2:2026 - Tests under reference conditions for process instrumentation. Official source

1. IEC 61298-3:2026 - Tests for effects of influence quantities on process instrumentation. Official source

1. JCGM 200:2012 (VIM) - International Vocabulary of Metrology - basic and general concepts and associated terms. Official source

1. JCGM 100:2008 and Amendment 1:2026 - Guide to the Expression of Uncertainty in Measurement and the 2026 amendment on nonlinearity in measurement models. Official source

1. IEC 61326-1:2020 - EMC requirements for electrical equipment for measurement, control and laboratory use. Official source

1. IEC 60751:2022 - Industrial platinum resistance thermometers and platinum temperature sensors. Official source

1. IEC 60584-1:2013 - Thermocouple reference functions and tolerances. Official source

1. IEC 60584-3:2021 - Thermocouple extension and compensating cables - tolerances and identification. Official source

1. IEC 60947-5-2:2019 - Requirements for inductive, capacitive, ultrasonic, photoelectric and magnetic proximity switches. Official source

1. IEC 60947-5-7:2024 - Requirements for proximity devices with analog or corresponding digital-value outputs. Official source

1. IEC 61131-9:2022 - Single-drop digital communication interface for small sensors and actuators, commonly known as IO-Link. Official source

1. FieldComm Group - HART technology - Official overview of simultaneous 4-20 mA analog and FSK digital HART communication. Official source

1. NAMUR NE 43 - Standardization of signal levels for failure information from digital transmitters with analog output. Official source

1. NAMUR NE 107 - Self-monitoring and diagnostics of field devices: Failure, Function Check, Out of Specification and Maintenance Required. Official source

1. ANSI/ISA-5.1-2024 - Instrumentation and Control - Symbols and Identification. Official source

1. IEC 60079-0:2026 - General requirements for Ex Equipment and Ex Components in or associated with explosive atmospheres. Official source

1. IEC 60079-11:2023 - Equipment protection by intrinsic safety “i”; current corrigenda and interpretation sheets also need review. Official source

1. IEC 61511-1:2016+A1:2017 - Safety instrumented systems lifecycle requirements for the process industry sector. Official source

# 12. Episode quality gate

- The listener can draw the complete chain from measurand to controller tag, quality and timestamp.

- Accuracy, precision, repeatability and uncertainty are not presented as synonyms.

- Calibration, adjustment and verification are explicitly separated.

- Dynamic response, filtering and aliasing are connected to control and alarm behavior.

- Sensing technologies are selected by physical principle and process conditions rather than slogans.

- 4-20 mA, HART and IO-Link are described accurately without treating them as mutually exclusive replacements.

- Installation, wiring, shielding, scaling and historian behavior are part of the same chain.

- Safety and Ex receive clear responsibility boundaries without pretending to provide certified design.

- The ending creates a direct bridge to Episode 4 on actuators and final control elements.
