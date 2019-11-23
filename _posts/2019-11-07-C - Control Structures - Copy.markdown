---
layout: post
title:  "C: Control Structures"
date:   2019-10-29 21:21:42 -0400
categories: C
---

The beginning of this chapter focuses a great deal on pseudocode and control structures, for practice I will be writing pseudocode to pre plan each program added to this post.
Also mentioned are control structures, namely sequence, selection and repetition, there are only seven within the base C language. I will do my best to create concrete examples of each control structure type if they are not already included in the exercises.

(float) before an assigned expression can be used to temporarily change two variables to float so their decimal places may be stored. This is known as a cast operator and can be done for most data types.

This post will contain my takeaways from section 3 of the book, including a few simple commented programs. All code snipets seen within this post are available [here](https://github.com/Jlance999/C-How-to-Program "C-How-to-Program Repo").

## Gas Mileage
Drivers are concerned with the mileage obtained by their automobiles. One
driver has kept track of several tankfuls of gasoline by recording miles driven and gallons used for
each tankful. Develop a program that will input the miles driven and gallons used for each tankful.
The program should calculate and display the miles per gallon obtained for each tankful. After processing 
all input information, the program should calculate and print the combined miles per gallon
obtained for all tankfuls.

```c
#include <stdio.h>

int main(void) {
  float miles;  // Initializing global variables
  float gallonsused;
  float average;

// Describing program function to user
  printf("This program will give your miles per gallon per tank, as well as an average of all tanks if you input multiple sets of data.\n\n");

 

  while(gallonsused != -1) {        //Uses -1 as sentinal to stop program, otherwise loops
    
    printf("Enter the gallons used (-1 to end): "); // Promts user for data
    scanf("%f", &gallonsused);      // Assigns data to gallonsused variable

    float totalgallons;             // Initializing local variable (only needed during loop)
    totalgallons = totalgallons + gallonsused; // Stores the sum of each gallonused entry
    
    float totalmiles;
    totalmiles = totalmiles + miles;          // Stores the sum of each miles entry

    float totalaverage;                       // Calculates miles per gallon average
    totalaverage = totalmiles / (totalgallons+1);   // Uses (totalgallons+1) to offset -1 sentinal

    if (gallonsused != -1) {
      printf("Enter the miles driven: ");   // Promts user for data
      scanf("%f", &miles);                  // Stores data to miles variable

      average = miles/gallonsused;          // Calculates miles per gallon.

      // Displays miles per gallon of current loops data.
      printf("The miles/gallon for this tank was %.3f\n\n", average); 
    }

    else {
     // Displays average miles per gallon using all data gathered from each loop.  
      printf("\nThe overall average miles/gallon was %.3f", totalaverage);
    }
  }

  return 0; // End
}
```

Example Output:
![image](/assets/images/Gas Mileage.png)




## Credit Limit Calculator
Develop a C program that will determine if a department store
customer has exceeded the credit limit on a charge account. For each customer, the following facts
are available:
a) Account number
b) Balance at the beginning of the month
c) Total of all items charged by this customer this month
d) Total of all credits applied to this customer's account this month
e) Allowed credit limit
The program should input each fact, calculate the new balance (= beginning balance +
charges – credits), and determine whether the new balance exceeds the customer's credit limit. For
those customers whose credit limit is exceeded, the program should display the customer's account
number, credit limit, new balance and the message “Credit limit exceeded.”

```c
#include <stdio.h>

int accountNum;         // Initializing global variables
float begBalance;
float totCharges;
float totCredit;
float credLimit;
float finBalance;



int main(void) {

  while (accountNum != -1) {                          // Loop ends when user inputs -1
   printf("\nEnter account number (-1 to end): ");    // Prompting user for input
   scanf("%d", &accountNum);                          // Assigning user input to variable

    if (accountNum != -1) {                           // Only runs if user did not input -1

      printf("Enter beginning balance: ");            // Typical prompts and assignments
     scanf("%f", &begBalance);

     printf("Enter total charges: ");
     scanf("%f", &totCharges);

      printf("Enter total credits: ");
      scanf("%f", &totCredit);

    printf("Enter credit limit: ");
     scanf("%f", &credLimit);

    finBalance = begBalance + totCharges -totCredit;  // Calculating balance on account.

    if (finBalance > credLimit) {                     // Warns if charges exceed limit.
    // This looks incredibly messy but I was challenging myself to use one print statement
      printf("Account:\t\t%d\nCredit limit:\t%.2f\nBalance:\t\t%.2f\nCredit Limit Exceeded.\n",accountNum, credLimit, finBalance);
     }
   }
  }
  return 0;   // End
}
```

