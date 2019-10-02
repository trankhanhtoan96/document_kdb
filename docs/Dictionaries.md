Dictionaries are an extension of lists which provide the foundation for creating tables. In mathematical terms, dictionary creates the

“domain → Range”

or in general (short) creates

“key → value”

relationship between elements.

A dictionary is an ordered collection of key-value pairs that is roughly equivalent to a hash table. A dictionary is a mapping defined by an explicit I/O association between a domain list and a range list via positional correspondence. The creation of a dictionary uses the "xkey" primitive (!)

```q
ListOfDomain ! ListOfRange
```

```q
q)d:`Name`Age`Sex`Weight!(`John;36;"M";60.3)   / Create a dictionary d

q)d

Name   | `John
Age    | 36
Sex    | "M"
Weight | 60.3

q)count d             / To get the number of rows in a dictionary.
4

q)key d               / The function key returns the domain
`Name`Age`Sex`Weight

q)value d             / The function value returns the range.

`John
36

"M"
60.3

q)cols d             / The function cols also returns the domain.
`Name`Age`Sex`Weight
```

# Lookup
```q
q)d[`Name]       / Accessing the value of domain `Name
`John

q)d[`Name`Sex]   / extended item-wise to a simple list of keys
`John
"M"
```

# Operations on Dictionaries
## modified
```q
d:`Name`Age`Sex`Weight! (`John;36;"M";60.3)
                                  / A dictionary d
                                  
q)d[`Age]:35                      / Assigning new value to key Age

q)d 
                              / New value assigned to key Age in d
Name   | `John
Age    | 35
Sex    | "M"
Weight | 60.3
```
## extended
```q
q)d[`Height]:"182 Ft"

q)d

Name   | `John
Age    | 35
Sex    | "M"
Weight | 60.3
Height | "182 Ft"
```
## Reverse Lookup
```q
q)d2:`x`y`z!99 88 77

q)d2?77
`z
```
## Removing
```q
q)d2:`x`y`z!99 88 77

q)d2    _`z

x| 99
y| 88
```

# Column Dictionaries
```q
q)scores: `name`id!(`John`Jenny`Jonathan;9 18 27)
                              / Dictionary scores
                              
q)scores[`name]               / The values for the name column are
`John`Jenny`Jonathan

q)scores.name                 / Retrieving the values for a column in a
                              / column dictionary using dot notation.
`John`Jenny`Jonathan

q)scores[`name][1]            / Values in row 1 of the name column
`Jenny

q)scores[`id][2]              / Values in row 2 of the id column is
27
```

# Flipping a Dictionary
The net effect of flipping a column dictionary is simply reversing the order of the indices. This is logically equivalent to transposing the rows and columns.
```q
q)scores

name  | John Jenny Jonathan
id    | 9   18   27

q)flip scores

  name     id
---------------
  John     9
  Jenny    18
Jonathan  27
```