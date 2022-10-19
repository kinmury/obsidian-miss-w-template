```javascript
let files = [];

dv.pages('"Workbench"')
	.sort()
	.where(
		page =>
			page.tags &&
			dv.page(page.file.path).tags.includes("VP")
	)
	.forEach(
		(file) => {
			files.push(
				dv.fileLink(
					file.file.path,
					false,
					file.file.name
						.replace(" - Home", "")
						.replace("·","")
				)
			)
		}
	);

dv.list(files);
```


```javascript
let files = [];

dv.pages('"Inbox/Report Notes"').sort().forEach(
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
					file.file.name.replace("Report Note", "RN")
				)
			);		
		}
	}
);

dv.list(files);
```

```javascript
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

```javascript
let files = [];

dv.pages('"Management"').forEach(
	(file) => {
		files.push(dv.fileLink(
			file.file.path, 
			false,
			file.file.name.replace("·", "")
		));		
	}
);

dv.list(files);
```