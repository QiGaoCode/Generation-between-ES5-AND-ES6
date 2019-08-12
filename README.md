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

