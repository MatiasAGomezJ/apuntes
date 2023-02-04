###### Columna AV

# Getting Started
```bash
npm install --save-dev jest
```

`sum.js`
```js
function sum(a, b) {
  return a + b;
}
module.exports = sum;
```

`sum.test.js`
```js
const sum = require('./sum');  
  
test('adds 1 + 2 to equal 3', () => {  
	expect(sum(1, 2)).toBe(3);  
});
```

Generate basic config file.
```bash
jest --init
```

# Using Matchers
```js
test('two plus two is four', () => {  
	expect(2 + 2).toBe(4);  
});
```
`toBe` uses `Object.is`

If you want to check the value of an object, use `toEqual` or `toStrictEqual`. `toEqual`  recursively checks every field of an object or array.
```js
test('object assignment', () => {  
	const data = {one: 1};  
	data['two'] = 2;  
	expect(data).toEqual({one: 1, two: 2});  
});
```

```ad-tip
Using `toStrictEqual` is preferred over using `toEqual`. `toEqual` simply ignores `undefined` values, whereas `toStrictEqual` takes them into account.
```

You can also test for the opposite of a matcher using `not`:

## Truthiness
you sometimes need to distinguish between `undefined`, `null`, and `false`, but you sometimes do not want to treat these differently.
-   `toBeNull` matches only `null`.
-   `toBeUndefined` matches only `undefined`.
-   `toBeDefined` is the opposite of `toBeUndefined`.
-   `toBeTruthy` matches anything that an `if` statement treats as true.
-   `toBeFalsy` matches anything that an `if` statement treats as false.

For example:
```js
test('null', () => {
  const n = null;
  expect(n).toBeNull();
  expect(n).toBeDefined();
  expect(n).not.toBeUndefined();
  expect(n).not.toBeTruthy();
  expect(n).toBeFalsy();
});

test('zero', () => {
  const z = 0;
  expect(z).not.toBeNull();
  expect(z).toBeDefined();
  expect(z).not.toBeUndefined();
  expect(z).not.toBeTruthy();
  expect(z).toBeFalsy();
});
```

## Numbers

Most ways of comparing numbers have matcher equivalents.

```js
test('two plus two', () => {
  const value = 2 + 2;
  expect(value).toBeGreaterThan(3);
  expect(value).toBeGreaterThanOrEqual(3.5);
  expect(value).toBeLessThan(5);
  expect(value).toBeLessThanOrEqual(4.5);

  // toBe and toEqual are equivalent for numbers
  expect(value).toBe(4);
  expect(value).toEqual(4);
});
```

For floating point equality, use `toBeCloseTo` instead of `toEqual`, because you don't want a test to depend on a tiny rounding error.

```js
test('adding floating point numbers', () => {  
	const value = 0.1 + 0.2;  
	//expect(value).toBe(0.3); This won't work because of rounding error  
	expect(value).toBeCloseTo(0.3); // This works.  
});
```

## Strings

You can check strings against regular expressions with `toMatch`:

```js
test('there is no I in team', () => {
  expect('team').not.toMatch(/I/);
});

test('but there is a "stop" in Christoph', () => {
  expect('Christoph').toMatch(/stop/);
});
```

## Arrays and iterables

You can check if an array or iterable contains a particular item using `toContain`:

```js
const shoppingList = [
  'diapers',
  'kleenex',
  'trash bags',
  'paper towels',
  'milk',
];

test('the shopping list has milk on it', () => {
  expect(shoppingList).toContain('milk');
  expect(new Set(shoppingList)).toContain('milk');
});
```

## Exceptions

If you want to test whether a particular function throws an error when it's called, use `toThrow`.

```js
function compileAndroidCode() {
  throw new Error('you are using the wrong JDK!');
}

test('compiling android goes as expected', () => {
  expect(() => compileAndroidCode()).toThrow();
  expect(() => compileAndroidCode()).toThrow(Error);

  // You can also use a string that must be contained in the error message or a regexp
  expect(() => compileAndroidCode()).toThrow('you are using the wrong JDK');
  expect(() => compileAndroidCode()).toThrow(/JDK/);

  // Or you can match an exact error mesage using a regexp like below
  expect(() => compileAndroidCode()).toThrow(/^you are using the wrong JDK$/); // Test fails
  expect(() => compileAndroidCode()).toThrow(/^you are using the wrong JDK!$/); // Test pass
});
```

```ad-tip
The function that throws an exception needs to be invoked within a wrapping function otherwise the `toThrow` assertion will fail.
```

# Testing Asynchronous Code
## Promises

