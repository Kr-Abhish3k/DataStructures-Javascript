# DataStructures-Javascript

Implementation of few most used DS in JS

## What is a data structure

A data structure is a way to store and organize data so that it can be used efficiently.
A data structure is a collection of data values, the relationships among them, and the functions or operations that can be applied to that data.

_Why to learan Data Strucutres?_
Every application that we build needs to model data in a certain way. To efficiently manage the data, we need data structure. Imagine walking into a library where books are just kept in aa random order, with no sorting and grouping of the books. It would take hours for us to find a particular book. It would waste a lot of time and we might not step in the same place ever again.
A similar approach comes in play when we strucutre our code as well. The difference between a function taking miliseconds vs a few minutes comes down to the selection of right data structure.
Data structures help us solve problems in a more efficient way both in terms of time and memory.
Learning about data structures also help us gain a more profound understanding of things we're already aware of.

Data structure are everywhere. For example:

- DOM : Tree data structure
- Browser back and forward button : stack data structure
- OS job scheduling : Queue data structure

## Data Structures in Javascript

Built in Data Structures in Javascript

- Arrays
- Maps
- Objects
- Sets

Custom Data Structures

- Stacks
- Queues
- Circular Queues
- Linked Lists
- Hash Tables
- Trees
- Graphs

## Built in Data Structures in Javascript

### Arrays

**CHARACTERISTICS**  
An array is a data structure is a data structure that can hold clooection of values.  
Array can contain a mix of different data types. We can store strings, booleans, numbers or even objects all in the same array.  
Arrays are resizable. We don't have to declar ethe size of an array before creating it.  
Javascript arrays are zero-indexed and the insertion order is maintained.  
Arrays are iterables. They can be used with a for loop.

```js
const arr = [1, 2, 3, "four"];

// to add element at end of array
arr.push("five");
// to remove from end of array
arr.pop();

// to add at begining
arr.unshift("zero");
// to remove from begining
arr.shift();

//To iterate over the array
for (const item of arr) {
  console.log(item);
}
```

**Other Common Array Methods**

- map: creates a new array populated with the results of calling a function on every element in the calling array.
- filter: creates a **shallow copy** of a portion of a given array, filtered down to the elements from the given array that pass the test implemented by the provided function.
- reduce: executes a user-supplied "reducer" callback function on each element of the array, in order, passing in the return value from the calculation on the preceding element. The final result of running the reducer across all elements of the array is a single value.
- concat: used to merge two or more arrays. This method does not change the existing arrays, but instead returns a new array.
- slice: returns a shallow copy of a portion of an array into a new array object selected from start to end (end not included) where start and end represent the index of items in that array.
- splice: It changes the contents of an array by removing or replacing existing elements and/or adding new elements in place.

#### Big-O Time Complexity

When it comes to arrays we need to keep in mind that it is very important to maintain the appropriate index anytime we perform an operation, and we need to consider it in calculating time complexity.  
If we insert or remove from end if an array, the time complexity is constant - O(1)

However if we insert or remove from begining of the array , the time complexity is linear - O(n)  
This is because the index has to be reset for every element in the array.

Accessing an element - O(1)  
Searching an element - O(n)

Based on above complexitites, we can derive the time complexities of other operations.
Push / Pop - O(1)  
shift/unshift/slice/splice/concat - O(n)
forEach/map/filter/reduce - O(n)

If we are using a map method on an array and the callback function also has an for loop inside it, the time complexity in such cases will be quadritic.

### Objects

**CHARACTERISTICS**

- An object id an un-ordered collection of key-value pairs. The key must either be a string or symbol data type where as the value can be of any data type.
- To retrive a value, you can use the corresponding key. This can be achieved using the dot notation or bracket notation.
- An object is not iterable. We cannot use it with for-of loop.

```js
const obj = {
  name: "Bruce Lee",
  speciality: "Martial Arts",
};
//to access
console.log(obj);
console.log(obj.name);
console.log(obj["speciality"]);

// to add
obj.age = 35;
obj["country"] = "China";
console.log(obj);

//to delete
delete obj.country;

// add functions as values
obj.greet = function () {
  console.log(this.name);
};

obj.greet();
```

**Other Common Object Methods**

- keys: returns an array whose elements are strings corresponding to the enumerable string-keyed property names found directly upon object.
- values: returns an array whose elements are values of enumerable string-keyed properties found directly upon object.
- entries: returns an array whose elements are arrays corresponding to the enumerable string-keyed property key-value pairs found directly upon object.

#### Big-O Time Complexity

Insert - O(1)  
Remove - O(1)  
Access - O(1)  
Search - O(n)  
Object.keys()/Object.values()/Object.entries()- O(n)

### Set

**CHARACTERISTICS**

- A set is a data structure that can hold a collection of values. The values however must be unique.
- Set can contain a mix of different data types. We can store strings, booleans, numbers or even objects all in the same sets.
- Sets are dynamically sized. We don't have to declare the size of a set before creating it.
- Sets do not maintain insertion order.
- Sets are iterables. They can be used with a for-of loop.

#### SETS vs ARRAY

- Arrays can contain duplicate values whereas sets cannot.
- Insertion order is maintained in arrays but it is not the case with sets.
- Searching and deleting an element in the set is faster compared to arrays.

```js
const set = new Set([1, 2, 3, 4, 6]);

console.log(set);

//to add
set.add(5);

//to delete
set.delete(4);

//to check if the set has a value
console.log(set.has(3));

//to get the size of the set
console.log(set.size);

//to get all the values in the set
console.log("values : ", set.values());

//to get all the keys in the set
console.log("keys : ", set.keys());

// to access each
for (const item of set) {
  console.log(item);
}

// to delete all values in set
set.clear();
console.log(set.size);
```

### Map

**CHARACTERISTICS**

- A map is an ordered collection of key-value pairs. Both keys and values can be of nay data type.
- To retrive a value, we can use the corresponding key.
- Maps are iterables. They can be used with a for of loop.

A lot of these charactersics are similar to objects.

#### MAPS vs OBJECTS

- Objects are unordered whereas maps are ordered.
- Keys in Objects acan only be of string or symbol type whereas in maps they can be of any type.
- An Object has a prototype and may contain a few default keys which may collide with owr own keys if we're not careful. A map on the other hand does not conatin any keys by default.
- Objects are not iterables whereas maps are iterables.
- The number of items in an object has to be determined manually whereas it is readily available in a map.
- Apart from string data, we can attach functionality to an object. Wehereas maps are restricted to just storing data.

```js
const map = new Map([
  ["a", 1],
  ["b", 2],
]);

console.log(map);

// to add a new value
map.set("c", 3);

// to delete any value
map.delete("a");

// to check existense
console.log(map.has("k"));

// to check length of stored properties
console.log(map.size);

// to access elements
for (const [key, value] of map) {
  console.log(`${key} :  ${value}`);
}

// to delete all values in map
map.clear();
console.log(map.size);
```

## Custom Data Structures

### Stack
