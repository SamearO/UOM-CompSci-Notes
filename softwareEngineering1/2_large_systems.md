# Understanding Large Systems

## How to Understand Large Codebases
* Develop general programming knowledge
* Develop application domain knowledge
* Read unit tests to understand the intended meaning of the codebase

## Unit Testing
* `Unit test`: An automated test that verifies a small piece of code in an isolated manner.
* Uses the `AAA pattern`:
    * `Arrange`: Set up the objects to be tested, usually the largest section.
    * `Act`: Invoke the code to be tested, should usually be one line long
    * `Assert`: Verify the output of the action.
* Tests should only have `AAA` pattern once, otherwise break them up into different tests.
* Tests should avoid branch statements.
