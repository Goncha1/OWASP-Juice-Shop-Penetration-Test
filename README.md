#Intern-Intelligence OWASP-Juice-Shop-Penetration-Test

This repository contains the details of the penetration testing I performed on the OWASP Juice Shop application, showcasing various vulnerabilities.

## Objective
The goal was to identify vulnerabilities in the OWASP Juice Shop by simulating real-world attack vectors.

## Tools and Technologies Used
- OWASP Juice Shop
- Kali Linux
- Burp Suite
- TryHackMe
  
Techniques:
-Manual Testing
-Automated Scanning
-Payload Injection

## Vulnerabilities Discovered

 1. SQL Injection
- Payload Used: `' OR 1=1 --`
- Details: This payload was used to bypass authentication on the login page. It works by manipulating the SQL query to always return true:
  #Screenshots of the penetration test in action:
![e3c84bc9-c784-4e0c-b489-82d1c16afbea](https://github.com/user-attachments/assets/c6ef79a8-a03a-40bb-9849-9cd3ec15dfbf)

  ```sql
  SELECT * FROM users WHERE email='' OR 1=1 --

- Result: Gained unauthorized access to the application.

  2. Brute Force Attack
- Tool Used: Burp Suite (Sniper Mode)

Details: Automated password guessing using Burp Suite’s Sniper mode with a wordlist.(When the status code:200)

Result: Successfully identified the correct password through automation.
  #Screenshots of the penetration test in action:
![a1bf6e57-92f0-4e80-b0b4-6bb77737ecdd](https://github.com/user-attachments/assets/e7df918e-b53c-4a41-8e72-8dacacb5bcb3)


3. Sensitive Data Exposure
Exploit: Discovered sensitive information by accessing a publicly available /ftp/ directory from the "About" page.

Impact: Exposed sensitive files and data due to improper file permissions.

4. DOM XSS
Payload Used: <iframe src="javascript:alert('xss')">

Details: Injected this payload into the search bar, triggering a JavaScript alert.

Impact: Demonstrated a vulnerability in how user input is handled on the client-side.
   #Screenshots of the penetration test in action:
![e1185c5d-8e19-4c13-b53a-02f807ca0d84](https://github.com/user-attachments/assets/897d770c-1568-45c0-947c-d4e5afe986db)

5. Reflected XSS
Payload Used: <iframe src="javascript:alert('xss')">

Details: Injected this payload into the URL parameters (id=), triggering JavaScript execution.

Impact: Highlighted the lack of input sanitization in URL parameters.

6. Broken Access Control
Exploit: Inspected the main-es2015.js file and discovered the path /administration. This allowed me to navigate to restricted pages without proper authorization.

Impact: Gained access to admin-only sections.

7. Poison Null Byte Exploit
Payload Used: %2500

Details: Appended %2500 (null byte) to the filename package.json.bak to bypass file upload restrictions.

Impact: Bypassed the file extension checks to upload potentially harmful files.


**Here is the link to the entire penetration testing video** https://drive.google.com/file/d/1EQi780zgE7Kqi85KK_oE6oFWeJs3Kqlj/view?usp=sharing
