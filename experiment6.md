## Ex.No.6: Use Sleuth Kit to Analyze Digital Evidence

### Description :
The **Sleuth Kit (TSK)** is a suite of command-line tools for analyzing disk images and recovering digital evidence. This guide outlines the steps to use TSK on a Windows machine for digital forensics.

---

### 1. Install Sleuth Kit

1.  **Download Sleuth Kit:**
    * Visit the official Sleuth Kit website or the provided Google Drive link (https://drive.google.com/drive/u/1/folders/1ilSFY7Tqn2L7AjQGhq8yJ8kixc_xTU-v) and download the latest Windows version.
2.  **Install Sleuth Kit:**
    * Run the installer and follow the instructions to install Sleuth Kit on your Windows machine.

---

### 2. Acquire the Disk Image

Before analysis, a **bit-by-bit copy** (disk image) of the storage device evidence is required.

1.  **Create Disk Image:**
    * Use a forensic tool like **FTK Imager** or **dd** to create a bit-by-bit copy.
    * Ensure the image is in a TSK-supported format, such as **.dd**, **.raw**, **.img**, or **.E01**.
2.  **Download Files (for this exercise):**
    * Download the following files from the Google Drive:
        * `4Dell Latitude CPi.E01`
        * `4Dell Latitude CPi.E02`

---

### 3. Mount the Disk Image (Optional)

Mounting the disk image simplifies the navigation and analysis of the file system.

1.  **Mount the Image:**
    * Use a tool like **OSFMount** to mount the image as a virtual drive on your Windows system.
    * *Note: This step is optional but can aid in easy file system navigation.*

---

### 4. Analyze the File System

Use the Sleuth Kit command-line tools to examine the file system structure and locate evidence.

1.  **Navigate to the Sleuth Kit Directory:**
    * Open the **Command Prompt** (cmd) and use the `cd` command to navigate to the directory where Sleuth Kit is installed (e.g., `C:\Program Files\SleuthKit\bin`).

2.  **Identify File System Type with `fsstat`:**
    * **Command:**
        ```arduino
        fsstat [image file] > filesystem_info.txt
        ```
    * **Purpose:** This command outputs detailed information about the file system, which is crucial for structural understanding.

3.  **List Partitions with `mmls`:**
    * **Command:**
        ```arduino
        mmls [image file] > partitions.txt
        ```
    * **Purpose:** This command lists the partitions present within the image file.

4.  **Analyze File System with `fls`:**
    * **Command:**
        ```arduino
        fls -r [image file] > file_list.txt
        ```
    * **Purpose:** The `-r` flag recursively lists files and directories in the file system, along with their metadata (inode numbers).

5.  **Recover Deleted Files with `icat`:**
    * **Command:**
        ```css
        icat [image file] [inode number] > [output file]
        ```
    * **Purpose:** To extract a specific file, replace `[inode number]` with the inode found from the `fls` output.

---

### 5. Analyze Metadata

Extract file metadata to gain insight into a file's history, creation, and usage.

1.  **View Metadata with `istat`:**
    * **Command:**
        ```css
        istat [image file] [inode number] > metadata_info.txt
        ```
    * **Purpose:** Provides detailed information about a file, including **timestamps (MAC times)**, size, and allocation status.

---

### 6. Timeline Analysis (Optional)

Creating a timeline of file activity is vital for reconstructing events.

1.  **Generate a Body File using `fls`:**
    * **Command:**
        ```css
        fls -m / -r [image file] > body.txt
        ```
    * **Purpose:** Generates a **body file** (`body.txt`) containing the essential metadata (MAC times, file paths) needed for timeline analysis.

2.  **Create Timeline with `mactime`:**
    * **Command:**
        ```css
        mactime -b body.txt > timeline.txt
        ```
    * **Purpose:** Processes the body file to create a **timeline** (`timeline.txt`) sorted by the Modified, Accessed, and Changed (MAC) times of the files.

---

### 7. Generate a Report

Document the findings by compiling all the collected data into a comprehensive report.

1.  **Compile the Data:**
    * Gather all the output files (e.g., `filesystem_info.txt`, `partitions.txt`, `file_list.txt`, `metadata_info.txt`, `timeline.txt`).
2.  **Analyze and Document:**
    * Review the findings, highlight crucial evidence, and write a report summarizing the investigation's methodology and results.

---

### 8. Finalize and Store Evidence

Ensure all evidence and reports are securely managed to maintain integrity and follow the chain of custody.

1.  **Archive Evidence:**
    * Use a secure, verifiable method to **archive** the original disk image and the analysis results.
2.  **Store Securely:**
    * Store the archived data in a secure location, strictly adhering to the **chain of custody** procedures.
