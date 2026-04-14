# Lab 11: Method Overloading and More Dice Rolls
**Due Date:** @ 11:59 the night *before* next lab

**Submission:** Push to GitHub repository + Submit link to Blackboard

---

## 📋 Overview
This lab expands on the dice-rolling simulation from Lab 9 by introducing **method overloading** — one of Java's most useful features for writing flexible, readable code. Imagine an application that lets a user choose how many dice to roll and what type of die to use (D6, D20, etc.). Rather than inventing a new name for every variation, you'll define multiple methods with the *same* name but different parameter lists, and let Java choose the right one automatically.

**Learning Objectives:**
- Understand what method overloading is and why it is useful
- Implement multiple overloaded methods with the same name but different signatures
- Call overloaded methods from `main` and observe which version is invoked
- Generate random integers in a specified range using `java.util.Random` or `Math.random()`
- Use a loop and counter to estimate a probability experimentally
- Practice bottom-up implementation: build helper methods first, then assemble them in `main`

---

## 🚀 Getting Started with GitHub Codespaces

### Initial Setup
1. **Accept the assignment** via the GitHub Classroom link provided
2. **Open your repository** in GitHub Codespaces:
   - Click the green "**Code**" button
   - Select "**Codespaces**" tab
   - Click "**Create codespace on main**"
3. **Wait for the environment to load** (this may take 1–2 minutes on first launch)
4. **Explore your workspace** — On the left side, you'll see the file explorer with:
   - `README.md` (this file)
   - `InClass11_FirstName_LastName.java` — for your in-class activity
   - Other supporting files

**Note:** You will create the `Lab11_FirstName_LastName.java` (or `MoreDiceRolls_FirstName_LastName.java`) file yourself. Update all filenames and class headers with your actual first and last name.

---

## 📚 Key Concepts for This Lab

### What Is Method Overloading?
**Method overloading** means defining two or more methods in the same class with the **same name** but **different parameter lists**. Java decides which version to call based on the number and types of arguments you pass — this is called *compile-time polymorphism*.

**Rules for overloading:**
- The parameter list must differ in number, type, or order of parameters
- The return type alone is **not** enough to distinguish overloaded methods
- Each overloaded version can have completely different logic inside

**Example pattern** (using a generic `describe` method — not your lab task):
```java
// Version 1 — no parameters
public static String describe() {
    return "No details provided.";
}

// Version 2 — one parameter
public static String describe(String item) {
    return "Item: " + item;
}

// Version 3 — two parameters
public static String describe(String item, int quantity) {
    return quantity + "x " + item;
}
```

When you write `describe()`, Java calls version 1. When you write `describe("apple")`, Java calls version 2. When you write `describe("apple", 3)`, Java calls version 3. Apply this same pattern to your dice methods.

### Generating Random Integers
You may use **either** of the following — both are acceptable:

- **`Math.random()`** — returns a `double` in the range [0.0, 1.0). You will need to scale and shift it to produce an integer in the range you need.
- **`java.util.Random`** — create a `Random` object and use `nextInt()`. Check the Java documentation for how `nextInt(n)` behaves and what adjustment is needed.

Think carefully about the range your method needs to produce, and make sure both endpoints are reachable.

### Estimating Probability with a Loop
You can estimate the theoretical probability of an event (like rolling snake eyes) by running many trials and dividing the number of successes by the total trials:

```
estimated probability = (number of successes) / (total trials) × 100
```

The more trials you run, the closer the estimate gets to the true probability. For two fair six-sided dice the true probability of snake eyes is 1/36 ≈ 2.78%.

---

**Before starting the lab, make sure you understand:**
- How to declare a method with a specific return type and parameter list
- Why two methods with the same name but different parameters are legal in Java
- How to generate a random integer in the range 1 to *n*
- How to use a `for` loop with a counter variable
- How to calculate and print a percentage

**Refer to:** Your lecture notes, textbook chapters on methods and overloading, and in-class examples.

---

## 📝 Part 1: In-Class Activity (Participation Points)
**File to Work With:** `InClass11_FirstName_LastName.java`

### Background
Before jumping into the main lab, let's practice the core idea of overloading with a simple example: an `add` method that behaves differently depending on the types it receives. This mirrors real-world library design — think of how `System.out.println()` accepts strings, integers, doubles, and more all under the same name.

