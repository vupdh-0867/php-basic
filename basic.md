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

## 5. Functions

### Define a function
To define a function in php you use `function` keyword.

```php
<?php
  // define a function with name is hello
  function hello() {
    echo "Hi! I'm a function\n";
  }

  // call function hello
  hello();
?>
```

This wlll produce the following result:
> Hi! I'm a function

### Passing arguments to function

Information can be passed to functions through arguments. Argument is like variable
You can pass one or multiple argument as you want to a function

```php
<?php
  function welcomeNewMember($name) {
    echo "Welcome $name join our group\n";
  }

  welcomeNewMember("Jani");
  welcomeNewMember("Hege");
?>
```

Results:
> Welcome Jani join our group\
> Welcome Hege join our group

The following example has a function with two arguments
```php
<?php
  function welcomeNewMember($name, $group) {
    echo "Welcome $name join $group group\n";
  }

  welcomeNewMember("Jani", "Sales");
  welcomeNewMember("Hege", "Design");
?>
```

Results:
> Welcome Jani join Sales group\
> Welcome Hege join Design group

### Passing arguments by Reference

If you want to reference to original variable using can use `&` keyword before argument names. The example below to make easy understanding.

```php
<?php
  function  addFive($num) {
    $num += 5;
  }
  
  function  addSix(&$num) {
    $num += 6;
  }

  $original_num = 10;

  addFive($original_num);
  echo "Original value is $original_num \n";

  addSix($original_num);
  echo "Original value is $original_num \n";
?>
```

Results:
> Original value is 10\
> Original value is 16

### Function return value

To return a value in a function you can use `return` keyword. You can return one or more value from a function using `return array(1, 2, 3, 4)`.

Following example take two arguments and return sum of them.

```php
<?php
  function sum($num1, $num2) {
    return $num1 + $num2;
  }

  echo "Sum of 5 and 10 is ". sum(5, 10);
?>
```

Results:

>Sum of 5 and 10 is 15

### Setting defaut value for function arguments

Sometime you want arguments have default value when call function but not pass it.

```php
<?php
  function draw($shape = "Circle") {
    echo "This is a $shape \n";
  }

  draw("Square");
  draw();
?>
```
Results:
> This is a Square\
> This is a Circle

See example below to undstanding more about default value:

```php
<?php
  function draw($shape = "Circle", $color) {
    echo "This is a $color $shape\n";
  }

  function draw2($color, $shape = "Circle") { // The arguments have default value must be passing later
    echo "This is a $color $shape\n";
  }

  draw("Red"); // It will be raise an error with missing agrument
  draw2("Red"); // This is a Red Circle
?>
```

### Dynamic function calls

It is possible to assign function names as string to variables and using it as function name.

```php
<?php
  function hello() {
    echo "Hello world!";
  }

  // using a variable
  $function_holder = "hello";
  $function_holder();

  // using call_user_func() method
  call_user_func($function_holder);

  // using eval() method 
  $function_name = "hello();";
  eval($function_name);
?>
```

