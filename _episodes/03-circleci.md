---
title: "Setting running your script on a remote server (CircleCI)"
teaching: 0
exercises: 15
questions:
- "How can I use automated services to perform smoke tests?"
objectives:
- "Set up smoke tests on CircleCI"
keypoints:
- "It's easy to set up smoke tests on CircleCI"
---

### Configuring tests for your repository

For CircleCI to know what tests to run we need to add a `.circleci/config.yml` file with the following content to our repository,

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
            python demean_age.py
```

When this file is added and pushed to GitHub we can go to CircleCI.com:

1. Log in on CircleCI (using your GitHub account)
2. From the Dashboard click "Projects" then "Add projects" and find your repository
3. Select version 2.0 and press "Start building"
3. See how your tests run

Tasks:

1. Can you break your script and see if the test fails?
