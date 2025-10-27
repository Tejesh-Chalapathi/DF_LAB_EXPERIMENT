# Experiment 7: Use AFLogical OSE to Extract Data from an Android Device

---

## Aim

To perform logical extraction of contacts, SMS, MMS, and call logs from an Android device using AFLogical OSE, supporting forensic investigations without requiring root access.

---

## Description

AFLogical OSE (Open Source Edition) is a forensic tool for collecting key data from Android devices. It focuses on logical acquisition—retrieving structured information (e.g., contacts, messages) via the device's APIs, rather than direct file system access. The process uses ADB (Android Debug Bridge) for communication and ensures extracted data is conveniently exported in CSV format for further analysis.

---

## Tools & Equipment Used

- AFLogical OSE (from [GitHub](https://github.com/den4uk/AFLogical-OSE))
- Java (installed on host computer)
- Android Debug Bridge (ADB) platform tools
- USB cable
- Android device (with USB Debugging enabled)
- Computer (Windows, macOS, or Linux)

---

## Procedure

### Step 1: Prepare Your Environment

- Download AFLogical OSE from GitHub or clone the repository.
- Install Java if not already installed.
- Download and install ADB platform tools; add them to your system’s PATH.
- Enable USB Debugging on the Android device via Settings > Developer Options.

### Step 2: Connect the Android Device

- Use a USB cable to connect the Android device to your computer.
- Verify the ADB connection:
Ensure the device appears in the output list.

### Step 3: Extract Data Using AFLogical OSE

- Navigate to the AFLogical OSE directory.
- Install the AFLogical app on the device:
- Launch the app on the Android device.
- Choose desired data types (contacts, SMS, MMS, call logs) from the app interface.
- Start the extraction. Data is saved as CSV files in the `/sdcard/aflogical` directory.

### Step 4: Transfer Extracted Data to Your Computer

- Pull extracted data using ADB:
- Verify the contents and integrity of the CSV files in the destination directory.

### Step 5: Analyze the Extracted Data

- Open the extracted CSV files using Excel, Google Sheets, or a text editor.
- Review entries for relevant contacts, messages, and call logs.
- Document findings and organize a report as needed.

### Step 6: Clean Up

- Uninstall the AFLogical app from the device:
- Safely disconnect the Android device.

---

## Result

Data from the Android device—including contacts, SMS, MMS, and call logs—was successfully extracted using AFLogical OSE, transferred to the computer, and analyzed in CSV format for forensic purposes. This procedure supports comprehensive investigations when access to logical data is required without rooting the device.

---
