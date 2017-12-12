##Object-Oriented programming

Each object is created based on a reference type, either one of the native types discussed in the previous chapter or developer-defined type.

#### 1. Creating Objects （建立对象）

As mentioned in the previous chapter, the simplest way to creat a custom object is to creat a new instance of objects

```

var person = new Object();
person.name = "Nicholas";
person.age = 29;
person.job = "Software Engineer";

person.sayName = function(){
    alert(this.name);
}

```

#### 2.The Factory Pattern(工厂模式)

```
function createPerson(name, age, job){
    var o = new Object();
    o.name = name;
    o.age = age;
    o.job = job;
    o.sayName = function(){
        alert(this.name);
    };
    return 0;
}
var person1 = createPerson("Nicholas", 29, "software Engineer");
var person2 = createPerson("Greg", 27, "Doctor");

```

#### 3.The Constructor Pattern(构建模式)
```
function Person(name, age, job){
    this.name = name;
    this.age = age;
    this.job = job;
    this.sayName = function(){
        alert(this.name);
    };
}

var person1 = new Person("Nicholas", 29, "software Engineer");
var person2 = new Person("Wangjing", 38, "Fron-end-developer");
```

To create w new instance of `Person`, The `new` operator is used. Calling a constructor in this manner essentially caused the following four steps to be taken:

1) Create a new object.
2) Assign the scope of the constructor to the new object(so `this` points to the new object).
3) Execute the code inside the constructor (adds properties to the new object).
4) Return the new object.

```
alert(person1.constructor == Person); // true
alert(person2.constructor == Person); //true

alert(person1 instanceof Object); //true
alert(person2 instanceof Person); //true
alert(person2 instanceof Object); //true
alert(person2 instanceof Person); //true
```

#### 3.Constructors as Functions(构建者作为函数)

The only difference between constructor functions and other functions is the way in which they are called.
Constructors are, after all, just functions that's no special syntax to define a constructor that automatically makes it behave as such.
Any function that is called with the `new` operatoracts as a constructor,whereas any function called without it acts just as you would expect a normal function call to act.

```
// use as a constructor
var person = new Person("Nicholas", 29, "Software Engineer");
person.sayName(); //"Nicholas"

// call as a function
Person("Greg", 27, "Doctor"); //adds to window
window.sayName(); //"Greg"

//call in the scope of another object
var o = new Object();
Person.call(o, "Kris" ,25, "Nurse");
o.sayName();  //"Kris"
```

Example 1 : shows the typical use of a constructor, to creat a new object via the `new` operator.

Example 2: Shows what happens when the `Person()` function is called without the `new` operator. remember that the this object always points to the `Global` object(`window` in web browsers) when a function is called in the global scope.

Example 3: The `Person()` function can also be called within the scope of a particular object using `call()` or `apply()`. In this case, its called in the scope of the object `o`, which then gets assigned all of the properties and the `sayNem()` method.

#### 4.Problems with Constructors(构建者作为函数)
#### 5.The Prototype Pattern
#### 6.Prototypes and the in Operator
#### 7.Alternate Prototype Syntax
#### 8.Dynamic Nature of Prototypes
#### 9.Native Object Prototypes
#### 10.Problems with Prototypes

##Combination Constructor/Prototype Pattern
##Dynamic Prototype Pattern
##Parasitic Constructor Pattern
##Durable Constructor Pattern
##Inheritance
##Prototype Chaining
#### 1.Default Prototypes()
#### 2.Prototype and Instance Relationships
#### 3.Working with Methods
#### 4.Problems with Prototype Chaining
##Constructor Stealing
#### 1.Passing Arguments
#### 2.Problems with Constructor Stealing
##Combination Inheritance
##Prototypal Inheritance
##Parasitic Inheritance
##Parasitic Combination Inheritance


