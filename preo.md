Higher Order Flow Control


map - select - project
forEach - do something with side effects, no return value but signals when all the actions are done
filter - where
reduce - fold - aggregate: perform some operation on everything in a collection, returning a new value, potentially with a new cardinality

suitable for many things, makes program operations generalizable, encourages use of more specific functions

var input = [1, 2, 3, 4, 5]

function double (n) {
  return 2 * n;
}

function lessThan (limit) {
  return function (n) {
    return n < limit;
  }
}

function add (prev, n) {
  return prev + n;
}

var nums = input.map(double).filter(lessThan(5));

console.log([
  'There are',
  nums.length,
  'numbers which, when doubled, are less than 5.',
  'They total',
  nums.reduce(add)
  ].join(' '));