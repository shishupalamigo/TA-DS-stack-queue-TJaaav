## Implement Stack

- Linear data structure
- Flexible size
- First in Last out (LIFO)

### Implement Stack using Array to Store Data

Create a class named `Stack` with the following properties and methods:

- While implementing this you can use Array to store data and use any array methods.
- Test the `Stack` class using `Test 1` and `Test 2` given below

The class `Stack` will accept one optional parameter `capacity` using which we can limit the data size. The value of `capacity` will default to `Infinity`.

Properties:

- `storage` use it to store the data for the queue. It should be an array
- `capacity` defaults to `Infinity` if the length is above capacity the item can't be added. Alert a message saying `Stack is overflowing`
- `length` it will return the length of the queue (Getter/Setter)

YOU CAN ADD OTHER PROPERTIES IF YOU NEED.

Methods:

- `add` Adds an element to the stack
- `remove` Removes an element from the stack
- `peek` returns the first element from the top of the stack
- `printAll` print all the elements of the stack from one after another from the top
- `isEmpty` Returns `true` if the stack is empty

```js
class Stack {
  // your code goes here
  constructor(maxSize) {
    if (isNaN(maxSize)) {
      maxSize = 10;
    }
    this.maxSize = maxSize;
    this.container = [];
  }
  display() {
    console.log(this.container);
  }
   get length() {
    return this.container.length;
  }
  isEmpty() {
    return this.container.length === 0;
  }
  isFull() {
    return this.container.length >= this.maxSize;
  }
  add(element) {
    if (this.isFull()) {
      console.log('The Stack is Full');
      return;
    }
    this.container.push(element);
    return this.container.length;
  }
  remove() {
    if (this.isEmpty()) {
      console.log('The Stack is Empty');
      return;
    }
    return this.container.pop();
  }
  peek() {
    if (this.isEmpty()) {
      console.log('The Stack is Empty');
      return;
    }
    return this.container[this.container.length - 1];
  }
}

// Test 1

const stack = new Stack();

stack.add(10);
stack.add(12);
stack.add(120);
stack.add(1);
stack.add(4);

console.log(stack.remove()); // => 4
console.log(stack.length); // => 4
console.log(stack.remove()); // => 1
console.log(stack.length); // => 3

console.log(stack.peek()); // 120

console.log(stack.isEmpty()); // false

console.log(stack.remove()); // => 120

console.log(stack.add(100)); // 3

console.log(stack.peek()); // => 100

console.log(stack.remove()); // => 100
console.log(stack.remove()); // => 12
console.log(stack.remove()); // => 10

console.log(stack.isEmpty()); // true

// Test 2

const stack2 = new Stack(4);

stack2.add(10);
stack2.add(12);
stack2.add(120);
stack2.add(1);
stack2.add(4); // alert Stack is overflowing

console.log(stack2.remove()); // => 1
console.log(stack2.length); // => 3
console.log(stack2.remove()); // => 120
console.log(stack2.length); // => 2

console.log(stack2.peek()); // 12

console.log(stack2.isEmpty()); // false

console.log(stack2.remove()); // => 12

console.log(stack2.add(100)); // 2

console.log(stack2.peek()); // => 100

console.log(stack2.remove()); // => 100
console.log(stack2.remove()); // => 10

console.log(stack2.isEmpty()); // true
```

### Implement Queue using Object to Store Data

Create a class named `Stack` with the following properties and methods:

- While implementing this you can only use an Object to store the data
- Test the `Stack` class using `Test 1` and `Test 2` given below

Properties:

- `storage` use it to store the data for the queue. It should be an object
- `capacity` defaults to `Infinity` if the length is above capacity the item can't be added. Alert a message saying `Queue is overflowing`
- `length` it will return the length of the queue (Getter/Setter)

YOU CAN ADD OTHER PROPERTIES IF YOU NEED.

Methods:

- `add` Adds an element to the stack
- `remove` Removes an element from the stack
- `peek` returns the first element from the top of the stack
- `printAll` print all the elements of the stack from one after another from the top
- `isEmpty` Returns `true` if the stack is empty

```js
class Stack {
  // your code goes here
  constructor(capacity) {
    if (isNaN(capacity)) {
      capacity = Infinity;
    }
    this.store = {};
  }
  get length() {
    return Object.keys(this.store).length;
  }
  add(element) {
    if (Object.keys(this.store).length >= this.capacity) {
      alert(`Stack is overflowing`);
      return;
    }
    this.store[Object.keys(this.store).length] = element;
    return Object.keys(this.store).length;
  }
  remove() {
    let index = Object.keys(this.store).length - 1;
    let elm = this.store[index];
    delete this.store[index];

    return elm;
  }
  peek() {
    return this.store[Object.keys(this.store).length - 1];
  }
  printAll() {
    Object.keys(this.store)
      .sort((a, b) => a - b)
      .forEach((key) => {
        console.log(this.store[key]);
      });
  }
  isEmpty() {
    return Object.keys(this.store).length === 0;
  }
}

// Test 1

const stack = new Stack();

stack.add(10);
stack.add(12);
stack.add(120);
stack.add(1);
stack.add(4);

console.log(stack.remove()); // => 4
console.log(stack.length); // => 4
console.log(stack.remove()); // => 1
console.log(stack.length); // => 3

console.log(stack.peek()); // 120

console.log(stack.isEmpty()); // false

console.log(stack.remove()); // => 120

console.log(stack.add(100)); // 3

console.log(stack.peek()); // => 100

console.log(stack.remove()); // => 100
console.log(stack.remove()); // => 12
console.log(stack.remove()); // => 10

console.log(stack.isEmpty()); // true

// Test 2

const stack2 = new Stack(4);

stack2.add(10);
stack2.add(12);
stack2.add(120);
stack2.add(1);
stack2.add(4); // alert Stack is overflowing

console.log(stack2.remove()); // => 1
console.log(stack2.length); // => 3
console.log(stack2.remove()); // => 120
console.log(stack2.length); // => 2

console.log(stack2.peek()); // 12

console.log(stack2.isEmpty()); // false

console.log(stack2.remove()); // => 12

console.log(stack2.add(100)); // 2

console.log(stack2.peek()); // => 100

console.log(stack2.remove()); // => 100
console.log(stack2.remove()); // => 10

console.log(stack2.isEmpty()); // true
```
