\# Week 3 — Module 1: Password Cracking with John the Ripper



\## Objective



The objective of this module was to understand and perform a password-recovery exercise on a password-protected PDF using \*\*John the Ripper (JTR)\*\* and the \*\*Johnny graphical interface\*\* in a Windows lab environment.



\## Tools Used



\* John the Ripper (JTR)

\* Johnny GUI

\* Windows

\* Password-protected PDF



\## Lab Workflow



```text

Password-Protected PDF

&#x20;       ↓

PDF Hash Extraction

&#x20;       ↓

$pdf$ Hash

&#x20;       ↓

hash1.txt

&#x20;       ↓

Johnny

&#x20;       ↓

Start New Attack

&#x20;       ↓

Password Recovered

&#x20;       ↓

PDF Successfully Opened

```



\## 1. Verify John the Ripper



John the Ripper was installed and verified from the Windows command line.



The `john.exe --help` command was used to confirm that John the Ripper was working correctly.



!\[JTR Working](screenshots/01-jtr-working.png)



\## 2. Configure Johnny



Johnny was configured to use the `john.exe` executable located in the JTR `run` directory.



!\[Johnny Configuration](screenshots/02-johnny-configuration.png)



\## 3. Extract the PDF Hash



The password-protected PDF was processed to obtain the PDF password-verification hash.



The extracted hash uses the `$pdf$` format.



!\[PDF Hash](screenshots/03-pdf-hash.png)



> Note: Sensitive hash information has been masked in the public documentation.



\## 4. Password Recovery



The extracted hash was saved as `hash1.txt`, loaded into Johnny, and a new attack was started.



!\[Password Recovery](screenshots/04-password-recovered.png)



> Note: The recovered password has been masked in the public documentation.



\## 5. Verify the Recovered Password



The recovered password was used to open the protected PDF successfully.



!\[PDF Unlocked](screenshots/05-pdf-unlocked.png)



\## Result



The Week 3 Module 1 lab was successfully completed.



The password-protected PDF was processed using John the Ripper and Johnny, and the recovered password was verified by successfully opening the PDF.



\## Key Learning



\* Understanding John the Ripper (JTR)

\* Understanding the Johnny graphical interface

\* Understanding PDF password-verification hashes

\* Extracting and storing a PDF hash

\* Loading a hash into Johnny

\* Performing a password-recovery exercise

\* Verifying the recovered password



\## Evidence



The five screenshots in this folder document the major stages of the lab:



1\. JTR working

2\. Johnny configuration

3\. PDF hash extraction

4\. Password recovery

5\. PDF successfully unlocked



\## Security Note



This exercise was performed as part of an authorized cybersecurity lab. Sensitive information such as the complete hash and recovered password has not been exposed in the public repository.



