# Javascript_interview_prep

let cleanRoom = () => {
	return new Promise((resolve,reject) => {
		resolve('Cleaned The Room!!');
	});
};

let removeGarbage=(p) => {
	return new Promise((resolve,reject) => {
		resolve('remove Garbage!');
	});
};

let winIcecream=(p) => {
	return new Promise((resolve, reject)=> {
		resolve('won Icecream');
	});
};

cleanRoom().then((res) => {
	console.log(res);
	return removeGarbage(res);
}).then((res) => {
	console.log(res);
	return winIcecream(res);
}).then((res) => {
	console.log(res);
})

/* Closure in Javascript */

passed = 5

const fun=()=> {
	var inner = 3;
	console.log(passed + inner);
}

function outer(){
	var out=5;
 function inner() {
		var ins = 7;
		console.log(out+ins);
	}
	return inner();

}
outer()

/* Java Script Interview Questions*/
//-----------------------------------------
Difference between let and var ?
Let isrecently in Javascript ES6/2015
whereas var is there in JS from the beginning.
variables defined with var gets hoisted where as let has very much limited scope hence prone to undefined errors.

Difference between " ==" and "==="?
They both are comparison operators == compares just the value where as === compares the value as well as type.

Difference between let and const ?
const cannot be reasigned whereas let can.

Difference between null and undefined  ?
undefined implicitly initialize the unintialize.

use of arrow function
----------------------

Use of Callback function
----------------------------
let x = function() {
	console.log("I am called from a inside function!!");
}

let y = function(callback) {
	console.log('Do Something!!');
	callback();
}

y(x);

/**/
let add=(a,b) => a+b;
let sub=(a,b) => a-b;
let calc=function(num1,num2,cb) {
	return cb(num1,num2);
}

calc(5,4,add);
------------------------------------
/* Javascript object creation pattern */

Constructor Pattern 
Factory Pattern 
Prototype Pattern 
Dynamic Prototype Pattern

-------------------------------
 var peopleFactory = function (name, age, state) {
 	var temp={};
 	temp.age=age;
 	temp.name=name;
 	temp.state=state;

 	temp.printPerson= function() {
 		console.log(this.name+ ", "+ this.age+", "+this.state);
 	}
 	return temp;
 };

 var person1=peopleFactory('john',23,'California');
 var person2=peopleFactory('Kie',27,'US');

 person1.printPerson();
 person2.printPerson();

 /*CONSTRUCTOR PATTERN*/
 
var peopleConstructor= function(name, age, state) {
 	this.name=name;
 	this.age=age;
 	this.state=state;

 	this.printPerson= function() {
 		console.log(this.name+ ", "+ this.age+", "+this.state);
 	};
 };

 var person1 = new peopleConstructor("Amit",22,"India");
 var person2= new peopleConstructor("Ankit",22,"India");

 person1.printPerson();
 person2.printPerson();

/*Prototype Pattern */

var peopleProto = function() {

}

peopleProto.prototype.age=0;
peopleProto.prototype.name="no name";
peopleProto.prototype.city="no city";

peopleProto.prototype.printPerson = function () {
	console.log(this.age+" "+this.name+" "+this.city);
};

var person1 = new peopleProto();
person1.age=23
person1.name="Amit"
person1.city="CA"

person1.printPerson();


//In reality, the only true difference between prototype and __proto__ is that the former is a property of a class constructor, while the latter is a property of a class instance.

/*DYNAMIC PROTOTYPE PATTERN*/
var peopledynamicproto = function(name, age, state) {
	this.name=name;
	this.age=age;
	this.state=state;		

	if(typeof this.printPerson !== 'function'){
		peopledynamicproto.prototype.printPerson = function () {
		console.log(this.age+" "+this.name+" "+this.state);
		};
		}
}

var person1 = new peopledynamicproto("Amit","21","California");

person1.printPerson();


