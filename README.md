Call( ), Bind( ), and Apply( ) : 
    We use call, bind and apply methods to set the this keyword independent of how the function is called. This is especially useful for the callbacks.We know that functions are a special kind of objects in JavaScript. So they have access to some methods and properties. 
JavaScript also provides some special methods and properties to every function object. So every function in JavaScript inherits those methods. Call, bind, and apply are some of the methods that every function inherits.

Bind( ):
    The bind method creates a new function and sets the this keyword to the specified object.
    
Syntax:  function.bind(thisArg, optionalArguments)

For example:
Let’s suppose we have two person objects.

const prasad = {
  name: 'Prasad',
  age: 24,
};

const pravin = {
  name: 'Pravin',
  age: 22,
};

Let’s add a greeting function:

function greeting()
{
  console.log(`Hi, I am ${this.name} and I am ${this.age} years old`);
}

We can use the bind method on the greeting function to bind the this keyword to john and jane objects. For example:

const greetingPrasad = greeting.bind(prasad);
  
  greetingPrasad();         // Hi, I am Prasad and I am 24 years old

const greetingPravin = greeting.bind(pravin);
  
  greetingPravin();         // Hi, I am Pravin and I am 22 years old


Here greeting.bind(prasad) creates a new function with this set to john object, which we then assign to greetingPrasad variable. Similarly for greetingPravin.

Call ( ):
The call method sets the this inside the function and immediately executes that function.
The difference between call() and bind() is that the call() sets the this keyword and executes the function immediately and it does not create a new copy of the function, while the bind() creates a copy of that function and sets the this keyword.


Syntax:function.call(thisArg, arg1, agr2, ...)

For example:

function greeting() {
  console.log(`Hi, I am ${this.name} and I am ${this.age} years old`);
}
const john = {
  name: 'John',
  age: 24,
};
const jane = {
  name: 'Jane',
  age: 22,
};

greeting.call(john);     // Hi, I am John and I am 24 years old

greeting.call(jane);     // Hi, I am Jane and I am 22 years old


Call () can also accept arguments
Call() also accepts a comma-separated list of arguments. The general syntax for this is function.call(this, arg1, arg2, ...)

For example:

function greet(greeting) {
  console.log(`${greeting}, I am ${this.name} and I am ${this.age} years old`);
}
const john = {
  name: 'John',
  age: 24,
};
const jane = {
  name: 'Jane',
  age: 22,
};

greet.call(john, 'Hi');   // Hi, I am John and I am 24 years old

greet.call(jane, 'Hello');  // Hello, I am Jane and I am 22 years old


Apply ( ):
The apply() method is similar to call(). The difference is that the apply() method accepts an array of arguments instead of comma separated values.

Syntax: function.apply(thisArg, [argumentsArr])

For example:

function greet(greeting, lang) {
  console.log(`${greeting}, I am ${this.name} and I am ${this.age} years old`);
}
const john = {
  name: 'John',
  age: 24,
};
const jane = {
  name: 'Jane',
  age: 22,
};

greet.apply(john, ['Hi']);     // Hi, I am John and I am 24 years old

greet.apply(jane, ['Hello']);  // Hi, I am Jane and I am 22 years old



Apply vs. Call vs. Bind Examples:

Call:

var person1 = {firstName: 'Jon', lastName: 'Kuperman'};
var person2 = {firstName: 'Kelly', lastName: 'King'};

function say(greeting) {
    console.log(greeting + ' ' + this.firstName + ' ' + this.lastName);
}

say.call(person1, 'Hello'); // Hello Jon Kuperman
say.call(person2, 'Hello'); // Hello Kelly King

Apply:

var person1 = {firstName: 'Jon', lastName: 'Kuperman'};
var person2 = {firstName: 'Kelly', lastName: 'King'};

function say(greeting) {
    console.log(greeting + ' ' + this.firstName + ' ' + this.lastName);
}

say.apply(person1, ['Hello']); // Hello Jon Kuperman
say.apply(person2, ['Hello']); // Hello Kelly King

Bind:

var person1 = {firstName: 'Jon', lastName: 'Kuperman'};
var person2 = {firstName: 'Kelly', lastName: 'King'};

function say() {
    console.log('Hello ' + this.firstName + ' ' + this.lastName);
}

var sayHelloJon = say.bind(person1);
var sayHelloKelly = say.bind(person2);

sayHelloJon(); // Hello Jon Kuperman
sayHelloKelly(); // Hello Kelly King

