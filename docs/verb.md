# each
```q
q)1, (2 3 5)       / Join
1 2 3 5

q)1, '( 2 3 4)     / Join each
1 2
1 3
1 4

q)reverse ( 1 2 3; "abc")           /Reverse
a b c
1 2 3

q)'[reverse] ( 1 4 3; "abc")
3 2 1
c b a

q)x: 9 18 27 36

q)y:10 20 30 40

q)x,y            / join
9 18 27 36 10 20 30 40

q)x,'y           / each
9   10
18  20
27  30
36  40

x: 1 2 3 4
q)1 _x           / drop the first element
2 3 4

q)-2_x           / drop the last two element
1 2
```

