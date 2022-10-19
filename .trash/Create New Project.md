%%DONE%%<%*
let homeNote = `---
cssClass: "home-page"
tags: ["VP", ""]
---

# {Project}

> [!table-3]
>
> > [!column] Report Notes
> > \`$=let files = dv.pages('"' + dv.current().file.folder + '/Inbox/Report Notes"').where(page=>dv.page(page.file.path).tags.includes("repNote"));let array = [];for (let file = 0; file < files.length; file++) {array.push(dv.fileLink(files[file].file.path,false, files[file].file.aliases[0]));}dv.list(dv.array(array))\`
>
> > [!column] Document Notes
> > \`$=let files = dv.pages('"' + dv.current().file.folder + '/Inbox/Document Notes"').where(page=>dv.page(page.file.path).tags.includes("docNote"));let array = [];for (let file = 0; file < files.length; file++) {array.push(dv.fileLink(files[file].file.path,false, files[file].file.aliases[0]));}dv.list(dv.array(array))\`
>
> > [!column] MOCs
> > \`$=dv.list(dv.pages('"' + dv.current().file.folder + '/Project-Box"').where(f=>dv.page(f.file.path).file.tags.includes("#moc")).file.link)\`

## Inbox Notes Issues

\`\`\`dataviewjs
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
\`\`\`

## Project - Box
`

let issuesNote = `---
cssClass: "home-page"
---

# {Project} Issues

> [!table-4]
> 
> > [!column] TBD
> > \`$=let files = dv.pages('"' + dv.current().file.folder + '/Issues"').where(page=>dv.page(page.file.path).tags && dv.page(page.file.path).tags.includes("issue") && dv.page(page.file.path).status.contains("tbd"));let array = [];for (let file = 0; file < files.length; file++) {array.push(dv.fileLink(files[file].file.path, false, files[file].file.aliases[0]));}dv.list(dv.array(array));\`
> 
> > [!column] In-Progress
> > \`$=let files = dv.pages('"' + dv.current().file.folder + '/Issues"').where(page=>dv.page(page.file.path).tags && dv.page(page.file.path).tags.includes("issue") && dv.page(page.file.path).status.contains("in-progress"));let array = [];for (let file = 0; file < files.length; file++) {array.push(dv.fileLink(files[file].file.path, false, files[file].file.aliases[0]));}dv.list(dv.array(array));\`
>
> > [!column] Review
> > \`$=let files = dv.pages('"' + dv.current().file.folder + '/Issues"').where(page=>dv.page(page.file.path).tags &&dv.page(page.file.path).tags.includes("issue") && dv.page(page.file.path).status.contains("review"));let array = [];for (let file = 0; file < files.length; file++) {array.push(dv.fileLink(files[file].file.path, false, files[file].file.aliases[0]));}dv.list(dv.array(array));\`
> 
> > [!column] Done
> > \`$=let files = dv.pages('"' + dv.current().file.folder + '/Issues"').where(page=>dv.page(page.file.path).tags && dv.page(page.file.path).tags.includes("issue") && dv.page(page.file.path).status.contains("done"));let array = [];for (let file = 0; file < files.length; file++) {array.push(dv.fileLink(files[file].file.path, false, files[file].file.aliases[0]));}dv.list(dv.array(array));\`
`

let title = "Project " + (
	app.vault.getAbstractFileByPath("Workbench").children.length + 1
);

await tp.file.create_new(
	"",
	title + "/Inbox/Document Notes/.EGF.md",
	false,
	app.vault.getAbstractFileByPath("Workbench")
);

await tp.file.create_new(
	"",
	title + "/Inbox/Report Notes/.EGF.md",
	false,
	app.vault.getAbstractFileByPath("Workbench")
);

await tp.file.create_new(
	"",
	title + "/Issues/.EGF.md",
	false,
	app.vault.getAbstractFileByPath("Workbench")
);

await tp.file.create_new(
	"",
	title + "/Project-Box/.EGF.md",
	false,
	app.vault.getAbstractFileByPath("Workbench")
);

await tp.file.create_new(
	"",
	title + "/Repository/.EGF.md",
	false,
	app.vault.getAbstractFileByPath("Workbench")
);

await tp.file.create_new(
	homeNote,
	title + "/· " + title + " - Home.md",
	false,
	app.vault.getAbstractFileByPath("Workbench")
);

await tp.file.create_new(
	issuesNote,
	title + "/"+ title +" - Issues.md",
	false,
	app.vault.getAbstractFileByPath("Workbench")
);
%>