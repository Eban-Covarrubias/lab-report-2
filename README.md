# lab-report-2

Part 1:
This is the code I made for StringServer, 
The functionality for the server is made in the StringHandeler class
which essentially is designed to search for either a / symbol or a /add-message at the end 
of the URL. Based on which it finds, the server will either display the messages that have been
added so far, or if propted to add a message the server will take in a request and add the message onto 
the end of the string.

![Image](StringServerCode.png)

Here are some screenshots of using /add-message, as you can see by adding a message into the URL
the web server will add the message onto a new line of the growing string. Note that the end of the path
looks like this: /add-message?s=How are you

![Image](How_are_you.png)
In this specific screenshot the methods called are: url.getPath().contains("/add-message") is called in order to verify that the path contains this specific string.
This is true, and the next method that is called is url.getQuery(). This returns the part of the path after the "?" symbol. The query in this case is s=How are you. The next method that is called is the split method, with an argument of "=". Calling split("=") and assinging the output to an array called parameters allows us to seperate the "s" and the "How are you" strings. From there we can use the .equals method on parameters[0] to verify that it is the string "s", and then we can concatenate the contents of parameters[1], which is "How are you", on the variable str, along with a new line character. This completes the functionality of the handleRequest method. This is called whenerever the webesite is loaded in.

Here is another example where I have added in multiple messages to the string, as you can see
the new message will be added to the previous message(s) in the next line.
![Image](AddingSecondLine.png)
In this screenshots the methods called are url.getPath().contains("/add-message") method in order to figure out if the path contains 
/add-message, if this is not in the path we will exit the if statement, any path other than "/" and "/add-message" will return "404 page not found". If the path is
/add-message the method url.getQuery() is used to get the paths Query. The Query is the part of the path after the "?" symbol. Next the split method
is called in order to seperate the two sides of the "=" in the Query. The two strings are saved in an array called parameters of size 2. If parameters[0]
is equal to "s" then the method continues and concatenates the value of parameters[1] to the variable str. This concatenation allows us to later display the value of 
the first added message after we add the second message. This entire process can be done as many times as you would like, in this specific example I only added to the string twice.

Part 2:
One of the buggy methods that I fixed was called averageWithoutLowest, here is the failure inducing test:

![Image](FailingTest.png)


Here is the actual buggy code being tested:

![Image](BuggyCode.png)


Here is a test that doesn't cause this buggy code to fail:

![Image](PassingTest.png)


And finally here is the symptom/output of running the tests:

![Image](JunitTestsOutput.png)
Note that the calculated value when the array is [1, 1, 5] 2.5 instead of 3, this is because the bug in the code causes the average to be
calculated without any of the lowest values. Meaning all of the 1's are removed, we are left with the value of 5/2 instead of (5+1)/2.

The bug in this code was that instead of simply removing the lowest value in the array, the code was actually removing every duplicate low value as well.
That is why when there was repeating 1's in a test the average was inaccurate, the code removed all the 1's instead of just a single 1.
The fix was quite simple, all that needed to be done was store the value of a lowest in a double and subtract it from the sum at the end of the for loop. Finding
the lowest value was also done in the same for loop that was adding up the sum. From there, the average could be accurately calculated and returned:

![Image](WorkingCode.png)


Part 3:
Something that I have learned is how to create a webserver and how URL's are incredibly important for passing information to webservers. I didn't realize how important the specific path of a URL was until I created a webserver that was modified entirely by entering queries into the path. I also learned a lot about testing with Junit, I previously have done all of my debugging using embeded print statements in my methods. Junit tests provide a much more clean and organized way to do testing on my methods.