You can read [here](https://www.geeksforgeeks.org/how-to-call-php-function-from-string-stored-in-a-variable/) to more information about dynamic functions.

## 6. Operators
PHP devides the operators in the following group:

- Arthmetic operators
- Assignment operators
- Comparison operators
- Increment/Decrement operators
- Logical operators
- String operators
- Array operators
- Conditional assignment operators

**Arthmetic operators**

Operator | Name | Example | Result
-------- | ---- | ------- | ------ 
\+ | Addition | $x + $y | Sum of $x and $y
\- | Subtraction | $x - $y | Difference of $x and $y
\* | Multiplication | $x * $y | Product of $x and $y
/ | Division | $x / $y | Quotient of $x and $y
% | Modules | $x % $y | Remainder of $x divided by $y
** | Exponentiation | $x ** $y | Result of raising $x to the $y'th power

**Assignment operators**

Assignment | Same as... | Description
-------- | ---- | -------
x = y | x = y | The left operand gets set to the value of the expression on the right
x += y | x = x + y | Addition
x -= y | x = x - y | Subtraction
x *= y | x = x * y | Subtraction
x /= y | x = x / y | Division
x %= y | x = x % y | Modules

**Comparsion operators**

The php comparsion operators are used to compare two values:

Operator | Name | Example | Result
-------- | ---- | ------- | ------ 
== | Equal | $x == $y | Returns true if $x is equal to $y
=== | Identical | $x === $y | Returns true if $x is equal to $y, and they are of the same type	
!= | Not equal | $x != $y | Return true if $x is not equal to $y
<> | Not equal | $x <> $y | Return true if $x is not equal to $y
!== | Not identical | $x !== $y | Return true if $x is not equal to $y, or they are not of the same type
\> | Greater than| $x > $y | Return true if $x greater than &y
< | Less than | $x < $y | Return true if $x less than &y
\>= | Greater than or equal to | $x >= $y | Return true if $x greater than or equal &y
<= | Less than or equal to | $x <= $y | Return true if $x less than or equal &y
<=> | Spaceship | $x <=> $y | Returns an integer less than, equal to, or greater than zero, depending on if $x is less than, equal to, or greater than $y.


**Increment / Decrement operators**

Operator | Name | Description
-------- | ---- | -------
++$x | Pre-increment | Increment $x by one, then return $x 
$x++ | Post-increment | Return $x, then increment $x by one
--$x | Pre-decrement | Decrement $x by one, then return $x
$x-- | Post-decrement | Return $x, then decrement $x by one


**Logical operators**

Operator | Name | Example | Result
-------- | ---- | ------- | ------ 
and | And | $x and $y | True if both $x and $y is true
or | Or | $x or $y | True if either $x or $y is true
xor | Xor | $x xor $y | True if either $x or $y is true, but not bold
&& | And | $x && $y | True if bold $x && $y is true
\|\| | And | $x \|\| $y | True if either $x or $y is true
! | Not | !$x | True if $x is not true

**String operators**

Operator | Name | Example | Result
-------- | ---- | ------- | ------ 
. | Concatenation | $txt1 . $txt2 | Concatenation of $txt1 and $txt2
.= | Concatenation assignment | $txt1 .= $txt2 | Append $txt2 to $txt1

**Conditional Assignment operators**

Operator | Name | Example | Result
-------- | ---- | ------- | ------ 
?: | Ternary | $x = $condition ? $value1 : $value2 | Return value of $x. If $condition is true then $x = $value1, else $x = value2
?? | Null coalescingt | $value1 ?? $value2 | Return value of $x, If $value1 is exist and is not null then $x = $value1, else $x = value2

## 7. Array

**Create an array in PHP:** Using `array()` function to create an array

```php
<?php
  $cars = array("Volvo", "BWM", "Toyota");
  echo "I like " . $cars[0] . ", " . $cars[1] . " and " . $cars[2] . ".";
?>
```
Results:
> I like Volvo, BWM and Toyota.

**Multidimensional Arrays:**

```php
<?php
  $marks = array(
    "john" => array(
      "math" => 10,
      "physic" => 8
    ),
    "jack" => array(
      "math" => 10,
      "physic" => 8
    )
  );

  echo "Mark for john in math is " . $marks['john']['math'];
  echo "\nMark for jack in physic is " . $marks['jack']['physic'];
?>
```
Results:
> Mark for john in math is 10\
> Mark for jack in physic is 8

**Get length of an array - count() function**

```php
<?php
  $cars = array("Volvo", "BWM", "Toyota");
  echo count($cars);
?>
```
Results:
> 3

## 8. Conditions

PHP support following three decision marking statements:

- `if` statement - executes some code if one condition is true
- `if...else` statement - executes some code if a condition is true or another code if that is false
- `if...elseif...else` statement - executes different codes for more than two conditions
- `switch` statement - select one of many blocks to be executed, using instead of `if...elseif...else` to avoid multiple block


### **The `if` statement**

#### Syntax
```php
if (condition) {
  // code to be executed if condition is true
}
```

#### Example
Output "You are old" if your age greater than 70

```php
<?php
  $age = 79;
  if ($age > 70) {
    echo "You are old";
  }
?>
```
Results:
> You are old

### **The `if...else` statement**
#### Syntax
```php
if (condition) {
  // code to be executed if condition is true
} else {
  // code to be executed if condition is false
}
```

#### Example
Output "You are old" if your age greater than 70, else "You are young"

```php
<?php
  $age = 50;
  if ($age > 70) {
    echo "You are old";
  } else {
    echo "You are young";
  }
?>
```
Results:
> You are young

### **The `if...elseif...else` statement**
#### Syntax
```php
if (condition1) {
  // code to be executed if condition1 is true
} elseif (condition2) {
  // code to be executed if condition1 is false and this condition is true
} else {
  // code to be executed if all condition is false
}
```

#### Example
Output "You are old" if your age greater than 70, or "You are young" if age greater than 20, else "You are child"

```php
<?php
  $age = 10;
  if ($age > 70) {
    echo "You are old";
  } elseif ($age > 20) {
    echo "You are young";
  } else {
    echo "You are child";
  }
?>
```
Results:
> You are child

### **The `switch` statement**
#### Syntax
```php
switch (n) {
  case label1:
    code to be executed if n = label1;
    break;
  case label2:
    code to be executed if n = label2;
    break;
  ...
  default:
    code to be executed if n not equal any labels;
}
```

#### Example
Output "Lan" if gender is female, "Diep" if gender is male, "Cong Cong" if gender is another 

```php
<?php
  $gender = "male";
  switch ($gender) {
    case "female":
      echo "Lan";
      break;
    case "male":
      echo "Diep";
      break;
    default:
      echo "Cong Cong";
  }
?>
```
Results:
> Diep

## 9. Loops
In PHP, we have the following looping statements:
- `while` - loops through a block of code as long as the condition is true
- `do...while` - loops through a block of code once and repeats the loops as long as if condition is true
- `for` - loops through a block of code a specific number of times
- `foreach` - loops through a block of code for each element in an array

### **The `while` loop**
#### Syntax
```php
while (condition) {
  // code to be executed if condition is true
}
```

#### Example
Output "Hello world" three times.

```php
<?php
  $count = 0;
  while ($count < 3) {
    echo "Hello world\n";
    $count++;
  }
?>
```

### **The `do...while` loop**
#### Syntax
```php
do {
  // code to be executed
  // and this will be repeat if condition in while is true
} while (condition)
```

#### Example
The do while will be print value of $x once, and then increment the variable $x with 1. Then the condition is checked. Code will be repeat as long as $x less than or equal 5.

```php
<?php
$x = 1;

do {
  echo "The number is: $x \n";
  $x++;
} while ($x <= 5);
?>
```

### **The `for` loop**
#### Syntax
```php
for (init counter; condition; increment counter) {
  // code to be executed;
}
```
Parameters:

+ *init counter*: Initialize the loop counter value
+ *condition*: If condtion is true then loop continues, else the loop ends
+ *increment counter*: Increment counter value

#### Example
The example below displays from 0 to 3:

```php
<?php
for ($x = 0; $x <= 3; $x++) {
  echo "The number is $x\n";
}
?>
```
Results:
> The number is 0\
> The number is 1\
> The number is 2\
> The number is 3

### **The `foreach` loop**
#### Syntax
```php
foreach ($array as $element) {
  // code to be executed;
}
```

#### Example
The example below displays name of student in a class:

```php
<?php
$names = array("qtv", "vu", "hai");
foreach($names as $name) {
  echo "The name of student is $name\n";
}
?>
```
Results:
> The name of student is qtv\
> The name of student is vu\
> The name of student is hai

## OOP
Các tính chất của lập trình hướng đối tượng:

### **Tính đóng gói**
- Tính đóng gói(encapsulation): "Đóng gói" các thuộc tính và phương thức của đối tượng(hoặc lớp) thông qua việc giới hạn quyền truy cập(hoặc thay đổi) giá trị của thuộc tính hoặc thực thi phương thức. 
- Trong PHP việc đóng gói được phân theo 3 cấp độ:
  - `public`: Có thể truy cập các thuộc tính và phương thức ở bất cứ đâu, mặc định là public
  - `protected`: Có thể truy cập các thuộc tính và phương thức ở trong class hoặc các class con
  - `private`: Chỉ có thể truy cập các thuộc tính và phương ở trong class đó

- cùng xem qua ví dụ phía dưới để hiểu rõ hơn về 3 loại truy cập trên:

```php
<?php
class People {
  public function talk() {
    echo "I know speak\n";
  }

  protected function eat() {
    echo "I know eat\n";
  }

  private function run() {
    echo "I know run\n";
  }

  public function eatFood() {
    self::eat();
  }

  public function runFlash() {
    self::run(); // only access private method using within class
  }
}

class Customer extends People {
  public function runFlash() {
    self::run(); // can't access private method to supper class
  }

  public function eatFood() {
    self::eat(); // can access protected method to super class
  }
}

People::talk();
People::eatFood();
People::runFlash();
People::run(); // can't access private method outside class

Customer::talk();
Customer::eatFood();
Customer::runFlash();
?>
```

### **Tính kế thừa**
- Tính thừ kế cho phép các class con kế thừa lại các thuộc tính và phương thức(protected và publish) được định nghĩa trong class cha
- Sử dụng từ khóa `extends` để kế thừa
- Trong php chỉ hỗ trợ đơn thừa kế, có nghĩa là một class chỉ kế thừa từ một class khác. Để sử dụng đa kế thừa thì php có sinh ra một thuật ngữ khá hay đó Traits(nếu các bạn đã từng làm việc vs ruby thì thằng này có vẻ giống mixin trong ruby)

- Ví dụ:

```php
<?php
  class Animal {
    private $name;
    
    public function __construct($name) {
      $this->name = $name;
    }

    public function hello() {
      echo "Hi! I'm an animal. My name is $this->name";
    }
  }

  class Dog extends Animal{
    
  }

  $dogi = new Dog("Dogi");
  $dogi->hello(); // Hi! I'm an animal. My name is Dogi
?>
```

### **Tính trừu tượng**
- Trong các tính chất thì tính trừu tượng thường làm cho các ae new dev hay loạn não.
- Tính trừ tượng hiểu đơn giản là nó ẩn những cái tính chất, đặc điểm, chi tiết(trong ngôn ngữ lập trình thì có thể xem những cái này là thuộc tính và phương thức) của đối tượng đi và chỉ hiển thị ra những cái cốt lõi một cách tổng thể.
- Vì vậy nó giúp chúng ta có 1 cách nhìn tổng quát về đối tượng thay vì phải quan tâm tất tần tật những thứ có trong nó và cách chúng thực thi như thế nào.
- Có 2 từ khóa bạn cần biết khi nói tới tính trừu tượng trong lập trình hướng đối tượng đó là `abstract` và `interface`
- Sau đây là một ví dụ để mọi người hiểu hơn về tính chất này:

Giả sử chúng ta có:
- Một `abstract` class `Animal` có chứa phương thức `hello()`, phương thức này chỉ khai báo tên chứ không implement(đây là rule khi mình khai báo phương thức trong `abstract` class).
- Một `interface` là `Action` có chứa phương thức `run()`, phương thức này cũng chỉ được khai báo tên thôi.
- Có một class Cat kế thừa lại lớp abstract `Animal` thông qua từ khóa `extends` và interface `Action` qua từ khóa `implements`.

```php
<?php
abstract class Animal {
  abstract protected function hello() : string; // một phương thức abstract phải được khai báo bắt đầu với từ khóa abstract
}

interface Action {
  function run();
}

class Cat extends Animal implements Action {
  function hi() {
    echo "Hi";
  }

  // các lớp con kết thừa abstract class thì phải định nghĩa lại những phương thức đã được khai báo trong abstract class
  public function hello() : string {
    return "hello viet name";
  }

  // cũng giống như abstract class, một class kế thừa interface thì phải định nghĩa lại những phương thức đã được khai báo trong interface
  function run() {
    echo "Running!";
  }
}

// Cat::hi();
$cat = new Cat;
$cat->hi();
echo $cat->hello();
```

Dưới đây là bảng thông kê những điểm khác biệt giữa `abstract` và `interface`:

a | Abstract | Interface
- | -------- | ---------
Multiple inheritance | Không hỗ trợ đa thừa kế | Một class có thể hiện thực nhiều interface
Access modifiers | Có thể xác định modifier | Mọi phương thức, property đều mặc định là public
Adding functionality | Không cần thiết | Mọi phương thức, property của interface cần được thực hiện trong class
Fields và Constants | Có | Không  


**Thực chất `abstract` được xem như là `bản thiết kết cho class` còn `interface` là `bản thiết kế cho method`**

### **Tính đa hình**
- Tính đa hình là gì? Hiểu một cách nôm na và thông thường thì tính đa hình là nhiều mặt, nhiều hình dạng,...
- Các lớp con có thể viết lại hoặc mở rộng phương thức của lớp cha mà nó kế thừa.
- Các class cùng implement một interface nhưng chúng có cách thức thực hiện khác nhau cho các method của interface đó.
- Qua đó cùng 1 phương thức sẽ cho kết quả khác nhau khi được gọi bởi các đối tượng thuộc lớp khác nhau.

```php
<?php
class Vehicle {
  function say() {
    echo "I would like to service you";
  }
}

class Car {
  function say() {
    echo "I'm a Car\n";
  }
}

class Bus {
  function say() {
    echo "I'm a Bus";
  }
}

$car = new Car;
$car->say(); // I'm a Car

$bus = new Bus;
$bus->say(); // I'm a Bus
```
Vẫn là phương thức `say` nhưng 2 đối tượng lại cho ra 2 kết quả khác nhau.

## **Static keyword**
- Thế nào là một phương thức static
- Phân biệt static::method() với self::method()

### **Thế nào là một phương thức static**
- Phương thức static có thể truy thông qua class mà không cần phải khởi tạo đối tượng.
- Khai báo một phương thức static trong một class như sau:

```php
public static function hello() {
  // SOME CODE HERE
}
```

- Để thực thì một phương thức `static` trong class ta có thể sử dụng những cách sau: `self::staticMethod()`, `static::staticMethod()` hoặc `$this->staticMethod()`. Trong đó `self` và `static` là đại diện cho `class`, còn `$this` thì đại diện cho `object`.
- Trong phương thức static thì không thể gọi thuộc tính và phương thức `non-static`, những ngược lại thì `non-static` có thể gọi các phương thức hoặc thuộc tính `static`.

### **Phân biệt static::method() với self::method()**
- Cả 2 từ khóa static và self đều đại diện cho class vậy tại sao phải sinh ra cả 2 trong khi chỉ cần 1 là đủ rồi.
- Nếu như xét phạm vi trong nội bộ của class thì 2 từ khóa này đều cho ra kết quả giống nhau.
- Mn xem qua ví dụ phía dưới để tìm ra điểm khác biệt:
Ở ví dụ này mình mở trọng phạm vi ra class con kế thừa class cha thì 2 từ khóa này hoạt dộng như thế nào

```php
<?php
class Human {
  protected static $className = 'class Human';

  public static function getClassName() {
    echo self::$className;
    echo " - ";
    echo static::$className."\n";
  }
}

class Student extends Human {
  protected static $className = 'class Student';
}

Human::getClassName(); // class Human - class Human
Student::getClassName(); // class Human - class Student
```

Trong ví dụ trên class `Student` đã `extends` class `Human`, và class `Student` đã override lại thuộc tính `$className`.
- Khi `Student::getClassName()` thực thi kết quả trả về là `class Human - class Student`, như vậy từ khóa self đại diện cho chính đối tượng khai báo nó, phương thức `getClassName` được khai báo trong class `Human` nên thuộc tính self trong phương thức này đại diện cho class `Human`, kết quả trả về là `class Human`. Còn `static` đại diện cho class gọi nó, ở đây class `Student` đã gọi phương thức `getClassName` nên `static` ở đây đại diện cho class `Student`.

Kết luận:
- `self`: Đại diện cho class khai báo nó
- `static`: Đại diện cho class gọi đến nó