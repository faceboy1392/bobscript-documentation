# BobScript
A custom scripting language made just for Bob Bot, built to be simple and concise.

This guide will hopefully teach you the basics of how to use BobScript's syntax and a few of its features, though I'd also encourage you to try these things out yourself as you read through the guide to see what does and doesn't work.

## Important note
BobScript is still extremely work-in-progress and is not yet available to make custom commands with. However, this guide will hopefully at least teach some of the basics of what is currently available.

## Comments
---
Since I'll be using them often in this guide, I'll quickly mention comments. A comment is some text in a script that is not executed as actual code. 

Any text followed by `//` will be ignored until the end of the line. The syntax highlighting here shows the comments as a different color.
```js
print 2 ^ 4 // Prints 2 to the power of 4 
```
> This above is a code block. Anywhere you see that formatting is a block of actual code. Any text formatted like `this` also represents a small snippet of code.

Text surrounded by `/* words here */` will form a multi-line comment, meaning that nothing in between the opening `/*` and the closing `*/` will be executed as actual code.
```js
print (5 * 38) / 4 + 1 /*
  Prints the product of 5 and 38
  divided by 4
  plus 1
*/
```
Comments are a useful way to document how your code works, though the above examples use them a bit too excessively just to demonstrate how they work.

Don't overuse comments, though also don't underestimate their importance for anyone (including yourself) who may try to read and understand your code.

## The print keyword
---
In this guide, I'll be using the `print` keyword a lot. You already saw it in the comments section above. It is basically just a simple way to output a value in raw text. If you are executing a script through one of Bob's commands on Discord or as a custom command, it'll just send a message containing the output.

Just type the `print` keyword followed by any value or expression.
```js
print "Hello Bob" // Outputs "hello world", fairly self-explanatory
print 4 * 30 // Outputs 120
```

## Values
---
BobScript values are fairly simple. A value is just a basic piece of information, and they come in a couple basic formats.

### Booleans
---
The simplest type of value, a boolean is either a `true` or `false`. Just like a simple "yes" or "no."
```js
print true // Literally just prints 'true'
print false // you probably get the point
```

### Numbers
---
I don't think I need to explain with too much detail what a number is. BobScript numbers can be whole numbers like `3`, `28`, or `0`, or they can be decimals like `2.59`. You can also use negative numbers.

You can also perform mathematical operations on numbers, though I'll get to those later.
```js
print 54 // it's just 54 nothing fancy here
``` 
> If you have any experience with programming languages that split numbers into integers and floating-point numbers, note that BobScript doesn't have any distinction between them. Something like `5 / 2` will output `2.5` without having to convert anything to floats..

### Strings
---
A string is basically just a piece of text. Think of it like a *string* of characters. Strings are denoted by any text surrounded in either single `'` or double `"` quotes.
```js
print "Greetings earthling"
```
Note that the following code is not valid:
```js
print "hamburger'
```
`"` and `'` are not interchangeable; if you start a string with one type of quote you have to end it with that same type of quote. 

### Nil
---
`nil`, also called "null" in some other languages, basically represents a lack of a value. It isn't too important yet, but just know that it exists.
```js
print nil
```

## Expressions
---
An expression is basically something that can be evaluated to a value. For example, `4*7` evaluates to `28`.

### Basic examples
--- 

Examples of expressions:
```js
print 15 + 9 // 24
print 10 - 3 // 7
print 3 * 6 // 18
print 48 / 6 // 8
print 2 ^ 4 // 16
print 10 % 4 // 2
print "Greetings " + "universe" // "Greetings universe"
print "He ate " + 47 + " apples" // "He ate 47 apples"
print "hi " * 4 // "hi hi hi hi "
```

Let's just quickly go through a couple of those. 

The first four are fairly self-explanatory. The fifth one, `2 ^ 4`, is pretty simple as well, it's just an exponent. The first number is the base and the second is the exponent itself. `10 % 4` is *modulo*, which just returns the remainder of the first number divided by the second.

