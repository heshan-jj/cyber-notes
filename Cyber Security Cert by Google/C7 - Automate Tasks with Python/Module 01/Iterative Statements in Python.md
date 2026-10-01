---
tags:
  - cybersecurity
  - python
  - programming
  - iterative-statements
  - loops
  - for-loops
  - while-loops
  - control-flow
  - google-cert
  - module-02
  - course-07
aliases:
  - Iterative Statements in Python
  - Python Loops
  - for and while Loops
  - Looping in Python
  - Loop Control with break and continue
  - Range Function in Python
---

> [!abstract] Iterative Statements & Loop Control
> An **iterative statement** (commonly called a **loop**) is a programming construct that repeatedly executes a block of instructions zero or more times based on specific criteria or sequences. In Python, security analysts rely on **`for` loops** to iterate across predefined sequences (e.g., lists of IP addresses, asset inventories, log records) and **`while` loops** to execute tasks until a dynamic condition evaluates to `False` (e.g., tracking failed login attempts). Loop flow can be finely controlled using the **`break`** and **`continue`** keywords.

---

# Understanding Iterative Statements

> [!info] Definition
> **Iteration** is the process of repeatedly executing a set of instructions. An **iterative statement** automates repetitive operations, eliminating manual execution and reducing human error in security workflows.

```
┌────────────────────────────────────────────────────────┐
│                   ITERATION FLOWCHART                  │
├────────────────────────────────────────────────────────┤
│                       [Start Loop]                     │
│                            │                           │
│                            ▼                           │
│                 ┌────────────────────┐                 │
│                 │ Evaluate Criteria/ │                 │
│                 │ Next Sequence Item │                 │
│                 └─────────┬──────────┘                 │
│                           │                            │
│                 ┌─────────┴─────────┐                  │
│             Valid/True           Done/False            │
│                 │                       │              │
│                 ▼                       ▼              │
│       ┌──────────────────┐      ┌──────────────┐       │
│       │   Execute Loop   │      │ Exit Loop &  │       │
│       │    Body Code     │      │ Continue Prg │       │
│       └─────────┬────────┘      └──────────────┘       │
│                 │                                      │
│                 └─────── Repeat ───────┘               │
└────────────────────────────────────────────────────────┘
```

Python provides two fundamental loop structures:
1. **`for` loops:** Iterate through a predetermined sequence of items or values.
2. **`while` loops:** Iterate continuously as long as a specified Boolean condition remains `True`.

---

# `for` Loops

If you need to iterate through a **specified sequence** (such as a list, tuple, dictionary, set, range, or string), use a **`for` loop**.

```python
for i in ["elarson", "bmoreno", "tshah", "sgilmore"]:
    print(i)
```

```
Output:
elarson
bmoreno
tshah
sgilmore
```

---

## Anatomy of a `for` Loop

A `for` loop consists of two distinct structural components:

```
┌─────────────────────────────────────────────────────────────────────────────────────────┐
│                                 ANATOMY OF A FOR LOOP                                   │
├─────────────────────────────────────────────────────────────────────────────────────────┤
│  HEADER:   for       asset         in       computer_assets:  ◄─── Ends with colon (:)  │
│             ▲          ▲           ▲               ▲                                    │
│          Keyword   Loop Variable Operator      Sequence List                            │
│                                                                                         │
│  BODY:         print(asset)  ◄─── Indented 4 spaces (Action per iteration)              │
└─────────────────────────────────────────────────────────────────────────────────────────┘
```

### 1. The Loop Header
- **`for` Keyword:** Signals the start of the `for` loop.
- **Loop Variable:** A temporary placeholder variable (`i`, `asset`, `user`) created in the header that holds the current sequence item during each iteration.
- **`in` Operator:** Tells Python to sequentially pull each item from the designated collection.
- **Sequence:** The target collection to iterate over (list, string, range, etc.).
- **Mandatory Colon (`:`):** The header must terminate with a colon.

### 2. The Loop Body
- Contains the statements executed during each cycle of the loop.
- **Indentation Rule:** Must be indented (standard: 4 spaces). Missing indentation triggers an `IndentationError`.

