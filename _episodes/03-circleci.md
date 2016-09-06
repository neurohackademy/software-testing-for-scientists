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

For CircleCI to know what tests to run we need to add a `circle.yml` file with the following content to our repository,

```
## Customize dependencies
dependencies:
  pre:
    - sudo apt-get update && sudo apt-get -y install r-base
## Customize test commands
test:
  override:
    - Rscript demean_age.R
```

When this file is added and pushed to GitHub we can go to CircleCI.com:
1. Log in on CircleCI (using your GitHub account)
2. From the Dashboard click "Add projects" and find your repository
3. See how your tests run

Tasks:
1. Can you break your script and see if the test fails?
