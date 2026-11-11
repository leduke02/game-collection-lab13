
# Blinker trace

Patch: rows 3 to 7, columns 8 to 12. `#` = alive, `.` = dead.

## Generation 0: live cells (4,10) (5,10) (6,10)

```
      c8 c9 c10 c11 c12
row3   .  .  .   .   .
row4   .  .  #   .   .
row5   .  .  #   .   .
row6   .  .  #   .   .
row7   .  .  .   .   .
```

Neighbor counts, generation 0:

```
      c8 c9 c10 c11 c12
row3   0  1  1   1   0
row4   0  2  1   2   0
row5   0  3  2   3   0
row6   0  2  1   2   0
row7   0  1  1   1   0
```

Apply the rules:
- (4,10) alive, 1 neighbor: dies
- (5,10) alive, 2 neighbors: survives
- (6,10) alive, 1 neighbor: dies
- (5,9) dead, 3 neighbors: born
- (5,11) dead, 3 neighbors: born
- every other cell: stays dead

## Generation 1: live cells (5,9) (5,10) (5,11)

```
      c8 c9 c10 c11 c12
row3   .  .  .   .   .
row4   .  .  .   .   .
row5   .  #  #   #   .
row6   .  .  .   .   .
row7   .  .  .   .   .
```

Neighbor counts, generation 1:

```
      c8 c9 c10 c11 c12
row3   0  0  0   0   0
row4   1  2  3   2   1
row5   1  1  2   1   1
row6   1  2  3   2   1
row7   0  0  0   0   0
```

Apply the rules:
- (5,9) alive, 1 neighbor: dies
- (5,10) alive, 2 neighbors: survives
- (5,11) alive, 1 neighbor: dies
- (4,10) dead, 3 neighbors: born
- (6,10) dead, 3 neighbors: born
- every other cell: stays dead

## Generation 2: live cells (4,10) (5,10) (6,10)

```
      c8 c9 c10 c11 c12
row3   .  .  .   .   .
row4   .  .  #   .   .
row5   .  .  #   .   .
row6   .  .  #   .   .
row7   .  .  .   .   .
```

Generation 2 equals generation 0, so the blinker flips between a vertical and
a horizontal line and returns after two generations.
