---
tags:
  - cybersecurity
  - python
  - programming
  - conditional-statements
  - logical-operators
  - control-flow
  - google-cert
  - module-01
  - course-07
aliases:
  - Conditional Statements in Python
  - Python Conditionals
  - if, elif, and else Statements
  - Logical Operators in Python
  - Comparison Operators in Python
  - Python Control Flow
---

> [!abstract] Conditional Statements & Logical Operators
> **Conditional statements** control the execution flow of Python programs by evaluating expressions against Boolean criteria (`True` or `False`). By utilizing the **`if`**, **`elif`**, and **`else`** keywords in conjunction with **comparison operators** and **logical operators** (`and`, `or`, `not`), security analysts can automate decision-making—such as evaluating HTTP status codes, filtering firewall events, and flagging anomalous network access.

---

# How Conditional Statements Work

> [!info] Definition
> A **conditional statement** evaluates an expression to determine whether it meets defined criteria:
> - If the condition evaluates to **`True`**, the associated indented block of code **executes**.
> - If the condition evaluates to **`False`**, Python **skips** the block and proceeds down the execution chain.

```
┌────────────────────────────────────────────────────────┐
│               CONDITIONAL LOGIC FLOW                   │
├────────────────────────────────────────────────────────┤
│                       [Condition]                      │
│                            │                           │
│                 ┌──────────┴──────────┐                │
│             Is True?               Is False?           │
│                 │                      │               │
│                 ▼                      ▼               │
│       [Execute Code Block]       [Skip / Go Next]      │
└────────────────────────────────────────────────────────┘
```

---

# Comparison Operators

Conditions rely on **comparison operators** to evaluate relationships between numeric, string, or boolean values:

| Operator | Meaning | Example Expression | Evaluates To | Common Security Use Case |
| :--- | :--- | :--- | :--- | :--- |
| `>` | Greater than | `failed_logins > 3` | `True` if count exceeds 3 | Brute-force detection threshold |
| `<` | Less than | `packet_size < 64` | `True` if size under 64 | Runt packet / fragment detection |
| `>=` | Greater than or equal to | `status >= 200` | `True` if status is 200+ | HTTP status code range check |
| `<=` | Less than or equal to | `status <= 226` | `True` if status is 226 or less | Successful response range cap |
| `==` | Equal to | `role == "admin"` | `True` if strings match exactly | Privilege & authentication checks |
| `!=` | Not equal to | `status != 200` | `True` if value is not 200 | Error / anomalous response check |

> [!warning] Critical Syntax Distinction: `=` vs. `==`
> - **`=` (Single Equals):** The **assignment operator**, used to store values into variables (`status = 200`).
> - **`==` (Double Equals):** The **comparison operator**, used to check equality (`status == 200`).

---

# Anatomy of an `if` Statement

Every conditional statement begins with the mandatory keyword **`if`**.

```python
if status == 200:
    print("OK")
```

An `if` statement consists of two essential structural components:

```
┌────────────────────────────────────────────────────────────────────────┐
│                        ANATOMY OF AN IF STATEMENT                      │
├────────────────────────────────────────────────────────────────────────┤
│  HEADER:   if status == 200:  ◄─── Starts with 'if', ends with ':'     │
│  BODY:         print("OK")    ◄─── Indented 4 spaces (Action to take)   │
└────────────────────────────────────────────────────────────────────────┘
```

### 1. The Header
- Begins with the **`if`** keyword, followed by the condition being evaluated.
- Parentheses around the condition are optional (`if (status == 200):`), but standard Python style omits them unless required for grouping.
- **Mandatory Colon (`:`):** The header line **must always end with a colon**. Omitting the colon results in a `SyntaxError`.

### 2. The Body
- The body contains the code statement(s) that execute when the condition evaluates to `True`.
- **Indentation Rule:** All lines in the body **must be indented** (standard convention is 4 spaces). Inconsistent or missing indentation causes an `IndentationError`.

---

# Branching Conditionals: `else` and `elif`

When an initial `if` condition evaluates to `False`, Python can branch into alternative decision paths using `else` and `elif`.

```
┌────────────────────────────────────────────────────────┐
│              BRANCHING EXECUTION LADDER                │
├────────────────────────────────────────────────────────┤
│  1. Check `if condition`                               │
│     ├── True  ──► Execute `if` body ──► Exit Ladder    │
│     └── False ──► Proceed to `elif`                    │
│  2. Check `elif condition`                             │
│     ├── True  ──► Execute `elif` body ──► Exit Ladder  │
│     └── False ──► Proceed to `else`                    │
│  3. Fallback `else`                                    │
│     └── Always executes if all above evaluate to False │
└────────────────────────────────────────────────────────┘
```

---

## 1. The `else` Statement

The **`else`** statement defines a fallback block that executes **only when all preceding conditions evaluate to `False`**:

```python
status = 404

if status == 200:
    print("OK")
else:
    print("check other status")

# Output: check other status
```

- Requires a trailing colon (`else:`).
- Has no condition of its own.

---

## 2. The `elif` (Else-If) Statement

The **`elif`** keyword allows evaluating multiple sequential conditions when preceding conditions are `False`. Multiple `elif` statements can be chained together:

