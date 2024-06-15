,# JS, CSS & HTML   
the more web-dev oriented languages.   
Javascript is a web-based interpreted programming language to make the interactive side of web pages and some mobile application and game development.   
Note : Javascript is not related to Java and HTML & CSS are not required to learn javascript, though it would be helpful.   
Since javascript is web-based. It runs in a browser naturally.
I'll be using google chrome.   
Console.log(*text*) : This is a command to run and output some code and display it in the console   
Window.alert(*text*) : This one kinda also works like console.log() but it doesn't output to the console. it instead makes a pop-up window to notify the user.   
### VARIABLES   
- They are containers for storing data.   
- There are two steps in making a variable; Declaration and assignments   
- To declare a variable, One of three keywords are used.
(var, let, const)   
- for now we will be using var or let to declare   
- to assign something to a variable, the assignment operator ("=", equals-sign) is used.   
- We can make the variable using two steps or in one sentence.   
    two step
//
let age; *declaration*
age = 21 *assignment*
//   
    one step
//
let age = 21; *both of them at the same time*.
//   
   
### DATA TYPES   
Variables store data but this data can be organised and identified in different groups.   
Strings = Unchangeable lines of text in most cases, integers are usually the way that a user can input sentences of words into a program without them being read as code but as “Input”. They are signified by the “” and ‘’.   
Integers : Whole number inputs that the code can interpret and change. Integers have no special identifiers but they must be whole to count as integers. These also contain negatives.   
Floats : Decimal numbers that can be interpret and managed in a computer’s memory. Floats can be positive or negative as long a decimal point is present.   
Booleans : Booleans are either portrayed as True or False. Booleans can also be represented as ones and zeros depending on the language.   
### ARITHEMTIC EXPRESSIONS   
Arithmetic expression are a combination of operands (values, variables, etc.) and operators (+, -, x, /, etc.) that can be evaluated to a value. ex. y = x^2 + 5x.   
Specials   
- += : This operator refers to "Increment". It is quite useful in algorithms to repeatedly mean "+1".   
- -= : "Decrement" operator is the exact opposite of Increment. It is done to represent "-1" in code.   
-  : Exponent is used to represent powers and exponents.   
- % : is used as a division method but instead of returning the whole number integer, it returns the remainder.   
   
Operator precedence : the order in which the equations are solved. The order is ;   
1. parenthesis()   
2. exponents   
3. multiplication & division   
4. addition & subtraction   
   
