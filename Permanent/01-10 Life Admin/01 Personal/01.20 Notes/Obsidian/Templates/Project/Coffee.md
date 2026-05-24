<%*
let title = tp.file.title; 
if (title.startsWith("Untitled")) {
	title = await tp.system.prompt("Give a title to this general project note:");
	await tp.file.rename(title);
	await tp.hooks.on_all_templates_executed(() => {});
}
_%>

---
title: <% title %>
start date: <% tp.date.now("YYYY-MM-DD") %>
type: project
tags:
  - project
  - coffee
draft: "true"
status: in progress
---
---
# <% title %>

# Seller

# Brew Method

# Notes
