# Do-While Loops

## Learning Goals

- Learn about `do-while` loops.

## What is a `do-while` Loop?

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

Notice the semicolon after the `while`. This is because in a `do-while` loop,
the `while` is a statement and not a block of statements.

This loop is suited for situations where we know we want the logic to run at
least once through and then potentially iterate through again. Consider the
flowchart below:

![do-while-loop-flowchart](https://curriculum-content.s3.amazonaws.com/java-mod-1/do-while-loops/do-while-conditional-flowchart.png)

## Do-While Loop in Action

Let's look at a program where we want the user to choose a lunch item from a
menu. Once the user chooses a menu item, a message will be displayed and the
program will present the menu again until the user is done choosing items.

```java
import java.util.InputMismatchException;
import java.util.Scanner;

public class LoopExample {
   public static void main(String[] args) {
      Scanner scanner = new Scanner(System.in);

      int choice = 0;

      do {
         // Prompt the user to select a menu item
         System.out.println("Welcome to the cafeteria! What would you like for lunch?");
         System.out.println("0. Exit");
         System.out.println("1. Pizza");
         System.out.println("2. Sandwich and Chips");
         System.out.println("3. Burger and Fries");

         try {
            choice = scanner.nextInt();

            // Display a message based on the user's choice
            switch (choice) {
               case 0:
                  // Do nothing - user wants to exit the program
                  break;
               case 1:
                  System.out.println("Here is your pizza!");
                  break;
               case 2:
                  System.out.println("Here is your sandwich and chips!");
                  break;
               case 3:
                  System.out.println("Here is your burger and fries!");
                  break;
               default:
                  System.out.println("Not a menu option - try again!");
            }
         } catch (InputMismatchException exception) {
            System.out.println("Invalid input");
         }
         
         // Add a new line for formatting
         System.out.println();

      } while (choice != 0);

   }
}
```

Let's break down what this `do-while` loop does:

1. Enter the `do-while` loop. Notice the difference between this execution and
   the previous loops we have seen so far. The `while` loop and the `for` loop
   would force us to check a conditional _before_ even entering the loop. Here
   the loop does not check a conditional first.
2. It will execute the statements inside the `do-while` loop and then check the
   condition at the _end_ of the first iteration of the loop to see if it should
   re-enter the loop.
3. Notice we are using a `switch` statement within the loop! We can nest
   conditionals and other loops inside a loop when appropriate.

If we run the program with the following input:

```text
1
2
3
0
```

The output would look like this:

```text
Welcome to the cafeteria! What would you like for lunch?
0. Exit
1. Pizza
2. Sandwich and Chips
3. Burger and Fries
1
Here is your pizza!

Welcome to the cafeteria! What would you like for lunch?
0. Exit
1. Pizza
2. Sandwich and Chips
3. Burger and Fries
2
Here is your sandwich and chips!

Welcome to the cafeteria! What would you like for lunch?
0. Exit
1. Pizza
2. Sandwich and Chips
3. Burger and Fries
3
Here is your burger and fries!

Welcome to the cafeteria! What would you like for lunch?
0. Exit
1. Pizza
2. Sandwich and Chips
3. Burger and Fries
0

```

We can take a closer look at this program by running it in the debugger and
analyzing each iteration.

We'll set three breakpoints:

- One on the
  `System.out.println("Welcome to the cafeteria! What would you like for lunch?");`
  line.
- Another on the `switch (choice)` line to go into the `switch` statement.
- And one more breakpoint on the `while (choice != 0);` line.

Let's run the debugger!

![hit-breakpoint-inside-do-while-loop](https://curriculum-content.s3.amazonaws.com/java-mod-1/do-while-loops/intellij-debugger-hit-breakpoint-8.png)

Notice that we are already within the first iteration of the loop! This is
because a `do-while` loop will always run through at least once. There is no
condition to check to enter the loop. Let's resume the program and enter in `1`
for the user input.

![hit-breakpoint-at-switch-statement](https://curriculum-content.s3.amazonaws.com/java-mod-1/do-while-loops/intellij-debugger-hit-breakpoint-9.png)

We hit the `switch` statement, which will determine which `case` the code should
execute based off the `choice` entered by the user. Since `choice` has the value
of `1`, we should see it enter the `case 1` block. Let's step-over and verify
this:

![enter-case-1](https://curriculum-content.s3.amazonaws.com/java-mod-1/do-while-loops/intellij-debugger-case-1.png)

When we step-over this line, the program will print "Here is your pizza!" to the
console and then will execute the `break` statement, which takes the execution
out of the `switch` statement. Let's resume the program. We should hit the
`while` statement this time:

![hit-while-statement-breakpoint](https://curriculum-content.s3.amazonaws.com/java-mod-1/do-while-loops/intellij-debugger-hit-breakpoint-10.png)

Since the conditional is at the end of the loop, we will evaluate here if we
should re-enter the loop. The boolean expression, `choice != 0` is currently
equivalent to `1 != 0` since `choice` is still set to the value of 1. The
expression will result in a `true` and take us up to the beginning of the loop.
Click on the step-over action again:

![second-iteration](https://curriculum-content.s3.amazonaws.com/java-mod-1/do-while-loops/intellij-debugger-hit-breakpoint-11.png)

And just like that, we enter into the second iteration of the `do-while` loop!
Let's resume the program and enter in `5` for the user input.

![hit-breakpoint-at-switch-statement-again](https://curriculum-content.s3.amazonaws.com/java-mod-1/do-while-loops/intellij-debugger-hit-breakpoint-12.png)

This time, the `choice` variable is set to the value of `5`. The `switch`
statement will look at its cases to see which case it should execute. Since no
cases specify `choice` having a value of `5`, it will fall into the `default`
case when we step-over:

![enter-default-case](https://curriculum-content.s3.amazonaws.com/java-mod-1/do-while-loops/intellij-debugger-default-case.png)

Let's resume the program:

![hit-while-breakpoint-again](https://curriculum-content.s3.amazonaws.com/java-mod-1/do-while-loops/intellij-debugger-hit-breakpoint-13.png)

This time, the conditional `choice != 0` is equivalent to `5 != 0`, which is
still `true`. So we'll step-over again and re-enter the loop.

![third-iteration](https://curriculum-content.s3.amazonaws.com/java-mod-1/do-while-loops/intellij-debugger-hit-breakpoint-14.png)

In this iteration, we'll resume the program and enter `0` for the user input:

![switch-statement-breakpoint](https://curriculum-content.s3.amazonaws.com/java-mod-1/do-while-loops/intellij-debugger-hit-breakpoint-15.png)

When we hit the `switch` statement this time, we'll see that when we step-over,
we'll enter in `case 0`.

![enter-case-0](https://curriculum-content.s3.amazonaws.com/java-mod-1/do-while-loops/intellij-debugger-case-0.png)

Notice that `case 0` does not do anything. It just has a `break` statement,
telling Java to exit out of the `switch` statement and proceed with executing
any statements after. We'll resume the program from here:

![exit-do-while-loop](https://curriculum-content.s3.amazonaws.com/java-mod-1/do-while-loops/intellij-debugger-exit-do-while-loop.png)

When we reach the `while` statement this time, the conditional, `choice != 0`
will be equivalent to `0 != 0`. The conditional is now `false` and we'll fall
out of the loop! If there were more statements after the loop to execute, the
program would continue. Since there are no statements after, we'll just resume
the program. The output in the console should look like this:

```text
Welcome to the cafeteria! What would you like for lunch?
0. Exit
1. Pizza
2. Sandwich and Chips
3. Burger and Fries
1
Here is your pizza!

Welcome to the cafeteria! What would you like for lunch?
0. Exit
1. Pizza
2. Sandwich and Chips
3. Burger and Fries
5
Not a menu option - try again!

Welcome to the cafeteria! What would you like for lunch?
0. Exit
1. Pizza
2. Sandwich and Chips
3. Burger and Fries
0

```

## Conclusion

We have now seen how to implement 3 different types of loops:

- `for` loop.
- `while` loop.
- `do-while` loop.

The `do-while` loop is an exit control loop, meaning the code within the loop
will run at least once through before determining if another iteration is
necessary.
