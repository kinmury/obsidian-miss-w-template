---
cssClass: "home-page"
tags: ["VP", ""]
---

# {Project}

> [!table-3]
>
> > [!column] Report Notes
> > `$=let files = [];dv.pages('"'+dv.current().file.folder+'/Inbox/Report Notes"').sort().where(page=>page.tags&&dv.page(page.file.path).tags.includes("repNote")).forEach((file) => {if (file.file.aliases[0]) {files.push(dv.fileLink(file.file.path,false,file.file.aliases[0]));}else{files.push(dv.fileLink(file.file.path,false,file.file.name.replace("Report Note", "RN").replace("'", ":").replace("''", ":").replace("'''", "")));}});dv.list(files);`
>
> > [!column] Document Notes
> > `$=let files = [];dv.pages('"'+dv.current().file.folder+'/Inbox/Document Notes"').sort().where(page=>page.tags&&dv.page(page.file.path).tags.includes("docNote")).forEach((file) => {if (file.file.aliases[0]) {files.push(dv.fileLink(file.file.path,false,file.file.aliases[0]));}else{files.push(dv.fileLink(file.file.path,false,file.file.name.replace("Document Note", "DN").replace("'", ":").replace("''", ":").replace("'''", "")));}});dv.list(files);`
>
> > [!column] MOCs
> > `$=dv.list(dv.pages('"' + dv.current().file.folder + '/Project-Box"').where(f=>dv.page(f.file.path).file.tags.includes("#moc")).file.link)`

## Inbox Notes Issues

```dataviewjs
let pages = dv.pages('"' + dv.current().file.folder + '/Inbox"')
	.where(
		page => page.tags && 
		(dv.page(page.file.path).file.tags.includes("#repNote") || 
		dv.page(page.file.path).file.tags.includes("#docNote")) &&
		page.status &&
		page.status[0].contains("tbd")
	).sort(status[2]);

if (pages.values.length > 0) {
	let container = dv.el("div", "", {cls: "dvjs-container"});
	
	for (let page of pages) {
		let field  = dv.el("div", "", {cls: "dvjs-field"});
		let header = dv.el("div", "", {cls: "header"});
		let time   = dv.el("div", "", {cls: "time"});
	
		header.append(dv.el(
			"a",
			dv.fileLink(page.file.path, false, page.file.aliases[0]),
			{cls: "note"})
		);
	
		let pageDate = new moment(new Date(page.status[2]));
		let timeLeft = pageDate.fromNow();
		
		time.append(dv.el(
			"i", pageDate.format("DD/MM/YYYY"),
			{attr: { title: pageDate.format("DD/MM/YYYY hh:mm:ss") + " - " + timeLeft}}
		));
	
		header.append(time);
	
		field.append(header);
		field.append(dv.el("ul", page.status[1], {cls: "tasks"}));
		
		container.append(field);
	}
} else {
	let container = dv.el("div", "#### <center>No Issues</center><br>");
}
```

## Project - Box
