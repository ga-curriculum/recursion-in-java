<h1>
  <span class="headline">Recursion in Java</span>
  <span class="subhead">Iterations and Recursions</span>
</h1>

**Learning objective:** By the end of this lesson, you'll be able to make decisions on whether to choose recursion or iteration in your program to express repetitive tasks.

## Algorithmic clarity
Clarity in code is important for making it easy to read, understand, and modify. One of the challenges that needs to be addressed for improving clarity is the number of lines of code. The more lines of code, the lesser the clarity and understandability of the algorithm. This has led to programming best-practices that target reducing the number of lines of code in a program. Once such best-practice is choosing to use recursion over iteration when dealing with repetitive logic.

Lets take an example of calculating the factorial of a given number. Mathematically, a factorial `n!` of an integer `n` is calculated by multiplying that integer and every other positive integer less than it. For example:
```plaintext
Factorial of 5 = 5 * 4 * 3 * 2 * 1
               = 120
```
This involves repetitively:
- Multiplying a `number` and `number - 1`.
- Decrementing `number` by `1`.  

Until `number` is 1.

Let's look at the iterative Java code to implement factorial calculation.

```java
public class IterativeFactorial {
    public static int factorial(int n) {
        int result = 1;
        for (int i = 1; i <= n; i++) {
            result *= i;
        }
        return result;
    }

    public static void main(String[] args) {
        int number = 5;
        System.out.println("Iterative Factorial of " + number + " is: " + factorial(number));
    }
}
```
The iterative approach to `factorial()` method used four lines of code, three variables `(result,n & i)` and evaluation of five expressions (`result =1`, `i = 1`, `i =<= n`, `i++`, `result *= i`).

## Recursion
Recursion is a process in which a function calls itself. Such a function is called a recursive function. Using a recursive algorithm, certain problems can be solved quite easily. Let's look at implementing the factorial calculation.

```java
public class RecursiveFactorial {
    public static int factorial(int n) {
        if (n == 0) {
            return 1; // Base case
        }
        return n * factorial(n - 1); // Recursive call
    }

    public static void main(String[] args) {
        int number = 5;
        System.out.println("Recursive Factorial of " + number + " is: " + factorial(number));
    }
}
```
We can see that the recursive approach to `factorial()` method needed only three lines of code, one variable `n` and two expressions to evaluate (`n == 0`, `n * factorial(n - 1)`).

### Advantages of recursion
1. Reduced lines of code
2. Simplified logic which is abstract, self contained and needs lesser control structures.
3. Improved readability because of more clarity and conciseness for recursion-friendly problems.

## Cautions while using recursion

### 1. Infinite recursion
Just as loops can run into the problem of infinite looping, recursive functions can run into the problem of infinite recursion. Infinite recursion is when the function never stops calling itself. Every recursive function should have a **halting condition**, which is the condition where the function stops calling itself.

In the `RecursiveFactorial` class above, the `if` condition serves both as a calculation logic (0! = 1) and also as the halting condition when `n` becomes `0` because of the `return` statement.

### 2. Time complexity of recursion
The time complexity of recursion depends on how many times the function calls itself. For example, if a function calls itself twice, its time complexity is `O(2^n)` where `n` is the input size. Comparatively, the time complexity of iteration is usually `O(n)`, where `n` is the input size. Though recursion may help in clarity of code, it would take a lot of CPU time.

### 3. `StackOverflowError` in Java
JVM allocates fixed and limited stack memory for tracing function calls and storing local function variables. It is typically 512 KB. Hence, with the increase in the input items to an algorithm, there is always an increased risk of JVM running out of stack memory during execution and throwing a `StackOverflowError`.

### 4. Memory consumption for variables
While iterative approach uses a fixed set of variables, in case of recursion even though the number of programmatically declared variables may be less, each instance of a function call allocates its own local memory for variables. Thus, recursive approach needs more memory than iterative approach.  


## Recursion vs iteration - Making a decision
Both approaches have their strengths and weaknesses. As a programmer, understanding when to use recursion versus iteration can lead to more efficient and readable code. It is a choice between code elegance and computing efficiency. When there is enough CPU power and no memory crunch, recursion is a better approach. When working with limited computing resources, iteration is a better approach.

## Final reflections

|Aspect|Recursion|Iteration|
|:---|:---|:---|
|**Applicable to**|Functions/Methods|Loops|
|**Halting condition**|To be explicitly coded.|Usually, part of the loop definition syntax.|
|**Code size**|Less|More|
|**Human readability**|Superior|Comparatively, inferior|
|**Execution Speed**|Slower|Faster|
|**Memory Usage**|More. Uses stack memory and more variable instances.|Less. No usage of stack.|
