# V5: Input Validation and Output Encoding Verification Requirements

## Control Objective

The most common web application security weakness is the failure to properly validate input coming from the client or from the environment before using it. This weakness leads to almost all of the major vulnerabilities in web applications, such as cross site scripting, SQL injection, interpreter injection, locale/Unicode attacks, file system attacks, and buffer overflows.

Ensure that a verified application satisfies the following high level requirements:

* All input is validated to be correct and fit for the intended purpose.
* Data from an external entity or client should never be trusted and should be handled accordingly.


## Security Verification Requirements

| # | Description | L1 | L2 | L3 | Since |
| --- | --- | --- | --- | -- | -- |
| **5.1** | Verify that the runtime environment is not susceptible to buffer overflows, or that security controls prevent buffer overflows. | ✓ | ✓ | ✓ | 1.0 |
| **5.3** | Verify that server side input validation failures result in request rejection and are logged. | ✓ | ✓ | ✓ | 1.0 |
| **5.5** | Verify that input validation routines are enforced on the server side. | ✓ | ✓ | ✓ | 1.0 |
| **5.6** | Verify that a single input validation control is used by the application for each type of data that is accepted. | ✓ | ✓ | ✓ | 1.0 |
| **5.10** | Verify that all SQL queries, HQL, OSQL, NOSQL and stored procedures, calling of stored procedures are protected by the use of prepared statements or query parameterization, and thus not susceptible to SQL injection. | ✓ | ✓ | ✓ | 2.0 |
| **5.11** | Verify that the application is not susceptible to LDAP Injection, or that security controls prevent LDAP Injection. | ✓ | ✓ | ✓ | 2.0 |
| **5.12** | Verify that the application is not susceptible to OS Command Injection, or that security controls prevent OS Command Injection. | ✓ | ✓ | ✓ | 2.0 |
| **5.13** | Verify that the application is not susceptible to Remote File Inclusion (RFI) or Local File Inclusion (LFI) when content is used that is a path to a file. | ✓ | ✓ | ✓ | 3.0 |
| **5.14** | Verify that the application is not susceptible to common XML attacks, such as XPath query tampering, XML External Entity attacks, and XML injection attacks. | ✓ | ✓ | ✓ | 2.0 |
| **5.15** | Verify that all string variables placed into HTML or other web client code is either properly contextually encoded manually, or utilize templates that automatically contextually encode to ensure the application is not susceptible to reflected, stored or DOM Cross-Site Scripting (XSS) attacks. | ✓ | ✓ | ✓ | 3.1 |
| **5.16** | Verify that if the application framework allows automatic mass parameter assignment (also called automatic variable binding) from the inbound request to a model, verify that security sensitive fields such as “accountBalance”, “role” or “password” are protected from malicious automatic binding. |  | ✓ | ✓ | 3.1 |
| **5.17** | Verify that the application has defenses against HTTP parameter pollution attacks, particularly if the application framework makes no distinction about the source of request parameters (GET, POST, cookies, headers, environment, etc.) |  | ✓ | ✓ | 2.0 |
| **5.18** | Verify that client side validation is used as a second line of defense, in addition to server side validation. |  | ✓ | ✓ | 3.0 |
| **5.19** | Verify that all input data is validated, not only HTML form fields but all sources of input such as REST calls, query parameters, HTTP headers, cookies, batch files, RSS feeds, etc; using positive validation (whitelisting), then lesser forms of validation such as grey listing (eliminating known bad strings), or rejecting bad inputs (blacklisting). |  | ✓ | ✓ | 3.0 |
| **5.20** | Verify that structured data is strongly typed and validated against a defined schema including allowed characters, length and pattern (e.g. credit card numbers or telephone, or validating that two related fields are reasonable, such as validating suburbs and zip or post codes match).  |  | ✓ | ✓ | 3.0 |
| **5.21** | Verify that unstructured data is sanitized to enforce generic safety measures such as allowed characters and length, and characters potentially harmful in given context should be escaped (e.g. natural names with Unicode or apostrophes, such as ねこ or O'Hara) |  | ✓ | ✓ | 3.0 |
| **5.22** | Verify that untrusted HTML from WYSIWYG editors or similar are properly sanitized with an HTML sanitizer and handle it appropriately according to the input validation task and encoding task.  | ✓ | ✓ | ✓ | 3.0 |
| **5.23** | Verify that where an application uses auto-escaping templating AND auto-escaping is disabled, output should be manually contextually encoded or sanitized to prevent XSS. |  | ✓ | ✓ | 3.1 |
| **5.24** | Verify that where data is transferred from one DOM context to another, the transfer uses safe JavaScript methods, such as using innerText or .val. |  | ✓ | ✓ | 3.1 |
| **5.25** | Verify when parsing JSON in browsers, that JSON.parse is used to parse JSON on the client. Do not use eval() to parse JSON on the client. |  | ✓ | ✓ | 3.0 |
| **5.26** | Verify that authenticated data is cleared from client storage, such as the browser DOM, after the session is terminated. |  | ✓ | ✓ | 3.0 |
| **5.27** | Test the application for Server Side Request Forgery vulnerabilities. | ✓ | ✓ | ✓ | 3.1 |


## References

For more information, see also:

* [OWASP Testing Guide 4.0: Input Validation Testing](https://www.owasp.org/index.php/Testing_for_Input_Validation)
* [OWASP Cheat Sheet: Input Validation](https://www.owasp.org/index.php/Input_Validation_Cheat_Sheet)
* [OWASP Testing Guide 4.0: Testing for HTTP Parameter Pollution](https://www.owasp.org/index.php/Testing_for_HTTP_Parameter_pollution_%28OTG-INPVAL-004%29)
* [OWASP LDAP Injection Cheat Sheet ](https://www.owasp.org/index.php/LDAP_Injection_Prevention_Cheat_Sheet)
* [OWASP Testing Guide 4.0: Client Side Testing ](https://www.owasp.org/index.php/Client_Side_Testing)
* [OWASP Cross Site Scripting Prevention Cheat Sheet ](https://www.owasp.org/index.php/XSS_%28Cross_Site_Scripting%29_Prevention_Cheat_Sheet)
* [OWASP Java Encoding Project](https://www.owasp.org/index.php/OWASP_Java_Encoder_Project)

For more information on auto-escaping, please see:

* [Reducing XSS by way of Automatic Context-Aware Escaping in Template Systems](http://googleonlinesecurity.blogspot.com/2009/03/reducing-xss-by-way-of-automatic.html)
* [AngularJS Strict Contextual Escaping](https://docs.angularjs.org/api/ng/service/$sce)
* [Improperly Controlled Modification of Dynamically-Determined Object Attributes](https://cwe.mitre.org/data/definitions/915.html)
