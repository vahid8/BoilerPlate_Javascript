

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li><a href="#general-notes">General notes</a></li>    
    <li><a href="#logical-operations">Logical operations</a></li>
    <li><a href="#functions">Functions</a>
      <ul>
        <li><a href="#Function-declaration">Function declaration</a></li>
        <li><a href="#Functions-in-functions">Functions in functions</a></li>
        <li><a href="#Functions-in-objects">Functions in objects</a></li>
        <li><a href="#Bind-applications">Bind application</a></li>
        <li><a href="#Functional-programming">Functional programming</a></li>
        <li><a href="#Notes">Notes</a></li>
      </ul>
    </li>
    <li><a href="#for-loops">For Loops</a></li>
    <li><a href="#data-structures">Data structures</a>
        <ul>
          <li><a href="#Primitive-Data-Types">Primitive Data Types</a>
           <ul>
             <li><a href="#Working-with-primitive-data">Working with primitive data</a></li>
              <li><a href="#String-methods">String methods</a></li>   
              <li><a href="#Math-methods">Math methods</a></li>   
           </ul>       
          </li>          
          <li><a href="#Non-Primitive-built-in-Data-Types">Non-Primitive-built-in Data Types</a>
            <ul>
              <li><a href="#Arrays">Arrays</a></li>
              <li><a href="#Sets">Sets</a></li>
              <li><a href="#Objects">Objects</a></li>
              <li><a href="#Maps">Maps</a></li>
            </ul>              
          </li>
        </ul>  
    </li>    
    <li><a href="#working-with-data">Working with data</a>
      <ul>
        <li><a href="#Switching-variables">Switching variables</a></li>
        <li><a href="#Deconstructing-array">Deconstructing array</a></li>
        <li><a href="#Deconstructing-objects">Deconstructing objects</a></li>
        <li><a href="#Maps">Maps</a></li>
        <li><a href="#...-Operator">... Operator</a></li>          
        <li><a href="#Rest">Rest</a></li>
        <li><a href="#Optional-chaining">Optional chaining</a></li>
        <li><a href="#Find-method">Find method</a></li>
        <li><a href="#Some-method">Some method</a></li>
        <li><a href="#Flat-method">Flat method</a></li>
        <li><a href="#sort-method">Sort method</a></li>
        <li><a href="#Array-from">Array from</a></li>
      </ul> 
    </li>    
    <li><a href="#Dates">Dates</a></li>
    <li><a href="#DOM-manupulation">DOM manupulation</a>
      <ul>
        <li><a href="#Selectors">Selectors</a></li>       
      </ul>    
    </li>    
  </ol>
</details>



<!-- General Notes -->
## General notes

'use strict' :Type this line to actiavte strict mode ( it improves debugging)   
boxing concept: using () around primitives will convert them to objects so we can apply methods on them e.g (2.7356).ToFixed(2)   

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

<!-- Logical Operations -->
## Logical Operations

### Operators
| Operator | Description |
| --- | --- |
===   | strict equal |
==    | equal with conversions |
''    | or |
&&    | and |

Logical operators use Any data type, return Any data type

### Short-circuitting    
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

<!-- Functions -->
## Functions
### Functions declaration
Different methods of function decleration
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

- functions will not change the primitive values    
- objects will be changed via passing into functions    
- There is no passing by value or refrence concept in javascript. Everything is passed by value.    
- functions are just another type of objects    
- functions have also properties and methods e,g myFunction.name  -> it will return name of the function    
- First order functions: javascript treat functions as first-class citizens    
- Higher ordewr functions: A function that recieves another function as an argument, that return a new function or both   
- addEventListener are higher order functions.    

### Functions in functions
These are called also higher order functions
```
const greet = function (greeting) {
    return function (name) {
        console.log('${greeting} ${name}`);
    };
};

const greeterHey = greet('Hey');
greeterHey('Jonas');
//or
great('Hello')('Jonas');
```

### Functions in objects
1 - use the function directly for the current object
```
lufthansaBooking = {
    airline: "Luftansa",
    iataCode: "LF",
    bookings: [],
    function book(flightNum, name){
        booking.push(`${name} has booked the flight ${name}
        in the ${this.airline}.`);
    }
}

