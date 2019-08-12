# Generation-between-ES5-AND-ES6
Here is the difference between ES5 and ES6

1. let and const

var in ES5 ==> function-scoped

const,let  ==> block-scoped


```javascript
function driversLicence5(passedTest) {
    
    if (passedTest) {
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
        let firstName = 'John';
        const yearOfBirth = 1990;
    }
    
    
    console.log(firstName + ', born in ' + yearOfBirth + ', is now officially allowed to drive a car.');
}

driversLicence5(true);
```
In ES6, it will shows firstName is not defined. shown error! it will only work in the block.
