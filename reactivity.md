# Reactivity

## Assignment

At the core of Svelte is a system of `reactivity` that keeps the DOM in sync with your application state

ie: in response to an event

```html
<script>
  let count = 0;

  function incrementCount() {
    count++;
  }
</script>

<button on:click="{incrementCount}">
  Clicked {count} {count === 1 ? 'time' : 'times'}
</button>
```

`Svelte 'instruments' this assignment with some code that tell the DOM will need to be updated`

## Declarations

Svelte update the DOM automatically when our component's state changes.

A lot of time, some part of a component's state need to be computed from other part, and them recomputed whenever they change

For these, we have `reactive declaration`, like this:

```javascript
let count = 0;
$: doubled = count * 2;
```

This looks strange, but a JS valid syntax, which Svelte inteprets mean: `rerun this code whenever any of the referenced values change`

`Reactive values` becomes very useful when you need to reference them multiple times, or you have values that depend on other reactive values

## Update Arrays and Objects

Since Svelte'reactivity is triggered by assignment, using array methods like `push()` and `slice()` won't automatically update

```javascript
let numbers = [1, 2, 3, 4];

function addNumber() {
  // this is how you update arrays and objects
  // numbers = numbers
  // or you can do this shorthand
  numbers = [...numbers, numbers.length + 1];
}

$: sum = numbers.reduce((t, n) => t + n, 0);
```
