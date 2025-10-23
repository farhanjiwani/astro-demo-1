# Astro

> [Pre-built Astro Demo Sites](https://astro.new/) > [Discord for help](https://astro.build/chat)

-   framework for **content-driven** websites
    -   blogs, marketing & e-commerce
-   reduce JS overhead/complexity
-   strengths: performance and SEO
-   MPA not SPA!

## Features

-   AIO web framework
-   Islands
    -   component-based arch
    -   render most of the page fast with static HTML
    -   smaller islands of JS added when needed
    -   selective hydration
-   UI-agnostic
-   server-first
-   zero JS by default
-   content collections
    -   organize, validate, type-safety
-   customizable
    -   many integrations and API hooks
-   easy to use
-   developer focused
-   content-driven

## Islands

### Client Islands

-   better performance
-   parallel loading
    -   not blocking the higher priority component (header)

Static HTML/CSS vs interactive (with the `client:*` prop)

```JSX
<MyComponent />

<MyComponent client:load />
```

-   `client:idle` only load when browser is idle
-   `client:visible` only load once it enters the viewport

### Server Islands

-   move expensive/slower code out of the way of the main rendering process
-   `server:defer` to make a server island
-   render fallback content to prevent CLS

```JSX
import MyComponent from "../MyComponent.astro"
<MyComponent server:defer />
```

---

---

## Blog Example Tutorial

> [Final Example Code](https://github.com/withastro/blog-tutorial-demo)
>
> > [IDX Version](https://idx.google.com/import?url=https:%2F%2Fgithub.com%2Fwithastro%2Fblog-tutorial-demo%2F) > > [StackBlitz Version](https://stackblitz.com/github/withastro/blog-tutorial-demo/tree/complete?file=src%2Fpages%2Findex.astro)

### Environment Setup

> https://docs.astro.build/en/tutorial/1-setup/

```bash
npm create astro@latest

# From install dir:
npm run dev
```

-   Install VSCode extension: [Astro language support extension](https://marketplace.visualstudio.com/items?itemName=astro-build.astro-vscode)
-   Edit `src/pages/index.astro` and see hot reload on save

### Create Pages & Posts

```markdown
---
title: 'My First Blog Post'
pubDate: 2022-07-01
description: 'This is the first post of my new Astro blog.'
author: 'Astro Learner'
image:
    url: 'https://docs.astro.build/assets/rose.webp'
    alt: 'The Astro logo on a dark background with a pink glow.'
tags: ['astro', 'blogging', 'learning in public']
---

[Markdown to be converted to HTML goes here]
```

-   just add pages to `/src/pages`
-   just use regular anchors for routing

```HTML
<a  href="/">Home</a>
<a  href="/about/">About</a>
```

-   add `posts/` in `pages/` along with markdown files
    -   `post-1.md` will be at URL `/posts/post-1
    -   `post-2.md` (if doesn't exist) will give 404
-   add "frontmatter" data in the code fences
    -   can use JavaScript or YAML
    -   can be used within the markdown content within `{}`, like JSX
    -   theses JS vars can also be used in the CSS

```astro
---
const  pageTitle  =  "About Me";
const identity = {
  firstName: "Sarah",
  country: "Canada",
  occupation: "Technical Writer",
  hobbies: ["photography", "birdwatching", "baseball"],
};
const skills = ["HTML", "CSS", "JavaScript", "React", "Astro", "Writing Docs"];
---
<h1>{pageTitle}</h1>
```

#### Styles

-   can just use `<style>` in the page's HTML markup
-   `define:vars={ {...} }` directive allows CSS to reference frontmatter
-   global styles can go into `src/styles/global.css` or something, then
    -   `import  '../styles/global.css';` in the frontmatter

```astro
---
// CSS Variables, but _not_ "CSS Variables", but accessed like "CSS Variables"
const skillColor = "crimson"
---
<style define:vars={{skillColor}}>
	.skill {
		color: var(--skillColor);
	}
</style>
```

### Build w/ Astro Components

### Query and Work w/ Local Files

### Add Interactivity

### Deploy
