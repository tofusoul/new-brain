---
tags:
  - Obsidian
  - Obsidian/Dataview
---

| Last Modified | `= this.file.mtime` |
| ------------- | ------------------- |
|               |                     |



[[Obsidian]]
## Basic Usage

source: [Vicky Zhao's Intro Vid](https://www.youtube.com/@VickyZhaoBEEAMP)

* Anything inside the below code blocks will be executed by Dataview:
> ``` dataview
>
>```
-  To list all tasks (too many, probably shouldn't use) 
> ``` dataview
> Task
> ```
* To show list from tags (the `#TAG` is in code quotes to stop it from being parsed and render as tags, don't use quotation marks)
> ```
> Task from `#TAG`
> ```
define custom fields with `field_name::field_falue`


# Deployed  Queries
Use these as examples, currently not familiar enough with the obsidian build
In [[30 Resources/Templates/Daily|Daily]]:

> ```dataview
>LIST FROM [[]]
>WHERE contains(text,this.file.name)
> ```


``` dataview
TASK FROM ""
WHERE contains(tags, "#Obsidian/Dataview/Queries") 
GROUP BY file.link
```


