# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Recursion

| Title     | Type    | Duration | Author               |
|-----------|---------|----------|----------------------|
| Recursion | Lecture | 1:30     | Suresh Melvin Sigera |

## What is Recursion?

Recursion occurs when a method calls itself, either directly or indirectly through another method. This concept can be
seen in single or multiple recursive calls within the same method.

Understanding recursive algorithms can be challenging as it is not how humans typically approach problem-solving. For
instance, when painting a fence, most people would start at one end and continue to the other, rather than splitting the
task into smaller, recursive parts. However, certain structures, like trees, inherently lend themselves to recursive
solutions due to their natural, self-repeating patterns.

## Thought experiment

It’s time for some mind-bending activity—you’ve been thinking about the same, iterative style of programming for too
long. So let’s expose your brain to a totally different way of thinking about solving problems.

Before we get there, let's have a thought experiment. For example, take a handy list of numbers you want to sum up; it
could be any numbers, say the number of marbles you and each of your friends has in his or her pockets. To generate the
sum, we have construct the Java code like this:

```java
import java.util.ArrayList;
import java.util.List;

public class SumNumbersNoRecursive {
    public static void main(String[] args) {
        List<Integer> list = new ArrayList<>();
        list.add(5);
        list.add(6);
        list.add(7);
        list.add(10);
        list.add(9);
        int sum = 0;
        for (Integer integer : list) sum += integer;
        System.out.println("sum-> " + sum);
    }
}
```

Now let's pretend the folks who developed the Java language decided to remove any form of iteration (like the for and
while loops). But you still needed to sum a list of numbers, so could you do it without iteration?

There’s another approach that computer scientists (and some in-the-know coders) use to break down problems. At first,
this approach may seem a little like magic (or sleight of hand), but let’s get a feel for it by revisiting our problem
of summing our marbles. Here’s how the approach works: we come up with two cases for summing our list of numbers: a base
case, and a recursive case.

The base case is the simplest case you can think of. So what is the simplest list of numbers you can take the sum of?
How about an empty list? What is its sum? Zero, of course!

Now for the recursive case. With the recursive case we’re going to solve a smaller version of the same problem. Here’s
how: we take the first item in the list, and add it to the sum of the rest of the list...

```java
import java.util.ArrayList;
import java.util.List;

public class SumNumbersRecursive {
    // Method to calculate sum recursively
    public static int sumOfArray(Integer[] a, int n) {
        if (n == 0)
            // base case
            return a[n];
        else
            // recursive case
            return a[n] + sumOfArray(a, n - 1);
    }

    // Method- main()
    public static void main(String[] args) {
        // Creating a List of Integer type
        // Declaring an object- 'al'
        List<Integer> al = new ArrayList<Integer>();

        // Adding elements to the List
        // Custom inputs
        al.add(1);
        al.add(2);
        al.add(3);
        al.add(4);
        al.add(5);

        // Converting above List to array
        // using toArray() method
        Integer a[] = new Integer[al.size()];
        al.toArray(a);

        // Display message
        System.out.print("Elements in List : ");

        // Printing array of objects
        // using for each loop
        for (Integer obj : a) {
            System.out.print(obj + " ");
        }

        // Recursion math to calculate sum snd
        // storing sum in a variable
        int sum = sumOfArray(a, a.length - 1);

        // Next line
        System.out.println();

        // Print the sum returned above
        System.out.println("Sum of elements  : " + sum);
    }
}
```

Adapting your brain to think recursively can indeed require extra effort, but the payoff is immense—think less about the
challenge as a struggle, and more as an opportunity for growth. While we could spend considerable time dissecting the
SumNumbersRecursive example, the real mastery of recursive thinking comes from practice. The more you engage with
recursive problems and code them, the more intuitive this style of thinking will become.

Consider palindromes—words or phrases that read the same forward and backward, like “tacocat.” Other examples include
“madam,” “radar,” and “kayak,” or even entire phrases such as “a nut for a jar of tuna” or “a man, a plan, a canal:
panama” once you disregard punctuation and whitespace.

