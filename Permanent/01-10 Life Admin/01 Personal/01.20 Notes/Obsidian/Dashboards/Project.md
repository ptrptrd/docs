---
title: Project
date: 2026-05-22 23:39
type: dashboard
tags:
  - dashboard
draft: "false"
---
# Open Project

```dataview
TABLE title AS "Title"
FROM ""
WHERE type = lower("Project")
WHERE status = "in progress"
SORT date DESC
```

# Completed Project

```dataview
TABLE title AS "Title"
FROM ""
WHERE type = lower("Project")
WHERE status = "completed"
SORT date DESC
```