Return a promise from your test, and Jest will wait for that promise to resolve. If the promise is rejected, the test will fail.

For example, let's say that `fetchData` returns a promise that is supposed to resolve to the string `'peanut butter'`. We could test it with:

```js
test('the data is peanut butter', () => {
  return fetchData().then(data => {
    expect(data).toBe('peanut butter');
  });
});
```

## Async/Await
Alternatively, you can use `async` and `await` in your tests. To write an async test, use the `async` keyword in front of the function passed to `test`. For example, the same `fetchData` scenario can be tested with:
```js
test('the data is peanut butter', async () => {
  const data = await fetchData();
  expect(data).toBe('peanut butter');
});

test('the fetch fails with an error', async () => {
  expect.assertions(1);
  try {
    await fetchData();
  } catch (e) {
    expect(e).toMatch('error');
  }
});
```

You can combine `async` and `await` with `.resolves` or `.rejects`.

```js
test('the data is peanut butter', async () => {
  await expect(fetchData()).resolves.toBe('peanut butter');
});

test('the fetch fails with an error', async () => {
  await expect(fetchData()).rejects.toMatch('error');
});
```
In these cases, `async` and `await` are effectively syntactic sugar for the same logic as the promises example uses.

## Callbacks
## `.resolves`/`.rejectse`
# Setup and Teardown
## Repeating Setup
`beforeEach` and `afterEach`.
## One-Time Setup
`beforeAll` and `afterAll`.
## Scoping
By default, applies to every test. You can group test together using `describe`, which the above hooks will affect only the test inside the `describe` structure.
```js
// Applies to all tests in this file
beforeEach(() => {
  return initializeCityDatabase();
});

test('city database has Vienna', () => {
  expect(isCity('Vienna')).toBeTruthy();
});

test('city database has San Juan', () => {
  expect(isCity('San Juan')).toBeTruthy();
});

describe('matching cities to foods', () => {
  // Applies only to tests in this describe block
  beforeEach(() => {
    return initializeFoodDatabase();
  });

  test('Vienna <3 veal', () => {
    expect(isValidCityFoodPair('Vienna', 'Wiener Schnitzel')).toBe(true);
  });

  test('San Juan <3 plantains', () => {
    expect(isValidCityFoodPair('San Juan', 'Mofongo')).toBe(true);
  });
});
```
Note that the top-level `beforeEach` is executed before the `beforeEach` inside the `describe` block. It may help to illustrate the order of execution of all hooks.
```js
beforeAll(() => console.log('1 - beforeAll'));
afterAll(() => console.log('1 - afterAll'));
beforeEach(() => console.log('1 - beforeEach'));
afterEach(() => console.log('1 - afterEach'));

test('', () => console.log('1 - test'));

describe('Scoped / Nested block', () => {
  beforeAll(() => console.log('2 - beforeAll'));
  afterAll(() => console.log('2 - afterAll'));
  beforeEach(() => console.log('2 - beforeEach'));
  afterEach(() => console.log('2 - afterEach'));

  test('', () => console.log('2 - test'));
});

// 1 - beforeAll
// 1 - beforeEach
// 1 - test
// 1 - afterEach
// 2 - beforeAll
// 1 - beforeEach
// 2 - beforeEach
// 2 - test
// 2 - afterEach
// 1 - afterEach
// 2 - afterAll
// 1 - afterAll
```
## Order of Execution
Jest executes all describe handlers in a test file _before_ it executes any of the actual tests. This is another reason to do setup and teardown inside `before*` and `after*` handlers rather than inside the `describe` blocks. Once the `describe` blocks are complete, by default Jest runs all the tests serially in the order they were encountered in the collection phase, waiting for each to finish and be tidied up before moving on.

```js
describe('describe outer', () => {
  console.log('describe outer-a');

  describe('describe inner 1', () => {
    console.log('describe inner 1');

    test('test 1', () => console.log('test 1'));
  });

  console.log('describe outer-b');

  test('test 2', () => console.log('test 2'));

  describe('describe inner 2', () => {
    console.log('describe inner 2');

    test('test 3', () => console.log('test 3'));
  });

  console.log('describe outer-c');
});

// describe outer-a
// describe inner 1
// describe outer-b
// describe inner 2
// describe outer-c
// test 1
// test 2
// test 3
```
Just like the `describe` and `test` blocks Jest calls the `before*` and `after*` hooks in the order of declaration. Note that the `after*` hooks of the enclosing scope are called first.

```ad-example
title: hola.js
```js
hola
```
```

```
