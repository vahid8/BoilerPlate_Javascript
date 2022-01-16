# BoilerPlate_Javascript

Type this line to actiavte strict mode ( it improves debugging)\
'use strict'

### Printing into console
```
| String Template Literals (inline print) | console.log(´My name is ${myFirstName}´) |
| String Template Literals (multiple line)| console.log(´My name is : |
|                                         |    written in two lines´) |
```

## Data Types
string, number , boolean
### type casting
String(a)\
Number(b)
### check type of variable 
```
console.log(typeof var)
```


## logical operations
```
===    strict equal \
==     equal with conversions \
||     or \
&&    and \
n >= 20 ? console.log("Tr") : console.log("Fa") Ternary operation
```

## Functions
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
      const age = 2037 - birthYear
}