### USER INPUT   
We will cover two ways to do this :
i. The easy way (browser window prompt).
ii. The hard way (HTML text box).   
```
The easy way :
//
let username = window.prompt("Enter your username : ")
console.log(username) quite easy but not practical
//


```
```
The hard way :
//
<body>
 <label id="label01"> Enter your name : </label><br>
 <input type = "text" id ="text01"><br>
 <button type = "button" id = "button01"></button>
 <script src = "web_02.js"></script>
</body>


```
```
JS section

let username;
document.getElementbyid("button01").onclick = function(){
 username = document.getElemenById("text01").value;
 console.log(username)
 document.getElementById("label01").innerHTML = "Welcome " + username;
}
This method is more practical but alot more difficult.
//


```
### TYPE CONVERSION   
Type conversion refers to changing the data type of any given value. There are keywords mean to change data. *the window prompt input always changes into strings*.   
Number(*String*) : Changes from string to number. Especially useful for the window prompt.   
Boolean(*String*) : a bit complex but it can output true or false. false will be output if the String is empty or if the string is == "false". otherwise, it will output true ex. (Boolean("pizza") is == to true.)*useful in detection of empty prompt inputs*.   
String(*number*, *boolean*) : are use to convert other datatypes into strings. not very useful in the beginner stage.   
Note : There is also the "typeof" method which can be used to output the details on what datatype a value is.   
### CONSTANT   
This is a keyword used to initiate a variable. It defers in the fact that it makes a constant variable (One that cannot be changed.) ex const pi = 3.14159; *we know that pi won't change*   
### MATH   
```
An object that contains many base mathematical functions.

let x = 69.69;
let y = 42;
let z = 15.99;


x = Math.round(x);
console.log(x);


x = Math.floor(x);
console.log(x);


x = Math.ceil(x);
console.log(x);

x = Math.pow(x, 3);
console.log(x);


x = Math.sqrt(x);
console.log(x);


x = Math.abs(x);
console.log(x);


Maximum = Math.max(x, y, z);
console.log(Maximum);


minimum = Math.min(x, y, z);
console.log(minimum);

x = Math.PI;
console.log(x);


```
### STRING PROPERTIES AND METHODS   
```
Methods always start with a ".".

let username = "Jamal"

1. .length() : This method outputs the length of a string. ex
console.log(username.length) = 5).

2. .charAt() : Method that outputs a character in a string at a given index. ex
console.log(username.charAt(0) = "J")

3. .indexOf() : Method that outputs the index of the first occurence of a character. ex
console.log(username.indexOf("a") = 1)always start with 0

4. .trim() : Removes any spaces in a string.
(console.log(username.trim()))

5. .toUpperCase : Changes String to Uppercase.
(console.log(username.toUpperCase()) = "JAMAL")

6. .toLowerCase : Changes String to Lowercase.
(console.log(username.toLowerrCase()) = "jamal")

7. .replaceAll("replacee", "replacer") :
Replaces all specific instances of a character in a string.
console.log(username.replaceAll("a"), "e") = "Jemel"


```
### SLICING   
Slicing is extracting a section of a string and then returning it as a new string without editing or changing the original string.   
```
let fullName = "Derrick Rose";
let firstName ;
let lastName ;

lastName = fullName.slice(0, 7);
firstName = fullName.slice(7);

console.log(lastName);
console.log(firstName);


```
### IF STATEMENTS   
A basic form of decision making. if a condition is true, code "A" runs. Else, code "B" runs instead.   
They resemble the if statements of Java yet javascript and java have no relation other than their similar names.   
```
//

let age = 16 ;

if(age >= 18){
 console.log("you are an adult.")
}
else if (age <= 0){
 console.log("You are unborn.")
}
else{
 console.log("You are underage.")
}
//


```
### SWITCHES   
These are a form of decision making that are more effective than a large number of if statements. They are mainly used when trying to find a match with many combinations.   
```
let grade = "A";

switch(grade){

case "A" :
console.log("You did great");
break;

case "B" :
console.log("You did good");
break;

case "C" :
console.log("You did alright");
break;

case "D" :
console.log("You almost failed");
break;

case "F" :
console.log("You FAILED");
break;

}


```
### LOGICAL OPERATORS   
Logical operators are structures used in a code flow to change and influence decision making in a computer.   
"AND" : And is a logical operator that only allows a result if both its conditions are true, if one is false or unfulfilled, the result won't be produced.   
"OR" : Or is a logical operator that works when one of its conditions is met. When none is met, false is returned.(\|\| is the symbol for "or in JS")   
"NOT" ; Not is used to directly to invert a condition's boolean state and to change code into its opposite counterpart. Not is not very strict with its conditions and is widely very applicable. (! is the symbol for not.)   
### WHILE & DO LOOPS   
While loops are an iterative tool used to repeat something. They are special because "while" a condition is met, they will continue to loop through the code given to it within its curly braces "{}".   
```
let number = 4;

while(number < 10){
 console.log(number);
 number += 1;
}


```
There is also the do/while variation where some code is run and then the code is thus repeated.   
```
do{
 cosole.log(number);
 number+=1;
}while(number < 10);


```
### FOR LOOPS   
For loops are another iterable device used in coding. They allow for iteration and repetition but for a limited amount of time or values. Where as while loops can potentially be infinite, for loops shouldn't. Here is a for loop :   
```
for(let i = 1; i>= 10, i+=1){
 console.log(i)
}


```
A for-loop has three stages separated by ";"(semi-colons) and they include ;   
1. Initialisation : Initialisation is the first part of a for loop that is usually used to initialise a variable. This variable often stores a "counter" which affects he amount of iteration that happens when code is ran. (let i = 0).   
2. Condition : The condition section of a for loop is used to determine when a for-loop while stop for it would have fulfilled it's purpose. (i >= 10)   
3. Statement : This is an optional part of the for loop that runs after the first iteration. It is usually used to advance the loop. (i+=1)   
