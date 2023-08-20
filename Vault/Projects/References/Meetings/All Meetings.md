---
date_created: 2023-08-08
date_modified: 2023-08-08
document_type: meetings
project: References
description: List of project meetings.
tags: references meetings
---
[[Projects/References/Home|Home]] | **[[Projects/References/Meetings/All Meetings|Meetings]]** | [[Projects/References/Notes/All Notes|Notes]] | [[Projects/References/References|References]]
# Meetings
**Create meeting**
```button
name + Add meeting
type note(Projects/References/Meetings/untitled meeting) template
action project/Project meeting
templater true
class tailwind-button-white
```
```dataviewjs
for (let group of dv.pages('"Projects/References/Meetings" and !#meetings').groupBy(p => p.meeting)) {
	dv.table(["Name", "Description", "Date created"], 
		group.rows 
			.sort(k => k.file.ctime, 'desc')
			.map(k => [
			k.file.link, 
			k['description'],
			k.file.ctime.year+"-"+k.file.ctime.month+"-"+k.file.ctime.day
			]))}
```

---
[[Projects/References/Home|Home]] | **[[Projects/References/Meetings/All Meetings|Meetings]]** | [[Projects/References/Notes/All Notes|Notes]] | [[Projects/References/References|References]]