---
cssClass: ["home-page", "no-width", "issues-appereance"]
---

# Inbox Notes Issues

```dataviewjs
let pages = dv.pages('"Inbox"')
	.where(
		page => page.tags && 
		(
			dv.page(page.file.path).file.tags.includes("#repNote") || 
			dv.page(page.file.path).file.tags.includes("#docNote")
		) &&
		page.status
	).sort(status[2]);

if (pages.values.length > 0) {
	let container = dv.el("div", "", {cls: "dvjs-container"});
	
	for (let page of pages) {
		let field  = dv.el("div", "", {cls: `dvjs-field ${page.status[0]}`});
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