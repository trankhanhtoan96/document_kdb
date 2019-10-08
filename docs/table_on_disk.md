# save table to file
```q
q) trade:([id:1 2 3]name:`a`b`c;des:("da";"db";"dc"))
q) `:/Users/tkt/trade_table set trade
```

# get data from file
```q
q) trade: get `:/Users/tkt/trade_table
id| name des 
--| ---------
1 | a    "da"
2 | b    "db"
3 | c    "dc"
```