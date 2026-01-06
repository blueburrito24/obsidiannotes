### Lecture 6
"Software testing" is how determine the quality of a software system. We observe, record and compare the output of the system to its intended behaviour and output, to find mistakes and errors!
We do testing from an early stage, and regularly too, the smallest of mistakes and changes could make our system impractical!

Test data is what we use to test our systems, providing heavy loads, extreme, borderline, nonsensical and invalid combinations of values to stress the boundaries of our system.

We should designate specialist teams to test the system, alongside business and systems analysts.
In eXtreme Programming, programmers often provide test harnesses, which are frameworks that return predictable results through assertions and verification of the code's expected behaviour and imitate external systems (such as file systems or databases). There is also testing done by the intended users of the system, referred to as user acceptance testing.

There are various types of testing:
- "Black box testing" -> establish whether the end-product does what it intends to in terms of functional requirements, carried out by systems analysts.
- "White box testing" -> establish whether the end-product provides a quality solution, not just a solution, to the problem, carried out by developers and aims at both functional and non-functional requirements.
- "Unit testing" -> checks on the function of individual classes.
- "Interface testing" -> verifies components' functions.
- "Integration testing" -> verifies the integration of all components in the system.
- "Subsystem testing" -> verifies the functionality of each sub-system.
- "System testing" -> checking if the entire system works.
- "Acceptance testing" -> checking if the system works to the requirements of the users AND specification.
- "Usability testing" -> checks if the users are satisfied with the system in its intended purpose.
- "Installation testing" -> checks if the system works on its intended platform.
- "Robustness testing" -> can the system handle anomalies?
	- "Mutation testing" -> introducing small bugs into the code, "mutating" it. This can include removing statements, changing values or decision parameters (If the tests run fine then the system "kills" the mutants - failing when the mutated code is ran).
- "Performance testing" -> stress-test the system in terms of speed and how much memory it uses etc.

There are also different levels of testing; 
- Level 1 would be testing components like classes and processes like use cases. 
- Level 2 refers to testing inputs and outputs in simulated environments.
- Level 3 involves testing in a live use environment relating to response times, performance under stress and recovery from failure, etc.

![[{9E822BC1-7C2C-4C75-8D97-BCD0650CEC36}.png]]
"Regression testing" is when we further test the software to ensure repeated behaviour after changes made to code or the addition of new code. It facilitates faster development, by reducing the risk of those changes and identifying unexpected effects efficiently, alongside running thousands of checks in one click!
Regression testing is pretty time and cost heavy, requiring data capture, analysis and reporting, etc.
![[Pasted image 20260106173102.png]]
If C1 depends on C2, then we need to retest C1. If not, then no, and if unsure, then we do.
There also needs to be documents in place before we go on with testing, such as test plans (which are written before even the code is done, featuring test cases) and test cases (specifying test data, expected outcomes, test descriptions and environment/configuration).
Test results are used for analysis and recorded in spreadsheets, databases or even specialist packages. The results are recorded when tests are both failed and passed. They also should be traceable back to requirements.
Error results need to be recorded in fault report packages, with enough details for the results to be reproduced in a way that allows for further investigation.

There are steps to test planning:
- Define the "testing unit" - what are we testing?
- Define what approaches we'll use - unit/integration/system? Functional/non-functional? Black-box/white-box? Etc.
- Determine the extent of our tests - what features are most critical? What scope are we testing at? What scenarios are high or low risk? What will be tested and what will be ignored?
- Determine how we document the tests - format, templates, location for storage, level of detail and methods for reporting and tracking.
- Determine input sources - where are we getting our test data and scenarios from? I.e., requirement documents, use cases, historical defect data, real production data, generated test data.
- Decide who will perform tests - developers on unit tests, QA team on system/integration tests, End users on acceptance testing, Automated/manual testing.
- Estimate resources needed - how much time do we need to schedule, who's available and what tools and budget do we have available?
- Identify what metrics to collect - code coverage percentages, the amount of defects we find, test pass/fail rates, defect density, test execution duration.

The team behind testing also needs to determine when we can stop testing the software, such as not being able to find another defect, when valid/extreme/out-of-bounds data finds no defects, when all test types given have been completed or when we have no time left for testing (which is really a last-resort measure).

Here's an example of path coverage testing
![[{790CD0B9-CCBC-45D2-9AED-E7639212D5CC}.png]]
Test cases for each path could include:
- showResult (8,8) "Well done! You guessed it!"->"The number I have in mind is 8"
- showResult (9,8) "Sorry. Your guess is too high."->"The number I have in mind is 8"
- showResult (7,8) "Sorry. Your guess is too low."->"The number I have in mind is 8"

Assertions are statements in Java that double-check assumed values, catching mistakes and enforcing rules.
![[{651C9CC9-BDDE-4EBF-83E1-96175F8A8D86}.png]]
They check for events that should never take place.

JUnit is a testing framework for repeating tests.
To use JUnit 5, you have to import either "org.junit.jupiter.api.Assertions" or "org.junit.jupiter.api.Test". The framework marks test methods with the "@Test" keyword. It also uses assert prefix methods such as assertFalse, assertTrue, assertEquals, assertThrows, etc.
![[Pasted image 20260106175632.png]]
"Fixtures" allow us to set up testing environments, involving the following lifecycle:
- @BeforeAll
- @BeforeEach
- @Test
- @AfterEach
- @AfterAll
The "before" prefix-methods are for preparation of test data and "after" prefix-methods are for maintenance.

"Test-driven development" is an approach to writing software where the test cases are the only way we move forward in development. We write test cases before even writing source code. We only produce code that addresses mentioned explicitly in the test cases, and we use testing frameworks like the aforementioned JUnit.
![[{E4F9CF76-6B33-4055-AC24-7EE28AB49B60}.png]]
Test-driven development ensures good statement coverage, reduced redundant code, rapid feedback and tests performed can be utilised later for further testing i.e., regression testing.

### Tutorial 6 - "Software Testing"

