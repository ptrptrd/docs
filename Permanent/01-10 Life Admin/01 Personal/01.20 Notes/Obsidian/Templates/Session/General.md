<%*
const sessionsFolder = 'Permanent/01-10 Life Admin/01 Personal/01.20 Notes/Obsidian/Sessions'; 
const today = tp.date.now('YYYY-MM-DD'); 

let index = 1; 

while (await tp.file.exists(`${sessionsFolder}/${today} ${index}.md`)) { 
	index++; 
} 

await tp.file.rename(`${today} ${index}`)
_%>
---
title: Session - <% tp.date.now("YYYY-MM-DD HH:mm") %>
date: <% tp.date.now("YYYY-MM-DD HH:mm") %>
type: journal
tags:
  - daily
  - journal
draft: "true"
---
---
# <% tp.date.now("dddd, MMMM Do YYYY") %>