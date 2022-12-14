%%DONE%%<%*
let homeNote = `---
cssClass: "home-page"
tags: ["VP", ""]
---

# {Project}

> [!table-3]
>
> > [!column] Report Notes
> > \`$=let files = [];dv.pages('"'+dv.current().file.folder+'/Inbox/Report Notes"').sort().where(page=>page.tags&&dv.page(page.file.path).tags.includes("repNote")).forEach((file) => {if (file.file.aliases[0]) {files.push(dv.fileLink(file.file.path,false,file.file.aliases[0]));}else{files.push(dv.fileLink(file.file.path,false,file.file.name.replace("Report Note", "RN").replace("'", ":").replace("''", ":").replace("'''", "")));}});dv.list(files);\`
>
> > [!column] Document Notes
> > \`$=let files = [];dv.pages('"'+dv.current().file.folder+'/Inbox/Document Notes"').sort().where(page=>page.tags&&dv.page(page.file.path).tags.includes("docNote")).forEach((file) => {if (file.file.aliases[0]) {files.push(dv.fileLink(file.file.path,false,file.file.aliases[0]));}else{files.push(dv.fileLink(file.file.path,false,file.file.name.replace("Document Note", "DN").replace("'", ":").replace("''", ":").replace("'''", "")));}});dv.list(files);\`
>
> > [!column] MOCs
> > \`$=dv.list(dv.pages('"' + dv.current().file.folder + '/Project-Box"').where(f=>dv.page(f.file.path).file.tags.includes("#moc")).file.link)\`

## Project - Box
`

let issuesNote = `---
cssClass: ["home-page", "issues-appereance", "no-width"]
---

# {Project} Issues

> [!table-4]
> 
> > [!column] TBD
> > \`$=let files = [];dv.pages('"'+dv.current().file.folder+'/Issues"').sort().where(page => page.tags &&dv.page(page.file.path).tags.includes("issue") &&dv.page(page.file.path).status.contains("tbd")).forEach((file) => {if (file.file.aliases[0]) {files.push(dv.fileLink(file.file.path,false,file.file.aliases[0]));}else{files.push(dv.fileLink(file.file.path,false,file.file.name));}});dv.list(files);\`
> 
> > [!column] In-Progress
> > \`$=let files = [];dv.pages('"'+dv.current().file.folder+'/Issues"').sort().where(page => page.tags &&dv.page(page.file.path).tags.includes("issue") &&dv.page(page.file.path).status.contains("in-progress")).forEach((file) => {if (file.file.aliases[0]) {files.push(dv.fileLink(file.file.path,false,file.file.aliases[0]));}else{files.push(dv.fileLink(file.file.path,false,file.file.name));}});dv.list(files);\`
>
> > [!column] Review
> > \`$=let files = [];dv.pages('"'+dv.current().file.folder+'/Issues"').sort().where(page => page.tags &&dv.page(page.file.path).tags.includes("issue") &&dv.page(page.file.path).status.contains("review")).forEach((file) => {if (file.file.aliases[0]) {files.push(dv.fileLink(file.file.path,false,file.file.aliases[0]));}else{files.push(dv.fileLink(file.file.path,false,file.file.name));}});dv.list(files);\`
> 
> > [!column] Done
> > \`$=let files = [];dv.pages('"'+dv.current().file.folder+'/Issues"').sort().where(page => page.tags &&dv.page(page.file.path).tags.includes("issue") &&dv.page(page.file.path).status.contains("done")).forEach((file) => {if (file.file.aliases[0]) {files.push(dv.fileLink(file.file.path,false,file.file.aliases[0]));}else{files.push(dv.fileLink(file.file.path,false,file.file.name));}});dv.list(files);\`

## Inbox Notes Issues

\`\`\`dataviewjs
let pages = dv.pages('"' + dv.current().file.folder + '/Inbox"')
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
		let field  = dv.el("div", "", {cls: \`dvjs-field \${page.status[0]}\`});
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
`

let title = "Project " + (
	app.vault.getAbstractFileByPath("Workbench").children.length
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

/*await tp.file.create_new(
	"",
	title + "/Repository/.EGF.md",
	false,
	app.vault.getAbstractFileByPath("Workbench")
);*/

await tp.file.create_new(
	homeNote,
	title + "/?? " + title + " - Home.md",
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