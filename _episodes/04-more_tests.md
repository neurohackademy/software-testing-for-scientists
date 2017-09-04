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
import sys
import numpy as np

age = np.loadtxt(sys.argv[1], skiprows=1, usecols=3)

mean_age = sum(age)/len(age)

np.savetxt("demeaned_" + sys.argv[1], age-mean_age)

print("done!")
```

## Modify the circle config to include both tests

```
version: 2
jobs:
  build:
    docker:
      - image: circleci/python:3.6.1
    steps:
      - checkout
      - run:
          name: Install Python deps in a virtual environment
          command: |
            python3 -m venv myenv
            . myenv/bin/activate
            pip install numpy
      - run:
          command: |
            . myenv/bin/activate
            python demean_age.py participants.tsv
      - run:
          command: |
            . myenv/bin/activate
            python demean_age.py participants2.tsv
```

Commit all changes and see the tests run on CircleCI.
