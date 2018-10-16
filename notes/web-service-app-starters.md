# Web Service App - Examples & Starters 

- Below is fully functional web service "starter" code for several APIs
- These were working as of 10/15/2018
- For most of these, you will need to apply for your own API key

## Contents
<!--- Local Navigation --->
I. [GIPHY API](#giphy)

II. [Dog API](#random-dog)

III. [Anime Schedule Finder API](#anime-schedule-finder)

<hr><hr>

<a id="giphy"></a>
## I. GIPHY API

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

**Screenshot:**

![screenshot](_images/web-service-starter-giphy.jpg)

<hr>

<a id="random-dog"></a>
## II. Dog API

- The Dog API docs can be found here: https://dog.ceo/dog-api/documentation/
- This API does not currently require an API key
- This API has multiple endpoints. The one we are using here just returns a single picture of a random dog. 
- If you are going to use this API with a project, you will need to use a different endpoint because this one doesn't do very much
- Suggestions:
  - You can use the "By Breed" endpoint which returns an array of images. You will use this in conjunction with a pulldown that has a list of all of the available breeds.

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="utf-8" />
 	<title>Dog Finder</title>
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
		const SERVICE_URL = "https://dog.ceo/api/breeds/image/random";
		
		// No API Key required!
		
		// 2 - build up our URL string
		// not necessary for this service endpoint
		let url = SERVICE_URL;
		
		// 3 - parse the user entered term we wish to search
		// not necessary for this service endpoint
		
		// 4 - update the UI
		document.querySelector("#debug").innerHTML = `<b>Querying web service with:</b> <a href="${url}" target="_blank">${url}</a>`;
		
		// 5- call the web service, and prepare to download the file
		$.ajax({
		  dataType: "json",
		  url: url,
		  data: null,
		  success: jsonLoaded
		});
		
		
	}
	
	
	function jsonLoaded(obj){
		// 6 - if there are no results, print a message and return
		// Here, we don't get an array back, but instead a single object literal with 2 properties
		
		if(obj.status != "success"){
			document.querySelector("#content").innerHTML = "<p><i>There was a problem!</p>";
			return; // Bail out
		}
		
		// 7 - if there is an array of results, loop through them
		let results = obj.data
		let bigString = "<p><i>Here is the result!</p>";
		let src = obj.message;
		
		bigString += `<img src="${src}" alt="random dog" />`
		
		// 8 - display final results to user
		document.querySelector("#content").innerHTML = bigString;
	}	
	
  </script>

</head>
<body>
<header>
 <h1>Dog Finder</h1>
</header>

<p>Search Term -&gt; <input id="searchterm" type="text" size="20" maxlength="20" autofocus value="not used" /></p>
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

**Screenshot:**

![screenshot](_images/web-service-starter-dogs.jpg)

<hr>




<a id="anime-schedule-finder"></a>
## III. Anime Schedule Finder API
- The *Jikan Unofficial MyAnimeList API* docs can be found here: https://jikan.docs.apiary.io/
- This API does not currently require an API key
- This API has a lot of endpoints!
- PS: making the user type in the day of the week is horrible, awful usability. If you end up using this endpoint, be sure to have the days of the week pre-populated in a pulldown!

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="utf-8" />
 	<title>Anime Schedule Finder</title>
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
	
	let term = ""; // we declared `term` out here because we will need it later
	function getData(){
		// 1 - main entry point to web service
		const SERVICE_URL = "https://api.jikan.moe/v3/schedule/";
		
		// No API Key required!
		
		// 2 - build up our URL string
		let url = SERVICE_URL;
		
		// 3 - parse the user entered term we wish to search
		term = document.querySelector("#searchterm").value;
		
		// get rid of any leading and trailing spaces
		term = term.trim();
		// encode spaces and special characters
		term = encodeURIComponent(term);
		
		// if there's no term to search then bail out of the function (return does this)
		if(term.length < 1){
			document.querySelector("#debug").innerHTML = "<b>Enter a search term first!</b>";
			return;
		}
		url += term;
		
		// 4 - update the UI
		document.querySelector("#debug").innerHTML = `<b>Querying web service with:</b> <a href="${url}" target="_blank">${url}</a>`;
		
		// 5- call the web service, and prepare to download the file
		$.ajax({
		  dataType: "json",
		  url: url,
		  data: null,
		  success: jsonLoaded
		});
		
		
	}
	
	
	function jsonLoaded(obj){
		// 6 - if there are no results, print a message and return
		if(obj.error){
			let msg = obj.error;
			document.querySelector("#content").innerHTML = `<p><i>Problem! <b>${msg}</b></p>`;
			return; // Bail out
		}
		
		// 7 - if there is an array of results, loop through them
		// this is a weird API, the name of the key is the day of the week you asked for
		let results = obj[term];
		if(!results){
			document.querySelector("#content").innerHTML = `<p><i>Problem! <b>No results for "${term}"</b></p>`;
			return;
		}
		
		
		let bigString = `<p><i>Here are <b>${results.length}</b> results!</i></p>`; // ES6 String Templating
		
		for (let i=0;i<results.length;i++){
			let result = results[i];
			let url = result.url;
			let title = result.title;
			var line = `<p class='result'><a href='${url}'>${title}</a></p>`;
			bigString += line;
		}
		
		// 8 - display final results to user
		document.querySelector("#content").innerHTML = bigString;
	}	
	
  </script>

</head>
<body>
<header>
 <h1>Anime Schedule Finder</h1>
</header>

<p>Search Term (enter a day of the week) -&gt; <input id="searchterm" type="text" size="20" maxlength="20" autofocus value="monday" /></p>
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

**Screenshot:**

![screenshot](_images/web-service-starter-anime-schedule.jpg)

<hr>


