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

		const element = document.getElementById('projects');
		if (element) {
			observer.observe(element);
		}

		return () => observer.disconnect();
	});

	const projects = [
		{
			title: 'Portfolio v1',
			description:
				'Developed a simple portfolio website showcasing my profile that I always used during job application or self-introduction.',
			tech: ['HTML', 'CSS', 'JavaScript'],
			category: 'Web Development',
			url: 'https://personal-website-7tpvrw7jb-anggas-projects-ed631bc1.vercel.app/' 
		},
		{
			title: 'AirBnB Clone',
			description:
				'Built a full-stack AirBnB clone with user authentication, and inventory management. Still building it! :).',
			tech: ['NextJS', 'Tailwind CSS', 'React', 'TypeScript', 'MongoDB', 'Prisma', 'NextAuth'],
			category: 'Full-Stack',
			url: '#' 
		},
		{
			title: 'Portfolio v2',
			description:
				'Created a second comprehensive portfolio website for my profile with some upgrades.',
			tech: ['Svelte', 'Vite', 'TypeScript', 'CSS', 'HTML'],
			category: 'Web Development',
			url: 'https://anggawibisono.de/' 
		}
	];
</script>

<section id="projects" class="projects">
	<div class="container">
		<div class="projects-content" class:visible>
			<h2 class="section-title text-center">Featured Projects</h2>
			<p class="section-subtitle text-center">
				A selection of projects showcasing my skills in Web Development
			</p>

			<div class="projects-grid">
				{#each projects as project, i}
					<article class="project-card" style="--delay: {i * 0.15}s">
						<div class="project-header">
							<span class="project-category">{project.category}</span>
							<a href={project.url} target="_blank" rel="noopener noreferrer" class="project-title-link">
								<h3 class="project-title">
									{project.title}
									<svg class="external-link-icon" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
										<path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"></path>
										<polyline points="15 3 21 3 21 9"></polyline>
										<line x1="10" y1="14" x2="21" y2="3"></line>
									</svg>
								</h3>
							</a>
						</div>
						<p class="project-description">{project.description}</p>
						<div class="project-tech">
							{#each project.tech as tech}
								<span class="tech-tag">{tech}</span>
							{/each}
						</div>
					</article>
				{/each}
			</div>
		</div>
	</div>
</section>

<style>
	.projects {
		background-color: var(--color-surface);
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

	.projects-content {
		opacity: 0;
		transform: translateY(30px);
		transition: all 0.8s cubic-bezier(0.4, 0, 0.2, 1);
	}

	.projects-content.visible {
		opacity: 1;
		transform: translateY(0);
	}

	.projects-grid {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
		gap: var(--spacing-2xl);
	}

	.project-card {
		background: var(--color-background);
		border-radius: var(--radius-xl);
		padding: var(--spacing-2xl);
		border: 1px solid var(--color-border);
		transition: all var(--transition-base);
		opacity: 0;
		transform: translateY(30px);
		animation: fadeInUp 0.6s ease forwards;
		animation-delay: var(--delay);
		display: flex;
		flex-direction: column;
		height: 100%;
	}

	.projects-content.visible .project-card {
		animation-play-state: running;
	}

	@keyframes fadeInUp {
		to {
			opacity: 1;
			transform: translateY(0);
		}
	}

	.project-card:hover {
		transform: translateY(-8px);
		box-shadow: var(--shadow-xl);
		border-color: var(--color-primary);
	}

	.project-header {
		margin-bottom: var(--spacing-lg);
	}

	.project-category {
		display: inline-block;
		font-size: var(--font-size-sm);
		color: var(--color-primary);
		font-weight: 600;
		text-transform: uppercase;
		letter-spacing: 0.5px;
		margin-bottom: var(--spacing-sm);
	}

	.project-title-link {
		text-decoration: none;
		display: inline-block;
		transition: all var(--transition-base);
	}

	.project-title {
		font-size: var(--font-size-2xl);
		margin-bottom: var(--spacing-md);
		color: var(--color-text);
		display: inline-flex;
		align-items: center;
		gap: var(--spacing-sm);
		transition: all var(--transition-base);
	}

	.external-link-icon {
		opacity: 0;
		transform: translateX(-5px);
		transition: all var(--transition-base);
		color: var(--color-primary);
	}

	.project-title-link:hover .project-title {
		color: var(--color-primary);
	}

	.project-title-link:hover .external-link-icon {
		opacity: 1;
		transform: translateX(0);
	}

	.project-description {
		color: var(--color-text-light);
		line-height: 1.7;
		margin-bottom: var(--spacing-lg);
		flex-grow: 1;
	}

	.project-tech {
		display: flex;
		flex-wrap: wrap;
		gap: var(--spacing-sm);
	}

	.tech-tag {
		display: inline-block;
		padding: var(--spacing-xs) var(--spacing-md);
		background: var(--color-surface);
		color: var(--color-text);
		font-size: var(--font-size-sm);
		font-weight: 500;
		border-radius: var(--radius-md);
		border: 1px solid var(--color-border);
		transition: all var(--transition-fast);
	}

	.project-card:hover .tech-tag {
		border-color: var(--color-primary);
		background: linear-gradient(135deg, var(--color-primary), var(--color-secondary));
		color: #0a1612;
		font-weight: 600;
	}

	@media (max-width: 768px) {
		.projects-grid {
			grid-template-columns: 1fr;
			gap: var(--spacing-xl);
		}

		.section-subtitle {
			font-size: var(--font-size-base);
		}

		.project-card {
			padding: var(--spacing-xl);
		}

		.project-title {
			font-size: var(--font-size-xl);
		}
	}
</style>
