# Genearl Notes

Type this line to actiavte strict mode ( it improves debugging)\
'use strict'

### variables definition
```
let, const (in ES6)

var (in older versions)
```

### Printing into console
```
| String Template Literals (inline print) | console.log(´My name is ${myFirstName}´) |
| String Template Literals (multiple line)| console.log(´My name is : |
|                                         |    written in two lines´) |
```

### logical operations
```
===    strict equal \
==     equal with conversions \
||     or \
&&    and \
n >= 20 ? console.log("Tr") : console.log("Fa") Ternary operation
```

### Functions
```
// function decleration
function calcAge1(birthYear){
  return 2037 - birthYear;
}

// function expression
const calcAge2 = function(birthYear){
  return 2037 - birthYear;
}

//  use Arrows
const calcAge3 = birthYear => 2037 - birthYear
or for multiline

const calcAge3 = birthYear => {
      const age = 2037 - birthYear;
      return age;
}
```

### For loops
```
for (let i = 0 ;i <= 6; i++)
{
console.log(`This is the ${i}`);
}
```

# Primitive Data Types
string, number , boolean
### type casting
String(a)\
Number(b)
### check type of variable 
```
console.log(typeof var)
```

# Data Structures
### Arrays
```
// Creating array 2 methods 
const year = [1999,2000,2001]
or
const year = new Array(1999,2000,2001)
// Get the length
console.log(year.length);
// appending element to array
year.push(2002)
// Insert element at the beginning
year.unshift(1998)
// remove elements from the end
year.pop()
// remove item from the begining
year.shift()
// get the index of an element
year.indexOf(2000)
// check if an element exists
doesExist = year.includes(2000)
```
### Objects
```
const jonas = {
  firstName: "jonas",
  lastName:  "chris",
  birthYear: 1999,
  friends: ["vahid","arman"],
  calcAge: function()
  {
  return 2037 - this.birthYear;
  }
  calcSalary: function(monthSalary)
  {
  return monthSalary*12;
  }
  calcSpecial: function(salary)
  {
  this.goodSalary = salary*20;
  }
}
// Access data and methods
console.log(jonas.firstName) or console.log(jonas["firstName"])
console.log(jonas.calcAge())
console.log(jonas.calcSalary(3000)) or console.log(jonas["calcSalary"](3000)) 
jonas.calcSpecial();
console.log(jonas.goodSalary);
// objects are copied by reference So by change of one, the copy will be changed as well
To make a new copy use the below command, However if there is an array or another object inside it will be copied again by reference and only the first order will be copied by value :
const myObjectCopy = Object.assign({},myObject);
```

# DOM (Document Object Model) manupulation
DOM methods and properties like Timer, Fetch  are not part of JS and are APIs provided by browsers
there is no need to import them 

### selectors
```
document.querySelector('.message') // select element by class
document.querySelector('#message') // select element by id
// Get content of html element
let txt = document.querySelector('#message').textContent;
// Get the value of an input element (e.g typed bu user)
let value = document.querySelector('#myInput').value;
// button event handler
document.querySelector('#check').addEventListener('click', myFunction())
// change css style 
document.querySelector('.message').style.color = 'red';
```