Example Output:
![image](/assets/images/Credit Limit Calculator.png)




## Printing Numbers from a Loop
Write a program that utilizes looping to print the numbers from 1 to 10 side by side on the same line with three spaces between numbers.

```c
#include <stdio.h>

int main(void) {

  int x = 1;
  
  while (x<=10) {
    printf("%d   ",x);
	
	x++;
  }
  return 0;
}
```

Example Output:
![image](/assets/images/Printing Numbers from a Loop.png)




Probably the easiest program since hello world, but it was the first time I found a use for incrementing in an exercise so I did it for
the sake of practice.

## Find the Largest Number
The process of finding the largest number (i.e., the maximum
of a group of numbers) is used frequently in computer applications. For example, a program that
determines the winner of a sales contest would input the number of units sold by each salesperson.
The salesperson who sells the most units wins the contest. Write a pseudocode program and then a
program that inputs a series of 10 non-negative numbers and determines and prints the largest of
the numbers. Hint: Your program should use three variables as follows:
counter: A counter to count to 10 (i.e., to keep track of how many numbers have
been input and to determine when all 10 numbers have been processed)
number: The current number input to the program
largest: The largest number found so far

### Pseudocode:
initialize variable largest
prompt for numbers
scan user input
if larger than previous number, save to variable, discard otherwise
	repeat until 10 numbers have been entered
	
print variable

```c
#include <stdio.h>

int main(void) {
  unsigned int largest;       // Initializing global variable, unsigned, no negative #
  int counter = 1;                  // Initializing global counter variable
  
  // Explaining program function to user.
  printf("This program will compare 10 positive integer and output the largest.\n\n");

  // Loop running 10 times
  while (counter <= 10) {
    int number;                    // Initializing local variable

    printf("Please enter value %d: ", counter);   // Prompting user for input
    scanf("%d", &number);                        // Stores value to temporary variable x 
    
    // Compares the current x with the stored largest value, and stores whichever is largest
    if (number > largest) {
      largest = number;
    }

    counter++;  // Keeping track of number of loops.
  }

  printf("\nLargest value given is %d\n", largest); // Prints largest value.

  return 0;
}
```

Example Output:
![image](/assets/images/Find the Largest Number.png)




I liked this exercise because it made me write my program out in pseudocode before starting, 
put a nested if statement into action and allowed me to make use of incrementing again.  I 
also took the liberty of using my counter in my printouts as we had to in the previous program 
because it made sense to keep track of how many values had been entered visually.
Simple, clean program.

## Finding the Two Largest Numbers
Using an approach similar to Exercise 3.23, find the two
largest values of the 10 numbers. [Note: You may input each number only once.]

```c
#include <stdio.h>

/*
 Using an approach similar to Exercise 3.23, find the two
largest values of the 10 numbers. [Note: You may input each number only once.]
*/

int main(void) {
  unsigned int largest;       // Initializing global variable, unsigned, no negative #
  unsigned int secondLargest;
  int counter = 1;                  // Initializing global counter variable
  
  // Explaining program function to user.
  printf("This program will compare 10 positive integer and output the largest.\n\n");

  // Loop running 10 times
  while (counter <= 10) {
    int number;                    // Initializing local variable

    printf("Please enter value %d: ", counter);   // Prompting user for input
    scanf("%d", &number);                        // Stores value to temporary variable x 
    
    // Compares the current x with the stored largest value, and stores whichever is largest
    if (number > largest) {
      secondLargest = largest;    // Stores current largest value as second largest
      largest = number;           // Stores new value as largest value
    }

    // In case the number is not the largest but is larger than current second largest
    if (number > secondLargest && number!= largest) {
      secondLargest = number;     
    }
    counter++;  // Keeping track of number of loops.
  }

  printf("\nLargest value given is %d\n", largest); // Prints largest value.
  printf("Second largest value given is %d\n", secondLargest); // Prints second largest


  return 0;
}
```

Example Output:
![image](/assets/images/Find the Two Largest Numbers.png)




There is no reason not to re-use my previous code for this so using the previous program
so I did so here as an example on how to iterate on previous code to get new results.

## Square of Asterisks

