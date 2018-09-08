# ICE: Basic HTML, CSS, and Validation 

## I. Overview & Goals

In this week's exercise, we will be taking a text document, marking it up as an HTML document, adding CSS formatting, and uploading it to your RIT web space. 

## II. Setting Up Your Folders and Files

On your local drive, (ideally in a previously created **230** folder), create a folder called **exercises**, and within it, create a folder called **recipe**.

We have uploaded a file called [kadayif.txt](cremebrulee.txt) to Github. When you click the link to view that file on Github, you'll see that it's a plain text file into which I've copied and pasted the content from the [Wikipedia entry for "Crème brûlée"](https://en.wikipedia.org/wiki/Cr%C3%A8me_br%C3%BBl%C3%A9e). 

To download that text file to your computer for editing, right-click on the button in the top right corner of the file that says "Raw," choose "Save link as...", and save the file to the week1 folder you just created.

You're also going to need to download the two images: [2014_0531_Crème_brûlée_Doi_Mae_Salong.jpg](2014_0531_Crème_brûlée_Doi_Mae_Salong.jpg) and [225px-Crema_Catalana_El_Glop.jpg](225px-Crema_Catalana_El_Glop.jpg). For each of those files, you will see a Download button in the top right corner. Right-click that button, choose "Save link as...", and download it to your local week1 folder. Then repeat that process with the second image. 

## III. Marking Up a Text File

Open the cremebrulee.txt file in your text editor of choice (I recommend Brackets, though Visual Studio Code has some cool features we'll reference below). It currently has no HTML markup at all--you're going to turn it into a proper HTML document, and add some simple CSS rules to make it look a bit more like the original Wikipedia entry. 

Use File->Save As... to save a new copy of the file called cremebrulee.html. Make sure you save it to the ICE2A folder and give it an .html extension--it's the extension that tells your editor to enable its HTML support. 

There are a lot of accented and foreign characters in this document. In HTML 4, the default character encoding for files was ISO-8859-1, which doesn't properly display special characters (like smart quotes and diacritical marks). Those characters had to be escaped out (e.g. &eacute; had to be represented as `&eacute;`, &copy; had to be represented as `&copy;`, and & had to be represented as `&amp;`)--if you didn't do that, they didn't display properly in the browser. HTML 5 uses UTF-8 encoding, which allows those special characters to appear properly in your document.

Because this Wikipedia article has many non-standard characters (like "smart" quotes and diacritical marks), the UTF-8 encoding is very helpful. 

First, set up your document with the standard HTML5 "skeleton":

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="utf-8" />
	<title></title>
</head>
<body>

</body>
</html>
```

Now we need to mark the text up as HTML. (Use the actual wikipedia page as a refrerence.)

- Add an h1 heading for the page title, and h2 headings for all of the subsections.
- Add paragraph tags to the individual paragraphs of text. 
- Make the Contents and References sections into numbered ("ordered") lists, and the See Also, Bibliography, and External Links sections into bulleted ("unordered") lists. (Hint: Emmet can be very helpful with this, too!)
- Add the two images where indicated in the file, with appropriate alt text. Don't worry about positioning them for now; we'll deal with that when we add the CSS. 
- Use the `<sup>` tag to make each of the footnote references a superscript.
- Where appropriate, add tags to make text bold (`<strong>...</strong>`) and/or italicized (`<em>...</em>`).

Don't worry about adding links yet; we'll be doing that next week. 

When you're done, preview your document in your editor or browser. It should look something like this: ![Creme Brulee Page Without CSS](images/cremebrulee1.png)

## IV. Publishing Your Files
 
Once you're satisfied with the HTML file, you're going to upload your exercises folder (which includes your ICE3A folder and its contents) to your 230 folder on Banjo. 

Test it by going to `http://people.rit.edu/yourid/230/exercises/ICE3A` -- you should see the .txt and .html files, and the two images. Click on the html file and make sure it displays properly. If you run into problems here, **ask for help ASAP**. 

## V. Adding Basic CSS Formatting
Now we're going to use CSS to start to make the page look a bit more like the original Wikipedia entry.

Create a new file in the ICE3A folder called cremebrulee.css. Add a link to the stylesheet in your <head> by typing `<link rel="stylesheet" type="text/css" href="cremebrulee.css" />`. 

For today, since you've already done quite a bit of work, I'm going to give you the CSS to start with. Paste the following style rules into your cremebrulee.css file:

```css
body {
    font-family: 'Helvetica Neue', Helvetica, Arial,sans-serif;
    line-height: 1.4;
    padding-left: 20px;
}

a { text-decoration: none; }

h1, h2 {
    font-family: 'Linux Libertine', Georgia, Times, 'Times New Roman', serif;
    line-height: 1.3;
    margin-bottom: 0.25em;
    padding: 0;
    border-bottom: 1px solid #a2a9b1;
    font-weight: normal;
    }

h1 {
    font-size: xx-large;
}
```
Save the changes your HTML and CSS files, and upload them to your ICE3A directory. Your cremebrulee.html file should now look more like this: ![Creme Brulee Page With CSS](images/cremebrulee2.png)

You're done!







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
![Unformatted Text](images/recipe-1.jpg)
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
![Structured Content](images/recipe-2.jpg)
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
![Code with Presentation](images/recipe-2.jpg)
 
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
![Better Presentation](images/recipe-4.jpg)
Now, while this page probably won’t win any design awards, the "look" and accessibility of the content has radically improved!

### Part 5:  Put Your Stamp On It
1. Change the background color of the footer text at the bottom of the page to a light gray color using the **footer** selector.
2. Add **three additional** CSS properties to the page that we have not yet used.

### Part 6:  Validate Your Page
  Use the online tools to make sure that your page is well-formed and passes HTML5 validation at http://validator.w3.org 

  Also validate the CSS! The CSS validator is extremely helpful in debugging wonky CSS:
http://jigsaw.w3.org/css-validator/

## VI. Submission
See the mycourses dropbox for submission instructions.

***ONCE YOU ARE DONE, UPLOAD THIS TO YOUR 230 EXERCISES FOLDER ON BANJO, AND LINK TO IT FROM YOUR MAIN PAGE.***
