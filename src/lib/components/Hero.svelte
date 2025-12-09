<script lang="ts">
  import { onMount } from "svelte";
  import profileImage from "../../photo/wibisono.png";

  let visible = $state(false);
  let typedText = $state("");
  let cursorVisible = $state(true);

  const roles = [
    "Business Informatics Student",
    "Project Management",
    "Technology Enthusiast",
  ];
  let currentRoleIndex = $state(0);

  onMount(() => {
    visible = true;

    // Typing effect
    const typeText = async () => {
      while (true) {
        const currentRole = roles[currentRoleIndex];

        // Type out
        for (let i = 0; i <= currentRole.length; i++) {
          typedText = currentRole.substring(0, i);
          await new Promise((resolve) => setTimeout(resolve, 100));
        }

        await new Promise((resolve) => setTimeout(resolve, 2000));

        // Delete
        for (let i = currentRole.length; i >= 0; i--) {
          typedText = currentRole.substring(0, i);
          await new Promise((resolve) => setTimeout(resolve, 50));
        }

        await new Promise((resolve) => setTimeout(resolve, 500));
        currentRoleIndex = (currentRoleIndex + 1) % roles.length;
      }
    };

    typeText();

    // Cursor blink
    const cursorInterval = setInterval(() => {
      cursorVisible = !cursorVisible;
    }, 500);

    return () => {
      clearInterval(cursorInterval);
    };
  });

  function scrollToSection(id: string) {
    const element = document.getElementById(id);
    if (element) {
      element.scrollIntoView({ behavior: "smooth" });
    }
  }
</script>

