---
tags:
  - cybersecurity
  - python
  - programming
  - data-types
  - google-cert
  - module-01
  - course-07
aliases:
  - Python Data Types
  - Data Types in Python
  - Python Data Types and Data Structures
  - Python Variables and Types
  - Strings, Lists, Tuples, Dicts, Sets
---

> [!abstract] Python Data Types & Structures
> A **data type** is a category for a particular classification of data that dictates how the Python interpreter handles the item and what operations can be performed on it. Python features foundational data types—**strings**, **integers**, **floats**, **Booleans**, and **lists**—along with specialized collections including **tuples** (immutable), **dictionaries** (key-value pairs), and **sets** (unique elements).

---

# Core Python Data Types

Python automatically determines data types upon variable assignment. Below are the five primary types utilized across security automation:

```
┌────────────────────────────────────────────────────────────────────────┐
│                        CORE PYTHON DATA TYPES                          │
├─────────────┬────────────────────────────────┬─────────────────────────┤
│ TYPE        │ DESCRIPTION                    │ EXAMPLE SYNTAX          │
├─────────────┼────────────────────────────────┼─────────────────────────┤
│ String      │ Ordered sequence of characters │ "updates needed"        │
│ List        │ Ordered, mutable collection    │ ["eraab", "drosas"]     │
│ Integer     │ Whole number (no decimal)      │ 42, -100, 0             │
│ Float       │ Number with a decimal point    │ 3.14, -0.25, 0.0        │
│ Boolean     │ Binary logical state           │ True, False             │
└─────────────┴────────────────────────────────┴─────────────────────────┘
```

---

# 1. String (`str`)

> [!info] Definition
> A **string** is an ordered sequence of characters, including letters, numbers, symbols, and spaces, enclosed within quotation marks.

- Strings can be declared with either **double quotes** (`"..."`) or **single quotes** (`'...'`).
- An empty pair of quotation marks (`""`) represents an **empty string**.
- Strings are commonly used in security to store IP addresses, usernames, log messages, and file paths.

```python
# Valid string declarations
message = "updates needed"
tax_rate = "20%"
version = "5.0"
error_code = "35"
mask = "**/**/**"
empty_str = ""

# Printing strings
print("updates needed")
print('updates needed')
```

> [!note] Best Practice
> Choose either single or double quotation marks and apply them consistently throughout your code. Double quotation marks (`""`) are standard across this course.

---

# 2. List (`list`)

> [!info] Definition
> A **list** is an ordered, sequential collection of data items enclosed in square brackets (`[...]`), separated by commas.

- Lists are **mutable** (elements can be added, updated, or removed).
- Elements can consist of any data type, including mixed types or nested lists.
- An empty bracket pair (`[]`) represents an **empty list**.

```python
# Lists with uniform data types
port_numbers = [12, 36, 54, 1, 7]
usernames = ["eraab", "arusso", "drosas"]
auth_flags = [True, False, True, True]

# List with mixed data types
mixed_record = [15, "approved", True, 45.5, False]

# Empty list
pending_scans = []

# Displaying a list
print([12, 36, 54, 1, 7])
# Output: [12, 36, 54, 1, 7]
```

---

# 3. Integer (`int`)

> [!info] Definition
> An **integer** is a whole numeric value (positive, negative, or zero) that contains **no decimal point**.

- Integers must **not** be placed in quotation marks (placing numbers in quotes converts them to strings).
- Integers support standard arithmetic operations: addition (`+`), subtraction (`-`), multiplication (`*`), and division (`/`).

```python
# Integer examples
failed_attempts = 5
temperature = -12
zero_count = 0

print(failed_attempts)
# Output: 5

# Arithmetic operations with integers
print(5 + 2)    # Output: 7
print(10 - 4)   # Output: 6
print(3 * 8)    # Output: 24
```

---

# 4. Float (`float`)

> [!info] Definition
> A **float** (floating-point number) is any real number that includes a **decimal point**.

