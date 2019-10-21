## Fun Suggester II - *Son of Fun Suggester*


- Mission: Enhance your Fun Suggester!


## I. Functional and Presentational Details

There is a button that displays a new fun suggestion when it is clicked 
When the web app is closed, and then re-opened at a later time, the app will remember and display the most recent suggestion that was displayed to user 
Display a list of all of the suggestions (i.e. the array) to the user:
 the list will be sorted alphabetically this
this list will be hidden under a <details> tag
 the <summary> text will be  “All Suggestions”

4) Give the user a way to add a suggestion to the array:
    -  use an <input> element - something like this: <input id="newItem" type="text" value="New fun thing to do" />
    - there will be a button that the user can click to add the suggestion to the array
    - don’t let the user add the text “New fun thing to do” to the array
    - don’t let the user add an item to an array if it already exists in the array (i.e. the same item can not be in the array twice)
- this functionality (the input and button) will be hid under a <details> tag
- the <summary> text will be  “Add a Suggestion”

5) 



## II. Implementation details
Click a button to see a new suggestion:      - see Web Apps 6 - JavaScript Events for help with this
           - put the “random event generation” code in a function named getRandomEvent()

The app will remember the last suggestion:
	- see Web Apps 9 - WebStorage API for help with this
 
Display a list of suggestions:  - the list will be sorted alphabetically - see Web Apps 8 - JavaScript Arrays for help  - this list will be hidden under a <details> tag  - the <summary> text will be  “All Suggestions” -  see this page for help with <details> and <summary>: https://developer.mozilla.org/en-US/docs/Web/HTML/Element/details 

4) Give the user a way to add a suggestion to the array: 
  - clicking the “Add Suggestion” button will call the AddSuggestion() function
- this function will 

remember the last suggestion:
use Web Storage - see Web Apps 9 - WebStorage API for help with this



## III. Process
Find a partner in “the other” major so that we have teams consisting of 1 New Media Interactive Development (BS) student, and 1 New Media Design (BFA) student.
Choose a “driver” who will type all of the HTML & JavaScript for the app
Together, write the code necessary to get an MVP (minimum viable product) functioning version of the application 
Together, walk through the process of coding the CSS (and any additional HTML) for the app. You can switch drivers if you want to.


## IV. Submission
See dropbox for due date
This app will be submitted by the New Media Design student
Post this to the web
Send the link to your NMID partner
ZIP and POST to dropbox - and be sure to put the link and the name of your NMID partner in the comments field