<section class="hero">
  <div class="cyber-grid"></div>
  <div class="glow-orb glow-orb-1"></div>
  <div class="glow-orb glow-orb-2"></div>
  <div class="glow-orb glow-orb-3"></div>

  <div class="container">
    <div class="hero-content" class:visible>
      <div class="hero-text">
        <p class="hero-greeting">
          <span class="bracket">[</span>
          <span class="glitch" data-text="INITIALIZING"
            >Welcome to my personal website</span
          >
          <span class="bracket">]</span>
        </p>
        <h1 class="hero-title">
          <span class="name-text">Ibnu Angga Wibisono B.Sc</span>
          <span class="role-container">
            <span class="gradient-text">{typedText}</span>
            <span class="cursor" class:visible={cursorVisible}>|</span>
          </span>
        </h1>
        <p class="hero-subtitle">
          <span class="highlight">Business Informatics graduate</span>
          and current Master's candidate at Hochschule Trier.<br />
          Bridging <span class="highlight">business strategy</span> and
          <span class="highlight">technology</span> through my passion for Management,
          Full-Stack Development and Artificial Intelligence.
        </p>
        <div class="hero-cta">
          <button
            class="btn btn-primary"
            onclick={() => scrollToSection("projects")}
          >
            <span>View Projects</span>
          </button>
          <button
            class="btn btn-secondary"
            onclick={() => scrollToSection("contact")}
          >
            <span>Contact Me</span>
          </button>
        </div>
      </div>

      <div class="hero-image">
        <div class="image-frame">
          <div class="frame-corner frame-corner-tl"></div>
          <div class="frame-corner frame-corner-tr"></div>
          <div class="frame-corner frame-corner-bl"></div>
          <div class="frame-corner frame-corner-br"></div>
          <div class="image-glow"></div>
          <img
            src={profileImage}
            alt="Ibnu Angga Wibisono"
            class="profile-image"
          />
        </div>

        <div class="social-section">
          <p class="social-label">Follow Me</p>
          <div class="social-buttons">
            <a
              href="https://www.linkedin.com/in/anggawibisono/"
              target="_blank"
              rel="noopener noreferrer"
              class="social-btn social-btn-linkedin"
            >
              <svg class="social-icon" width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
                <path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/>
              </svg>
              LinkedIn
            </a>
            <a
              href="https://github.com/anggaxws"
              target="_blank"
              rel="noopener noreferrer"
              class="social-btn social-btn-github"
            >
              <svg class="social-icon" width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
                <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
              </svg>
              GitHub
            </a>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<style>
  .hero {
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
    overflow: hidden;
    background: radial-gradient(
      ellipse at center,
      rgba(19, 24, 39, 0.8) 0%,
      var(--color-background) 100%
    );
  }

  /* Cyber grid background */
  .cyber-grid {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-image: linear-gradient(
        rgba(0, 255, 157, 0.04) 1px,
        transparent 1px
      ),
      linear-gradient(90deg, rgba(0, 255, 157, 0.04) 1px, transparent 1px);
    background-size: 50px 50px;
    transform: perspective(500px) rotateX(60deg) scale(2);
    transform-origin: center bottom;
    opacity: 0.3;
    animation: gridMove 20s linear infinite;
  }

  @keyframes gridMove {
    0% {
      background-position: 0 0;
    }
    100% {
      background-position: 50px 50px;
    }
  }

  /* Animated glow orbs */
  .glow-orb {
    position: absolute;
    border-radius: 50%;
    filter: blur(80px);
    opacity: 0.4;
    animation: float 20s ease-in-out infinite;
  }

  .glow-orb-1 {
    width: 400px;
    height: 400px;
    background: radial-gradient(
      circle,
      var(--color-primary) 0%,
      transparent 70%
    );
    top: 10%;
    right: 10%;
    animation-delay: 0s;
  }

  .glow-orb-2 {
    width: 500px;
    height: 500px;
    background: radial-gradient(
      circle,
      var(--color-secondary) 0%,
      transparent 70%
    );
    bottom: 15%;
    left: 5%;
    animation-delay: 5s;
  }

  .glow-orb-3 {
    width: 300px;
    height: 300px;
    background: radial-gradient(
      circle,
      var(--color-accent) 0%,
      transparent 70%
    );
    top: 50%;
    left: 50%;
    animation-delay: 10s;
  }

  @keyframes float {
    0%,
    100% {
      transform: translate(0, 0) scale(1);
    }
    25% {
      transform: translate(50px, -50px) scale(1.1);
    }
    50% {
      transform: translate(-30px, 30px) scale(0.9);
    }
    75% {
      transform: translate(30px, 50px) scale(1.05);
    }
  }

  .hero-content {
    position: relative;
    z-index: 10;
    opacity: 0;
    transform: translateY(30px);
    transition: all 1s cubic-bezier(0.4, 0, 0.2, 1);
    display: flex;
    align-items: center;
    gap: var(--spacing-4xl);
  }

  .hero-content.visible {
    opacity: 1;
    transform: translateY(0);
  }

  .hero-text {
    flex: 1;
    max-width: 600px;
  }

  .hero-image {
    flex-shrink: 0;
  }

  .image-frame {
    position: relative;
    width: 350px;
    height: 350px;
    padding: 8px;
    background: linear-gradient(
      135deg,
      rgba(0, 255, 157, 0.1),
      rgba(0, 212, 255, 0.1)
    );
    border-radius: var(--radius-xl);
    animation: frameRotate 10s linear infinite;
  }

  @keyframes frameRotate {
    0% {
      background: linear-gradient(
        135deg,
        rgba(0, 255, 157, 0.1),
        rgba(0, 212, 255, 0.1)
      );
    }
    50% {
      background: linear-gradient(
        135deg,
        rgba(0, 212, 255, 0.1),
        rgba(10, 255, 239, 0.1)
      );
    }
    100% {
      background: linear-gradient(
        135deg,
        rgba(0, 255, 157, 0.1),
        rgba(0, 212, 255, 0.1)
      );
    }
  }

  .frame-corner {
    position: absolute;
    width: 30px;
    height: 30px;
    border: 2px solid var(--color-primary);
    z-index: 2;
  }

  .frame-corner-tl {
    top: -2px;
    left: -2px;
    border-right: none;
    border-bottom: none;
    border-top-left-radius: var(--radius-lg);
  }

  .frame-corner-tr {
    top: -2px;
    right: -2px;
    border-left: none;
    border-bottom: none;
    border-top-right-radius: var(--radius-lg);
  }

  .frame-corner-bl {
    bottom: -2px;
    left: -2px;
    border-right: none;
    border-top: none;
    border-bottom-left-radius: var(--radius-lg);
  }

  .frame-corner-br {
    bottom: -2px;
    right: -2px;
    border-left: none;
    border-top: none;
    border-bottom-right-radius: var(--radius-lg);
  }

  .image-glow {
    position: absolute;
    top: 50%;
    left: 50%;
    width: 120%;
    height: 120%;
    background: radial-gradient(
      circle,
      var(--color-glow-primary) 0%,
      transparent 70%
    );
    transform: translate(-50%, -50%);
    opacity: 0.3;
    animation: pulse 3s ease-in-out infinite;
    z-index: 0;
  }

  @keyframes pulse {
    0%,
    100% {
      opacity: 0.3;
      transform: translate(-50%, -50%) scale(1);
    }
    50% {
      opacity: 0.5;
      transform: translate(-50%, -50%) scale(1.05);
    }
  }

  .profile-image {
    position: relative;
    width: 100%;
    height: 100%;
    object-fit: cover;
    border-radius: var(--radius-lg);
    z-index: 1;
    transition: all var(--transition-base);
  }

  .image-frame:hover .profile-image {
    transform: scale(1.02);
  }

  .image-frame:hover .frame-corner {
    border-color: var(--color-secondary);
  }

  .social-section {
    margin-top: var(--spacing-xl);
    text-align: center;
  }

  .social-label {
    font-size: var(--font-size-sm);
    font-weight: 600;
    color: var(--color-primary);
    text-transform: uppercase;
    letter-spacing: 0.1em;
    margin-bottom: var(--spacing-md);
    font-family: var(--font-mono);
  }

  .social-buttons {
    display: flex;
    gap: var(--spacing-md);
    justify-content: center;
  }

  .social-btn {
    display: inline-flex;
    align-items: center;
    gap: var(--spacing-sm);
    padding: var(--spacing-sm) var(--spacing-lg);
    font-size: var(--font-size-sm);
    font-weight: 600;
    border-radius: var(--radius-md);
    border: 1px solid var(--color-border);
    background: var(--color-surface);
    color: var(--color-text);
    text-decoration: none;
    transition: all var(--transition-base);
    position: relative;
    overflow: hidden;
    text-transform: uppercase;
    letter-spacing: 0.05em;
  }

  .social-btn::before {
    content: '';
    position: absolute;
    top: 0;
    left: -100%;
    width: 100%;
    height: 100%;
    background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.1), transparent);
    transition: left var(--transition-slow);
  }

  .social-btn:hover::before {
    left: 100%;
  }

  .social-icon {
    transition: transform var(--transition-base);
  }

  .social-btn-linkedin:hover {
    background: linear-gradient(135deg, rgba(0, 119, 181, 0.2), rgba(0, 212, 255, 0.2));
    border-color: var(--color-secondary);
    color: var(--color-secondary);
    box-shadow: 0 0 20px rgba(0, 212, 255, 0.3);
    transform: translateY(-2px);
  }

  .social-btn-github:hover {
    background: linear-gradient(135deg, rgba(0, 255, 157, 0.2), rgba(10, 255, 239, 0.2));
    border-color: var(--color-primary);
    color: var(--color-primary);
    box-shadow: 0 0 20px rgba(0, 255, 157, 0.3);
    transform: translateY(-2px);
  }

  .social-btn:hover .social-icon {
    transform: scale(1.1) rotate(5deg);
  }

  .hero-greeting {
    font-size: var(--font-size-lg);
    color: var(--color-primary);
    margin-bottom: var(--spacing-md);
    font-weight: 600;
    font-family: var(--font-mono);
    letter-spacing: 0.1em;
    text-transform: uppercase;
  }

  .bracket {
    color: var(--color-secondary);
    font-weight: 700;
  }

  .glitch {
    position: relative;
    animation: glitch 3s infinite;
  }

  @keyframes glitch {
    0%,
    90%,
    100% {
      transform: translate(0);
    }
    92% {
      transform: translate(-2px, 1px);
    }
    94% {
      transform: translate(2px, -1px);
    }
    96% {
      transform: translate(-1px, 2px);
    }
  }

  .hero-title {
    font-size: clamp(2.5rem, 5vw, 4.5rem);
    font-weight: 800;
    line-height: 1.2;
    margin-bottom: var(--spacing-lg);
  }

  .name-text {
    display: block;
    margin-bottom: var(--spacing-sm);
    background: linear-gradient(
      135deg,
      var(--color-text) 0%,
      var(--color-text-light) 100%
    );
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .role-container {
    display: block;
    min-height: 1.2em;
  }

  .gradient-text {
    background: linear-gradient(
      135deg,
      var(--color-primary) 0%,
      var(--color-secondary) 100%
    );
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    filter: drop-shadow(0 0 8px rgba(0, 255, 157, 0.2));
    font-family: var(--font-mono);
  }

  .cursor {
    color: var(--color-primary);
    opacity: 0;
    transition: opacity 0.1s;
    animation: cursorPulse 1.5s ease-in-out infinite;
  }

  .cursor.visible {
    opacity: 1;
  }

  @keyframes cursorPulse {
    0%,
    100% {
      opacity: 1;
    }
    50% {
      opacity: 0.3;
    }
  }

  .hero-subtitle {
    font-size: var(--font-size-lg);
    color: var(--color-text-light);
    margin-bottom: var(--spacing-2xl);
    line-height: 1.8;
    max-width: 750px;
  }

  .highlight {
    color: var(--color-primary);
    font-weight: 600;
    position: relative;
  }

  .hero-cta {
    display: flex;
    gap: var(--spacing-lg);
    flex-wrap: wrap;
    margin-top: var(--spacing-xl);
  }

  @media (max-width: 768px) {
    .hero {
      min-height: 90vh;
    }

    .hero-content {
      flex-direction: column;
      gap: var(--spacing-2xl);
    }

    .hero-text {
      max-width: 100%;
    }

    .image-frame {
      width: 280px;
      height: 280px;
    }

    .cyber-grid {
      background-size: 30px 30px;
    }

    .glow-orb-1,
    .glow-orb-2,
    .glow-orb-3 {
      width: 250px;
      height: 250px;
    }

    .hero-greeting {
      font-size: var(--font-size-base);
    }

    .hero-subtitle {
      font-size: var(--font-size-base);
    }

    .hero-cta {
      gap: var(--spacing-md);
    }

    .social-buttons {
      flex-direction: column;
      gap: var(--spacing-sm);
    }

    .social-btn {
      width: 100%;
      justify-content: center;
    }
  }

  @media (max-width: 480px) {
    .image-frame {
      width: 240px;
      height: 240px;
    }

    .frame-corner {
      width: 20px;
      height: 20px;
    }

    .glow-orb-1,
    .glow-orb-2,
    .glow-orb-3 {
      width: 200px;
      height: 200px;
      filter: blur(60px);
    }

    .hero-cta {
      flex-direction: column;
      width: 100%;
    }

    .btn {
      width: 100%;
      justify-content: center;
    }
  }
</style>
