# Operators and Expressions

In this chapter, we will learn about operators and expressions in JavaScript.


- [Operators and Expressions](#operators-and-expressions)
  - [Learning Outcomes](#learning-outcomes)
  - [What is an Operator?](#what-is-an-operator)
  - [What is an Expression?](#what-is-an-expression)
  - [Relationship Between Operators and Expressions](#relationship-between-operators-and-expressions)
  - [Types of Operators](#types-of-operators)
    - [Arithmetic Operators](#arithmetic-operators)
    - [Assignment Operators](#assignment-operators)
    - [Comparison Operators](#comparison-operators)
    - [Logical Operators](#logical-operators)
    - [Bitwise Operators (optional - not used in this course)](#bitwise-operators-optional---not-used-in-this-course)
    - [String Operators](#string-operators)
    - [Conditional (Ternary) Operator](#conditional-ternary-operator)
    - [Comma Operator](#comma-operator)
    - [Unary Operators](#unary-operators)
  - [Exercises](#exercises)
    - [Exercise 1 - Basic Arithmetic Operators](#exercise-1---basic-arithmetic-operators)
    - [Exercise 2 - Comparison Operators](#exercise-2---comparison-operators)

## Learning Outcomes

After completing this topic, you will be able to:

- Define what an operator is
- Define what an expression is
- Distinguish between operators and expressions
- List the most common operators in JavaScript
- Explain the difference between different types of operators
- Use operators in your program
- Explain the difference between the equality operator (`==`) and the strict equality operator (`===`)
- Explain the difference between the inequality operator (`!=`) and the strict inequality operator (`!==`)

## What is an Operator?

An operator is a symbol used to perform an operation on one or more values. For example, the `+` symbol is used to add two values together. The values on which the operator operates are called operands. For example, in the expression `5 + 10`, the `+` symbol is the operator, and `5` and `10` are the operands.

```javascript
let x = 5 + 10; // 5 and 10 are operands, + is the operator. x is the variable to which the result of the operation is assigned
```
## What is an Expression?

An expression is a combination of values, variables, operators, and functions that evaluates to a new value. For example, `2 + 3` is an expression that evaluates to `5`. Expressions can be used to perform calculations, manipulate strings, and more.

## Relationship Between Operators and Expressions

The primary relationship is that operators are used in expressions to define the type of operation to be performed on the operands. An expression can consist of a simple operation with only one operator (such as `x + y`) or a more complex operation with multiple operators (such as `(x + y) * (a - b)`).

The type of operator determines the type of expression. For example, arithmetic operators create arithmetic expressions, logical operators create logical expressions, and so on.

The evaluation of expressions often follows a specific order of operations determined by the precedence and associativity of the operators involved. This means that some operations are performed before others. For example, multiplication and division are performed before addition and subtraction.

## Types of Operators

JavaScript has many different types of operators. In this topic, we will cover the most commonly used operators.

### Arithmetic Operators

Arithmetic operators are used to perform arithmetic operations on numerical values. We need arithmetic operators when we want to perform calculations in our programs. For example, we might want to add two numbers together or multiply two numbers.

JavaScript has 5 arithmetic operators:

- `+`: **Addition** - adds two values together
- `-`: **Subtraction** - subtracts one value from another
- `*`: **Multiplication** - multiplies two values together
- `/`: **Division** - divides one value by another
- `%`: **Modulus** - returns the remainder of dividing one value by another

```javascript
let x = 5 + 10; // addition - result is 15
let y = 5 - 10; // subtraction - result is -5
let z = 5 * 10; // multiplication - result is 50
let w = 5 / 10; // division - result is 0.5
let v = 5 % 10; // modulus - result is 5
```
### Assignment Operators

Assignment operators are used to assign values to variables. Sometimes we want to perform an operation on a variable and assign the resulting value back to the same variable. For example, we might want to add `10` to the current value of a variable.

JavaScript has 8 assignment operators:

- `=`: assigns a value to a variable
- `+=`: adds a value to a variable and assigns the result to the variable
- `-=`: subtracts a value from a variable and assigns the result to the variable
- `*=`: multiplies a variable by a value and assigns the result to the variable
- `/=`: divides a variable by a value and assigns the result to the variable
- `%=`: divides a variable by a value and assigns the remainder to the variable
- `**=`: raises a variable to the power of a value and assigns the result to the variable
- `++`: increments a variable by 1
- `--`: decrements a variable by 1

```javascript
let x = 5; // declares a variable x and assigns the value 5
x += 10; // adds 10 to x and assigns the result to x - result is 15
x -= 10; // subtracts 10 from x and assigns the result to x - result is 5
x *= 10; // multiplies x by 10 and assigns the result to x - result is 50
x /= 10; // divides x by 10 and assigns the result to x - result is 5
x %= 10; // divides x by 10 and assigns the remainder to x - result is 5
x **= 2; // raises x to the power of 2 and assigns the result to x - result is 25
x++; // increments x by 1 - result is 26
x--; // decrements x by 1 - result is 25
```
### Comparison Operators

Comparison operators are used to compare two values. Comparing values is useful when we want to check if two values are equal or not, or if one value is greater or less than another value. The result of a comparison is a boolean value `true` or `false`.

JavaScript has 8 comparison operators:

- `==`: equal - returns true if two values are equal
- `!=`: not equal - returns true if two values are not equal
- `>`: greater than - returns true if the first value is greater than the second value
- `<`: less than - returns true if the first value is less than the second value
- `>=`: greater than or equal - returns true if the first value is greater than or equal to the second value
- `<=`: less than or equal - returns true if the first value is less than or equal to the second value
- `===`: strict equal - returns true if two values are equal and of the same type
- `!==`: strict not equal - returns true if two values are not equal or not of the same type

```javascript
let x = 5;
let y = 10;
let z = '5';

console.log(x == y); // false
console.log(x != y); // true
console.log(x > y); // false
console.log(x < y); // true
console.log(x >= y); // false
console.log(x <= y); // true
console.log(x === y); // false
console.log(x !== y); // true
console.log(x == z); // true
console.log(x === z); // false
```
> It is recommended to always use strict equality (`===`) and strict inequality (`!==`) when comparing values because, as shown in the example above, the equality operator (`==`) and the inequality operator (`!=`) can give unexpected results.
>
> For example, `5 == '5'` returns `true`, but `5 === '5'` returns `false`. This is because the equality operator (`==`) converts the operands to the same type before comparing them, while the strict equality operator (`===`) does not convert the operands to the same type before comparing them but considers both the values and their types.

### Logical Operators

Logical operators are used to combine two or more `boolean` values and return a single `boolean` value. For example, we might want to check if a number is greater than `10` and less than `20`. This can be done by combining two comparison operators with a logical `AND` operator (`&&`).

JavaScript has 3 logical operators:

- `&&`: logical `AND` - returns `true` if both operands are `true`
- `||`: logical `OR` - returns `true` if one of the operands is `true`
- `!`: logical `NOT` - returns `true` if the operand is `false`

```javascript
let x = 5;
let y = 10;

console.log(x > 5 && x < 10); // false
console.log(x > 5 || x < 10); // true
console.log(!(x > 5)); // true
```
### Bitwise Operators (optional - not used in this course)

Bitwise operators are used to perform operations on numerical values at the binary level. Bitwise operations are actions performed on numbers in their binary form. For example, the binary representation of the number `5` is `101`. The binary representation of the number `10` is `1010`. A bitwise `AND` operation on the numbers `5` and `10` results in `0` because `101` AND `1010` is `0`. Considering from right to left, the first bit of the result is `0` because the first bits of the operands are `1` and `0`. The result of the second bit is `0` because the second bits of the operands are `0` and `1`. The result of the third bit is `0` because the third bits of the operands are `1` and `0`.

JavaScript has 7 bitwise operators:

- `&`: bitwise `AND` - returns `1` if both bits are `1`
- `|`: bitwise `OR` - returns `1` if one of the bits is `1`
- `^`: bitwise `XOR` - returns `1` if one of the bits is `1` and the other is `0`
- `~`: bitwise `NOT` - inverts the bits
- `<<`: bitwise `left shift` - shifts bits to the left
- `>>`: bitwise `right shift` - shifts bits to the right
- `>>>`: bitwise `zero-fill right shift` - shifts bits to the right and fills empty bits with `0`

```javascript
let x = 5; // 101
let y = 10; // 1010

console.log(x & y); // 0 - 101 AND 1010 is 0
console.log(x | y); // 15 - 101 OR 1010 is 1111
console.log(x ^ y); // 15 - 101 XOR 1010 is 1111
console.log(~x); // -6 - inverts 101 bits to 010 and then converts 010 to decimal, resulting in -6
console.log(x << 1); // 10 - shifts 101 bits to the left by 1, resulting in 1010
console.log(x >> 1); // 2 - shifts 101 bits to the right by 1, resulting in 10
console.log(x >>> 1); // 2 - shifts 101 bits to the right by 1, resulting in 10 and fills the empty bit with 0
```
### String Operators

String operators are used to concatenate strings. For example, we might want to concatenate a person's first name and last name to get their full name.

JavaScript has only one string operator:

- `+`: concatenation - concatenates two strings

```javascript
let firstName = 'John';
let lastName = 'Doe';

console.log(firstName + ' ' + lastName); // 'John Doe'
```
### Conditional (Ternary) Operator

The conditional operator is used to assign a value to a variable based on a condition. For example, we might want to assign the value `true` to a variable if a number is greater than `10`, or the value `false` if the number is less than `10`.

JavaScript has only one conditional operator:

- `?:`: conditional - assigns a value to a variable based on a condition

```javascript
let x = 5;

let result = x > 10 ? true : false; // false
```
### Comma Operator

The comma operator is used to evaluate multiple expressions and return the result of the last expression.

JavaScript has only one comma operator:

- `,`: comma - evaluates multiple expressions and returns the result of the last expression

```javascript
let x = 5;

let result = (x = 10, x + 5); // 15
console.log(result); // 15
```

### Unary Operators

Unary operators are used to perform operations on a single value. For example, we might want to make a positive number negative or convert a value to a number.

JavaScript has 3 unary operators:

- `+`: unary plus - converts a value to a number, if it is not already a number
- `-`: unary minus - converts a value to a number and negates it
- `!`: logical NOT - returns the opposite boolean value

```javascript
let x = '5';

console.log(+x); // 5
console.log(-x); // -5
console.log(!x); // false
```
## Exercises

Create a file `index.js` and write the code for the following exercises in that file.

Test your code by running the `index.js` file using the command `node index.js`.

Also, test your code with different variable values.

### Exercise 1 - Basic Arithmetic Operators

**Objective**: Using basic arithmetic operators.

**Description**: Write a program that declares two variables, `num1` and `num2`, assigned with random numbers. Perform `addition`, `subtraction`, `multiplication`, and `division` operations with these variables. Output the result of each operation.

**Expected Output**: The `sum`, `difference`, `product`, and `quotient` of `num1` and `num2`.

<details>
  <summary>Solution</summary>

```javascript
let num1 = 5;
let num2 = 10;

console.log(num1 + num2); // 15
console.log(num1 - num2); // -5
console.log(num1 * num2); // 50
console.log(num1 / num2); // 0.5
</details>
```
![Using Operators](operators.gif)

</details>

### Exercise 2 - Comparison Operators

**Objective**: Compare two values using various comparison operators.

**Description**: Assign numerical values to two variables. Use comparison operators (`==`, `!=`, `>`, `<`, `>=`, `<=`) to compare these values and output the result of each comparison.

**Expected Output**: Expressions showing the result of each comparison between `a` and `b`.

<details>
  <summary>Solution</summary>

```javascript
let a = 5;
let b = 10;

console.log(a == b); // false
console.log(a != b); // true
console.log(a > b); // false
console.log(a < b); // true
console.log(a >= b); // false
console.log(a <= b); // true
</details>
```

# Operatörler ve İfadeler

Bu bölümde JavaScript'te operatörler ve ifadeler hakkında bilgi edineceğiz.

- [Operatörler ve İfadeler](#operatörler-ve-ifadeler)
  - [Öğrenme Hedefleri](#öğrenme-hedefleri)
  - [Operatör Nedir?](#operatör-nedir)
  - [İfade Nedir?](#ifade-nedir)
  - [Operatörler ve İfadeler Arasındaki İlişki](#operatörler-ve-ifadeler-arasındaki-ilişki)
  - [Operatör Türleri](#operatör-türleri)
    - [Aritmetik Operatörler](#aritmetik-operatörler)
    - [Atama Operatörleri](#atama-operatörleri)
    - [Karşılaştırma Operatörleri](#karşılaştırma-operatörleri)
    - [Mantıksal Operatörler](#mantıksal-operatörler)
    - [Bitwise Operatörler (isteğe bağlı - bu derste kullanılmamıştır)](#bitwise-operatörler-isteğe-bağlı---bu-derste-kullanılmamıştır)
    - [String Operatörleri](#string-operatörleri)
    - [Koşul (Ternary) Operatörü](#koşul-ternary-operatörü)
    - [Virgül Operatörü](#virgül-operatörü)
    - [Unary Operatörler](#unary-operatörler)
  - [Alıştırmalar](#alıştırmalar)
    - [Alıştırma 1 - Temel Aritmetik Operatörler](#alıştırma-1---temel-aritmetik-operatörler)
    - [Alıştırma 2 - Karşılaştırma Operatörleri](#alıştırma-2---karşılaştırma-operatörleri)

## Öğrenme Hedefleri

Bu konuyu tamamladıktan sonra şunları yapabileceksiniz:

- Operatörün ne olduğunu tanımlayın.
- İfadenin ne olduğunu tanımlayın.
- Operatörler ile ifadeleri birbirinden ayırt edin.
- JavaScript'teki en yaygın operatörleri listeleyin.
- Farklı türdeki operatörlerin arasındaki farkı açıklayın.
- Programınızda operatörleri kullanın.
- Eşitlik operatörü (`==`) ile sıkı eşitlik operatörü (`===`) arasındaki farkı açıklayın.
- Eşitsizlik operatörü (`!=`) ile sıkı eşitsizlik operatörü (`!==`) arasındaki farkı açıklayın.

## Operatör Nedir?

Operatör, bir veya birden fazla değer üzerinde işlem yapmak için kullanılan bir semboldür. Örneğin, `+` sembolü iki değeri toplamak için kullanılır. Operatörün işlem yaptığı değerlere operand denir. Örneğin, `5 + 10` ifadesinde `+` operatör, `5` ve `10` operandlardır.

```javascript
let x = 5 + 10; // 5 ve 10 operand, + operatör. x değişkenine işlemin sonucu atanır
```

## İfade Nedir?
İfade, değerler, değişkenler, operatörler ve fonksiyonların bir kombinasyonudur ve bir sonuç döner. Örneğin, 2 + 3 bir ifadedir ve sonucu 5'tir. İfadeler, hesaplamalar yapmak, stringleri manipüle etmek gibi birçok işlemde kullanılır.

Operatörler ve İfadeler Arasındaki İlişki
Temel ilişki, operatörlerin ifadelerde kullanılan işlemleri tanımlamasıdır. Bir ifade, yalnızca bir operatör içeren basit bir işlemden (x + y) veya birden fazla operatör içeren karmaşık bir işlemden ((x + y) * (a - b)) oluşabilir.

- İfadelerin değerlendirilmesi genellikle operatörlerin önceliği ve birleşme kurallarına bağlıdır. Örneğin, çarpma ve bölme işlemleri toplama ve çıkarmadan önce yapılır.

## Operatör Türleri
- JavaScript'te birçok farklı operatör türü vardır. Bu konuda en yaygın kullanılan operatörleri inceleyeceğiz.

## Aritmetik Operatörler
Aritmetik operatörler, sayısal değerler üzerinde matematiksel işlemler yapmak için kullanılır. Örneğin, iki sayıyı toplamak veya çarpmak isteyebiliriz.

JavaScript'te 5 aritmetik operatör vardır:

+: Toplama - iki değeri toplar.
-: Çıkarma - bir değeri diğerinden çıkarır.
*: Çarpma - iki değeri çarpar.
/: Bölme - bir değeri diğerine böler.
%: Modulus - bir değeri diğerine böler ve kalanı döner.

let x = 5 + 10; // toplama - sonuç 15
let y = 5 - 10; // çıkarma - sonuç -5
let z = 5 * 10; // çarpma - sonuç 50
let w = 5 / 10; // bölme - sonuç 0.5
let v = 5 % 10; // modulus - sonuç 5

Atama Operatörleri
Atama operatörleri, değişkenlere değer atamak için kullanılır. Bir değişken üzerinde işlem yapıp sonucu aynı değişkene atamak isteyebiliriz.

JavaScript'te 8 atama operatörü vardır:

=: bir değişkene değer atar.
+=: bir değişkene değer ekler ve sonucu aynı değişkene atar.
-=: bir değişkenden değer çıkarır ve sonucu aynı değişkene atar.
*=: bir değişkeni bir değerle çarpar ve sonucu aynı değişkene atar.
/=: bir değişkeni bir değere böler ve sonucu aynı değişkene atar.
%=: bir değişkeni bir değere böler ve kalanı aynı değişkene atar.
**=: bir değişkenin üssünü alır ve sonucu aynı değişkene atar.
++: bir değişkeni 1 artırır.
--: bir değişkeni 1 azaltır.

let x = 5;
x += 10; // sonuç 15
x -= 10; // sonuç 5
x *= 10; // sonuç 50
x /= 10; // sonuç 5
x %= 10; // sonuç 5
x **= 2; // sonuç 25
x++; // sonuç 26
x--; // sonuç 25

## Karşılaştırma Operatörleri
Karşılaştırma operatörleri, iki değeri karşılaştırmak için kullanılır. Karşılaştırma sonucu true veya false döner.

JavaScript'te 8 karşılaştırma operatörü vardır:

==: eşit mi - iki değer eşitse true döner.
!=: eşit değil mi - iki değer eşit değilse true döner.
>: büyük mü - ilk değer ikincisinden büyükse true döner.
<: küçük mü - ilk değer ikincisinden küçükse true döner.
>=: büyük veya eşit mi - ilk değer ikincisinden büyük veya eşitse true döner.
<=: küçük veya eşit mi - ilk değer ikincisinden küçük veya eşitse true döner.
===: sıkı eşitlik - iki değer hem eşit hem aynı türdeyse true döner.
!==: sıkı eşitsizlik - iki değer eşit değilse veya farklı türdeyse true döner.

let x = 5;
let y = 10;
let z = '5';

console.log(x == y); // false
console.log(x != y); // true
console.log(x > y); // false
console.log(x < y); // true
console.log(x >= y); // false
console.log(x <= y); // true
console.log(x === z); // false
console.log(x !== z); // true

## Alıştırmalar
Alıştırma 1 - Temel Aritmetik Operatörler
İki değişken tanımlayın ve dört temel matematiksel işlemi uygulayın.

let num1 = 5;
let num2 = 10;

console.log(num1 + num2); // 15
console.log(num1 - num2); // -5
console.log(num1 * num2); // 50
console.log(num1 / num2); // 0.5

## Alıştırma 2 - Karşılaştırma Operatörleri
İki değişken tanımlayın ve karşılaştırma operatörleriyle sonuçlarını yazdırın.

let a = 5;
let b = 10;

console.log(a == b); // false
console.log(a != b); // true
console.log(a > b); // false
console.log(a < b); // true
console.log(a >= b); // false
console.log(a <= b); // true

let x = 5;
let y = 10;
let z = '5';

console.log(x == y); // false
console.log(x != y); // true
console.log(x > y); // false
console.log(x < y); // true
console.log(x >= y); // false
console.log(x <= y); // true
console.log(x === y); // false
console.log(x !== y); // true
console.log(x == z); // true
console.log(x === z); // false