lufthansaBooking.book(583, "vahid");
```
2 - use the function from one object for another object (apply or call)
```
const swiss = {
    airline: "swiss air lines",
    iataCode: "LX",
    bookings: [],
}
const book = lufthansaBooking.book
book.call(swiss, 583, "vahid"); // swiss object will be used in phrases with this
// or
const flightData = [583, "Vahid"];
book.apply(swiss, flightData);
// or
book.call(swiss, ...flightData)
```
3 - copy the function from one object to another (bind)   
you can use the function directly after binding   
```
const bookEw = book.bind(swiss);
bookEW(23,"vahid")
// or specify even paramters
const bookEw = book.bind(swiss, 23);
bookEW("vahid");
```
### Bind applications
1 - bind in addEventListener -> why ? because the listner will pass the selected class (btn) as the object (to be used for this keyword) to the function   
// To pass our own object we need to use bind   
document.querySelector('.buy').addEventListener('click', Luftansa.buyPlane.bind(Luftansa))    

2 - use bind for partial application    
```
const addTax = (rate, value) => value + value * rate;   
const.log(addTax(0.1, 200))   

// fix the rate value and use the new function
const addVAT = addTax.bind(null, 0.23); // bind needs an object to pass as the first arg
console.log(addVAT(200));

// solving the above using functions in functions
const addTaxRate = function(rate){
    return function(value){
        return value + value * rate;
    }
}

const addVAT2 = addTaxRate(0.23);
console.log(addVAT2(200));
```
### Functional programming
// Map filter and reduce create a new array but forEach will not create   
```
const mySecondArray = myArray.map(function(item){return item *10})
or 
const mySecondArray = myArray.map(item => item *10)

const mySecondArray = myArray.filter(function(item){return item > 0 });
or 
const mySecondArray = myArray.filter(item => item > 0 );

const balance = myArray.reduce(function(accumulator, curr, i, arr){return accumulator + curr;}, 0); // last 0 is the initial value of the accumulator
```

### Notes
```
// run a function only once , it accepts no input since it is medant to run only once
// But it can use the global variables
(()=> console.log("im here"))()

