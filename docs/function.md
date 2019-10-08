# create custom function

```q
q) functionname:{[arg1;arg2] res:arg1+arg2; res /res is the responsive of the function}
q) functionname[3;4]
7
```

# abs
```q
q)abs -9.9
9.9
```

# all
```q
q) all 4 5 0 -4 / Logical AND (numeric min), returns the minimum value
0b
```

# & (and)
```q
q)1b & 1b
1b
q)1b&0b
0b
```

# | (or)
```q
q)1b|1b
1b
q)1b|0b
1b
q)0b|0b
0b

```

# not
```q
q)not 1b
0b
q)not 0b
1b
```

# asc
```q
q)asc 1 2 4 3
`s#1 2 3 4
```

# avg
```q
q)avg 1 2 4 3
2.5
```

# by
```q
q)select des by name from trade
name| des 
----| ----
a   | "da"
b   | "db"

```

# cols
```q
q)cols trade
`name`des
```

# count
```q
q)a:til 9
q)a
0 1 2 3 4 5 6 7 8
q)count a
9
```

# cut
```q
q)(1 3 5) cut "abcdefghijkl"
"bc"
"de"
"fghijkl"
q)5 cut "abcdefghijkl"
"abcde"
"fghij"
"kl"
```

# delete
```q
delete size from trade
```

# distinct
```q
q)distinct 1 2 3 2 3 4 5 2 1 3 
1 2 3 4 5
```

# first
```q
q)first 1 3 34 5 3
1
```

# flip
```q
q)trade

       time                   sym      price   size
------------------------------------------------------
  2009.06.18T06:04:42.919    apple   72.05742   36
  2009.11.14T12:42:34.653    ibm     16.11385   12
  2009.12.27T17:02:11.518    apple   68.15909   97

q)flip trade

time | 2009.06.18T06:04:42.919 2009.11.14T12:42:34.653
2009.12.27T17:02:11.518

sym   |  apple         ibm         apple
price | 72.05742     16.11385    68.15909
size  | 36 12 97
```
# iasc
```q
q)iasc 5 4 0 3 4 9
2 3 1 4 0 5
```

# idesc
```q
q)idesc 0 1 3 4
3 2 1 0
```

# in
```q
q)2 in 1 2 4
1b
```
# lower
```q
q)lower ("JoHn";`HERRY`SYM)
"john"
`herry`sym
```
# ? (random)
```q
q)9?5
4 0 2 1 2 1 2 3 2
```

# read0
```q
read0 `:c:/q/README.txt  / gives the contents of *.txt file
```

# read1
```q
read1 `:c:/q/t1 /Read in a q data file
```

# reverse
```q
q)reverse 2 30 29 1 3 4
4 3 1 29 30 2
q)reverse "HelloWorld"
"dlroWolleH"
```

# set
```q
q)`x set 9
`x

q)x
9

q)`:c:/q/test12 set trade
`:c:/q/test12

q)get `:c:/q/test12

       time                   sym      price     size
---------------------------------------------------------
  2009.06.18T06:04:42.919    apple    72.05742    36
  2009.11.14T12:42:34.653     ibm     16.11385    12
  2009.12.27T17:02:11.518    apple    68.15909    97
  2015.04.06T10:03:36.738    samsung  48.35       99
  2015.04.06T10:03:47.540    samsung  48.35       99
  2015.04.06T10:04:44.844    samsung  48.35       99
```

# ssr
```q
q)/ssr - String search and replace, syntax - ssr["string";searchstring;replaced-with]
q)ssr["HelloWorld";"o";"O"]
"HellOWOrld"
```

# string
```q
q)a:string (1 2 3)
q)a
,"1"
,"2"
,"3"
q)a[1]
,"2"
q)a[1][0]
"2"
```

# system
```q
/send system command
q)system "ls"
"docs"
"mkdocs.yml"
"site"
```

# tables
```q
/list all tables
q)tables `
,`trade
```

# til
```q
q)til 9
0 1 2 3 4 5 6 7 8
```

# trim
```q
q)trim " John "
"John"
```

