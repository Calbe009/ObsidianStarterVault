---
date_created: 2023-08-08
date_modified: 2023-08-08
document_type: project-dashboard
is_active: true
project: References
tags: dashboard project references
---
**[[Projects/References/Home|Home]]** | [[Projects/References/Meetings/All Meetings|Meetings]] | [[Projects/References/Notes/All Notes|Notes]] | [[Projects/References/References|References]]
# References
**Description**:: 
**Link**: *add link (if relevant)*


## Tasks
*[[Projects/References/Tasks|+ Add a task]]*
```dataviewjs 
dv.taskList(dv.pages('"Projects/References"').file.tasks .where(t => !t.completed))
```

## Meetings
```button
name + Add meeting
type note(Projects/References/Meetings/untitled meeting) template
action project/Project meeting
templater true
class tailwind-button-white
```
```dataviewjs
for(let group of dv.pages('"Projects/References/Meetings" and !#meetings').limit(10).groupBy(p => p.meeting)) {
	dv.table(["Name", "Description", "Date created"], 
		group.rows 
			.sort(k => k.file.ctime, 'desc')
			.map(k => [
			k.file.link, 
			k['description'],
			k.file.ctime.year+"-"+k.file.ctime.month+"-"+k.file.ctime.day
			]))}
```
*Only showing the last 10 meetings*
*[[Projects/References/Meetings/All Meetings|View all meetings →]]*

## Notes
```button
name + Add note
type note(Projects/References/Notes/untitled note) template
action project/Project note
templater true
class tailwind-button-white
```
```dataviewjs
for(let group of dv.pages('"Projects/References/Notes" and !#dashboard and !#notes').limit(10).groupBy(p => p.note)) {
	dv.table(["Name", "Description", "Date created"], 
		group.rows 
			.sort(k => k.file.ctime, 'desc')
			.map(k => [
			k.file.link, 
			k['description'],
			k.file.ctime.year+"-"+k.file.ctime.month+"-"+k.file.ctime.day
			]))}
```
*Only showing the last 10 notes*
*[[Projects/References/Notes/All Notes|View all notes →]]*

---
**[[Projects/References/Home|Home]]** | [[Projects/References/Meetings/All Meetings|Meetings]] | [[Projects/References/Notes/All Notes|Notes]] | [[Projects/References/References|References]]