<script lang="ts">
  import { onMount } from "svelte";

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

    const element = document.getElementById("projects");
    if (element) {
      observer.observe(element);
    }

    return () => observer.disconnect();
  });

  const erasmusProjects = [
    {
      title: "Social Media and its Business Opportunities Inside",
      description:
        "I designed and coordinated the Erasmus+ SM4B project from start to finish, inspired by my personal experience of going viral online (10+ million views) and facing harmful social media interactions. I managed all core project activities, including documentation, partner and stakeholder coordination, and research. I also established and managed the project websites, delivered SEO training, and trained young people in digital entrepreneurship, social media business opportunities, and responsible online use.",
      tech: ["Germany", "Poland", "Türkiye"],
      category: "Erasmus+",
      url: "https://erasmus-plus.ec.europa.eu/projects/search/details/2023-1-PL01-KA210-YOU-000159357",
    },
    {
      title: "Introduction to ERPSW for VET Teachers",
      description:
        "I contributed to the Erasmus+ ERPSW project by setting up and managing the project websites, supporting project coordination, and organizing monthly meetings and follow-ups. I also delivered SEO training and helped improve the visibility and impact of the project’s digital learning resources.",
      tech: ["Germany", "Türkiye"],
      category: "Erasmus+",
      url: "https://erasmus-plus.ec.europa.eu/projects/search/details/2023-1-DE02-KA210-VET-000150687",
    },
    {
      title: "C4F - Code for Future",
      description:
        "I managed and coordinated the Erasmus+ Code4Future project, handling documentation, meetings, and partner follow-ups. I established and managed the project websites and delivered coding fundamentals training to over 20 high school students in Adana, Türkiye. At the end of the project, we organized a writing contest in both partner countries and selected three winners from each to visit the German tech company Xient GmbH in Cologne.",
      tech: ["Germany", "Türkiye"],
      category: "Erasmus+",
      url: "https://erasmus-plus.ec.europa.eu/projects/search/details/2022-3-DE04-KA210-YOU-000092666",
    },
    {
      title:
        "Intergenerational Hub for the Amelioration of Sustainable Agricultural Practices and Entrepreneurial Mindset",
      description:
        "I supported the Erasmus+ GrandFriend project by contributing to project documentation and research, developing training resources, and managing stakeholders. I also established and managed the project website and delivered SEO training to support the visibility and impact of the project’s educational outputs.",
      tech: ["Germany", "Cyprus", "Greece", "Poland"],
      category: "Erasmus+",
      url: "https://erasmus-plus.ec.europa.eu/projects/search/details/2022-1-DE02-KA220-ADU-000085106",
    },
    {
      title: "Youth Participation for Developing Sustainable Green Cities",
      description:
        "I supported the Erasmus+ GreenCities project by assisting with project management, documentation, meetings, and partner follow-ups. I also contributed to research and established and managed the project website to support communication and visibility.",
      tech: ["Germany", "Cyprus", "Hungary", "Greece", "Bulgaria", "Turkiye"],
      category: "Erasmus+",
      url: "https://erasmus-plus.ec.europa.eu/projects/search/details/2021-1-DE02-KA220-SCH-000034688",
    },
    {
      title: "Training for self-protection against forest fires in rural areas",
      description:
        "I co-managed the project on self-protection against forest fires in rural areas, supporting project planning, documentation, and research. I collaborated with experts to deliver trainings, contributed to the development of training resources, and established and managed the project websites to support learning and dissemination.",
      tech: ["Germany", "Türkiye", "Cyprus", "Italy", "Spain", "Greece", "Portugal"],
      category: "Erasmus+",
      url: "https://erasmus-plus.ec.europa.eu/projects/search/details/2021-1-DE02-KA220-ADU-000028430",
    },
  ];

  const webProjects = [
    {
      title: "Portfolio v.1",
      description:
        "Developed a simple portfolio website showcasing my profile that I always used during job application or self-introduction.",
      tech: ["HTML", "CSS", "JavaScript"],
      category: "Web Development",
      url: "https://anggawibisono.vercel.app/",
    },
    {
      title: "AirBnB Clone",
      description:
        "Built a full-stack AirBnB clone with user authentication, and inventory management. Still building it! :).",
      tech: [
        "NextJS",
        "Tailwind CSS",
        "React",
        "TypeScript",
        "MongoDB",
        "Prisma",
        "NextAuth",
      ],
      category: "WEB DEVELOPMENT",
      url: "#",
    },
    {
      title: "Portfolio v.2",
      description:
        "Created a second comprehensive portfolio website for my profile with some upgrades.",
      tech: ["Svelte", "Vite", "TypeScript", "CSS", "HTML"],
      category: "Web Development",
      url: "https://anggawibisono.de/",
    },
  ];
