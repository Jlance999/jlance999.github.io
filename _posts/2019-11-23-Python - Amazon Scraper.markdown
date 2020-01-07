---
layout: post
title:  "Python: Amazon Price Scraper"
date:   2019-11-23 21:21:42 -0400
categories: Python
---

So Christmas is on the horizon and I thought it would be a fun side project / good break from all of the very low level C code to make a price scraper for Amazon. I followed a tutorial by Dev Ed 
on youtube which you can find [here](https://www.youtube.com/watch?v=Bg9r_yLk7VY&t=71s "Build A Python App That Tracks Amazon Prices"). Now this was a usable program but it had a few issues I wasn't sure I could live with 
so I sat out to make this program into something I and others may be more comfortable using. I doubt I will be able to fix all of these problems, I have 0 experience with python, but I will post an extensive list and mark 
off those that I have fixed thusfar here.
 
## Problems 

- [x] The number stored requires knowing ahead of time the number of digits it will contain - see Price Conversion
- [ ] The program has no GUI, not an issue for people used to working with a terminal but definitely hurts usability - see GUI
- [ ] The program only tracks one product at a time
- [ ] The program requires a URL to work, possibly not an issue, but it would be better to have this stored in a variable instead of hard coded into the function
- [ ] The program only tracks prices whie running (duh), maybe we can webhost this or at least make it run on computer startup (Rasberry Pi microserver time?)
- [ ] If the price of the product does fall to where we want it to, it will send an email every time it checks again (at whatever frequency you have set)
- [ ] There is no way to change the price to notify by except changing a conditional within the program, maybe have that set to a variable based off of the original scan.
- [x] There is no storage of the price changes over time, having this functionality may make it clear if an item being watched is holding its value or dropping over time - see Saving Data to Files
 
## Price Conversion
 
23 Nov 19: This was actually a very easy fix, we simply imported a decimal supporting library then stripping the dollar symbol from the stored value. The same method can be used to strip other currency symbols as well, and we no longer 
are storing a set number of digits, so we do not need to modify the progrom for each individual item based on the number of digits in its price moving forward.
 
![image](/assets/images/AmazonScraper.py Price Conversion - Visual Studio Code.png)

## Saving Data to Files

03 Jan 20: My current solution is saving data to a txt file. This is subject to change and still needs some work at this time. Namely, now that I have began with setting up a live graph through matplotlib I realize I need to also store the date and possibly time along with the price in order to properly graph the changes over time. I'll use the time library and simple concatonation with a comma as my delimmiter and split the data, but have not set this up yet.

05 Jan 20: Storage of values and date to text now fully automated and formatted to be plotted by graphing function. To do this I utilized the time function, converted the current time to a string and saved it to my txt file on the same line as my price value. It may be nice to have the date format itself configurable by the user when this is a finished product.

![image](/assets/images/AmazonScraper.py Date to txt - Visual Studio Code.png)

## Graphing Data

03 Jan 20: I've imported matplit lib and am currently digging through its documentation and a few tutorials elsewhere (sentdex on YouTube) in order to try to get this running. As of now I'm displaying a graph but still need to figure out how to properly get my data to display.

04 Jan 20: Data is now showing on graph, the reason it was not working previously was due to how I was storing data to the txt file. Using a different text file with my own inputs it worked without issue. Because I was not storing the date the graph function was looking for a second variable to split and finding only the price. Once I've set up my data storage function with the ability to store the date with the price the issue should be permenantly fixed. I also had a few issues with my animate function not being a child function of the graph function, and variable hierchy not being used. By making the graph itself a variable local to the graph function and nesting the animate function which will poll the text document for changes at a set rate (1 second currently) I was able to fix this issue.

![image](/assets/images/AmazonScraper.py Graph Function - Visual Studio Code.png)

![image](/assets/images/AmazonScraper.py Graph Example - Visual Studio Code.png)

## GUI

06 Jan 20:
Using tkinter I was able to begin working my way to a useable GUI, its pretty awful at this point, and is taking quite a lot of refactoring of the program as whole to get working. Previously I was using the original tutorials janky implementation to run the program with a while(True) statement. From this point I will be working to make the program less autonomous and more GUI oriented. I intend to make how often things are checked configurable as well as a few other options, as well as implement the graph function into the GUI itself if possible, or have it ran on a button press instead of running each time the program is executed.

![image](/assets/images/AmazonScraper.py GUI Beginnings - Visual Studio Code.png)