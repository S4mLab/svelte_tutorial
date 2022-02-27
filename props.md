# Props

## Declare props

In most projects, we need to pass data down from one component to its children components.

to do this, we need to declare properties (props)

we do that with `export` keyword

`App.svelte`

```html
<script>
  import Nested from './Nested.svelte';
</script>

<Nested answer="{42}" />
```

`Nested.svelte`

```html
<script>
  export let answer;
</script>

<p>The answer is {answer}</p>
```

## Default values

We can easily set the default values for props

in this case, we set the default value in `Nested.svelte`

`Nested.svelte`

```html
<script>
  export let answer = 'a mystery';
</script>

<p>The answer is {answer}</p>
```

if you don't pass any prop to `<Nested/>`, the value of the prop would be the default value, which is `a mystery`

## Spread props

If you have an object of properties, you can spread them onto the component instead of specifying each one,

`Appp.svelte`

```html
<script>
  export Info from './Info.svelte';

  const pkg = {
    name: 'Svelte',
    version: 3,
    speed: 'blazing',
    website: 'https://svelte.dev',
  };
</script>

<Info {...pkg} />
```

`Info.svelte`

```html
<script>
  export let name;
  export let version;
  export let speed;
  export let website;
</script>

<p>
  The <code> {name} </code> package is {speed} fast. Download version {version}
  from <a href="https://www.npmjs.com/package/{name}"> npm </a> and
  <a href="{website}"> learn more here </a>
</p>
```
