FlexiConc
=========

FlexiConc is a Python library developed to support corpus linguists by supporting the analysis of concordances.

Clicking onto the **'FlexiConc'** tab will take you to the FlexiConc
view. In order to create a flexiconc analsis tree, you will need to select a corpus
to search in (see :ref:`The CLiC corpora`). 

Search the corpora
------------------

This is where you select a corpus to search in. The
selection is very flexible and lets you pick a pre-defined corpus (see :ref:`The CLiC corpora`)
or choose your own subcorpus – with any of the books available in CLiC.

Only in subsets
---------------

Here you can decide whether you want to search through 'all text' – the
whole book(s) – or just one of the subsets: 'short suspensions', 'long
suspensions', 'quotes' and 'non-quotes' (see :ref:`The CLiC corpora`).

Search for terms
----------------

This is the fundamental parameter of the concordance search – it lets
you determine the node word or phrase that forms the basis of the
concordance.


The tokenisation from CLiC 2.0 onwards is based on unicode standard rules
(i.e. Unicode word boundaries implemented with the [ICU]_ library), used
both for queries and importing books.

We consider a boundary mark to be a word-boundary if...
* The [ICU]_ library describes it as at the end of a word, e.g. ``jump`` or number, e.g. ``32.3``.
* It is a single hyphen character surrounded by alpha-numeric characters.
* It is an apostrophe preceded with ``s``, e.g. ``3 days' work``.
* It is one of a whitelist of words preceded with an apostrophe, e.g. ``'tis``.

CLiC 2.0 and onwards supports **wildcards**:

* ``*`` means "zero or more characters", for example:
  
  Placing * at the end of a the sequence ``can`` serves as a placeholder for
  any sequence of characters (or zero) and therefore retrieves all instances of 
  words starting with this sequence, including ``can``, ``cannot`` and ``can't``
  (but also ``candle``, ``candles``, ``candlestick`` etc.)
  
  ``*`` in ``with * hands`` serves as a placeholder for any word token
  between ``with`` and ``hands``, retrieving sequences like ``with her hands``, 
  ``with his hands``, ``with their hands``, ``with both hands``, 
  ``with clean hands`` etc.

* ``?`` means "one"

The search will only retrieve valid tokens according to the rules above.
This means that the search will ignore punctuation in your search query except for 
punctuation sign will not retrieve any results. If your research focuses
on punctuation markers you can evade this issue by using the filter
function in the subset tab: Go to the subset tab, select the relevant
subset, for example non-quotes, and filter the rows to the punctuation
marker of interest.
Two hyphens separate words: for example, *Char--lotte* in Oliver
Twist (OT.c6.p20) “Oliver's gone mad! Char--lotte!” counts as two
tokens.

For the detailed technical documentation and more examples see :mod:`clic.tokenizer`.

'Whole phrase' or 'Any word'
----------------------------

When you have entered several terms, you need to specify whether it is
to be searched as one phrase (equivalent to using double quotes in a
search engine, e.g. *dense fog*) or any of the words individually
(*dense* and *fog*).


Changing the query
----------------------------
It is important to note that FlexiConc is designed to operate on a single concordance. That is, within each session, you should only be working with the results of one query. If you change the above query, you will not be able to access the results that you produced the previous time that the query was run, and you will need to reapply any annotations or algorithms. 
To make sure that your work is saved, it is recommended to *save your analysis tree* before switching to a new query.



Concordancing strategies
----------------------------
  
FlexiConc takes the query result as input and allows you to perform different steps, which are operationalized as algorithms.
Each FlexiConc algorithm performs an operation that belongs to one of three central categories:
  
1.	Selecting
  Focus on specific subsets of concordance lines based on a variety of criteria, including metadata categories and contextual keywords.
  
2.	Ordering
  Arrange concordance lines by sorting or ranking them, using numeric preference scores to prioritize those of interest.
  
3.	Grouping
  Organize lines into groups by applying explicit partitioning criteria or through clustering based on similarity measures.



Analysis tree
----------------------------
  
FlexiConc organizes the concordancing process in an analysis tree. Algorithms can be applied sequentially in a hierarchical structure, meaning that you can ‘branch off’ the analysis on any level. For instance, you can apply a 
sorting algorithm to a subset, which results in only that subset being sorted. Alternatively, you can apply the same sorting algorithm to the concordance lines that you obtained the subset from, which would lead to all lines 
within that view being sorted.

By default, your analysis has one branch, which is started when you run the query, and is represented by the button with the number 1 next to the tree symbol. Clicking on the tree symbol takes you to an overview of the entire 
analysis tree.


Adding algorithms
----------------------------

When you are on a branch, clicking on the add algorithm button shows all available algorithms. You can scroll down or use the search bar to type an algorithm name.
Adding a new algorithm below an existing one will create a new node on the same branch. Clicking on the plus sign + next to the tree symbol creates a new branch on the top level. 

If you click on the branch symbol at the bottom of a node, you create a new branch below that node. 

The branches are numbered by default; and the number automatically counts up in the order of branch creation. 
This is a useful default, as the numbering then serves as a record of the order in which your analysis gradually built up. However, there are cases where the numbering isn’t enough to keep track of your results. 
You can therefore create a named path for any given branch. 

Creating a named path will not overwrite your numbered path. Instead, it creates a copy that is stored separately under the name that you chose, and which you can access through the tree view just like a numbered path. After creating a named path, you will stay on the numbered path you have copied. Named paths are immutable, i.e., you cannot append any algorithms to them.
You can, however, keep working on the numbered branch from which you created the named path; or you can create a new branch from within the named path to copy over the steps into yet another branch.



Annotations
----------------------------

Annotations are automatic analyses of the concordance data that are added to the concordance through some external source of information. Once it has been added, you can use annotations in various sorts of algorithms. You can find the annotations in the add annotation toolbar located right below the query window.
