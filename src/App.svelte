<script>
	import Inner from './Inner.svelte'

	const handleMessage = (event) => {
		alert(event.detail.text)
	}
</script>

<Inner on:say-hello={handleMessage}/>