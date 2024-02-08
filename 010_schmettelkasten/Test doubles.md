202207110852

Status: 

Tags: [[TDD]]

# Test doubles

### Dummy

Dummies are passed around to satisfy a type system and  are never used

### Fakes

Fakes make shortcuts that make them unsuitable for production, such as using in-memory databases.

### Verified fakes
Same as fakes, but the fakes are tested themselves to verify that they have the same behaviour as the real thing.

### Stub

Fakes return a list of predefined, canned responses to calls.

### Spies

Spies are stubs that also record what methods are called on them.

### Mocks

Mocks specify a sequence of calls that are expected to be executed in a certain order in the test.



---
# References