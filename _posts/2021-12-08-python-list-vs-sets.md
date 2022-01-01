---
 title: Search Performance in Python's List and Set 
 tags: [python]
 style: fill
 color: light
 excerpt: Understand which data structure out of list and set should you use to store an element for searching
 comments: true
 categories: computer-science
 last_modified_at: 2021-12-08T22:20:02+05:30
---


## Introduction
This article talks about the search performance of list and set.


## Searching

Sometimes we need to search through a collection of things. Let’s look at two options: lists and sets.
Take the following code below:

```python
s = set(['s', 'p', 'a', 'm'])
l = ['s', 'p', 'a', 'm']

def lookup_set(s):
return 's' in s

def lookup_list(l):
return 's' in l
```

Even though both functions look identical, because lookup_set is utilizing the fact that sets in Python are hashtables, the lookup performance between the two is very different.

## Searching in List
To determine whether an item is in a list, Python will have to go through each item until it finds a matching item. 
The runtime complexity is `O(n)`. This means that in the worst case, n operations will take place to search a list of n elements. 
Consider a real example where you are searching through millions of records in a database. This means a million operations will take place to find a specific element.

## Searching in Set
To understand how much faster is searching in sets, lets understand how the sets are implemented in Python. 
The sets are implemented as hashtables in Python. 
In a set, on the other hand, the hash of the item will tell Python where in the set to look for a matching item. As a result, the search can be done quickly, even if the set is large.
Searching in dictionaries works the same way.