- Floats are not enclosed in quotation marks.
- Useful for representing percentages, risk scores, execution timestamps, and calculated averages.

```python
# Float examples
risk_score = 7.8
delta_time = -1.34
baseline = 0.0

print(1.2 + 2.8)
# Output: 4.0
```

### Regular Division vs. Floor Division

| Division Operator | Symbol | Behavior | Example | Output |
| :--- | :--- | :--- | :--- | :--- |
| **Standard Division** | `/` | Always returns a **float**, even when dividing whole numbers. | `print(1 / 4)` | `0.25` |
| **Floor Division** | `//` | Divides and **rounds down** to the nearest whole integer. | `print(1 // 4)` | `0` |

```python
# Standard division (always results in float)
print(1 / 4)         # Output: 0.25
print(1.0 / 4.0)     # Output: 0.25

# Floor division (rounds down to the nearest whole number)
print(1 // 4)        # Output: 0 (integer)
print(1.0 // 4.0)    # Output: 0.0 (float maintaining decimal notation)
```

---

# 5. Boolean (`bool`)

> [!info] Definition
> A **Boolean** represents a logical state that can evaluate to only one of two values: **`True`** or **`False`**.

- Boolean values are capitalized and **never** enclosed in quotation marks (`True` vs `"True"`).
- Often generated dynamically as the result of conditional logic or numerical comparisons.

```python
# Direct Boolean assignment
is_admin = True
is_locked = False

print(True)
# Output: True

# Generating Booleans via comparison operators
print(9 > 10)    # Output: False
print(5 == 5)    # Output: True
print(40 <= 50)  # Output: True
```

---

# Additional Data Types & Data Structures

Beyond the primary types, Python includes three powerful data structures for grouping and organizing information:

```
┌────────────────────────────────────────────────────────────────────────┐
│                     ADDITIONAL DATA STRUCTURES                         │
├─────────────┬─────────────┬───────────────────┬────────────────────────┤
│ TYPE        │ SYNTAX      │ MUTABILITY        │ KEY CHARACTERISTIC     │
├─────────────┼─────────────┼───────────────────┼────────────────────────┤
│ Tuple       │ `(...)`     │ Immutable (fixed) │ Ordered, memory-lean   │
│ Dictionary  │ `{k: v}`    │ Mutable           │ Key-Value mappings     │
│ Set         │ `{...}`     │ Mutable           │ Unordered, unique only │
└─────────────┴─────────────┴───────────────────┴────────────────────────┘
```

---

## 1. Tuple (`tuple`)

> [!info] Definition
> A **tuple** is an ordered collection of data elements enclosed in parentheses (`(...)`) that **cannot be changed (immutable)** after creation.

- **Immutability:** Elements cannot be added, modified, or removed once initialized.
- **Cybersecurity Application:** Storing static system parameters, cryptographic hashes, or software identifiers to guarantee they cannot be tampered with while processing an **Access Control List (ACL)**.
- **Performance:** Tuples consume less memory than lists, making them optimal for large, read-only datasets.

```python
# Tuples of various types
approved_hashes = ("wjaffrey", "arutley", "dkot")
status_codes = (46, 2, 13, 2, 8, 0, 0)
flags = (True, False, True, True)

# Mixed-type tuple
system_record = ("wjaffrey", 13, True)

print(approved_hashes)
# Output: ('wjaffrey', 'arutley', 'dkot')
```

---

## 2. Dictionary (`dict`)

> [!info] Definition
> A **dictionary** is an associative data structure consisting of **key-value pairs** enclosed in curly brackets (`{...}`).

- Each `key` is separated from its associated `value` by a colon (`:`).
- Individual pairs are separated by commas.
- Keys must be unique and provide fast, predictable data retrieval.
- **Cybersecurity Application:** Mapping user IDs to privilege levels, IP addresses to geo-locations, or HTTP status codes to descriptions.

