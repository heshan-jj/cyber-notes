---
tags:
  - cybersecurity
  - python
  - programming
  - python-environments
  - google-cert
  - module-01
  - course-07
aliases:
  - Python Environments
  - Python Coding Environments
  - Notebooks, IDEs, and the Command Line
  - Running Python Code
  - Jupyter and Google Colab
---

> [!abstract] Python Coding Environments
> Python code can be written and executed across several distinct environments, including **Notebooks**, **Integrated Development Environments (IDEs)**, and the **Command Line Interface (CLI)**. In introductory security courses and data workflows, **Notebooks** (such as Jupyter Notebook and Google Colab) serve as the primary medium, providing an interactive, cell-based environment combining executable code with rich **Markdown** documentation.

---

# Python Execution Environments Overview

Developers and security analysts select environments based on their workflow needs—ranging from exploratory analysis to enterprise software engineering:

```
┌────────────────────────────────────────────────────────────────────────┐
│                      PYTHON EXECUTION ENVIRONMENTS                     │
├───────────────────┬───────────────────────────┬────────────────────────┤
│    1. NOTEBOOKS   │         2. IDEs           │    3. COMMAND LINE     │
│ Interactive cells │ Full-featured development │ Direct execution &     │
│ (Code + Markdown) │ apps (GUI, debug, lint)   │ terminal scripting     │
└───────────────────┴───────────────────────────┴────────────────────────┘
```

---

# 1. Notebooks

> [!info] Definition
> A **notebook** is an online, interactive interface used for writing, storing, running, and documenting code.

Notebooks are structured into distinct units called **cells**. Content within a notebook is organized into two primary cell types:

```
┌────────────────────────────────────────────────────────────────────────┐
│ 📝 MARKDOWN CELL: Explanatory text, headers, and documentation         │
├────────────────────────────────────────────────────────────────────────┤
│ [▶] CODE CELL: Python code statement (e.g., print("Security Log"))    │
│ ────────────────────────────────────────────────────────────────────── │
│ 📤 OUTPUT: Security Log                                                │
└────────────────────────────────────────────────────────────────────────┘
```

### Cell Types in a Notebook

| Cell Type | Primary Purpose | How It Works |
| :--- | :--- | :--- |
| **Code Cells** | Writing and executing code | Users enter Python code and trigger execution (often via a **Play button** `[▶]` or `Shift + Enter`). The output generates immediately below the cell. |
| **Markdown Cells** | Documenting and explaining code | Formats plain text using the **Markdown language** to create structured headings, bullet points, hyperlinks, and styled notes around the code. |

### Common Notebook Platforms

- **[Jupyter Notebook](https://jupyter.org/about):** An open-source web application that allows users to create and share documents containing live code, visualizations, and narrative text across multiple programming languages.
- **[Google Colaboratory (Google Colab)](https://colab.research.google.com/):** A cloud-hosted Jupyter notebook environment provided by Google that runs directly in the browser with zero initial configuration and built-in sharing capabilities.

---

# 2. Integrated Development Environments (IDEs)

> [!info] Definition
> An **Integrated Development Environment (IDE)** is a comprehensive software application designed for writing code, offering built-in editing assistance, debugging capabilities, and automated error-correction tools.

Key characteristics of IDEs include:
- **Graphical User Interface (GUI):** Provides dedicated panels for project file exploration, package management, source control, and configuration.
- **Code Assistance & Linter Tools:** Highlights syntax errors in real-time, suggests autocompletions, and formats code according to industry standards.
- **Customizability:** Allows programmers to install extensions, themes, and customized toolchains.
- **Examples:** Visual Studio Code (VS Code), PyCharm, and Eclipse.

---

# 3. The Command Line (CLI)

> [!info] Definition
> A **Command-Line Interface (CLI)** is a text-based user interface used to interact directly with the operating system and execute programs via typed commands.

The command line is indispensable for security professionals, especially when managing remote servers and automated scripts:
- **File & Directory Access:** Allows navigation across all storage drives and directories to locate Python scripts (`.py` files).
- **Direct Script Execution:** Runs Python programs directly through system interpreters (e.g., `python3 script.py`).
- **Terminal File Editors:** Enables creating and editing Python files on headless systems using built-in terminal text editors such as **Nano** or **Vim**.

---

# Environment Comparison Matrix

| Environment | Interface Type | Best Used For | Key Strengths |
| :--- | :--- | :--- | :--- |
| **Notebooks** | Web-based / Cell-based | Learning, data analysis, quick prototyping, interactive reports | Step-by-step execution, inline output, rich Markdown documentation |
| **IDEs** | Desktop GUI Application | Complex software development, large security codebases | Advanced debugging, automated error correction, multi-file navigation |
| **Command Line (CLI)** | Text-based Terminal | Automated scripts, cron jobs, remote Linux server administration | Lightweight, fast, universal across headless servers and containers |

---

# Key Terms at a Glance

| Term | Meaning |
| :--- | :--- |
| **Notebook** | An online interface for writing, storing, running, and documenting code. |
| **Code Cell** | A notebook block where programming code is written and executed. |
| **Markdown Cell** | A notebook block used to format text and document code logic. |
| **Markdown** | A lightweight markup language used for formatting plain text. |
| **IDE** | A dedicated software suite providing coding, editing assistance, and debugging tools. |
| **CLI** | A text-based interface for issuing commands to the operating system. |

---

# Exam Tips

> [!tip] Key Takeaways for the Exam
> - **Notebook Cell Roles:** **Code cells** execute instructions and display output below; **Markdown cells** provide narrative formatting and documentation.
> - **Execution Mechanism:** Code cells are triggered using an in-cell **play button** or keyboard shortcut (`Shift + Enter`).
> - **Popular Notebook Platforms:** **Jupyter Notebook** and **Google Colaboratory (Colab)** support running Python alongside other languages.
> - **IDE Features:** IDEs feature a **GUI** with built-in **error correction** and editing assistance.
> - **CLI Utility:** The CLI allows accessing files/directories on the hard drive, opening terminal text editors, and running scripts without a graphical desktop.

---

## Related Notes

- [[Python Variables and Naming Conventions]]
- [[Python Data Types]]
- [[Programming and Python in Cybersecurity]]
- [[Tools and their purposes]]
- [[Common Security Tools]]
- [[Cybersecurity Fundamentals]]
