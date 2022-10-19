---
cssClass: "home-page"
---

# {Project} Issues

> [!table-4]
> 
> > [!column] TBD
> > `$=let files = [];dv.pages('"'+dv.current().file.folder+'/Issues"').sort().where(page => page.tags &&dv.page(page.file.path).tags.includes("issue") &&dv.page(page.file.path).status.contains("tbd")).forEach((file) => {if (file.file.aliases[0]) {files.push(dv.fileLink(file.file.path,false,file.file.aliases[0]));}else{files.push(dv.fileLink(file.file.path,false,file.file.name));}});dv.list(files);`
> 
> > [!column] In-Progress
> > `$=let files = [];dv.pages('"'+dv.current().file.folder+'/Issues"').sort().where(page => page.tags &&dv.page(page.file.path).tags.includes("issue") &&dv.page(page.file.path).status.contains("in-progress")).forEach((file) => {if (file.file.aliases[0]) {files.push(dv.fileLink(file.file.path,false,file.file.aliases[0]));}else{files.push(dv.fileLink(file.file.path,false,file.file.name));}});dv.list(files);`
>
> > [!column] Review
> > `$=let files = [];dv.pages('"'+dv.current().file.folder+'/Issues"').sort().where(page => page.tags &&dv.page(page.file.path).tags.includes("issue") &&dv.page(page.file.path).status.contains("review")).forEach((file) => {if (file.file.aliases[0]) {files.push(dv.fileLink(file.file.path,false,file.file.aliases[0]));}else{files.push(dv.fileLink(file.file.path,false,file.file.name));}});dv.list(files);`
> 
> > [!column] Done
> > `$=let files = [];dv.pages('"'+dv.current().file.folder+'/Issues"').sort().where(page => page.tags &&dv.page(page.file.path).tags.includes("issue") &&dv.page(page.file.path).status.contains("done")).forEach((file) => {if (file.file.aliases[0]) {files.push(dv.fileLink(file.file.path,false,file.file.aliases[0]));}else{files.push(dv.fileLink(file.file.path,false,file.file.name));}});dv.list(files);`
