<script lang="ts">
	import favicon from '../photo/avatar.png';
	import '../app.css';

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
	<title>Portfolio - Ibnu Angga Wibisono </title>
	<meta name="description" content="Portfolio of a Business Informatics Master's student passionate about Full-Stack Development and Artificial Intelligence" />
</svelte:head>

{@render children()}
