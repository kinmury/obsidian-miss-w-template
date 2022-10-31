---
tags: ["miss-w"]
---

# Dataview

> This is the most **powerful** tool this vault have, it transforms your files and the data it stores to a *database* that you can access and read its information within any note on the vault

There is "kinda a debate" over if users should use it or not, since it "breaks the point" of using **links** in the first place. I understand the point of both sides of the fight:
- You could stop using `MOC`s and use **Dataview Queries** instead, making your job a little easier.
	- But that would mean loosing the ability to join ideas and, ultimately, loosing the point of using the *Zettelkasten Workflow*.
- You should use `MOC`s to connect ideas, but that also means that you will *manually* create links and changed them nonstop whenever an new issue is created, his stage has been modified, or to go and write more notes just to hold *a one line task* (here I'm referring to the `Inbox Notes Issues/Status`).
	- Here you can create a filter of all this repetitive and, pretty must in constant change, elements of your vault.
- But also you are relying on a plugin, which could disappear at any point, along with the Obsidian program, and then you are left with Markdown notes that hold code blocks with no meaning without said plugin.
	- If we follow this ideology, then we should stop using any digital tool at our disposal and go back to using pen and paper, something that has been used (and still is to this day, because it's still important to know how to write good by hand) for a long time.
	- Yeah, it's true that it's more future proof (since we have and enormous amount of history documentation on paper (or walls, depending on how far we go back in time)), but at this point and age, seeing how things are evolving to go more digital than ever, I kinda doubt that we get to a point where we don't have access to technology at all or a way to go back to a previous version of a software (something that Obsidian provides by the way).
		- `P.S.` - Paper can also be liability in a number of ways (storage, the danger of begin torn off, burned or soaked wet, ...)

As you can probably see, this debate goes even deeper than the use of this plugin, so we'll stop here. 

My approach isn't one sided, but I try to use the best of both worlds: Dataview and Links. The only use that I personally give Dataview (in my personal vault and this template vault) is just to create a workflow for my tasks system and not so much as to organize my notes (for that we use `MOC`s or link to notes directly).

Now back to the documentation, Dataview uses `SQL` syntax to query notes, here is an example:

```dataview
TABLE file.name, file.ctime, file.tags
FROM ""
WHERE contains(tags, "repNote") = true
```

As you can see, its displaying a `TABLE` with the name, creation time and tags that all files (`FROM ""` is the equivalent of `FROM everywhere`) that contains the tag `repNote` (`WHERE contains(tags, "repNote") = true`).

This is the simplest way you can use Dataview, by using `SQL` Queries (from now on **Dataview Queries**). But if you know how to program code, you can use Dataview alongside `JavaScript` and do really interesting stuff (like the `issues-table-like-kanban` that I've added to this vault in [[Issues]]).

There are a lot of things that can be done with this plugin, and I cannot explain it all to you, not only because is not the point of this documentation, but also because it's already been explain much better by the creators of said plugin. Just search for their repository on GitHub, there you'll find the **Full Documentation** on how to use it.

And also not everyone may know how to use `SQL` or `JavaScript`, so... if you are new to this, just stick with `SQL` for now and when you know how Dataview works, you can move on using `JavaScript` (alongside your own `CSS` snippets).