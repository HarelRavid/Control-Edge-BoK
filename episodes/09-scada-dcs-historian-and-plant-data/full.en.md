---
episode: 9
language: en
title: "SCADA, DCS, Historians and Plant Data Infrastructure"
target_duration: "40-45 minutes"
status: completed
extracted_from: docx
---

> CONTROL EDGE \| EPISODE 9<br>SCADA, DCS, Historians and Plant Data Infrastructure<br>From live control values to trustworthy operational history<br>Architecture, timestamps, quality, compression, availability, context, cybersecurity and integration

| Audience | Mechanical, process, manufacturing, instrumentation, data and automation engineers |
| --- | --- |
| Target duration | 40-45 minutes |
| Format | Dialogue between Yael, a young mechanical engineer, and Amir, a senior process and controls engineer |
| Core example | A multi-skid utility system whose SCADA values disagree after a network outage |
| Deliverable | Full script + NotebookLM prompt + architecture map + checklist + sources |

Educational material. It does not replace system architecture, cybersecurity risk assessment, data-governance decisions, vendor instructions, validation, or the contractually applicable editions of standards.

# 1. Pre-production alignment check

- The episode continues directly from Episode 8: a truthful local HMI still needs trustworthy supervisory data, time, quality and context at plant level.

- SCADA, DCS and historian are treated as architectural roles, not as rigid product labels; modern platforms often combine several roles.

- The episode stays above the millisecond control loop. A historian or dashboard is not presented as a substitute for deterministic controller logic.

- Data integrity includes value, engineering unit, source, timestamp, quality, identity, configuration version and processing history.

- The closing prepares Episode 10 on process control, PID and loop performance.

> Standards freshness check - August 2026<br>The standards map was rechecked in August 2026. Key current references include IEC 62541-1:2025 and the 2025-2026 OPC UA revisions, IEC 62264-2:2026, ANSI/ISA-95.00.01-2025, IEC 62682:2022, IEC 62381:2024, IEC 62443-2-1:2024 and IEC 61512-1:2026. The episode does not imply that one standard defines every historian or DCS implementation.

# 2. Episode objectives

- Distinguish HMI, SCADA, DCS, historian, MES and ERP by responsibility and time horizon.

- Map a resilient supervisory architecture from controllers to acquisition servers, operator clients, historians and enterprise interfaces.

- Explain source timestamps, server timestamps, sequence of events, data quality and clock synchronization.

- Explain sampling, deadband, compression, interpolation and aggregates without confusing stored data with physical truth.

- Design buffering, store-and-forward, redundancy, backup, restore, retention, RPO and RTO around credible failure scenarios.

- Add context through assets, equipment hierarchy, units, metadata, batches, events and configuration version.

- Separate process history, alarm history, event journals and audit trails.

- Apply cybersecurity boundaries, identities, least privilege and controlled northbound integration.

# 3. Timing and segment plan

| Time | Segment | Purpose |
| --- | --- | --- |
| 00:00-03:00 | Cold open: three screens, three answers | Show how stale, delayed and reprocessed data can look plausible but disagree. |
| 03:00-07:00 | SCADA, DCS, historian and MES | Define architectural roles and time horizons without relying on marketing labels. |
| 07:00-11:00 | The plant data path | Map controllers, acquisition, supervisory servers, clients, historians and enterprise interfaces. |
| 11:00-15:00 | DCS versus SCADA | Compare integrated process control with supervisory control of autonomous or distributed assets. |
| 15:00-20:00 | Timestamp and quality | Explain source time, server time, data age, sequence of events and clock discipline. |
| 20:00-25:00 | Historian fundamentals | Explain sampling, deadband, compression, raw storage, interpolation and aggregates. |
| 25:00-29:30 | Outages and availability | Design buffering, store-and-forward, redundancy, failover, backup and restore. |
| 29:30-34:00 | From tags to context | Add units, assets, equipment hierarchy, batches, events and versioned metadata. |
| 34:00-37:30 | Alarms, events and audit | Separate operator alarms, process events, sequence-of-events records and change history. |
| 37:30-41:00 | Northbound integration | Connect MES, ERP, analytics and cloud without surrendering control-system boundaries. |
| 41:00-43:30 | Cybersecurity and lifecycle | Apply zones, conduits, identities, patching and monitored remote access. |
| 43:30-45:00 | Acceptance checklist and bridge | Turn the case into a reusable specification and prepare the PID episode. |

