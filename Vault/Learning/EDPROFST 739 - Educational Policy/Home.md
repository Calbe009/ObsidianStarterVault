---
date_created: 2023-08-08
date_modified: 2023-08-08
document_type: course
tags: sub-dashboard course
---
[[Learning/Learning Dashboard|Learning Dashboard]] / **[[Learning/EDPROFST 739 - Educational Policy/Home.md|EDPROFST 739 - Educational Policy]]**
# EDPROFST 739 - Educational Policy
**Overview**
Title:: MEdLd - EDPROFST 739
Subject:: Educational Policy
Description:: 
Completed:: false
Link:: 


## Actions
```button
name + Add lecture
type note(Learning/EDPROFST 739 - Educational Policy/Lectures/unnamed lecture) template
action learning/Course lecture
templater true
class tailwind-button-white
```

```button
name + Add assignment
type note(Learning/EDPROFST 739 - Educational Policy/Assignments/unnamed assignment) template
action learning/Course assignment
templater true
class tailwind-button-white
```

```button
name + Add note
type note(Learning/EDPROFST 739 - Educational Policy/Notes/unnamed note) template
action learning/Course note
templater true
class tailwind-button-white
```


## Lectures
```dataviewjs
for (let group of dv.pages('"Learning/EDPROFST 739 - Educational Policy" and #lecture').groupBy(p => p.lecture)) {
	dv.table(["Lecture", "Description", "Date created"], 
		group.rows 
			.sort(k => k.file.ctime, 'desc')
			.map(k => [
			k.file.link, 
			k['description'],
			k.file.ctime.year+"-"+k.file.ctime.month+"-"+k.file.ctime.day
			]))
}
```


## Assignments

```dataviewjs
for (let group of dv.pages('"Learning/EDPROFST 739 - Educational Policy" and #assignment').groupBy(p => p.lecture)) {
	dv.table(["Lecture", "Completed", "Date created"], 
		group.rows 
			.sort(k => k.file.ctime, 'desc')
			.map(k => [
			k.file.link, 
			k['completed'],
			k.file.ctime.year+"-"+k.file.ctime.month+"-"+k.file.ctime.day
			]))
}
```


## Notes
```dataviewjs
for (let group of dv.pages('"Learning/EDPROFST 739 - Educational Policy" and #course-note').groupBy(p => p.lecture)) {
	dv.table(["Note", "Description"], 
		group.rows 
			.sort(k => k.file.ctime, 'desc')
			.map(k => [
			k.file.link, 
			k['description']
			]))
}
```


---
[[Learning/Learning Dashboard|Learning Dashboard]] / **[[Learning/EDPROFST 739 - Educational Policy/Home.md|EDPROFST 739 - Educational Policy]]**