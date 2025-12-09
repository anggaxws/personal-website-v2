<script lang="ts">
	import { onMount } from 'svelte';

	let visible = $state(false);

	onMount(() => {
		const observer = new IntersectionObserver(
			(entries) => {
				entries.forEach((entry) => {
					if (entry.isIntersecting) {
						visible = true;
					}
				});
			},
			{ threshold: 0.2 }
		);

		const element = document.getElementById('about');
		if (element) {
			observer.observe(element);
		}

		return () => observer.disconnect();
	});

	const highlights = [
		{
			title: 'Business & Technology Integration',
			description: 'Combining a Business Informatics background with technical expertise to align organizational needs with effective digital solutions'
		},
		{
			title: 'Project Management',
			description: 'Experienced on leading EU-funded Erasmus+ projects, coordinating multicultural teams, and ensuring structured, compliant project delivery across Europe.'
		},
		{
			title: 'Frontend Development',
			description: 'Creating responsive, user-friendly interfaces with React, Next.js, Tailwind CSS, and modern JavaScript/TypeScript tools.'
		},
		{
			title: 'Backend Development',
			description: 'Building scalable APIs and server-side applications with Node.js, Express.js, Python, and database integrations.'
		},
		{
			title: 'Multilingual Abilities',
			description: 'Fluent in German (C1) and English (C1), with additional proficiency in Indonesian (N), Javanese (N), Malay and Turkish (B1) enabling smooth collaboration and clear communication in diverse, multicultural teams.'
		},
		{
			title: 'Growth Mindset & Innovation',
			description: 'Passionate about learning and growing consistently through opportunities to improve, innovate, and build better solutions.'
		}
	];
</script>

<section id="about" class="about">
	<div class="container">
		<div class="about-content" class:visible>
			<h2 class="section-title text-center">About Me</h2>

			<div class="about-intro">
				<p class="intro-text">
					I'm a <strong>Business Informatics graduate (B.Sc.)</strong> and current
					<strong>Master's student at Hochschule Trier</strong>, combining a solid foundation in
					business strategy with a deep interest in Full-Stack development and Artificial
					Intelligence.
				</p>
				<p class="intro-text">
					With over three years of experience in <strong>Project Management</strong> during my
					Bachelor, I've learned to coordinate teams, manage complexities, and transform business needs into clear, actionable technological solutions.
				</p>
				<p class="intro-text">
					Passionate about <strong>innovation, problem-solving, and continuous growth</strong>, I'm
					always eager to take on challenges that push me to learn more and do better. My goal is to
					create meaningful impact at the intersection of technology and business.
				</p>
				<p class="intro-text">
					Always open to new opportunities, collaborations, and meaningful conversations. I'm really
					excited to connect with you and explore how we can learn and work together!
				</p>
			</div>

			<div class="highlights-grid">
				{#each highlights as highlight, i}
					<div class="highlight-card" style="--delay: {i * 0.2}s">
						<h3 class="highlight-title">{highlight.title}</h3>
						<p class="highlight-description">{highlight.description}</p>
					</div>
				{/each}
			</div>

			<!-- <div class="about-footer">
				<p class="footer-text">
					Always open to new opportunities, collaborations, and meaningful conversations. I'm really
					excited to connect with you and explore how we can learn and work together!
				</p>
			</div> -->
		</div>
	</div>
</section>

<style>
	.about {
		background-color: var(--color-background);
		position: relative;
	}

	.about::before {
		content: '';
		position: absolute;
		top: 50%;
		left: 0;
		width: 100%;
		height: 1px;
		background: linear-gradient(
			90deg,
			transparent,
			var(--color-border),
			transparent
		);
	}

	.section-title {
		margin-bottom: var(--spacing-3xl);
		position: relative;
	}

	.section-title::after {
		content: '';
		display: block;
		width: 60px;
		height: 4px;
		background: linear-gradient(90deg, var(--color-primary), var(--color-secondary));
		margin: var(--spacing-md) auto 0;
		border-radius: 2px;
	}

	.about-content {
		opacity: 0;
		transform: translateY(30px);
		transition: all 0.8s cubic-bezier(0.4, 0, 0.2, 1);
	}

	.about-content.visible {
		opacity: 1;
		transform: translateY(0);
	}

	.about-intro {
		max-width: 800px;
		margin: 0 auto var(--spacing-3xl);
	}

	.intro-text {
		font-size: var(--font-size-lg);
		line-height: 1.8;
		color: var(--color-text-light);
		margin-bottom: var(--spacing-lg);
	}

	.intro-text strong {
		color: var(--color-text);
		font-weight: 600;
	}

	.highlights-grid {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
		gap: var(--spacing-xl);
		margin-bottom: var(--spacing-3xl);
	}

	.highlight-card {
		padding: var(--spacing-xl);
		background: var(--color-surface);
		border-radius: var(--radius-lg);
		border: 1px solid var(--color-border);
		transition: all var(--transition-base);
		opacity: 0;
		transform: translateY(20px);
		animation: fadeInUp 0.6s ease forwards;
		animation-delay: var(--delay);
	}

	.about-content.visible .highlight-card {
		animation-play-state: running;
	}

	@keyframes fadeInUp {
		to {
			opacity: 1;
			transform: translateY(0);
		}
	}

	.highlight-card:hover {
		transform: translateY(-5px);
		box-shadow: var(--shadow-lg);
		border-color: var(--color-primary);
	}

	.highlight-title {
		font-size: var(--font-size-xl);
		margin-bottom: var(--spacing-sm);
		color: var(--color-primary);
	}

	.highlight-description {
		color: var(--color-text-light);
		line-height: 1.6;
		margin: 0;
	}

	.about-footer {
		max-width: 700px;
		margin: 0 auto;
		text-align: center;
		padding: var(--spacing-2xl);
		background: linear-gradient(135deg, var(--color-surface) 0%, var(--color-background) 100%);
		border-radius: var(--radius-lg);
		border: 1px solid var(--color-border);
	}

	.footer-text {
		font-size: var(--font-size-lg);
		color: var(--color-text-light);
		margin: 0;
		line-height: 1.7;
	}

	@media (max-width: 768px) {
		.highlights-grid {
			grid-template-columns: 1fr;
			gap: var(--spacing-lg);
		}

		.intro-text,
		.footer-text {
			font-size: var(--font-size-base);
		}
	}
</style>