---

## The Dual Roles of the `in` Operator

The keyword **`in`** serves two completely different purposes in Python depending on context:

| Context | Example | Purpose & Return Value |
| :--- | :--- | :--- |
| **`for` Loop Header** | `for user in user_list:` | Iteration tool: pulls each item sequentially from `user_list`. |
| **Conditional Expression** | `if "elarson" in user_list:` | Membership operator: evaluates to `True` if `"elarson"` is present, otherwise `False`. |

---

## Iterating Over Different Data Types

### 1. Looping Through Lists
Lists of security assets, IP addresses, or usernames can be systematically parsed:

```python
computer_assets = ["laptop1", "desktop20", "smartphone03"]

for asset in computer_assets:
    print(asset)
```

### 2. Looping Through Strings
Strings are sequences of characters. Iterating through a string inspects each character one by one:

```python
string = "security"

for character in string:
    print(character)
```

```
Output:
s
e
c
u
r
i
t
y
```

---

# Generating Sequences with `range()`

The built-in **`range()`** function generates an immutable sequence of numbers on demand, commonly used to control loop execution counts.

```python
range(start, stop, step)
```

```
┌─────────────────────────────────────────────────────────────────┐
│                      RANGE FUNCTION PARAMETERS                  │
├─────────────────────────────────────────────────────────────────┤
│  range( 0   ,   5   ,   1 )                                     │
│         ▲       ▲       ▲                                       │
│       START    STOP   STEP/INCREMENT                            │
│    (Inclusive)(Exclusive)                                       │
│                                                                 │
│  Generates: [0, 1, 2, 3, 4]  (Note: 5 is EXCLUDED)              │
└─────────────────────────────────────────────────────────────────┘
```

### Syntax and Parameters

| Parameter | Type | Default Value | Description |
| :--- | :--- | :--- | :--- |
| **`start`** | Integer | `0` | **Inclusive** starting value of the sequence. |
| **`stop`** | Integer | *Required* | **Exclusive** upper limit (sequence concludes at `stop - 1`). |
| **`step`** | Integer | `1` | Increment value between each generated number. |

### Syntax Variations

```python
# Explicit: start=0, stop=5, step=1
for i in range(0, 5, 1):
    print(i)
# Outputs: 0, 1, 2, 3, 4

# Shorthand: default start (0) and default step (1)
for i in range(5):
    print(i)
# Outputs: 0, 1, 2, 3, 4

# Custom start and step: start=2, stop=10, step=2
for i in range(2, 10, 2):
    print(i)
# Outputs: 2, 4, 6, 8
```

> [!warning] Exclusive Stop Point Rule
> In `range(start, stop)`, the **`stop` value is never included** in the output sequence. `range(0, 5)` stops at `4`.

---

# `while` Loops

If you need a loop to execute based on a **dynamic condition** rather than a fixed sequence, use a **`while` loop**.
- The loop continues executing as long as the condition evaluates to **`True`**.
- As soon as the condition evaluates to **`False`**, the loop terminates.

```python
i = 1
while i < 5:
    print(i)
    i = i + 1
```

```
Output:
1
2
3
4
```

---

## Anatomy of a `while` Loop

```
┌────────────────────────────────────────────────────────────────────────┐
│                        ANATOMY OF A WHILE LOOP                         │
├────────────────────────────────────────────────────────────────────────┤
│  INITIALIZATION:  i = 1              ◄─── Set loop variable OUTSIDE    │
│  HEADER:          while i < 5:       ◄─── Condition + ends with ':'    │
│  BODY:                print(i)       ◄─── Indented execution block     │
│                       i = i + 1      ◄─── MUST update condition state  │
└────────────────────────────────────────────────────────────────────────┘
```

### Key Differences Between `for` and `while` Headers:
1. **Loop Variable Initialization:** In a `while` loop, the variable controlling the loop **must be initialized before** the loop begins.
2. **State Mutation:** The loop body **must update** the variable so the condition eventually becomes `False`; otherwise, an infinite loop occurs.

