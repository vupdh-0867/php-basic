# PHP cơ bản

## Nội dung
1. [Chương trình "Hello world"](https://github.com/quangvv-1620/php-basic/blob/master/basic_vi.md#1-hello-world)
2. [Các cú pháp cơ bản](https://github.com/quangvv-1620/php-basic/blob/master/basic_vi.md#2-basic-syntax)
3. [Biến](https://github.com/quangvv-1620/php-basic/blob/master/basic_vi.md#3-variables)
4. [Kiểu dữ liệu](https://github.com/quangvv-1620/php-basic/blob/master/basic_vi.md#4-data-types)
5. [Hàm](https://github.com/quangvv-1620/php-basic/blob/master/basic_vi.md#5-functions)
6. [Toán tử](https://github.com/quangvv-1620/php-basic/blob/master/basic_vi.md#6-operators)
7. [Mảng](https://github.com/quangvv-1620/php-basic/blob/master/basic.md#7-array)
8. [Điều kiện](https://github.com/quangvv-1620/php-basic/blob/master/basic_vi.md#8-conditions)
9. [Vòng lặp](https://github.com/quangvv-1620/php-basic/blob/master/basic_vi.md#9-loops)

## 1. Chương trình "Hello world"

Để học PHP cơ bản, việc đầu tiên chúng ta cần làm là viết một đoạn code PHP in ra câu "Hello, world!"

Hãy tạo một file có tên `hello_world.php` theo đường dẫn vào thư mục học PHP (của mình là `Desktop/php-basic/`) và thêm đoạn code sau vào file vừa tạo

```php
<?php
  echo "Hello, World!";
?>
```

**Thực thi file:** để thực thi file php, hãy mở terminal và gõ theo cú pháp `php path_to_file`, như ở ví dụ này là `php Desktop/php-basic/hello_world.php` sau đó kết quả sẽ được hiển thị trên terminal như sau :

> Hello, World!

Thật đơn giản đúng không nào!

Nếu bạn không muốn thực thi bằng file, bạn có thể `php -a` để code ngay trên terminal.

![run by shell](./images/run_by_shell.png)

## 2. Các cú pháp cơ bản

### PHP tags

- **Canonical PHP tags:** Cách phổ biến nhất để sử dụng PHP tag

```php
<?php ... ?>
```

- **Short-open (SGML-style) tags:**

```php
<? ... ?>
```

Tuy nhiên, đây không phải là cú pháp mặc định của PHP, để sử dụng short-open tags ta phải đặt giá trị của `short_open_tag` trong file **php.ini** file thành On. (Đường dẫn file php.ini trong ubuntu là /etc/php/x.x/cli/php.ini)

- **ASP-style tags:** Đã bị loại bỏ ở PHP 7

```php
<% ... %>
```

- **HTML script tags:** Đã bị loại bỏ ở PHP 7

```php
<script language="php">...</script>
```

### Comment trong PHP

- **Comment một dòng**

Để thực hiện comment theo từng dòng trong PHP bạn có thể sử dụng cú pháp `#` hoặc `//` trước mỗi dòng

```php
<?php
  # This is a single comment
  // and this is a single comment too
  print "An example with single line comments";
?>
```

- **Comment nhiều dòng**

Còn đối với comment cho nhiều dòng trong PHP bạn có thể sử dụng cú pháp `/**/`:

```php
<?php
  /* This is a first line comment
  And this is a second line comment
  */

  print "An example with multi line comments";
?>
```

- **In một đoạn văn bản nhiều dòng**

Để in một đoạn văn bản có nhiều dòng, có 2 cách sau:

```php
<?php
  # Sử dụng heredoc, dùng cho trường hợp bạn muốn in ra dấu "", '' và sử dụng biến(string interpolation) trong đoạn text
print <<<END
This uses the "here document" syntax to output
multiple lines with $variable interpolation. Note
that the here document terminator must appear on a
line with just a semicolon no extra whitespace!
END;

# Sử dụng cặp quote ""
print "This spans
multiple lines. The newlines will be
output as well";
?>
```

- **Cú pháp trong PHP có phân biệt hoa thường**

```php
<?php
  $capital = 10;
  print("Variable capital is $capital \n");
  print("Variable CaPiTal is $CaPiTal");
?>
```

Kết quả in ra sẽ là:

> Variable capital is 10\
> Variable CaPiTal is

và ở trước dòng thứ 2 sẽ xuất hiện một error báo biến $CaPiTal chưa được định nghĩa.

## 3. Biến

### Khai báo biến trong PHP

```php
<?php
  $x = 10;
  $txt = "Hello world!";
?>
```

### Một số quy tắc cần lưu ý đối với biến trong PHP

- Tất cả các biến trong php được bắt đầu với ký hiệu đô la `($)`
- PHP sẽ tự động chuyển kiểu dữ liệu của biến nếu cần thiết

```php
<?php
  $num1 = 1;
  $num2 = "2";
  print($num1 + $num2) //3
?>
```

- Tên biến phải bắt đầu với ký tự alphabet hoặc dấu gạch dưới `(_)`
- Tên biến không thể bắt đầu với số
- Tên biến phân biệt hoa thường($age và $AGE là 2 biến khác nhau)

### Phạm vi của biến

- Biến toàn cục (global variable)
- Biến cục bộ (local variable)
- Biến static (static variable)

**Biến toàn cục (global variable)**

Là biến được định nghĩa **bên ngoài** một hàm và có phạm vi toàn cục và chỉ có thể được truy cập ở bên ngoài hàm

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

Tuy nhiên vẫn có cách để chúng ta có thể sử dụng biến toàn cục bên trong một hàm bằng cách sử dụng từ khóa *`global`*

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

**Note:** PHP cũng tự động lưu các biến global vào một mảng là `$GLOBALS[index]` với `index` là tên của biến.

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

**Biến cục bộ (local variable)**

Là biến được định nghĩa **bên trong** một hàm và có phạm vi cục bộ và chỉ có thể được truy cập ở bên trong hàm

```php
<?php
  function display() {
    $local_var = 10; // local variable
    print "\$local_var inside the function is $local_var. \n";
  }

  display();

  // using $local_var outside the function will be raise an error
  print "\$local_var outside the function is $local_var. \n";
?>
```

Đoạn code này sẽ bắn ra lỗi theo format sau:
> PHP Notice:  Undefined variable: local_var in /Path_to/php-basic/hello_world.php on line x

**Biến static (static variable)**

Thông thường, sau khi một hàm thực hiện xong, tất cả các biến bên trong nó sẽ bị xóa đi. Tuy nhiên, trong một số trường hợp bạn muốn các biến này không bị xóa đi. Để làm điều này ta sử dụng từ khóa `static`.

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

Kết quả thực thi sẽ là:
> Value of x is 1.\
> Value of x is 2.\
> Value of x is 3.

## 4.Data types

- Integer: số nguyên, ví dụ 123
- Doubles: số thực , ví dụ: 2.12
- Booleans: true hoặc false
- Null
- Strings
- Arrays
- Objects
- Resources - các biến đặt biệt nắm giữ tham chiếu đến các tìa nguyên beenn ngoài PHP như kết nối tới database

### Integers

```php
$int_var = 12345;
$another_int = -12345 + 12345;
```

Integer là các số nguyên nằm trong khoảng -2,147,483,648 đến 2,147,483,647

### Doubles

**Mặc định, double sẽ in ra giá trị chỉ lấy một chữ số sau dấu (`.`)**

```php
<?php
   $firt_double = 2.2888800;
   $second_double = 2.2111200;
   $sum = $firt_double + $second_double;

   print("$firt_double + $second_double = $sum");
?>
```

Kết quả:

> 2.2888800 + 2.2111200 = 4.5

### Boolean

Such as another programming language, boolean type has only two posisible values either true or false.
Cũng giống như các ngôn ngữ lập trình khác, kiểu boolean trong PHP có 2 giá trị là `true` hoặc `false`

```php
$var = true;
if ($var === true)
  print("This will aways print");
else
  print("This will never print");
```

**Một số quy tắc khi so sánh giá trị boolean với các giá trị khác**

- Nếu giá trị là một số, 0 sẽ được quy về false, các số còn lại là true

```php
  $var1 = 0;
  $var1 == false; // true

  $var2 = 1;
  $var2 == true; // true
```

- Nếu giá trị là một chuỗi, chuỗi rỗng "" hoặc "0" sẽ được quy về false, còn lại là true

```php
  $var1 = ""; // or $var1 = "0"
  $var1 == false; // true

  $var2 = "asd";
  $var2 == true; // true
```

- Nếu giá trị là một mảng, mảng rỗng sẽ được quy về false, mảng có giá trị sẽ là true

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

Chuỗi là một dãy các ký tự liên tiếp nhau được bọc trong cặp dấu nháy đơn hoặc nháy kép.

```php
  $string1 = "This is a string in php";
  $string2 = 'This is a string in php too using single quote';
```

Ta có thể sử dụng biến ngay trong chuỗi được bọc bởi dấu nháy kép

```php
<?php
  $my_name = "QTV";

  $literally = 'My name is $my_name';
  print($literally);

  $literally = "\nMy name is $my_name";
  print($literally);
?>
```

Kết quả:

> My name is $my_name\
> My name is QTV

### Mảng

```php
<?php
  $cars = array("Volvo", "BMW", "Toyota");
  // or in PHP > 5.3
  //$cars = ["Volvo", "BMW", "Toyota"];

  // using var_dump function to return the data type and value of variable
  var_dump($cars);
?>
```

Kết quả:

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

Để tạo một đối tượng, ta phải khai báo class của đối tượng đó.

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

## 5. Hàm

### Định nghĩa một hàm

Để định nghĩa một hàm trong PHP ta sử dụng từ khóa function

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

Kết quả:
> Hi! I'm a function

### Truyền đối số vào hàm

Các thông tin có thể được truyền vào hàm thông qua tham số, bạn có thể truyền một hoặc nhiều đối số vào hàm

Hàm có một đối số

```php
<?php
  function welcomeNewMember($name) {
    echo "Welcome $name join our group\n";
  }

  welcomeNewMember("Jani");
  welcomeNewMember("Hege");
?>
```

Kết quả:
> Welcome Jani join our group\
> Welcome Hege join our group

Hàm có nhiều đối số

```php
<?php
  function welcomeNewMember($name, $group) {
    echo "Welcome $name join $group group\n";
  }

  welcomeNewMember("Jani", "Sales");
  welcomeNewMember("Hege", "Design");
?>
```

Kết quả:
> Welcome Jani join Sales group\
> Welcome Hege join Design group

### Truyền đối số bằng tham chiếu

Nếu bạn muốn tác động đến giá trị của biến truyền vào, sử dụng tham chiếu bằng cách sử dụng thêm ký tự `&` vào trước tham số của hàm:

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

### Hàm trả về giá trị

Để trả về giá trị bạn có thể sử dụng từ khóa `return`. Trường hợp muốn trả về nhiều giá trị ta có thể đưa các giá trị đó vào mảng `return array(1, 2, 3, 4)`.

Ví dụ: Hàm sum($num1, $num2) sẽ trả về giá trị là tổng của $num1 và $num2.

```php
<?php
  function sum($num1, $num2) {
    return $num1 + $num2;
  }

  echo "Sum of 5 and 10 is ". sum(5, 10);
?>
```

Kết quả:
>Sum of 5 and 10 is 15

### Đặt giá trị mặt định cho tham số

```php
<?php
  function draw($shape = "Circle") {
    echo "This is a $shape \n";
  }

  draw("Square");
  draw();
?>
```

Kết quả:
> This is a Square\
> This is a Circle

Ví dụ sau sẽ làm rõ hơn về giá trị mặc định của tham số:

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

### Các kỹ thuật gọi hàm khác

PHP cung cấp một số các kỹ thuật để gọi hàm ngoài cách truyền thống:

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

Xem thêm tại [đây](https://www.geeksforgeeks.org/how-to-call-php-function-from-string-stored-in-a-variable/) để hiểu thêm về các cách gọi hàm khác

## 6. Toán tử

Trong PHP có các toán tử được phân loại theo các nhóm sau:

- Toán tử số học(Arthmetic operators)
- Toán tử gán(Assignment operators)
- Toán tử so sánh(Comparison operators)
- Toán tử tăng/giảm(Increment/Decrement operators)
- Toán tử logic(Logical operators)
- Toán tử với chuỗi(String operators)
- Toán tử với mảng(Array operators)
- Toán tử gán theo điều kiện(Conditional assignment operators)

**Toán tử số học(Arthmetic operators)**

Operator | Name | Example | Result
-------- | ---- | ------- | ------
\+ | Addition | $x + $y | Tổng của $x và $y
\- | Subtraction | $x - $y | Hiệu của $x và $y
\* | Multiplication | $x * $y | Tích của $x và $y
/ | Division | $x / $y | Thương của $x và $y
% | Modules | $x % $y | Số dư khi chia $x cho $y
** | Exponentiation | $x ** $y | Kết quả của $x lũy thừa $y

**Toán tử gán(Assignment operators)**

Assignment | Same as... | Description
-------- | ---- | -------
x = y | x = y | Gán giá trị của y cho x
x += y | x = x + y | Cộng
x -= y | x = x - y | Trừ
x *= y | x = x * y | Nhân
x /= y | x = x / y | Chia
x %= y | x = x % y | Chia lấy dư

**Toán tử so sánh(Comparison operators)**

The php comparsion operators are used to compare two values:

Operator | Name | Example | Result
-------- | ---- | ------- | ------
== | Equal | $x == $y | Trả về true nếu $x bằng $y
=== | Identical | $x === $y | Trả về true nếu $x bằng $y, và $x và $y có cùng kiểu dữ liệu
!= | Not equal | $x != $y |Trả về true nếu $x không bằng $y
<> | Not equal | $x <> $y |Trả về true nếu $x không bằng $y
!== | Not identical | $x !== $y |Trả về true nếu $x không bằng $y, hoặc chúng không có cùng kiểu dữ liệu
\> | Greater than| $x > $y |Trả về true nếu $x lớn hơn &y
< | Less than | $x < $y |Trả về true nếu $x nhỏ hơn &y
\>= | Greater than or equal to | $x >= $y |Trả về true nếu $x lớn hơn hoặc bằng &y
<= | Less than or equal to | $x <= $y |Trả về true nếu $x nhỏ hơn hoặc bằng &y
<=> | Spaceship | $x <=> $y | Trả về 0 nếu $x bằng $y, 1 nếu $x lớn hơn $y, -1 nếu $x nhỏ hơn $y.

**Toán tử tăng/giảm(Increment/Decrement operators)**

Operator | Name | Description
-------- | ---- | -------
++$x | Pre-increment | Tăng $x lên một đơn vị, sau đó trả về $x
$x++ | Post-increment | Trả về $x, sau đó tăng $x lên một đơn vị
--$x | Pre-decrement | Giảm $x xuống một đơn vị, sau đó trả về $x
$x-- | Post-decrement | Trả về $x, sau đó giảm $x xuống một đơn vị

**Toán tử logic(Logical operators)**

Operator | Name | Example | Result
-------- | ---- | ------- | ------
and | And | $x and $y | Trả về true nếu cả $x và $y là true
or | Or | $x or $y | Trả về true nếu $x hoặc $y là true
xor | Xor | $x xor $y | Trả về true nếu $x hoặc $y là true, nhưng không phải cả hai
&& | And | $x && $y | Trả về true nếu cả $x và $y là true
\|\| | And | $x \|\| $y | Trả về true nếu $x hoặc $y là true
! | Not | !$x | Trả về true nếu $x không là true

**Toán tử với chuỗi(String operators)**

Operator | Name | Example | Result
-------- | ---- | ------- | ------
. | Concatenation | $txt1 . $txt2 | Trả về kết quả là giá trị của $txt1 được ghép với giá trị của $txt2
.= | Concatenation assignment | $txt1 .= $txt2 | Ghép giá trị của $txt2 vào $txt1, giống với $txt1 = $txt1 . $txt2

**Toán tử với mảng(Array operators)**

Operator | Name | Example | Result
-------- | ---- | ------- | ------
\+ | Union | $arr1 + $arr2 | Trả về kết quả một mảng mới chứa tất cả giá trị của $arr1 và $arr2, nếu cả $arr1 và $arr2 có giá trị trùng nhau thì chỉ lấy một
== | Equality | $arr1 == $arr2 | Trả về true nếu giá trị của từng phần tử trong $arr1 bằng phần tử ở vị trí tương ứng trong $arr2
=== | Identity | $arr1 === $arr2 | Trả về true nếu giá trị và kiểu dữ liệu của từng phần tử trong $arr1 bằng phần tử ở vị trí tương ứng trong $arr2
!= | Inequality | $arr1 != $arr2 | Trả về true nếu tồn tại bất kỳ giá trị của phần tử  nào trong $arr1 khác với phần tử ở vị trí tương ứng trong $arr2
<> | Inequality | $arr1 <> $arr2 | Trả về true nếu tồn tại bất kỳ giá trị của phần tử  nào trong $arr1 khác với phần tử ở vị trí tương ứng trong $arr2
!== | Non-identity | $arr1 !== $arr2 | Trả về true nếu tồn tại bất kỳ giá trị hoặc kiểu dữ liệu của phần tử  nào trong $arr1 khác với phần tử ở vị trí tương ứng trong $arr2

**Toán tử gán theo điều kiện(Conditional assignment operators)**

Operator | Name | Example | Result
-------- | ---- | ------- | ------
?: | Ternary | $x = $condition ? $value1 : $value2 | Trả về giá trị của $x. Nếu $condition là true thì $x = $value1, ngược lại $x = value2
?? | Null coalescingt | $value1 ?? $value2 | Trả về giá trị của $x. Nếu $value1 tồn tại và không phải null thì $x = $value1, ngược lại $x = $value2

## 7. Mảng

**Tạo một mảng trong PHP:** Sử dụng hàm `array()` hoặc cặp dấu ngoặc vuông `[]`

```php
<?php
  $cars = array("Volvo", "BWM", "Toyota");
  //or with PHP > 5.3
  $cars = ["Volvo", "BWM", "Toyota"];

  echo "I like " . $cars[0] . ", " . $cars[1] . " and " . $cars[2] . ".";
?>
```

Kết quả:
> I like Volvo, BWM and Toyota.

**Mảng đa chiều:**

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

Kết quả:
> Mark for john in math is 10\
> Mark for jack in physic is 8

**Lấy độ dài của mảng - count() function**

```php
<?php
  $cars = array("Volvo", "BWM", "Toyota");
  echo count($cars);
?>
```

Kết quả:
> 3

## 8. Biểu thức điều kiện

PHP hỗ trợ các biểu thức điều kiện sau:

- `if` Là biểu thức điều kiện trong PHP kiểm tra một hoặc tổ hợp biểu thức điều kiện nào đó. Nếu biểu thức trả về true thì thực thi các dòng lệnh. Nếu không thì không làm gì cả.

- `if...else` Là biểu thức kiểm tra một hoặc tổ hợp biểu thức điều kiện nào đó. Nếu trả về true thì sẽ thực thi khối lệnh bao trong if , còn không thì thực thi khối lệnh được bao bởi else.

- `if...elseif...else` Là biểu thức kiểm tra một hoặc một tổ hợp biểu thức điều kiện nào đó, nếu biểu thức trả về giá trị true thì khối lệnh bên trong sẽ được thực thi.

- `switch` Là cú pháp kiểm tra sự thỏa mãn của tất cả  các trường hợp của biểu thức. Tương tự như elseif.

### **Biểu thức điều kiện IF**

#### Cú pháp

```php
if (condition) {
  // code to be executed if condition is true
}
```

#### Ví dụ

In ra "You are old" nếu tuổi lớn hơn 70

```php
<?php
  $age = 79;
  if ($age > 70) {
    echo "You are old";
  }
?>
```

Kết quả:
> You are old

### **Biểu thức if…else**

#### Cú pháp

```php
if (condition) {
  // code to be executed if condition is true
} else {
  // code to be executed if condition is false
}
```

#### Ví dụ

In ra "You are old" nếu tuổi lớn hơn 70, ngược lại in ra "You are young"

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

Kết quả:
> You are young

### **Biểu thức elseif**

#### Cú pháp

```php
if (condition1) {
  // code to be executed if condition1 is true
} elseif (condition2) {
  // code to be executed if condition1 is false and this condition is true
} else {
  // code to be executed if all condition is false
}
```

#### Ví dụ

In ra "You are old" nếu tuổi lớn hơn 70, hoặc "You are young" nếu tuổi lớn hơn 20, ngược lại in ra "You are child"

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

Kết quả:
> You are child

### **Biểu thức switch…case**

#### Cú pháp

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

#### Ví dụ

In ra "Minh" nếu giới tính là female, "Dat" nếu giới tính là male, "Cong Cong" nếu giới tính là another

```php
<?php
  $gender = "male";
  switch ($gender) {
    case "female":
      echo "Minh";
      break;
    case "male":
      echo "Dat";
      break;
    default:
      echo "Cong Cong";
  }
?>
```

Kết quả:
> Dat

## 9. Vòng lặp

Trong PHP có các loại vòng lặp sau:

- `while` - Thực hiện hành động chừng nào điều kiện còn đúng (true), điều kiện sẽ được kiểm tra trước khi hành động được thực hiện
- `do...while` - Giống while nhưng điều kiện sẽ được kiểm tra sau khi hành động thực hiện
- `for` - Thực hiện hành động với số lần lặp nhất định
- `foreach` - Thực hiện hành động trong khối code với từng phần tử trong mảng

### **Vòng lặp `while`**

#### Cú pháp

```php
while (condition) {
  // code to be executed if condition is true
}
```

#### Ví dụ

In ra "Hello world" 3 lần.

```php
<?php
  $count = 0;
  while ($count < 3) {
    echo "Hello world\n";
    $count++;
  }
?>
```

### **Vòng lặp `do...while`**

#### Cú pháp

```php
do {
  // code to be executed
  // and this will be repeat if condition in while is true
} while (condition)
```

#### Ví dụ

Giá trị của $x sẽ được in ra trước, sau đó giá trị của $x sẽ được tăng thêm 1 và thực hiện kiểm tra điều kiện. Lặp lại khi $x còn nhỏ hơn hoặc bằng 5

```php
<?php
$x = 1;

do {
  echo "The number is: $x \n";
  $x++;
} while ($x <= 5);
?>
```

### **Vòng lặp `for`**

#### Cú pháp

```php
for (init counter; condition; increment counter) {
  // code to be executed;
}
```

Trong đó:

- *init counter*: Khởi tạo biến đếm
- *condition*: Nếu điều kiện còn đúng thì vong lặp sẽ tiếp thục,ngược lại vòng lặp sẽ dừng
- *increment counter*: Tăng giá trị của biến đếm

#### Ví dụ
In ra các số từ 0 đến 3:

```php
<?php
for ($x = 0; $x <= 3; $x++) {
  echo "The number is $x\n";
}
?>
```

Kết quả:
> The number is 0\
> The number is 1\
> The number is 2\
> The number is 3

### **Vòng lặp `foreach`**

#### Cú pháp

```php
foreach ($array as $element) {
  // code to be executed;
}
```

#### Ví dụ

Ví dụ sau in ra tất cả tên của sinh viên trong một lớp

```php
<?php
$studentNames = array("qtv", "vu", "hai");
foreach($studentNames as $name) {
  echo "The name of student is $name\n";
}
?>
```

Kết quả:
> The name of student is qtv\
> The name of student is vu\
> The name of student is hai