```python
status = 400

if status == 200:
    print("OK")
elif status == 400:
    print("Bad Request")
elif status == 500:
    print("Internal Server Error")
else:
    print("check other status")

# Output: Bad Request
```

### `elif` Short-Circuiting vs. Chained `if` Statements

| Construct | Execution Behavior | Use Case |
| :--- | :--- | :--- |
| **`if ... elif ... else`** | **Short-circuits:** As soon as one branch evaluates to `True`, Python executes its body and **skips all subsequent branches**. | Mutually exclusive outcomes (e.g., an HTTP response can only have one status). |
| **Multiple standalone `if`s** | **Evaluates all:** Python checks **every single `if` statement independently**, regardless of whether previous conditions were `True`. | Independent multi-criteria checks (e.g., checking multiple security flags independently). |

---

# Logical Operators for Compound Conditions

Logical operators combine or modify Boolean conditions to evaluate complex security criteria:

```
┌────────────────────────────────────────────────────────────────────────┐
│                       LOGICAL OPERATORS SUMMARY                        │
├──────────┬─────────────────────────────────────┬───────────────────────┤
│ OPERATOR │ EVALUATION RULE                     │ EXAMPLE               │
├──────────┼─────────────────────────────────────┼───────────────────────┤
│ `and`    │ `True` ONLY if BOTH conditions True │ `status >= 200 and ...`│
│ `or`     │ `True` if AT LEAST ONE is True      │ `code == 100 or ...`  │
│ `not`    │ Inverts Boolean result              │ `not(status == 200)`  │
└──────────┴─────────────────────────────────────┴───────────────────────┘
```

---

## 1. The `and` Operator

Requires **both conditions** on either side of the operator to evaluate to `True`.

```python
# Checking if an HTTP status falls within the successful 2xx range (200-226)
status = 201

if status >= 200 and status <= 226:
    print("successful response")

# Output: successful response
```

---

## 2. The `or` Operator

Requires **at least one condition** on either side of the operator to evaluate to `True`.

```python
# Checking if a status represents an informational response code (100 or 102)
status = 100

if status == 100 or status == 102:
    print("informational response")

# Output: informational response
```

---

## 3. The `not` Operator & Parentheses Precedence

The **`not`** operator inverts a condition's Boolean outcome (reversing `True` to `False` and `False` to `True`).

```python
# Alerting on any status code falling OUTSIDE the successful 2xx range
status = 503

if not (status >= 200 and status <= 226):
    print("check status")

# Output: check status
```

> [!note] Operator Precedence with `not`
> Parentheses are essential when using `not` with compound conditions. Python evaluates expressions enclosed in **parentheses first**. 
> - In `not (status >= 200 and status <= 226)`, Python first evaluates the `and` range check to `False`, then `not` inverts it to `True`, triggering the alert.

---

# Comprehensive Security Automation Example

```python
# Automated Security Log Triage Script
http_status = 403
user_role = "guest"
failed_attempts = 4

# Rule 1: Flag high-risk authentication failures
if failed_attempts >= 5 or (http_status == 403 and user_role == "guest"):
    print("[ALERT] Suspicious unauthorized access attempt detected.")
elif http_status == 200:
    print("[INFO] Authorized request processed successfully.")
else:
    print("[LOG] Standard non-critical event logged.")

# Output: [ALERT] Suspicious unauthorized access attempt detected.
```

---

# Key Terms at a Glance

| Term | Meaning |
| :--- | :--- |
| **Conditional Statement** | A programming construct that executes code blocks based on Boolean evaluations. |
| **Header** | The initial line of a conditional block (e.g., `if condition:`) containing the keyword, expression, and colon. |
| **Body** | The indented block of code containing instructions executed when the condition evaluates to `True`. |
| **`elif`** | Evaluates secondary conditions if preceding `if`/`elif` checks evaluate to `False`. |
| **`else`** | Catch-all fallback block executed when all previous branches are `False`. |
| **Short-Circuiting** | Halting further evaluation in a conditional ladder once a matching `True` branch executes. |
| **Logical Operator** | Keywords (`and`, `or`, `not`) used to combine or negate Boolean expressions. |

---

# Exam Tips

> [!tip] Key Takeaways for the Exam
> - **Mandatory Syntax:** Every `if`, `elif`, and `else` header **must terminate with a colon (`:`)** and have its body **indented**.
> - **Equality Check:** Use `==` to test equality; `=` is strictly reserved for variable assignment.
> - **`elif` Execution:** Only the **first** `elif` block that evaluates to `True` runs; all subsequent `elif` and `else` blocks are bypassed.
> - **Compound Logic:**
>   - `and` &rarr; All conditions must be `True`.
>   - `or` &rarr; Only one condition needs to be `True`.
>   - `not` &rarr; Inverts the Boolean outcome (`True` &rarr; `False`, `False` &rarr; `True`).
> - **Grouping with Parentheses:** Use parentheses with `not` to enforce proper evaluation order over compound expressions.

---

## Related Notes

- [[Python Variables and Naming Conventions]]
- [[Python Data Types]]
- [[Python Environments and Notebooks]]
- [[Programming and Python in Cybersecurity]]
- [[Iterative Statements in Python]]
- [[Tools and their purposes]]
- [[Logs and SIEM Tools]]
- [[Playbooks and Incident Response]]
