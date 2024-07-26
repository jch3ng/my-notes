---
entity: "[[howto]]"
---

`dv.queryMarkdown` can write to a file. In my case, I only use Templater for my Daily Note template:

```
 << [[<% moment(tp.file.title, "YYYY-MM-DD").subtract(1, "days").format("YYYY-MM-DD-ddd") %>]] |  `<% moment(tp.file.title, "YYYY-MM-DD").add(0, "days").format("YYYY-MM-DD-ddd") %>`  | [[<% moment(tp.file.title, "YYYY-MM-DD").add(1, "days").format("YYYY-MM-DD-ddd") %>]] >>
```


```
<%*
dv = this.app.plugins.plugins["dataview"].api;
const fileTitle = tp.file.title;
const query = `LIST from [[podcast]]`; 
const out = await dv.queryMarkdown(query);
tR += out.value;
%>
```