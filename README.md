# Lab 12: Array Processing and Bubble Sort
**Due Date:** @ 11:59 p.m. the night *before* next lab

**Submission:** Push to GitHub repository + Submit link to Blackboard

---

## 📋 Overview

A casino is setting up a digital interface for some of its games. One of these is the dice game craps. You will build the logic for the game by collecting and sorting statistics related to rolling the dice.

**Learning Objectives:**
- Practice method abstraction and stepwise refinement
- Store and process data using one-dimensional arrays
- Use arrays as method arguments and return values
- Implement a bubble sort algorithm

---

## 🚀 Getting Started with GitHub Codespaces

### Initial Setup
1. **Accept the assignment** via the GitHub Classroom link provided
2. **Open your repository** in GitHub Codespaces:
   - Click the green "**Code**" button
   - Select "**Codespaces**" tab
   - Click "**Create codespace on main**"
3. **Wait for the environment to load** (this may take 1–2 minutes on first launch)
4. **Explore your workspace** — on the left side you'll see the file explorer with:
   - `README.md` (this file)
   - `InClass12_FirstName_LastName.java` — for your in-class activity
   - `ARRAY_VISUALIZATION.md` — a visual guide to the array structure and sort process

**Note:** You will create the `Lab12_FirstName_LastName.java` (or `Craps_FirstName_LastName.java`) file yourself. Update all filenames and class headers with your actual first and last name.

---

## 📝 Part 1: In-Class Activity (Participation Points)

**File to Work With:** `InClass12_FirstName_LastName.java`

### Background: Bubble Sort

One of the most important operations you can perform on an array is **sorting** its elements. This activity introduces **bubble sort** — an algorithm that repeatedly steps through an array and places values in increasing order. The name comes from the behavior of the sort: smaller numbers gradually *bubble* toward the front of the array, while larger numbers *sink* toward the back.

A key thing to understand first: when you pass an array to a method, Java passes a *reference* to that array — not a copy. This means any changes made inside the method are reflected in the original array even if the method returns `void`.

### Task

Implement a **separate method** that:
- Takes an `int` array as its only argument
- Returns nothing (`void`)
- Sorts the array in place using bubble sort

#### How bubble sort works

Your sort will use **two nested `for` loops**:

**Outer loop — controls the number of passes:**
- Starts at step `0`
- Total number of steps = `array length – 1`
- Each pass guarantees that one more element has settled into its final position at the back

**Inner loop — controls which pairs are compared each pass:**
- Starts at position `0`
- Total positions to examine = `array length – 1 – current step`
- For example: step 0 examines all but the last position; step 1 examines all but the last two; and so on

**Inside the inner loop:**
- Compare the element at the current index with the element at the *next* index
- If the current element is **greater than** the next element, **swap** the two

#### Testing your method

Once your sort method is implemented, test it in `main`:
1. Construct an `int` array containing **10 random numbers**
2. Print the array contents **before** sorting
3. Call your sort method
4. Print the array contents **after** sorting

💡 **Remember:** Take a screenshot of your terminal output and add it to your repository (drag and drop into the file explorer on the left).

📊 **See [ARRAY_VISUALIZATION.md](ARRAY_VISUALIZATION.md) for a visual walkthrough of how the array and sort behave step by step.**

---

## 🔬 Part 2: Main Lab Assignment — Craps

Create a file named `Lab12_FirstName_LastName.java` or `Craps_FirstName_LastName.java` (replace with your actual name). Include comments describing your program's purpose and each method's role — comments are a significant part of the grade.

The steps below follow a **bottom-up implementation**: methods built in earlier steps are called in later ones.

### Methods Required

| Method | Parameters | Return Type |
|---|---|---|
| `main` | standard | `void` |
| `rollDice` | none | `int[]` (one-dimensional) |
| `sortResults` | `int[]` (one-dimensional) | `int[]` (one-dimensional) |

---

### Step 1 — Implement `rollDice`

