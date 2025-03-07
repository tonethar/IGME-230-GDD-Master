# 2 - PHP Scalars & Data Types

## Contents
<!--- Local Navigation --->
I. [PHP Types](#section1)

II. [PHP Variables](#section2)

III. [Integers & Floats](#section3)

IV. [Booleans](#section4)

V. [Strings](#section5)

VI. [Type Coercion](#section6)

VII. [Constants](#section7)

VIII. [Operators](#section8)

IX. [Web Server Caching](#section9)

X. [Review Questions](#section10)

XI. [Review Exercise](#section11)

<hr><hr>

## I. <a id="section1">PHP Types
- In PHP, values have an associated *type*, but variables do not
- PHP has 4 *scalar* (i.e. "primitive") types: [integer](https://www.php.net/manual/en/language.types.integer.php), [float](https://www.php.net/manual/en/language.types.float.php) (aka double), [string](https://www.php.net/manual/en/language.types.string.php) and [boolean](https://www.php.net/manual/en/language.types.boolean.php)
- PHP has 2 *composite* types: [array](https://www.php.net/manual/en/language.types.array.php) and [object](https://www.php.net/manual/en/language.types.object.php)
- PHP has 2 *special* types: [resource](https://www.php.net/manual/en/language.types.resource.php) and [null](https://www.php.net/manual/en/language.types.null.php) (resource is an [opaque data type](https://en.wikipedia.org/wiki/Opaque_data_type))

## II. <a id="section2">PHP Variables
- variables in PHP are denoted with a leading dollar sign `$`
- variable names must begin with a letter or underscore character
- variables can, but do not need, to be declared before assignment
- variables do not have intrinsic *types* - a variable does not know in advance whether it will be used to store a number or a string or something else
- PHP does a good job of automatically converting types from one to another when necessary

## III. <a id="section3">Integers & Floats
Run the following code and observe the results:
  
**php-types-1.php**
```php
<?PHP
	// sum integers
	$a = 1;
	$b = 2;
	$c = $a + $b;
	$isInteger = is_int($c);
	echo "<p>The sum of integers $a and $b is $c. isInteger = $isInteger</p>";
	
	// explicit casting of $c to an int
	$a = 1;
	$b = 2.99;
	$c = $a + (int)$b;
	$isInteger = is_int($c);
	echo "<p>The sum of integers $a and $b is $c. isInteger = $isInteger</p>";
	
	// sum floats
	$a = 1.0;
	$b = 2.0;
	$c = $a + $b;
	$isFloat = is_float($c);
	echo "<p>The sum of floats $a and $b is $c. isFloat = $isFloat</p>";
	
	$a = 1.0;
	$b = 2.99;
	$c = $a + $b;
	$isFloat = is_float($c);
	echo "<p>The sum of floats $a and $b is $c. isFloat = $isFloat</p>";
?>
```
  
## IV. <a id="section4">Booleans
PHP has several values that are automatically coerced to `FALSE` in a boolen content, all other values are coerced to `TRUE`.  Run the following code and observe the results:

**php-types-2.php**
```php
<?PHP
  $phpIsWeird = TRUE;
  if ($phpIsWeird){
  	echo("<p>PHP is REALLY weird!</p>");
	}else{
   	echo("<p>PHP is NOT weird!</p>");
  }
  
  $ritIsWeird = 0; // 0 and 0.0 are false, all other numbers coerce to TRUE
  if ($ritIsWeird){
  	echo("<p>RIT is REALLY weird!</p>");
	}else{
   	echo("<p>RIT is NOT weird!</p>");
  }
  
  $rochesterIsWeird = ""; // empty strings "" and '' are FALSE
  if ($rochesterIsWeird){
  	echo("<p>Rochester is REALLY weird!</p>");
	}else{
   	echo("<p>Rochester is NOT weird!</p>");
  }
  
  $gccisIsWeird = []; // empty array is FALSE
  if ($gccisIsWeird){
  	echo("<p>GCCIS is REALLY weird!</p>");
	}else{
   	echo("<p>GCCIS is NOT weird!</p>");
  }
  
  $thisDemoIsDone = "XYZPDQ"; // most everything else is TRUE
  if ($thisDemoIsDone){
  	echo("<p>This demo is DONE!</p>");
	}else{
   	echo("<p>This demo is NOT DONE!</p>");
  }
?>
```


More here: https://stackoverflow.com/questions/2382490/how-does-true-false-work-in-php
  
## V. <a id="section5">Strings
Run the following code and observe the results:

**php-types-3.php**
```php
<?PHP
  // string values may be single or double quoted
  $name = 'Fred';
  $name = "Fred";
   
  // strings may be concatenated with a dot (period)
  $greeting1 = "<p>My name is " . $name . "</p>";
   
  // string variables WILL be interpolated in a double-quoted string
  $greeting2 = "<p>My name is $name</p>";
   
  // string variables WILL NOT interpolate in a single-quoted string
  $greeting3 = '<p>My name is $name</p>';
  
  echo($greeting1); // My name is Fred
  echo($greeting2); // My name is Fred
  echo($greeting3); // My name is $name
?>
```

## VI. <a id="section6">Type Coercion
PHP does not require (or support) explicit type definition in variable declaration; a variable's type is determined by the context in which the variable is used. That is to say, if a string value is assigned to variable `$var`, `$var` becomes a string. If an integer value is then assigned to `$var`, it becomes an integer.
  
 **The code below works as expected in PHP 5, but the automatic string conversion in the 4th and 5th line below produces warnings in PHP 7:**
 
  **php-types-4.php**
 ```php
 <?php
	// In PHP 5, these run as follows
	$foo = "1";  				// $foo is string (ASCII 49)
	$foo *= 2;   				// $foo is now an integer (2)
	$foo = $foo * 1.3;  // $foo is now a float (2.6)
	$foo = 5 * "10 Little Piggies"; 	// $foo is integer (50) *
	$foo = 5 * "Small Pigs = 10";     	// $foo is integer (0)	**
	echo $foo;
	

// * In PHP 7, this currently gives an error: "A non well formed numeric value encountered"
	
// ** In PHP 7, this currently gives an error: "A non-numeric value encountered"	
?>
```

**The solution - PHP 7, you will need to *explicitly cast* the strings to integers with `(int)` to avoid the errors:**
 
**php-types-5.php**
 ```php
 <?php
	// In PHP 7, get rid of the errors by casting
	$foo = "1";  		// $foo is string (ASCII 49)
	$foo *= 2;   		// $foo is now an integer (2)
	$foo = $foo * 1.3;  	// $foo is now a float (2.6)
	$foo = 5 * (int)"10 Little Piggies";  	// 50 because this string is converted to 10
	echo "<p>The first result is $foo</p>"; 
	$foo = 5 * (int)"Small Pigs = 10";  	// 0 because this string is converted to 0
	echo "<p>The second result is $foo</p>";
?>
```



Read more here: http://php.net/manual/en/language.types.type-juggling.php 

## VII. <a id="section7">Constants
	
Constant values can be created via the [`define()`](http://php.net/manual/en/function.define.php) function, and are then accessed without using the `$` in the name of the constant.
  
 **php-types-6.php**
 ```php
<?PHP
 	define("PI", 3.14159);
 	$radius = 10;
 	$area = PI * $radius * $radius;
	echo "<p>The area of a radius $radius circle is $area</p>";
?>
 ```
 
 PHP also has a number of pre-defined "magic constants": http://php.net/manual/en/language.constants.predefined.php
 
 ## VIII. <a id="section8">Operators
	
PHP has all of the standard arithmetic, comparison, logical, assignment and conditional operators that you know and love - take a look here: https://www.tutorialspoint.com/php/php_operator_types.htm

 ## IX. <a id="section9">Web Server Caching
*In computing, a cache is a hardware or software component that stores data so future requests for that data can be served faster; the data stored in a cache might be the result of an earlier computation, or the duplicate of data stored elsewhere.* - https://en.wikipedia.org/wiki/Cache_(computing)

PHP on banjo has an annoying habit of caching the results of your PHP pages for up to 24 hours!, which is nice for performance, but makes it harder to develop and debug PHP pages. You will want to turn off this behavior, so add the following to a `.htaccess` file that is located either in your `www` folder or your `230` folder (recall that .htaccess file directives effect the current directory, and all of its sub-directories):

```
<IfModule mod_expires.c>
        ExpiresActive On
        ExpiresDefault "now"
</IfModule>
Header set Cache-Control "max-age=0, private, no-cache, no-store, must-revalidate"
ModPagespeed off
```

Here is the documentation for these directives:
- http://httpd.apache.org/docs/current/mod/mod_expires.html
- https://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.9
- https://www.modpagespeed.com/doc/configuration

**The above directives are turning off ALL caching, both the client (web browser) and the server.**

 ## X. <a id="section10">Review Questions
1. Give 2 ways to *concatenate* strings in PHP.
1. List the 4 PHP *scalar* types.
1. True or False. PHP variables are *strongly typed*, like Java, C#, and C++


 ## XI. <a id="section11">Review Exercise
1. Make a copy of *php-types-6.php*, name the copy **php-2-HW.php**, and modify it so that it also calculates the circumference of the circle, and echos that value out in another paragraph.

<hr><hr>





| <-- Previous Unit | Home | Next Unit -->
| --- | --- | --- 
|   **[Intro to PHP (chapter 1)](php-1.md)**  |  **[About this PHP Tutorial Series](php-0.md)** | **[PHP Arrays (chapter 3)](php-3.md)**
