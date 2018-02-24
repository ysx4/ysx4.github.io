---
layout: post
title: "Test Driven Development (TDD)"
author: "不是很喜欢TDD的Yang"
categories: techynotes
tags: [concept]
techy: true
---

### Golden rules
* Don't write any implementation code until there's a failing test that requires it
* Run tests after making changes to the code

### TDD life-cycle
1. Write the test
2. Run the test (there is no implementation code, test does not pass)
3. Write just enough implementation code to make the test pass
4. Run all tests (tests pass)
5. Refactor
6. Repeat

### TDD Best practices
1. Naming Conventions
    * Separate the implementation from the test code
    * Place test classes in the same package as implementation
    * Name test classes in a similar fashion as classes they test
    * Use descriptive names for test methods
2. Processes
    * Write the test before writing the implementation code
    * Only write new code when test is failing
    * Rerun all tests every time implementation code changes
    * All tests should pass before new test is written
    * Refactor only after all tests are passing
3. Development practices
    * Write the simplest code to pass the test
    * Write assertions first, act later
    * Minimize assertions in each test
    * Do not introduce dependencies between tests
    * Tests should run fast
    * Use mocks
    * Use setup and tear-down methods
    * Do not use base classes
4. Tools
    * Code coverage
    * Continuous integration (CI)
    * Use TDD together with BDD 
