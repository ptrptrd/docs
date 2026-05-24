<%*
let title = tp.file.title; 
if (title.startsWith("Untitled")) {
	title = await tp.system.prompt("Give a title to this note:");
	await tp.file.rename(title);
	await tp.hooks.on_all_templates_executed(() => {});
}
_%>

---
title: <% title %>
date: <% tp.date.now("YYYY-MM-DD HH:mm") %>
type: dashboard
tags:
  - dashboard
draft: "false"
---
# Open Project

```dataview
TABLE title AS "Title"
FROM ""
WHERE type = lower("<%title%>")
WHERE status = "in progress"
SORT date DESC
```

# Completed Project

```dataview
TABLE title AS "Title"
FROM ""
WHERE type = lower("<%title%>")
WHERE status = "completed"
SORT date DESC
```