# Task 3 — Identify Constraint Violations

This task identifies realistic situations where the formal constraints of the railway level-crossing system are violated.

A constraint violation occurs when the actual system state does not satisfy the required logical rule.

---

## C1 — Barrier Must Not Open When a Train Is Present

### Constraint

```text
Train_Present → ¬Barrier_Open
```

### Violation

```text
Train_Present = TRUE
Barrier_Open = TRUE
```

### Explanation

The train is present at the crossing, but the barrier is open. This violates the rule because the barrier must remain closed while a train is present.

---

## C2 — Barrier Must Remain Closed When a Train Is Approaching

### Constraint

```text
Train_Approaching → ¬Barrier_Open
```

### Violation

```text
Train_Approaching = TRUE
Barrier_Open = TRUE
```

### Explanation

A train is approaching the crossing, but the barrier is open. The system should have kept the barrier closed to prevent road traffic from entering the crossing.

---

## C3 — Train Must Not Pass When Barrier Is Open

### Constraint

```text
Barrier_Open → ¬Train_Permitted
```

### Violation

```text
Barrier_Open = TRUE
Train_Permitted = TRUE
```

### Explanation

The system has permitted the train to pass even though the barrier is open. This creates an unsafe condition because road traffic may still be inside or entering the crossing.

---

## C4 — Warning Must Be Active When a Train Is Approaching

### Constraint

```text
Train_Approaching → Warning_Active
```

### Violation

```text
Train_Approaching = TRUE
Warning_Active = FALSE
```

### Explanation

A train is approaching, but the warning lights and alarms are not active. The system has failed to warn road users about the approaching train.

---

## C5 — Barrier Can Open Only After the Train Has Cleared

### Constraint

```text
Barrier_Open → Train_Cleared
```

### Violation

```text
Barrier_Open = TRUE
Train_Cleared = FALSE
```

### Explanation

The barrier has opened before the train has completely cleared the crossing. This can allow vehicles or pedestrians to enter the crossing while the train is still present.

---

## C6 — Sensor Failure Must Cause Safe Mode

### Constraint

```text
Sensor_Failure → Safe_Mode
```

### Violation

```text
Sensor_Failure = TRUE
Safe_Mode = FALSE
```

### Explanation

A critical sensor has failed, but the system continues normal operation instead of entering safe mode. This is dangerous because the system may no longer have reliable information about the crossing.

---

## C7 — Communication Loss Must Prevent Unsafe Operation

### Constraint

```text
Communication_Lost → ¬Train_Permitted
```

### Violation

```text
Communication_Lost = TRUE
Train_Permitted = TRUE
```

### Explanation

Communication with the control system has been lost, but the system still permits the train to pass. The system should have prevented the operation until safe communication was restored or an appropriate fail-safe procedure was activated.

---

## C8 — Incorrect Sensor Readings Must Prevent Barrier Opening

### Constraint

```text
Incorrect_Sensor → ¬Barrier_Open
```

### Violation

```text
Incorrect_Sensor = TRUE
Barrier_Open = TRUE
```

### Explanation

The sensor readings are incorrect or conflicting, but the system opens the barrier. This is a violation because unreliable sensor information should not result in an unsafe barrier operation.

---

## C9 — Emergency Condition Must Activate Warnings

### Constraint

```text
Emergency → Warning_Active
```

### Violation

```text
Emergency = TRUE
Warning_Active = FALSE
```

### Explanation

An emergency condition has occurred, but the warning system is not activated. This could prevent drivers, pedestrians, or railway operators from receiving an important safety warning.

---

## C10 — Barrier Must Be Closed Before Train Passage

### Constraint

```text
Train_Permitted → Barrier_Closed
```

### Violation

```text
Train_Permitted = TRUE
Barrier_Closed = FALSE
```

### Explanation

The system permits the train to pass without confirming that the barrier is closed. This violates the safety requirement that the crossing must be protected before train passage.

---

## C11 — Barrier Failure Must Cause Safe Mode

### Constraint

```text
Barrier_Failure → Safe_Mode
```

### Violation

```text
Barrier_Failure = TRUE
Safe_Mode = FALSE
```

### Explanation

The barrier has failed, but the system continues normal operation. The system should enter safe mode so that further unsafe operations are prevented.

---

## C12 — Critical Fault Must Prevent Train Passage

### Constraint

```text
Critical_Fault → ¬Train_Permitted
```

### Violation

```text
Critical_Fault = TRUE
Train_Permitted = TRUE
```

### Explanation

A critical safety fault is active, but the system still permits the train to pass. This violates the safety requirement because train movement should not be authorized while a critical fault exists.

---

# Violation Summary

| Constraint ID | Violation Condition                                      | Result                                                   |
| ------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| C1            | `Train_Present = TRUE` and `Barrier_Open = TRUE`         | Barrier is open while train is present.                  |
| C2            | `Train_Approaching = TRUE` and `Barrier_Open = TRUE`     | Barrier is open while train is approaching.              |
| C3            | `Barrier_Open = TRUE` and `Train_Permitted = TRUE`       | Train is permitted while barrier is open.                |
| C4            | `Train_Approaching = TRUE` and `Warning_Active = FALSE`  | Warning system is not activated.                         |
| C5            | `Barrier_Open = TRUE` and `Train_Cleared = FALSE`        | Barrier opens before train clears.                       |
| C6            | `Sensor_Failure = TRUE` and `Safe_Mode = FALSE`          | System does not enter safe mode.                         |
| C7            | `Communication_Lost = TRUE` and `Train_Permitted = TRUE` | Train is permitted despite communication loss.           |
| C8            | `Incorrect_Sensor = TRUE` and `Barrier_Open = TRUE`      | Barrier opens despite incorrect sensor data.             |
| C9            | `Emergency = TRUE` and `Warning_Active = FALSE`          | Emergency warning is not activated.                      |
| C10           | `Train_Permitted = TRUE` and `Barrier_Closed = FALSE`    | Train is permitted without confirmed closed barrier.     |
| C11           | `Barrier_Failure = TRUE` and `Safe_Mode = FALSE`         | System continues normal operation after barrier failure. |
| C12           | `Critical_Fault = TRUE` and `Train_Permitted = TRUE`     | Train is permitted despite critical fault.               |

---

# Conclusion

The identified violations demonstrate how the railway level-crossing system can fail to satisfy its safety constraints.

Each violation can be detected by comparing the actual system state with the corresponding formal constraint.

For example:

```text
Constraint:
Train_Present → ¬Barrier_Open

Actual State:
Train_Present = TRUE
Barrier_Open = TRUE
```

Since the barrier is open while a train is present, the constraint is violated.

These violation scenarios can be used by the Software Verification Team to design test cases and verify whether the railway level-crossing system responds correctly to abnormal and unsafe situations.
