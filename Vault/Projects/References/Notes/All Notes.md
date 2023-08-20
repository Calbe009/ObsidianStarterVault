---
date_created: 2023-08-08
date_modified: 2023-08-08
document_type: notes
project: References
description: List of project notes.
tags: references notes
---
[[Projects/References/Home|Home]] | [[Projects/References/Meetings/All Meetings|Meetings]] | **[[Projects/References/Notes/All Notes|Notes]]** | [[Projects/References/References|References]]
# Notes
**Create new note**
```button
name + Add note
type note(Projects/References/Notes/untitled note) template
action project/Project note
templater true
class tailwind-button-white
```
**Flat view**
```dataviewjs
for (let group of dv.pages('"Projects/References/Notes" and !#dashboard and !#notes').groupBy(p => p.note)) {
	dv.table(["Name", "Description", "Date created"], 
		group.rows 
			.sort(k => k.file.ctime, 'desc')
			.map(k => [
			k.file.link, 
			k['description'],
			k.file.ctime.year+"-"+k.file.ctime.month+"-"+k.file.ctime.day
			]))}
```


**Hierarchical view**
```dataviewjs
for (let group of dv.pages('"Projects/References/Notes" and !#dashboard and !#notes').groupBy(p => p.file.folder)) {
  let headerLevel = group.key.split("/").length;
  dv.header(headerLevel, `${group.key.replace(group.key.split("/")[0], "").slice(1).replaceAll("/", " / ")}`);  
  dv.table(["Name", "Description", "Date created"],
  group.rows.map(k => [k.file.link, k['description'], k.file.ctime.year+"-"+k.file.ctime.month+"-"+k.file.ctime.day]))
}
```

---
[[Projects/References/Home|Home]] | [[Projects/References/Meetings/All Meetings|Meetings]] | **[[Projects/References/Notes/All Notes|Notes]]** | [[Projects/References/References|References]]