Write a program that reads in the side of a square and then prints that
square out of asterisks. Your program should work for squares of all side sizes between 1 and 20.

```c
#include <stdio.h>

int main(void) {
  int size;         // Initializing global variables
  int counter=0;

  // Explaining program function to user
  printf("This program will print a square in the size of your choosing, size is measured in number of characters across, any size from 1-20 is accepted.\n\n");

  printf("What size square would you like? ");  // Prompting user for input
  scanf("%d", &size);                           // Assigning input to size variable

  while(counter <= size) {                      // Will loop [size] times
    int counter2 = 0;                           // Resets counter for second loop to 0

   while (counter2 <= size) {                   // Outputs "* " [size] times
     printf("* ");

     counter2++;
   }
   printf("\n");                                // Moves output to new line

   counter++;                                   // Increments counter
  }
  return 0; // End
}
```

Example Output:
![image](/assets/images/Square of Asterisks.png)

To be honest I have skipped quite a few exercises thus far, especially those that seemed to use things
I already used in previous exercises, but just organized them trivially in another way. I decided to do 
this one because it seemed interesting even though it was basically text formatting again.

So after starting this program I realized it was one I had to ask for help with in my Intro to C course
and it did take me 3-4 extra minutes to figure out but its honestly so rewarding doing it correctly 
these years later, I will go ahead and try one more similar problem just to drill the work home.

## Hollow Square of Asterisks
Modify the program you wrote in Exercise 3.32 so that it
prints a hollow square.

```c
#include <stdio.h>

int main(void) {
  int size;         // Initializing global variables
  int counter=1;

  // Explaining program function to user
  printf("This program will print a hollow square of asterisks in the size of your choosing, 
  size is measured in number of characters across, any size from 1-20 is accepted.\n\n");

  printf("What size square would you like? ");  // Prompting user for input
  scanf("%d", &size);                           // Assigning input to size variable

  while(counter <= size) {                      // Will loop [size] times
    int counter2 = 0;                           // Resets counter for second loop to 0

    if(counter == 1 || counter == size) {       // Only runs the first and last line.
     while (counter2 < size) {                  // Outputs "* " [size] times
      printf("* ");

      counter2++;                               // Increments counter
      }
    }

    else {
      int counter3 = 0;                         // Initializing local counter
      printf("* ");                             // Prints first two characters of inner
      while (counter3 <= (size-3)) {            // Accounts for the 3 characters outside
        printf("  ");
        counter3++;                             // Increments counter for spaces in inner
      }
      printf("*");                              // Prints last character of inner lines
    }
   printf("\n");                                // Moves output to new line

   counter++;                                   // Increments counter
  }
  return 0; // End
}
```

Example Output:
![image](/assets/images/Hollow Square of Asterisks.png)

I was honestly surprised by how many nested loops I needed for this, maybe the way I did it is inneficient, 
however I really enjoyed this exercise. The core change here is just forming logic for when to print different
lines. I realized I only needed my previous loop during the first and last lines so I set up an if loop to run it
the first line and the [size] line, allowing it to scale and know based on the user input where to print itself.
I simply printed the middle lines every loop that I was not printing the first and last lines, determining its 
output using the size variable much in the way I did with the original program, but subtracting 3 characters from it 
so I could print the first asterisk and space and asterisk after outside of the loop.

## How Fast is Your Computer?
How can you determine how fast your own computer really
operates? Write a program with a while loop that counts from 1 to 1,000,000,000 by 1s. Every time
the count reaches a multiple of 100,000,000, print that number on the screen. Use your watch to
time how long each 100 million repetitions of the loop takes.

```c
#include <stdio.h>

int main(void) {
  int counter = 0;  // Initializing counter variable

  while (counter <= 1000000000) {       // Loops 1 billion times
    if ((counter % 100000000) == 0) {   // Prints any number divisible by 100 million
      printf("%d\n", counter);
    }
    counter++;                          // Ups counter by 1 per loop
  }
  return 0;   // end
}
```

Example Output:
![image](/assets/images/How Fast is Your Computer.png)

Not much garnered from this program to be honest, it was very simple I just hadn't previously used the remainder
operator.

## Palindrome Tester
A palindrome is a number or a text phrase that reads the same backward as forward. For example, each of the following five-digit integers is a palindrome: 12321,
55555, 45554 and 11611. Write a program that reads in a five-digit integer and determines whether
or not it’s a palindrome. [Hint: Use the division and remainder operators to separate the number
into its individual digits.]

