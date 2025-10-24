<script lang="ts">
	import Header from '$lib/components/Header.svelte';

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href="/assets/logo.svg" />
</svelte:head>

<Header />

<main>
	{@render children?.()}
</main>
