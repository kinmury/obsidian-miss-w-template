---
tags: ["miss-w"]
---

# Inbox

Welcome to the place where all notes are created. Here is the place where you'll spend most of the time (if you aren't working in any project, that's for later).

If you open up the `Inbox` folder, your find yourself with 4 distinctive sub-folders:
- `· Notes`^[The `· ` at the start of the name it's just for it to appear above all the other folders. You can rename if you want (**but** you will need to change the settings of the vault, so don't do it at least you know what you're doing)] - This folder is where all the new notes will go in, whenever you use the `CTRL+N` command, click a link to a *not yet created note* or use the `Advance New File` command `SHIFT+ALT+N` (not recommended if you will create a note here, since `CTRL+N` is faster and easier to use).
	- The important difference between this folder an the rest is the fact that **no template** will be *applied* to the note if you create it inside this folder.
	- More about the **template** thing on the last 2 folders of this section.
- `· Temporal` - Whenever you don't have a destination nor a connection to other notes for your note, you can store it temporally (as you may have guessed by the name) here.
	- I recommend that you don't let your notes live on this folder for too long. If it stays more that 3-4 days (even this much time is dangerous) that means either it doesn't have any connection to an already established hierarchy of connections or that you *maybe* need to create a new set of connections relating to the topics of said notes. Worst case scenario, you need to get rid of said notes since they don't give you any value for you or your knowledge base (vault).
- `Report Notes`^[I know that this folder is the last one, but I need to explain the purpose of this folder so that the next folder (or previous folder, depending on how are you looking at it) make sense.] - Most of the times, you want to create a new note here, either using `SHIFT+ALT+N` and writing the name of this folder (after choosing the folder, it will ask you for a name, you can just press `Enter` again, since the name that you would have given will be overwritten by a **template**) or using the right-click over the folder. ^3fa0b8
	- Go and create a new note on said folder and see what happens.
	- If have created a note (thank you if you did, now the explanation will make more sense, if not... well... nothing will happen, I'm just the narrator) you'll see that 2 things have happened:
		1. **The name of the file has been changed** - The name should be among the lines of `Report Note - YYYY-MM-DD HH'mm''ss'''`:
			- `YYYY-MM-DD` - Is the date format chosen for the file. `YYYY` is the year, `MM` the month and `DD` for the day, and said values should be the same as the date that you have created the note.
			- `HH'mm''ss'''` - The exact time that you have created the note, being `HH` the hours (in `24 h` format), `mm` the minutes and `ss` seconds. Said values can be differentiated by the amount of `'` next to each one of them.
		2. **New content was added to the note** - You should see the following:

```md
---
alias: ""
tags: ["repNote", ""]
status:
[
	"", # tbd / in-progress / review / done
	[ # Description/s
		""
	],
	"" # Date YYYY-MM-DD
]
---

# `$=dv.current().alias`
```

Here we already have a lot of things to discuss: What is the `---` section? Why it has a different font that the rest of the note? What are all that stuff that is inside the section? And that is that `$=` after a Twitter-looking-hashtag?

Let's go one step at a time:
- `Front matter` - Is the name for the first section of every note (the one that it's between the `---`) and, at some point, the most important element of said note^[Only at the *organizing point of view*, is more than clear that the content of the note is the most important thing of any note].
	- Here it lays a set of data that it will be use further down the line that gives **key** information about the note at hand. Each one of those data (the word that stands before the `:`) it's called a `key`, and each one of them has a different purpose:
		- `alias` - This will be the "real" name of the note. By this I mean that the note will have more that one name.
			- The original one is the one that appears on top of the note (and in the file itself), but we both know that the name used in this type of notes will be repetitive and not very useful for us to connect ideas/notes.
			- That's where `alias` comes in, thanks to him, we can now give a proper name to the note. Said name needs to be inside the `""`.
		- `tags` - Next one on the list is the `tag` key. Using the Twitter reference made not so long ago, the same ideology we have with the hashtags on any social platform we can apply it to the Obsidian tags: We give a key value/s to the note in order for us to better establish connections between other notes further down the line.
			- I forgot to tell you, the `front matter` use the `YAML` syntax which, at some extend, is easy to use:
				- `key:value` - The "word"/variable before the `:` is the **key** element and the variables that come after the `:` are the values.
				- There is a number of ways to give values to a `key`, and the most simple way is by using a `string` (the set of words you used to put a name on the `alias`, using the `""` characters.^[That's one of the basic types of variables in any programming languages, and there is more: integer (number), boolean (true/false), floats...])
			- As you can see, there is a new type of value next to the `tags` key: `["repNote", ""]`.
				- The `[]` represents the start and the end of an *array*. Another basic type of any programming language.
				- The idea of the array is to store a determined number of elements inside the same variable. You can see it as a bag: You have one bag, but inside the bag you can have one product, or multiple products.
			- The `tags` key holds a number of `string` variables, in other words, you have one variable (type `array`) that can hold a lot of `string`s. In case you need to add more `string`s to your array, just use the `,` after every `""` and you should be fine.
		- `status` - Here its where things gets a little more interesting, but you will see that its not so different than the previous key:
			- The `status` key starts and end with `[]`, that means we have an array of `string`s^[Actually, it could be any other type of variable, but we'll stick with the strings for pretty much the rest of the time].
			- The first `""` has a `#` next to it. You can see by the color that is greyed out. That means that its a *comment*, meaning that it doesn't add any value to the `front matter` itself, but helps the user understand what is happening on the line that is written on. 
				- This value can be any set of characters, but I want you do use one of the 4 `string`s that are written next to it.
				- As you can see, it follows the same logic explained back in the [[Management]] folder, and it's for a reason that will be discussed later.
			- After the first `""` we see another `[]`. As you may guessed, we have another `array`. Now you may be asking: Can we have an `array` inside another `array`? *YES*, you can have multiple arrays inside an array inside another set of arrays inside ar... you get the point: A box inside another bigger box inside another  even bigger box.
				- Here we have another set of `string`s. Here you will need to add a description. For what? I'll explain in a bit, let us first finish understanding the array
			- Finally, we have another `""`, and here I'm asking you to write a date with the format `YYYY-MM-DD`, the same way the date of the created note is written.
			- Now, What is this for? This represents the `status` of your note. If there is something that needs to be done, specifically about the note that you are writing on, you may want to write it there.
				- If there is more than one tasks that you want to add to the same note, just add another `,` after the last `""`, write another `""` after the `,`, write the task and repeat this action the number of times that you need.
- `# $=dv.current().alias` - And, finally, you have this thing after a `# `. A `#` followed by a space means that we have a *heading*.
	- Maybe this should have been introduce to you at the beginning of the guide (even thought this is not a guide on *How to use Obsidian - Basic to Expert Level*, for that exists the [Official Help Site](https://help.obsidian.md/Obsidian/Index), where everything that you need to know about how Obsidian works is explained much better that I will ever do, so make sure to check that out in case you are still lost on how to use Obsidian (Obsidian change a lot every now and then, so it's always good to check the Help site in order to know what new things you can do (Or read the `Release Notes` whenever you update Obsidian)))
	- But in case you are new and want to finish reading this guide before the *Help Site*, Obsidian use `Markdown` syntax, where some symbols *style* the text, so certain elements look a certain ways, being `# ` one of them.
	- Inside the heading there is a `$=dv.current().alias`. That is a *command*, a **[[Dataview]]** *command* (or very tiny script if you will). I'm not gonna dig much into it for now, but I'll explain what it does:
		- `dv.current()` - Is a function that retrieves all the meta-data that the actual file can give you. The "meta-data" refers to all the `key`s that the file has, being these `key`s all the ones that every note has by default and the ones that we define inside the `front matter`.
		- This means that we can retrieve all the data that we have written inside it: `alias`, `tags` and `status`. In this case, we just want to get the `alias`, so we write `.alias` after the previous code.
		- Once that is done, (if you are using the configuration that I have made for the vault^[In the case that you are using `Live Preview`, you will see the result after you move your cursor out of the heading line]), you can see the result of said function on `Preview View` (Use `CTRL+E` to change between `Edit View` and `Preview View`).

Before talking about **What should we write inside the Report Note?**, I want to clarify why should we fill up all this information.

There are 2 main ways we can store Obsidian Notes:
- **Using Links** - All the `[[Note Name]]` that we write on the notes are `link`s from one note to another. This is a powerful tool, not only to create paths between notes, but also to ***connect*** ideas one to another. This is very important in the long run for your vault/knowledge base, but will talk more about it later.
	- But my point with the links is to create what we usually call `MOC`s (*Map Of Contents*), a note in which we store a list of links to another notes.
- **Using [[Dataview]]** - [[Dataview]] is a plugin that lets you use all the data store on every note of you vault as if it were a database.
	- This vault make a huge use of said plugin, but I also recommend using `MOC`s, since the use that I give to this plugins is just to organize tasks and files just for enough time for me to move it to a better place (being that place inside the [[Management]] folder or a better suited `MOC`)

So, this `front matter` will help us store the small and precise tasks that we have on certain topics/notes more easily, as well as let us retrieve said tasks from other places (*cough cough* [[Issues]] *cough cough*^[I'll explain that code later on the guide, but you can see what is for by seeing the result on the `Preview View` (if you have filled the `front matter` on your `Test Report Note` correctly, you should be able to see your task on [[Issues|said]] note)]).

And now, the **most important** part of the *Report Note*: ==It's content==. Everything, and I mean *everything* that it's new and it's not processed correctly should go on a `Report note`.

Taking classes on some subject? `Report Note`, Some appointment with your colleges? `Report Note`, You found something about a book interesting and need to store your thoughts about it? `Report Note`.

Anything now that needs to be written fast just so that you don't forgive about it should be written inside the `Report Note`.

- `Document Notes` - You don't need to create a new `Document Note`, since the only difference between this type of note and the previous one is the use of the tag `docNote`, instead of `repNote`: ^123252
	- Both `tag`s are used to distinguish one type of notes from the other

Now then, Whats the difference? This note serves as *the clean up* from the `Report Notes`. This means that the `Document Note` is the formal version of your `Report Note` that, once is done, will go directly into your [[Slip-box]].

The main purpose of this folder is to create a filter between what you have collected into your `Report Note` and what you want to store into your [[Slip-box]], but, *most importantly*  **HOW** will you store it is the most crucial thing of all this process.

I recommend you to use *your own words* when writing your `Document Notes`. This is because of 2 things:
- **It's your own vault** - The vault represents your knowledge and, as such, it should only contain your knowledge, your way of thinking, your way of seeing things, understanding them, how you interact with them. There is no point on just *coping* information from one source of information to another.
- **To improve your writing** - This is something that I still struggle myself (and pretty sure will still struggle for a while). For a long time, there were some people that said that I couldn't explain the things that I had understood correctly, and that wasn't too long ago. At first I didn't thought much about it, but as time goes on, this became more of an issue that I had to start addressing.
	- If you have understood the concepts that I'm writing on this guide, that means that I have improved my writing thanks to doing this exact thing: *Writing the stuff I learn with my own words*.
	- And, if you didn't, that means that I failed in my mission to explain it to you (taking into account that English isn't my native language, so... sorry for that as well 😥), and for that I'm sorry, I really did tried my best. But this is still worth it, since is just another practice round in my journey. A way for you to see if your writing is good or not (or if it has improve over time), is to read what you have written before "putting it away" on your [[Slip-box]] or read what you already have stored inside it (something that you may have to do more times that you thing).

But enough of **Why**s, and lets continue with the guide. Once you have written your `Document Note`, and you have confirmed that everything it's on his place, you can proceed with the next step:
- *Storing it on the [[Slip-box]]*