What about the seventh one where it adds two strings together? That's called concatenation. It simply takes the two strings and turns them into one. Note the trailing space in `"Greetings "`, it makes sure the output doesn't become `"Greetingsuniverse"`.

The one after that is pretty simple as well. Any value can be added to a string to become part of that string.

The last one takes a string and repeats it a specified number of times.

### Order of Operations
---
When evaluated, expressions use the <a href="https://en.wikipedia.org/wiki/Order_of_operations" target="_blank">Order of Operations</a>. You may also know this by the abbreviations PEMDAS or BIDMAS. 

If you aren't already familiar with the order of operations, it basically defines an order (or *precedence*) in which you should solve certain parts of an expression:

1. Parentheses `()`
1. Exponents `^`
1. Multipication / division `* /`
1. Addition / subtraction `+ -`

For example, `1+3*5` will evaluate to `16` because `3*5` is evaluated first and then `1` is added to that.

BobScript follows these rules:
```js
print 20 - 3 * 5 // 5
print 2 ^ 3 + (-4) // 4
print 6 * (2 + 1) // 18
```

Multiplication and division have the same precedence, and so do addition and subtraction. If multiple operations of the same precedence are chained together, it just evaluates them left to right.

## Variables
---
You can't have a proper scripting language without the almighty *variable*. A variable is sort of like a little bucket of information with a label on it.

A variable can contain any value, and accessing that variable later will return that value. Variables usually contain booleans, numbers, strings, or `nil`. They can also contain other things like functions, but that's not what this part of the guide is about.

Before using a variable, it needs to be *declared*. This can be done by using the `var` keyword followed by the name of the variable you want to create. You can also use an equal sign `=` to assign it a value.
```js
var foo = "bar"
print foo // outputs "bar"
```
> *What the heck is a foo bar and why do programmers always use it in their code examples?*

Let me just go over that code above real quick. First, a variable is declared using the `var` keyword followed by the name of the variable you want to create. Then, it is assigned a value using the equal sign `=` followed by a string value. It doesn't matter what that value is, it can even be an expression that evaluates to a value. 

On the next line, it then uses the name of the variable to access that value. 

Variables that are not assigned a value default to `nil`:
```js
var myBraincells
print myBraincells // outputs nil
```

To assign a new value to a variable, it's roughly the same as declaring a variable, just without the `var` keyword:
```js
var h = "hello world"
print h // "hello world"
h = "this variable is enhanced with disney's fastplay"
print h // "this variable is enhanced with disney's fastplay"
```

Variables can be used anywhere that a value can be used. `print` statements, expressions, variables can even be assigned to the values of other variables.
```js
// Gives the circumference and area of a circle based on a given radius
var radius = 7
var diameter = radius * 2

var pi = 3.1415926535

print "Circumference: " + diameter * pi
print "Area: " + ( pi * r ^ 2 )

// Multiplies a string and adds a space in between
var cool_string = "yeet"
print ( cool_string + " " ) * 5 // "yeet yeet yeet yeet yeet "
```
> It is recommended to use <a href="https://en.wikipedia.org/wiki/Snake_case" target="_blank">snake_case</a> to name your variables in BobScript. In snake_case, most variables are usually lowercase and variable names consisting of multiple words are separated by an underscore `_`

## Semicolons
---
Before I go any further, I'd like to quickly mention semicolons `;`. A lot of programming languages require a `;` at the end of every statement to explicitly separate statements.

BobScript doesn't necessarily require you to put explicit semicolons at the end of every statement. Usually, it can tell when to automatically insert a little invisible semicolon in your script. This is typically at the end of each line, with a few exceptions.

To clarify: When I say statement, I mean things like `print 4 + 3` or `var a = "hi"`. Most of the time I'll put individual statements on separate lines in this guide.

However, there are problems with BobScript inserting hidden semicolons at the end of most lines. Look at the following code:
```js
var result = 5
+ 34
* 57
/ 2
```
It's a slightly strange script, but it illustrates what I'm trying to explain. BobScript will look at this script and think you are trying to declare `result` and assign it the value of `5`. It'll think that is the end of the statement. Then, it will look at the next line and return an error because it thinks the `+ 34` shouldn't be there. 

