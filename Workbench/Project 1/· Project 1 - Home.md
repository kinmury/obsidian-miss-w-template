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

## Project - Box