# 4. Plant information architecture map

| Layer | Primary responsibility | Typical horizon | Engineering boundary |
| --- | --- | --- | --- |
| Controller / DCS control node | Deterministic control, interlocks, sequencing and local fallback | Milliseconds to seconds | Do not depend on historian availability for basic control. |
| Acquisition / gateway | Normalize protocols, preserve timestamps and quality, buffer data | Sub-second to seconds | Avoid uncontrolled direct polling from many clients. |
| SCADA supervisory services | Plant or site visualization, commands, alarms, coordination | Seconds to minutes | Supervisory command must have ownership, feedback and safe failure behavior. |
| DCS system services | Integrated engineering, process libraries, operator environment and redundancy | Milliseconds to hours | Product boundaries vary; verify what remains operational during server loss. |
| Historian | Time-series retention, retrieval, event frames, calculations and reporting | Seconds to years | Stored values may already be sampled, filtered or compressed. |
| MES / operations management | Production execution, genealogy, quality, work and material context | Minutes to shifts | Use controlled interfaces and a shared information model. |
| ERP / business systems | Planning, logistics, finance and enterprise master data | Hours to months | Do not make plant safety depend on enterprise connectivity. |

> Data trust rule<br>A trustworthy record is not only a number. It is value + engineering unit + source + source timestamp + arrival timestamp + quality/status + asset context + configuration version + processing history. If one element is missing, the system should communicate the limitation rather than silently presenting certainty.

# 5. NotebookLM production prompt

Create an English-only audio episode of 40-45 minutes using only the uploaded source pack and this document. Use two hosts: Yael, a young mechanical engineer who asks practical questions about equipment, commissioning and failure behavior; and Amir, a senior process and controls engineer who explains architecture, operations and lifecycle trade-offs. Make the exchange sound like two engineers investigating a real plant incident, not a lecture read by alternating voices.

Use the continuous case of a utility system with three skids. After a network outage, the local HMI shows current values, the SCADA overview shows a smooth but stale trend, and the historian report shows backfilled data with different timestamps. Give Yael approximately 45% of the speaking time and Amir 55%. Yael should challenge phrases such as real time, raw data, redundant, single source of truth and no data loss. Amir should answer with measurable requirements, failure modes and verification tests.

Expand every acronym the first time it appears. Distinguish standards from product implementation. Do not invent standard clauses, vendor capabilities, performance values or certifications. State that example periods, retention times, deadbands and recovery objectives are illustrative. Explain that modern SCADA, DCS and historian products overlap, so selection must be based on responsibilities and tested behavior rather than labels.

Cover architecture, SCADA versus DCS, time and quality, historian sampling and compression, interpolation, store-and-forward, redundancy, backup and restore, RPO and RTO, context and ISA-95, OPC UA information semantics, alarms/events/audit, MES/ERP/cloud integration, cybersecurity and acceptance testing. End with a ten-question checklist and a clear transition to Episode 10 on process control, PID and loop performance.

# 6. Full episode script

## 00:00-03:00 | Cold open - three screens, three answers

Amir: It is six fifteen in the morning after a forty-minute network outage. The utility skid is running again. On the local panel, discharge pressure is 5.8 bar and flow is 42 cubic metres per hour. On the SCADA overview, pressure is 5.1 bar and the flow trend is perfectly smooth. In the morning report, the historian shows 5.6 bar at the same clock time and a sudden burst of thirty values arriving together.

