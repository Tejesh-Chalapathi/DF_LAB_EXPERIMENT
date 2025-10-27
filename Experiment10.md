# Ex.No.10: Use Ghidra to Disassemble and Analyze the Malware Code

---

## Project Objectives :

* To provide a hands-on guide to disassembling and analyzing malware with **Ghidra**.
* To enable readers to recognize common malware functionalities, such as **persistence mechanisms**, **anti-analysis techniques**, and **network communications**.
* To equip users with the skills to interpret low-level assembly code and understand high-level behaviors using Ghidra's decompiler.

---

## Prerequisites :

* **Ghidra:** Installed and configured (requires Java Development Kit - JDK).
* **Virtual Machine (VM):** A secure, isolated, and virtualized environment (e.g., VMWare, VirtualBox) to safely handle binaries.
* **Sample Binary:** A benign sample or a controlled, safe hex dump for analysis (due to ethical/safety concerns).


---

## Project Outline (GitHub Repository Components)

A typical project structure for this analysis exercise would include the following components:

### 1. Repository Root :

| File/Folder | Description |
| :--- | :--- |
| `README.md` | Provides an overview of Ghidra, project requirements, and an outline of the analysis tutorial. |
| `templates/` | Contains the template for documenting the forensic analysis findings. |
| `docs/` | Contains the step-by-step analysis tutorials. |
| `scripts/` | Stores automation scripts for Ghidra (Python/Java). |
| `samples/` | Stores the benign sample binaries or hex dumps for practice. |

---

### 2. Tutorial Steps (`docs/Tutorial_StepX.md`)

Step-by-step instructions on performing static analysis using Ghidra:

#### A. Environment Setup
* Instructions for setting up a virtualized and isolated analysis environment.
* Guide on installing Ghidra and verifying the Java dependency.

<img width="1919" height="1079" alt="10 18" src="https://github.com/user-attachments/assets/b680f3fc-a76d-4807-a424-0231451ddaa2" />


#### B. Initial Analysis
* **Loading the Binary:** How to launch Ghidra, create a new project, and import the sample binary.
* **Auto-Analysis:** How to run the initial Ghidra auto-analysis and select appropriate analyzers.
* **Identifying Entry Points:** Locating the main function or the binary's execution starting point.

<img width="1180" height="893" alt="10 15" src="https://github.com/user-attachments/assets/ad5a2d82-3a35-43d6-8f00-98ff8738f6ba" />


<img width="758" height="571" alt="10 14" src="https://github.com/user-attachments/assets/f3015e75-b1c5-4721-a1df-c75c1af4badc" />


#### C. Function Analysis
* **Decompilation:** Using Ghidra's Decompiler window to translate assembly into high-level C-like code.
* **Function Identification:** Methods for renaming and analyzing critical functions to understand their purpose.
* **Cross-Referencing (XREF):** Utilizing Ghidra's cross-referencing features to trace where a function is called or where a variable is used.

<img width="1176" height="898" alt="10 11" src="https://github.com/user-attachments/assets/f286577d-c059-4ed4-ac06-f4ec730231f5" />


<img width="1191" height="874" alt="10 10" src="https://github.com/user-attachments/assets/1e5550cd-5a43-4634-969d-a8d11f5b2184" />


#### D. String and Import Analysis
* **Locating Strings:** Using the **Defined Strings** window to find meaningful static strings (e.g., URLs, file paths, registry keys) that indicate malicious behavior.
* **Interpreting Imports:** Analyzing the **Import Table** to identify relevant imported functions (e.g., `CreateFileA`, `URLDownloadToFile`, `RegSetValueEx`) that suggest malware functionality.

<img width="1173" height="885" alt="10 9" src="https://github.com/user-attachments/assets/4e344b93-40db-4a11-b7ea-f19aedbac814" />

<img width="1208" height="989" alt="10 7" src="https://github.com/user-attachments/assets/be096a02-aa4c-476a-8d65-7d07c6fc651a" />


#### E. Advanced Techniques (Optional)
* Introduction to using Ghidra's **Control Flow Graphs (CFGs)** for visualizing program execution flow.
* Examples of writing and running custom Ghidra scripts (Python/Java) for automation.

---

### 3. Example Automation Scripts (`scripts/`)

Scripts using Ghidra's API to automate repetitive analysis tasks:

| Script Example | Purpose |
| :--- | :--- |
| `extract_strings.py` | Automates the extraction and listing of all unique string references in the binary. |
| `network_analysis.py` | Identifies and flags functions that contain network-related API calls (e.g., `socket`, `connect`, `send`). |
| `label_functions.py` | Automates the labeling of functions and data segments based on known malicious patterns (e.g., file system manipulation, registry edits). |

---

### 4. Sample Data (`samples/`)

* **Benign Binary or Hex Dump:** Provide safe files for users to practice the disassembly steps.
    * *Example:* `benign_sample1.bin` (A simple C program that mimics system calls or file writing but contains no harmful payload).

<img width="1882" height="1078" alt="10 4" src="https://github.com/user-attachments/assets/0144283f-b16f-442a-b4a6-d85f10e01ab9" />


<img width="1484" height="885" alt="10 3" src="https://github.com/user-attachments/assets/aa426beb-ccc2-486e-92b0-eb484c93fc54" />

<img width="1913" height="1075" alt="10 2" src="https://github.com/user-attachments/assets/16504555-58fa-4b7d-861d-bb79f29fec11" />


---

### 5. Report Template

A template to structure and document the findings of the Ghidra analysis:

1.  **Summary of Analysis:** Brief description of the suspected malware and the scope of the analysis.
2.  **Function Analysis:** Detailed summary of key functions, their purpose, and forensic findings.
3.  **Behavioral Indicators:** Summary of observed behaviors (e.g., persistence, communication protocols, anti-analysis checks).
4.  **Recommendations:** Suggestions for containment, eradication, or further analysis (e.g., dynamic analysis).
