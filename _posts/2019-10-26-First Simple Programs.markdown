---
layout: post
title:  "C: First Simple Programs"
date:   2019-10-26 11:21:42 -0400
categories: C
---

This post will contain my takeaways from section 2 of the book, including a few simple commented programs. All code snipets seen within this post are available [here](https://github.com/Jlance999/C-How-to-Program "C-How-to-Program Repo").

# II: Introduction to C Programming

## Hello World
We start with the obvious first program anyone makes, simply displaying "Hello World" to the screen.

```c
#include <stdio.h> // Include standard input and output library functions (such as printf).

int main(void) {
  // Main function, every program must have one. Void means it receives no values.
  printf("Hello World\n"); // What will be displayed, f stands for "formatted", \n an escape sequence which begins a new line after World
  return 0; // Every line must end with a ;, functions are defined between a set of braces. 0 is the value returned by this function as we do not need it to return a value.
}
```

Example Output:
![image](/assets/images/Hello World.png)


Nearly everything is commented here, worth noting is that anything following // is a comment, and will not be ran as instructions.

Other escape sequences include:
* \t for a tab
* \a for an alert (will produce a sound or visable alert)
* \" for a double quote
* \\ to place a single \

## Arithmatic Functions
Next we go over basic arithmetic operators, as it was an exercise in the end of chapter.

```c
#include <stdio.h>

int main( void) {

									// Initializing global variables.
int int1;
int int2;
int sum;
int difference;
int quotient;
int product;
int remainder;

printf("Enter first integer: ");	// Prompts user for integer value
scanf("%d", &int1);					// Records integer value to be used in calculations

printf("Enter second integer: ");
scanf("%d", &int2);

sum = int1 + int2;					// Stores the sum of the 2 integer variables as a sum variable.
printf("\n\nSum: %d.\n", sum);		// Prints Sum: and the value stored in the sum variable.

difference = int1 - int2;
printf("Difference: %d.\n", difference);

quotient = int1 / int2;
printf("Quotient: %d.\n", quotient);

remainder = int1 % int2;
printf("Remainder: %d.\n", remainder);

return 0;							// End program (non commented functions are self explanatory.)
}
```

Example Output:
![image](/assets/images/Arithmetic Functions.png)




The only other things covered in this chapter are the use of () to denite which arithmetic should be done first, for instance when adding multiple variables then dividing them by one value, and the use of equality operands / if statements,
 we will use them shortly.

 There are a few other exercises that seem interesting for this chapter, the following is their requirements and my take on them.

 
## Printing Values with printf
Write a program that prints the numbers 1 to 4 on the same
line. Write the program using the following methods.
a) Using one printf statement with no conversion specifiers.
b) Using one printf statement with 4 printf statements.

```c
#include <stdio.h>

int main(void) {
  int num1 = 1;     // Assignment of values for second statement.
  int num2 = 2;
  int num3 = 3;
  int num4 = 4;

  printf("1234\n"); // Printing the numbers as plane text.

  printf("%d%d%d%d\n", num1, num2, num3, num4); // Printing the numbers as integers.

  printf("1");      // Printing four statements to the same line.
  printf("2");
  printf("3");
  printf("4\n");

  return 0;
}
```


##Comparing Integers
Write a program that asks the user to enter two integers, obtains the
numbers from the user, then prints the larger number followed by the words “is larger.” If the
numbers are equal, print the message “These numbers are equal.” Use only the single-selection
form of the if statement you learned in this chapter.


#include <stdio.h>      // Included to allow use of scanf/printf
```c
int main(void) {
int int1;     //initializing variables to hold user input
int int2;

  printf("Please enter first integer for comparison: "); // Prompting user for input
  scanf("%d", &int1);                                    // Assinging input to int variable

  printf("Please enter second integer for comparison: ");
  scanf("%d", &int2);

  if (int1 == int2){                                     // Testing for equal values
    printf("These numbers are equal\n");
  }

  if(int1 > int2){                                      // Testing if int1 is a larger int
    printf("%d is larger.\n", int1);
  }

  if(int2 > int1){                                      // Testing if int2 is a larger int
    printf("%d is larger.\n", int2);
  }

  return 0;   // End
}
```

Write a program that inputs three different
integers from the keyboard, then prints the sum, the average, the product, the smallest and the largest of these numbers. Use only the single-selection form of the if statement you learned in this chapter.


