# BaseNumber
A library that allows you to work with numbers in different bases from 2 to 36.

## Create a BaseNumber object:
```JavaScript
const dec = new BaseNumber(10, 10);  // new BaseNumber(number, base);

const hex = new BaseNumber("f2", 16);
```
BaseNumber.js works with decimal base numers by default, so you can omit the base argument:
```JavaScript
const dec = new BaseNumber(10);
```
### Obtain number value
Since BaseNumber allows user to create up to base 36 number, number value is an string that may contain letters and numbers:
```JavaScript
dec.value();  // returns "10"
hex.value();  // returns "f2"
```
### Obtain number base
Number base is save as an integer
```JavaScript
dec.base();   // returns 10
hex.base();   // returns 16
```
## Modify number instance
Once a BaseNumber object is created, you can modify it dynamically:
### Modify value
The `newValue` method allows user to modify the value of an instance. It takes two parameters, second is optional, and returns the old instance:
```JavaScript
dec.newValue(number[, base]);
```
The `number` argument can be either a string/float variable or another BaseNumber instance. In case it´s a BaseNumber instance, `base` parameter would be equal to the number instance's `base`. E.g:
```JavaScript
dec.newValue(hex);  // base argument is by default hex.base()

// Now 'dec' is a copy of 'hex' instance (same value and same base)
```
In case number argument is a string/float variable, the `base` parameter would be equal to the **instance base** by default, unless you specify it:
```JavaScript
dec.newValue(5);  // base argument is by default dec.base()

// New value is 5 in base 10
```
Also you can get the old instance as a return value:
```JavaScript
const dec = new BaseNumber(10);

const oldValue = dec.newValue(5);  // base argument is by default dec.base()

console.log(oldValue.value());   //  prints "10"
```
## Simple Math Operations
BaseNumber allows you to make some simple math operations with normal variables or another BaseNumber instance. Although following examples show only integer numbers, *all math operation are also available for float numbers*:
### Addition
The addition method takes three arguments, two of them optional:
```JavaScript
dec.add(number[, base[, resultBase]]);
```
The `number` argument can be either a string/float variable or another BaseNumber instance. In case it´s a BaseNumber instance, `base` parameter would be equal to the number instance's `base`. E.g:
```JavaScript
dec.add(hex);  // base argument is by default hex.base()
```
In case number argument is a string/float variable, the `base` parameter would be **10** by default, unless you specify it:
```JavaScript
dec.add(77);     // Base by default is 10 

dec.add(77, 8);  // Base is 8
```
Last argument `resultBase` specify the base in which the result will be parsed.
```JavaScript
const dec1 = new BaseNumber(10);
const dec2 = new BaseNumber(5);

dec1.add(dec2);   // returns "15"

dec1.add(dec2, null, 16);   // returns "f"

/* Notice that the null parameter in base doesn´t affect the
   result since dec2 is a BaseNumber instance with its own base */
```
For string/float:
```JavaScript
const dec = new BaseNumber(10);

dec.add(5);   // returns "15"

dec.add(5, 10, 16);   // returns "f"

/* Notice that when using the resultBase argument
   you need to specify base since you are not using
   a BaseNumber instance */
```
The remaining Math operations works exactly the same:
### Subtract
```JavaScript
const dec = new BaseNumber(10);

dec.subtract(5);   // returns "5"

dec.subtract(5, 10, 16);   // returns "5"
```
### Multiply
```JavaScript
const dec = new BaseNumber(10);

dec.multiply(5);   // returns "50"

dec.multiply(5, 10, 16);   // returns "32"
```
### Divide
```JavaScript
const dec = new BaseNumber(10);

dec.divide(5);   // returns "2"

dec.divide(5, 10, 16);   // returns "2"
```




