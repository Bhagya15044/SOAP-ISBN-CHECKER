**Test Plan for Validating ISBN Numbers for Books via SOAP-based Web Service**

* **Objective**

* **Scope**

* **Inclusions**

* **Test Environments**

* **Defect Reporting procedure**

* **Test Strategy**

* **Test Schedule**

* **Test Deliverables**

* **Entry and Exit criteria**

* **Test Execution**

  * **Entry Criteria**

    * **Exit Criteria**

* **Test closure**

  * **Entry Criteria**

    * **Exit Criteria**

      * **Tools**

      * **Risks and Mitigations**

      * **Approvals**

**Objective:** 

The objective of this test plan is to validate the correctness of ISBN numbers (**10**\-digit or **13**\-digit formats) for books through a SOAP-based API. The goal is to ensure the service accurately identifies valid and invalid ISBNs. Any bugs or unexpected behaviour observed during testing will be documented and tracked in JIRA.

**Scope:**

1\. This test plan covers validation of the **ISBN** verification functionality for books, including both positive and negative test scenarios to ensure accurate handling of valid and invalid ISBN inputs.

2\. The testing approach includes API testing using **Postman**, where SOAP-based requests are constructed and executed to validate service responses.

3\.  Testing will be conducted in a stable test environment using tools such as **Postman**, with the required **service URLs, payloads**, and **headers** configured as per the API definition or extracted using developer tools when documentation is unavailable.

4\.  The success of the testing process will be evaluated based on the number and severity of defects found, the time taken to complete testing, and the overall accuracy of the service in detecting valid and invalid ISBNs.

5\.  The scope also outlines the roles and responsibilities of key stakeholders involved in testing, including the test lead, QA engineers responsible for execution, and developers handling defect resolution.

**Inclusions:**

**1.Introduction: **This test plan outlines the strategy and objectives for testing a SOAP-based API that validates ISBN numbers for books. The goal of this testing effort is to ensure that the service accurately identifies valid and invalid ISBNs according to standard formats (ISBN-**10** and ISBN-**13**), handles unexpected inputs gracefully, and complies with the expected request/response structure. This document also details the tools used, test coverage, request configuration, and validation criteria**.**

**2.Test Objectives: **

This section outlines the specific testing objectives, grouped into key categories to ensure complete validation of the ISBN validation service.

**A. Valid Input Testing**

* Validate correct ISBN formats:

  * **ISBN-10** (10-digit valid numbers)

  * **ISBN-13** (13-digit valid numbers)

---

 **B. Invalid Input Testing**

Test the API’s robustness by submitting a variety of invalid inputs, ensuring it correctly identifies and rejects non-compliant values.

| Input Type | Example Value | Purpose |
| :---- | :---- | :---- |
| Alphabetic characters only | "abcdefghij" | Input validation |
| Special characters | "@\#&\*\!$" | Symbol handling |
| Alphanumeric mix | "123abc456" | Mixed-type input check |
| Empty string | "" | Blank field handling |
| Null input | null (programmatic) | Backend handling of null values |
| Fewer than 10 digits | "12345" | Short-length rejection |
| More than 13 digits | "123456789012345" | Excess-length rejection |
| Input with leading/trailing spaces | " 1234567890 " | Whitespace trimming validation |
| Unicode characters (foreign language) | "你好", "مرحبا" | Encoding and character set check |
| Emojis or symbols | "📘🔢1234" | Unicode/emoji rejection |
| Mixed input (symbols \+ digits) | "123书籍456\!" | Complex invalid input pattern rejection |

---

**C. Request Header Configuration Testing**

The API requires specific headers for correct processing. Each of these headers will be validated for correctness, presence, and behavior under incorrect/missing values.

| Header | Description | Example Value |
| :---- | :---- | :---- |
| Content-Type | Specifies the format of the request body | text/xml; charset=utf-8 |
| Accept | Indicates expected response format from server | application/xml |
| SOAP Action | Specifies the intent of the request (in SOAP 1.1, if required) | "http://tempuri.org/ValidateISBN" |
| Authorization | Carries authentication credentials if the service is secured | Basic YWRtaW46cGFzc3dvcmQ= (base64) |
| Cookies | Used if session tracking is required (rare in SOAP) | JSESSIONID=XYZ123... |
| *Custom headers* | Any project-specific headers required by the service | X-Client-ID, X-Env, etc. |

