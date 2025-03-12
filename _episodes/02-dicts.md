---
title: "Dictionaries"
teaching: 15
exercises: 15
questions:
- "What is a dictionary, and how do I use it?"
objectives:
- "Explain how dictionaries work."
- "Learn about dictionary operations."
keypoints:
- "A dictionary stores values accessible by unique keys."
- "Dictionaries may contain values of different types."
---

## A dictionary allows you to keep data associated to a custom key

* **Different from lists**
  * You access elements in lists by their position, but in a dictionary the keys don't need to be ordered.
* **Different from sets**
  * Sets contain only unique values with no associated keys, while dictionaries map keys to values.
* **A very fast data structure**
  * Lookups, insertions, and deletions in dictionaries are very fast (average-case O(1)).

### Basic Operations

- **Creation:** Use curly braces `{}` or the `dict()` constructor.
- **Access:** Use square brackets (`dict[key]`) or the `get()` method.
- **Modification:** Add or update entries using assignment (`dict[key] = value`).
- **Deletion:** Use the `del` statement or the `pop()` method.
- **Keys:** Use `dict.keys()` to get all keys in the dictionary.
- **Values:** Use `dict.values()` to get all values in the dictionary.

~~~python
# A simple example of a dictionary in biotechnology
data = {'a': "Hello", 'b': 2, 'c': ["apple", "banana", "cherry"]}
print(len(data))         # Output: 3
print(data['a'])         # Output: Hello
~~~
{: .python}

### Example: DNA Codon Table

Consider a simplified DNA codon table where each codon (a triplet of nucleotides) maps to an amino acid.

~~~python
# Example input here
codon_to_amino = {
    "ATG": "Methionine",
    "TTT": "Phenylalanine",
    "TTC": "Phenylalanine",
    "TAA": "Stop",
    "TAG": "Stop",
    "TGA": "Stop"
}
# Access amino acid for codon 'ATG'
print("Codon ATG codes for:", codon_to_amino["ATG"])
~~~
{: .python}

~~~
Codon ATG codes for: Methionine
~~~
{: .output}

> ## Initialising
>
> What does the following program print?
>
> ~~~python
> codon_dict = {"ATG": "Methionine", "TAA": "Stop", "TAG": "Stop"}
> codon_dict["ATG"] = "Start"  # Change: ATG now maps to Start
> codon_dict["TGA"] = "Stop"
> print("Updated codon dictionary:", codon_dict)
> ~~~
> {: .python}
>
> _Hint: The order of keys may vary._
>
> > ## Solution
> > The program prints a dictionary with keys 'ATG', 'TAA', 'TAG', and 'TGA'. The value for 'ATG' is updated to "Start". For example:
> > ~~~python
> > Updated codon dictionary: {'ATG': 'Start', 'TAA': 'Stop', 'TAG': 'Stop', 'TGA': 'Stop'}
> > ~~~
{: .solution}

> ## Fill in the Blanks
>
> Fill in the blanks so that the program below retrieves the correct amino acid for the given codon.
>
> ~~~python
> codon_translation = {"GGT": "Glycine", "GGC": "Glycine", "GGA": "Glycine", "GGG": "Glycine"}
> amino_acid = codon_translation[______]
> print("Amino acid for GGT:", amino_acid)
> ~~~
> {: .python}
>
> _Expected output: Amino acid for GGT: Glycine_
>
> > ## Solution
> > Replace the blank with "GGT":
> > ~~~python
> > amino_acid = codon_translation["GGT"]
> > ~~~
{: .solution}

> ## Adding a New Codon
>
> Extend the dictionary by adding the codon "CCC" for "Proline" to the dictionary below.
>
> ~~~python
> codon_dict = {"ATG": "Methionine", "TAA": "Stop"}
> # Add code here
> print(codon_dict)
> ~~~
> {: .python}
>
> _Expected output: {'ATG': 'Methionine', 'TAA': 'Stop', 'CCC': 'Proline'}_
>
> > ## Solution
> > ~~~python
> > codon_dict["CCC"] = "Proline"
> > ~~~
{: .solution}
