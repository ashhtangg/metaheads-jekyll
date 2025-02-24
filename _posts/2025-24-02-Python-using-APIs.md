---
category: doc
tags: [python]
---

### Summary

Here's a basic guide on how to get data from an API and use it for your code - 

```
import requests 

response = requests.get(url = "example")
data = response.json()

data["example value"]["example value"]

```

Here's an example of how you could make a quiz game from a quiz related API 

```
from data import question_data
score = 0 

for q in question_data["results"]:
    question = q["question"]
    correct_answer = q["correct_answer"].lower()

    user_answer = input(f"{question} ").lower()
    if user_answer == correct_answer:
        score += 1

print(f"Your final score is: {score}/{len(question_data['results'])}")
		
```

When you're reviewing JSON data from an API, usually you have to do `data["results"]` for the loop since the list of dictionaries live within the key