To make this work, you can use the ellipses character `…` to continue a statement on the next line.
```js
var result = 5 …
+ 34 …
* 57 …
/ 2
```

This will make the code act like it's all on one line, even though it isn't. Splitting a statement across multiple lines like this can sometimes help with readability.

> You can still put explicit semicolons in your code if you want to, and it is useful if you want multiple statements on the same line for whatever reason. It's just not required usually.

## Logic
---
Since the next section heavily involves logical and comparison operators, I'll go over them here first.

### Logical operations
---
A logical operator compares two values, usually booleans, and decides whether or not the specific comparison is true.

There are three logical operators in BobScript.
```js
var cool_bool = true

// Logical AND
print cool_bool and true // true
print cool_bool and false // false

// Logical OR
print cool_bool or false // false

// Logical NOT
print !cool_bool // false
```
> Similar to mathematical calculations, boolean logic (what is shown above) follows its own order of operations. NOT (`!`) is first, then AND (`and`), then OR (`or`). Anything inside parentheses `()` goes before any of that.

### Comparison operators
---
Comparison operators do roughly what their name suggests: They *compare* two values.
```js
// Equal
print 5 + 3 == 8 // true
print "Hello" == "Hi" // false

// Not equal
print 8    != 6 + 1 // true
print "20" != 20 // true, different value types are never equal

// Greater than, less than, greather than or equal, less than or equal
print 5 >  3 // true
print 5 >= 6 // false
print 3 <  3 // false
print 3 <= 3 // true

print "Die hard" == "Christmas movie" // false, fight me
```
> Note the difference between `=` and `==`. A single equal sign `=` is used to assign a value to a variable, while a double equal sign `==` is used to check equality of two values. It's a confusing distinction sometimes, but it'll get easier to remember the more you practice.

### Truthiness / falsiness
---
Booleans aren't the only thing that can produce a true or false state. All values are inherently either *truthy* or *falsy*. Specifically, `false` and `nil` are *falsy* while all other values are considered *truthy*. Just keep this in mind when using control flow structures, which is what the next section talks about.

## Control flow
---
An important part of any language is a way to modify the behavior of the script based on certain conditions. This is usually called <a href="https://en.wikipedia.org/wiki/Control_flow" target="_blank">control flow</a>, and is essential to making a useful scripting language.

### Code blocks
---
Before I get to things like `if` statements or loops, there is one important thing to define first. Any code wrapped by opening and closing curly braces `{}` is called a *code block*. Code blocks group a bunch of code together. They are usually used with control flow statements and functions, though can also stand alone in a part of a script.

Code blocks also have something called <a href="https://en.wikipedia.org/wiki/Scope_(computer_science)" target="_blank">scope</a>. It is a somewhat complicated subject that I won't go over here, but the rule of thumb is that *what is declared in a code block stays in that code block*. Here's a quick example:
```js
var a = "Hello"
{
  print a // "Hello"

  var b = "world"
  print b // "world"
}
print b // Unknown variable error
```
In this code, `b` is defined inside a code block, and as such it is only available in the *scope* of that code block, which also includes any code blocks nested inside that block but not anything outside of the block.

However, this still works:
```js
var cool_fact = "Bees have 5 eyes"
{
  print cool_fact // "Bees have 5 eyes"

  cool_fact = "The mitochondria is the powerhouse of the cell."
}
print cool_fact // "The mitochondria is the powerhouse of the cell."
```
Changes to an existing variable persist throughout the whole script, not just the code block it is in.

### If statements
---
One common control flow structure BobScript has is the `if` statement. It takes an expression that evaluates to `true` or `false` and executes some code depending on whether or not that expression is `true`.
```js
// Exhibit A
if (9 + 10 == 21) {
  print "you stoopid"
} else {
  print "the prophecy was wrong"
}
// Outputs "the prophecy was wrong"
```
Let's deconstruct what's happening here. First, there is the `if` keyword followed by an expression. This expression has to be wrapped in parentheses `()`. This expression is called the *condition*.

