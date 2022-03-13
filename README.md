# Genearl Notes

Type this line to actiavte strict mode ( it improves debugging)\
'use strict'

### variables definition
```
let, const (in ES6)

var (in older versions)
```

### Printing into console
| Description | Command |
| --- | --- |
| String Template Literals (inline print) | console.log(´My name is ${myFirstName}´) |
| String Template Literals (multiple line)| console.log(´My name is : |
|                                         |    written in two lines´) |

### logical operations
| Operator | Description |
| --- | --- |
===   | strict equal 
==    | equal with conversions 
||    | or 
&&    | and 
Logical operators use Any data type, return Any data type
// Short-circuitting
console.log(3 || 'Jonas') -> result is 3 -> it retuns the first true value
it can be used instead of ternary operator as well e.g const geust = resturant.geustNym || 10 

console.log(3 && 'Jonas') -> result is 'Jonas -> it retuns the last true value if all are ture otherwise the first false value

// 0, '', null, undefined are falsi values but if we need to have 0, '' as true values we need to use ?? (it includes only
Nullish (null and undefined) as falsi values)
const a =  0 || 10 // result in a= 10 becasue 0 is treated as falsi
const a = 0 ?? 10 // result in 0

// use logical operator in another way
a ||= 10 // it keeps a if it is a truely value otherwise set it to 10
a ??= 10 



### Ternary operator

n >= 20 ? console.log("Tr") : console.log("Fa") Ternary operation


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
for (const item of myArray){}
for (const [num, item] of myArray.entries(){}
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
| Command | Description |
| --- | --- |
| const year = [1999,2000,2001] |  Creating array  method 1  |
| const year = new Array(1999,2000,2001) |  Creating array  method 2  |
| console.log(year.length); | Get the length |
| year.push(2002); | appending element to array |
| year.unshift(1998); | Insert element at the beginning |
| year.pop(); | remove elements from the end |
| year.shift() | remove item from the begining |
| year.indexOf(2000); | get the index of an element |
| doesExist = year.includes(2000); | check if an element exists |


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
### Switching variables
```
[a, b] = [b, a]
```

### Deconstructing array

```
const arr = ['apple', 'orrange', 'benana', 'Avocado']
const [x, ,z] = arr // result will be x = 'apple', z = 'benana'

const [i, [j,k]] = ['apple', ['orrange', 'benana']]

// To get multiple retuns from a function 
const [x, y, z] = solveProblem(theInput)

// Set Default Values
const [x=2, y=2, z=2] = [8, 9] // here z will be equal to 2 

```


### Deconstructing objects

```
resturant = {openningHours: '2-10', Menue: ['Hamburger', 'Pizza'], prices : {Hamburger: '10_euro', Pizza: '12_euro'}}
const {openningHours, Menue, prices} = resturant  // with the original name
const {openningHours: op, Menue: me, prices: cost} = resturant  // assigning new names original name
const {openningHours: op = '12-9', Menue: me = [], prices = []} = resturant  // assigning default value in case one parameters is not defined in the original object -> usefull in objects when passing objects instead of one by one parameters
const {prices:{Hamburger, Pizza}} // nested objects deconstruction
console.log(Hamburger, pizza)

// mutating variables ( if you want to assign a predefined variable you need parantesis other wise you get error)
let a = 2
let b = c
const obj = {a = 23, b = 34, c = 45};
({a,b} = obj )

// use deconstruction directly in function and thenn you can pass the variables as an object and the order doesnt matter
function({openningHours, Menue=[]}){}

```


# DOM (Document Object Model) manupulation
DOM methods and properties like Timer, Fetch  are not part of JS and are APIs provided by browsers
there is no need to import them 

### selectors
| Command | Description |
| --- | --- |
| document.querySelector('.message') | select element by class|
| document.querySelector('#message') |  select element by id |
| let txt = document.querySelector('#message').textContent; |  Get content of html element |
| let value = document.querySelector('#myInput').value; | Get the value of an input element (e.g typed bu user) |
| document.querySelector('#check').addEventListener('click', myFunction()) |  button event handler |
| document.querySelector('.message').style.color = 'red'; | change css style |
| --- | --- |

### ... operator 
It is similar to * operators for lists in python and is used here for arrays
Use cases :
1- print -> console.log(...myArray)
2. Create shallow copy (copy by value) -> newArray = [...myArray]
3. create shallow copy of objects -> const newResturant = {...restuarnt}
4. merging two arrays
// it can be used for all iterables : arrays, strings, set, maps

### Rest sintax

const (a, b, ...restArray) = [2, 3, 4, 5, 6, 7] // restArray will be = [4, 5, 6, 7]
it Also works for objects -> const {ab, ...restObjects} = resturants
it cna be used for functions -> So we can have arbitray number of input variables
