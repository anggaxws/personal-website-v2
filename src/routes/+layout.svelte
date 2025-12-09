<script lang="ts">
	import favicon from '$lib/assets/favicon.svg';
	import '../app.css';

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
	<title>Portfolio - Ibnu Angga Wibisono</title>
	<meta name="description" content="Portfolio of Ibnu Angga Wibisono" />
</svelte:head>

{@render children()}
