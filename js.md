Javascript from basics
======================

After a self training in javascript variable types and basic way to write in js we can begin with simple examples to understand how to perform code in.


for ..in for objects
--------------------

```js
for (var miProp in miObj) {
 // Sample code 
 document.write(miProp, " = ", document[miProp], "<BR>");
 // Recovery all object document property 
}
```

Using with statement
--------------

It is used to code on a easy way with objects. Instead of call method from an object referencing object everytime:

```js
document.write("Title: ", document.title);
document.write("<BR>");
```

It is possible to use this with statement to make code more readable:

```js
with (document) {
    write("Title: ", title);
    write("<BR>");
}
```

Object copies
-------------

When you copy an object both object share memory routes so if we modify one the other is modified too.

```js
var myObject2 = myObject
```

So will be interesting to copy an object like this:

```js
var myObject = new Object("Host1", "192.168.1.1", "Intel    X8300", 4000);
var myObject2 = new Object(myObject.host, myObject.address, myObject.cpu, myObject.ram);
```

Maybe it is possible to add a method to copy object in class.

```js
function copyObject(objTarget) {
    objTarget.host = this.host;
    objTarget.address = this.address;
    objTarget.cpu = this.cpu;
    objTarget.ram = this.ram;
}
```

or using with statement

```js
function copyObject(objTarget) {
    with(objTarget) {
    host = this.host;
    address = this.address;
    cpu = this.cpu;
    ram = this.ram;
    }
}
```

and call method in this way:

```js
var myObject = new Object("Host1", "192.168.1.1", "Intel X8300", 4000);
var myObject2 = new Object();
myObject.copyObject(myObject2);
```

String Object
=============

```js
var myString = "New string";
// or usign single quotes
var myString1 = 'Single quotes string';
// backslash to special characters
var myString2 = "String \"backslash\"";
// String "backslash"
var concatString = myString1 + myString2; 
```

String methods
--------------
--------------

*.length();
-----------

```js
var intLong = "My string size is".length;
// intLong = 16
```

*.charAt(int);
--------------

```js
var strByIndex = "Which my first char is?".charAt(0);
// strByIndex = M
for (var  i = 0; i < strByIndex.lenght; i++) {
        document.write(strByIndex.charAt(i));
}
```

*.charCodeAt(int);
------------------

```js
var ASCICodeCharByIndex = "My string size is".charCodeAt(0);
// ASCICodeCharByIndex = ¿?
for (var i = 0; i < ASCICodeCharByIndex; i++) {
    document.write(ASCICodeCharByIndex.charCodeAt(i) + "-");
}
```

Character codificación
----------------------
----------------------

```xml
<?xml version="1.0" encoding="utf-8">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="es-ES" lang="es">
```

```js
function isValid(string) {
var expreg = new RegExp("^[a-zA-Z ]{1,20}$","g");
if (expreg.test(string)) {
    return string + " is OK";
    } else {
    return string + " is KO";
    }
}
```

```js
var expreg = new RegExp("[0-6][0-9].[0-9]{3}.[0-9]{3}-[A-Z]","g");
var numInString = "A serie of numbers: 33.666.666-W 37.000.000-Z";
document.write("RegExp match ", expreg.exec(numInString));
// 33.666.666-W
nums = numInString.match(/\b[0-6][0-9].[0-9]{3}.[0-9]{3}-[A-Z]\b/g);
 

```
Substring
---------
---------

```js
var str = "This is a text example".substring(1,3);
// str = "hi"
// from position 1 to position 3
var str = "this is a text example".substr(1,2);
// str = "hi"
// 2 characters in position 1
```

String Evaluation
-----------------
-----------------

To execute dynamic code from a string type variable

```js
var numpag = 10;
document.write(eval("numpag"));
var var1 = "numpag";
// no quotes needed
dockument.write(eval(var1)); 
document.write(eval("20+4")); // 24
```