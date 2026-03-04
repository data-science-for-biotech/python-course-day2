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

## Hint

To build this, one way to read the numbers is to keep track of the current character
you are reading, and then looking ahead to the next character to see if that's bigger
and you need to subtract.

## Bonus challenge

Write an Arabic to Roman numeral converter, e.g. going the other way around.
reversed



SOLUTION script: 
> > ## Solution
> >
> > ~~~python
> > """Convert Roman numerals to their numerical value"""
> > 
> > import sys
> > 
> > NUMERAL_VALUES = {
> >     'I': 1,
> >     'V': 5,
> >     'X': 10,
> >     'L': 50,
> >     'C': 100,
> >     'D': 500,
> >     'M': 1000
> > }
> > 
> > def main():
> >     if len(sys.argv) < 2:
> >         print("Usage:", sys.argv[0], "<roman numeral>")
> >         sys.exit(1)
> > 
> >     numeral = sys.argv[1]
> >     result = convert(numeral)
> > 
> >     print(f"{numeral}:\t{result}")
> > 
> > 
> > def convert(numeral: str) -> int:
> >     """Convert a Roman numeral to its numerical value"""
> >     value = 0
> >     i = 0
> >     for char in numeral:
> >         current_value = NUMERAL_VALUES[char]
> > 
> >         if i + 1 < len(numeral):
> >             next_value = NUMERAL_VALUES[numeral[i + 1]]
> >             if current_value < next_value:
> >                 value -= current_value
> >                 i += 1
> >                 continue
> > 
> >         value += current_value
> >         i += 1
> > 
> >     return value
> > 
> > 
> > def convert_reverse(numeral: str) -> int:
> >     """Convert a Roman numeral to its numerical value (reverse iteration)"""
> >     value = 0
> >     prev_value = 0
> > 
> >     for char in reversed(numeral):
> >         current_value = NUMERAL_VALUES[char]
> > 
> >         if current_value < prev_value:
> >             value -= current_value
> >         else:
> >             value += current_value
> > 
> >         prev_value = current_value
> > 
> >     return value
> > 
> > 
> > def to_roman(num: int) -> str:
> >     """Convert a number to its Roman numeral representation"""
> >     if num <= 0 or num >= 4000:
> >         raise ValueError("Number must be between 1 and 3999")
> > 
> >     result = ""
> >     for numeral, value in sorted(NUMERAL_VALUES.items(), key=lambda x: x[1], reverse=True):
> >         while num >= value:
> >             result += numeral
> >             num -= value
> > 
> >         # Handle subtractive notation
> >         if numeral == 'M' and num >= 900:
> >             result += 'CM'
> >             num -= 900
> >         elif numeral == 'D' and num >= 400:
> >             result += 'CD'
> >             num -= 400
> >         elif numeral == 'C' and num >= 90:
> >             result += 'XC'
> >             num -= 90
> >         elif numeral == 'L' and num >= 40:
> >             result += 'XL'
> >             num -= 40
> >         elif numeral == 'X' and num >= 9:
> >             result += 'IX'
> >             num -= 9
> >         elif numeral == 'V' and num >= 4:
> >             result += 'IV'
> >             num -= 4
> > 
> >     return result
> > 
> > 
> > def test_convert():
> >     assert convert("III") == 3
> >     assert convert("IV") == 4
> >     assert convert("IX") == 9
> >     assert convert("LVIII") == 58
> >     assert convert("MCMXCIV") == 1994
> > 
> > def test_convert_reverse():
> >     assert convert_reverse("III") == 3
> >     assert convert_reverse("IV") == 4
> >     assert convert_reverse("IX") == 9
> >     assert convert_reverse("LVIII") == 58
> >     assert convert_reverse("MCMXCIV") == 1994
> > 
> > def test_to_roman():
> >     assert to_roman(3) == "III"
> >     assert to_roman(4) == "IV"
> >     assert to_roman(9) == "IX"
> >     assert to_roman(58) == "LVIII"
> >     assert to_roman(1994) == "MCMXCIV"
> > 
> > if __name__ == "__main__":
> >     main()
> > ~~~
> > {: .language-python}
> {: .solution}
