# Code analysis
## Metadata_Framework 
#### Version 1.0 

**By: default**

*Date: 2023-08-21*

## Introduction
This document contains results of the code analysis of Metadata_Framework



## Configuration

- Quality Profiles
    - Names: Sonar way [Python]; 
    - Files: AYeVFt0viG7mriH640Ur.json; 


 - Quality Gate
    - Name: Sonar way
    - File: Sonar way.xml

## Synthesis

### Analysis Status

Reliability | Security | Security Review | Maintainability |
:---:|:---:|:---:|:---:
A | A | E | A |

### Quality gate status

| Quality Gate Status | ERROR |
|-|-|

Metric|Value
---|---
Reliability Rating on New Code|OK
Security Rating on New Code|OK
Maintainability Rating on New Code|OK
Coverage on New Code|ERROR (8.4% is less than 80%)
Duplicated Lines (%) on New Code|ERROR (25.1% is greater than 3%)
Security Hotspots Reviewed on New Code|ERROR (0.0% is less than 100%)


### Metrics

Coverage | Duplications | Comment density | Median number of lines of code per file | Adherence to coding standard |
:---:|:---:|:---:|:---:|:---:
11.5 % | 22.7 % | 24.6 % | 773.5 | 99.8 %

### Tests

Total | Success Rate | Skipped | Errors | Failures |
:---:|:---:|:---:|:---:|:---:
0 | 0 % | 0 | 0 | 0

### Detailed technical debt

Reliability|Security|Maintainability|Total
---|---|---|---
-|-|0d 3h 47min|0d 3h 47min


### Metrics Range

\ | Cyclomatic Complexity | Cognitive Complexity | Lines of code per file | Coverage | Comment density (%) | Duplication (%)
:---|:---:|:---:|:---:|:---:|:---:|:---:
Min | 1.0 | 0.0 | 70.0 | 0.0 | 7.1 | 0.0
Max | 203.0 | 679.0 | 8289.0 | 42.9 | 54.9 | 73.0

### Volume

Language|Number
---|---
Python|8289
Total|8289


## Issues

### Issues count by severity and types

Type / Severity|INFO|MINOR|MAJOR|CRITICAL|BLOCKER
---|---|---|---|---|---
BUG|0|0|0|0|0
VULNERABILITY|0|0|0|0|0
CODE_SMELL|0|0|11|1|0


### Issues List

Name|Description|Type|Severity|Number
---|---|---|---|---
Cognitive Complexity of functions should not be too high|Cognitive Complexity is a measure of how hard the control flow of a function is to understand. Functions with high Cognitive Complexity will be <br /> difficult to maintain. <br /> See <br />  <br />    Cognitive Complexity  <br /> |CODE_SMELL|CRITICAL|1
Assertions should not fail or succeed unconditionally|Assertions are meant to detect when code behaves as expected. An assertion which fails or succeeds all the time should be fixed. <br /> This rule raises an issue when an assertion method is given parameters which will make it succeed or fail all the time. It covers three cases: <br />  <br />    an assert statement or a unittest’s assertTrue or assertFalse method is called with a value which will <br />   be always True or always False.  <br />    a unittest’s assertIsNotNone or assertIsNone method is called with a value which will be always None or never None. <br />    <br />    a unittest’s assertIsNot or assertIs method is called with a literal expression creating a new object every time (ex: <br />   [1, 2, 3]).  <br />  <br /> Noncompliant Code Example <br />  <br /> import unittest <br />  <br /> class MyTestCase(unittest.TestCase): <br />     def expect_fail1(self): <br />         assert False <br />  <br />     def expect_fail2(self): <br />         self.assertTrue(False)  # Noncompliant. This assertion always fails. <br />  <br />     def expect_not_none(self): <br />         self.assertIsNotNone(round(1.5))  # Noncompliant. This assertion always succeeds because "round" returns a number, not None. <br />  <br />     def helper_compare(param): <br />         self.assertIs(param, [1, 2, 3])  # Noncompliant. This assertion always fails because [1, 2, 3] creates a new object. <br />  <br /> Compliant Solution <br />  <br /> import unittest <br />  <br /> class MyTestCase(unittest.TestCase): <br />     def expect_fail(self): <br />         self.fail("This is expected") <br />  <br />     def expect_not_none(self): <br />         self.assertNotEqual(round(1.5), 0) <br />  <br />     def helper_compare(param): <br />         self.assertEqual(param, [1, 2, 3]) <br />  <br /> See <br />  <br />    Python documentation - the unittest module  <br />    Python documentation - the assert <br />   statement  <br /> |CODE_SMELL|MAJOR|11


## Security Hotspots

### Security hotspots count by category and priority

Category / Priority|LOW|MEDIUM|HIGH
---|---|---|---
LDAP Injection|0|0|0
Object Injection|0|0|0
Server-Side Request Forgery (SSRF)|0|0|0
XML External Entity (XXE)|0|0|0
Insecure Configuration|0|0|0
XPath Injection|0|0|0
Authentication|0|0|0
Weak Cryptography|0|0|0
Denial of Service (DoS)|0|0|0
Log Injection|10|0|0
Cross-Site Request Forgery (CSRF)|0|0|0
Open Redirect|0|0|0
Permission|0|0|0
SQL Injection|0|0|0
Encryption of Sensitive Data|0|0|0
Traceability|0|0|0
Buffer Overflow|0|0|0
File Manipulation|0|0|0
Code Injection (RCE)|0|0|0
Cross-Site Scripting (XSS)|0|0|0
Command Injection|0|0|0
Path Traversal Injection|0|0|0
HTTP Response Splitting|0|0|0
Others|0|0|0


### Security hotspots

Category|Name|Priority|Severity|Count
---|---|---|---|---
Log Injection|Configuring loggers is security-sensitive|LOW|CRITICAL|10
