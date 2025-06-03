
function Person(name, age) {
  this.name = name;
  this.age = age;
}
Person.prototype.introduce = function() {
  console.log(`Hi, my name is ${this.name} and I am ${this.age} years old.`);
};
function Employee(name, age, jobTitle) {
  Person.call(this, name, age); 
  this.jobTitle = jobTitle;     
}
Employee.prototype = Object.create(Person.prototype);
Employee.prototype.constructor = Employee;
Employee.prototype.work = function() {
  console.log(`${this.name} is working as a ${this.jobTitle}.`);
};

const person1 = new Person("Alice", 30);

const employee1 = new Employee("Bob", 40, "Software Developer")
person1.introduce();    // Hi, my name is Alice and I am 30 years old.
employee1.introduce();  // Hi, my name is Bob and I am 40 years old.

// Call work on the Employee instance
employee1.work();       // Bob is working as a Software Developer.
