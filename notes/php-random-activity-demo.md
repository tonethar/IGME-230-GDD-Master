# Random Activity - Utilizing a Web Service with PHP

## I. Overview
- Later on in the course we will learn about using JavaScript to download web services - [Web Apps - 10](notes/web-apps-10.md)
- Today we'll give you a brief preview of how to download and parse a web service using PHP. The web service we will use is a simple one called the [Bored API](https://www.boredapi.com) - this API returns a random activity (in **JSON** format) every time it is called 
- This is what we will be building:

![Image](_images/random-activity-1.jpg)

- Clicking the button causes the PHP page to reload, and the PHP script to request another activity from the web service


## II. Get Started

Here's the starter code:

**random-activity.php**

```php
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="utf-8" />
	<title>Random Activity!</title>
	<style>
		body{
			font-family: sans-serif;
			background-color: lightblue;
		}
		p{
			color: red;
			font-size: 2em;
			font-style: italic;
		}
		input[type="submit"]{
			font-size:20pt;
			border:1px groove gray;
			margin-top:1.5em;
			display:block;
		}
	</style>
</head>
<body>
   <h1>Something you could do if you are bored ...</h1>

   <!-- PHP will start here -->

   <!-- PHP will end here -->
	
   <form action="random-activity.php" method="post">
      <input type="submit" value="Get another Activity!">
   </form>
</body>
</html>
```



