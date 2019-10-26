---
layout: post
title:  "C: First Simple Programs"
date:   2019-10-26 11:21:42 -0400
categories: C
---

This post will contain my takeaways from section 2 of the book, including a few simple commented programs. All code snipets seen within this post are available on both my repl.it and my github, usernames for both are jlance999.

II: Introduction to C Programming
##Hello World
We start with the obvious first program anyone makes, simply displaying "Hello World" to the screen.

```c
#include <stdio.h> // Include standard input and output library functions (such as printf).

int main(void) {
  // Main function, every program must have one. Void means it receives no values.
  printf("Hello World\n"); // What will be displayed, f stands for "formatted", \n begins a new line after World
  return 0; // Every line must end with a ;, functions are defined between a set of braces. 0 is the value returned by this function as we do not need it to return a value.
}
```

Nearly everything is commented here, worth noting is that anything following // is a comment, and will not be ran as instructions.