Yael: Which screen is wrong?

Amir: That is the trap. Each screen may be faithfully showing a different representation. The local HMI reads the controller now. The SCADA server may be displaying the last good value received before the outage. The historian may have accepted buffered values after communication returned, but those records could carry source timestamps, server timestamps or arrival timestamps depending on configuration. The smooth trend may be interpolation across a gap, not measurement.

Yael: So three credible-looking displays can disagree without any one database being corrupted.

Amir: Exactly. The engineering failure is that the system does not make age, quality, source and processing visible. A number without its data lineage can become a confident lie.

Yael: And the operator may act on the green number because it looks precise.

Amir: Today we follow the value from the controller through SCADA or DCS services into the historian and upward to manufacturing and business systems. We will ask what each layer owns, what happens during an outage, how time is established, what “raw” really means, and how to prove that the history can be trusted.

Yael: Then the core question is not “which software do we buy?” It is “what truth must survive each failure?”

Amir: That is the right opening requirement.

## 03:00-07:00 | SCADA, DCS, historian and MES are roles

Yael: Let us clean up the vocabulary. People call a local touchscreen SCADA, call a plant SCADA a DCS, and sometimes call the historian the database inside either one.

Amir: Product suites blur the names, so define the responsibility. A Human-Machine Interface, or HMI, is the interaction surface. Supervisory Control and Data Acquisition, or SCADA, usually coordinates and supervises multiple controllers or remote assets, collects data, presents alarms and trends, and allows authorized supervisory commands. The field controllers should normally remain capable of safe local operation if the supervisory layer is unavailable.

Yael: A Distributed Control System?

Amir: A DCS is commonly selected for process plants that need integrated control engineering, process-control libraries, operator stations, alarm management, historian interfaces and high-availability patterns under one system architecture. Control is distributed among controllers or nodes, but engineering and operations are coordinated as a system. That is a tendency, not a universal legal definition.

Yael: And the historian?

Amir: The historian is optimized for time-oriented industrial records: values, timestamps, status, events, calculations and retrieval over long periods. It is not merely a relational database with a table named Tags. It typically manages high write rates, time-range queries, compression, aggregates, asset context and continuity through communication interruptions.

Yael: MES is above that?

Amir: Manufacturing Execution System, or more broadly Manufacturing Operations Management, coordinates production work: schedules, work orders, material, genealogy, quality, performance and sometimes maintenance. ISA-95 and IEC 62264 give us useful terminology for boundaries and information exchange between manufacturing operations and enterprise systems.

Yael: So the hierarchy is not about prestige. It reflects different decisions and time horizons.

Amir: Correct. A controller decides whether a valve may open now. SCADA helps an operator supervise a site. A historian supports diagnosis and evidence. MES asks what was produced, with which material and under which conditions. ERP plans resources and business activity. When one layer begins silently owning another layer’s decision, failures become difficult to predict.

## 07:00-11:00 | The plant data path

Yael: Walk me through one pressure value from the transmitter to a monthly report.

Amir: The transmitter produces a measured value and status. The input module or device network delivers it to the controller. The controller scales it, validates it and may expose both the process variable and diagnostic state. An acquisition server, gateway or native DCS service subscribes to or polls that data. It should preserve the source identity, engineering unit, quality and timestamp when available.

Yael: Then the SCADA server distributes it to clients?

Amir: Usually through a managed server layer rather than allowing every workstation to hammer the controller directly. The supervisory service may maintain current values, command services, alarms and user sessions. A historian collector receives selected values and events, applies configured collection rules and writes them to durable storage. Reports or analytics then query the historian rather than repeatedly reading live controllers.

Yael: Why is direct polling from every application dangerous?

