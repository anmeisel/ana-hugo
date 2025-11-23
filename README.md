# Ana on Hugo

To view locally, simply run:
`hugo server` in the root.

# Guide

I came across hugo around 2018? I wanted an easy static site generator and saw that low tech magazine were using it. I wanted to steal LTM's page size calculator as well but never got it to work.

Anyway, here's a little intro to how my hugo site is configured. I can't write about the md files specifically (which is where all my info lies) but here's the "heart" of the site...

I can define my site settings in here:

```{.toml file=hugo.toml}
baseURL = 'https://ana.help'
languageCode = 'en-us'
title = 'Ana Meisel'
theme = 'hugo-PaperMod'
description = '㋡'
[markup.goldmark.renderer]
unsafe = true
```

- `baseURL`: We're starting with the website's canonical URL.
- `languageCode`: Define your language for site translators.
- `title` and `description`: Meta title and meta description for SEO
- `theme`: You also have to use a theme (kinda like wp?)
- We have to then use the Goldmark library to render Markdown files into HTML using `[markup.goldmark.renderer]`
- And `unsafe = true` is for the Goldmark Markdown renderer. It enables the rendering of raw HTML from Markdown files. By default, Hugo's Goldmark renderer ignores this HTML for security reasons, but setting this option to true allows you to include custom HTML elements, such as styled text, tables, or complex layouts.

I haven't modified anything from my original layout defined in the `hugo-PaperMod` other than my `.md` files in `content/` and my css. The markdown is pretty self-explanatory, so let's have a look at my css.

I constructed my website into 2 columns.

This is my left side:

```{.css file=assets/css/common/post-entry.css}
.left-entry {
    position: relative;
    display: inline-block;
    vertical-align: top;
    width: calc(50%);
    z-index: 2;
    /* it needs to be above the right side */
    color: green !important;
}
```

This is my right side:

```{.css file=assets/css/common/post-entry.css}
.right-entry {
    position: absolute;
    display: inline-block;
    vertical-align: top;
    left: 0;
    width: calc(50%);
    margin-left: calc(50%);
}
```

My text content within posts:

```{.css file=assets/css/common/post-entry.css}
.post-content {
  font-size: 12px;
  margin-left: 20px;
  margin-top: 3px;
  margin-bottom: 20px;
}
```

For my text and image formatting:

```{.css file=assets/css/common/post-entry.css}
.entry-header h2 {
  font-size: 15px;
  margin-left: 20px;
}

.entry-content {
  margin: 8px 0;
  color: var(--secondary);
  font-size: 12px;
  line-height: 1.6;
  overflow: hidden;
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-line-clamp: 2;
  margin-left: 20px;
}

.entry-footer {
  color: var(--secondary);
  font-size: 10px;
  margin-left: 20px;
  margin-top: var(--content-gap);
}

.entry-link {
  position: absolute;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
}

.entry-cover,
.entry-isdraft {
  font-size: 14px;
  color: var(--secondary);
}

.entry-cover {
  margin-bottom: var(--gap);
  text-align: center;
  height: 100vh;
  width: 50vw;
  overflow: hidden;
}

.entry-cover img {
  /* border-radius: var(--radius); */
  pointer-events: none;
  object-fit: cover;
  height: 100vh;
  width: 100%;
}

.entry-cover a {
  color: var(--secondary);
  /* box-shadow: 0 1px 0 var(--primary); */
  text-decoration: wavy;
}
```

For my cv (not in use):

```{.css file=assets/css/common/post-entry.css}
.experience {
  position: absolute;
  top: -2em;
  left: 0;
  margin-left: 30vw;
  width: 65vw;
  padding-left: 2em;
}

.info {
  width: 30vw;
}
```

My floating unicodes exist in `assets/css/common/main.css` using the `.floating` class, along with my other _weird_ and _quirky_ styling like image loading using (`blurred-img`)and link of the week box using (`flame`).

You would think that footer styling would go into `footer.css` because it's positioned at the bottom of my page but to everyone's surprise my accessibility toggle is called with `.logo` in `assets/css/common/header.css`. I think I must have decided to put this where the footer is later and forgot to rename my class _and_ put it in the right css component.

However, my GitHub link and page size renderer are in the correct places and we'll be relieved to refer to `assets/css/common/footer.css` for this.

Back to my `header.css`, you'll find my static links, lazy loading, and accessibility ui.

My `post-single.css` contains more granular styling around text and link colours and indentation.
