# ICE: HTML, CSS, and Validation

## Formatting a Recipe		

### Overview

Today you will be given an existing HTML page that already has significant content, in this case, a recipe. Your tasks are to:
- mark it up with the appropriate HTML tags
- improve the presentation of the page by utilizing  a variety of CSS properties as well as type, class, and id selectors. 
- run it through the HTML validator to ensure your markup is well-written

### Part 1: Get the files

1. Download a copy of the startup files from the content area of our myCourses conference.
2. Rename the included HTML file to:  kadayif.html.
3. Change the contents of the `<title>` tag so it includes your full name
4. Now, go ahead and preview the file in your browser.  You should see something like this:  
[image goes here]
5. Pretty ugly, huh?  Let’s continue to part 2

### Part 2:  Adding Structure and Meaning to the Content

Let’s add some structural and semantic tags to this mess!

1. Add `<h1>` tags to the name of the dish at the top of the page.
2. Put the text "Yield:  24 Servings" into a `<p>` element.
3. Make the text "Ingredients" and "Directions" level 2 headers.
4. Put the ingredients into an **unordered** list.  Give this list a **class** attribute of "ingredients".
5. Put the directions into an **ordered** list.
6. Make the URL on the bottom of the page a hypertext link.
7. Wrap the updated URL in a `<footer>` element. It should look like this:

    ```
    <footer>
        <a href = "http://...">source: http://...</a>
    </footer>
    ```
Note:  replace the "..." with the rest of the URL.

8. Right after the `<h1>` element, add an `<img>` tag that displays the image file provided.  Set the **src**, **alt**, and **title** attributes to the appropriate values.
9. Add a link at the bottom of the page (after the source link) that goes to your home page (the index.html page you posted the last time).  Wrap this link in a `<p>` tag.
10. Preview the page.  It should look like the image below.
    [image goes here]
11. Test this page with the validator.  Do not continue until the page passes validation.
	
### Part 3:  Improving the Presentation with CSS
Now, we’ll apply CSS to improve the overall presentation of the recipe.
1. Now, let’s add some document-level styles into our kadayif.html page.  Inside the `<head>` tag of the page (below the `<meta>` tag) add the following **style** tag:

    ```
    <style type=”text/css”>

    </style>
    ```
    
2. Inside of the `<style>` tag you just created, we will add a rule that will change the font for all of the text in the document.  Add the following style rule between the `<style>` tags:

    ```
    body {
        font-family: “trebuchet ms”, tahoma, verdana;
    }
    ```
    
Reload the page to make sure a change happened.

3. Now, add the following declarations to the **body** selector you just created:

    ```
    margin-left: 10%;
    margin-right: 10%;
    border: 1px solid gray;
    ```
    
Test this!  You should now see a border around the text.

4. Did you notice that the text is too close to the border?  Let’s fix that.  Add the following to the body selector:

    ```
    padding-left: 1em;
	padding-right: 1em;
    ```
    
Test it!  There should be more room now.  Notice how the **margin** declarations affect the *outside* of the **body** tag while the **padding** declarations affect the *inside* of the body tag.  These properties work the same way with any of the other container elements (i.e., `<p>`, `<ol>`, `<em>`, etc.)

5. For fun, see if you can change the `<h1>` tag’s background to a light gray.  If you don’t know how to set background colors in CSS, search for it on-line.
6. Now, adjust the padding properties (padding-bottom, padding-top, etc.) of your **h1** rule so the text fits into its "box" a little better.
7. Add the declarations necessary to center the `<h1>` tags text using the **text-align** property.
8. ***Stop!***  Validate your page.  Do not continue until your page validates correctly.
9. Now, try validating the CSS you have used in your page.  You can find the CSS validator at:
http://jigsaw.w3.org/css-validator
10. Preview your page.  It should look like the image below.
 
 
### Part 4:  Adding Even More Rules
Now, make the following changes:
1. The items in your lists are tightly "scrunched" together.  In the `<style>` tag, add a rule for the `<li>` tags that will put more space between each item.  Use the following reference and look under the headings **padding** or **margin** for more ideas:
http://www.w3schools.com/css/css_reference.asp
2. Add a gray (or any color other than white) background color to the list of ingredients.  You can use the **ingredients** class selector to accomplish this.  Check today’s slides if you don’t remember how to do this.
3. What happened?  The background of the `<ul class="ingredients">` entity now stretches to fill most of the page.  Fix this by using the **width** property in your style rule.  Set the width to about 250 pixels.  Then, set the **list-style-type** property to **circle**.  Finally, adjust the **padding** so the list looks a little better.
4. This page would look a lot better if we put the image over on the right side of the page opposite the ingredients list.  We can do this using the **float** property.  We’ll discuss **float** in our next lecture.  For now, just add the following style rule to your page:
	```img { float: right; clear: both;}```
5. Now, let’s change the “Yield: 24 servings” paragraph so it uses and *in-line* style (as opposed to the *embedded* styles we have been working with).  Move the HTML for this so that it is before the **img** tag, not after.  Then change the tag as follows:
	```<p style="float: right; font-weight: bold">Yield: 24 servings</p>```
6. Add a *class selector* rule named: **.important**.  Set this rule so that text will be rendered in *red, 10% larger* than the default font size, and with a *yellow* background.
7. Use the `<span>` tag to apply this class to the text "Place on lowest oven rack."
8. Now, use another `<span>` tag to apply the same class rule to the text "Cool" near the bottom of the instruction list.
9. Validate your HTML!
10. Your page should now look something like the image below.
 
Now, while this page probably won’t win any design awards, the "look" and accessibility of the content has radically improved!

### Part 5:  Put Your Stamp On It
1. Change the background color of the footer text at the bottom of the page to a light gray color using the **footer** selector.
2. Add **three additional** CSS properties to the page that we have not yet used.

### Part 6:  Validate Your Page
Use the online tools to make sure that your page is well-formed and passes HTML5 validation at http://validator.w3.org 

Also validate the CSS! The CSS validator is extremely helpful in debugging wonky CSS:
http://jigsaw.w3.org/css-validator/

*** ONCE YOU ARE DONE, UPLOAD THIS TO YOUR 230 EXERCISES FOLDER ON BANJO, AND LINK TO IT FROM YOUR MAIN PAGE. ***