These headers will be tested for:

* Presence and correct values

* Missing or malformed headers

* Behaviour when unauthorized

---

 **D. Response Validation**

* Validate that the response structure is consistent and conforms to expected XML schema

  * Example: \<IsValidISBN10Result\>true\</IsValidISBN10Result\>

* Check that invalid inputs return appropriate error messages or SOAP fault responses

---

**Test Environment**

The test environment defines the necessary tools, access methods, and configurations used to validate the SOAP-based ISBN validation API.

1. **API Testing Tool**

   * All testing will be performed using Postman, where SOAP requests are manually constructed, sent, and verified using appropriate request headers and XML body structure.

2. **SOAP Endpoint & Protocol**

   * The service will be accessed through a defined SOAP endpoint over HTTP or HTTPS protocols, depending on the environment setup.

   * The complete request will include the SOAP envelope in the body and appropriate headers (e.g., Content-Type: text/xml).

3. **Authentication Methods**

   * The API may use one of the following authentication types:

     * **No Authentication –** if publicly accessible

     * **Basic Authentication –** using username and password

     * **Bearer Token Authentication –** using access tokens in the header

   * Each type will be validated as per the configured access policy of the endpoint.

4. **Environment Types**

   * Testing will be executed in the following environment(s), depending on project access and readiness:

     * Development (DEV)

     * User Acceptance Testing (UAT)

     * Production-like Environment (Read-only, if permitted)

5. **Team Access Roles**

   * Access to the environment will be defined as per role:

     * **Testers** – For execution of test scenarios and bug reporting

     * **Developers** – For defect fixing and technical support

     * **Stakeholders/Managers** – For reviewing test status and results (if required)

 **Defect Reporting Procedure**

This section defines how defects will be identified, how they should be reported, and which tools will be used to track them during testing of the ISBN Validation SOAP API.

**1\. Defect Identification Criteria**

A defect will be logged if any of the following behaviours are observed**:**

| Scenario | Explanation |
| :---- | :---- |
| **Incorrect validation result** | The API returns a wrong output for a given ISBN input. 🔹 *Example: Returns true for an invalid 13-digit ISBN.* |
| **Malformed or invalid XML response** | The SOAP response does not follow the correct XML structure or schema. 🔹 *Example: Missing closing tags, incorrect tag names, or invalid nesting**.*** |
| **Missing or incorrect response headers** | Expected headers are absent or contain incorrect values in the response. 🔹 *Example: Content-Type header is missing or set to text/html instead of text/xml.* |
| **Unexpected HTTP status codes** | The API returns HTTP status codes that don't match the expected outcome. 🔹 *Example: For invalid input, it should return 400 Bad Request but returns 200 OK.* |
| **System exception or crash** | The API throws an unhandled exception or crashes. 🔹 *Example: Response returns 500 Internal Server Error due to malformed input.* |
| **Behaviour different from documentation** | The actual behavior of the API differs from what’s specified in the API documentation. 🔹 *Example: Documentation says “returns false for alphabetic input”, but API returns true.* |

**Clarification:**  
“Behaviour deviates from documentation” means — if the service does something different than what the client/BA/API documentation says it should do.  
 Yes — this is a valid defect and important to catch.

**2\.  Steps for Reporting a Defect**

Each defect will be reported following a clear and structured process:

1. Log the defect in the tracking tool (e.g., JIRA) using the project’s standard template.

2. Include the following key details:

   * Defect summary and environment (e.g., UAT, DEV)

   * Step-by-step reproduction steps

   * Expected vs actual result

   * SOAP request (headers \+ body)

   * SOAP response (status \+ body)

   * Authentication used (if any)

3. **Attach supporting evidence:**

   * Postman screenshots

   * Raw XML response

   * Error logs (if available)

Assign to the correct developer/team with appropriate severity and priority**.**

**4\.  Tools for Defect Tracking**

The following tools will be used to report, track, and manage all defects:

| Tool | Purpose |
| :---- | :---- |
| **JIRA** | Primary defect tracking and task management system |
| **Zephyr** | Integrated with JIRA for linking test cases to defects |
|  |  |

 **Test Strategy**

The overall testing strategy for the ISBN Validation SOAP API is focused on ensuring the correctness and reliability of the service response for both valid and invalid ISBN inputs.

