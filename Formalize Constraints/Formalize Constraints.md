# Task 2 — Formalize Constraints

The following constraints are expressed using logical notation.

### Symbols Used

| Symbol | Meaning |
|---|---|
| `Train_Present` | A train is currently present at the crossing |
| `Train_Approaching` | A train is approaching the crossing |
| `Barrier_Open` | The barrier is open |
| `Barrier_Closed` | The barrier is closed |
| `Warning_Active` | Warning lights/alarms are active |
| `Sensor_Failure` | A critical sensor has failed |
| `Communication_Lost` | Communication with the control system is lost |
| `Incorrect_Sensor` | Sensor readings are incorrect or conflicting |
| `Emergency` | An emergency condition exists |
| `Train_Permitted` | The train is permitted to pass |
| `Barrier_Failure` | The barrier has failed |
| `Critical_Fault` | A critical safety fault is active |
| `Safe_Mode` | System is operating in safe mode |
| `Train_Cleared` | The train has completely cleared the crossing |

---

## Formal Constraints

### C1 — Barrier must not open when a train is present

**Formal Expression:**

```text
Train_Present → ¬Barrier_Open
