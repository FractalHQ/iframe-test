<script>
	import Menu from '$lib/Menu.svelte'
</script>

<Menu />

<slot />

<style>
	:global(html, body) {
		margin: 0;
		padding: 0;
		font-family: 'Roboto', sans-serif;
		font-size: 16px;
		color: #333;
		background-color: #fff;
	}
</style>
