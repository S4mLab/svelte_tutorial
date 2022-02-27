# LOGIC

## If blocks

Svelte has a way to express logic like loop and conditionals

to condiionally render some markup, we wrap in `if` block

```html
{#if user.loggedIn}
<button on:click="{toggle}">Log out</button>
{/if} {#if !user.loggedIn}
<button on:click="{toggle}">Log in</button>
{/if}
```

or, you can use `else if` like this

```html
{#if user.loggedIn}
<button on:click="{toggle}">Log out</button>
{:else}
<button on:click="{toggle}">Log in</button>
{/if}
```

## else-if block

```html
{#if x > 10}
<p>{x} is greater than 10</p>
{:else if 5 > x}
<p>5 is greater than {x}</p>
{:else}
<p>{x} is between 5 and 10</p>
{/if}
```

## Each block

To loop over list of data, use `each` block

```html
<script>
  let cats = [
    { id: 'J---aiyznGQ', name: 'Keyboard Cat' },
    { id: 'z_AbfPXTKms', name: 'Maru' },
    { id: 'OUtn3pvWmpg', name: 'Henri The Existential Cat' },
  ];
</script>

<h1>The Famous Cats of YouTube</h1>

<ul>
  {#each cats as cat}
  <li>
    <a target="_blank" href="https://www.youtube.com/watch?v={cat.id}">
      {cat.name}
    </a>
  </li>
  {/each}
</ul>
```

The second arg is the index

```html
{#each cats as cat, i}
<li>
  <a target="_blank" href="https://www.youtube.com/watch?v={cat.id}">
    {i + 1}: {cat.name}
  </a>
</li>
{/each}
```

you can also destructuring the object

```html
{#each cats as {id, name}, i}
<li>
  <a target="_blank" href="https://www.youtube.com/watch?v={id}">
    {i + 1}: {name}
  </a>
</li>
{/each}
```