Then, it is followed by a code block. The code block isn't required in this particular example; see below for a slightly more concise way of doing it. Either way, it executes the following statement or the following code block if and only if the condition evaluates to `true`. If it doesn't, then the code after the `else` keyword runs instead.
```js
// Exhibit B
if (9 + 10 == 21) print "you stoopid"
else print "the prophecy was wrong"
```
Either way, it outputs the same thing. Using code blocks like in the first example lets you run multiple bits of code altogether, though the second option works when you only want to do one thing if it is `true` or one thing if it is `false`.

Another example:
```js
var myVar

if (!myVar) print "You forgot to assign a value to myVar!"
```
This works because `myVar` defaults to `nil` since no value was assigned to it, and `nil` is *falsy* as I mentioned earlier.

### While loops
---
A loop is basically some code that repeats itself over and over again. Once it finishes running, it *loops* back around and runs the code again.

The `while` loop keeps looping as long as a certain condition evaluates to `true`.
```js
var counter = 0
while (counter < 5) {
  counter = counter + 1
  print counter
}
/* Outputs the following:
1
2
3
4
5
*/
```
> IMPORTANT: don't do `while(true)`, that's not a good idea.

Let's see another example, one that outputs the first several numbers in the <a href="https://en.wikipedia.org/wiki/Fibonacci_number" target="_blank">Fibonacci Sequence</a>. Basically, it's a sequence of numbers where each one is the sum of the two numbers before it. Utilizing loops makes this possible in a somewhat concise way.
```js
var output = "0, 1, " // Using a string as the output to avoid spamming the print keyword, should make it go faster

var i = 0

var last = 0
var current = 1
var next

while (i <= 20) {
  next = last + current

  output = output + next + ", "
  last = current
  current = next

  i = i + 1 // Don't forget to increment 'i' or the loop goes forever
}

print output
```
> There are much better ways to find numbers in the Fibonacci Sequence, this is just one I put together real quickly. I encourage you to try to find a better way of doing it!

### For loops
---
`while` loops are useful, but they aren't the only type of loop available in BobScript. `for` loops are an alternative option that are good for different uses.

I'll show an example first:
```js
for (var i = 0; i < 10; i = i + 1) {
  print i
}
// Outputs 1-9
```
They are a bit fancy, but let's just see what is happening here. 

1. It starts with the `for` keyword followed by an opening `(`
1. A variable `i` is declared with `var` and set equal to a number, in this case `0`.
1. Semicolon `;`
1. An expression that evaluates to `true` or `false` is provided, similar to the `while` loop. The loop will keep going until this is `false`.
1. Semicolon `;`
1. An iterator is provided, whidh is an expression that modifies the variable declared earlier, increasing it by `1`. You can increase it or decrease it however much you want, it doesn't matter.
1. After the closing `)`, a statement or code block should be provided to execute each time it loops.

You can access `i` at any point inside the loop.

> The variable declared in a `for` loop doesn't have to be called `i`, it's just standard convention to use the letter `i` for it. Maybe because it stands for "iterator"?

```js
print "Initiating launch sequence..."
for (var i = 10; i > 0; i = i - 1) {
  if (i == 10) print "T minus " + i + ","
  else if (i == 6) print "Main engine ignition..."
  else print i + ","
}
print "We have lift off!"
/* Outputs:
Initiating launch sequence...
T-minus 10,
9,
8,
7,
Main engine ignition...
5,
4,
3,
2,
1,
We have lift off!
*/
```

## Functions
---
A function is basically a piece of code that can be reused over and over again. You write it once and can use it multiple times.
```js
fun greet() {
  print "Salutations, fellow human."
}

greet() // Prints "Salutations, fellow human"
```

Let's deconstruct what is happening here real quick
1. The `fun` keyword is used to declare a function, similar to how the `var` keyword is used to declare a variable
1. After that is the name of the function, `greet` followed by a pair of parantheses `()`
1. The body of the function is a code block denoted by curly braces `{}`
1. Inside the function body is the code that runs when the function is *called*.
1. On the last line is the name of the function, `greet`, again followed by parantheses `()`. However, this isn't part of the function declaration, and is actually *calling* that function.

