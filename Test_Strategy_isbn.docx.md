                        **Test Strategy for ISBN Checker**

**Introduction**

This document describes the test strategy for the ISBN Checker web service. This service is used to validate ISBN numbers and return whether the input is valid or invalid. The objective of this strategy is to define the testing approach, scope, tools, risks, and execution plan for the ISBN validation service.

**Objective**

The objective is to test the ISBN Checker service to ensure it works correctly, returns accurate validation results, handles invalid inputs properly, and supports the expected request formats without issues.

**Features to Be Tested (In Scope)**

* ISBN-10 validation.

* SOAP 1.1 request and response.

* SOAP 1.2 request and response.

* JSON request and response.

* Valid ISBN inputs.

* Invalid ISBN inputs.

* Empty input, null input, and special character input.

* ISBN values with incorrect length.

* ISBN values ending with X.

**Features Not to Be Tested (Out of Scope)**

* ISBN-13 validation, if the current project scope is only ISBN-10.

* Any unrelated book search or catalog features.

* UI screens or mobile application features, if not part of the service.

* Internal backend systems not exposed through the ISBN validation service.

* Third-party integrations outside the scope of the checker.

**Types of Testing We Will Do**

* **Functional Testing:** To verify that the ISBN Checker returns correct results for valid and invalid inputs.

* **API Testing:** To validate SOAP 1.1, SOAP 1.2, and JSON requests and responses.

* **Positive Testing:** To confirm that valid ISBN values are accepted correctly.

* **Negative Testing:** To verify that invalid inputs are rejected correctly.

* **Boundary Testing:** To test short, long, and edge-case ISBN values.

* **Input Validation Testing:** To check empty, null, alphabetic, and special character inputs.

* **Response Validation Testing:** To verify that the service returns the expected boolean response.

* **Regression Testing:** To make sure existing validation behavior still works after any changes.

**Tools Used**

* **Postman** – for API testing.

* **SOAP UI** – for SOAP request validation.

* **JIRA** – for bug tracking.

* **Excel sheet** – to write and manage test cases.

* **Browser / web service endpoint** – to verify service responses manually if needed.

**Team and Timeline**

**Team:**

* 1 manual tester.

* 1 automation tester, if automation is planned.

**Timeline:**

* **Day 1:** Understand requirements and prepare test scenarios.

* **Day 2:** Write test cases.

* **Day 3:** Execute functional and API test cases.

* **Day 4:** Log defects and retest fixed issues.

* **Day 5:** Final review and sign-off.

**Entry and Exit Criteria**

**Entry Criteria:**

* Service endpoint is available.

* Requirements are clear.

* Test data is ready.

* Test environment is stable.

**Exit Criteria:**

* All planned test cases are executed.

* No critical or high-severity defects remain open.

* Test results are documented.

* Final sign-off is completed.

**Deliverables**

* Test Strategy document.

* Test Cases document.

* Test Execution report.

* Bug report.

* Final Test Summary report.

**Risks**

* Service may be unavailable during testing.

* Requirements may change.

* Incorrect or incomplete test data may be used.

* Time may be limited for deeper testing such as regression or automation.

