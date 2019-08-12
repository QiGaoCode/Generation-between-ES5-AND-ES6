# Generation-between-ES5-AND-ES6
Here is the difference between ES5 and ES6

## 1. let and const

var in ES5 ==> function-scoped

const,let  ==> block-scoped


```javascript
function driversLicence5(passedTest) {
    
    if (passedTest) {
        // function scope
        var firstName = 'John';
        var yearOfBirth = 1990;
    }
    
    
    console.log(firstName + ', born in ' + yearOfBirth + ', is now officially allowed to drive a car.');
}

driversLicence5(true);
```
```javascript
function driversLicence6(passedTest) {
    
    if (passedTest) {
        // block scope
        let firstName = 'John';
        const yearOfBirth = 1990;
    }
    
    
    console.log(firstName + ', born in ' + yearOfBirth + ', is now officially allowed to drive a car.');
}

driversLicence6(true);
```
In ES6, it will shows firstName is not defined. shown error! it will only work in the block.

Then we change to
```javascript
function driversLicence6(passedTest) {
    let firstName;
    const yearOfBirth = 1990;
    if (passedTest) {
        // block scope
        firstName = 'John'
    }
    
    
    console.log(firstName + ', born in ' + yearOfBirth + ', is now officially allowed to drive a car.');
}

driversLicence6(true);
```
Then it works.

In ES6, we can only use the variable only after we actually declare and define it. 


## 2. BLOCK AND IIFEs
To show Data privacy.

ES6
```javascript
{
    const a = 1;
    let b = 2;
    var c = 3;
}

console.log(a + b);  ==> a is not defined, as we cannot access from the block which show the data privacy just like IIFEs
console.log(c);
```

ES5: THE OLD WAY TO USE IIFEs
```javascript
（function(){
    var c = 3;
})();
```

## 3. Strings

```javascript

// ES5
console.log('This is ' + firstName + ' ' + lastName + '. He was born in ' + yearOfBirth + '. Today, he is ' + calcAge(yearOfBirth) + ' years old.');

// ES6 called Template Literals. Instead of using quote, we use backticks (``). and dollar sign $ and curly brackets{}
console.log(`This is ${firstName} ${lastName}. He was born in ${yearOfBirth}. Today, he is ${calcAge(yearOfBirth)} years old.`);

```

### new method for strings
```javascript
//first name johb, last name Smith
const n = `${firstName} ${lastName}`;
console.log(n.startsWith('j'));
console.log(n.endsWith('Sm'));
console.log(n.includes('oh'));
console.log(`${firstName} `.repeat(5)); // output johnjohnjohnjohnjohn
```

## 4. Arrow Functions  => arrow operator
```javascript
const years = [1990, 1965, 1982, 1937];

// ES5
var ages5 = years.map(function(el) {
    return 2016 - el;
});
console.log(ages5); // output [26,51,34,79]


// ES6

let ages6 = years.map(el => 2016 - el); // simplest form with one line of code
console.log(ages6); // output [26,51,34,79]

// example for more than one parameter.
ages6 = years.map((el, index) => `Age element ${index + 1}: ${2016 - el}.`); // Use Template Literals ``
console.log(ages6);  // output ["Age element 1: 26", "Age element 2: 52" ...]

// add more than one lines of code : need brackets and return statement.
ages6 = years.map((el, index) => {
    const now = new Date().getFullYear();
    const age = now - el;
    return `Age element ${index + 1}: ${age}.`
});
console.log(ages6);
```

### Another using of arrow function , this keyword. arrow function do not have a this keyword. they have a lexical this variable.


```javascript
function Person(name) {
    this.name = name;
}

// ES5
Person.prototype.myFriends5 = function(friends) {
    
    var arr = friends.map(function(el) {
       return this.name + ' is friends with ' + el; 
    }.bind(this));
    // bind apply ,call can define the this variable manully.
    
    console.log(arr);
}

var friends = ['Bob', 'Jane', 'Mark'];
new Person('John').myFriends5(friends);


// ES6
Person.prototype.myFriends6 = function(friends) {

    var arr = friends.map(el => `${this.name} is friends with ${el}`);

    console.log(arr);
}

new Person('Mike').myFriends6(friends);
```

## 5. Destructuring

```javascript
// ES5
var john = ['John', 26];
//var name = john[0];
//var age = john[1];


// ES6
// data structure
const [name, age] = ['John', 26];
console.log(name);
console.log(age);


const obj = {
    firstName: 'John',
    lastName: 'Smith'
};

// use object
const {firstName, lastName} = obj;
console.log(firstName);
console.log(lastName);

const {firstName: a, lastName: b} = obj;
console.log(a);
console.log(b);



function calcAgeRetirement(year) {
    const age = new Date().getFullYear() - year;
    return [age, 65 - age];
}


const [age2, retirement] = calcAgeRetirement(1990);
console.log(age2);
console.log(retirement);
```

## 6. Array

```javascript
const boxes = document.querySelectorAll('.box'); // get the node list

//ES5
var boxesArr5 = Array.prototype.slice.call(boxes); // transform to the array
boxesArr5.forEach(function(cur) {
    cur.style.backgroundColor = 'dodgerblue';
});

//ES6
const boxesArr6 = Array.from(boxes);
Array.from(boxes).forEach(cur => cur.style.backgroundColor = 'dodgerblue');


//ES5
for(var i = 0; i < boxesArr5.length; i++) {
    
    if(boxesArr5[i].className === 'box blue') {
        continue;
    }
    
    boxesArr5[i].textContent = 'I changed to blue!';
    
}


//ES6 
for (const cur of boxesArr6) {
    if (cur.className.includes('blue')) {
        continue;
    }
    cur.textContent = 'I changed to blue!';
}




//ES5
var ages = [12, 17, 8, 21, 14, 11];

var full = ages.map(function(cur) {
    return cur >= 18;
});
console.log(full);

console.log(full.indexOf(true));
console.log(ages[full.indexOf(true)]);


//ES6
console.log(ages.findIndex(cur => cur >= 18));
console.log(ages.find(cur => cur >= 18));
*/

```

example of Array.from(boxes)
