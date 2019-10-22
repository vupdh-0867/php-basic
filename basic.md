# PHP BASIC

## List Contents
1. [Hello world](https://github.com/quangvv-1620/php-basic/blob/master/basic.md#1-hello-world)
2. [Basic syntax](https://github.com/quangvv-1620/php-basic/blob/master/basic.md#2-basic-syntax)
3. [Variables](https://github.com/quangvv-1620/php-basic/blob/master/basic.md#3-variables)
4. [Data types](https://github.com/quangvv-1620/php-basic/blob/master/basic.md#4-data-types)
5. [Functions](https://github.com/quangvv-1620/php-basic/blob/master/basic.md#5-functions)
6. [Operators](https://github.com/quangvv-1620/php-basic/blob/master/basic.md#6-operators)
7. [Array](https://github.com/quangvv-1620/php-basic/blob/master/basic.md#7-array)
8. [Conditions](https://github.com/quangvv-1620/php-basic/blob/master/basic.md#8-conditions)
9. [Loops](https://github.com/quangvv-1620/php-basic/blob/master/basic.md#9-loops)


## 1. Hello world
To learn php basic, the first thing a developer must to do that is building a script to talk with the world "Hello world".
So let to do that!

You create a new file with name `hello_world.php` in your path(my path is `Desktop/php-basic/`) folder and past code below to this file.

```php
<?php
  echo "Hello, World!";
?>
```

**Run file:** to run file php, you must open your terminal and run comanline `php path_file`, as my terminal is `php Desktop/php-basic/hello_world.php` and it will produce following result:

> Hello, World!

Well! That is so easy, right now!

If you don't want to run with file, you can using `php -a` as your terminal and pass your code in that to run.

![run by shell](./images/run_by_shell.png)

## 2. Basic syntax
### Escaping to PHP 
There are four ways to do `escaping to php`:

- **Canonical PHP tags:** The most way using for php tag

```
<?php ... ?>
```

- **Short-open (SGML-style) tags:**

```
<? ... ?>
```

But that is not as default syntax of php tags. To using short-open use must recognize the tags with two step following:
  - Choose the --enable-short-tags configuration option when you're building PHP.
  - Set the short_open_tag setting in your **php.ini** file to on. This option must be **disabled to parse XML** with PHP because the same syntax is used for XML tags

- **ASP-style tags:** To use ASP-style tags, you will need to set the configuration option in your php.ini file.

```
<% ... %>
```

- **HTML script tags:**

```
<script language="php">...</script>
```
### Commenting code
- **Single-line comments**

To comment one line in php you can using `#` or `//` syntaxs:

```php
<?php
  # This is a single comment
  // and this is a single comment too
  print "An example with single line comments";
?>
```

- **Multiple-line comments**

To comment multiple lines in php you can using `/**/` syntax:

```php
<?php
  /* This is a first line comment
  And this is a second line comment
  */

  print "An example with multi line comments";
?>
```

- **Multiple-line printing**

To print multiple lines in php you can using `<<<END ... END` syntax:

```php
<?php
  # First Example
print <<<END
This uses the "here document" syntax to output
multiple lines with $variable interpolation. Note
that the here document terminator must appear on a
line with just a semicolon no extra whitespace!
END;

# Second Example
print "This spans
multiple lines. The newlines will be
output as well";
?>
```

- **PHP is case sensitive**

```php
<?php
  $capital = 10;
  print("Variable capital is $capital<br>");
  print("Variable CaPiTal is $CaPiTal<br>");
?>
```
This will be get following result:

> Variable capital is 10\
> Variable CaPiTal is 

## 3. Variables
### Declare PHP variables

```php
<?php
  $x = 10;
  $txt = "Hello world!";
?>
```

### Some rules you must know when working with variable in php
- All variables in php are donated with a leading dollar sign `($)`
- PHP automate converting types from one to another when necessary
- A variable name must start with a letter or underscore character
- A variable name cannot start with a number
- Variable names are case-sensitive($age and $AGE is two difference variables)

### Variable scope

- Global variable
- Local variable
- Static variable

**Global variable**

A variable declare **outside** a function has a GLOBAL SCOPE and can only accessed outside a function

```php
<?php
  $x = 10; // global variable

  function display() {
    // using $x inside this function will be raise an error
    print "\$x inside the function is $x. \n";
  }

  display();
  print "\$x outside the function is $x. \n";
?>
```

So, how to do using a global variable inside a function, using *`global`* keyword

```php
<?php
  $x = 10; // global variable
  $y = 5; // global variable

  function display() {
    global $x, $y;
    $y += $x;
  }

  display();
  echo $y; // 15
?>
```

**Note:** PHP also stores all global variable in an array called `$GLOBALS[index]`. The `index` holds the name of the variable.


```php
<?php
  $x = 10; // global variable
  $y = 5; // global variable

  function display() {
    $GLOBALS['y'] += $GLOBALS['x'];
  }

  display();
  echo $y; // 15
?>
```

**Local variable**

A variable declared within a function has a LOCAL SCOPE and can only accessed within that function:

```php
<?php
  function display() {
    $x = 10; // local variable
    print "\$x inside the function is $x. \n";
  }

  display();

  // using $x outside the function will be raise an error
  print "\$x outside the function is $x. \n";
?>
```

This will produce the following result:
> PHP Notice:  Undefined variable: x in /home/vo.van.quang/Desktop/php-basic/hello_world.php on line 7

**Static variable**

Normally, when a function is completed/executed, all of its variables are deleted. However, sometime you want to local variables **NOT** to be deleted. To do this, using `static` keyword.

```php
<?php
  function display() {
    static $x = 0; // declare a static variable
    $x ++;
    echo "Value of x is $x. \n";
  }

  display();
  display();
  display();
?>
```

This will produce the following result:
> Value of x is 1.\
> Value of x is 2.\
> Value of x is 3.

## 4.Data types
- Integer: are whole numbers, like 123
- Doubles: are floating-point numbers, like: 2.12
- Booleans: True or False
- Null: NULL
- Strings
- Arrays
- Objects
- Resources - are special variables that hold references to resources external to php such as database conneciton

### Integers

```php
$int_var = 12345;
$another_int = -12345 + 12345;
```

The range of Integer is from -2,147,483,648 to 2,147,483,647

### Doubles
**By default, doubles print with the minumum number of decimal places(1)**

```php
<?php
   $firt_double = 2.2888800;
   $second_double = 2.2111200;
   $sum = $firt_double + $second_double;
   
   print("$firt_double + $second_double = $sum");
?>
```

And result will be such as below:

> 2.2888800 + 2.2111200 = 4.5

### Boolean
Such as another programming language, boolean type has only two posisible values either true or false.

```php
$var = true;
if ($var === true)
  print("This will aways print");
else
  print("This will never print");
```

**Some rules to compare any value not of Boolean type**
- If the value is a number, it is false if exactly equal zero and true otherwise
```php
  $var1 = 0;
  $var1 == false; // true

  $var2 = 1;
  $var2 == true; // true
```

- If the value is a string, it is false if the string is empty or is the string "0", and is true otherwise

```php
  $var1 = ""; // or $var1 = "0"
  $var1 == false; // true

  $var2 = "asd";
  $var2 == true; // true
```
- If the value is an array, it is false if it contains no other value, and it is true otherwise.

```php
  $true_array[0] = "An array element";
  $false_array = array();

  $true_array == true; // true
  $false_array == true; // false
```

### NULL

```php
  $null_var = null; // false with boolean type
```

### Strings

A string is a sequence of characters inside quotes(single or double qoutes), like "Hello world".

```php
  $string1 = "This is a string in php";
  $string2 = 'This is a string in php too using single quote';
```

You can inject variable to string using double quote

```php
<?php
  $my_name = "QTV";

  $literally = 'My name is $my_name';
  print($literally);

  $literally = "\nMy name is $my_name";
  print($literally);
?>
```

And you will see output such as bellow:

> My name is $my_name\
> My name is QTV

### Arrays

An array stores multiple values in one single variable

```php
<?php
  $cars = array("Volvo", "BMW", "Toyota");

  // using var_dump function to return the data type and value of variable
  var_dump($cars);
?>
```
Results:
```php
array(3) {
  [0]=>
  string(5) "Volvo"
  [1]=>
  string(3) "BMW"
  [2]=>
  string(6) "Toyota"
}
```

### Object

To create an object, we must declare a class of object. For this, we use the `class` keyword

```php
<?php
  class Car {
    function Car() {
      $this->color = "RED";
    }
  }

  // create an object
  $car = new Car();

  // show properties of object
  echo $car->color;
?>
```