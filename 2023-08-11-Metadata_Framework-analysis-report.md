# Code analysis
## Metadata_Framework 
#### Version 1.0 

**By: default**

*Date: 2023-08-11*

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

| Quality Gate Status | OK |
|-|-|



### Metrics

Coverage | Duplications | Comment density | Median number of lines of code per file | Adherence to coding standard |
:---:|:---:|:---:|:---:|:---:
12.4 % | 18.5 % | 16.0 % | 1310.0 | 99.6 %

### Tests

Total | Success Rate | Skipped | Errors | Failures |
:---:|:---:|:---:|:---:|:---:
0 | 0 % | 0 | 0 | 0

### Detailed technical debt

Reliability|Security|Maintainability|Total
---|---|---|---
-|-|1d 2h 10min|1d 2h 10min


### Metrics Range

\ | Cyclomatic Complexity | Cognitive Complexity | Lines of code per file | Coverage | Comment density (%) | Duplication (%)
:---|:---:|:---:|:---:|:---:|:---:|:---:
Min | 1.0 | 0.0 | 87.0 | 0.0 | 0.3 | 0.0
Max | 196.0 | 629.0 | 8745.0 | 47.3 | 50.0 | 40.6

### Volume

Language|Number
---|---
Python|8745
Total|8745


## Issues

### Issues count by severity and types

Type / Severity|INFO|MINOR|MAJOR|CRITICAL|BLOCKER
---|---|---|---|---|---
BUG|0|0|0|0|0
VULNERABILITY|0|0|0|0|0
CODE_SMELL|0|7|58|13|0


### Issues List

Name|Description|Type|Severity|Number
---|---|---|---|---
String literals should not be duplicated|Duplicated string literals make the process of refactoring error-prone, since you must be sure to update all occurrences. <br /> On the other hand, constants can be referenced from many places, but only need to be updated in a single place. <br /> Noncompliant Code Example <br /> With the default threshold of 3: <br />  <br /> def run(): <br />     prepare("this is a duplicate")  # Noncompliant - "this is a duplicate" is duplicated 3 times <br />     execute("this is a duplicate") <br />     release("this is a duplicate") <br />  <br /> Compliant Solution <br />  <br /> ACTION_1 = "action1" <br />  <br /> def run(): <br />     prepare(ACTION_1) <br />     execute(ACTION_1) <br />     release(ACTION_1) <br />  <br /> Exceptions <br /> No issue will be raised on: <br />  <br />    duplicated string in decorators  <br />    strings with less than 5 characters  <br />    strings with only letters, numbers and underscores  <br />  <br />  <br /> @app.route("/api/users/", methods=['GET', 'POST', 'PUT']) <br /> def users(): <br />     pass <br />  <br /> @app.route("/api/projects/", methods=['GET', 'POST', 'PUT'])  # Compliant <br /> def projects(): <br />     pass <br /> |CODE_SMELL|CRITICAL|4
Cognitive Complexity of functions should not be too high|Cognitive Complexity is a measure of how hard the control flow of a function is to understand. Functions with high Cognitive Complexity will be <br /> difficult to maintain. <br /> See <br />  <br />    Cognitive Complexity  <br /> |CODE_SMELL|CRITICAL|3
Bare "raise" statements should only be used in "except" blocks|A bare raise statement, i.e. a raise with no exception provided, will re-raise the last active exception in the current <br /> scope. If the "raise" statement is not in an except or finally block, no exception is active and a RuntimeError <br /> is raised instead. <br /> If the bare raise statement is in a function called in an except statement, the exception caught by the <br /> except will be raised. This works but is hard to understand and maintain. Nothing indicates in the parent except that the <br /> exception will be reraised, and nothing prevents a developer from calling the function in another context. <br /> Note also that using a bare raise in a finally block only works when an exception is active, i.e. when an exception from <br /> the try block is not caught or when an exception is raised by an except block. It will fail in any other case and should not <br /> be relied upon. This code smell is handled by rule S5704. <br /> This rule raises an exception when a bare raise statement is not in an except or finally block. <br /> Noncompliant Code Example <br />  <br /> raise  # Noncompliant <br />  <br /> def foo(): <br />     raise  # Noncompliant <br />     try: <br />         raise  # Noncompliant <br />     except ValueError as e: <br />         handle_error() <br />     except: <br />         raise <br />     else: <br />         raise  # Noncompliant <br />     finally: <br />         raise <br />  <br /> def handle_error(): <br />     raise  # Noncompliant. This works but is hard to understand. <br />  <br /> Compliant Solution <br />  <br /> raise ValueError() <br />  <br /> def foo(): <br />     raise ValueError() <br />     try: <br />         raise ValueError() <br />     except: <br />         raise <br />     else: <br />         raise ValueError() <br />     finally: <br />         raise <br />  <br /> See <br />  <br />    Python Documentation - The raise statement  <br /> |CODE_SMELL|CRITICAL|6
Sections of code should not be commented out|Programmers should not comment out code as it bloats programs and reduces readability. <br /> Unused code should be deleted and can be retrieved from source control history if required.|CODE_SMELL|MAJOR|47
Assertions should not fail or succeed unconditionally|Assertions are meant to detect when code behaves as expected. An assertion which fails or succeeds all the time should be fixed. <br /> This rule raises an issue when an assertion method is given parameters which will make it succeed or fail all the time. It covers three cases: <br />  <br />    an assert statement or a unittest’s assertTrue or assertFalse method is called with a value which will <br />   be always True or always False.  <br />    a unittest’s assertIsNotNone or assertIsNone method is called with a value which will be always None or never None. <br />    <br />    a unittest’s assertIsNot or assertIs method is called with a literal expression creating a new object every time (ex: <br />   [1, 2, 3]).  <br />  <br /> Noncompliant Code Example <br />  <br /> import unittest <br />  <br /> class MyTestCase(unittest.TestCase): <br />     def expect_fail1(self): <br />         assert False <br />  <br />     def expect_fail2(self): <br />         self.assertTrue(False)  # Noncompliant. This assertion always fails. <br />  <br />     def expect_not_none(self): <br />         self.assertIsNotNone(round(1.5))  # Noncompliant. This assertion always succeeds because "round" returns a number, not None. <br />  <br />     def helper_compare(param): <br />         self.assertIs(param, [1, 2, 3])  # Noncompliant. This assertion always fails because [1, 2, 3] creates a new object. <br />  <br /> Compliant Solution <br />  <br /> import unittest <br />  <br /> class MyTestCase(unittest.TestCase): <br />     def expect_fail(self): <br />         self.fail("This is expected") <br />  <br />     def expect_not_none(self): <br />         self.assertNotEqual(round(1.5), 0) <br />  <br />     def helper_compare(param): <br />         self.assertEqual(param, [1, 2, 3]) <br />  <br /> See <br />  <br />    Python documentation - the unittest module  <br />    Python documentation - the assert <br />   statement  <br /> |CODE_SMELL|MAJOR|11
Local variable and function parameter names should comply with a naming convention|Shared naming conventions allow teams to collaborate effectively. This rule raises an issue when a local variable or function parameter name does <br /> not match the provided regular expression. <br /> Exceptions <br /> Loop counters are ignored by this rule. <br />  <br /> for i in range(limit):  # Compliant <br />     print(i) <br /> |CODE_SMELL|MINOR|7


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
Log Injection|6|0|0
Cross-Site Request Forgery (CSRF)|0|0|0
Open Redirect|0|0|0
SQL Injection|0|0|0
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
Log Injection|Configuring loggers is security-sensitive|LOW|CRITICAL|6
