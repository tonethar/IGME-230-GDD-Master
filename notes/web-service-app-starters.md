# Web Service App Starters

- Below is fully functional web service "starter" code for several APIs
- These were working as of 10/15/2018
- For most of these, you will need to apply for your own API key

## Contents
<!--- Local Navigation --->
I. [GIPHY API](#giphy)

II. [Dog API](#dog)



## I. GIPHY API <a id="giphy"></a>

- The GIPHY API docs can be found here: https://developers.giphy.com/docs/

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="utf-8" />
 	<title>GIF Finder</title>
 	<style>
	/* We have no style! */
 	</style>
	<!-- Import jQuery -->
  <script src="http://ajax.googleapis.com/ajax/libs/jquery/1.10.2/jquery.min.js"></script>
  <script>
  
	window.onload = init;
	
	function init(){
		document.querySelector("#search").onclick = getData;
	}
	
	function getData(){
		// 1 - main entry point to web service
		const SERVICE_URL = "https://api.giphy.com/v1/gifs/search?";
		
		// Public API key from here: https://developers.giphy.com/docs/
    const API_KEY = "dc6zaTOxFJmzC";  // if this doesn't work, get your own key, it's free!
		
		// 2 - build up our URL string
		let url = SERVICE_URL;
		url += "api_key=" + API_KEY;
		
		// 3 - parse the user entered term we wish to search
		let term = document.querySelector("#searchterm").value;
		
		// get rid of any leading and trailing spaces
		term = term.trim();
		// encode spaces and special characters
		term = encodeURIComponent(term);
		
		// if there's no term to search then bail out of the function (return does this)
		if(term.length < 1){
			document.querySelector("#debug").innerHTML = "<b>Enter a search term first!</b>";
			return;
		}
		url += "&q=" + term;
		
		// 4 - update the UI
		document.querySelector("#debug").innerHTML = `<b>Querying web service with:</b> <a href="${url}" target="_blank">${url}</a>`;
		
		// 5 - call the web service, and prepare to download the file
		$.ajax({
		  dataType: "json",
		  url: url,
		  data: null,
		  success: jsonLoaded
		});
		
		
	}
	
	
	function jsonLoaded(obj){
		// 6 - if there are no results, print a message and return
		if(!obj.data || obj.data.length == 0){
			document.querySelector("#content").innerHTML = "<p><i>No results found!</p>";
			return; // Bail out
		}
		
		// 7 - if there is an array of results, loop through them
		let results = obj.data
		let bigString = `<p><i>Here are <b>${results.length}</b> results!</p>`; // ES6 String Templating
		
		for (let i=0;i<results.length;i++){
			let result = results[i];
			let url = result.url;
			let smallURL = result.images.fixed_width_small.url;
			if (!smallURL) smallURL = "images/no-image-found.png";
			var line = `<div class='result'><img src='${smallURL}' title= '${result.id}' />`;
      			line += `<span><a target='_blank' href='${url}'>View on Giphy</a></span></div>`;
			bigString += line;
		}
		
		// 8 - display final results to user
		document.querySelector("#content").innerHTML = bigString;
	}	
	
  </script>

</head>
<body>
  <header>
    <h1>GIF Finder</h1>
  </header>

  <p>Search Term -&gt; <input id="searchterm" type="text" size="20" maxlength="20" autofocus value="cats" /></p>
  <p><button type="button" id="search" class="green">Search!</button></p>
  <p id="debug"></p>
  <hr>
  <h2>Results</h2>
  <div id="content">
    <p>No data yet!</p>
  </div>
</body>
</html>
```

<hr>

## II. Dog API <a id="dog"></a>

- The Dog API docs can be found here: https://dog.ceo/dog-api/documentation/

```html

```

<hr>
