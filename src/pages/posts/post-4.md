---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Automatically generated blog post list"
author: "Paul Bilinas"
pubDate: 11/11/2026
description: "Discusses the use of import.meta.glob to retrieve posts at compile time."
image:
    url: "https://docs.astro.build/default-og-image.png"
    alt: "The word astro against an illustration of planets and stars."
tags: ["astro"]
---
Instead of manually updating a blog post list every time a new post is created, we can use Astro's import.meta.glob function to retrieve a list of files. For example, to retrieve all markdown files from the posts folder, we place the following line in the frontmatter:

`const allPosts = Object.values(import.meta.glob('./posts/*.md', { eager: true }));`

Now to dynamically generate the list on our blog page, we use the map function to generate the html for each post:

`{allPosts.map((post: any) => <li><a href={post.url}>{post.frontmatter.title}</a></li>)}`