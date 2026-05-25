---
title: Sample Project 01
start date: 2026-05-24
type: project
draft: "false"
status: completed
tags:
  - project
  - photo
  - video
  - publishing
---
# Sample Project 01

# Progression

## Photos
- [ ] Import to Lightroom
- [ ] Photo Selection
- [ ] Editing Others' Photos
- [ ] Editing Own Photos
- [ ] Portfolio Selection
- [ ] Done

## Videos
- [ ] Footage Selection
- [ ] Editing Own Footage
- [ ] Portfolio Selection
- [ ] Done

# Notes

---
# Tasks

```dataview
TASK 
FROM "Permanent/01-10 Life Admin/01 Personal/01.20 Notes/Obsidian/Journal" OR "Permanent/01-10 Life Admin/01 Personal/01.20 Notes/Obsidian/Sessions"
WHERE contains(text, "[[" + this.file.name + "]]")
SORT file.name ASC
```

---
# Journal & Session Index

<!-- QueryToSerialize: TABLE title AS "Title" FROM "Permanent/01-10 Life Admin/01 Personal/01.20 Notes/Obsidian/Journal" OR "Permanent/01-10 Life Admin/01 Personal/01.20 Notes/Obsidian/Sessions" WHERE contains(file.outlinks, this.file.link) SORT date DESC -->
<!-- SerializedQuery: TABLE title AS "Title" FROM "Permanent/01-10 Life Admin/01 Personal/01.20 Notes/Obsidian/Journal" OR "Permanent/01-10 Life Admin/01 Personal/01.20 Notes/Obsidian/Sessions" WHERE contains(file.outlinks, this.file.link) SORT date DESC -->

| File                                                                                                       | Title                      |
| ---------------------------------------------------------------------------------------------------------- | -------------------------- |
| [[Sample Session]] | Session - 2026-05-11 21:42 |
| [[Sample Journal]]  | Journal - 2026-05-10       |

<!-- SerializedQuery END -->

# Journal & Session Notes

<!-- DataviewJSToSerialize:
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
-->
<!-- SerializedDataviewJS -->
## [[Sample Journal]]


This is a test note to test project template. 

#### Sub Progress 1

This progress should still be included in the project note. 


## [[Sample Session]]


Starting doing photo and video 

### Next ToDo 

- [ ] Check photo number 1 [[Sample Project 01]]  


### [[Sample Knowledge 01]]

This is a basic information. 

#### Reference 

Check https://wikipedia.com.


### [[Sample Music 01]]

- [ ] Start sampling drum. [[Sample Music 01]]

#### Mixing 

- [ ] Turn vocal's volume down. [[Sample Music 01]]
- [ ] Add new task. [[Sample Music 01]]
<!-- SerializedDataviewJS END -->





