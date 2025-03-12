---
title: "Project: Roman numeral converter"
teaching: 0
exercises: 150
questions:
- "Write a Roman numeral converter"
objectives:
- "Learn how to solve a problem by designing a Python program"
- "Get more hands-on experience"
keypoints:
---

As our first programming exercise, we'll build a Roman number converter. This
will help you to go through the full process of designing a program to solve
a data challenge.


## Introduction to Roman Numerals

Roman numerals originated in ancient Rome and have been used throughout Western
Europe until the late Middle Ages. They are composed of combinations of letters
from the Latin alphabet: I, V, X, L, C, D, and M, which stand for:

- **I** = 1
- **V** = 5
- **X** = 10
- **L** = 50
- **C** = 100
- **D** = 500
- **M** = 1000

### Basic Rules of Roman Numerals:

1. **Addition**: When a smaller numeral appears after a larger or equal one,
   you add the values (e.g., VI is 6 because V + I = 6).
2. **Subtraction**: When a smaller numeral appears before a larger one, you
   subtract the smaller from the larger (e.g., IV is 4 because I is before V).
   The most common subtraction combinations are:
   - I can be placed before V and X to make 4 and 9.
   - X can be placed before L and C to make 40 and 90.
   - C can be placed before D and M to make 400 and 900.
3. **Repetition**: The same symbol can be repeated up to three times in
   succession. For example:
   - III = 3
   - XXX = 30
4. **Combination**: Roman numerals are usually written from largest to smallest
   from left to right, apart from when doing subtractions.

### Examples:

- **III** = 1 + 1 + 1 = 3
- **IV** = 5 - 1 = 4
- **IX** = 10 - 1 = 9
- **LVIII** = 50 + 5 + 3 = 58
- **MCMXCIV** = 1000 + (1000 - 100) + (100 - 10) + (5 - 1) = 1994

## Why It Matters in Programming

Converting between Roman and Arabic numerals involves understanding both
addition and subtraction rules, making it an excellent exercise for developing
algorithms. You'll need to read in strings of characters while adhering to
specific logic patterns —- a fundamental skill in programming.

As you embark on this project, think about the different approaches you can
take. Consider efficiency, readability, and how you might handle edge cases or
errors (such as invalid numeral sequences). This will not only help you write
better code but also enhance your problem-solving skills.

## Bonus challenge

Write an Arabic to Roman numeral converter, e.g. going the other way around.