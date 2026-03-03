---
title: "Sets"
teaching: 10
exercises: 10
questions:
- "What is a set, and how do I use it?"
objectives:
- "Explain how sets work."
- "Learn about set operations."
keypoints:
- "A set stores an unordered collection of unique values."
- "Sets automatically remove duplicate entries."
- "Sets support operations like union, intersection, and difference."
---

## A set keeps an unordered collection of unique items.

* **Different from lists**
  * Lists have a defined order and can contain duplicate values, whereas sets are unordered and contain only unique items.
* **Efficient operations**
  * Sets offer fast membership testing and support operations like union, intersection, and difference.
* **Mutability**
  * You can add or remove items from a set, but duplicate entries are ignored.

~~~python
beatles = set(['John', 'Paul', 'George', 'Ringo'])
print('Beatles:', beatles)
print('Length:', len(beatles))
beatles.add('Ringo')  # Adding 'Ringo' again does nothing
print('Beatles:', beatles)
print('Length:', len(beatles))
~~~
{: .python}

~~~
Beatles: {'John', 'Paul', 'George', 'Ringo'}
Length: 4
Beatles: {'John', 'Paul', 'George', 'Ringo'}
Length: 4
~~~
{: .output}

## Check Membership with `in`

Use the `in` keyword to test if an element exists in a set.

~~~python
print('Ringo is one of the Beatles:', 'Ringo' in beatles)
print('Keith is one of the Beatles:', 'Keith' in beatles)
~~~
{: .python}

~~~
Ringo is one of the Beatles: True
Keith is one of the Beatles: False
~~~
{: .output}

## Adding and Removing Items

### Add Items with `add()`

~~~python
beatles.add('Pete')
print('After adding Pete:', beatles)
~~~
{: .python}

~~~
After adding Pete: {'John', 'Paul', 'George', 'Ringo', 'Pete'}
~~~
{: .output}

### Remove Items with `remove()`

~~~python
beatles.remove('Pete')
print('After removing Pete:', beatles)
~~~
{: .python}

~~~
After removing Pete: {'John', 'Paul', 'George', 'Ringo'}
~~~
{: .output}

## Set Operations

### Union of Sets

Combine two sets using `union()` (or the `|` operator):

~~~python
odd = set([1, 3, 5, 7, 9])
even = set([2, 4, 6, 8, 10])
all_numbers = odd.union(even)
print('Odd numbers:', odd)
print('Even numbers:', even)
print('All numbers:', all_numbers)
~~~
{: .python}

~~~
Odd numbers: {1, 3, 5, 7, 9}
Even numbers: {2, 4, 6, 8, 10}
All numbers: {1, 2, 3, 4, 5, 6, 7, 8, 9, 10}
~~~
{: .output}

> ## Note
> Since sets are unordered, the printed order of elements may vary.
{: .callout}

### Intersection of Sets

Retrieve common elements with `intersection()`:

~~~python
primes = set([2, 3, 5, 7])
odd_primes = primes.intersection(odd)
print('Primes that are odd:', odd_primes)
~~~
{: .python}

~~~
Primes that are odd: {3, 5, 7}
~~~
{: .output}

### Difference of Sets

Get elements in one set but not in another with `difference()`:

~~~python
even_non_primes = even.difference(primes)
print('Even numbers that are not prime:', even_non_primes)
~~~
{: .python}

~~~
Even numbers that are not prime: {4, 6, 8, 10}
~~~
{: .output}

> ## Order Matters in `difference()`
> The result of `difference()` depends on the order of the sets.
{: .callout}

### Converting a Set to a Sorted List

To display a set in order, convert it to a list and sort it:

~~~python
sorted_primes = sorted(primes)
print('Sorted primes:', sorted_primes)
~~~
{: .python}

~~~
Sorted primes: [2, 3, 5, 7]
~~~
{: .output}

> ## Initialising Challenge
>
> What does the following program print?
>
> ~~~python
> letters = set('Hello world!')
> sorted_letters = list(letters)
> sorted_letters.sort()
> print('Letters in greeting:', sorted_letters)
> ~~~
> {: .python}
{: .challenge}

> ## Fill in the Blanks Challenge
>
> Fill in the blanks "__" so that the program below produces the output shown.
>
> ~~~python
> multiples_of_two = set([2, 4, 6, 8, 10])
> multiples_of_three = set([3, 6, 9])
> result1 = multiples_of_two.__(multiples_of_three)
> print('1', result1)
> result2 = multiples_of_three.__(multiples_of_two)
> sorted_result2 = sorted(result2)
> print('2', sorted_result2)
> ~~~
> {: .python}
>
> ~~~
> 1 {6}
> 2 [3, 9]
> ~~~
> {: .output}
{: .challenge}

> ## Comparing Bacterial Isolates
>
> You have two sets representing bacteria isolated from two different sources:
>
> ~~~python
> clinical_isolates = {"Staphylococcus aureus", "Escherichia coli", "Pseudomonas aeruginosa", "Klebsiella pneumoniae"}
> environmental_isolates = {"Bacillus subtilis", "Escherichia coli", "Staphylococcus epidermidis", "Pseudomonas aeruginosa"}
> ~~~
> {: .language-python}
>
> Write code to:
>
> 1. Print the bacteria common to both sets (intersection).
> 2. Print the bacteria unique to the clinical sample (difference).
> 3. Print all unique bacteria from both sets (union) as a sorted list.
>
> > ## Solution
> >
> > ~~~python
> > # 1. Intersection: bacteria present in both samples
> > common_bacteria = clinical_isolates.intersection(environmental_isolates)
> > print("Common bacteria:", common_bacteria)
> > 
> > # 2. Difference: bacteria unique to the clinical sample
> > unique_clinical = clinical_isolates.difference(environmental_isolates)
> > print("Unique to clinical sample:", unique_clinical)
> > 
> > # 3. Union: all unique bacteria from both sets, sorted alphabetically
> > all_bacteria = sorted(clinical_isolates.union(environmental_isolates))
> > print("All unique bacteria:", all_bacteria)
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}
