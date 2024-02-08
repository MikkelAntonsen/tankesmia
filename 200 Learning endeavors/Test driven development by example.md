### TDD core tenet
1. Write a failing test before you write any code
2. Remove duplication

This means that you are not allowed to start with a design/object/solution. You first task is fixing code so your test runs at all (adding functions and objects and whatnot).

`Start small or not at all`

### Claim: duplication is a symptom of dependency
???
The thing that has the duplicated thing depends on the thing?

### Small steps
Small steps in TDD aren't a virtue in and of themselves, but being able to take small steps when it is necessary is a skill worth practicing.

Writing a list of tests that need to be written is a nice way to break work up

### TDD workflow
1. Write a test
2. See test fail
3. Add minimum amount of code to make it work (fake code or obvious solution)
4. Verify green test
5. Refactor to remove duplication  (is duplication all we want to do here???)

### TDD triangulation
If you at some point have a concern with a design, then write that concern as a failing test (if worried about state being reused, write a test that reuses object.).

### Value objects helps against aliasing

Value objects are objects who are immutable whos equality is based on it's attributes, not identify (memory address). Aliasing is when two places in the code can modify the same same object from different places.
Aliasing makes code hard to reason about and debug -> value objects do not have aliasing problems because they are immutable.

### TDD vs notemaking
TDD is a conversation between code and test the same way notemaking is a conversation between your slipbox and a new text.
Each test added to a test suite is like a note added to the slipbox.
Both efforts allow you to break complex problems into simple steps. Both proceedures let you use yourself as a sparring partner. Both give you a measure of progress (good for habit making!)

### Test list

You're expected to keep a list over tests that have to be written and concerns that have to be addressed. Work your way through, one at a time. If writing the next test on the list is not easy, make a test that brings you closer but is an easy next step.

### Writing code when tests are failing

If you need to change code (which implies failing a test) while you're already in the red, it's preferable to go back to green and then fix the dependent code.
Rule of thumb: Only one breaking test at the time.

### A test cycle is not done until we have removed duplication

### Autospec
Using autospec in python fails a test if an unspecified method is called.

### Mocking politely

Wrap third party libraries and structures with your own facade. This way your code does not depend on the third party code directly and is easier to test.

# Coming up
Chapter 14, Change

[source](http://ce.sharif.edu/courses/99-00/1/ce475-1/resources/root/Books/KentBeck_TestDrivenDevelopmentByExample-2002.pdf)