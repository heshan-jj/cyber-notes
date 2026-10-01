---
tags:
  - cybersecurity
  - python
  - programming
  - built-in-functions
  - function-composition
  - data-analysis
  - automation
  - google-cert
  - module-02
  - course-07
aliases:
  - Built-in Functions in Python
  - Common Built-in Functions in Python
  - Python Built-in Functions
  - print, type, max, min, and sorted in Python
  - Function Composition in Python
  - Nested Functions in Python
---

> [!abstract] Python Built-in Functions & Function Composition
> **Built-in functions** are pre-compiled, globally accessible routines native to Python that can be executed directly without custom definitions or imports. In security automation, analysts rely on built-in functions to display triage alerts ([`print()`](#print---console-output--telemetry-reporting)), inspect object data structures ([`type()`](#type---data-type-inspection--validation)), detect statistical anomalies and outlier session durations ([`max()`](#max-and-min---identifying-extremes--anomalies) / [`min()`](#max-and-min---identifying-extremes--anomalies)), and sequence event logs ([`sorted()`](#sorted---ordering-telemetry--log-sequences)). Furthermore, Python allows **function composition** (nesting functions), where the returned output of one function serves as the input argument for another.

---

# Overview of Core Built-in Functions

Unlike [[Defining and Calling Functions in Python|user-defined functions]] which must be declared with `def`, built-in functions are instantly available across any script or [[Python Environments and Notebooks|Jupyter notebook]].

| Built-in Function | Arguments Accepted | Return Value | Modifies Original? | Common Cybersecurity Use Case |
| :--- | :--- | :--- | :--- | :--- |
| **`print()`** | Multiple comma-separated objects (`*args`) | `None` (Outputs to console) | No | Displaying security alerts, investigation prompts, and debug traces |
| **`type()`** | Single object | Type class (`<class '...'>`) | No | Validating parsed log data types before performing calculations |
| **`min()`** | Iterable OR multiple comma-separated values | Smallest element | No | Finding minimum session duration, lowest port number, or baseline traffic |
| **`max()`** | Iterable OR multiple comma-separated values | Largest element | No | Identifying longest active sessions, peak packet sizes, or brute-force spikes |
| **`sorted()`** | Single iterable (list, string, tuple, etc.) | **New** sorted list | **No (Immutable)** | Chronologically ordering timestamps, sorting IP addresses, ranking risk scores |

---

# `print()` — Console Output & Telemetry Reporting

The **`print()`** function outputs specified objects as text strings to the terminal or standard output stream.

```python
print(*objects, sep=' ', end='\n')
```

### Multi-Argument Handling
`print()` can accept **any number of arguments** separated by commas. Python automatically converts each object to a string and inserts a single space between them:

```python
month = "September"
failed_threshold = 100

print("Investigate failed login attempts during", month, "if more than", failed_threshold)
```

```
Output:
Investigate failed login attempts during September if more than 100
```

> [!tip] Comma Separation vs. String Concatenation
> Passing multiple comma-separated arguments to `print()` automatically formats different [[Python Data Types|data types]] (strings, integers, floats, booleans) without requiring manual type conversion (e.g., `str(failed_threshold)`).

---

# `type()` — Data Type Inspection & Validation

The **`type()`** function returns the exact data type classification of any given object.

```python
type(object)
```

- **Constraint:** `type()` accepts **only one argument**.
- **Role in Security Scripting:** Security logs ingested from SIEM platforms or APIs often arrive as raw strings. Before performing arithmetic (e.g., calculating remaining login attempts or subnet masks), analysts use `type()` to prevent `TypeError` exceptions.

```python
source_ip = "192.168.1.1"
port_number = 443
is_flagged = True

print(type(source_ip))    # <class 'str'>
print(type(port_number))  # <class 'int'>
print(type(is_flagged))   # <class 'bool'>
```

---

# Passing One Function into Another (Function Composition)

In Python, functions can be **nested** inside one another. When a function call is passed as an argument into another function, Python resolves the **innermost function first** and passes its returned result directly into the outer function.

```python
print(type("This is a string"))
```

```
Output:
<class 'str'>
```

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    NESTED FUNCTION EXECUTION FLOW                       │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│   Outer Function: print( ... )                                          │
│                          ▲                                              │
│                          │  Passes Return Value: <class 'str'>          │
│                          │                                              │
│   Inner Function: type("This is a string")                              │
│                          │                                              │
│                          ▼                                              │
│   Evaluates: type("This is a string") ──► Returns <class 'str'>         │
│   Then Executes: print(<class 'str'>) ──► Displays to screen            │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

### Why Function Nesting is Necessary:
Functions like `type()`, `min()`, `max()`, and `sorted()` return programmatic data in memory (see [[Parameters, Return Statements, and Variable Scope in Python|Return Statements]]). If you run `type("security")` alone in a script, Python computes the data type but does not display it. Passing `type()` inside `print()` allows the result to be output to the console.

---

# `max()` and `min()` — Identifying Extremes & Anomalies

The **`max()`** and **`min()`** functions calculate the upper and lower mathematical boundaries from a collection of inputs.

### Syntax Variations:
1. **Multiple Arguments:** `min(10, 5, 20)` or `max(10, 5, 20)`
2. **Single Iterable:** `min([10, 5, 20])` or `max([10, 5, 20])`

---

## Cybersecurity Scenario: Session Anomaly Detection

Security analysts monitor session lengths to identify suspicious user behavior:
- **Abnormally Short Sessions (`min`):** May indicate automated credential-stuffing scanners that immediately disconnect upon failure.
- **Abnormally Long Sessions (`max`):** May indicate unauthorized persistence, compromised credentials, or stalled connections.

```python
# User login session durations recorded in minutes across one week
time_list = [12, 2, 32, 19, 57, 22, 14]

shortest_session = min(time_list)
longest_session = max(time_list)

print("Shortest session duration:", shortest_session, "minutes")
print("Longest session duration:", longest_session, "minutes")
```

```
Output:
Shortest session duration: 2 minutes
Longest session duration: 57 minutes
```

---

# `sorted()` — Ordering Telemetry & Log Sequences

The **`sorted()`** function takes an iterable (such as a list, string, or tuple) and returns a **new list** containing all elements arranged in ascending order.

```python
sorted(iterable, key=None, reverse=False)
```

```python
time_list = [12, 2, 32, 19, 57, 22, 14]

sorted_sessions = sorted(time_list)
print("Sorted session times:", sorted_sessions)
```

```
Output:
Sorted session times: [2, 12, 14, 19, 22, 32, 57]
```

---

## Sorting Rules & Data Behaviors

1. **Numeric Data:** Sorted from smallest value to largest value (`2` &rarr; `12` &rarr; `57`).
2. **String / Text Data:** Sorted alphabetically based on ASCII / Unicode character values:
   - Uppercase characters precede lowercase characters (`"Alert"` comes before `"alert"`).
   - Numeric string characters precede alphabetical characters (`"10.0.0.1"` comes before `"admin"`).
3. **Strings as Iterables:** When passed a string, `sorted()` splits and returns the characters as a sorted list:
   ```python
   print(sorted("security"))
   # Output: ['c', 'e', 'i', 'r', 's', 't', 'u', 'y']
   ```

---

## Non-Destructive Nature (Immutability of Original Data)

> [!important] `sorted()` Never Mutates the Original List
> `sorted()` creates and returns a **brand new list** in memory. The original collection remains completely unchanged:

```python
time_list = [12, 2, 32, 19, 57, 22, 14]

print("1. Result of sorted(time_list):", sorted(time_list))
print("2. Original time_list variable:", time_list)
```

```
Output:
1. Result of sorted(time_list): [2, 12, 14, 19, 22, 32, 57]
2. Original time_list variable: [12, 2, 32, 19, 57, 22, 14]
```

To preserve the sorted order for subsequent operations in your script, you must store the returned list in a new variable:

```python
ordered_telemetry = sorted(time_list)
```

---

## Type Homogeneity Constraint

> [!warning] Incompatible Mixed Data Types Cause `TypeError`
> `sorted()` requires all elements within the iterable to be comparable with one another. Attempting to sort a list containing mixed, incompatible data types (such as integers and strings) triggers an exception:

```python
# ❌ INVALID: Cannot compare integers and strings
mixed_log = [1, 2, "hello"]
# sorted(mixed_log) ──► TypeError: '<' not supported between instances of 'str' and 'int'
```

### Remediation in Security Pipelines:
Before sorting raw event logs, sanitize and standardize the data types using list comprehensions or parsing loops (e.g., ensuring all elements are converted to integers with `int()` or strings with `str()`).

---

# Built-in Functions Quick Reference

```
┌─────────────────────────────────────────────────────────────────────────┐
│                     BUILT-IN FUNCTIONS QUICK CHEAT SHEET                │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│   print(a, b, c)  ──► Prints all objects separated by spaces            │
│   type(obj)       ──► Returns data type class: <class 'str'>, etc.      │
│   min(iterable)   ──► Finds smallest numeric/alphabetical element       │
│   max(iterable)   ──► Finds largest numeric/alphabetical element        │
│   sorted(seq)     ──► Returns a NEW list sorted in ascending order      │
│                                                                         │
│   Nested Example:                                                       │
│   print(sorted(min_list)) ──► Evaluates inner sorted(), then prints it  │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

---

# Key Takeaways

> [!important] Summary Checklist
> - **Built-in Functions:** Core Python tools ready for direct execution without imports or custom `def` headers.
> - **`print()`:** Flexible output function accepting multiple heterogeneous arguments separated by commas.
> - **`type()`:** Single-argument inspection utility essential for defensive type-checking.
> - **Function Composition:** Resolves from the inside out; the return value of an inner function feeds as an argument to the outer function.
> - **`max()` & `min()`:** Extract peak and floor values from lists or numeric series (critical for anomaly detection).
> - **`sorted()` Immutability:** Always outputs a fresh sorted list, leaving the original data structure intact.
> - **Type Consistency:** Collections passed to `sorted()` must contain mutually comparable data types.

---

## Related Notes

- [[Working with Lists in Python]]
- [[Working with Strings in Python]]
- [[Defining and Calling Functions in Python]]
- [[Parameters, Return Statements, and Variable Scope in Python]]
- [[Python Data Types]]
- [[Python Variables and Naming Conventions]]
- [[Conditional Statements in Python]]
- [[Iterative Statements in Python]]
- [[Programming and Python in Cybersecurity]]
- [[Python Environments and Notebooks]]
- [[Logs and SIEM Tools]]
- [[Playbooks and Incident Response]]
- [[Authentication and the AAA Framework]]
- [[Brute Force Attacks]]
