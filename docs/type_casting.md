# Casting Integers to Floats
```q
q)a:9 18 27

q)$[`float;a]     / Specify desired data type by its symbol name, 1st way
9 18 27f
```

# Casting Strings to Symbols
```q
q)b: ("Hello";"World";"HelloWorld")    / define a list of strings
q)c: `$b                               / this is how to cast strings to symbols

q)c                                    / Now c is a list of symbols
`Hello`World`HelloWorld
```

# Casting Strings to Non-Symbols
```q
q)b:900               / b contain single atomic integer

q)c:string b          / convert this integer atom to string “900”

q)c
```
