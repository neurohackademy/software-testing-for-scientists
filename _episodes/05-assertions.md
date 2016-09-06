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

Add the following lines after mean age calculation in your R script:

```
args <- commandArgs(trailingOnly = TRUE)

demographics <- read.csv(file=args[1], head=TRUE, sep="\t")

age <- demographics[4]
mean_age <- sum(age)/length(age)
stopifnot(mean_age < 100)
stopifnot(mean_age > 10)
demean_age <- age - mean_age


write.table(demean_age, file="age_demeaned.tsv", row.names=FALSE, col.names=FALSE, sep="\t")

print("done!")
```
Commit, push and check out CircleCI.

Do your tests still pass?