When you *call* a function, you tell it to execute the code contained inside the function body. You can also pass values into a function like so:
```js
var pi = 3.1415926535

// Finds the area of a circle given its radius
fun find_area_of_circle(radius) {
  return pi * (radius ^ 2)
}

print find_area_of_circle(5) // Prints approximately 78.54
print find_area_of_circle() // Error
```

Inside the parantheses `()` of the function declaration, the name of a variable is provided. This variable is then created inside the scope of the function and only the code in the function has access to that particular variable. This variable is called a *parameter*. When the function is later called, an *argument* is provided.

Note the difference between the terms *parameter* and *argument*. It is easy to forget, but a *parameter* is the variable available inside the function and an *argument* is the expression that is passed into the function call.

In the example above, an error is thrown if that *argument* is not provided in the function call. Functions that have arguments always require those arguments to be provided.

You may have also noticed the `return` keyword in the example above. It tells the function to stop right there and not execute any other code in the function body. Instead, it *returns* a value in place of the function call. So in this case, the first print statement wasn't printing the function but was instead printing the result it *returned*.

`return` statements also don't have to return a value. If no value is provided, they return `nil` by default.

Here's another example:
```js
fun check_weather(temperature, rain) {
  if (rain == true) return "Bring a rain coat."

  if (temperature < 30) return "Bring a heavy coat."
  if (temperature < 55) return "Bring a light coat."
  
  return "No coat needed."
}

print check_weather(34, true) // Outputs "Bring a rain coat."
print check_weather(45, false) // Outputs "Bring a light coat."
```
> Yes it's measuring in Fahrenheit, I'm American and I use those units.

This function has two parameters: `temperature` and `rain`, separated by commas.

In the first function call, the temperature is 34 degrees and it is going to rain. In the function body, it checks if it is going to rain. If so, it *returns* `"Bring a rain coat"`. It doesn't execute the rest of the function after it returns out of it, meaning it doesn't even check the temperature.

In the second function call, it's 45 degrees and it isn't raining. The first two `if` statements don't evaluate, so it keeps going until it seems that the temperature is less than 55, which is where it returns `"Bring a light coat"`.

If there was no rain and the temperature was higher than 55, it would have reached the end of the function and returned `"No coat needed."`.

The names of the parameters don't actually matter at all, but I'd recommend naming them something that explains what that parameter means so that it is easier to understand your code.

### First-class functions
---
Functions in BobScript are <a href="https://en.wikipedia.org/wiki/First-class_function" target="_blank">*first-class*</a>, meaning they act like variables and can be passed around like one. 
```js
fun callback(num) {
  print num ^ 2
}

fun big_math_thing(num, func) {
  var result = some_big_calculation_that_takes_a_while_to_complete(num)
  func(result)
}

big_math_thing(57, callback)
```

In this example, a function named `callback()` is defined. It takes one argument, a number, and returns the result of it squared.

The `big_math_thing()` function takes two arguments: `num` and `func`. It calls some function that does some long and difficult calculation and stores the result of that function in the variable `result`. Then, it calls the `func` variable like it's a function, providing `result` as an argument.

At the bottom, `big_math_thing()` is called and provided `57` and the `callback` function as arguments. However: notice how `callback` does **NOT** have any parantheses `()` around it when it is being passed as an argument. If it did have parantheses, it would just call that function instead, but omitting them means it is treated as a variable.

In `big_math_thing()` it then calls the `func()` parameter, which in this case is the `callback()` function since that is what was passed as that argument. This means it takes the result of the really long calculation, squares it and prints it.

## Classes
---
Classes are a somewhat complex subject. The first-class functions I mentioned in the section above are a feature of a *functional* programming style. Classes are part of what is called *Object Oriented Programming*. These two styles of programming each have their benefits and drawbacks, and there are people who will fiercely defend one style and say that the other is garbage. For the sake of flexibility, BobScript doesn't pick a side, and just supports both of them.

Now that that quite side note is out of the way, what even is a class?

