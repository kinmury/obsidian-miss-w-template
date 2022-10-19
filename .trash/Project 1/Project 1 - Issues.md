---
cssClass: "home-page"
---

# {Project} Issues

> [!table-4]
> 
> > [!column] TBD
> > `$=let files = dv.pages('"' + dv.current().file.folder + '/Issues"').where(page=>dv.page(page.file.path).tags && dv.page(page.file.path).tags.includes("issue") && dv.page(page.file.path).status.contains("tbd"));let array = [];for (let file = 0; file < files.length; file++) {array.push(dv.fileLink(files[file].file.path, false, files[file].file.aliases[0]));}dv.list(dv.array(array));`
> 
> > [!column] In-Progress
> > `$=let files = dv.pages('"' + dv.current().file.folder + '/Issues"').where(page=>dv.page(page.file.path).tags && dv.page(page.file.path).tags.includes("issue") && dv.page(page.file.path).status.contains("in-progress"));let array = [];for (let file = 0; file < files.length; file++) {array.push(dv.fileLink(files[file].file.path, false, files[file].file.aliases[0]));}dv.list(dv.array(array));`
>
> > [!column] Review
> > `$=let files = dv.pages('"' + dv.current().file.folder + '/Issues"').where(page=>dv.page(page.file.path).tags &&dv.page(page.file.path).tags.includes("issue") && dv.page(page.file.path).status.contains("review"));let array = [];for (let file = 0; file < files.length; file++) {array.push(dv.fileLink(files[file].file.path, false, files[file].file.aliases[0]));}dv.list(dv.array(array));`
> 
> > [!column] Done
> > `$=let files = dv.pages('"' + dv.current().file.folder + '/Issues"').where(page=>dv.page(page.file.path).tags && dv.page(page.file.path).tags.includes("issue") && dv.page(page.file.path).status.contains("done"));let array = [];for (let file = 0; file < files.length; file++) {array.push(dv.fileLink(files[file].file.path, false, files[file].file.aliases[0]));}dv.list(dv.array(array));`
