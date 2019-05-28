# Array in PHP7

## What is an Array?

- Stores multiple values in one variable.
- A special variable,holds more than one value at a time.

## Create an Array in PHP

In php, `array()` function is used to create an array.

```php
array()
```

## Indexed Array
Array with a numeric index
There are two ways to create indexed array.

### The index can be assigned automatically

```php
$cars = array('volvo','BMW','toyota');
```

### The index can be assigned manually

```php
$cars[0] = 'volvo';
$cars[1] = 'BMW';
$cars[2] = 'toyota';
```

## Associative Array

Array with named keys.
There are two ways to create associative array

```php
$age = array('Peter'=>'35','Ben'=>'37','Joe'=>'43');
```

or

```php
$age['Peter'] = '35';
$age['Ben'] = '37';
$age['Joe'] = '43';
```
