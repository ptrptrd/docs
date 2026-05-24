---
title: Sample Language 01
date: 2026-05-24
type: knowledge
language: Sample Language 01
tags:
  - knowledge
draft: "true"
---
---
# Sample Language 01

# Journal & Session Index

```dataview
TABLE title AS "Title"
FROM "Permanent/01-10 Life Admin/01 Personal/01.20 Notes/Obsidian/Journal" OR "Permanent/01-10 Life Admin/01 Personal/01.20 Notes/Obsidian/Sessions"
WHERE contains(file.outlinks, this.file.link)
SORT date DESC
```

# Journal & Session Notes

```dataviewjs
const journalFolder = '"Permanent/01-10 Life Admin/01 Personal/01.20 Notes/Obsidian/Journal"'
const sessionsFolder = '"Permanent/01-10 Life Admin/01 Personal/01.20 Notes/Obsidian/Sessions"'

const currentNoteName = dv.current().file.name;
const pages = dv.pages(`${journalFolder} OR ${sessionsFolder}`);

function demoteHeadings(line) {
	return line.replace(/^(#{1,6})(\s+)/, (match, hashes, space) => {
		const newLevel = Math.min(6, hashes.length + 1);
		return '#'.repeat(newLevel) + space;
	});
}

for (let page of pages) {
	const content = await dv.io.load(page.file.path);
	const lines = content.split('\n');
	let output = [];
	let inside = false; 
	let targetLevel = null;
	
	for (const line of lines) {
		const headingMatch = line.match(/^(#{1,6})(\s+)/);
		
		if (!inside) {
			// Found the note part for this project
			if (headingMatch && line.includes(`[[${currentNoteName}]]`)){
				targetLevel = headingMatch[1].length;
				inside = true;
			}
		} else {
			if (headingMatch && headingMatch[1].length <= targetLevel) {
				break;
			}
			output.push(demoteHeadings(line));
		}
	}
	
	if (output.length > 0) {
		dv.header(2, `[[${page.file.name}]]`);
		dv.paragraph(output.join('\n'));
	}
}
```

---