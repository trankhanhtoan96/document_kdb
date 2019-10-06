Tables are at the heart of kdb+

# Creating Tables
```q
t: ([]id:(1 2);name:(`a`b))

q)tablea
id name
-------
1  a   
2  b 
```

# get column names of table `cols t`

# retrieve value of column `t.name`

# Primary key
```q
a:flip `name`des!(`a`b`c;`da`db`dc)
b:flip (enlist `id)!(enlist 1 2 3)

t:b!a

id |  name      des
---   | ---------------
  1  |  a      da
  2 |  b     db
  3 |  c   dc
  
 
q)t:([id:(1 2 3)]name:(`a`b`c);des:(`da`db`dc))
id| name des
--| --------
1 | a    da 
2 | b    db 
3 | c    dc 
```
# foreign key

```q
q)sector:([id:1 2 3]name:(`a`b`c);des:(`da`db`dc))
q)sector
id| name des
--| --------
1 | a    da 
2 | b    db 
3 | c    dc 

q)tab:([id:4 5 6]name:(`q`w`e);se:`sector$1 2 3)
id| name se
--| -------
4 | q    1 
5 | w    2 
6 | e    3 

q)select from tab where se.name=`b
id| name se
--| -------
5 | w    2 

```

# Manipulating Tables
```q
q)trade:([]name:`a`b;des:("da";"db");time:(.z.T;.z.T-100);size:((123+10*1.2)*0.123;(1213+130*1.22)*4.123))
name des  time         size    
-------------------------------
a    "da" 22:55:21.084 16.605  
b    "db" 22:55:20.984 5655.107
```

# select
`select [columns] [by columns] from table [where clause]`

```q
q)select name by time from trade where size >100
time        | name
------------| ----
22:55:20.984| b  

# insert

```q
`tablename insert (values)
Insert[`tablename; values]
```

```q
q)`trade insert (`c;"dc";10:30:00.000;50.0)
q)insert[`trade;(`d;"dd";10:30:00.000;50.2)]
name des  time         size    
-------------------------------
a    "da" 22:55:21.084 16.605  
b    "db" 22:55:20.984 5655.107
c    "dc" 22:55:21.000 12.2    
c    "dc" 10:30:00.000 50      
d    "dd" 10:30:00.000 50.2   
```
# delete
```q
delete columns from table
delete from table where clause
```

```q
q)delete des from trade
name time         size    
--------------------------
a    22:55:21.084 16.605  
b    22:55:20.984 5655.107
c    22:55:21.000 12.2    
c    10:30:00.000 50      
d    10:30:00.000 50.2  

q)delete from trade where size>100
name des  time         size  
-----------------------------
a    "da" 22:55:21.084 16.605
c    "dc" 22:55:21.000 12.2  
c    "dc" 10:30:00.000 50    
d    "dd" 10:30:00.000 50.2  
```

# update
`update column: newValue from table where ….`

```q
q)update name:`e from trade where size=50
name des  time         size    
-------------------------------
a    "da" 22:55:21.084 16.605  
b    "db" 22:55:20.984 5655.107
c    "dc" 22:55:21.000 12.2    
e    "dc" 10:30:00.000 50      
d    "dd" 10:30:00.000 50.2  
```