//closures
we attached to the function, exactly as it was at the time and place the function was created.
console.dir(booker); // to see the closures (available variables)
```

<!-- For Loops -->
## For loops

```
for (let i = 0 ;i <= 6; i++)
{
console.log(`This is the ${i}`);
}
for (const item of myArray){}
for (const [num, item] of myArray.entries(){}
// loop over objects
const resturants = {
fri: {openning: 8 , close: 10},
sat: {openning: 9 , close: 11}
}
for (const key of Object.keys(resturants)){}
for (const value of Object.values(resturants){}
for (const [key, value] of Objects.entries(resturants){}
for (const [key, {opening_hour, closing_hour}] in Objects.entries(resturants){}

```
<!-- Data Structures -->
## Data Structures

### Primitive Data Types
string, number , boolean
#### type casting
String(a)\
Number(b)


#### Working with primitive data
```
console.log(typeof var) \\ check type of data
numbers are saved as binary base
console.log(0.1 +0.2) // result 0.30000000000000004
convert string to number  
Number('23')
or 
+'23'
//parsing
Number.parseInt('30px') // result  30
Number.parseFloat('2.5rem') // result 2.5
// Numeric Seperator
const diameter = 287_460_000_000; //increase code redaibily (javascript skip _ sign)
// BigInt
maximum number that javascript can handle is 2**53 -1 
if you have bigger numbers use BigInt(theNumebr) or theNumbern syntax

//check if value is Nan
Number.isNan(20) //false
Number.isNan('20') //false
Number.isNan(+'20X) //true

//Checking if value is number
Number.isFinite(20) //true
Number.isFinite('20') //false
Number.isFinite(+'20X) //false
Number.isFinite(23/0) //false
```

#### String methods
| Command | Description |
| --- | --- |
| const airline = 'A323 portugal airlines' |  Creating a string  |
| airline.indexOf("p") |  find all the occurance of a letter  |
| airline.lastIndexOf("p") |find the last occurance of a letter|
| airline.slice(5) | result will be portugal airlines|
| airline.slice(5, 13) | result will be portugal|
| airline.toLowerCase() | --- |
| airline.toUppercase() | --- |
| airline.trim() | rermove spaces from the string |
| airline.replace("p", "q") | replace first p with q |
| airline.replace(/p/g, 'q') | replace all occurance of p with q using regular expressions |
| airline.split(" ") | split the string|
| ["I", "am", "here"].join(" ") | --- |
| airline.includes('portugal') | returns Boolean
| airline.startsWith('A32') | returns Boolean
| airline.endWidth('portugal') | returns Boolean
| padEnd() and padStart() , ... | Other methods are available as well |

#### Math methods
| Command | Description |
| --- | --- |
| Math.sqrt() | --- |
| Math.max(5,18,23,'45') | result 45 |
| Math.min() | --- |
| Math.PI | --- |
| Math.random() | create random between 0 and 1 |
| Math.trunc() | remove the decimal part |
| Math.round() | round to the closest Int |
| Math.ceil() | round to the upper Int |
| Math.floor() | round to the lower Int |
| (2.73456).toFixed(2) | round up to 2 decimal returns a string |


### Non-Primitive-built-in Data Types
#### Arrays
| Command | Description |
| --- | --- |
| const year = [1999,2000,2001] |  Creating array  method 1  |
| const year = new Array(1999,2000,2001) |  Creating array  method 2  |
| const year = new Array(7) |  create an empty array with 7 elements |
|  x.fill(1) | fill the empty array with 1 |
| console.log(year.length); | Get the length |
| year.push(2002); | appending element to array |
| year.unshift(1998); | Insert element at the beginning |
| year.pop(); | remove elements from the end |
| year.shift() | remove item from the begining |
| year.indexOf(2000); | get the index of an element |
| doesExist = year.includes(2000); | check if an element exists |

Array methods
```
let arr = ["a", "b", "c", "d", "e"];
arr.slice(2) // will rerturn a new array (copy) with (["c","d","e"])
arr.slice(2,4);
arr.slice(-1);
arr.slice() //create a shallow copy of the array or using ... operator [...arr]

//splice is the same as slice but it changes the original array instead of creating a copy

arr.reverse() // it mutate (change) the original array
arr.concat(arr2) or [..arr, ..arr2]

att[0] or arr.at(0)
last element 
arr[arr.length-1];
arr.slice(-1)[0]; // cerate a copy of last element
arr.at(-1);
at method also works on strings
```


#### Sets
```
const mySet = new Set([1,2,3,4])
conolse log(mySet.size) // Get the length of the set
console.log(mySet.has(3)) // Check if an element exists in a set
mySet.add(6) // add an element to a set
mySet.delete(4) // delete an element
mySet.clear() // delete all elements inside a set
// There is no way to access elements in a set in Javascript
// They are iterable like arrays
console.log(new Set('jonassmandias').size) // to see how many uniq letters are in a string
```


#### Objects
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
#### Maps
// They are like objects but the keys can be also non strings.    
const restourants = new Map().    
restourants.set('name', 'Alfred') // adding new key value pair to the map.    
restourants.set('openning', 8).set('closing', 10) // adding multiple in one line.     
// Create a new map at once:    
```
const resturants = new Map([ 
['question', 'what is the best programming language ?'],
[1, 'C'],
[2, 'Java'],
[3, 'JavaScript'],
['correct', 3],
['true', 'correct ...'],
['false', 'try again'],
])
```
resturants.get('name') // get the value of a key.     
resturants.has('name') // check if a key exists.    
resturants.delete('name') // delete a key value pair.     
resturants.clear() // remove all elements from Map.     
resturants.size // get the length of key value pairs.     

// Iterate over it and print only if it is a question 
```
for(const [key, value] of question){        
if (tytpeof key === 'number') console.log(`Answer ${key}: ${value}`);   
}  
```
// Convert map to an array
```
console.log([...resturants]);      
console.log(resturants.entries());       
console.log(...resturants.keys());    
console.log(...resturants.values());     
```


<!-- Working with data -->
## Working with data

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

### ... Operator  (spread operator)
It is similar to * operators for lists in python and is used here for arrays
Use cases :
1- print -> console.log(...myArray)
2. Create shallow copy (copy by value) -> newArray = [...myArray]
3. create shallow copy of objects -> const newResturant = {...restuarnt}
4. merging two arrays
// it can be used for all iterables : arrays, strings, set, maps

### Rest 
const (a, b, ...restArray) = [2, 3, 4, 5, 6, 7] // restArray will be = [4, 5, 6, 7]
it Also works for objects -> const {ab, ...restObjects} = resturants
it cna be used for functions -> So we can have arbitray number of input variables

```
const upperFirstWord = function (str) {
    const [first, ...others] = str.split(' ');
    return [first.toUppercase(), ...others].join(' ');
}
```

#### Optional chaining
to prevent error if an object dosent have a property, data or method inside
console.log(resturants.openningHours?.mon?.open) // returns undefined if the open variable is not defined on mon
console.log(resturants.order?.(0,1)) // returns the result if the method exists otherwise returns None

#### Find method
- find or findIndex works similar but the latter gives the index isntead of value
```
const firstWithdrawal = myArray.find(item => item <0 )    
// It finds the first negative elenment and return the value
or searching in objects (usefull for logins)
const account = accounts.find(acc => acc.owner === 'Jessica Davis')
```
#### Some method
```
some (is there any) and every method (are all elements)
it return Booleans
console.log(myArray.some(item => item > 0)); return true if at least 1 positive value exist
console.log(myArray.every(item => item > 0)); return true if all elements are positive value
```

#### Flat method
```
// flat and flatMap to handle nested Arrays
myArray.flat(); //like np.flatten() only goes one level depth array of Arrays
myArray.flat(2); // it will flat till 2 levels [[[]]]

flatMap combines the map and flta -> do the mapping at do the flat at the end
accounts.flatMap(acc => acc.movements)
```

#### Sort method
```
myArray.sort() // it sorts the array based on strings
//for sorting umbers we need to define the rule in a cvallback function
myArray.sort((a,b) => {
    if (a > b) return 1;
    if (b > a) return -1;
})
```
#### Array from
```
// create Array from others method
const y = Array.from({length: 7}, () => 1); using call back to create and fill the elem,ents at one step
const z = Array.from({length: 7}, (_,i) => i+1); //will create [1,2,3,4,5,6,7]

// get all values from ui into arrows
labelBalance.addEventListener('click', function () {
    const myArray = Array.from(
        document.querySelectorAll('.movements_value'),
        item => Number(item.textContent)  Do the mapping for each element to convert them to Number
    )
})
```

<!-- Dates -->
## Dates
### Create Dates
| Command | Description |
| --- | --- |
| const now = new Date() | get current dates |
| new Date ('Aug 02 2020 18:05:41') | create from known string date |
| new Date ('December 24, 2015') | Another way to create |
| new Date(2022, 10, 19, 15, 23) | Thu Nov 19 2037 15:23:00 // month are zero based -> dec = 11 |

### Extract data from Date object
| Command | Description |
| --- | --- |
| myTime.getFullYear() | get the year |
| myTime.getMonth() | get the montgh |
| myTime.getDate() | get the day of month |
| myTime.getDay() | get the day of week |
| myTime.getHours() | get hour |
| myTime.getMinutes() | get minute |
| myTime.getSeconds() | get second |
| myTime.toISOString() | convert to international format |
| const timePassed = myTime.getTime() | time passed from myTime in mili second |
| new Date(timePassed) | convert from milisecond to Date format |

### change Date object
For all above methodes there is a set method as well e.g:     
myTime.setFullYear(2023) // set the year to 2023

### Date operations
convert the Date to Number (result will be in millisecond) and do the operations and convert the result back to Date format




<!-- DOM manupulation -->
## DOM (Document Object Model) manupulation

DOM methods and properties like Timer, Fetch  are not part of JS and are APIs provided by browsers
there is no need to import them 

### Selectors
| Command | Description |
| --- | --- |
| document.querySelector('.message') | select element by class|
| document.querySelector('#message') |  select element by id |
| let txt = document.querySelector('#message').textContent; |  Get content of html element |
| let value = document.querySelector('#myInput').value; | Get the value of an input element (e.g typed bu user) |
| document.querySelector('#check').addEventListener('click', myFunction()) |  button event handler |
| document.querySelector('.message').style.color = 'red'; | change css style |


- DOM add elements
```
myClassContainer.innerHTML = ''; //empty all txts
const myContent = '<div class ="movement_row">
                    im here with ${myVariable}
                    </div>'

myClassContainer.insertAdjacentHTML('afterbegin', myContent) //add the new content to the innerHTML
```

- DOM addEventListener
```
btnLogin.addEventListener('click', function(e)){
    //prevent form from submitting ( refreshing the page)
    e.preventDefault();
}
```

