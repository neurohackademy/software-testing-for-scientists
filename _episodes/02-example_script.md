---
title: "Creating an example script."
teaching:
exercises: 10
questions:
- "How do I know my code runs?"
objectives:
- "Set up the example script"
keypoints:
- "Running things manually does not scale."
---

## Setting up an example

1. Create a new repository on github
2. Clone it to your computer
3. Inside create a demean_age.py file

```
import numpy as np

age = np.loadtxt("participants.tsv", skiprows=1, usecols=3)

mean_age = sum(age)/len(age)

np.savetxt("demeaned_age.txt", age-mean_age)

print("done!")
```

4. Download [this data file](https://gist.githubusercontent.com/chrisfilo/95d01249ecdf80e850bc8e08ac8f61c6/raw/1773e78e54b082c7f8ed0a06ddc586d426330d5e/participants.tsv) and put it next to the .py file

Tasks:

- "Can you check if the script runs without errors?"