</script>

<section id="projects" class="projects">
  <div class="container">
    <div class="projects-content" class:visible>
      <h2 class="section-title text-center">Featured Projects</h2>
      <p class="section-subtitle text-center">
        A selection of projects showcasing my contributions and skills
      </p>

      <!-- Erasmus Projects Section -->
      {#if erasmusProjects.length > 0}
        <div class="project-category-section">
          <h3 class="category-section-title">Erasmus+ Projects</h3>
          <div class="projects-grid">
            {#each erasmusProjects as project, i}
              <article
                class="project-card erasmus-card"
                style="--delay: {i * 0.15}s"
              >
                <div class="project-header">
                  <span class="project-category erasmus-badge"
                    >{project.category}</span
                  >
                  <a
                    href={project.url}
                    target="_blank"
                    rel="noopener noreferrer"
                    class="project-title-link"
                  >
                    <h3 class="project-title">
                      {project.title}
                      <svg
                        class="external-link-icon"
                        width="16"
                        height="16"
                        viewBox="0 0 24 24"
                        fill="none"
                        stroke="currentColor"
                        stroke-width="2"
                        stroke-linecap="round"
                        stroke-linejoin="round"
                      >
                        <path
                          d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"
                        ></path>
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
      {/if}

      <!-- Web Development Projects Section -->
      <div class="project-category-section">
        <h3 class="category-section-title">Web Development</h3>
        <div class="projects-grid">
          {#each webProjects as project, i}
            <article
              class="project-card"
              style="--delay: {(i + erasmusProjects.length) * 0.15}s"
            >
              <div class="project-header">
                <span class="project-category">{project.category}</span>
                <a
                  href={project.url}
                  target="_blank"
                  rel="noopener noreferrer"
                  class="project-title-link"
                >
                  <h3 class="project-title">
                    {project.title}
                    <svg
                      class="external-link-icon"
                      width="16"
                      height="16"
                      viewBox="0 0 24 24"
                      fill="none"
                      stroke="currentColor"
                      stroke-width="2"
                      stroke-linecap="round"
                      stroke-linejoin="round"
                    >
                      <path
                        d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"
                      ></path>
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
    content: "";
    display: block;
    width: 60px;
    height: 4px;
    background: linear-gradient(
      90deg,
      var(--color-primary),
      var(--color-secondary)
    );
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

  .project-category-section {
    margin-bottom: var(--spacing-4xl);
  }

  .project-category-section:last-child {
    margin-bottom: 0;
  }

  .category-section-title {
    font-size: var(--font-size-xl);
    color: var(--color-text);
    margin-bottom: var(--spacing-2xl);
    font-weight: 600;
    position: relative;
    padding-left: var(--spacing-lg);
  }

  .category-section-title::before {
    content: "";
    position: absolute;
    left: 0;
    top: 50%;
    transform: translateY(-50%);
    width: 4px;
    height: 24px;
    background: linear-gradient(
      180deg,
      var(--color-primary),
      var(--color-secondary)
    );
    border-radius: 2px;
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

  .erasmus-card {
    border: 1px solid var(--color-border);
  }

  .erasmus-card:hover {
    border-color: var(--color-primary);
    box-shadow: var(--shadow-xl);
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
    background: linear-gradient(
      135deg,
      var(--color-primary),
      var(--color-secondary)
    );
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
