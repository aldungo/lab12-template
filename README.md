# Programming Fundamentals I — Lab 11

## Method Overloading and More Dice Rolls

Due date: 11:59 p.m. the night before the next lab meeting

---

## Purpose

To expand on our dice rolling simulation, we’ll consider cases where the amount and kinds of dice depend on inputs to the program. Imagine an application with an interface that lets a user specify how many dice to roll and the type of dice (D6, D20, etc.). This program emphasizes the following concept:

• Overloading methods

---

## In‑Class 11

Let’s practice a simple case of method overloading. Prepare a program that includes two versions of an `add` method: one that performs mathematical addition, and one that performs String concatenation.

- The first `add` method takes two doubles as arguments and returns a double equal to the sum of the two parameters.
- The second `add` method takes two Strings as arguments and returns a String that concatenates the first parameter with a space and then the second parameter.

After implementing these two methods, test both in `main` by printing sample outputs. For example:

```
Adding 250 and 500 gives: 750.0
Combining words ‘Hello’ and ‘world’ gives: Hello world
```

---

## Lab 11 Task: MoreDiceRolls

Create a project called `MoreDiceRolls_FirstName_LastName` or `Lab11_FirstName_LastName`. Remember to include comments summarizing the program.

The steps below follow a bottom‑up implementation. Methods implemented earlier will be used later. Make sure the three custom methods you implement all have the same name (i.e., you are overloading the method). You may use either `java.util.Random` or `Math.random()`.

### Step 1 — Roll a single six‑sided die

- Implement a method that rolls one six‑sided die.
- Parameters: none
- Returns: `int` result in the range 1–6 (inclusive)

### Step 2 — Roll a single die with any number of sides

- Implement a method that rolls one die with any number of sides.
- Parameters: one `int` specifying the number of sides
- Returns: `int` result in the range 1–numberOfSides (inclusive)

### Step 3 — Roll two dice and sum them

- Implement a method that rolls two dice, each of which may have any number of sides.
- Parameters: two `int` values specifying the number of sides for each die
- Returns: `int` equal to the sum of the two results

### Step 4 — Use the methods in main

In your `main` method:

1. Print the result of calling each of the three methods. For the second and third calls, use `(20)` and `(6, 6)`, respectively.
2. After the three print statements, declare an `int` variable to count how many times you roll snake eyes (two 1s) when using two six‑sided dice.
3. Create a loop to perform 10,000 rolls using the third method. Increment the snake‑eyes counter whenever the result is 2.
4. After the rolls, print the probability of rolling snake eyes.

---

## Example Output

Your exact results will vary because rolls are random. Example flow:

```
The result of rolling a single six-sided die is 4
The result of rolling a single twenty-sided die is 8
The result of rolling two six-sided dice is 6
The probability of rolling snake eyes is 2.84%.
```

---

## Grading Criteria (100 points)

Make sure you have the following in your program:

• Comments describing this program — 5 points

• Properly implementing the first custom method — 9 points
   - Method header — 3 points
   - Method body — 6 points

• Properly implementing the second custom method — 16 points
   - Method header — 6 points
   - Method body — 10 points

• Properly implementing the third custom method — 30 points
   - Method header — 8 points
   - Method body — 22 points

• Properly implementing the main method — 40 points
   - First three print statements — 9 points
   - Variable declaration and loop — 25 points
   - Last print statement — 6 points

---

## How to Run

From a terminal in VS Code (macOS, zsh):

```bash
# Compile (replace with your actual file name):
javac Lab11_FirstName_LastName.java

# Or if you used the alternate name:
javac MoreDiceRolls_FirstName_LastName.java

# Run (match the class name you compiled):
java Lab11_FirstName_LastName
# or
java MoreDiceRolls_FirstName_LastName
```

---

## Screenshots

Please upload at least one screenshot of your console output. You can use the example outputs to show the correct corresponding behavior or use your own input/rolls.

---

## Submitting Your Work

1. Commit and push your changes using Source Control panel.
2. Verify on GitHub that your latest commit is present and your filenames follow the required convention.
3. Submit your repository URL to Blackboard to complete the assignment.

Good luck, and have fun rolling! 🎲