Amir: It multiplies connections, creates inconsistent scan rates, makes troubleshooting harder and can load controllers or networks unpredictably. It also produces competing definitions. One dashboard scales pressure in bar, another in kilopascals, a third applies its own bad-quality rule. A governed acquisition and semantic layer reduces that drift.

Yael: But centralization creates a single point of failure.

Amir: Only if poorly designed. We separate the functions that must continue. Basic control stays in controllers. Acquisition can be redundant or buffered. Supervisory clients can reconnect. Historians can use redundant collectors and archives. Northbound interfaces can be isolated through an industrial demilitarized zone, or IDMZ. The objective is graceful degradation: losing a report should not stop the plant; losing the supervisory server should not erase local control; losing a network link should not silently convert old data into current data.

Yael: That means the architecture diagram must show data direction, command direction and failure boundaries.

Amir: Yes, plus identity boundaries, time sources, buffering locations, ownership of configuration and the recovery path. A line labelled Ethernet is not an architecture.

## 11:00-15:00 | DCS versus SCADA - selection by behavior

Yael: Suppose I am designing a chemical plant with several packaged skids. Do I choose DCS or SCADA?

Amir: Start with control philosophy and lifecycle. If the plant needs hundreds of interacting regulatory loops, standardized faceplates, integrated alarm configuration, controller redundancy, plant-wide engineering and online maintenance under one governed system, a DCS architecture may reduce integration risk. If assets are geographically dispersed or independently controlled, communications are intermittent, and the central role is supervision, telemetry and coordination, SCADA may be the natural center.

Yael: What about a factory with high-speed machines and a central control room?

Amir: Machine PLCs should retain their deterministic sequencing and motion. A SCADA or manufacturing platform can supervise production areas, collect alarms and history, and coordinate recipes. Forcing a central server to execute machine interlocks would create a fragile timing dependency.

Yael: Modern DCS products can control remote skids, and SCADA platforms can provide redundancy, objects and integrated engineering. So the feature lists overlap.

Amir: They do. Replace the label question with acceptance questions. Which functions continue if an operator server fails? Can controllers run without the engineering server? How are changes propagated and audited? Are alarm priorities configured once or copied? How is time synchronized? What is the maximum data age shown after a link failure? How are remote sites buffered? What is the tested failover time? Can a replacement workstation be restored from a controlled baseline?

Yael: Also, who maintains it for twenty years?

Amir: Exactly. A beautiful architecture that requires rare specialists for every tag change may be unsuitable. Lifecycle, patching, licensing, virtualization support, spare strategy, cybersecurity support and vendor independence all matter. A system is not integrated because the same logo appears on every screen; it is integrated when responsibilities, data models and failure behavior are coherent.

## 15:00-20:00 | Time, quality and the age of a value

Yael: Let us return to the outage. Which timestamp should the historian store?

Amir: Ideally the record preserves the source timestamp - when the data source says the value was measured or produced - and also enough information to know when the server received or processed it. OPC UA distinguishes source timestamp and server timestamp, and associates a StatusCode with the value. That matters when data are buffered and arrive late.

Yael: Give me a mechanical example.

Amir: A vibration monitor captures a peak at 10:02:15.200 while the network is down. It forwards the sample at 10:07. If the historian stores only arrival time, the event appears five minutes late and may no longer align with the motor trip. If it stores the source time but does not mark delayed arrival, analysts may assume the value was available to the operator in real time. Both facts matter.

Yael: And quality is more than good or bad.

Amir: Yes. Quality can indicate good, uncertain or bad, with reasons such as communication failure, sensor fault, out of service, local override or last usable value. The client must not treat a bad or uncertain value as ordinary data. A trend should show gaps or quality changes instead of drawing a smooth line that implies measurement continuity.

Yael: Clock synchronization becomes part of process evidence.

Amir: Absolutely. Specify the plant time architecture: authoritative sources, Network Time Protocol or Precision Time Protocol where needed, time zones, daylight-saving handling, UTC storage, leap-second behavior if relevant, and monitoring of clock offset. Sequence-of-events applications may require much tighter synchronization than ordinary historian trends.