---

## `while` Loop Condition Types

### 1. Integer-Based Conditions (Counters & Thresholds)
Commonly used to track attempt thresholds, rate limiting, and retry counts:

```python
login_attempts = 0

while login_attempts < 5:
    print("Login attempts:", login_attempts)
    login_attempts = login_attempts + 1
```

```
Output:
Login attempts: 0
Login attempts: 1
Login attempts: 2
Login attempts: 3
Login attempts: 4
```
*(When `login_attempts` reaches `5`, `5 < 5` evaluates to `False`, terminating the loop.)*

### 2. Boolean-Based Conditions (State Flags)
Used for indeterminate processes, polling loops, or event-driven listeners:

```python
count = 0
login_status = True

while login_status == True:
    print("Try again.")
    count = count + 1
    if count == 4:
        login_status = False
```

```
Output:
Try again.
Try again.
Try again.
Try again.
```

---

# Controlling Loop Execution: `break` and `continue`

Python provides loop control keywords to alter standard iteration flow from inside conditional statements:

```
┌─────────────────────────────────────────────────────────────────────────┐
│                      LOOP FLOW CONTROL COMPARISON                       │
├─────────────────────────────────────────────────────────────────────────┤
│    [break]                             [continue]                       │
│       │                                     │                           │
│       ▼                                     ▼                           │
│  TERMINATES the entire loop           SKIPS remaining lines in current  │
│  immediately. Jumps OUT of loop.      iteration. Jumps to NEXT cycle.   │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## The `break` Keyword

The **`break`** keyword immediately terminates the loop, transferring control to the first line of code outside the loop structure.

```python
computer_assets = ["laptop1", "desktop20", "smartphone03"]

for asset in computer_assets:
    if asset == "desktop20":
        break
    print(asset)
```

```
Output:
laptop1
```

> [!note] Execution Trace with `break`
> 1. Iteration 1: `asset = "laptop1"`. `asset == "desktop20"` is `False`. Prints `"laptop1"`.
> 2. Iteration 2: `asset = "desktop20"`. Condition is `True` &rarr; `break` executes.
> 3. The loop halts immediately. `"desktop20"` and `"smartphone03"` are never processed.

---

## The `continue` Keyword

The **`continue`** keyword skips the rest of the current iteration's code block and proceeds immediately to the next iteration.

```python
computer_assets = ["laptop1", "desktop20", "smartphone03"]

for asset in computer_assets:
    if asset == "desktop20":
        continue
    print(asset)
```

```
Output:
laptop1
smartphone03
```

> [!note] Execution Trace with `continue`
> 1. Iteration 1: `asset = "laptop1"`. `asset == "desktop20"` is `False`. Prints `"laptop1"`.
> 2. Iteration 2: `asset = "desktop20"`. Condition is `True` &rarr; `continue` executes. `print(asset)` is skipped.
> 3. Iteration 3: `asset = "smartphone03"`. `asset == "desktop20"` is `False`. Prints `"smartphone03"`.

---

## `break` vs. `continue` Comparison

| Feature | `break` | `continue` |
| :--- | :--- | :--- |
| **Action** | Aborts and terminates the loop entirely. | Skips remainder of current iteration only. |
| **Subsequent Iterations** | Canceled. | Continue as normal. |
| **Security Use Case** | Stop scanning when malicious signature/threat is found. | Skip benign/allowlisted IPs and process remaining logs. |

---

# Infinite Loops

> [!caution] Infinite Loop
> An **infinite loop** occurs when a loop's conditional expression never evaluates to `False` and contains no terminating `break` statement.

```python
# DANGEROUS: Missing variable increment leads to an infinite loop
i = 0
while i < 5:
    print(i)
    # Missing: i = i + 1
