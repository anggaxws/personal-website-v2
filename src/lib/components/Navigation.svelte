<script lang="ts">
	import { onMount } from 'svelte';

	let scrolled = $state(false);
	let mobileMenuOpen = $state(false);

	onMount(() => {
		const handleScroll = () => {
			scrolled = window.scrollY > 50;
		};

		window.addEventListener('scroll', handleScroll);
		return () => window.removeEventListener('scroll', handleScroll);
	});

	function scrollToSection(id: string) {
		mobileMenuOpen = false;
		const element = document.getElementById(id);
		if (element) {
			element.scrollIntoView({ behavior: 'smooth' });
		}
	}

	function scrollToTop() {
		mobileMenuOpen = false;
		window.scrollTo({ top: 0, behavior: 'smooth' });
	}

	const navItems = [
		{ label: 'About', id: 'about' },
		{ label: 'Projects', id: 'projects' },
		{ label: 'Skills', id: 'skills' },
		{ label: 'Contact', id: 'contact' }
	];
</script>

<nav class="nav" class:scrolled>
	<div class="container">
		<div class="nav-content">
			<button class="logo" onclick={scrollToTop}>
				<span class="logo-text">Ibnu Angga Wibisono</span>
			</button>

			<button
				class="mobile-menu-btn"
				onclick={() => (mobileMenuOpen = !mobileMenuOpen)}
				aria-label="Toggle menu"
			>
				<span class="hamburger" class:open={mobileMenuOpen}></span>
			</button>

			<ul class="nav-links" class:open={mobileMenuOpen}>
				{#each navItems as item}
					<li>
						<button class="nav-link" onclick={() => scrollToSection(item.id)}>
							{item.label}
						</button>
					</li>
				{/each}
				<li>
					<a
						class="resume-btn"
						href="https://drive.google.com/file/d/1ftHKDezc9PZuqPHaa78rx_P6Un5rLPMJ/view?usp=sharing"
						download
						target="_blank"
						onclick={() => (mobileMenuOpen = false)}
					>
						Resume
					</a>
				</li>
			</ul>
		</div>
	</div>
</nav>

{#if mobileMenuOpen}
	<button
		class="overlay"
		onclick={() => (mobileMenuOpen = false)}
		aria-label="Close mobile menu"
	></button>
{/if}

<style>
	.nav {
		position: fixed;
		top: 0;
		left: 0;
		right: 0;
		z-index: 1000;
		background: transparent;
		transition: all var(--transition-base);
		border-bottom: 1px solid transparent;
	}

	.nav.scrolled {
		background: rgba(10, 22, 18, 0.85);
		backdrop-filter: blur(20px) saturate(180%);
		-webkit-backdrop-filter: blur(20px) saturate(180%);
		box-shadow: 0 4px 30px rgba(0, 0, 0, 0.3), 0 0 15px rgba(0, 255, 157, 0.08);
		border-bottom: 1px solid rgba(0, 255, 157, 0.15);
	}

	.nav-content {
		display: flex;
		align-items: center;
		justify-content: space-between;
		padding: var(--spacing-lg) 0;
	}

	.logo {
		background: none;
		border: none;
		cursor: pointer;
		padding: 0;
	}

	.logo-text {
		font-size: var(--font-size-xl);
		font-weight: 700;
		background: linear-gradient(135deg, var(--color-primary), var(--color-secondary));
		-webkit-background-clip: text;
		-webkit-text-fill-color: transparent;
		background-clip: text;
		transition: all var(--transition-base);
		filter: drop-shadow(0 0 6px rgba(0, 255, 157, 0.2));
		font-family: var(--font-mono);
		letter-spacing: 0.05em;
	}

	.logo:hover .logo-text {
		filter: drop-shadow(0 0 10px rgba(0, 255, 157, 0.4));
		transform: scale(1.02);
	}

	.nav-links {
		display: flex;
		gap: var(--spacing-xl);
		list-style: none;
		margin: 0;
		padding: 0;
	}

	.nav-link {
		background: none;
		border: none;
		color: var(--color-text);
		font-size: var(--font-size-base);
		font-weight: 500;
		cursor: pointer;
		padding: var(--spacing-sm) var(--spacing-md);
		border-radius: var(--radius-md);
		transition: all var(--transition-base);
		position: relative;
		text-transform: uppercase;
		letter-spacing: 0.05em;
		font-size: var(--font-size-sm);
	}

	.nav-link::after {
		content: '';
		position: absolute;
		bottom: 0;
		left: 50%;
		width: 0;
		height: 2px;
		background: var(--color-primary);
		transform: translateX(-50%);
		transition: width var(--transition-base);
		box-shadow: 0 0 4px var(--color-primary);
	}

	.nav-link:hover {
		color: var(--color-primary);
	}

	.nav-link:hover::after {
		width: 80%;
	}

	.resume-btn {
		display: inline-flex;
		align-items: center;
		justify-content: center;
		padding: var(--spacing-sm) var(--spacing-lg);
		background: linear-gradient(135deg, var(--color-primary), var(--color-secondary));
		color: var(--color-background);
		font-weight: 700;
		text-decoration: none;
		border-radius: var(--radius-lg);
		box-shadow: 0 8px 30px rgba(0, 255, 157, 0.25), 0 0 12px rgba(0, 255, 157, 0.35);
		transition: transform var(--transition-base), box-shadow var(--transition-base),
			filter var(--transition-base);
		letter-spacing: 0.05em;
		text-transform: uppercase;
	}

	.resume-btn:hover {
		transform: translateY(-2px) scale(1.01);
		box-shadow: 0 12px 40px rgba(0, 255, 157, 0.35), 0 0 18px rgba(0, 255, 157, 0.45);
		filter: brightness(1.05);
	}

	.mobile-menu-btn {
		display: none;
		background: none;
		border: none;
		cursor: pointer;
		padding: var(--spacing-sm);
		z-index: 1001;
	}

	.hamburger {
		display: block;
		width: 24px;
		height: 2px;
		background: var(--color-text);
		position: relative;
		transition: all var(--transition-base);
	}

	.hamburger::before,
	.hamburger::after {
		content: '';
		position: absolute;
		width: 24px;
		height: 2px;
		background: var(--color-text);
		transition: all var(--transition-base);
	}

	.hamburger::before {
		top: -7px;
	}

	.hamburger::after {
		bottom: -7px;
	}

	.hamburger.open {
		background: transparent;
	}

	.hamburger.open::before {
		top: 0;
		transform: rotate(45deg);
	}

	.hamburger.open::after {
		bottom: 0;
		transform: rotate(-45deg);
	}

	.overlay {
		display: none;
	}

	@media (max-width: 768px) {
		.mobile-menu-btn {
			display: block;
		}

		.nav-links {
			position: fixed;
			top: 0;
			right: -100%;
			height: 100vh;
			width: 70%;
			max-width: 300px;
			background: var(--color-background);
			flex-direction: column;
			padding: var(--spacing-4xl) var(--spacing-xl);
			gap: var(--spacing-lg);
			box-shadow: var(--shadow-xl);
			transition: right var(--transition-base);
			border-left: 1px solid var(--color-border);
		}

		.nav-links.open {
			right: 0;
		}

		.nav-link {
			width: 100%;
			text-align: left;
			padding: var(--spacing-md);
			font-size: var(--font-size-lg);
		}

		.resume-btn {
			width: 100%;
		}

		.overlay {
			display: block;
			position: fixed;
			top: 0;
			left: 0;
			right: 0;
			bottom: 0;
			background: rgba(0, 0, 0, 0.5);
			z-index: 999;
			cursor: pointer;
			border: none;
		}
	}
</style>
