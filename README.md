**ISBN Checker – SOAP Web Service Test Assets**

**Overview**  
This repository contains **QA documentation** and supporting materials for testing a public **SOAP web service** that validates **ISBN numbers** (book identifiers). The main focus is on the **`IsValidISBN10`** operation, which checks whether a given **ISBN‑10** number is valid and returns a **boolean** result (**true/false**).[web:4][web:12]  

The repository is designed both for **learning purposes** (for new QA/automation testers) and as a small, real example of an **API testing** project.

**About the SOAP ISBN Checker**  
The system under test is the **DataFlex Web Service for testing ISBN Numbers**, hosted at `webservices.daehosting.com`.[web:4]  

Key points about the service:  
- It exposes operations to validate both **ISBN‑10** and **ISBN‑13** numbers.[web:4][web:8]  
- **`IsValidISBN10`** validates a **10‑digit ISBN**; the test is done by calculating a **checksum** based on the first 9 digits and comparing it with the last digit, which can be a number or the letter **`X`**.[web:4][web:12][web:24]  
- **`IsValidISBN13`** validates a **13‑digit ISBN** using a checksum on the first 12 digits and comparing it with the last digit.[web:4][web:8]  
- Each operation returns a simple **boolean result** (**`true`** or **`false`**) to indicate whether the supplied ISBN is valid.[web:12][web:8]  
- The service supports multiple **request/response formats**:  
  - **SOAP 1.1** requests and responses in **XML**.[web:12][web:8]  
  - **SOAP 1.2** requests and responses in **XML**.[web:12][web:8]  
  - **JSON** requests and responses with the same validation logic.[web:12][web:8]  

This makes it a good, simple target for practicing **API / web service testing**.

**Repository Contents**  
(Adjust filenames to match your actual documents.)

- **`Test-Plan-ISBN-Checker.docx`**  
  Formal **test plan** describing **objectives**, **scope**, **test environments**, **types of testing**, **entry/exit criteria**, **risks**, and **approvals** for the ISBN Checker web service.

- **`Test-Plan-ISBN-Checker.pdf`** (optional)  
  **PDF** version of the same test plan for easy viewing.

- **`Test-Strategy-ISBN-Checker.docx`** (planned / optional)  
  High‑level **test strategy** document describing the **overall testing approach**, **test levels**, and **coverage**.

- **`Test-Cases-ISBN-Checker.xlsx`** (planned / optional)  
  Detailed **test cases** derived from the test plan and strategy.

You can update this section as you add more **QA artifacts**.

**What the Test Plan Covers**  
The included **test plan** focuses on:

- **Functional validation** of the **`IsValidISBN10`** web service.  
- **Input combinations** such as:  
  - **Valid ISBN‑10** values.  
  - **Invalid ISBN‑10** values.  
  - **Length errors** (too short / too long).  
  - **Special characters**, **alphabetic characters**, and **empty / null** values.  
  - ISBN‑10 values ending with **`X`**.  
- **Request formats**:  
  - **SOAP 1.1**  
  - **SOAP 1.2**  
  - **JSON** calls to the service.[web:12][web:8]  
- **Response behavior**: verifying that the service returns the **correct boolean value** and uses the **expected response format**.[web:12][web:8]  
- **Test process**:  
  - **Test environment setup**  
  - **Defect reporting procedure**  
  - **Test execution** flow  
  - **Test closure** activities  

The document is written in a **client‑ready formal style**, but with wording simple enough for **junior QA team members** and **freshers** to understand.

**Who This Repository Is For**  

- **QA freshers / trainees** learning how to:  
  - Read and understand a **test plan**.  
  - Translate a test plan into **test cases**.  
  - Test **SOAP / JSON APIs** using tools like **Postman** or **SOAP UI**.  

- **Automation learners** who want a small, well‑scoped **web service** to automate (**API test automation**).  

- **Interview / portfolio** use to showcase understanding of **test planning** for **web services**.

**How to Use This Repository**  

1. **Read the Test Plan**  
   Start with the **test plan document** to understand:  
   - **What** is being tested (the **ISBN validation web service**).  
   - **Which types of testing** are expected (**functional**, **positive/negative**, **boundary**, **input validation**, **API testing**).  
   - **Which environments, tools, and entry/exit criteria** are defined.

2. **Prepare Test Cases (for practice)**  
   Based on the test plan, write your own **test cases** for:  
   - **Valid** and **invalid ISBN‑10** inputs.  
   - Different **request formats** (**SOAP 1.1**, **SOAP 1.2**, **JSON**).  
   - **Edge cases** and **negative scenarios**.

3. **Execute Tests Using Tools**  
   Use **Postman**, **SOAP UI**, or similar tools to:  
   - Send **SOAP/XML** or **JSON** requests to the service.  
   - Verify that the **boolean response** matches your **expected result** for each test case.

4. **Extend the Repository**  
   You can extend this repository by adding:  
   - A dedicated **Test Strategy** document.  
   - Detailed **manual / automation test cases**.  
   - **Automation scripts** (e.g., Postman collections, RestAssured, Karate, etc.).  
   - **Test execution reports** and **defect reports**.

**Notes**  

- The ISBN Checker service is a **public demo SOAP web service** and is commonly used for **learning and practice**.[web:17][web:19]  
- Be mindful not to overload the service with unnecessary **traffic / requests**.
