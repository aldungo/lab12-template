# Array Visualization Guide for Lab 12

## Understanding the Rolls Array

The `rollDice` method uses an array to count how many times each dice sum appears. Here's how the array is structured:

### Array Structure

```
Index:      0    1    2    3    4    5    6    7    8    9    10
            |    |    |    |    |    |    |    |    |    |    |
Dice Sum:   2    3    4    5    6    7    8    9   10   11   12
            |    |    |    |    |    |    |    |    |    |    |
Count:    [ 0 ][ 0 ][ 0 ][ 0 ][ 0 ][ 0 ][ 0 ][ 0 ][ 0 ][ 0 ][ 0 ]
```

### Key Points

- **Array Length**: 11 elements (indices 0-10)
- **Dice Sums**: Range from 2 (1+1) to 12 (6+6)
- **Index Formula**: `rolls[diceSum - 2]`

### Examples

When you roll the dice:
- Roll a **2** → Increment `rolls[0]`
- Roll a **7** → Increment `rolls[5]`
- Roll a **12** → Increment `rolls[10]`

### Visual After 10 Rolls Example

```
Index:      0    1    2    3    4    5    6    7    8    9    10
            |    |    |    |    |    |    |    |    |    |    |
Dice Sum:   2    3    4    5    6    7    8    9   10   11   12
            |    |    |    |    |    |    |    |    |    |    |
Count:    [ 1 ][ 0 ][ 1 ][ 2 ][ 1 ][ 3 ][ 1 ][ 0 ][ 1 ][ 0 ][ 0 ]
```

This shows:
- Rolled a 2 once
- Rolled a 5 twice
- Rolled a 7 three times (most common)
- Never rolled a 3, 9, 11, or 12

## Understanding the Bubble Sort

### Before Sorting (by dice value)

```
Index:        0    1    2    3    4    5    6    7    8    9    10
Dice Value:   2    3    4    5    6    7    8    9   10   11   12
Count:      [285][523][828][1089][1379][1652][1443][1119][832][547][303]
```

### After Sorting (by count, ascending)

```
Index:        0    1    2    3    4    5    6    7    8    9    10
Dice Value:   2   12    3   11    4   10    5    9    6    8    7
Count:      [285][303][523][547][828][832][1089][1119][1379][1443][1652]
```

Notice how both arrays are swapped together - the dice values stay matched with their counts!

## Probability Calculation

After 10,000 rolls:

```
Probability = (count / 10000) * 100

Example: If 7 was rolled 1652 times
Probability = (1652 / 10000) * 100 = 16.52%
```

### Output Format

```
The probability of rolling a 2 is approximately 2.85%.
The probability of rolling a 12 is approximately 3.03%.
...
The probability of rolling a 7 is approximately 16.52%.
```

Results are sorted from **least likely** to **most likely** to roll!