```c
#include <stdio.h>
 
int main()
#include <stdio.h>
 
int main()
{
   int posPalindrome;                   // Initializing variable to hold user input
   int revPosPalindrome = 0;            // Initializing variable to hold reverse of input
   int i;                               // Initializing holding variable
 
    // Explaining program function to user
   printf("This program will take a 5 digit integer input and determine if it is a Palindrome.\n\n");
 
    // Promtping user for input
   printf("Please enter a 5 digit integer: ");
    // Storing user input
   scanf("%d", &posPalindrome);
    // Holding user input in temporary variable for use in calculations
   i = posPalindrome;
  
    // Could also just be when it runs 5 times, but this allows longer integer inputs.
   while (i != 0)
   {
     // Adds a 0 to the end of current stored value, matters later
      revPosPalindrome = revPosPalindrome * 10;

     // Adds the remainder of i divided by 10, this replaces the 0 from the last line
      revPosPalindrome = revPosPalindrome + i%10;
 
     // Divides held value by 10, this drops the last digit, which is now stored in revPal
      i = i/10;
   }
 
    /*After the while function has completed, the revPosPalindrome variable will hold the
      user input value backwards to forwards. At this point we only need to compare them to
      determine if the value is a Palindrome.
    */
   if (posPalindrome == revPosPalindrome)
      printf("%d is a palindrome number.\n", posPalindrome);
   else
      printf("%d isn't a palindrome number.\n", posPalindrome);
 
   return 0;  // End
}
```

Example Output:
![image](/assets/images/Palindrome Tester.png)



Honestly I wasn't able to figure this one out on my own. I ended up finding the solution online elsewhere 
and using a printf command within the loop to understand what was happening. By printing between each 
line within the while name I was able to determine how the loop functioned, in this case I've explained it
all within the commented code. The wheel does not always need to be reinvented. Sometimes you are better off
saving your time, learning how it was done elsewhere and implementing it so you have the understanding to do it
in the future.

## Printing the Decimal Equivalent of a Binary Number
Input an integer (5 digits or fewer)
containing only 0s and 1s (i.e., a “binary” integer) and print its decimal equivalent. [Hint: Use the
remainder and division operators to pick off the “binary” number’s digits one at a time from right
to left. Just as in the decimal number system, in which the rightmost digit has a positional value of
1, and the next digit left has a positional value of 10, then 100, then 1000, and so on, in the binary
number system the rightmost digit has a positional value of 1, the next digit left has a positional
value of 2, then 4, then 8, and so on. Thus the decimal number 234 can be interpreted as 4 * 1 + 3
* 10 + 2 * 100. The decimal equivalent of binary 1101 is 1 * 1 + 0 * 2 + 1 * 4 + 1 * 8 or 1 + 0 + 4
+ 8 or 13.]


```c
#include <stdio.h>

int main(void) {

int binaryIn;           // Processing global variables
int processing;         // Holds rightmost binary digit to be processed
int digitalOut=0;       // Initializing digital value to 0, errors were produced otherwise
int holding;            // not needed. could use binaryIn instead for the entire program

printf("This program takes a user input binary number and returns its decimal equivalent.\n\n");

printf("Please enter binary number for conversion: ");
scanf("%d", &binaryIn);

holding = binaryIn; // Holds initial binary value, redundant in this case, not needed
int digitalProc=0;  // Initializes variable that will process binary value to digital
int binMult = 1;

while (holding !=0) {
  processing = holding%10;  // Puts rightmost value of holding into a variable for use

  digitalProc= processing*binMult;  // Multiplies rightmost variable to get digital value

  digitalOut = digitalOut + digitalProc;  // Adds 1s, 2s, 4s, 8s, etc binary inputs

  holding = holding/10; // Removes rightmost value from further processing

  binMult = binMult*2;  // Multiplies itself by 2, because binary goes up in power of 2
}

printf("Decimal value is %d\n", digitalOut);  // Output

  return 0; // End
}
```

Example Output:
![image](/assets/images/Printing the Decimal Equivalent of a Binary Number.png)


I wanted to leave this as an example of how to understand what is going on during your loops. This 
is the same process I used in the previous problem to understand how it was done, this time I did it
to debug my own code and came up with the solution to this problem on my own.

