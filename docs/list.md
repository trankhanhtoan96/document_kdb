# list
```q
(9;8;7)   or   ("a"; "b"; "c")   or   (-10.0; 3.1415e; `abcd; "r")

q)l1:(-10.0;3.1415e;(`abcd;"r"))    / Assigning variable name to general list

q)count l1                        / Calculating number of items in the list l1
4

q)symbols:(`Life;`Is;`Beautiful)    / Simple Symbols List
`Life`Is`Beautiful

q)chars:("h";"e";"l";"l";"o";" ";"w";"o";"r";"l";"d") 
"hello world"
```
# indexing of list
## Index Notation
```q
q)L:(99;98.7e;`b;`abc;"z")

q)L[0]
99

q)L[1]
98.7e

q)L[4]
"z"
```

## Indexed Assignment
```q
q)L1:9 8 7

q)L1[2]:66      / Indexed assignment into a simple list
                / enforces strict type matching.
                
q)L1
9 8 66
```

# Lists from Variables
```q
q)l1:(9;8;40;200)

q)l2:(1 4 3; `abc`xyz)

q)l:(l1;l2)               / combining the two list l1 and l2

q)l
9 8 40 200
(1 4 3;`abc`xyz)
```

# Joining Lists
The most common operation on two lists is to join them together to form a larger list. More precisely, the join operator (,) appends its right operand to the end of the left operand and returns the result. It accepts an atom in either argument.
```q
q)1,2 3 4
1 2 3 4

q)1 2 3, 4.4 5.6     / If the arguments are not of uniform type,
                     / the result is a general list.
1
2
3
4.4
5.6
```

# Elided Indices
```q
q)L:((1 2 3; 4 5 6 7); (`a`b`c;`d`e`f`g;`0`1`2);("good";"morning"))

q)L
(1 2 3;4 5 6 7)
(`a`b`c;`d`e`f`g;`0`1`2)
("good";"morning")

/Retrieve all items in the second position of each list at the top level.
q)L[;1;]
4 5 6 7
`d`e`f`g
"morning"


/Retrieve the items in the third position for each list at the second level.
q)L[;;2]
3 6
`c`f`2
"or"
```
