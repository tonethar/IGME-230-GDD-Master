# Fun Suggester II - *Son of Fun Suggester*


- Mission: Enhance your Fun Suggester!


## I. Functional and Presentational Details

1) There is a button that displays a new fun suggestion when it is clicked

2) When the web app is closed, and then re-opened at a later time, the app will remember and display the most recent suggestion that was displayed to user 

3) The app displays a list of all of the suggestions (i.e. the array) to the user:
    - the list will be sorted alphabetically
    - the list will be hidden under a `<details>` tag
    - the `<summary>` text will be  “All Suggestions”

4) Give the user a way to add a suggestion to the array:
    - use an `<input>` element
    - there will be a `<button>` that the user can click to add the suggestion to the array
    - do not let the user add the text "New fun thing to do" to the array
    - do not let the user add an item to the suggestions array if it already exists in said array (i.e. the same item can not be in the array twice)
    - this functionality (the `<input>` and `<button>` will be hidden under a `<details>` tag
    - the `<summary>` text will be  "Add a Suggestion"

5) 



## II. Implementation details

1) Click a button to see a new suggestion:
    - see [Web Apps 6 - JavaScript Events](./web-apps-6.md) for help with this
    - put the "random event generation" code in a function named `getRandomEvent()`
      - See [Web Apps 5 - JavaScript Functions](./web-apps-5.md) for help on writing functions

2) The app will remember the last suggestion:
    - see [Web Apps 9 - WebStorage API](./web-apps-9.md) for help with this
  
3) Display a list of all suggestions:
    - the list will be sorted alphabetically - see [Web Apps 8 - JavaScript Arrays](./web-apps-8.md) for help
    - see this page for help with `<details>` and `<summary>`: 
      - https://developer.mozilla.org/en-US/docs/Web/HTML/Element/details

4) Give the user a way to add a suggestion to the array: 
    -  the `<input>` can look something like this: 
      - `<input id="newItemInput" type="text" value="New fun thing to do" />`
    - clicking the "Add Suggestion" button must call an `addSuggestion()` function
    

5) 



## III. Process
  - Get back with your *Fun Suggester* partner from last time
  - If you were not here last time, find someone to work with, and get going on *Fun Suggester* first


## IV. Submission
  - See dropbox for due date
  - This app will be submitted by the New Media Design student
  - Post this to the web
  - Send the link to your NMID partner
  - ZIP and POST to dropbox - and be sure to put the link and the name of your NMID partner in the comments field