Example Output:
![image](/assets/images/Printing the Decimal Equivalent of a Binary Number1.png)




## Factorial
The factorial of a nonnegative integer n is written n! (pronounced “n factorial”)
and is defined as follows:
n! = n · (n - 1) · (n - 2) · … · 1 (for values of n greater than or equal to 1)
and
n! = 1 (for n = 0).
For example, 5! = 5 · 4 · 3 · 2 · 1, which is 120.
a) Write a program that reads a nonnegative integer and computes and prints its factorial.

```c
#include <stdio.h>

int main(void) {
  unsigned int factorial; // Global variable to hold user input
  int totalIn = 0;        // Counter variable
  int totalOut;       // Initializing variable to hold final answer

    // Explaining program function to user
  printf("This program will take a single digit integer input and output the factorial.\n");

    // Prompting user for input
  printf("Please enter integer: ");
  scanf("%d", &factorial);     // Storing user input to variable
  totalIn = factorial -1;      // Initializing counter variable value based on input
  totalOut = factorial;        // Holding user input for calculation, not needed

  while (totalIn > 0) {               // Loops until counter hits 0
    totalOut = totalOut * totalIn;    // Multiplies user input by counter current value
    totalIn--;                        // Reduces counter value by 1 every loop
  }
  printf("\nThe factorial is %d\n", totalOut);  // Output

  return 0;   // End
}
```

Example Output:
![image](/assets/images/Factorial.png)




## Target-Heart-Rate Calculator
While exercising, you can use a heart-rate monitor to see
that your heart rate stays within a safe range suggested by your trainers and doctors. According to
the American Heart Association (AHA), the formula for calculating your maximum heart rate in
beats per minute is 220 minus your age in years. Your target heart rate is a range that’s 50–85% of
your maximum heart rate. [Note: These formulas are estimates provided by the AHA. Maximum
and target heart rates may vary based on the health, fitness and gender of the individual. Always consult a physician or qualified health care professional before beginning or modifying an exercise program.]
Create a program that reads the user’s birthday and the current day (each consisting of the month,
day and year). Your program should calculate and display the person’s age (in years), the person’s
maximum heart rate and the person’s target-heart-rate range.

```c
#include <stdio.h>

int main(void) {
    // Variables to hold birthdate values
  int birthMonth;
  int birthDay;
  int birthYear;
    // Variables to hold current date values
  int curMonth;
  int curDay;
  int curYear;

    // Explains program functionality to user
  printf("This program will take your birth date and the current date and output your age, maximum heart rate, and target heart rate.");

    // Typical prompt / storage
  printf("Please enter your birthday month MM: ");
  scanf("%d", &birthMonth);

  printf("Please enter your birthday day DD: ");
  scanf("%d", &birthDay);

    printf("Please enter your birthday year YYYY: ");
  scanf("%d", &birthYear);

  printf("Please enter the current month MM: ");
  scanf("%d", &curMonth);

  printf("Please enter the current day DD: ");
  scanf("%d", &curDay);

  printf("Please enter the current year YYYY: ");
  scanf("%d", &curYear);

  int age = curYear - birthYear;                  // Calculates age, if statements do rest
  int maxHeartRate = 220-age;                     // Calculates heartrate based on age
  int lowTarHeartRate = maxHeartRate*.5;          // Calculates lower end target heart rate
  int highTarHeartRate = maxHeartRate*.85;        // Calculates higher end target heart rate

   // If current month is after birth month, we know the age, and will print.
  if (curMonth>birthMonth){
  printf("\nYou are %d\nYourYour Maximum Heart Rate is %d\nYour Target Heart Rate is %d-%d\n", age,maxHeartRate, lowTarHeartRate, highTarHeartRate);
  }
    // If the current month is the same as the birth month, we need further checks
  else if (curMonth == birthMonth) {
    if (curDay > birthDay || curDay == birthDay) {
      printf("\nYou are %d\nYour Maximum Heart Rate is %d\nYour Target Heart Rate is %d-%d\n", age, maxHeartRate, lowTarHeartRate, highTarHeartRate);
    }

    // If the current day is within the same month but before the birth day, age adjust
    else {
      age = age-1;              // Refactoring age
      maxHeartRate = 220-age;   // Refactoring maximum heart rate with new age value

      printf("\nYou are %d\nYour Maximum Heart Rate is %d\nYour Target Heart Rate is %d-%d\n", age, maxHeartRate, lowTarHeartRate, highTarHeartRate);
    }
  }
    // If the current month is before the birth month, we know the age value needs adjustment
  else {
    age = age-1;                // Refactoring age
    maxHeartRate = 220-age;     // Refactoring maximum heart rate with new age value

    printf("\nYou are %d\nYour Maximum Heart Rate is %d\nYour Target Heart Rate is %d-%d\n", age, maxHeartRate, lowTarHeartRate, highTarHeartRate);
  }

  return 0;   // End
}
```