**What this method does:** simulates 10,000 pairs of dice rolls and counts how often each possible sum occurs.

**Inside `rollDice`:**

1. Construct a one-dimensional `int` array with a length of **11**.
   - This array tracks how many times each sum is rolled.
   - Position `0` holds the count for a sum of **2** (the lowest possible roll).
   - Position `10` holds the count for a sum of **12** (the highest possible roll).

2. Write a `for` loop that iterates **10,000 times**. Each iteration:
   - Generates two random integers from **1–6**
   - Adds them together
   - Increments the array element at the position representing that sum

3. After the loop, **return** the array.

---

### Step 2 — Implement `sortResults`

**What this method does:** sorts the roll-count data in ascending order while keeping a parallel array of the corresponding dice sums in sync — so you always know *which* sum belongs to *which* count.

**Inside `sortResults`:**

1. Construct a one-dimensional `int` array with these initial values:

   ```java
   { 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12 }
   ```

2. Perform a **bubble sort** on the **results array passed into this method** to place its values in increasing order.

3. Whenever you swap two elements in the results array, perform the **identical swap** at the same positions in the array you constructed in step 1.
   > This parallel swap is what keeps the dice-sum labels aligned with their counts — it will be essential for correct output in Step 3.

4. After sorting, **return** the array you constructed in step 1.

---

### Step 3 — Implement `main`

**What this method does:** ties everything together and prints the probability of rolling each possible sum.

**Inside `main`:**

1. Call `rollDice` and assign the returned array to an `int` array variable.
2. Call `sortResults` (passing the array from step 1) and assign the returned array to a second `int` array variable.
3. Write a `for` loop that iterates over every element in either array (both are the same length).
   - The array from `rollDice` holds the **count** for each sum.
   - The array from `sortResults` holds the **corresponding sum label**.
   - Use both together to calculate and print each probability, formatted to **two decimal places**:

     ```
     The probability of rolling a 2 is approximately 2.77%.
     ```

---

## Example Output

The dice rolls are random, so your numbers will differ slightly from this sample each run.

```
The probability of rolling a 2 is approximately 2.85%.
The probability of rolling a 12 is approximately 3.03%.
The probability of rolling a 3 is approximately 5.23%.
The probability of rolling a 11 is approximately 5.47%.
The probability of rolling a 4 is approximately 8.28%.
The probability of rolling a 10 is approximately 8.32%.
The probability of rolling a 5 is approximately 10.89%.
The probability of rolling a 9 is approximately 11.19%.
The probability of rolling a 6 is approximately 13.79%.
The probability of rolling a 8 is approximately 14.43%.
The probability of rolling a 7 is approximately 16.52%.
```

---

## Grading Criteria (150 points)

| Component | Points |
|---|---|
| **Comments describing this program** | 10 |
| **`rollDice` method** | **42** |
| &nbsp;&nbsp;&nbsp;Method header | 6 |
| &nbsp;&nbsp;&nbsp;Array construction | 4 |
| &nbsp;&nbsp;&nbsp;`for` loop to handle dice rolls | 15 |
| &nbsp;&nbsp;&nbsp;Correctly incrementing the right array position | 15 |
| &nbsp;&nbsp;&nbsp;Return statement | 2 |
| **`sortResults` method** | **68** |
| &nbsp;&nbsp;&nbsp;Method header | 5 |
| &nbsp;&nbsp;&nbsp;Array construction | 4 |
| &nbsp;&nbsp;&nbsp;Nested `for` loops for bubble sort | 35 |
| &nbsp;&nbsp;&nbsp;Correctly swapping elements in both arrays | 22 |
| &nbsp;&nbsp;&nbsp;Return statement | 2 |
| **`main` method** | **30** |
| &nbsp;&nbsp;&nbsp;Calling `rollDice` | 5 |
| &nbsp;&nbsp;&nbsp;Calling `sortResults` | 5 |
| &nbsp;&nbsp;&nbsp;`for` loop to print results | 20 |
| **Total** | **150** |
