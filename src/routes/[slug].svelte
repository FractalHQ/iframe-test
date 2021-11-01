<script context="module">
	import { pages } from '$lib/pages'

	export async function load(ctx) {
		let slug = ctx.page.params.slug
		console.log(slug)
		const match = pages.find((p) => p.name === slug)
		console.log(match)
		let iframe = match

		return { props: { slug, iframe } }
	}
</script>

<script>
	export let slug, iframe
</script>

<svelte:head>
	<title>{slug}</title>
</svelte:head>

{#if iframe?.url}
	<iframe
		title={slug}
		src={iframe?.url}
		width="100%"
		height="100%"
		frameborder="0"
	/>
{:else}
	<p>No page found for {slug}...</p>
	<a href="/">Go home</a>
{/if}

<style>
	iframe {
		display: flex;
		height: 100vh;
	}
</style>