**1\. Test Scenario and Test Case Design**

We will begin by identifying test scenarios and developing corresponding test cases based on the features outlined in the scope, such as:

* Validation of 10-digit and 13-digit ISBNs

* Handling of invalid inputs (alphanumeric, special characters, etc.)

* Header and authorization validations

While writing test cases, the following approaches will be used:

*  Positive and Negative Testing

*  Exploratory Testing – Based on tester experience and intuition

*  Error Guessing – Based on common error-prone inputs (e.g., emojis, empty values)

**2\. Types of Testing Performed**

The following testing types will be conducted as part of this project**:**

| Type of Testing | Description |
| :---- | :---- |
| **API Functional Testing** | Verifying that the SOAP service returns correct results for valid/invalid ISBNs. |
| **Negative Testing** | Testing invalid formats, missing headers, special characters, null inputs, etc**.** |
| **Regression Testing** | Ensuring previously working scenarios continue to function after changes or fixes. |
| **Retesting** | Re-validating failed scenarios after defect fixes. |
| **Exploratory Testing** | Unscripted testing to uncover edge-case issues or undocumented behaviour. |
| **User Acceptance Testing (UAT)** | Optional — conducted to validate functionality as per end-user expectations. |

**3\. Defect Reporting and Communication**

* Any defects identified during testing will be logged in JIRA using a standard defect template.

* Daily status updates, including defect reports, will be shared with the development team and project manager via EOD email.

* Regression and retesting cycles will be repeated as needed until the service meets the quality expectations.

**Entry & Exit Criteria (SOAP API Testing)**

**🔹 Requirement Analysis Phase**

| Entry Criteria |
| :---- |
| \- API Documentation is shared by the Product Manager, including:  🔹 Endpoint and host URL  🔹 HTTP method (e.g., POST/GET)  🔹 Headers (e.g., Content-Type, SOAP Action)  🔹 Authorization type (e.g., Basic, Bearer Token)  🔹 Request payload structure (XML)  🔹 Expected response format and status codes  🔹 Sample cURL or Postman collection |
| **\-** User Story or JIRA Ticket is assigned indicating the feature to be tested (e.g., ISBN validation) |

| Exit Criteria |
| :---- |
| \- The QA team has reviewed and understood the API documentation and user story.\- Any open questions are clarified with the Product Manager or Developer.\- Initial list of test scenarios is prepared**.** |

---

**🔹 Test Execution Phase**

| Entry Criteria |
| :---- |
| **\-** Test scenarios and test cases are reviewed and approved internally.\- API endpoint is accessible and stable.\- Test data, environment, and necessary tools (e.g., Postman) are ready**.** |

| Exit Criteria |
| :---- |
| **\-** All test cases (positive and negative) have been executed.\- Any defects are logged in JIRA with required details.\- Test case execution status and defect reports are documented**.** |

---

**🔹 Test Closure Phase**

| Entry Criteria |
| :---- |
| \- All major defects are resolved or accepted.\- Test execution is complete.\- Final test and defect reports are prepared. |

| Exit Criteria |
| :---- |
| **\-** Test Summary Report is reviewed and shared with stakeholders.\- Final approval is received from relevant stakeholders.\- Lessons learned or retrospectives (if applicable) are recorded. |

---

**Tools Used**

| Tool | Purpose |
| :---- | :---- |
| **Postman** |  Used for sending and validating SOAP requests. |
| **JIRA** | Used for defect logging, tracking, and reporting**.** |

 **Risk and Mitigation**

| Potential Risk | Mitigation Strategy |
| :---- | :---- |
| **API documentation not shared on time** | Follow up regularly with the Product Manager and request early access or staging endpoints. |
| **Test resource unavailability** | Ensure backup tester is trained and available. |
| **Unstable API environment** | Inform dev team early; keep buffer time in the test schedule. |
| **No clear acceptance criteria in user story** |   Clarify expectations with product owner before starting     test execution. |

 **Approvals**

Before moving to the next test phase, the following documents will be shared with the client or internal stakeholder for approval:

*  Test Plan

* Test Scenarios

*  Test Cases

* Daily Test Execution and Defect Reports

* Final Test Summary Report

Testing for the next phase will begin only after receiving required approvals.