Yael: What is data age?

Amir: The elapsed time between the moment represented by the value and now. A value can have good quality but be too old for the current decision. The SCADA screen should therefore distinguish quality from freshness. After reconnect, the system must not paint the last known value as live without showing its age.

Yael: So every specification should ask: who stamped the value, how accurate was that clock, and what did the system know at the time?

Amir: Precisely.

## 20:00-25:00 | Historian fundamentals - raw is not the physical world

Yael: Engineers often ask for all raw data forever. Is that a meaningful requirement?

Amir: Not until we define raw. The controller may update a value every ten milliseconds. The acquisition server may sample it every second. A deadband may suppress small changes. A historian compression algorithm may retain only points needed to represent the trend within a configured deviation. The stored record is raw relative to the historian, but it is not every physical sample.

Yael: Deadband and compression are the same?

Amir: They can be related but should be separated conceptually. An acquisition or exception deadband decides whether a new value is reported. Compression decides whether a reported value needs to be archived after considering surrounding points. A display deadband may only affect visualization. Using one word for all three hides data loss mechanisms.

Yael: Why compress at all? Storage is cheap.

Amir: Storage is only one cost. High-frequency data increase network load, indexing, backup size and query time. Intelligent collection can preserve useful shape with far fewer records. But the settings must follow the use case. A one-degree compression deviation may be acceptable for room temperature and unacceptable for a narrow quality limit. Short spikes, extrema and trip precursors can disappear if the rule is poorly chosen.

Yael: And interpolation?

Amir: When a query asks for a value every minute, the historian may interpolate between stored points, return stepped values, calculate averages, minima, maxima or time-weighted results. Those are derived values, not measurements. A report must identify the retrieval method and quality of the interval. Averaging across bad-quality gaps can create a precise answer with weak evidence.

Yael: Then “show me the trend” is underspecified.

Amir: Ask for time range, time zone, raw versus interpolated, sampling interval, aggregate method, boundary treatment, bad-quality handling and whether late data can revise earlier results. For regulated or contractual records, preserve the query definition and calculation version as well as the values.

Yael: The historian is therefore an engineering system, not an infinite memory card.

Amir: Exactly. Collection rules are part of the measurement design.

## 25:00-29:30 | Outages, store-and-forward and availability

Yael: The sales presentation says “no data loss.” What should I ask next?

Amir: Ask which failure, for how long, and under which storage capacity. Store-and-forward means a collector or gateway buffers records when the destination is unavailable and forwards them later. It reduces loss during a network or server outage, but the buffer is finite. It also needs rules for order, duplicates, clock changes, corrupt records and what happens when the buffer fills.

Yael: Redundant historian servers solve everything?

Amir: Redundancy addresses specific component failures. Two servers can share one power source, one switch, one storage array or one corrupted configuration. Define failure domains. Determine whether collectors can write to both nodes, how clients discover the active service, how split-brain is prevented, and how failback is controlled.

Yael: We should define Recovery Point Objective and Recovery Time Objective.

Amir: Yes. RPO is the acceptable amount of data loss measured in time. RTO is the acceptable time to restore the service. They are business and operational requirements, not properties guessed after purchase. A safety investigation historian may need a very small RPO; a monthly energy dashboard may tolerate more.

Yael: Backup is not the same as redundancy.

Amir: Correct. Redundancy supports continuity. Backup protects against deletion, corruption, ransomware, configuration error and longer disasters. A backup that has never been restored is an assumption. Test restoration of software, configuration, certificates, identities, tag databases, archives, calculations and client connectivity. Document dependency order.

Yael: And retention?

Amir: Define what is kept, at which resolution, for how long, under which legal or quality obligations, and how deletion is controlled. Long-term aggregates can coexist with shorter high-resolution retention. But never delete the only evidence needed to interpret the aggregate - such as quality flags, units or configuration history.

