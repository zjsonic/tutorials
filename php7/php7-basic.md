# PHP7 Basic

## What is PHP
- php stans for hyptertext preprocessor
- php is a script language
- php are excuted on server and return html to browser
- php can generate dynamic page content
- php can curd、open and close files on server
- php can curd data in your database
- php can collect form data
- php can send and receive cookies

## web host with PHP7 support
- install a web server
- install php
- install a database, such as MySQL

## PHP7 syntax
- php script can be placed anywhere in the document
- php script starts with `<?php` and ends with `?>`
- php statement ends with a semicolon (;)
- php supports 3 ways of commenting
  - `//`
  - `#`
  - `/*  */`
- php is case-sensitive

## php variable
- php variable starts with a `$` sign
- 函数外部定义的variable只能在函数外部访问
- 函数内部定义的variable只能在函数内部访问
- `echo` statement is often used to output to the screen.
```
<!DOCTYPE html>
<html>
  <head>Test php</head>

  <body>
  	<?php
    	$name = 'zhangsan';
    	echo "My name is $name!";
      echo "My name is" . $name . "!";
    ?>
  </body>
</html>
```
