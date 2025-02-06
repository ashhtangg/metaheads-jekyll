---
category: doc
tags: [python, pandas]
---

### Introduction

Since I'm going through Pandas as part of my journey in learning Python, one challenge I had was to create something that would return the phonetic version of whatever the input was

I've completed it with the code below and thought to walk through it here

```

import pandas

data = pandas.read_csv("nato_phonetic_alphabet.csv")

new_dict = {row.letter: row.code for (index, row) in data.iterrows()}

name = input("Please enter your name: ").upper()
splitname = [letter for letter in name]

phonetic = [new_dict[letter] for letter in splitname if letter in new_dict]
print(phonetic)
```

### Explanation

So we import pandas in first 

After we get pandas to read the CSV that contains the phonetic data

From there, we name a new dictionary (with dictionary comprehension and the .interrows() method)

We then ask for a input from the user - make a new list (using list comprehension) with just the letters

We then make a final list called phonetic - if the letter is in new_dict, for each letter in splitname, find the corresponding phonetic per letter

--

### Hardest Part

The most complicated section of this code would the the the dataframe to dictionary conversion

`new_dict = {row.letter: row.code for (index, row) in data.iterrows()}`

So when you use pandas to read a CSV, it automatically converts it to a DataFrame 

So when you're making the new dictionary, you want to use the iterrows() method which allows you to get the values from a specific row.

So you'll have to refer back to the CSV, see that the headers for the CSV are both 'letter' and 'code', then reference it for the dictionary

`row.letter: row.code`

With looping through a dataframe the `(index, row)` refers to the 'index' the corresponding 0,1,2,3,4,5 etc with each row, and the row refers to the actual row

You can do either do `row["header"]` or `row.header` to refer to all the roles under a certain column, the dictionary syntax is prefered as it works with spaces
