```dataviewjs
let files = dv.pages(
	'"' + dv.current().file.folder + '/Inbox/Report Notes"')
	.where(
		page => 
			dv.page(page.file.path).tags.includes("repNote")
	);

let array = [];

for (let file = 0; file < files.length; file++) {
	array.push(
		dv.fileLink(
			files[file].file.path,
			false, 
			files[file].file.aliases[0])
	);	
}

dv.list(dv.array(array))
```

```dataviewjs
let files = [];

dv.pages(
	'"' + dv.current().file.folder + '/Inbox/Report Notes"'
)
.sort()
.where(
	page => 
		page.tags &&
		dv.page(page.file.path).tags.includes("repNote")
)
.forEach(
	(file) => {
		if (file.file.aliases[0]) {
			files.push(
				dv.fileLink(
					file.file.path,
					false,
					file.file.aliases[0]
				)
			);
		} else {
			files.push(
				dv.fileLink(
					file.file.path,
					false,
					file.file.name
						.replace("Report Note", "RN")
						.replace("'", ":")
						.replace("''", ":")
						.replace("'''", "")
				)
			);
		}
	}
);
	
dv.list(files);
```

`$=let files = [];dv.pages('"'+dv.current().file.folder+'/Inbox/Report Notes"').sort().where(page=>page.tags&&dv.page(page.file.path).tags.includes("repNote")).forEach((file) => {if (file.file.aliases[0]) {files.push(dv.fileLink(file.file.path,false,file.file.aliases[0]));}else{files.push(dv.fileLink(file.file.path,false,file.file.name.replace("Report Note", "RN").replace("'", ":").replace("''", ":").replace("'''", "")));}});dv.list(files);`

---

```dataviewjs
let files = [];

dv.pages(
	'"' + dv.current().file.folder + '/Inbox/Document Notes"'
)
.sort()
.where(
	page => 
		page.tags &&
		dv.page(page.file.path).tags.includes("docNote")
)
.forEach(
	(file) => {
		if (file.file.aliases[0]) {
			files.push(
				dv.fileLink(
					file.file.path,
					false,
					file.file.aliases[0]
				)
			);
		} else {
			files.push(
				dv.fileLink(
					file.file.path,
					false,
					file.file.name
						.replace("Document Note", "DN")
						.replace("'", ":")
						.replace("''", ":")
						.replace("'''", "")
				)
			);
		}
	}
);
	
dv.list(files);
```

`$=let files = [];dv.pages('"'+dv.current().file.folder+'/Inbox/Document Notes"').sort().where(page=>page.tags&&dv.page(page.file.path).tags.includes("docNote")).forEach((file) => {if (file.file.aliases[0]) {files.push(dv.fileLink(file.file.path,false,file.file.aliases[0]));}else{files.push(dv.fileLink(file.file.path,false,file.file.name.replace("Document Note", "DN").replace("'", ":").replace("''", ":").replace("'''", "")));}});dv.list(files);`

---

```dataviewjs
let files = dv.pages(
	'"' + dv.current().file.folder + '/Issues"'
)
.where(
	page => 
		dv.page(page.file.path).tags && 
		dv.page(page.file.path).tags.includes("issue") && 
		dv.page(page.file.path).status.contains("tbd")
);

let array = [];

for (let file = 0; file < files.length; file++) {
	array.push(
		dv.fileLink(
			files[file].file.path,
			false, 
			files[file].file.aliases[0]
		)
	);
}

dv.list(dv.array(array));
```

```dataviewjs
let files = [];

dv.pages(
	'"' + dv.current().file.folder + '/Issues"'
)
.sort()
.where(
	page => 
		page.tags &&
		dv.page(page.file.path).tags.includes("issue") &&
		dv.page(page.file.path).status.contains("tbd")
)
.forEach(
	(file) => {
		if (file.file.aliases[0]) {
			files.push(
				dv.fileLink(
					file.file.path,
					false,
					file.file.aliases[0]
				)
			);
		} else {
			files.push(
				dv.fileLink(
					file.file.path,
					false,
					file.file.name
				)
			);
		}
	}
);

dv.list(files);
```

`$=let files = [];dv.pages('"'+dv.current().file.folder+'/Issues"').sort().where(page => page.tags &&dv.page(page.file.path).tags.includes("issue") &&dv.page(page.file.path).status.contains("tbd")).forEach((file) => {if (file.file.aliases[0]) {files.push(dv.fileLink(file.file.path,false,file.file.aliases[0]));}else{files.push(dv.fileLink(file.file.path,false,file.file.name));}});dv.list(files);`