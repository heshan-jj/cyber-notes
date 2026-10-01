---
tags:
  - cybersecurity
  - python
  - programming
  - functions
  - parameters
  - arguments
  - return-statements
  - variable-scope
  - global-variables
  - local-variables
  - google-cert
  - module-02
  - course-07
aliases:
  - Parameters, Return Values, and Variable Scope in Python
  - Parameters and Arguments in Python
  - Return Statements in Python
  - Global and Local Variables in Python
  - Python Variable Scope
  - Function Scope in Python
  - Parameters, Return Statements, and Scope
---

> [!abstract] Parameters, Return Statements & Variable Scope
> Functions become truly powerful when they can accept dynamic input, process it, and output meaningful results. **Parameters** act as placeholders in function headers, while **arguments** are the actual data passed into those parameters during function invocation. The **`return`** keyword outputs processed data back to the main program for storage and conditional evaluation. Furthermore, understanding **variable scope**—the distinction between **global variables** (accessible everywhere) and **local variables** (restricted to a function's execution lifecycle)—is critical for writing modular, bug-free security automation tools.

---

# Parameters vs. Arguments

While often used interchangeably in casual conversation, **parameters** and **arguments** represent two distinct stages of data handling in Python:

```
┌─────────────────────────────────────────────────────────────────────────────────────────┐
│                                PARAMETERS VS. ARGUMENTS                                 │
├─────────────────────────────────────────────────────────────────────────────────────────┤
│  DEFINITION:   def remaining_login_attempts( maximum_attempts , total_attempts ):       │
│                                                     ▲                 ▲                 │
│                                                Parameter 1       Parameter 2            │
│                                                (Placeholder)     (Placeholder)          │
│                                                     ▲                 ▲                 │
│  INVOCATION:   remaining_login_attempts(            3        ,        2        )        │
│                                                     ▲                 ▲                 │
│                                                 Argument 1        Argument 2            │
│                                               (Actual Value)    (Actual Value)          │
└─────────────────────────────────────────────────────────────────────────────────────────┘
```

### Key Differences Breakdown

| Characteristic | Parameter | Argument |
| :--- | :--- | :--- |
| **Where Defined** | In the **function header** during definition | In the **function call** during invocation |
| **Role** | Variable/placeholder waiting for data | Concrete value/data passed into the placeholder |
| **Scope** | Local to the function | Defined in the caller's environment |
| **Example** | `def calc_risk(ip_score, vuln_level):` | `calc_risk(85, 3)` |

---

## 1. Parameters (Input Placeholders)

A **parameter** is a variable defined inside the parentheses of a function header. It establishes the input contract that the function body expects to operate on:

```python
def remaining_login_attempts(maximum_attempts, total_attempts):
    print(maximum_attempts - total_attempts)
```

- In this header, `maximum_attempts` and `total_attempts` are parameters.
- They behave like local variables within the function body, holding whatever values are passed in during execution.

---

## 2. Arguments (Input Data)

An **argument** is the specific value, variable, or data structure passed into a function when calling it:

```python
remaining_login_attempts(3, 2)
```

```
Output:
1
```

### Positional Mapping
Python maps arguments to parameters **positionally by default**:
- The **1st argument** (`3`) binds to the **1st parameter** (`maximum_attempts`).
- The **2nd argument** (`2`) binds to the **2nd parameter** (`total_attempts`).

> [!warning] Argument Order Matters
> In positional mapping, swapping argument positions alters the calculation. Calling `remaining_login_attempts(2, 3)` binds `maximum_attempts = 2` and `total_attempts = 3`, producing `-1` instead of `1`.

---

# Return Statements & Function Output

While `print()` displays text on the screen, it does not allow the rest of your program to capture or manipulate the calculation. To pass data **out** of a function back into the calling environment, use the **`return`** keyword.

```python
def remaining_login_attempts(maximum_attempts, total_attempts):
    return maximum_attempts - total_attempts
```

> [!important] Syntax Note: `return` is a Statement, Not a Function
> `return` is a Python reserved keyword. You do **not** use parentheses after `return` (write `return value`, not `return(value)`).

---

## Capturing Return Values in Variables

Returning information allows you to capture the result in a variable and pass it to downstream security checks, such as automated account lockout logic:

```python
def remaining_login_attempts(maximum_attempts, total_attempts):
    return maximum_attempts - total_attempts

# Store the returned calculation in a variable
remaining_attempts = remaining_login_attempts(3, 3)

# Evaluate the result in a security conditional
if remaining_attempts <= 0:
    print("Your account is locked")
```

```
Output:
Your account is locked
```

### `print()` vs. `return` Comparison

| Feature | `print()` | `return` |
| :--- | :--- | :--- |
| **Purpose** | Displays output to the human console/terminal | Sends programmatic data back to the caller |
| **Variable Assignment** | Returns `None`; cannot be stored or reused | Stored directly into variables for further processing |
| **Execution Impact** | Code execution continues to the next line | **Immediately terminates** the function execution |
| **Typical SecOps Role** | Logging status messages, debug console prints | Returning parsed IP lists, threat scores, boolean flags |

---

## Immediate Function Exit on `return`

When Python executes a `return` statement, it **immediately exits the function**, returning control to the calling line. Any code placed after `return` within that function block is **dead code** and will never execute:

```python
def evaluate_firewall_rule(port):
    if port == 22:
        return "SSH: High Monitoring Required"
        print("This line will NEVER execute")  # Unreachable code
    
    return "Standard Traffic Allowed"

status = evaluate_firewall_rule(22)
print(status)
```

```
Output:
SSH: High Monitoring Required
```

---

# Understanding Variable Scope

**Scope** refers to the region of a program where a particular variable is recognized, accessible, and valid. Python distinguishes primarily between **global scope** and **local scope**.

```
┌─────────────────────────────────────────────────────────────────────────┐
│                          VARIABLE SCOPE HIERARCHY                       │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│   GLOBAL SCOPE (Entire Program)                                         │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │  device_id = "7ad2130bd"                                        │   │
│   │  org_domain = "company.internal"                                │   │
│   │                                                                 │   │
│   │   LOCAL SCOPE: greet_employee(name)                             │   │
│   │   ┌─────────────────────────────────────────────────────────┐   │   │
│   │   │  name = "Marcus"             ◄── Local parameter        │   │   │
│   │   │  total_string = "Welcome..." ◄── Local variable         │   │   │
│   │   │                                                         │   │   │
│   │   │  (Destroyed from memory when function exits)            │   │   │
│   │   └─────────────────────────────────────────────────────────┘   │   │
│   │                                                                 │   │
│   │   Cannot access total_string out here!                          │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 1. Global Variables

A **global variable** is defined outside of any function body. It belongs to the top-level script environment and is accessible anywhere across the entire program.

```python
device_id = "7ad2130bd"

def display_device():
    # Functions can read global variables
    print("Inspecting device:", device_id)

display_device()
print("Global verification:", device_id)
```

```
Output:
Inspecting device: 7ad2130bd
Global verification: 7ad2130bd
```

- **Lifetime:** Exists for the entire duration of the program execution.
- **Use Cases in SecOps:** System-wide constants, global environment configurations, base API URLs, and default threshold values.

---

## 2. Local Variables

A **local variable** is created inside a function definition. This includes **parameters** as well as any variables initialized within the function body.

```python
def greet_employee(name):
    total_string = "Welcome " + name
    return total_string

# Calling the function
greeting = greet_employee("Alex")
print(greeting)

# Attempting to access total_string outside causes an error:
# print(total_string)  --> NameError: name 'total_string' is not defined
```

- **Lifetime:** Created dynamically when the function is invoked, and **erased from memory (garbage collected)** as soon as the function returns.
- **Isolation:** Local variables inside one function cannot interfere with or be accessed by other functions or the global scope.

---

# Variable Shadowing & Best Practices

## 1. Variable Shadowing (Local vs. Global Name Collisions)

If you assign a value to a variable inside a function that shares the exact same name as a global variable, Python creates a **new, separate local variable** that shadows (masks) the global variable within that function:

```python
username = "elarson"  # Global variable
print("1: Global before function ->", username)

def greet():
    username = "bmoreno"  # Local variable (shadows global)
    print("2: Local inside function ->", username)

greet()
print("3: Global after function  ->", username)
```

```
Output:
1: Global before function -> elarson
2: Local inside function -> bmoreno
3: Global after function  -> elarson
```

### Execution Trace:
1. `print("1:", username)` reads the global variable `"elarson"`.
2. `greet()` creates a **local** variable `username` assigned to `"bmoreno"`. The local print outputs `"bmoreno"`.
3. When `greet()` terminates, its local scope is destroyed.
4. `print("3:", username)` reads the unchanged global variable `"elarson"`.

---

## 2. Best Practices for Clean Security Code

> [!tip] Best Practices for Managing Scope & Functions
> 1. **Avoid Overlapping Names:** Use unique, unambiguous variable names. Never reuse a global variable name as a local variable or parameter name.
> 2. **Pass Data via Parameters (Pure Functions):** Instead of having functions rely on global variables, pass values explicitly through parameters.
> 
> ```python
> # ❌ POOR PRACTICE: Function depends on global state
> target_host = "192.168.1.50"
> def scan_target():
>     print("Scanning:", target_host)
> 
> # ✅ RECOMMENDED: Function is modular and accepts parameters
> def scan_target(host):
>     print("Scanning:", host)
> 
> scan_target("192.168.1.50")
> scan_target("10.0.0.1")
> ```
> 
> 3. **Minimize Global State:** Global variables make code harder to debug, test, and maintain during incident response scripting.

---

# Common Scope & Parameter Errors

| Error Pattern | Code Sample | Problem Description | Resolution |
| :--- | :--- | :--- | :--- |
| **`NameError`** | `def calc(): x = 5`<br>`calc()`<br>`print(x)` | Attempting to access a local variable from the global scope after function termination. | Return the variable using `return x` and store it globally. |
| **`TypeError: missing positional argument`** | `def auth(user, token): ...`<br>`auth("admin")` | Calling a function with fewer arguments than required parameters. | Provide all expected arguments (`auth("admin", "secret123")`). |
| **`TypeError: unsupported operand type`** | `def add(a, b): return a + b`<br>`add("5", 10)` | Passing incompatible argument types into parameters. | Ensure argument types match the expected operations (e.g. `int("5")`). |
| **Ignoring Return Value** | `remaining_login_attempts(3, 3)`<br>`if remaining_attempts <= 0:` | Calling a fruitful function without assigning its return value to a variable. | Assign the call result: `remaining_attempts = remaining_login_attempts(3, 3)`. |

---

# Key Takeaways

> [!important] Summary Checklist
> - **Parameters:** Variables declared in the function header that define expected inputs.
> - **Arguments:** Real values passed into function parameters upon calling.
> - **Return Keyword:** Sends processed data back to the calling context and terminates the function immediately.
> - **Global Scope:** Variables defined outside functions; available throughout the entire program.
> - **Local Scope:** Parameters and variables defined inside a function; created at runtime and deleted upon function exit.
> - **Clean Architecture:** Pass inputs explicitly via parameters and capture outputs via `return` rather than manipulating global state.
