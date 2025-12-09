# Portfolio Website

A modern, responsive portfolio website built with SvelteKit for a Business Informatics Master's student with expertise in Full-Stack Development and Artificial Intelligence.

## Features

- **Modern Design**: Clean, professional UI with a blue/teal color scheme
- **Fully Responsive**: Optimized for desktop, tablet, and mobile devices
- **Smooth Animations**: Subtle micro-interactions and scroll-based animations
- **Dark Mode Support**: Automatic dark mode based on system preferences
- **Sections**:
  - Hero/Intro with call-to-action buttons
  - About section with background and highlights
  - Projects showcase with categorized examples
  - Skills organized by category
  - Contact information with social links
  - Responsive navigation with mobile menu

## Tech Stack

- **Framework**: SvelteKit (Svelte 5)
- **Language**: TypeScript
- **Styling**: Custom CSS with CSS variables for theming
- **Build Tool**: Vite

## Getting Started

### Prerequisites

- Node.js (v20.19, v22.12, or v24+)
- npm, pnpm, or yarn

### Installation

1. Clone the repository
2. Install dependencies:

```bash
npm install
```

### Development

Start the development server:

```bash
npm run dev
```

Or open in browser automatically:

```bash
npm run dev -- --open
```

The site will be available at `http://localhost:5173/`

### Building for Production

Create a production build:

```bash
npm run build
```

Preview the production build:

```bash
npm run preview
```

## Customization

### Update Personal Information

1. **Contact Details**: Edit the `contactMethods` array in [src/lib/components/Contact.svelte](src/lib/components/Contact.svelte#L23-L37)
2. **Projects**: Modify the `projects` array in [src/lib/components/Projects.svelte](src/lib/components/Projects.svelte#L23-L51)
3. **Skills**: Update the `skillCategories` in [src/lib/components/Skills.svelte](src/lib/components/Skills.svelte#L23-L44)
4. **About Content**: Edit the text in [src/lib/components/About.svelte](src/lib/components/About.svelte#L28-L50)

### Customize Colors

Edit the CSS variables in [src/app.css](src/app.css#L3-L50) to change the color scheme:

```css
:root {
	--color-primary: #2563eb; /* Main brand color */
	--color-secondary: #0d9488; /* Secondary accent */
	--color-accent: #f59e0b; /* Hover states */
	/* ... */
}
```

## Project Structure

```
src/
├── app.css                      # Global styles and design system
├── routes/
│   ├── +page.svelte            # Main page
│   └── +layout.svelte          # Root layout
└── lib/
    └── components/
        ├── Navigation.svelte   # Fixed navigation bar
        ├── Hero.svelte         # Hero section
        ├── About.svelte        # About section
        ├── Projects.svelte     # Projects showcase
        ├── Skills.svelte       # Skills grid
        └── Contact.svelte      # Contact section and footer
```

## Deployment

The site can be deployed to various platforms:

- **Vercel**: Automatic deployment from Git
- **Netlify**: Connect your repository
- **Cloudflare Pages**: Deploy via Git integration
- **Static Hosting**: Build and upload the `build` folder

You may need to install a specific [adapter](https://svelte.dev/docs/kit/adapters) for your deployment target.

## License

This project is open source and available for personal and commercial use.
# personal-website-v2
