---
tags: ["miss-w"]
---

# Workbench

Finally, the one of the most important tool of the vault/workflow: **The Projects Folder**. Here will stay all the projects, small and big ones, that you will working on until you finished them.

You can see there is already two folders:
- `· Archive` - Once a project is done you will move the project into an Archive (this folder). This action of moving the project folder into this one is just so that the projects don't cluster between them and you can see the ones that are currently being worked on and not yet finished.
- `Project 1` - The base folders hierarchy for any project that you'll do. You can erase this folder, since this one and all its content can be generate whenever needed using the [[Create New Project]] **template**.

Before explaining what every sub-folder inside the project folders is used for, I'll explain how to create a new project.

## Creating a Base Project

You (eventually) will work on more than one project, so you'll need to create multiple projects, and for that this vault provides you with the [[Create New Project]] **template**.

This template will generate all the folders that are inside every *`M.I.S.S.W.` project*. And I say *`M.I.S.S.W.` project* because that's how I need them to be and how the **template** will generate them, providing with every tool that I founded necessarily in order to work properly on any project.

To use a **template**, you'll need a note, any note for this matter. I recommend creating a new note and then erasing said note just in case something happens, but using an already established and used note will work as well. 

Once you are on said note, use the `ALT+E` command to open the prompt, which will ask you to choose between all the available templates that you have on your *Template Folder* (more on this on [[Templater]]). The one that you need is [[Create New Project]] (as you already know), choose it an apply it (`Enter`).

It will happen 2 things:
- *"Error" Messages* - A bunch on notices (the square looking texts) on the top left corner of the app will appear, showing that an error has occurred. The error make sense, because the command couldn't be executed as intended, but fear not, that is normal with the current template that we have.
	- If I find out a better way to code the template in order to not appear those error messages, I will update it and push it to the repository, but for now (sadly) we have to deal with it.
- *`%%DONE%%`* - On your note you'll see (only on `Edit View`) this text. If you see this text, that means your template was applied correctly and your new project folder was created.
	- Most of the times it will work, but because the way "naming folders" on said template works, there are some situations where it may break (lucky for us, it will only happen on this condition, and it's pretty easy to understand why and how to fix it ourselves).

Lets suppose we begin to create our projects into an empty `Wrokbench` folder. We use it a bunch of times repeatedly, without doing any changes at all to the folders, and we end up with the following folder structure:

```md
Workbench
├─── · Archive
├─── Project 1
├─── Project 2
├─── Project 3
└─── Project 4
```

Everything looks normal, but you see that you created far more projects that needed and (for some reason) you decided to erase the first project, so we have the following structure:

```md
Workbench
├─── · Archive
├─── Project 2
├─── Project 3
└─── Project 4
```

Then you remembered why you needed 4 projects and not only 3, so you go and use the template again. A different error will occur, and the `%%DONE%%` text won't show up. And it make sense.

I'm going to show and explain a little piece of the code that is used on the template to better explain why this happens:

```typescript
let title = "Project " + (
	app.vault.getAbstractFileByPath("Workbench").children.length
);

await tp.file.create_new(
	"",
	title + "/Inbox/Document Notes/.EGF.md",
	false,
	app.vault.getAbstractFileByPath("Workbench")
);
```

The first variable of this code is `title`, and it contains the name of the project folder when its created: `Project N`, being $N$ a number. Which one? The number of `children` that the folder `Workbenck` has. In other words, the number of sub-folders that the `Workbench` folder has.

Since we'll always have the `· Archive` folder, the number of sub-folders the `Workbench` have will start with 1, since no project is created yet. Otherwise it will increase its number with each project it contains.

Then, we go and create a new file using the function `tp.file.create_new()`, to which we give some parameters, being our `title` one of them.

Now, lets see what happens when we try to execute the template on the previous hierarchy:

```md
Workbench
├─── · Archive
├─── Project 2
├─── Project 3
└─── Project 4
```

The counter give as the number $4$, since there are 4 sub-folders inside the `Workbench` folder. This means that it will go and create a now project called `Project 4`. This is where the error occurs, because there is an already created `Project 4` folder and you can't overwrite it, since it may contain important information inside said folder.

What can we do to avoid this problem? 2 Things:
1. **Erase the last created project first** - Instead of erasing a project with a lower number, we start erasing the project that has the biggest number, and then we go to the next biggest number, and so on.
2. **Change the Project Name** - You'll end up doing this anyway, since your project probably has a name and its easier for you to differentiate your projects if they have distinctive names instead of numbers. If you do that, you shouldn't get this error.

But now that you know why it happens, whenever it does, you'll know how to fix it.

## Project Folder Hierarchy

You will find that you know what the sub-folders of your project are meant for, since they are pretty much the same as the ones we already explained before:
- **Inbox** - This folder contains your `Report Notes` and your `Document Notes`.
- **Project-Box** - The `Slip-Box` but for your project.

Yup, it's that simple, you have a "minimalistic" version of your main vault, but dedicated only for the project at hand.

> [!tip]- Optional
> There is a "hidden"^[It doesn't exists, but if you create one, you'll find out it also has an icon next to its name] sub-folder called `Repository`. This folder serves as a `git`/`GitHub` folder for your project.
> 
> I'll talk about my way of syncing the Obsidian Vault later but, in my case, I use a `git` repository (*Project Repository*) inside the main `git` repository (*Obsidian Vault Repository*), and this is called using `submodules`. This is "kinda" complicated to configure and use, so if your knowledge about `git` is still on its early stages, do *not* try to use `submodules`, since it'll definitely going to break the syncing process in some way or another.

But there is another sub-folder (arguably the most important of them all), the **Issues** folder. Whenever there is a task to do or an issue has been found that needs to be fixed, you create a new *issue* inside the **Issues** folder.

To do so, you create a new file, either using the `Right-click` over the folder or using `ALT+SHIFT+N`, writing and selecting the folder and then pressing `ENTER` (yup, the name that you give the issue file will be overwritten shortly). Once you have created the file, apply the [[Default Issue Note]] **template** to the same note.

The result of the new note should be something among the next lines:

```md
---
alias: [""]
tags: ["issue", ""]
status: "tbd" # tbd / in-progress / review / done
---

> [!bug] `$=dv.current().file.aliases[0]`
> 

### Progress



### Closure


```

> [!warning] Be careful when you create/erase a new issue
> Remember the error about the [[Create New Project]] template that you saw earlier in this note/documentation? Not only can happen the same here with the issues, but it's more probably to happen, since you won't need to change the file name itself.
> 
> You have to be careful when you create new issue, since you'll have a problem if you try to remove any issue that is in between the existing ones. Your best bet in those scenarios is to change the state of the issue to `done` (we'll talk about it now)

