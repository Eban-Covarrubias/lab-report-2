# lab-report-2

This is the code I made for StringServer, 
The functionality for the server is made in the StringHandeler class
which essentially is designed to search for either a / symbol or a /add-message at the end 
of the URL. Based on which it finds, the server will either display the messages that have been
added so far, or if propted to add a message the server will take in a request and add the message onto 
the end of the string.

![Image](StringServerCode.png)

Here are some screenshots of using /add-message, as you can see by adding a message into the URL
the web server will add the message onto a new line of the growing string.

![Image](How_are_you.png)

![Image](AddingSecondLine.png)
