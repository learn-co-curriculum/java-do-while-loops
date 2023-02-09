# Do-While Loop

## Learning Goals

- Learn about do-while loops and how they differ from the other loops

## The do-while in Java

The last loop that we can use in Java is called a `do-while` loop. A
**do-while** loop acts differently from the other loops in that it is an exit
control loop. This means that we are checking a conditional at the bottom of
the loop. This also means that we will always run through a `do-while` loop at
least once. Let's look at the syntax of a `do-while` loop:

```java
do {
    // Code to run for each iteration of the loop
} while (boolean expression);
```

This loop is suited for situations where we know we want the logic to run at
least once through and then potentially iterate through again.

Let's look back at the example where we simulated the passing of time. But this
time, we will implement it within a `do-while` loop instead of a `while` loop.

```java
// simulate the passing of time
int startingYear = 2000;
int targetYear = 2011;
int currentYear = startingYear;
do {
    int yearDifference = currentYear - startingYear;
    System.out.println(yearDifference + " year(s) have passed");
    // conditional logic based on the current year
    currentYear++;
} while (currentYear < targetYear);
```

Let's break down what this `do-while` loop does:

Before we even get into the `do-while` loop, we initialize the variables
`startingYear` and `targetYear` to 2000 and 2011 respectively. Afterwards, we
set `currentYear` equal to `startingYear`. So `currentYear` will be assigned
the same value as `startingYear`, which is 2000.

Now we'll execute the first iteration of the loop:

1. Enter the `do-while` loop. Notice the difference between this execution and
   the previous loops we have seen so far. The `while` loop and the `for` loop
   would force us to check a conditional _before_ even entering the loop. Here
   the loop does not check a conditional first.
2. Calculate the difference between `currentYear` and `startingYear` and store
   the return value in the local variable `yearDifference`. So `yearDifference`
   would be set to 2000 - 2000, which is 0.
3. Since `yearDifference` is currently assigned the value of 0, we will print
   that out on a new line.
4. Increment `currentYear`. So `currentYear++` will reassign the variable
   `currentYear` to 2001.
5. Check the condition `currentYear < targetYear`. This boolean expression will
   evaluate to 2001 < 2011; which is true. So we will continue in the `do-while`
   loop.

Let's look at the next iteration of the loop:

1. Continue in the `do-while` loop since the conditional at the end of the
   loop evaluated to true.
2. Evaluate the expression `currentYear - startingYear` and store
   the return value in `yearDifference`. So 2001 - 2000 = 1.
3. Print out the value of `yearDifference` within the `println()` statement.
   So it will print the line "1 year(s) have passed".
4. Increment `currentYear`. So `currentYear++` will reassign `currentYear`
   to 2002.
5. Check the condition `currentYear < targetYear`. This boolean expression will
   evaluate to 2002 < 2011; which is true. So we will continue in the `do-while`
   loop.

This will go on until `currentYear` is set to 2011, at which point the
expression `currentYear < targetYear` will be no longer true. When the boolean
expression that is controlling the `do-while` loop is false, we will exit the
loop.

The final output of this code will be the following:

```java
0 year(s) have passed
1 year(s) have passed
2 year(s) have passed
3 year(s) have passed
4 year(s) have passed
5 year(s) have passed
6 year(s) have passed
7 year(s) have passed
8 year(s) have passed
9 year(s) have passed
10 year(s) have passed
```
