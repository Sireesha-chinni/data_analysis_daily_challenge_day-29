# Day 29: Student Marks Analyzer (Python Dictionary)

A small Python coding challenge that uses nested dictionaries to analyze student marks across subjects.

## Problem Statement

Given the marks of several students in different subjects, use a dictionary to:

1. Store the student data
2. Calculate each student's **total** and **average** marks
3. Find the **top scorer**
4. Find the **failed students** (marks below 40 in any subject)

## Input Data

```python
students = {
    "Asha": {"Math": 78, "Science": 85, "English": 67},
    "Ravi": {"Math": 35, "Science": 40, "English": 50},
    "John": {"Math": 90, "Science": 92, "English": 88}
}
```

## Approach

| Task | Method |
|------|--------|
| Store data | Nested dictionary: student name → {subject: marks} |
| Total marks | `sum(marks.values())` for each student |
| Average marks | `total / len(marks)`, rounded to 2 decimals |
| Top scorer | `max(totals, key=totals.get)` |
| Failed students | Loop through each subject score and flag the student if any score is below 40 (`break` once found) |

## Code

```python
# Total and average
totals = {}
averages = {}
for name, marks in students.items():
    totals[name] = sum(marks.values())
    averages[name] = round(totals[name] / len(marks), 2)
    print(f"{name}: Total = {totals[name]}, Average = {averages[name]}")

# Top scorer
top_scorer = max(totals, key=totals.get)
print("Top scorer:", top_scorer, "with", totals[top_scorer], "marks")

# Failed students (marks < 40 in any subject)
failed = []
for name, marks in students.items():
    for subject, score in marks.items():
        if score < 40:
            failed.append(name)
            break
print("Failed students:", failed)
```

## Output

```
Asha: Total = 230, Average = 76.67
Ravi: Total = 125, Average = 41.67
John: Total = 270, Average = 90.0
Top scorer: John with 270 marks
Failed students: ['Ravi']
```

## Results Summary

| Student | Total | Average | Status |
|---------|-------|---------|--------|
| Asha | 230 | 76.67 | Pass |
| Ravi | 125 | 41.67 | Fail (Math: 35) |
| John | 270 | 90.00 | Pass (Top scorer) |

## Concepts Practiced

- Nested dictionaries
- Looping with `.items()` and `.values()`
- Built-in functions: `sum()`, `len()`, `max()`, `round()`
- Using `key=` with `max()`
- Conditional logic and `break`
- f-string formatting

## How to Run

1. Open `Day-29-Data-analytics-challenge-python.ipynb` in Jupyter Notebook or JupyterLab.
2. Run the cells from top to bottom.

Requires Python 3.x (tested on 3.9). No external libraries needed.

## Files

- `Day-29-Data-analytics-challenge-python.ipynb`: solution notebook
- `Day29_Coding_Challenge.pdf`: original problem statement
- `README.md`: this file

## Possible Improvements

- Handle ties when more than one student has the top total
- Show which subject(s) a student failed in, not just their name
- Add per-subject averages and the highest scorer in each subject
- Wrap the logic in reusable functions
