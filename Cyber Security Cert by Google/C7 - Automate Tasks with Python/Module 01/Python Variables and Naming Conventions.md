---
tags:
  - cybersecurity
  - python
  - programming
  - variables
  - naming-conventions
  - google-cert
  - module-01
  - course-07
aliases:
  - Python Variables
  - Variables in Python
  - Python Variables and Naming Conventions
  - Assigning and Reassigning Variables
  - Variable Naming Best Practices
---

> [!abstract] Python Variables & Naming Conventions
> In Python, a **variable** is a named storage container in a computer's memory that holds a mutable data value. Security analysts rely heavily on variables to capture dynamic operational metrics such as failed login attempts, allow lists, IP addresses, and session tokens. Structuring variables correctly requires understanding **assignment**, **reassignment**, **memory copying**, and strict adherence to **Python naming syntax rules and stylistic best practices (PEP 8)**.

---

# What is a Variable?

> [!info] Definition
> A **variable** is a named container in a computer's memory that stores data of a particular data type (e.g., string, integer, Boolean, list).

The data stored within a variable can change dynamically throughout program execution, while the variable's name (identifier) remains constant.

### The Labeled Box Analogy

Think of a variable as a labeled storage box:

```
┌────────────────────────────────────────────────────────┐
│                      VARIABLE BOX                      │
│  Label (Variable Name): username                       │
│  ┌──────────────────────────────────────────────────┐  │
│  │ Stored Value: "nzhao"   (Data Type: str)         │  │
│  └──────────────────────────────────────────────────┘  │
└────────────────────────────────────────────────────────┘
```

- **Box Label:** The variable's name (`username`), used to reference the stored data.
- **Box Contents:** The data value (`"nzhao"`), which can be swapped, updated, or reassigned.
- **Automatic Typing:** Python dynamically infers and assigns the appropriate data type based on the value provided.

---

# Assigning and Reassigning Variables

### 1. Assigning a Variable
To declare and initialize a variable, place the variable identifier on the left side of the assignment operator (`=`) and the value on the right:

```python
# Initial assignment
username = "nzhao"
login_attempts = 3
is_authenticated = False
```

### 2. Reassigning a Variable
Reassigning updates the value stored in the existing memory container. The previous value is replaced:

```python
# Reassigning 'username' with a new string
username = "zhao2"
login_attempts = login_attempts + 1
```

### 3. Assigning Variables to Other Variables
You can assign the current value of one variable to a second variable. This copies the value into the second container:

```python
# Copying variable value
username = "nzhao"
old_username = username

# Updating the primary variable
username = "zhao2"
```

### Complete Workflow Example

```python
# Tracking user account changes during an access audit
username = "nzhao"
old_username = username
username = "zhao2"

print("Previous username:", old_username)
print("Current username:", username)

# Output:
# Previous username: nzhao
# Current username: zhao2
```

---

# Variable Naming Rules & Guidelines

Python distinguishes between **strict syntax rules** (which cause interpreter errors if violated) and **stylistic best practices** (which ensure readability and team maintainability).

```
┌────────────────────────────────────────────────────────────────────────┐
│                        VARIABLE NAMING CRITERIA                        │
├──────────────────────────────────┬─────────────────────────────────────┤
│ SYNTAX RULES (Enforced)          │ STYLE GUIDELINES (Best Practices)   │
├──────────────────────────────────┼─────────────────────────────────────┤
│ • Letters, numbers, underscores  │ • Use lowercase with snake_case     │
│ • Cannot start with a number     │ • Descriptive, meaningful names     │
│ • Case-sensitive (a != A)        │ • Avoid overly similar names        │
│ • No reserved Python keywords    │ • Concise without being cryptic     │
└──────────────────────────────────┴─────────────────────────────────────┘
```

---

## 1. Syntax Rules (Mandatory)

Violating these rules causes a `SyntaxError` or runtime failure:

1. **Allowed Characters:** Variable names can only contain **letters** (`a-z`, `A-Z`), **numbers** (`0-9`), and **underscores** (`_`).
   - *Valid:* `date_3`, `username`, `interval2`
   - *Invalid:* `user-name` (hyphen), `user$name` (special symbol), `user name` (space).
2. **Numbers at Start:** A variable name cannot begin with a number.
   - *Valid:* `log_1`, `ip_address2`
   - *Invalid:* `1_log`, `2nd_ip`
