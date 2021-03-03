<h1 align=center>----- Links -----</h1>

1. JavaScript.info: https://javascript.info/devtools
2. MDN JavaScript Reference: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference
3. Compatability Tables: https://caniuse.com/

<h1 align=center>----- Fundamentals -----</h1>

## Hello World!
#### The 'script' Tag
The ```<script>``` tag can be used to add JavaScript directly to the html document.

    <script src="/path/to/script1.js"></script>                 //using an absolute path
    <script src="https://something.script.js"></script>         //using url
    <script src="/path/to/script2.js"></script>                 //linking to multiple files

## Code Structure
#### Semicolons
Usually, but not always, a page break will indicate a semicolon (automatic semicolon insertion). However, the following would not produce a semicolon:

    alert(3 +                       //no semicolon is inserted due to ()
    1
    - 23);

Semicolons are also not assumed before square ```[]``` brackets. 

## The Modern Mode, 'use strict'
Inserted at the beginning of a document (or function/object/class) to make the script work the 'modern' way. The devloper console does not use ```use strict``` mode by default. 

## Variables
#### A Variable
Can begin with letters, '$', and '_ '. Cannot contain hyphens. Case matters. Variables are declared with the ```let``` keyword. Multiple variables can be declared on one line:

    let user = "Markus", age = 22, message = "Hi";          //same line declaration
    let user = "Markus"                                     //multiline declaration
        , age = 22,
        , message = "Hi";

#### var vs let
The ```var``` keyword has no block scope. For example, a variable declared in a if-then statement can be called outside that statement if declared with 'var' instead of 'let'.

#### Constants
To declare use ```const``` instead of ```let```. Constants that are known prior to execution should be named in all uppercase, while other constants can be named in camelCase.

## Data Types
#### Numbers
Consists of integers and floats. ```NaN``` represents a computational error caused by a incorrect or an undefined mathematical operation. ```NaN``` is sticky meaning that any further attempts on ```NaN``` will return ```NaN```. ```Infinity``` (or the - version) represent the mathematical Infinity. It is greater than any number.

    alert(1 / 0);                       //Infinity (division by zero)
    alert("not a number" / 2);          //NaN

#### BigInt
The 'number' type cannot represent values greater than 2^(53) - 1 or 9007199254740991. A ```BigInt``` is created by appending a ```n``` to the end of an integer:

    const bitOne = 238477474777474747457577575784n;












    

#### Strings
Strings can use '', "", ``. Backticks have 'extended functionality'. They allow for embeding variables and expressions into a string by wrapping them in ${...}. The expression inside ${...} is evaluated and the result becomes part of the string. 

    let name = "John";
    alert( `Hello, ${name}!` );         //Hello, John
    alert( `the result is ${1 + 2}` );  //the result is 3
In JavaScript there is no char type.
##### Boolean (logical type)
Boolean type has only two values: true, false.
##### The 'undefined' Value
The meaning of undefined is 'value not assigned', as in ```let num;```.

























JavaScript uses two kinds of types: primitive and reference. 
1. Primitive types are stored as simple data types (there are 5): Boolean, Number, String, Null, Undefined. Variables that hold a primitive directly contain the primitive value.
2. Reference types are stored as objects, which are really just references to locations in memory. Variables that hold references hold a pointer to the location in memory where the value is stored.
To identify primitive data types we can use the ```typeof``` operator (exception is ```null```).

    console.log(typeof "Markus");       //'string'
    console.log(typeof 23);             //'number'
    console.log(typeof true);           //'boolean'
    console.log(typeof undefind);       //'undefined'
    console.log(typeof null);           //'object'

    console.log(value === null);        //true or false (best way to determine is a value is null)



### Comparisons
Note the difference between using ```==``` and ```===```. The tripple equals does the comparison of two items without coercing the item to another type, as in:

    console.log("5" == 5);                  //true
    console.log("5" === 5);                 //false
    console.log(undefined == null);         //true
    console.log(undefined === null);        //false


# Functions

///
///

### Arrow Functions








# Constructors
Constructors should be named with a capital first letter and executed only with the 'new' operator. Any function can be used as a constructor (used with new). 
    
    function User(name) {
      this.name = name;
      this.isAdmin = false;
    
    let user = new User("Fred");
When a function is executed with ```new``` it does the following:

1. A new empty object is created and assigned to this.
2. The function body executes. Usually it modifies ```this```, adds new properties to it.
3. The value of ```this``` is returned.

### Return Statement in Constructors
If there is a ```return``` statement and:
1. It is called with an object, then the object is returned instead of this.
2. It is called with a primitive, it is ignored (```this``` is returned).

##### Dereferencing Objects
JavaScript is a garbage-collected language, but it is still good idea to dereference objects with null.

    let object1 = new Object();
    object1 = null;                     //dereference

##### Adding/Removing Properties
    let object1 = new Object();
    let object2 = object1;

    object1.myProp = "Hello";           //property also applies to object2 since both have pointers
                                        //to the same object

### Instantiating Built-in Types
    let items = new Array();
    let now = new Date();
    let error = new Error("Something happened here!");
    let func = new Function("console.log('Hi');");
    let object = new Object();
    let re = new RegExp("\\d+");

### Objects and Literals
A literal is syntax that allows you to define a reference value without explicityly creating an objet, using the ```new``` operator and the object's constructor. Object literals are made up of an identifier string, a colon, and a value, with multiple properties seperated by commas:

    var book = {
        name: "Markus",             //using identifiers
        "year": 1984,               //using strings literals (use if there are to be spaces)
    }

### Function Literals
Creating function using literal form is both easier and less error prone:

    function sq(val) {                                          //literal
        return val * val;
    }

    let sq = new Function("val", "return val * val;");          

# Property Access
Can access using dot notation or bracket notation:

    let array = [];                         //dot notation
    array.push(1);

    let array = [];                         //bracket notation
    array["push"](123);                     //allows for special characters in property names

    let array = [];                         //using variable instead of string literal
    let method = "push";
    array[method](123);

# Identifying Reference Types

    function reflect(value) {
        return value;
    }

    console.log(typeof reflect);            //'function'
    d