```python
# Dictionary mapping numeric keys to building locations
facility_zones = {
    1: "East",
    2: "West",
    3: "North",
    4: "South"
}

# User account metadata dictionary
user_profile = {
    "username": "drosas",
    "role": "Security Analyst",
    "access_level": 3,
    "mfa_enabled": True
}

print(facility_zones[1])
# Output: East
```

---

## 3. Set (`set`)

> [!info] Definition
> A **set** is an unordered collection of **unique** values enclosed in curly brackets (`{...}`).

- **Duplicate Elimination:** Sets automatically discard duplicate entries upon creation.
- **Cybersecurity Application:** Isolating unique source IPs from a massive web server log containing thousands of repeated access attempts.

```python
# Set containing unique usernames
analyst_accounts = {"jlanksy", "drosas", "nmason"}

# Automatic deduplication example
raw_ips = ["192.168.1.1", "10.0.0.1", "192.168.1.1", "172.16.0.5", "10.0.0.1"]
unique_ips = set(raw_ips)

print(unique_ips)
# Output: {'192.168.1.1', '10.0.0.1', '172.16.0.5'}
```

---

# Data Structure Comparison Matrix

| Data Structure | Delimiter Syntax | Mutability | Ordering | Allows Duplicates? | Primary Security Purpose |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **List** | Square brackets `[]` | **Mutable** | Ordered | Yes | Collecting sequence of events, editable logs |
| **Tuple** | Parentheses `()` | **Immutable** | Ordered | Yes | Tamper-proof software IDs, fixed ACL constants |
| **Dictionary** | Curly brackets `{k: v}` | **Mutable** | Key-Mapped | Keys: No, Values: Yes | User profile lookup, IP-to-threat score mapping |
| **Set** | Curly brackets `{}` | **Mutable** | Unordered | **No** (Unique only) | Deduplicating raw firewall IPs, unique users |

---

# Key Terms at a Glance

| Term | Meaning |
| :--- | :--- |
| **Data Type** | A category classifying a particular type of data and defining valid operations. |
| **String (`str`)** | An ordered sequence of characters wrapped in quotes. |
| **List (`list`)** | A mutable, ordered collection of elements in square brackets. |
| **Integer (`int`)** | A whole numeric value without decimals. |
| **Float (`float`)** | A numeric value containing decimal points. |
| **Boolean (`bool`)** | A binary logical value (`True` or `False`). |
| **Floor Division (`//`)** | Mathematical division that rounds down to the nearest whole integer. |
| **Tuple (`tuple`)** | An immutable, ordered collection of elements in parentheses. |
| **Dictionary (`dict`)** | A collection of associative key-value pairs in curly braces. |
| **Set (`set`)** | An unordered collection of unique elements with no duplicates. |

---

# Exam Tips

> [!tip] Key Takeaways for the Exam
> - **Strings & Booleans in Quotes:** Numbers or Booleans inside quotes (e.g., `"5.0"` or `"True"`) are treated as **strings**, not numeric or Boolean types.
> - **Division Output:** Standard division (`/`) **always produces a float**, while floor division (`//`) rounds down to the whole integer.
> - **List vs. Tuple:** Lists (`[...]`) can be modified (**mutable**); tuples (`(...)`) **cannot be changed** (**immutable**).
> - **Dictionary vs. Set:** Both use `{...}`, but dictionaries contain **colons** separating key-value pairs (`{key: value}`), whereas sets contain single unique items (`{item1, item2}`).
> - **Set Uniqueness:** Adding duplicate values to a set automatically removes the redundancy.

---

## Related Notes

- [[Conditional Statements in Python]]
- [[Iterative Statements in Python]]
- [[Defining and Calling Functions in Python]]
- [[Parameters, Return Statements, and Variable Scope in Python]]
- [[Built-in Functions in Python]]
- [[Python Variables and Naming Conventions]]
- [[Programming and Python in Cybersecurity]]
- [[Python Environments and Notebooks]]
- [[Tools and their purposes]]
- [[Logs and SIEM Tools]]
- [[Cybersecurity Fundamentals]]
