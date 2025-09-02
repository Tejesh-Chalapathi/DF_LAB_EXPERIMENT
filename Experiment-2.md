# Experiment - 2
# Recover deleted or damaged files from a storage device using Test Disk
 

## Aim  
To recover deleted or damaged files from a storage device using **TestDisk**, a forensic recovery tool.  

---

## Description  
In digital forensics, recovering deleted or corrupted files is an essential step during investigations. When files are deleted, their entries are removed from the file system, but the actual data often remains on the storage media until overwritten. TestDisk is an open-source forensic tool designed to recover lost partitions, fix disk errors, and restore deleted files.  

In this experiment, we use TestDisk to identify and restore deleted or damaged files from a storage device, ensuring data integrity for forensic analysis.  

---


## Tools & Equipment Used
- Test disk (Software)

- Source Drive: A USB flash drive or hard disk containing data.

- Destination Drive: Internal hard drive is enough with sufficient free space to store the recovered data

---

## Procedure  

**Launch TestDisk**  
   - Open the TestDisk tool (from command line or executable).  
   ![Fig-1](<Output Screenshot/2-1.png>)

   - Run it with administrative privileges for full access.


**Select Create/Append Log**  
   - On startup, choose **Create** to generate a log file for documentation.  
    ![Fig-2](<Output Screenshot/2-2.png>)


**Choose the Storage Device**  
   - TestDisk lists all available storage devices.
    ![Fig-3](<Output Screenshot/2-3.png>)

   - Use the arrow keys to select the target device.  


**Select Partition Table Type**  
   - TestDisk detects the partition table type (e.g., Intel/MBR, EFI GPT).
    ![Fig-4](<Output Screenshot/2-4.png>)

   - Confirm the suggestion by pressing **Enter**. 


**Analyze the Disk**  
   - Select **Analyse** → Quick Search to find lost partitions.  
   ![Fig-5](<Output Screenshot/2-5.png>)

   - Use **Deeper Search** if needed. 
    ![Fig-6](<Output Screenshot/2-6.png>)
 

**Access Advanced Options**  
   - Go to **Advanced → File System Utilities**. 
    ![Fig-7](<Output Screenshot/2-7.png>)

   - Select the partition where files were deleted.

   - Press **Enter** to view files.  
 

**Recover Deleted Files**  
   - Deleted files are shown in red. 
    ![Fig-8](<Output Screenshot/2-8.png>)

   - Highlight a file and press **C** (copy) to recover. 
    ![Fig-9](<Output Screenshot/2-9.png>)

   - Choose a **different drive** as the destination to avoid overwriting data.  
 

**Verify Recovered Files**  
   - Open the destination folder and check if the files were restored correctly.

   - Document the recovery in the log file.  
     ![Fig-10](<Output Screenshot/2-10.png>)
---

## Result  
Deleted or damaged files were successfully recovered from the storage device using TestDisk, and their integrity was preserved for forensic analysis.  
