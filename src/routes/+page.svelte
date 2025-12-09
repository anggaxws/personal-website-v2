<script lang="ts">
	import Navigation from '$lib/components/Navigation.svelte';
	import Hero from '$lib/components/Hero.svelte';
	import About from '$lib/components/About.svelte';
	import Projects from '$lib/components/Projects.svelte';
	import Skills from '$lib/components/Skills.svelte';
	import Contact from '$lib/components/Contact.svelte';
</script>

<Navigation />
<main>
	<Hero />
	<About />
	<Projects />
	<Skills />
	<Contact />
</main>

<style>
	main {
		padding-top: 80px; /* Account for fixed navigation */
	}
</style>
