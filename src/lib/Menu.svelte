<script>
	import { pages } from '$lib/pages'
	import { onMount } from 'svelte'

	let loaded = Array(pages.length).fill(false)
	let ghostFrame = null
	onMount(() => {
		ghostFrame = document.createElement('iframe')
		ghostFrame.style.visibility = 'hidden'
		document.body.appendChild(ghostFrame)
	})
	function preload(url, i) {
		if (loaded[i]) return
		ghostFrame.src = url
		loaded[i] = true
	}
</script>

<nav>
	{#each pages as page, i}
		<a
			href={page.path}
			on:mouseover={() => preload(page.url, i)}
			on:focus={() => preload(page.url, i)}
		>
			{page.name}
		</a>
	{/each}
</nav>

<style>
	nav {
		width: 100vw;
		display: flex;
		justify-content: space-around;
		color: pink;
	}
</style>
