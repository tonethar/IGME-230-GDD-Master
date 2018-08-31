# Using PHP to detect the HTTP *User-Agent string*

## I. Overview
- In software development, a **user agent** is software that acts on behalf of a user. In the HTTP protocol, a user agent is a client application that submits HTTP requests. Examples of HTTP clients include web browsers, 'bots such as search engine web crawlers, and apps that consume HTTP services (weather, stock quotes, etc)
- In HTTP, the client sents a **user-agent string** that contains a list of keywords and comments that are designed to communicate the client's capabilities to the server. For example, the User-Agent string might be used by a web server to filter web assets based on the known capabilities of a particular version of client software. ex. A "flip phone" would not receive a web site's images and CSS style sheets.

## II. Examples of User-Agent strings
- The user-agent string includes:
  - the application type
  - operating system
  - software vendor or software version
- In HTTP, this information is sent by the client as a HTTP *request header*
- Here are some sample user agent strings:

**Chrome on Mac OS:**
`Mozilla/5.0 (Macintosh; Intel Mac OS X 10_13_6) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/68.0.3440.106 Safari/537.36`

**Firefox on Android Mobile:**
`Mozilla/5.0 (Android; Mobile; rv:14.0) Gecko/14.0 Firefox/14.0`

**iPhone:**
`Mozilla/5.0 (iPhone; CPU iPhone OS 8_0_2 like Mac OS X) AppleWebKit/600.1.4 (KHTML, like Gecko) Version/8.0 Mobile/12A366 Safari/600.1.4`

**GoogleBot:**
`Googlebot/2.1 (+http://www.googlebot.com/bot.html)`

**Amazon Kindle 3:**
`Mozilla/5.0 (Linux; U; en-US) AppleWebKit/528.5+ (KHTML, like Gecko, Safari/528.5+) Version/4.0 Kindle/3.0 (screen 600x800; rotate)`
  
**Pantech Feature Phone:**
`PantechP7040/JLUS04042011; Mozilla/5.0 (Profile/MIDP-2.0 Configuration/CLDC-1.1; Opera Mini/att/4.2.16479; U; en-US) Opera 9.50`

## III. What's my user-agent string?

- point your browser here to see: https://www.esolutions.se/whatsmyinfo
- or post this PHP script to your people.rit.edu account:

**user-agent.php**
```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="utf-8" />
	<title></title>
</head>
<body>
<?php echo $html; ?>
  <?php 
    $useragent = $_SERVER['HTTP_USER_AGENT'];
    echo "<p>Your browser's user agent string is $useragent</p>"; 
  ?>
</body>
</html>
```



## IV. Reference
- https://en.wikipedia.org/wiki/User_agent
- https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol
- https://en.wikipedia.org/wiki/List_of_HTTP_header_fields
- https://www.w3.org/Protocols/HTTP/HTRQ_Headers.html#user-agent
