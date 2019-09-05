# Saving banjo.rit.edu from itself
## I. Overview
`banjo.rit.edu` is the new RIT web server for http://people.rit.edu

While this new web server solves a lot of problems we had with the old `gibson.rit.edu`, it also creates a host of new ones. 
Most of these new issues are because Banjo has enabled the [Google PageSpeed Module](https://www.modpagespeed.com) to help pages load significantly faster and more consistently. 

+ https://moz.com/blog/use-googles-pagespeed-module-to-dramatically-increase-the-speed-of-your-website

Unfortunately, there are undesirable byproducts for creaters of web pages that are under active development: it makes HTML/CSS/JavaScript debugging more difficult, and HTML validation impossible. So, we basically need to "turn it off" for all of our 230 web development this semester.

### An example of PageSpeed module causing trouble!
**A) Here's some CSS and JavaScript we've created for a simple game. Note how the &lt;style&gt; and &lt;script&gt; tags are nicely indented and easy to read.**

![Code listing](images/banjo-code-listing.jpg)


**B) When we upload it to Banjo, and view it in the Inspector, you can see how the white space has been stripped out of the contents of the &lt;style&gt; and &lt;script&gt; tags, and the code is harder to read and debug.**

![Compressed code listing](images/banjo-code-listing-server-compressed.jpg)


**C) If we look in the Inspector again, under the Network tab, we can actually see that the Banjo server is utilizing an HTTP header (`X-Mod-Pagespeed`) to let the web browser know "Hey, I'm using the PageSpeed module!"**

![HTTP Headers](images/banjo-modpagespeed-headers.jpg)


***In this instance, the browser doesn't seem to be much anything about it that we know of. But because HTTP headers are human readable, it's easy for us as web developers to see why our CSS and JS is getting compressed. Move on to the next part to turn off the PageSpeed module!***

***One thing the server is doing here is stripping out all of the white space in the document - make a note of your file size - which is the `Content-Length` header in the response headers) before you move on***

## II. .htaccess files to the rescue!

.htaccess files allow you to make web server configuration changes on a per-folder basis. 

We have given you a text file named "htaccess" (inside of the [FixingBanjo.zip](FixingBanjo.zip) file) that contains a single line of text:

`ModPagespeed off`

This unsurprisingly tells the web server to disable the PageSpeed module for the directory that contains the file, and all of its sub-directories.

Note: htaccess files are *plain text* files - just like HTML, CSS or JS files - make sure they DO NOT have any kind of file extension when you create them (example `.txt`, `.html` etc).

## III. Instructions:
1. Using your SFTP client of choice, upload this file to the `www` folder on your banjo.rit.edu account.
2. Then, on Banjo, change its filename from htaccess to .htaccess (just add a "." to the front of the name). Make sure you set the permissions on this file to 644. 
3. Now you should be all good! Check the response headers and the file size (the `Content-Length` header) to be sure that PageSpeed is turned off.
4. **Important:** If you already have a .htaccess file in the www folder, don't replace it with the one we gave you. Instead, just add `ModPagespeed off` to the end of it.

**Note:** The reason we don't use the "." before uploading the file is that on Unix-based systems, like the Mac, any file starting with a "." is considered a system file and *hidden* - i.e., invisible, and difficult for us to find in order to upload to the server.

## IV. Discussion:
*If you did everything correctly, you have disabled the PageSpeed module for your www folder and all of its sub-directories.*

*If you check the Inspector's Network tab again you should see that Banjo is no longer sending the `X-Mod-Pagespeed` header, which means that Banjo is no longer compressing the CSS & JS before sending the page to the web browser.*

*So what do .htaccess files DO? They simply let us "script" the behavior of the web server on a per-folder basis.*


## V. One more thing: HTTPS versus HTTP
One more thing to watch for on banjo - external scripts must be downloaded *securely* via **https** rather than by *insecure* **http**.

Example - this will fail on banjo:

`<script src="http://code.jquery.com/jquery-2.2.0.min.js"></script>`

Your code will fail and you will see this error in the browser console:

`The page was not allowed to run insecure content from http://code.jquery.com/
jquery-2.2.0.min.js.`

If you change the 'src' value to the following (utilizing `https` instead of `http`), the jQuery will now successfully load:

`<script src="https://code.jquery.com/jquery-2.2.0.min.js"></script>`

## VI. One last thing: Using PuTTY or Terminal to ssh to 'banjo.rit.edu`

If you remember your basic Unix commands from IGME-110, then creating and maintaining .htaccess files directly on the server is **a lot easier** than editing text files locally and using FTP to transfer them to banjo.

1. Fire up your preferred console app

2. Connect to banjo
```
ssh abc1234@banjo.rit.edu
```

3. "Change directory" to your `www` folder
```
cd www
```

4. Open up (or create) your .htaccess file in the nano text editor (or another editor if your prefer):
```
nano .htaccess
```

5. Make your changes, and then save the file (control-o) and exit (control-x)

```
ModPagespeed off
```
