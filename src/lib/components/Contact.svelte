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

		const element = document.getElementById('contact');
		if (element) {
			observer.observe(element);
		}

		return () => observer.disconnect();
	});

</script>

<section id="contact" class="contact">
	<div class="container">
		<div class="contact-content" class:visible>
			<h2 class="section-title text-center">Let's Connect</h2>
			<p class="section-subtitle text-center">
				I'm always open to new opportunities, collaborations, and meaningful conversations. Feel
				free to reach out!
			</p>

			<div class="cta-section">
				<h3 class="cta-title">Want to send me an email?</h3>
				<p class="cta-text">
					Let's create something amazing at the intersection of technology and business.
				</p>
				<a href="mailto:wibisonoibnuangga@gmail.com" class="btn btn-primary"> Get In Touch </a>
			</div>
		</div>
	</div>
</section>

<footer class="footer">
	<div class="container">
		<div class="footer-content">
			<p class="footer-copyright">© 2025 Portfolio. All rights reserved.</p>
		</div>
	</div>
</footer>

<style>
	.contact {
		background: linear-gradient(180deg, var(--color-surface) 0%, var(--color-background) 100%);
		position: relative;
	}

	.section-title {
		margin-bottom: var(--spacing-md);
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

	.section-subtitle {
		font-size: var(--font-size-lg);
		color: var(--color-text-light);
		max-width: 700px;
		margin: 0 auto var(--spacing-3xl);
		line-height: 1.6;
	}

	.contact-content {
		opacity: 0;
		transform: translateY(30px);
		transition: all 0.8s cubic-bezier(0.4, 0, 0.2, 1);
	}

	.contact-content.visible {
		opacity: 1;
		transform: translateY(0);
	}


	.cta-section {
		max-width: 600px;
		margin: 0 auto;
		text-align: center;
		padding: var(--spacing-3xl);
		background: var(--color-surface);
		border-radius: var(--radius-xl);
		border: 1px solid var(--color-border);
	}

	.cta-title {
		font-size: var(--font-size-3xl);
		margin-bottom: var(--spacing-md);
		background: linear-gradient(135deg, var(--color-primary) 0%, var(--color-secondary) 100%);
		-webkit-background-clip: text;
		-webkit-text-fill-color: transparent;
		background-clip: text;
	}

	.cta-text {
		font-size: var(--font-size-lg);
		color: var(--color-text-light);
		margin-bottom: var(--spacing-xl);
		line-height: 1.6;
	}

	.footer {
		background-color: var(--color-surface);
		padding: var(--spacing-2xl) 0;
		border-top: 1px solid var(--color-border);
	}

	.footer-content {
		text-align: center;
	}

	.footer-text {
		font-size: var(--font-size-base);
		color: var(--color-text-light);
		margin-bottom: var(--spacing-sm);
	}

	.heart {
		color: #ef4444;
		display: inline-block;
		animation: heartbeat 1.5s ease-in-out infinite;
	}

	@keyframes heartbeat {
		0%,
		100% {
			transform: scale(1);
		}
		10%,
		30% {
			transform: scale(1.1);
		}
		20%,
		40% {
			transform: scale(1);
		}
	}

	.footer-copyright {
		font-size: var(--font-size-sm);
		color: var(--color-text-light);
		margin: 0;
	}

	@media (max-width: 768px) {
		.section-subtitle,
		.cta-text {
			font-size: var(--font-size-base);
		}

		.cta-title {
			font-size: var(--font-size-2xl);
		}

		.cta-section {
			padding: var(--spacing-2xl);
		}
	}
</style>
