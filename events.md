# Events

## Event modifiers

DOM event handlers can have modifiers that change their behaviour.

ie: a handler with `once` modifier will only run a single time

```html
<script>
  function handleClick() {
    alert('no more alerts');
  }
</script>

<button on:click|once="{handleClick}">Click me</button>
```

## Component events

Components can also dispatch events. To do that, they must create an event dispatcher

`Inner.svelte`

```html
<script>
  import { createEvenDispatcher } from 'svelte';

  const dispatch = createEventDispatcher();

  // when this function is triggered
  // it will dispatch the custom event that you just create,
  // in this case, you name the event as 'say-hello'
  // the event also send an obj when the event is called,
  // it is also a custom obj, u can put whatever prop you like in there
  const sayHello = () => {
    dispatch('say-hello', {
      text: 'Hi there',
    });
  };
</script>

<!-- when button click, trigger sayHello > trigger the dispatch event -->
<button on:click="{sayHello}">Click to say hello</button>
```