### Task
Prepare a program with **two overloaded versions** of a method named `add`:

1. **Numeric addition:**
   - Parameters: two `double` values
   - Returns: a `double` equal to the sum of the two parameters

2. **String concatenation:**
   - Parameters: two `String` values
   - Returns: a `String` formed by joining the first parameter, a space `" "`, and the second parameter

After implementing both methods, **test them in `main`** by printing the results. Your output should look similar to:

```
Adding 250 and 500 gives: 750.0
Combining words 'Hello' and 'world' gives: Hello world
```

You may use any sample values you like, as long as both overloaded methods are called and their output is printed.

💡 **Remember:** Take a screenshot of your terminal output and add it to your repository (drag and drop into the file explorer on the left).

### Think About It
Notice that you only had to remember one method name — `add` — to perform two completely different operations. This is exactly the readability benefit that overloading provides!

---

## 🔬 Part 2: Main Lab Assignment

### Background
A tabletop game needs a flexible dice-rolling engine. Instead of writing `rollD6()`, `rollD20()`, `rollTwoD6()` etc., a well-designed approach uses one overloaded method name — something like `rollDice` — with different signatures for each use case. You'll build that engine and then use it to run a probability experiment: estimating how often two six-sided dice come up as snake eyes.

### The Big Picture
You'll create a program with **three overloaded method variants** working together, plus `main`:
1. `rollDice()` — rolls one standard six-sided die (no parameters)
2. `rollDice(int sides)` — rolls one die with any number of sides
3. `rollDice(int sides1, int sides2)` — rolls two dice and returns their sum
4. **`main`** — calls all three, then runs the probability experiment

This is a **bottom-up implementation**: build and understand each method before moving to the next.

### Task
Create a file named `Lab11_FirstName_LastName.java` or `MoreDiceRolls_FirstName_LastName.java` (replace with your actual name). Include comprehensive comments describing your program's purpose and each method's job.

---

## 🛠️ Implementation Guide

### Step 1 — Roll a Single Six-Sided Die

Implement a **value-returning method** that rolls one standard die.

**Method design:**
- **Method name:** choose a descriptive name like `rollDice` — whatever you pick, **all three overloaded versions must share the exact same name**
- **Return type:** `int`
- **Parameters:** none
- **Logic:** Return a random integer in the range **1–6 (inclusive)**

**Test your logic:** every call should produce a value from 1 to 6 — never 0, never 7.

---

### Step 2 — Roll a Single Die with Any Number of Sides

Implement a second overloaded version that generalizes to any die type.

**Method design:**
- **Method name:** same name as Step 1 (e.g., `rollDice`)
- **Return type:** `int`
- **Parameters:** one `int` specifying the number of sides (e.g., `20` for a D20)
- **Logic:** Return a random integer in the range **1–numberOfSides (inclusive)**

---

### Step 3 — Roll Two Dice and Sum Them

Implement a third overloaded version that rolls two dice of potentially different sizes.

**Method design:**
- **Method name:** same name as Steps 1 & 2 (e.g., `rollDice`)
- **Return type:** `int`
- **Parameters:** two `int` values — the number of sides for each die
- **Logic:** Roll each die independently and return the **sum** of both results

---

### Step 4 — Implement the Main Method

Now bring everything together.

**Implementation steps:**

1. **Call each of the three overloaded methods once** and print the result:
   - `rollDice()` — no arguments (single D6)
   - `rollDice(20)` — one argument (single D20)
   - `rollDice(6, 6)` — two arguments (two D6s)

   **Required output format (values will vary):**
   ```
   The result of rolling a single six-sided die is 4
   The result of rolling a single twenty-sided die is 8
   The result of rolling two six-sided dice is 6
   ```

2. **Declare an `int` counter** to track how many times snake eyes occur (both dice show 1, so the sum equals 2).

3. **Create a `for` loop** that calls `rollDice(6, 6)` exactly **10,000 times**. Inside the loop, increment the counter whenever the result equals `2`.

