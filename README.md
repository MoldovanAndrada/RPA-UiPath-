# RPA-UiPath-



Goal:	     The constructed robot is able to automatically search for custom offers on a booking site and email the cheapest as well as the most expensive deals to a client.

Description:	     The robot reads from an excel file the input date concerning the destination of multiple people: location, period, number of persons.  Using this data, it will search different available offers on the site https://www.booking.com/index.html and save in a new excel file the most expensive, respectively the cheapest 2 offers it found on the first two pages. The results will be sent on the email address which is also mentioned in the input excel file.

Actors:	     Any client who wants to be able to inform multiple people about the best offers of booking.com can be an actor.

Preconditions:	     The folder of the project must contain the file “Book.xlsx” which is written in the corresponding format

Post Conditions	Success:	     A new file “Results.xls” can be found in the mail folder and an email is sent to all the email addresses mentioned in the initial excel file.

Post Conditions	Failure:	     An error indicating the failure details is present on the screen

Main Workflow/Success Scenario:     The user creates a file in which they mention the details about their desired booking, the computer then reads that .xlsx file and creates a dataTable structure storing an entry per row. The table is iterated on rows and variables are created for each element of the row. The variables are then introduced into the search fields of booking.com (location, the date which is being selected from the interactive calendar) and the default number of adults children and rooms is being increased or decreased accordingly. After the search button is clicked, the browser page is being scrolled down and each offer selected individually, so the name of the place and the price can be extracted and correlated. The tables containg the offers are sorted by price, once decreasing and one time increasing, then all other elements besides the first 2 will be deleted. Now the “Results.xlsx” file is ready to be sent to the corresponding email in the row.
 
Exceptions:	  First exception occurs when an element of the 2nd or 3rd column in the entry file does not correspond to a number, in that case a BusinessRuleException is thrown and when caught, the user is being notified via a Message Box about the problem and told which row he should change. If they doesn’t go in the “Book.xlsx” to change it, however, it will just be ignored during the future execution of the program. The second exception works and is being handled in the same way, but this time it checks whether or not the email field contains a “@” character.

Extensions:     We used Microsoft365 extension so that we could link the email address of the sender to the robot. It is possible for an error to occur and the things to go wrong if the input data does not match the patter, for example if a certain column that was not included in the expected exceptions contains, for example, a numeric element instead of s string, the robot may encounter a step when it cannot process it and has to stop. Another error can be caused by the misspelling of the entry file. Other ‘bad scenarios’ include a bad internet connection which cannot handle the automated navigation, or the client using a very slow PC which cannot keep up with the robot and needs extra delay seconds.  
 
Frequency of Use:	 Whenever the client is up for a holiday/weekend away, might be something like 5 times a year.
 



