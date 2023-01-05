---
draft: true
date: 2022-12-20T14:43:58+01:00
lastmod: null
title: 'The Making of This Website'
description: null
summary: null
tags: [blog, hugo, pico]
---

There is a saying that the first task on a ToDo list should be "Write a ToDo list".
In that spirit, the first (real) post on a new blog should be about the blog itself.
This post will describe the motivation for and the superficial technical details of this blog
(or rather, the website).

## The Motivation - Why Create a Website?

I've had this domain lying around unused for a year already.
Initially, I only bought it for having a custom E-Mail address.
Back then, I already considered building a website, but it was a plan that kept being pushed back
in favor of other tasks or simply normal life.
Besides, I could never really decide on what purpose I wanted my hypothetical website to _achieve_.
Do I want to build a flashy portfolio? Do I want to create a blog? Do I want to have
a minimal site for showing personal information?
This decision-to-be-made lingered in the back of my ToDo list for about a year until a few weeks
ago, when I read a random comment on [HN](https://news.ycombinator.com) claiming how valueable
having a blog is.
Newly motivated by this comment, I decided to finally tackle this task and created a mental list of
goals and non-goals that I wanted my website-to-be to fulfill:

**Goals:**

- ❗️ It _must_ be as **cheap** as possible (#student-budget).
- ❗️ It _must_ be as simple as possible to **maintain** the page, ideally for a **long time**.
- ❗️ It _must_ be possible to **set** the **initial** website **up** in a relatively **short timeframe**.
- ❕ It _should_ be possible to create "content-pages" (e.g. for a blog) and "normal HTML-based pages"
  (e.g. for the homepage).
- ❔ It would be _nice_ to be able to write **content** in a markup language like **Markdown** or **AsciiDoc**.
- ❔ It would be _nice_ to be able to use **Git** for **content management**.

**Non-Goals:**

- ❌ It _does not_ need a fully-fledged CMS.
- ❌ It _does not_ need interactivity (e.g. comment-boxes) and/or account management.
- ❌ It _does not_ need a flashy, custom design **in the first version**.

## Choosing The Technology

Driven by the above points, I went on a market research regarding which technologies are out there.
One thing became clear very quickly:
There are very many options out there for building your own website/blog.
Too many, in fact.
In a certain sense, it felt overwhelming.
From toolbox-like frameworks to plug-and-play solutions, from Astro to Wordpress, there are a lot options
which all have their respective pros and cons which would have to be evaluated.
In the end, I decided to short-circuit the process by choosing an application that was often recommended
in various online forums: Hugo.

### Hugo

[Hugo](https://gohugo.io) is an established solution for a lot of blogs.
It is a static site generator focused on performance.
From my perspective, Hugo is fantastic for unopinionated DIY projects:
When you setup a new Hugo project and run it, you see... absolutely nothing in the browser.
By default, Hugo doesn't even come with a theme installed.
It basically forces you to either find a premade theme or build your own one.

I myself was determined to go with the second route.
Using an off the shelf theme would work, but I wouldn't learn anything about Hugo by using one
(and I wanted to learn how Hugo works!).
In addition, having a custom theme means that, while it is certainly more work, you do have more
control over it.
I will be responsible for maintaining it, but I can granularly control what does and what doesn't show up.
It will be my very own website.

### Pico.css

The problem with building your own website is that a website, typically, needs some kind of design
and while I do consider myself good at *judging* designs, I did not at all feel motivated to come
up with my own one for this project.
I also knew that I would already have to spend a big amount of my available time on learning Hugo
in order to quickly come up with a good result.
Creating a good looking design in parallel was basically not even an option to consider.
No, I needed a CSS library which does the heavy lifting.

After evaluating a few options, I decided on [Pico.css](https://picocss.com) which describes itself
as a "minimal CSS Framework for semantic HTML".
Indeed, the coolest aspect of Pico is that, as long as you use its intended semantic HTML tags,
you don't need to worry about CSS at all.
There are, apart from a few exceptions, no CSS classes.
Each HTML tag has a default style - and that is it.
While I do believe that this approach will not work out well for "larger" sites, it is a very good
choice for this one for the following reasons:

* It allows to me to have a good-looking design without putting in any effort.
* Not having to apply any CSS classes in the code means that, if I later want to use another
  design, I won't have to do a lot of cleanup. Removing the stylesheet will be enough.
* In order to correctly style the site, I must use semantic HTML (which is always a good thing).

One thing to note is that, while Pico does a lot of heavy lifting, I still had to write
[custom CSS](https://github.com/manuelroemer/site/blob/550b5354aae683f39b84f76a0f7bbe99a8b0f42c/static/css/global.css)
in the end, mainly for aligning elements.
By using atomic CSS and thus by combining the different rules in HTML, I could minimize
the CSS to be written though.

### NPM and Prettier

The above two technologies, Hugo and Pico.css, already allow for the creation of a fully-fledged
website.
And in the spirit of my goals above, I am very hesitant about adding more technologies and dependencies
than absolutely required.
After all, having more dependencies typically implies more maintenance - a non-goal, for this website.
However, there is one thing that I don't want to live without anymore when working with code: Formatters.
In the web space, Prettier has become my go-to formatter of choice and, if possible, I wanted to have
it integrated into the repository.
It turns out that it *is* possible.
The only requirement for it to work with Hugo's templating engine is a plugin:
[prettier-plugin-go-template](https://github.com/NiklasPor/prettier-plugin-go-template).

Using prettier (and the plugin) implicitly adds one additional dependency though: NPM.
In my eyes, that actually brings an advantage:
By having NPM set up in your repository, you automatically gain a simple task runner for free via
the `scripts` section in the `package.json` file.
I used that opportunity and placed common commands like starting the dev server or formatting
the repository in my [`package.json` file](https://github.com/manuelroemer/site/blob/550b5354aae683f39b84f76a0f7bbe99a8b0f42c/package.json).

### GitHub Pages

At this point, everything required for building the website was decided.
There was only one point missing: Where and how do I deploy the website once it is done?

This was, by far, the simplest decision:
Since Hugo is a static site generator, any static site hoster would work.
Considering that I was already using GitHub for the repository (and thus also GitHub actions for building it),
using GitHub pages for hosting the artifacts seemed like the obvious choice.
The best part about GitHub pages is that it is entirely free - an appealing price tag, especially when
considering my goal #1.

## Building The Website

## Deploying The Website

## Outlook and Conclusion