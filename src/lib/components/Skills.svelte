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

    const element = document.getElementById("skills");
    if (element) {
      observer.observe(element);
    }

    return () => observer.disconnect();
  });

  const skillCategories = [
    {
      title: "Frontend Development",
      skills: [
        "Next.js",
        "BootStrap",
        "Svelte/SvelteKit",
        "React",
        "TypeScript",
        "HTML/CSS",
        "Tailwind CSS",
      ],
    },
    {
      title: "Backend Development",
      skills: [
        "Node.js",
        "Python",
        "Express.js",
        "PostgreSQL",
        "MongoDB",
        "REST APIs",
        "GraphQL",
        "MySQL",
      ],
    },
    {
      title: "Business & Management",
      skills: [
        "Project Management",
        "Business Strategy",
        "Requirements Analysis",
        "Stakeholder Management",
      ],
    },
    {
      title: "Tools & Technologies",
      skills: ["Git", "Docker", "SAP", "AWS", "VSCode", "Figma"],
    },
  ];
</script>

<section id="skills" class="skills">
  <div class="container">
    <div class="skills-content" class:visible>
      <h2 class="section-title text-center">Skills & Expertise</h2>
      <p class="section-subtitle text-center">
        A comprehensive set of technical skills that I’m actively developing.
        I’m not an expert yet, but I continuously learn by doing and improving
        with every challenge.
      </p>

      <div class="skills-grid">
        {#each skillCategories as category, i}
          <div class="skill-category" style="--delay: {i * 0.1}s">
            <h3 class="category-title">{category.title}</h3>
            <div class="skills-list">
              {#each category.skills as skill}
                <span class="skill-tag">{skill}</span>
              {/each}
            </div>
          </div>
        {/each}
      </div>
    </div>
  </div>
</section>

<style>
  .skills {
    background-color: var(--color-background);
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

  .skills-content {
    opacity: 0;
    transform: translateY(30px);
    transition: all 0.8s cubic-bezier(0.4, 0, 0.2, 1);
  }

  .skills-content.visible {
    opacity: 1;
    transform: translateY(0);
  }

  .skills-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: var(--spacing-2xl);
  }

  .skill-category {
    background: var(--color-surface);
    border-radius: var(--radius-xl);
    padding: var(--spacing-2xl);
    border: 1px solid var(--color-border);
    transition: all var(--transition-base);
    opacity: 0;
    transform: translateY(20px);
    animation: fadeInUp 0.6s ease forwards;
    animation-delay: var(--delay);
  }

  .skills-content.visible .skill-category {
    animation-play-state: running;
  }

  @keyframes fadeInUp {
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }

  .skill-category:hover {
    transform: translateY(-5px);
    box-shadow: var(--shadow-lg);
    border-color: var(--color-primary);
  }

  .category-title {
    font-size: var(--font-size-xl);
    margin-bottom: var(--spacing-lg);
    color: var(--color-primary);
    position: relative;
    padding-bottom: var(--spacing-sm);
  }

  .category-title::after {
    content: "";
    position: absolute;
    bottom: 0;
    left: 0;
    width: 40px;
    height: 3px;
    background: linear-gradient(
      90deg,
      var(--color-primary),
      var(--color-secondary)
    );
    border-radius: 2px;
  }

  .skills-list {
    display: flex;
    flex-wrap: wrap;
    gap: var(--spacing-sm);
  }

  .skill-tag {
    display: inline-block;
    padding: var(--spacing-sm) var(--spacing-md);
    background: var(--color-background);
    color: var(--color-text);
    font-size: var(--font-size-sm);
    font-weight: 500;
    border-radius: var(--radius-md);
    border: 1px solid var(--color-border);
    transition: all var(--transition-fast);
    white-space: nowrap;
  }

  .skill-tag:hover {
    background: linear-gradient(
      135deg,
      var(--color-primary),
      var(--color-secondary)
    );
    color: #0a1612;
    border-color: transparent;
    transform: translateY(-2px);
    box-shadow: 0 2px 8px rgba(0, 255, 157, 0.2);
    font-weight: 600;
  }

  @media (max-width: 768px) {
    .skills-grid {
      grid-template-columns: 1fr;
      gap: var(--spacing-xl);
    }

    .section-subtitle {
      font-size: var(--font-size-base);
    }

    .skill-category {
      padding: var(--spacing-xl);
    }

    .category-title {
      font-size: var(--font-size-lg);
    }

    .skill-tag {
      font-size: var(--font-size-xs);
      padding: var(--spacing-xs) var(--spacing-sm);
    }
  }
</style>
