---
title: "Programming Style"
teaching: 15
exercises: 15
questions:
- "How can I make my programs more readable?"
- "How do most programmers format their code?"
objectives:
- "Provide sound justifications for basic rules of coding style."
- "Refactor one-page programs to make them more readable and justify the changes."
- "Use Python community coding standards (PEP-8)."
keypoints:
- "Follow standard Python style in your code."
- "Use docstrings to provide online help."
---

## Follow standard Python style in your code.

* [PEP8](https://www.python.org/dev/peps/pep-0008) is a style guide for Python that discusses topics such as:
  - How you should name variables.
  - How you should use indentation.
  - How to structure your `import` statements.
  <br>
Adhering to PEP8 makes it easier for other Python friends (and yourself) to read and understand your code. Tools like the [PEP8 library](https://pypi.python.org/pypi/pep8) or the "flake8" extension in VS Code can help check your code for compliance.  
<br><br>
~~~python
# Run the Zen of Python
import this
~~~
{: .python}

<br>

## Use docstrings for functions

* If the first statement in a function is a string literal (not assigned to a variable), it becomes the function's docstring.
* Docstrings provide online help accessible via the `help()` function.

~~~python
def average(values):
    """
       Return the average of values, or None if no values are supplied.
    """
    if len(values) == 0:
        return None
    return sum(values) / len(values)

help(average)
~~~
{: .language-python}

~~~
Help on function average in module __main__:

average(values)
    Return the average of values, or None if no values are supplied.
~~~
{: .output}

> ## Multiline Strings
>
> Often use *multiline strings* for documentation. These start and end with three quote characters (single or double).
>
> ~~~python
> """This string spans
> multiple lines.
>
> Blank lines are allowed."""
> ~~~
> {: .language-python}
{: .callout}

## Examples of Bad/Not Pythonic Code

### Example 1: Poor Naming and Formatting
~~~python
# Bad: confusing function name, lack of whitespace, and multiple statements on one line
def f(x,y):return x+y; print(f(1,2))
~~~
{: .language-python}

*Issues:*
- The function name `f` is not descriptive.
- No whitespace around operators or after commas.
- Multiple statements on one line reduce readability.

*Improved Version:*
~~~python
def add_numbers(a, b):
    """
    Return the sum of a and b.
    """
    return a + b

result = add_numbers(1, 2)
print(result)
~~~
{: .language-python}

### Example 2: Importance of Good Comments

*Without Comments:*
~~~python
def process_data(data):
    result = []
    for d in data:
        if d % 2 == 0:
            result.append(d ** 2)
        else:
            result.append(d ** 3)
    return result

print(process_data([1, 2, 3, 4]))
~~~
{: .language-python}

*Issues:*
- Missing comments and docstring.

*With Clear Comments:*
~~~python
def process_data(data):
    """
    Process each number in the list:
    - Square even numbers.
    - Cube odd numbers.
    """
    result = []
    for d in data:
        # Check if the number is even
        if d % 2 == 0:
            result.append(d ** 2)
        else:
            # Number is odd: cube it
            result.append(d ** 3)
    return result

print(process_data([1, 2, 3, 4]))
~~~
{: .language-python}

## Exercises

> ## What Will Be Shown?
>
> Highlight the lines in the code below that will be available as online help.
> Are there lines that should be made available but won't be?
> Will any lines produce a syntax error or a runtime error?
>
> ~~~python
> "Find maximum edit distance between multiple sequences."
> # This finds the maximum distance between all sequences.
>
> def overall_max(sequences):
>     '''Determine overall maximum edit distance.'''
>
>     highest = 0
>     for left in sequences:
>         for right in sequences:
>             '''Avoid checking sequence against itself.'''
>             if left != right:
>                 this = edit_distance(left, right)
>                 highest = max(highest, this)
>
>     # Report.
>     return highest
> ~~~
> {: .language-python}
{: .challenge}

> ## Document This
>
> Turn the comment on the following function into a docstring
> and check that `help` displays it properly.
>
> ~~~python
> def middle(a, b, c):
>     # Return the middle value of three.
>     # Assumes the values can actually be compared.
>     values = [a, b, c]
>     values.sort()
>     return values[1]
> ~~~
> {: .language-python}
{: .challenge}

> ## Messy code
>
> 1. Read the code and try to predict what it does.
> 2. Run it: Does it produce the expected counts?
> 3. Refactor the code to improve its readability and structure.
> 4. Compare your solution with a partner and discuss your changes.
>
> ~~~python
> # Messy code - fix me!
> dna = "ATCGATCGAATTCG"
> k = 3
> kmers = {}
> i = 0
> while i < len(dna):
>     if i + k <= len(dna):
>         s = ""
>         j = 0
>         while j < k:
>             s = s + dna[i+j]
>             j = j + 1
>         if s in kmers:
>             kmers[s] = kmers[s] + 1
>         else:
>             kmers[s] = 1
>     i = i + 1
> print(kmers)
> ~~~
> {: .language-python}
>
> > ## Solution
> >
> > ~~~python
> > def count_kmers(dna, k):
> >     """
> >     Count all k-mers (substrings of length k) in the given DNA string.
> >
> >     Parameters:
> >         dna (str): The DNA sequence.
> >         k (int): The length of each k-mer.
> >
> >     Returns:
> >         dict: A dictionary mapping each k-mer to its count.
> >     """
> >     counts = {}
> >     for i in range(len(dna) - k + 1):
> >         kmer = dna[i:i+k]
> >         counts[kmer] = counts.get(kmer, 0) + 1
> >     return counts
> >
> > # Example usage
> > dna_sequence = "ATCGATCGAATTCG"
> > kmer_length = 3
> > kmer_counts = count_kmers(dna_sequence, kmer_length)
> > print(kmer_counts)
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}
