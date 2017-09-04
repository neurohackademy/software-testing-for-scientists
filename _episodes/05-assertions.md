---
title: "Adding assertion tests"
teaching:
exercises: 10
questions:
- "Can I add assertion statements in my code?"
objectives:
- "Learn how to increase the quality of your code with assertions"
keypoints:
- "Assertions combined with smoke tests are an easy way to test your software"
---

## Adding assertions

Add the following lines after mean age calculation in your Python script:

```
assert mean_age < 100
assert mean_age > 10 
```
Commit, push and check out CircleCI.

Do your tests still pass?