# xasc
```q
q)/xasc - Order table ascending, allows a table (right-hand argument) to be sorted such that (left-hand argument) is in ascending order

q)`price xasc trade

          time                 sym      price      size
----------------------------------------------------------
   2009.11.14T12:42:34.653     ibm     16.11385     12
   2015.04.06T10:03:36.738   samsung   48.35        99
   2015.04.06T10:03:47.540   samsung   48.35        99
   2015.04.06T10:04:44.844   samsung   48.35        99
   2009.12.27T17:02:11.518    apple    68.15909     97
   2009.06.18T06:04:42.919    apple    72.05742     36
```

# xcol
```q
q)/xcol - Renames columns of a table

q)`timeNew`symNew xcol trade

        timeNew                 symNew    price      size
-------------------------------------------------------------
   2009.06.18T06:04:42.919      apple    72.05742     36
   2009.11.14T12:42:34.653       ibm     16.11385     12
   2009.12.27T17:02:11.518      apple    68.15909     97
   2015.04.06T10:03:36.738     samsung   48.35        99
   2015.04.06T10:03:47.540     samsung   48.35        99
   2015.04.06T10:04:44.844     samsung   48.35        99
```

# xcols
```q
q)/xcols - Reorders the columns of a table,

q)`size`price xcols trade

  size    price           time                   sym
-----------------------------------------------------------
   36   72.05742   2009.06.18T06:04:42.919      apple 
   12   16.11385   2009.11.14T12:42:34.653       ibm
   97   68.15909   2009.12.27T17:02:11.518      apple
   99   48.35      2015.04.06T10:03:36.738     samsung 
   99   48.35      2015.04.06T10:03:47.540     samsung
   99   48.35      2015.04.06T10:04:44.844     samsung
```

# xdesc
```q
q)/xdesc - Order table descending, allows tables to be sorted such that the left-hand argument is in descending order.

q)`price xdesc trade

        time                   sym       price      size
-----------------------------------------------------------
   2009.06.18T06:04:42.919    apple    72.05742      36
   2009.12.27T17:02:11.518    apple    68.15909      97
   2015.04.06T10:03:36.738   samsung   48.35         99
   2015.04.06T10:03:47.540   samsung   48.35         99
   2015.04.06T10:04:44.844   samsung   48.35         99
   2009.11.14T12:42:34.653     ibm     16.11385      12
```

# xkey
```q
q)/xkey - Set key on table

q)`sym xkey trade

    sym   |      time                    price     size
--------- | -----------------------------------------------
   apple  | 2009.06.18T06:04:42.919    72.05742     36
    ibm   | 2009.11.14T12:42:34.653    16.11385     12
   apple  | 2009.12.27T17:02:11.518    68.15909     97
  samsung | 2015.04.06T10:03:36.738    48.35        99
  samsung | 2015.04.06T10:03:47.540    48.35        99
  samsung | 2015.04.06T10:04:44.844    48.35        99
```

# like
```q
q)/like is a dyadic, performs pattern matching, return 1b on success else 0b

q)"John" like "J??n"
1b

q)"John My Name" like "J*"
1b
```

# ltrim
```q
q)/ ltrim - monadic ltrim takes string argument, removes leading blanks

q)ltrim " Rick "
"Rick "
```

# rtrim
```q
q)/rtrim - takes string argument, returns the result of removing trailing blanks

q)rtrim " Rick "
" Rick"
```

# ss
```q
q)/ss - string search, perform pattern matching, same as "like" but return the indices of the matches of the pattern in source.

q)"Life is beautiful" ss "i"
1 5 13
```

# sum
```q
q)sum 2 3 4 5 6
20

q)sum (1 2; 4 5)
5 7
```

# deltas
```q
/difference from its previous item.

q)deltas 2 3 5 7 9
2 1 2 2 2

q)deltas `x`y`z!9 18 27

x | 9
y | 9
z | 9
```

# max
```q
q)max 3 6 5 1 19 3
19
```

# excerpt
```q
q)1 2 3 4 3 1 except 1
2 3 4 3
```