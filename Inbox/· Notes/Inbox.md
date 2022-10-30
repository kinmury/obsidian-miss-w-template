---
tags: ["miss-w"]
---

# Inbox

Welcome to the place where all notes are created. Here is the place where you'll spend most of the times (if you aren't working in any project, that's for later).

If you open up the `Inbox` folder, your find yourself with 4 distinctive sub-folders:
- `· Notes`^[The `· ` at the start of the name it's just for it to appear above all the other folders. You can rename if you want (**but** you will need to change the settings of the vault, so don't do it at least you know what you're doing)] - This folders is where all the new notes will go in, whenever you use the `CTRL+N` command, click a link to a *not yet created* note or use the `Advance New File` command `SHIFT+ALT+N` (not recommended if you will create a note here, since `CTRL+N` is faster and easier to use).
	- The important difference between this folder an the rest is the fact that **no template** will be *applied* to the note if you create it inside this folder.
	- More about the **template** thing on the last 2 folders of this section.
- `· Temporal` - Whenever you don't have a destination nor a connection to other notes for your note, you can store it temporally (as you may have guessed by the name) here.
	- I recommend that you don't let your notes live on this folder for too long. If it stays more that 3-4 days (even this much time is dangerous) that means either it doesn't have any connection to an already established hierarchy of connections or that you *maybe* need to create a new set of connections relating to the topics of said notes. Worst case scenario, you need to get rid of said notes since they don't give you any value for you or your knowledge base (vault).
- `Report Notes`^[I know that this folder is the last one, but I need to explain the purpose of this folder so that the next (or previous, depending on how are you looking at it) folder make sense.] - Most of the times, you want to create a note note here, either using `SHIFT+ALT+N` and writing the name of this folder (after choosing the folder, it will ask you for a name, you can just press `Enter` again, since the name that you would have given will be overwritten by a **template**) or using the right-click over the folder.
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
	"" # Date
]
---

# `$=dv.current().alias`
```

Here we already have a lot of things to discuss: What is the `---` section? Why it has a different font that the rest of the note? What are all that stuff that is inside the section? And that is that `$=` after a Twitter-looking-hastag?

Let's go one step at a time:
- `Frontmatter` - The first section of everyone (the one that it's between the `---`) and, at some point, the most important element of the note^[Only at the *organising point of view*, is more that clear that the content of the note is the most important thing of any note].
	- Here it lays a set of data that it will be use further down the line that gives **key** information about the note at hand. Each one of those data (the word that stands before the `:`) it's called a `key`, and each one of them has a different purpose:
		- `alias` - This will be the "real" name of the note. By this I mean that the note will have more that one name.
			- The original one is the one that appears on top of the note (and in the file itself), but we both know that the name used in this type of notes will be repetitive and not very useful for us to connect ideas/notes.
			- That's where `alias` comes in, thanks to him, we can now give a proper name to the note. Said name needs to be inside the `""`.
		- `tags` - Next one on the list is the `tag` key. Using the Twitter reference made not so long ago, the same ideology we have with the hashtags on any social platform we can applied it to the Obsidian tags: We give a key value/s to the note in order for us to better establish connections between other notes further down the line.
			- I forgot to tell you, the `frontmatter` use the `YAML` syntax which, at some extend, is easy to use:
				- `key:value` - The "word"/variable before the `:` is the **key** element and the variables that come after the `:` are the values.
				- There is a number of ways to give values to a `key`, and the most simple way is by using a `string` (the set of words you used to put a name on the `alias`, using the `""` characters.^[That's one of the basic types of variables in any programming languages, and there is more: integer (number), boolean (true/false), floats...])
			- As you can see, there is a new type of value next to the `tags` key: `["repNote", ""]`.
				- The `[]` represents the start and the end of an *array*. Another basic type of any programming language.
				- The idea of the array is to store a determined number of elements inside the same variable. You can see it as a bag: You have one bag, but inside the bag you can have one product, or multiple products.
			- The `tags` key holds a number of `string` variables, in other words, you have one variable (type `array`) that can hold a lot of `string`s. In case you need to add more `string`s to your array, just use the `,` after every `""` and you should be fine.
		- `status` - Here its where things gets a little more interesting, but you will see that its not so different than the previous key:
			- The `status` key starts and end with `[]`, that means we have an array of `string`s^[Actually, it could be any other type of variable, but we'll stick with the string for pretty much the rest of the time].
			- The first `""` has a `#` next to it. You can see by the color that is greyed out. That means that its a *commentary*, meaning that it doesn't add any value to the `frontmatter`, but helps the user understand what is happening. 
				- This value can be any set of characters, but I want you do use one of the 4 `string`s that are written beside it.
				- As you can see, it follows the same logic explained back in the [[Management]] folder, and it's for a reason that will be discussed later.
			- After the first `""` we see another `[]`. As you may guessed, we have another `array`. Now you may be asking: Can we have an `array` inside another `array`? *YES*, you can have multiple arrays inside an array inside another set of arrays inside ar... you get the point: A box inside another bigger box inside another  even bigger box.
				- Here we have another set of `string`s. Here you will need to add a description. For what? I'll explain in a bit, let us first finish understanding the array
			- Finally, we have another `""`, and here I'm asking you to write a date

<br>

- `Document Notes` - 