Example Output:
![image](/assets/images/Target-Heart-Rate Calculator.png)




## Enforcing Privacy with Cryptography
The explosive growth of Internet communications
and data storage on Internet-connected computers has greatly increased privacy concerns. The field
of cryptography is concerned with coding data to make it difficult (and hopefully—with the most
advanced schemes—impossible) for unauthorized users to read. In this exercise you’ll investigate a
simple scheme for encrypting and decrypting data. A company that wants to send data over the Internet has asked you to write a program that will encrypt it so that it may be transmitted more securely. All the data is transmitted as four-digit integers. Your application should read a four-digit
integer entered by the user and encrypt it as follows: Replace each digit with the result of adding 7
to the digit and getting the remainder after dividing the new value by 10. Then swap the first digit
with the third, and swap the second digit with the fourth. Then print the encrypted integer. Write
a separate application that inputs an encrypted four-digit integer and decrypts it (by reversing the
encryption scheme) to form the original number. [Optional reading project: Research “public key
cryptography” in general and the PGP (Pretty Good Privacy) specific public key scheme. You may
also want to investigate the RSA scheme, which is widely used in industrial-strength applications.]

```c
#include <stdio.h>

  // Work in progress, I have not figured out how to deal with 0 values in last step
int main(void) {

  int unencrypted;
  int firstArith;
  int revEncrypted = 0;
  int encrypted = 0;
  int fullEncrypted;

    // Explains program function to user
  printf("This program will read a 4 digit integer, and encrypt it to be de-encrypted by its partner program.\n");

  printf("Please enter a 4 digit integer: ");     // Prompts user for input
  scanf("%d", &unencrypted);                      // Stores input for modification

  while (unencrypted != 0) {
    
      // Uses requested arithmetic to hide original values
    firstArith = unencrypted % 10;
    firstArith = firstArith + 7;
    firstArith = firstArith % 10;

    revEncrypted = revEncrypted * 10;
    revEncrypted = revEncrypted + firstArith;
    printf("revEncrypted is %d\n", revEncrypted);

    unencrypted = unencrypted / 10;
    printf("Unencrypted is %d\n", unencrypted);
  }
  
    // Un-reverses previously encrypted integer
  while (revEncrypted != 0) {

    encrypted = encrypted * 10;
    encrypted = encrypted + (revEncrypted % 10);
    printf("Encrypted is %d\n", encrypted);

    revEncrypted = revEncrypted / 10;
    printf("revEncrypted is %d\n", revEncrypted);
  }
    // Initializing holding value for modification
  int holding = encrypted;
  holding = holding / 10;
  holding = holding % 10;

    // Swaps 3rd value to the front of fullEncrypted.
  fullEncrypted = holding;
  fullEncrypted = fullEncrypted * 10;
  printf("fullEncrypted is %d\n", fullEncrypted);

    // Initializing holding value for modification
  holding = encrypted;
  holding = holding % 10;

    // Swaps 4th value to the second slot of integer
  fullEncrypted = fullEncrypted + holding;
  fullEncrypted = fullEncrypted * 10;
  printf("fullEncrypted is %d\n", fullEncrypted);

    // Initializing holding value for modification
  holding = encrypted;
  holding = holding / 1000;
  holding = holding % 10;

    // Swaps 1st value to the 3rd slot of integer
  fullEncrypted = fullEncrypted + holding;
  fullEncrypted = fullEncrypted * 10;
  printf("fullEncrypted is %d\n", fullEncrypted);

    // Initializing holding value for modification
  holding = encrypted;
  holding = holding / 100;
  holding = holding % 10;

    // Swaps 2nd value to the 4th slot of integer
  fullEncrypted = fullEncrypted + holding;
  printf("fullEncrypted is %d\n", fullEncrypted); // Prints final value
  


  return 0;   // End
}
```

Example Output:
![image](/assets/images/Enforcing Privacy with Cryptography.png)