4. **After the loop**, calculate the probability as a percentage and print it:
   ```
   The probability of rolling snake eyes is 2.84%.
   ```
   Divide the counter by `100.0` to convert to a percentage (e.g., 284 snake eyes → `284 / 100.0` = `2.84`), then print with `printf()` using `%.2f%%`.

---

## 💻 Example Output

Your exact numbers will differ on every run because rolls are random. Example:

```
The result of rolling a single six-sided die is 4
The result of rolling a single twenty-sided die is 8
The result of rolling two six-sided dice is 6
The probability of rolling snake eyes is 2.84%.
```

**Sanity check:** The experimental probability should hover close to **2.78%** (1/36) — values roughly in the range 2–4% indicate your program is working correctly.

---

## 🏃 Running Your Program

### Using the Terminal
1. Open the terminal in your codespace (**Terminal → New Terminal**)
2. Compile your program:
   ```bash
   javac Lab11_FirstName_LastName.java
   ```
   Or if you used the alternate name:
   ```bash
   javac MoreDiceRolls_FirstName_LastName.java
   ```
3. Run your program:
   ```bash
   java Lab11_FirstName_LastName
   ```
   or
   ```bash
   java MoreDiceRolls_FirstName_LastName
   ```

Replace the placeholder name with your actual first and last name.

**For the in-class activity:** Use `InClass11_FirstName_LastName` instead.

💡 **Remember:** After running your program, take a screenshot of your console output and add it to your file directory on the left as part of your submission.

---

## ✅ Grading Criteria

This lab is worth **100 points** total, distributed as follows:

### Comments (5 points)
- Clear program description at the top of the file
- Comments explaining what each method does
- Comments on any complex logic

### First Custom Method — `rollDice()` (9 points)
- Correct method signature with appropriate return type and no parameters (3 points)
- Correct random logic producing values 1–6 inclusive (6 points)

### Second Custom Method — `rollDice(int sides)` (16 points)
- Correct method signature with appropriate return type and one `int` parameter (6 points)
- Correct random logic producing values 1–`sides` inclusive (10 points)

### Third Custom Method — `rollDice(int sides1, int sides2)` (30 points)
- Correct method signature with appropriate return type and two `int` parameters (8 points)
- Correctly rolls both dice and returns their sum (22 points)

### Main Method (40 points)
- Three print statements calling each overloaded method correctly (9 points)
- Counter variable declaration and 10,000-iteration loop (25 points)
- Final probability print statement with correct formatting (6 points)

---

## 📤 Commit Your Changes

### Step 1: Use VS Code's Source Control Panel
- Click the Source Control icon in the left sidebar (looks like a branch)
- Review your changes in the staging area
- Type a descriptive commit message (e.g., `"Completed Lab 11: Method Overloading and More Dice Rolls"`)
- Click "**Commit**" then "**Sync Changes**" to push your code to GitHub

### Step 2: Verify Submission
After pushing your changes:
1. Visit your assignment repository on GitHub Classroom
2. Confirm that your latest code and commit message appear
3. Verify that your files are named correctly with your actual first and last name
4. Check that your screenshot is included in the repository

### Step 3: Submit to Blackboard Assignment
1. Copy the URL of your assignment repository from GitHub
2. Submit this GitHub repository link to the corresponding Blackboard assignment
3. This confirms you are DONE and ready for grading

---

## 🎉 Closing Thoughts

**Great work making it to Lab 11!** You've now used one of Java's most elegant features: writing a single intuitive method name that adapts to whatever arguments you give it.

**What you've learned:**
- How to design and implement overloaded methods with different signatures
- How Java resolves which overloaded version to call at compile time
- How to generate random integers uniformly in any range
- How to run a simulation loop and estimate a probability experimentally
- How to format percentage output with `printf()`

**Why this matters:** Overloading is everywhere in Java's standard library — `System.out.println()`, `Math.max()`, `String.valueOf()` all rely on it. Understanding overloading makes you a better reader *and* writer of Java code.

**Moving forward:** Next you'll explore arrays, which open the door to storing and processing collections of data — a natural next step for a dice-rolling engine that needs to record many results at once.

**Remember:** Include detailed comments describing what each method does. Future you (and your graders!) will appreciate it!

---

**Important:** Focus on completing the lab assignment. Do NOT edit or tamper with any test files, markdown files, or class files if they appear in your repository.