---
title: "Adding more tests"
teaching:
exercises: 10
questions:
- "Can I add more tests?"
objectives:
- "Add more tests"
keypoints:
- "Adding more smoke tests is easy"
---

## Creating another dataset

Copy the `participants.tsv` file to `participants2.tsv` and modify ages of a few participants.

## Modifying the script to take command line arguments

Make your script read the data path from the command line:
```
args <- commandArgs(trailingOnly = TRUE)

demographics <- read.csv(file=args[1], head=TRUE, sep="\t")

age <- demographics[4]
demean_age <- age - sum(age)/length(age)

write.table(demean_age, file="age_demeaned.tsv", row.names=FALSE, col.names=FALSE, sep="\t")

print("done!")
```

## Modify the circle config to include both tests

```
## Customize dependencies
dependencies:
  pre:
    - sudo apt-get update && sudo apt-get -y install r-base
## Customize test commands
test:
  override:
    - Rscript age_demean.R participants.tsv
    - Rscript age_demean.R participants2.tsv
```

Commit all changes and see the tests run on CircleCI.
