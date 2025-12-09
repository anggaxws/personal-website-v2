# Customization Guide

This guide will help you personalize your portfolio website with your own information, projects, and styling preferences.

## Quick Start Checklist

- [ ] Update personal contact information
- [ ] Add your real projects
- [ ] Update skills list
- [ ] Customize color scheme (optional)
- [ ] Add your own favicon
- [ ] Update meta tags for SEO

## 1. Personal Contact Information

**File**: [src/lib/components/Contact.svelte](src/lib/components/Contact.svelte)

Find the `contactMethods` array around line 23:

```typescript
const contactMethods = [
	{
		title: 'Email',
		value: 'your.email@example.com', // Update this
		link: 'mailto:your.email@example.com', // Update this
		icon: '✉️'
	},
	{
		title: 'LinkedIn',
		value: 'Connect with me',
		link: 'https://linkedin.com/in/yourprofile', // Update this
		icon: '💼'
	},
	{
		title: 'GitHub',
		value: 'View my code',
		link: 'https://github.com/yourusername', // Update this
		icon: '💻'
	}
];
```

Also update the email in the "Get In Touch" button around line 51:

```html
<a href="mailto:your.email@example.com" class="btn btn-primary">
```

## 2. Update Projects

**File**: [src/lib/components/Projects.svelte](src/lib/components/Projects.svelte)

Replace the example projects with your real projects (around line 23):

```typescript
const projects = [
	{
		title: 'Your Project Name',
		description: 'Brief description of what the project does and its impact',
		tech: ['Technology', 'Stack', 'Used'],
		category: 'Project Category'
	},
	// Add more projects...
];
```

Tips:
- Keep descriptions concise (2-3 sentences)
- List 3-5 key technologies per project
- Categories help visitors understand the project focus

## 3. Update Skills

**File**: [src/lib/components/Skills.svelte](src/lib/components/Skills.svelte)

Modify the `skillCategories` array (around line 23):

```typescript
const skillCategories = [
	{
		title: 'Your Category',
		skills: ['Skill 1', 'Skill 2', 'Skill 3']
	},
	// Add more categories...
];
```

Tips:
- Group related skills together
- List skills you're confident demonstrating
- Keep skill names concise

## 4. Update About Section

**File**: [src/lib/components/About.svelte](src/lib/components/About.svelte)

The about text is already populated with your information from the prompt, but you can refine it further around lines 28-50.

You can also customize the highlights array:

```typescript
const highlights = [
	{
		title: 'Your Highlight',
		description: 'Brief description'
	},
	// Add more highlights...
];
```

## 5. Customize Hero Section

**File**: [src/lib/components/Hero.svelte](src/lib/components/Hero.svelte)

Update the hero text around lines 17-27:

```html
<h1 class="hero-title">
	Your Name<br />
	<span class="gradient-text">Your Title</span>
</h1>
<p class="hero-subtitle">
	Your elevator pitch or tagline
</p>
```

## 6. Customize Colors

**File**: [src/app.css](src/app.css)

Change the color scheme by updating CSS variables (lines 4-12):

```css
:root {
	/* Primary brand color (used for links, buttons) */
	--color-primary: #2563eb; /* Blue */
	--color-primary-hover: #1d4ed8;

	/* Secondary accent color */
	--color-secondary: #0d9488; /* Teal */

	/* Accent color for hover states */
	--color-accent: #f59e0b; /* Amber */

	/* Text colors */
	--color-text: #1f2937;
	--color-text-light: #6b7280;

	/* Background colors */
	--color-background: #ffffff;
	--color-surface: #f9fafb;
	--color-border: #e5e7eb;
}
```

### Color Scheme Ideas

**Professional Blue & Green:**
```css
--color-primary: #0ea5e9;
--color-secondary: #10b981;
--color-accent: #f59e0b;
```

**Tech Purple & Blue:**
```css
--color-primary: #8b5cf6;
--color-secondary: #3b82f6;
--color-accent: #ec4899;
```

**Modern Indigo & Cyan:**
```css
--color-primary: #6366f1;
--color-secondary: #06b6d4;
--color-accent: #f97316;
```

## 7. Update Favicon

Replace the default favicon:

1. Create or download your favicon image
2. Replace [src/lib/assets/favicon.svg](src/lib/assets/favicon.svg) with your own
3. Or update the link in [src/routes/+layout.svelte](src/routes/+layout.svelte)

## 8. Update Meta Tags (SEO)

**File**: [src/routes/+layout.svelte](src/routes/+layout.svelte)

Update the title and description (around lines 10-11):

```html
<title>Your Name - Portfolio</title>
<meta name="description" content="Your custom description for search engines" />
```

You can also add additional meta tags:

```html
<meta property="og:title" content="Your Name - Portfolio" />
<meta property="og:description" content="Your description" />
<meta property="og:image" content="/your-preview-image.jpg" />
<meta name="twitter:card" content="summary_large_image" />
```

## 9. Update Navigation Logo

**File**: [src/lib/components/Navigation.svelte](src/lib/components/Navigation.svelte)

Change "Portfolio" to your name or brand (around line 43):

```html
<span class="logo-text">Your Name</span>
```

## 10. Update Footer

**File**: [src/lib/components/Contact.svelte](src/lib/components/Contact.svelte)

Update the footer text around line 68:

```html
<p class="footer-copyright">© 2024 Your Name. All rights reserved.</p>
```

## Testing Your Changes

After making changes:

1. Check the development server at `http://localhost:5173/`
2. Test responsiveness by resizing your browser
3. Test navigation and smooth scrolling
4. Check all links work correctly
5. Test on mobile devices

## Build for Production

When you're happy with your changes:

```bash
npm run build
npm run preview
```

This builds and previews the production version of your site.

## Need Help?

- [SvelteKit Documentation](https://svelte.dev/docs/kit)
- [Svelte Tutorial](https://learn.svelte.dev/)
- [CSS Variables Guide](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties)