So, how about writing a recursive function to detect palindromes? What would we gain? Let’s explore. Writing a recursive
function typically involves two components: a base case and a recursive case:

**Base case**: The simplest scenario you can directly solve. An empty string is a palindrome by default since it reads
the same forwards and backwards. Similarly, a single letter is always a palindrome because it remains unchanged when
reversed.
**Recursive case**: This involves reducing the problem size slightly and then applying the function recursively. For
instance, if the first and last characters of a string match, the string is a palindrome if the substring between them
is also a palindrome.

Armed with our base and recursive cases, we're prepared to develop our recursive solution. Implementing the base case is
straightforward: check if the string is empty or a single character. The recursive case involves more nuanced thinking:
after confirming the first and last characters match, the remainder of the string (excluding these characters) is
checked recursively for palindrome properties. If they don't match, we immediately return False.

This structured approach to recursion not only makes the problem more manageable but also reinforces the recursive
mindset, helping you solve increasingly complex problems with this elegant method.

```java
import java.util.Scanner;

public class PalindromeCheckRecursive {
    public static boolean isPal(String s) {
        // if length is 0 or 1 then String is palindrome
        if (s.isEmpty() || s.length() == 1)
            return true;
        if (s.charAt(0) == s.charAt(s.length() - 1))
            /* check for first and last char of String:
             * if they are same then do the same thing for a substring
             * with first and last char removed. and carry on this
             * until you string completes or condition fails
             * Function calling itself: Recursion
             */
            return isPal(s.substring(1, s.length() - 1));

        /* If program control reaches to this statement it means
         * the String is not palindrome hence return false.
         */
        return false;
    }

    public static void main(String[] args) {
        //For capturing user input
        Scanner scanner = new Scanner(System.in);
        System.out.println("Enter the String for check:");
        String string = scanner.nextLine();
        /* If function returns true then the string is
         * palindrome else not
         */
        if (isPal(string))
            System.out.println(string + " is a palindrome");
        else
            System.out.println(string + " is not a palindrome");
    }
}
```

### No Question is Too Simple

- **Question**: How can we be sure a recursive function will eventually terminate?
    - **Answer**: The key to understanding when a recursive function will stop is the concept of the base case. This is
      a specific scenario within the problem that can be solved directly, without further recursion. Once the function
      reaches this base case, it stops calling itself, effectively ending the recursion.
- **Question**: How do we ensure that the function will reach the base case?
    - **Answer**: Each recursive call typically works with a slightly smaller or simpler version of the original
      problem. As long as the problem is continuously reduced in size or complexity at each step, and the reduction is
      correctly designed, the function will inevitably converge on the base case.
- **Question**How do function parameters remain consistent across recursive calls without getting mixed up?
    - **Answer**Excellent observation! In recursion, each function call has its own separate execution context,
      including parameters and local variables. This isolation means that changes to parameters or variables in one
      recursive call do not affect those in previous or future calls. Even though it might seem as if the same function
      is being called, each instance operates independently with its own set of data, thanks to how modern programming
      languages manage function calls' execution stacks. This management ensures that each recursive call is
      self-contained and consistent.

## Summary and Key Takeaways

### Summary

Recursion is a powerful technique in programming that simplifies certain problems by breaking them down into smaller,
manageable components. Here are the key takeaways:

### Key Takeaways

- **Recursive Thinking**: Transitioning to recursive thinking requires viewing problems as a series of smaller,
  self-similar tasks.
- **Base and Recursive Cases**: Effective recursive functions have clear base cases for direct solutions and recursive
  cases for reducing problem size.
- **Problem Suitability**: While recursion can provide elegant solutions for problems like tree traversal, summing
  elements, or checking palindromes, it's important to use it when it enhances clarity and efficiency.
- **Memory Considerations**: Each recursive call adds a layer to the call stack, which can lead to stack overflow in
  cases of deep recursion or large input sizes.

Recursion offers a different perspective on solving problems, often leading to cleaner, more readable code, but it's
crucial to understand its implications on performance and memory usage.






