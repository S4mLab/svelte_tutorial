<script>
    import {createEventDispatcher} from 'svelte'

    const dispatch = createEventDispatcher();

    // 
    const sayHello = () => {
        dispatch('say-hello', {
            text: 'Hello there, I am S4m'
        })
    }
</script>

<button on:click={sayHello}>
    Click to say Hello
</button>