```

### Terminating Infinite Loops
- In terminal/command-line environments or interactive notebooks, press:
  - **`CTRL + C`** (Windows / Linux / macOS)
  - **`CTRL + Z`** (Suspends process in Unix)
  - Interrupt kernel button in Jupyter/Colab notebooks.

### Intentional Infinite Loops in Security Engineering
Not all infinite loops are bugs. Continuous daemon services intentionally use infinite loops with `break` guards:
- Web servers and API listeners (`while True:` awaiting client requests).
- SIEM log scrapers tailing real-time syslog files.
- Network intrusion detection daemon sniffers.

```python
# Continuous network event listener pattern
while True:
    packet = listen_for_packet()
    if packet is None:
        continue
    if packet.contains_exploit():
        alert_soc(packet)
        break # or keep monitoring
```

---

# Practical Security Automation Examples

### Example 1: IP Allowlist / Denylist Filtering (`for` + `continue`)
```python
network_ips = ["192.168.1.10", "10.0.0.1", "172.16.0.5", "192.168.1.25"]
allowlisted_subnets = "192.168.1."

print("[*] Initiating Vulnerability Scan on External Targets...")
for ip in network_ips:
    if ip.startswith(allowlisted_subnets):
        # Skip trusted internal IPs
        continue
    print(f"[SCAN] Scanning target IP: {ip}")
```

```
Output:
[*] Initiating Vulnerability Scan on External Targets...
[SCAN] Scanning target IP: 10.0.0.1
[SCAN] Scanning target IP: 172.16.0.5
```

### Example 2: Account Lockout Guard (`while` + `break`)
```python
max_allowed_attempts = 3
attempts = 0
authenticated = False

while attempts < max_allowed_attempts:
    attempts += 1
    # Simulated authentication check
    input_user = "admin"
    input_pass = "wrong_password" if attempts < 3 else "correct_password"
    
    if input_pass == "correct_password":
        authenticated = True
        print(f"[AUTH SUCCESS] Access granted on attempt {attempts}.")
        break
    else:
        print(f"[AUTH FAIL] Invalid credentials. Attempt {attempts}/{max_allowed_attempts}.")

if not authenticated:
    print("[SECURITY ALERT] Account locked due to excessive failed attempts!")
```

---

# Key Terms at a Glance

| Term | Meaning |
| :--- | :--- |
| **Iterative Statement** | A programming construct that repeatedly executes instructions zero or more times. |
| **`for` Loop** | A loop that iterates across a predetermined sequence (lists, strings, ranges). |
| **`while` Loop** | A loop that executes repeatedly as long as a Boolean condition remains `True`. |
| **Loop Variable** | A variable used to hold current iteration data or control loop cycles. |
| **`range()`** | Built-in function generating a sequence of integers `(start, stop, step)`. |
| **`break`** | Statement that exits and halts the surrounding loop immediately. |
| **`continue`** | Statement that skips the remainder of the current iteration and starts the next. |
| **Infinite Loop** | A loop whose condition never becomes `False`, running perpetually until interrupted. |

---

# Exam Tips

> [!tip] Key Takeaways for the Exam
> - **`for` vs `while` Choice:**
>   - Use **`for`** when iterating through a known collection or sequence.
>   - Use **`while`** when repeating instructions until a specific condition or event occurs.
> - **`range()` Rules:**
>   - Default `start` = `0`, default `step` = `1`.
>   - The `stop` value is **exclusive** (`range(0, 4)` &rarr; `0, 1, 2, 3`).
> - **Dual Nature of `in`:**
>   - In a loop header (`for x in seq:`): iteration directive.
>   - In a condition (`if x in seq:`): membership test returning Boolean `True`/`False`.
> - **`break` vs `continue` Impact:**
>   - `break` exits the entire loop.
>   - `continue` only skips the rest of the *current* cycle.
> - **Preventing Infinite Loops:** Always ensure `while` loop conditions have a state change (`i = i + 1`) or an reachable `break` statement.

---

## Related Notes

- [[Conditional Statements in Python]]
- [[Python Variables and Naming Conventions]]
- [[Python Data Types]]
- [[Programming and Python in Cybersecurity]]
- [[Python Environments and Notebooks]]
- [[Logs and SIEM Tools]]
- [[Playbooks and Incident Response]]
