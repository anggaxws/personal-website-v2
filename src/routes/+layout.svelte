<script lang="ts">
	import '../app.css';

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href='src/photo/avatar.png' />
	<title>Portfolio - Ibnu Angga Wibisono </title>
	<meta name="description" content="Portfolio of a Business Informatics Master's student passionate about Full-Stack Development and Artificial Intelligence" />
</svelte:head>

{@render children()}
