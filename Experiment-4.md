# Experiment 4 : Analyze Email Headers and Detect Email Spoofing using MHA (Mail Header Analyzer)

## Aim 🎯
The aim of this experiment is to analyze an email's full header to determine its true origin and detect if it has been spoofed. This process is a key step in digital forensics and cybersecurity investigations, as it helps to identify malicious emails (like phishing attempts) that deceptively appear to come from a legitimate sender.

## Description 📝
Email headers contain a wealth of metadata that tracks an email's journey from sender to recipient. While the "From" field is easily manipulated by attackers, the full header, which includes a series of "Received" lines, is much harder to forge. Each "Received" line is added by a mail server as the email passes through it, creating a chronological trail of its path. By analyzing this trail and other key fields, one can unmask the true source of an email. MHA (Message Header Analyzer) is a useful, free online tool that parses this raw, often confusing text into a clean, human-readable format, highlighting important details like IP addresses, server information, and authentication results (SPF, DKIM, and DMARC).

## Tools & Equipment Used 🛠️
Computer: Any computer with a web browser and an internet connection.

Email Client: An email program (like Outlook, Gmail, or Apple Mail) that allows you to view an email's full headers.

MHA (Message Header Analyzer): A web-based tool provided by Microsoft for analyzing email headers. The tool can be accessed at https://mha.azurewebsites.net/.

## Procedure 👩‍🔬
Retrieve the Full Email Header:
![Fig-1](<Output Screenshot/4-1.png>)
Open the suspicious email in your email client.

Find the option to view the "original" or "full" headers. This process varies by client. For example, in Gmail, you can click the three dots next to the reply button and select "Show original." In Outlook, you might find it under "File" then "Properties."
![Fig-2](<Output Screenshot/4-2.png>)
Once the raw header is displayed, copy the entire block of text.

Analyze with MHA:
![Fig-3](<Output Screenshot/4-3.png>)
Open your web browser and navigate to the MHA tool at https://mha.azurewebsites.net/.

Paste the copied header text into the text box provided.

Click the Analyze header button.
![fig-4](<Output Screenshot/4-4.png>)
Interpreting the Results:
![Fig-5](<Output Screenshot/4-5.png>)
MHA will parse the header and present a summarized, easy-to-read report.

Received Hops: Look at the "Received" headers. They are listed in reverse chronological order, so the first one at the top is the last server the email passed through, and the last "Received" header at the bottom is the originating server. Check to see if the originating server's domain and IP address match the purported sender's email address. A mismatch is a major red flag for spoofing.
![Fig-6](<Output Screenshot/4-6.png>)
Sender Details: Examine the From field and compare it with the Sender field (if present) and the Return-Path. These values can often be a mix of legitimate-looking names and forged email addresses.

Authentication Results: Look for the SPF, DKIM, and DMARC results.
![Fig-7](<Output Screenshot/4-7.png>)
SPF (Sender Policy Framework): A "Pass" result means the email came from an IP address authorized by the sending domain's owner. A "Fail" is a strong indicator of spoofing.

DKIM (DomainKeys Identified Mail): A "Pass" result means the email's signature is valid, confirming it was not tampered with during transit. A "Fail" or "None" is suspicious.

DMARC (Domain-based Message Authentication, Reporting, and Conformance): This policy instructs the receiving server on how to handle emails based on the SPF and DKIM results. A "Pass" is good; a "Fail" indicates the message likely violated the sender's policy.

## Results 📊
Spoofing Detection: The analysis successfully identified discrepancies between the "From" address and the actual originating server's IP and domain.

Authentication Failure: The MHA report showed "Fail" results for SPF, DKIM, or DMARC, confirming that the email's authenticity could not be verified.

IP Tracing: The chain of "Received" headers revealed the email's true path, pinpointing the malicious server from which it originated, even though the sender's address was spoofed. This confirms that MHA is a highly effective tool for detecting email spoofing and analyzing headers.
