---
layout: post
title:  "Python: Amazon Price Scraper"
date:   2019-10-29 21:21:42 -0400
categories: Python
---

So Christmas is on the horizon and I thought it would be a fun side project / good break from all of the very low level C code to make a price scraper for Amazon. I followed a tutorial by Dev Ed 
on youtube which you can find [here](https://www.youtube.com/watch?v=Bg9r_yLk7VY&t=71s "Build A Python App That Tracks Amazon Prices"). Now this was a usable program but it had a few issues I wasn't sure I could live with 
so I sat out to make this program into something I and others may be more comfortable using. I doubt I will be able to fix all of these problems, I have 0 experience with python, but I will post an extensive list and mark 
off those that I have fixed thusfar here.
 
- [x] The number stored requires knowing ahead of time the number of digits it will contain - see Price Conversion
- [ ] The program has no GUI, not an issue for people used to working with a terminal but definitely hurts usability
- [ ] The program only tracks one product at a time
- [ ] The program requires a URL to work, possibly not an issue, but it would be better to have this stored in a variable instead of hard coded into the function
- [ ] The program only tracks prices whie running (duh), maybe we can webhost this or at least make it run on computer startup (Rasberry Pi microserver time?)
- [ ] If the price of the product does fall to where we want it to, it will send an email every time it checks again (at whatever frequency you have set)
- [ ] There is no way to change the price to notify by except changing a conditional within the program, maybe have that set to a variable based off of the original scan.
- [ ] There is no storage of the price changes over time, having this functionality may make it clear if an item being watched is holding its value or dropping over time
 
## Price Conversion
 
This was actually a very easy fix, we simply imported a decimal supporting library then stripping the dollar symbol from the stored value. The same method can be used to strip other currency symbols as well, and we no longer 
are storing a set number of digits, so we do not need to modify the progrom for each individual item based on the number of digits in its price moving forward.
 
![image](/assets/images/AmazonScraper.py Price Conversion - Visual Studio Code [Admi.png)