First, let me talk about *objects*. Objects are organized structures of information. They are primarily built around *key-value pairs*, which I'll show an exmaple of here:
```json
{
  "username": "john_the_destroyer",
  "age": 304,
  "logged_in": true,
  "profile": "hello i am a human i breathe the air through my nostril"
}
```
> This is not valid BobScript code, it's something called <a href="https://en.wikipedia.org/wiki/JSON">JSON</a>.

In this case, there are 4 key-value pairs: 
```
username  - "john_the_destroyer"
age       - 304
logged_in -> true
profile   - "hello i am a human i breathe the air through my nostril"
```

Let's say you have an *object* called `user` with these key-value pairs.
```js
var user // Some code to get the user goes here

print user.username  // Outputs "john_the_destroyer"
print user.logged_in // true
```

To access a specific value, you provide the *key* that corresponds to that value. Imagine it like looking up something in a dictionary: You look for a specific word and then it gives you that word's definition. Keys can have any *value* assigned to them, similar to variables. 

However, the example above overlooks a key detail: Where do you get `user` from?

The answer is a *class*. A class is sort of a *template* to build an *object*. Classes define different *properties* and *methods* that go on that object. A property is like a variable built into the object, with the name being the key and the value being the, well, value. The example code above is accessing the `username` and `logged_in` properties of that `user` object. 

Methods are similar. They are functions that are built into objects.

Here is an example of a class:
```js
class Car {
  init(model, year) {
    this.model = model
    this.year = year
  }
  drive() {
    print "vroom vroom"
  }
}
```

There is a decent amount to unpack here. First, there is the `class` keyword followed by the name of the class. Class names are uppercase, which isn't a BobScript thing but just standard programming convention. After the name of the class is a pair of curly braces `{}`. Note that despite the braces, this doesn't act like a normal code block.

Inside the class body is a set of methods. You can have a class without methods, but that's usually not very useful. Methods are defined just like normal functions, but without the `fun` keyword (that's not to say that methods aren't fun). They have the name of the method, a set of parantheses `()` optionally containing parameters, and curly braces `{}` for the code blocks of those methods.

However, if you try to call `Car.drive()`, it gives you a error because that method doesn't exist. Why is that? Well, `Car` is not itself an object, just a template to build objects. 

An *instance* of a class is an object that was created following the template that the class defines.
```js
var cool_car = Car("Corvette Stingray", 1970)
print cool_car.year // 1970
```

Instances of classes are created by calling the class like a function. But where do those two arguments above go?

The `init()` method is a special one. `init()` is called behind-the-scenes any time an instance of a class is created. Its parameters are the arguments that you provide in the parantheses `()`. In this case, the `model` and `year` parameters in the `init()` method have the values `"Corvette Stingray"` and `1970` respectively. 

In the `init()` method, the properties `model` and `year` of a variable called `this` are being set using *dot notation*, where you access a specific key with `variable_name.key` and set it like a normal variable with `=`. But what is `this`? It refers to class instance that the method is in.

Let's say we add another method to the `Car` class:
```js
get_specs() {
  return this.year + " " + this.model
}
```

This method accesses those same properties of `this`, which refers to the class instance that method is in. In this case, the method above would return `1970 Corvette Stingray`.

Here is another example:
```js
class Item {
  init(name, price, stock) {
    this.name = name
    this.price = price
    this.stock = stock
  }

  restock(stock) {
    this.stock = this.stock + stock
  }

  sell(amount) {
    this.stock = this.stock - amount
  }

  calculate_price(amount, tax) {
    return (this.price * amount) * tax
  }
}

var burger = Item('Cheeseburger', 2.75, 30)
var chips = Item('Doritos', 0.75, 25)

print burger.stock // 30
burger.sell(3)
print burger.stock // 27

print chips.calculate_price(11, 1.06) // 8.745 dollars
```
> hmmmm yummy chips

In this example, two different instances of `Item` are created: `burger` and `chips`. These two items follow the same *template* (the `Item` class), but they have different names, prices, and stocks. You could create as many instances as you want and they would all be unique individual objects.