Once again, we have a `Front matter` and a `File Content`:
- `Front matter` - Is pretty much the same as usual, we have:
	- `alias` - The name of the issue. It should be as descriptive as possible but as short as possible as well. You'll write a longer and more concise description about the issue shortly.
	- `tags` - Array of `tag`s, being `issue` a default one. Please don't erase it, since it'll be needed in another note. But you can add as much `tag`s as you like.
	- `status` - In this case, we only need the `stage` that the `issue` is going through. The possible `stage`s are written in the comment, after the `#`.
- `File Content`
	- There are 3 main section in the `issue` note:
		- **Description** - Inside the [callout](https://help.obsidian.md/How+to/Use+callouts) (`> [!bug]`) you'll have a title and a description. The title is already applied, since you have written it as the `alias` inside the `front matter`.
		- **Progress** - After this heading you should write all the progress that you have made in relation to the issue.
			- *Obviously* you can't nor should always write it down, specially if the `isse` is `Do X` or `Review Y`. Only write what's needed.
		- **Closure** - Once you have found a solution to the issue, you should also write it after this heading, so that the next time you need the fix or when you need to explain what was your solution to a certain problem, you know where to find it.

### General View

^9607d0

The tools provided previously have a good use inside this workflow, but where can we see all the issues or the files that have a status with ease? Do you expect us to go file by file to search about this stuff? 

That's where the last 2 files comes into place:
- `Project N - Home` - Here we'll find pretty much all our files for the project, at least the key ones. There are 2 ways we find our project files:
	- **Dynamically** - Using [[Dataview]] we can make a quick search over the files that we have on our project and see them. The first "table" (the one that shows up after the first heading) contains 3 types of files: `Report Notes`, `Document Notes` and `MOC`s.
		- Every one of the lists shows all the files that have said `tags` inside their respective `front matter`s and they also need to be stored in a specific folder.
		- The `Report Notes` and `Document Notes` have said `tags` already written on their templates, but I haven't told you about which notes have the `moc` `tag`. And the answer to that question is: *Whichever note you see fit*.
		- If you have a note that you want to serve as as a `MOC` note, just write: `tags: ["moc"]`^[Or add `, "moc"` to an existing array of `tag`s] inside the `front matter` and you are good to go.
	- **Manually** - After the second heading (`Project - Box`) there is nothing more, not a single [[Dataview|Dataview Query]] to be found, as opposed to the previous section. That's because the vault can't anticipate which structure your going to use for your project, nor the type of content that you'll be using.
		- This one is on you. You decide what kinds of notes your have, what structure they'll have and how they're gonna connect with one another. 
		- If you want to use [[Dataview]] to filter all the notes, go ahead. If you want to put **links** to `MOC`-notes, you can do that as well. Maybe you need a combination of both. Whatever you may need, however you want to filter and structure your project notes, here will be the place where you start your index.
- `Project N - Issues` - Finally, the "home-made version of [[Kanban]]". This is pretty much the same configuration as the one we use in our [[Management]] system, but this one is just for the issues that the project contains.
	- The main difference that we have is that you can't dynamically change the `status`/`stage` the issue is on, you have to change that manually on the `front matter` of said notes individually.
	- Here is why there is the `issue` tag on those notes, so that the [[Dataview|Dataview Query]] can find those files and show it to you in this note.

Also, you can find another section called `Inbox Note Issues`. Remember the `status` key on the `front matter` of the `Report Notes` and  `Document Notes`? Here is where they show up. They will be showed up in a specific way, and with a different border color depending on which stage they're in.

The only reason they don't appear along the "official" `issues` pane is because the issues that we write on a `Report` or `Document` `Note` is just so that we don't forget there is something to do on that note or an event/task that we need to take care of. Once we have time, these issues (the ones from the `Report` and `Document` `Notes`) should be either organised on official `Issue Notes` or not, depending on the situation at hand.