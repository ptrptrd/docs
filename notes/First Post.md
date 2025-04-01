---
title: First post
description: Test out the workflow uploading this markdown file to Astro website.
pubDate: 01.04.2025
---

First blog? First post? All I know this is the first time I started some sort of documentation. Primarily for my future self to save time from searching through the web again. And also to remember things that I have done. 

But maybe this can be useful too to anyone comes across this blog. 

## Features 

Important features for my documentation:
- [ ] Separate content management from the actual website 
- [ ] Upload image 
- [ ] Support code annotations 
- [ ] Content should be editable from anywhere 

## Solutions 

The easiest solution seems to be using markdown files, which are hosted in a Git repository. 
These then will be taken as content for a static site.

Markdown files -> Uploaded to Git -> Trigger static site builder -> Publish to Github

### Editors 

For now Obsidian with Git plugin is used. 

### Folder Structures 

~~~bash 
|- docs 
	|- notes 
		|- assets
		|  |- something.png
		|  |- ...
		|- First Post.md	
~~~

### Image Upload

Image should be under assets as shown in folder structure. 
And relative path should be used when importing image. Such in the example below.

![](assets/ptrptrd.png)

### Website Rebuild

The folder contains also GitHub workflow file, which will trigger the rebuild of the static website. This website will then be deployed to GitHub Page. 

### Static Site 

Astro is used as static site generator. No big reason behind it. Astro 5.0 was newly released when research for this website was being done. 

## Still Missing 

- [ ] Online Obsidian like editor to be able to edit contents from anywhere