Yael: During an outage, what should the operator see?

Amir: Clear loss-of-communication status, last update time, data age and affected scope. Not a calm green plant frozen in the past.

## 29:30-34:00 | From tags to operational context

Yael: A historian with two hundred thousand tags still feels hard to use. Why?

Amir: Because tag names are not context. A name such as PT_4317.PV may tell an instrumentation engineer something, but an analyst also needs asset, location, service, unit, range, engineering unit, equipment state, batch, product, maintenance status and configuration version.

Yael: This is where ISA-95 and equipment hierarchies help.

Amir: Yes. IEC 62264 and ISA-95 provide models and terminology for enterprise-control integration, equipment hierarchy and manufacturing operations information. The current standards continue to evolve, including the 2026 update to IEC 62264-2. They do not dictate one database schema, but they help teams agree what an enterprise, site, area, work unit, equipment resource or operations record means.

Yael: OPC UA information models also add semantics.

Amir: OPC UA can represent objects, variables, relationships, methods, events, engineering units, status and role permissions in an address space. Companion specifications can define domain models. The benefit is not the protocol name by itself; it is consistent meaning carried across interfaces.

Yael: What about batch production?

Amir: IEC 61512-1:2026 refreshes the batch-control models and reinforces separation between recipe procedural elements and equipment procedural elements. For history, that enables us to relate values to unit procedures, operations, phases and batches rather than only to clock time.

Yael: Context can change. A transmitter may be replaced or a tag may be rescaled.

Amir: Therefore metadata needs effective dates and version control. A pressure value from last year must be interpreted with the range, unit, calibration state and equipment mapping that applied then, not today’s configuration. Asset context is historical data too.

Yael: So “single source of truth” should not mean one giant database.

Amir: Right. It should mean governed ownership, authoritative definitions and traceable synchronization. Different systems can remain authoritative for different objects: the controller for live state, the maintenance system for work history, MES for genealogy, ERP for material master, and the historian for time-series records.

## 34:00-37:30 | Alarms, events, sequence of events and audit

Yael: The historian stores values. Does it also store alarms?

Amir: Often yes, but separate the record types. An alarm is an operator notification requiring awareness or response. IEC 62682 treats alarm management as a lifecycle, including philosophy, rationalization, design, operation, maintenance and performance monitoring. An alarm historian records alarm states, acknowledgements, shelving and related operator actions.

Yael: An event is broader.

Amir: Correct. Pump started, recipe selected, mode changed, communication lost and report generated are events, but not all should be alarms. A sequence-of-events, or SOE, record is optimized to preserve the order of discrete changes, often with precise source timestamps. An audit trail records who changed what, when, from where and under which authorization.

Yael: Why not put everything in one chronological list?

Amir: Because purpose and required integrity differ. The operator needs actionable alarms. The investigator needs ordered events and configuration changes. The quality system may need electronic records and signatures. Mixing them without type, source and identity makes the list noisy and legally ambiguous.

Yael: What should be correlated during our outage?

Amir: Controller communication status, gateway buffer state, server failover events, clock offset alarms, operator commands, acknowledgement activity, historian backfill records and configuration changes. With a shared time basis and identities, we can reconstruct what happened. Without them, teams argue from screenshots.

Yael: Alarm history itself needs performance metrics.

Amir: Yes. Flood rate, standing alarms, chattering, stale acknowledgements and bad actors should be measured. But do not let a historian query replace the alarm-management process. The data support governance; they do not create it automatically.

## 37:30-41:00 | Northbound integration without losing control boundaries

Yael: Management wants all plant data in the cloud and in the enterprise data lake. What is the engineering response?

Amir: Start with use cases and data contracts. Which data, at what resolution, with what latency, quality, context and retention? Who consumes it? Is the flow read-only or are commands returned? A dashboard that needs hourly energy totals should not receive direct controller access.