3. **Case Sensitivity:** Variable identifiers are strictly case-sensitive.
   - `time`, `Time`, `TIME`, and `timE` are four completely separate variables.
4. **No Reserved Keywords:** You cannot use Python's built-in keywords or boolean literals as variable names.
   - *Reserved:* `True`, `False`, `if`, `else`, `elif`, `for`, `while`, `def`, `class`, `import`, `and`, `or`, `not`, `in`, `is`.

```python
# Syntax Examples
valid_var = 100       # Valid
_internal_id = "A01"  # Valid
# 2nd_attempt = 2     # SyntaxError: invalid decimal literal
# if = "condition"    # SyntaxError: invalid syntax
```

---

## 2. Stylistic Guidelines (Best Practices)

Following the official Python style guide (**PEP 8**) ensures team readability and reduces security misconfigurations:

| Guideline | Recommended Practice | Discouraged Practice | Rationale |
| :--- | :--- | :--- | :--- |
| **Multi-Word Separation** | Use **snake_case** (`login_attempts`, `invalid_user`, `status_update`). | `loginattempts`, `LOGINATTEMPTS` | Greatly enhances visual scanning during incident investigations. |
| **Descriptive Names** | `num_login_attempts`, `device_id`, `threat_score` | `x`, `temp`, `data`, `variable_that_equals_3` | Code should clearly self-document what metric is being tracked. |
| **Avoid Similar Names** | Use distinct names (`start_timestamp`, `end_timestamp`). | `start_time`, `starting_time`, `time_starting` | Minimizes accidental variable cross-over bugs and typos. |
| **Balanced Length** | `user_email`, `failed_ips` | `the_email_address_of_the_user_logged_in` | Avoids cluttering math calculations and conditional logic. |

> [!note] Camel Case vs. Snake Case
> While Python's official convention is **snake_case** (`login_attempts`), you may occasionally encounter **camelCase** (`loginAttempts`) in codebases influenced by JavaScript or Java. Stick to snake_case for standard Python scripting.

---

# Summary Table: Valid vs. Invalid Identifiers

| Identifier Name | Status | Reason / Explanation |
| :--- | :--- | :--- |
| `username` | **Valid** | Standard single-word identifier. |
| `login_attempts` | **Valid (Recommended)** | Uses standard snake_case formatting. |
| `failed_ip_2` | **Valid** | Combines letters, underscores, and a trailing number. |
| `2nd_attempt` | ❌ **Invalid** | Cannot begin with a number. |
| `user-role` | ❌ **Invalid** | Contains a hyphen (interpreted as subtraction `-`). |
| `user name` | ❌ **Invalid** | Spaces are not permitted. |
| `True` / `if` | ❌ **Invalid** | Python reserved keywords. |

---

# Key Terms at a Glance

| Term | Meaning |
| :--- | :--- |
| **Variable** | A named storage location in memory holding a mutable value. |
| **Assignment Operator (`=`)** | Assigns the value on the right to the variable on the left. |
| **Reassignment** | Overwriting the current value in a variable with a new value. |
| **Case-Sensitive** | Distinguishing between uppercase and lowercase letters in names. |
| **Reserved Keyword** | Built-in Python keywords reserved exclusively for language syntax. |
| **Snake Case** | Naming convention separating lowercase words with underscores (`snake_case`). |
| **Camel Case** | Naming convention capitalizing subsequent words without spaces (`camelCase`). |

---

# Exam Tips

> [!tip] Key Takeaways for the Exam
> - **Variable Assignment Direction:** Values flow from **right to left** (`variable = value`).
> - **Copying Values:** Assigning `old_var = current_var` captures the state of `current_var` at that moment in time.
> - **Character Rules:** Variable names may only contain letters, numbers, and underscores, and **cannot start with a number**.
> - **Case Sensitivity:** `user_id` and `User_Id` are treated as two different variables by Python.
> - **Reserved Keywords:** Never name a variable after language constructs like `True`, `False`, `if`, `for`, or `def`.

---

## Related Notes

- [[Conditional Statements in Python]]
- [[Python Data Types]]
- [[Python Environments and Notebooks]]
- [[Programming and Python in Cybersecurity]]
- [[Tools and their purposes]]
- [[Cybersecurity Fundamentals]]
