###### Columna AW

# Syntax
```js
x === y
```

# Description

# Examples
```js
"hello" === "hello"; // true
"hello" === "hola"; // false

3 === 3; // true
3 === 4; // false

true === true; // true
true === false; // false

null === null; // true
```

```js
"3" === 3; // false
true === 1; // false
null === undefined; // false
```

```js
const object1 = {
  key: "value",
};

const object2 = {
  key: "value",
};

console.log(object1 === object2); // false
console.log(object1 === object1); // true
```