Yael: We can publish through OPC UA, APIs, messaging or files.

Amir: Yes. OPC UA supports structured client-server and PubSub patterns. IEC 62541-14:2026 defines the PubSub model. MQTT is widely used as a transport pattern, often with an industrial namespace convention, but the topic tree alone does not guarantee semantics or security. REST APIs and database replicas may suit other cases. Select the interface by contract, not fashion.

Yael: Where does the industrial DMZ fit?

Amir: It separates zones and mediates exchange between control networks and enterprise or cloud environments. Historians may replicate outward; jump hosts, proxies, brokers or file-transfer services can prevent direct inbound sessions to controllers. IEC 62443-3-2 uses zones and conduits in security risk assessment, while IEC 62443-2-1:2024 addresses the asset owner’s operational security program.

Yael: And writing back from enterprise systems?

Amir: Treat it as a command path, not data integration. Define authorization, validation, rate limits, ownership, interlocks, expiry, acknowledgement and fallback. A production order may be transferred to MES, then an approved recipe version to the control system through a controlled workflow. An analyst notebook should not write a pump speed directly.

Yael: Data lakes often copy records without industrial quality flags.

Amir: That destroys meaning. Preserve source time, quality, unit, asset identity and transformation lineage. If the enterprise platform normalizes or resamples data, retain the method and version. Otherwise the organization gains more data and less evidence.

## 41:00-43:30 | Cybersecurity and lifecycle

Yael: SCADA and historians live for decades. How do we secure them without destabilizing operations?

Amir: Through an asset-owner security program, architecture and controlled lifecycle. Inventory components, firmware, operating systems, interfaces, accounts, certificates and dependencies. Segment zones and conduits. Apply least privilege and role-based access. Use individual identities for operators, engineers and services. Monitor remote access and remove standing vendor accounts where possible.

Yael: Patch everything immediately?

Amir: Not blindly. Assess vulnerabilities, exposure, compensating controls, vendor support, test evidence and operational risk. Maintain a test environment or representative validation method. Back up before change, define rollback, and verify the application afterward. Unsupported systems need an explicit risk treatment plan, not denial.

Yael: Certificates and service accounts are easy to forget.

Amir: They are common outage causes. Track expiry, ownership and renewal. Protect secrets. Avoid shared administrator passwords embedded in scripts. Log privileged actions and review them. Ensure backups include certificate material where appropriate, but protect private keys separately.

Yael: What about availability attacks, such as a report query exhausting the historian?

Amir: Resource availability is a security requirement too. Separate workloads, set query limits, monitor queues and disk capacity, and protect control-facing services from analytics bursts. A cybersecure system must remain operable, not merely encrypted.

Yael: IEC 62443 gives the framework, but implementation still depends on the system under consideration.

Amir: Exactly. Standards organize the questions and responsibilities. The project must translate them into tested requirements.

## 43:30-45:00 | Acceptance checklist and bridge

Yael: Let us close with ten questions. One: which system is authoritative for each value, command, alarm, event and configuration item?

Amir: Two: are source timestamp, server or arrival time, quality and data age preserved and visible? Three: what collection, deadband, compression and interpolation rules apply to each use case? Four: what happens during loss of controller, network, collector, server, storage, time source and identity service?

Yael: Five: where is buffering located, how long does it last, and what happens when it fills? Six: what are the RPO, RTO, redundancy, backup and tested restore requirements? Seven: are units, assets, batches, events and configuration versions historically traceable?

Amir: Eight: are alarms, events, SOE records and audit trails separated and correlated correctly? Nine: are northbound and write-back interfaces governed through zones, conduits, identities and data contracts? Ten: do FAT, FIT, SAT and SIT tests prove normal operation, failover, backfill, stale-data indication, clock error and recovery?

Yael: In our opening incident, the fix is not to choose one screen as the winner. It is to make each representation explicit and test the whole chain.

