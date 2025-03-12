---
title: "Dictionaries"
teaching: 5
exercises: 10
questions:
- "What is a dictionary , and how do I use it?"
objectives:
- "Explain how dictionaries work."
- "Learn about dictionary operations"
keypoints:
- "A dictionary stores values accessible by unique keys."
- "Dictionaries may contain values of different types."
---
## A dictionary allows you to keep data associated to a custom key

* Different from lists
  * You access elements in lists by their position, in a dictionary the keys don't need to be ordered
* Different from sets
  * Sets cont


~~~
Example input here

~~~
{: .python}
~~~
example output
~~~
{: .output}



> ## Initialising
>
> What does the following program print?
>
> ~~~
> letters = set('Hello world!')
> sorted_letters = list(letters)
> sorted_letters.sort()
> print('Letters in greeting:', sorted_letters)
> ~~~
> {: .python}
{: .challenge}

> ## Fill in the Blanks
>
> Fill in the blanks so that the program below produces the output shown.
>
> ~~~
> multiples_of_two = set([2, 4, 6, 8, 10])
> multiples_of_three = set([3, 6, 9])
> result1 = multiples_of_two._______(multiples_of_three)
> print('1', result1)
> result2 = multiples_of_____.______(multiples_of______)
> sorted_result2 = list(result2)
> sorted_result2.sort()
> print('2', sorted_result2)
> ~~~~
> {: .python}
>
> ~~~
> 1 {6}
> 2 [3, 9]
> ~~~
> {: .output}
{: .challenge}

