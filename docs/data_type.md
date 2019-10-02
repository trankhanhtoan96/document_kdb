# Data Type

| Name  | Example |
|---| ---|
| boolean |1b |
| byte | 0xff|
| short |23h |
| int | 23i|
| long |23j |
| real | 2.3e|
| float | 2.3f|
| char |“a” |
| varchar | `ab|
| month |2003.03m |
| date |2015.03.17T18:01:40.134 |
| minute |08:31 |
| second | 08:31:53|
| time | 18:03:18.521|
| enum |`u$`b, where u:`a`b |

# Date
```q
q)x:2015.01.22      / This is how we write 22nd Jan 2015

q)`int$x            / Number of days since 2000.01.01
5500i

q)x.year            / Another way of extracting year
2015i

q)x.mm              / Another way of extracting month
1i

q)x.dd              / Another way of extracting day
22i

q)x+1        / Add one day
2015.01.23

q)x-7        / Subtract 7 days
2015.01.1
```

# Time
```q
q)tt1: 03:30:00.000     / tt1 store the time

q)tt1
03:30:00.000

q)`int$tt1              / Number of milliseconds
12600000i

q)tt1.hh
3i

q)tt1.mm
30i

q)tt1.ss
0i
```

# Datetimes
```q
q)dt:2012.12.20T04:54:59:000      / 04:54.59 AM on 20thDec2012
q)`float$dt
4737.205
```