Amir: Exactly. Episode 10 moves back into the control layer: process dynamics, feedback, PID, tuning, saturation, anti-windup and the difference between a loop that looks stable and one that performs well.

# 7. Engineering design and acceptance checklist

- Assign an authoritative owner for live values, commands, alarms, events, master data and configuration.

- Specify source timestamp, arrival/server timestamp, quality, freshness and clock accuracy requirements.

- Define acquisition rate, deadband, compression, interpolation and aggregate rules per use case.

- Document behavior during loss of controller, network, collector, server, storage, time and identity services.

- Size and test buffers; define duplicate, ordering, overflow and late-data behavior.

- Define redundancy, failure domains, RPO, RTO, backup, offline copy and tested restoration.

- Maintain versioned units, ranges, assets, equipment hierarchy, batches and transformation lineage.

- Separate and correlate process values, alarms, events, SOE and audit records.

- Govern enterprise and cloud interfaces with zones, conduits, identities and explicit write-back workflows.

- Test normal, degraded, failover, backfill, stale-value, clock-error and recovery scenarios during FAT/FIT/SAT/SIT.

# 8. Glossary

| Term | Meaning |
| --- | --- |
| SCADA | Supervisory system for monitoring, data acquisition and authorized control across multiple controllers or sites. |
| DCS | Integrated distributed process-control architecture with coordinated engineering and operations services. |
| Historian | Industrial time-series platform for collecting, retaining, contextualizing and retrieving process records. |
| Source timestamp | Time assigned by the original data source to the value or event. |
| Server timestamp | Time assigned by the server when it received or processed the value. |
| Data quality | Status describing whether a value is good, uncertain or bad and why. |
| Data age | Elapsed time between the represented measurement time and the present decision. |
| Deadband | Threshold that suppresses reporting or processing of changes below a configured magnitude. |
| Compression | Historian rule that reduces stored points while attempting to preserve useful trend shape. |
| Interpolation | Calculated estimate between stored points; not a direct measurement. |
| Store-and-forward | Local buffering during destination outage followed by later delivery. |
| RPO | Recovery Point Objective - maximum acceptable data loss expressed as time. |
| RTO | Recovery Time Objective - maximum acceptable service restoration time. |
| SOE | Sequence of Events - ordered discrete event record using precise timestamps. |
| Data lineage | Traceable source, transformations, versions and ownership of a data record. |

# 9. Standards and source map

The standards below provide frameworks and definitions. Product documentation is included only as an implementation example; contractual applicability and exact editions must be confirmed for each project.

- IEC 62541-1:2025 - OPC unified architecture - Overview and concepts

- IEC 62541-3:2025 - OPC UA Address Space Model

- IEC 62541-6:2025 - OPC UA Mappings

- IEC 62541-14:2026 - OPC UA PubSub

- OPC Foundation - Data Access quality and timestamps

- ANSI/ISA-95.00.01-2025 / IEC 62264-1 Mod - Models and terminology

- IEC 62264-2:2026 - Objects and attributes for enterprise-control integration

- IEC 62264-3:2016 - Manufacturing operations management activity models

- IEC 61512-1:2026 - Batch control models and terminology

- IEC 62682:2022 - Management of alarm systems for process industries

- IEC 62381:2024 - FAT, FIT, SAT and SIT for process automation systems

- IEC 62443-2-1:2024 - Asset owner security program requirements

- IEC 62443-3-2:2020 - Security risk assessment, zones and conduits

- IEC 62443-3-3:2013 - System security requirements and security levels

- Ignition 8.3 User Manual - Store and Forward and Tag Historian

- AVEVA documentation - PI compression configuration example

# 10. Bridge to the next episode

Episode 10 moves from plant data back into the physical process: process dynamics, open-loop and closed-loop behavior, PID structure, tuning, saturation, anti-windup, cascade and the practical tests that separate a stable loop from a high-performing loop.
