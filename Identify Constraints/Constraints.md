# Railway Level-Crossing System
## Software Verification Team — Constraint Analysis

### Overview

This project analyzes a railway level-crossing control system from a Software Verification perspective.

The system must safely control railway barriers, detect trains, process sensor information, activate warnings, and handle abnormal situations such as:

- Sensor failure
- Barrier failure
- Communication loss
- Incorrect sensor readings
- Emergency conditions

The purpose of this analysis is to identify system constraints, express them formally using logical notation, and identify realistic situations in which those constraints could be violated.

---

# Task 1 — Identify Constraints

The following constraints describe rules that the railway level-crossing system must always satisfy.

| Constraint ID | Constraint in Simple English | Why the Constraint is Necessary |
|---|---|---|
| C1 | The barrier must not open while a train is present at the crossing. | Prevents road traffic from entering the crossing while a train is passing. |
| C2 | The barrier must remain closed while a train is approaching the crossing. | Gives sufficient protection before the train reaches the crossing. |
| C3 | The train must not be allowed to pass when the barrier is open. | Prevents unsafe coordination between the railway and road traffic. |
| C4 | Warning lights and alarms must be activated when a train is approaching. | Warns drivers and pedestrians that a train is approaching. |
| C5 | The barrier must not open until the train has completely cleared the crossing. | Prevents vehicles from entering the crossing too early. |
| C6 | If a critical sensor fails, the system must enter a safe state. | A failed sensor may provide unreliable information about the train or crossing. |
| C7 | If communication with the control system is lost, the system must not perform unsafe operations. | Prevents dangerous decisions when reliable communication is unavailable. |
| C8 | Incorrect or conflicting sensor readings must not cause the barrier to open. | Prevents unsafe barrier operation caused by faulty sensor data. |
| C9 | An emergency condition must activate the required warning or safety response. | Ensures dangerous situations receive immediate attention. |
| C10 | The barrier must be confirmed closed before a train is permitted to pass. | Ensures the crossing is physically protected before train movement. |
| C11 | The system must detect a barrier failure when the commanded and actual barrier states are different. | Allows the system to respond when the barrier does not operate correctly. |
| C12 | The system must not allow normal operation when a critical safety fault is active. | Prevents the system from continuing normal operation during dangerous conditions. |

---
