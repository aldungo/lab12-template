# Programming Fundamentals I — Lab 12

## Array Processing and Bubble Sort

Due date: 11:59 p.m. the night before the next lab meeting

---

## Purpose

A casino is setting up a digital interface for some of the various games. One of these is the dice game craps. You will be building the logic for the game by collecting statistics related to rolling the dice.

This lab focuses on the following concepts:

• Method abstraction and stepwise refinement
• Array processing
• Using arrays with methods

---

## In‑Class 12

This lab will emphasize array processing and using multiple methods with arrays. One of the most important kinds of processing with arrays is sorting the elements. For this lab, you will be performing a bubble sort to place the results in increasing order. The name of this sort comes from the fact that smaller numbers will bubble to the top (front of the array) while larger numbers sink to the bottom (back of the array).

Implement a separate method that takes an int array as its argument and returns nothing. Since the array reference is shared, the original array will be changed regardless of whether anything is returned from this method.

A bubble sort will require two nested for loops. The outer for loop represents each step of the sort. These steps start from 0, and the total number of steps is equal to the array length – 1. The inner for loop represents the part of the array to sort for that step. The positions to examine start from 0, and the total number of positions to examine is equal to the array length – 1 – the current step. For example, step 0 considers all but the last position, step 1 considers all but the last two positions, and so on.

In this inner for loop, you will compare adjacent elements in the array. Check if the element at the current index of the array is greater than the element in the next index. If this is true, these two elements need to be swapped.

Once this method is implemented, you will need to test it in the main method. Construct an int array that includes 10 random numbers. Print the contents of the array before and after sorting.

---

## Lab 12 Task: Craps

Create a project called `Craps_FirstName_LastName` or `Lab12_FirstName_LastName`. Remember to include comments describing your program. A key component of this lab should be comments describing the methods used.

The steps provided are broken down into a bottom-up implementation. Methods implemented in earlier steps will be used in later steps.

### Methods Required

The following is a listing of the methods necessary for this program. This listing specifies the parameters and return types for each of the methods:

• The main method

• The `rollDice` method that takes no arguments and returns a one-dimensional int array

• The `sortResults` method that takes a one-dimensional int array and returns a one-dimensional int array

### Step 1 — Implement the rollDice method

In the `rollDice` method, construct a one-dimensional int array with a length of 11. This array will hold the number of times each number is rolled. For example, position 0 of this array holds the number of times a 2 is rolled, and position 10 (the last position) holds the number of times a 12 is rolled.

In the `rollDice` method, write a for loop that will iterate 10,000 times. In this for loop, generate two random numbers from 1-6 and add these numbers together. Increment the element at the position that represents the number rolled.

After the for loop in the `rollDice` method, return the int array.

### Step 2 — Implement the sortResults method

In the `sortResults` method, construct a one-dimensional array with the following initial values:

```java
{ 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12 }
```

The `sortResults` method will take the results array (the array passed into this method) and perform a bubble sort to place the results in increasing order. If elements in the results array are swapped, perform an identical swap on the one-dimensional array that was constructed in this method. (This second swap will be important for the output of this program later.)

After sorting both arrays, return the one-dimensional array that was constructed in this method.

### Step 3 — Implement the main method

In the main method, make a call to the `rollDice` method and assign the result to an int array. Next, make a call to the `sortResults` method and assign the result to another int array.

Finally, write a for loop that will iterate over all elements in either array (they both have the same length). The array returned from `rollDice` holds the probabilities of rolling a specific number, and the array returned from `sortResults` holds the corresponding number. Use this information to prepare print statements indicating the probability of rolling each number. The probability must be formatted to two decimal places. For example:

```
The probability of rolling a 2 is approximately 2.77%.
```

---

## Example Output

The following is an example program flow. Keep in mind that the dice rolls are random, so the outputs will be slightly different each time you run the program.

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

Make sure you have the following in your program:

• **Comments describing this program — 10 points**

• **Properly implementing the rollDice method — 42 points**
   - Method header — 6 points
   - Array construction — 4 points
   - For loop to handle dice rolls — 15 points
   - Properly incrementing the correct position of the array — 15 points
   - Writing the return statement — 2 points

• **Properly implementing the sortResults method — 68 points**
   - Method header — 5 points
   - Array construction — 4 points
   - Nested for loops to handle bubble sort — 35 points
   - Properly swapping elements in both arrays — 22 points
   - Writing the return statement — 2 points

• **Properly implementing the main method — 30 points**
   - Calling the rollDice method — 5 points
   - Calling the sortResults method — 5 points
   - For loop to print the results — 20 points

**The grade will be out of 150 points for this lab assignment.**
