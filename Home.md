---
cssClass: "home-page"
---

# HOME

## Inbox

> [!table-4]
> 
> > [!column] Notes
> > `$=dv.list((dv.pages('"Inbox/· Notes"').file.link).sort())`
> 
> > [!column] Temporal
> > `$=dv.list((dv.pages('"Inbox/· Temporal"').file.link).sort())`
> 
> > [!column] Document Notes
> > `$=let files = [];dv.pages('"Inbox/Document Notes"').sort().forEach((file) => {if (file.file.aliases[0]){files.push(dv.fileLink(file.file.path,false,file.file.aliases[0]));}else{files.push(dv.fileLink(file.file.path,false,file.file.name.replace("Document Note", "DN")));}});dv.list(files);`
> 
> > [!column] Report Notes
> > `$=let files = [];dv.pages('"Inbox/Report Notes"').sort().forEach((file)=>{if (file.file.aliases[0]) {files.push(dv.fileLink(file.file.path,false,file.file.aliases[0]));}else{files.push(dv.fileLink(file.file.path, false,file.file.name.replace("Report Note", "RN")))}});dv.list(files);`

## Work Area

> [!table-3]
> > [!column] Management
> > `$=let files = [];dv.pages('"Management"').forEach((file) => {files.push(dv.fileLink(file.file.path,false,file.file.name.replace("·", "")));});dv.list(files);`
>
> > [!column] MOCs
> > `$=dv.list((dv.pages('"Slip-Box"').where(f => dv.page(f.file.path).file.tags.includes("#moc")).file.link).sort())`
>
> > [!column] Projects
> > `$=let files = [];dv.pages('"Workbench"').sort().where(page=>page.tags&&dv.page(page.file.path).tags.includes("VP")).forEach((file)=>{files.push(dv.fileLink(file.file.path,false,file.file.name.replace(" - Home", "").replace("·","")));});dv.list(files);`