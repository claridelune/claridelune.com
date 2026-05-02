+++
date = '2026-02-25T16:40:21-05:00'
draft = false
title = 'How I Use Git'
description = 'Things I love about git and how I use it'
tags = ['git']
+++

This is how I "survive" git, tips, tricks and more.

So `.gitconfig` is more useful than people think. It's not just name and email
and credentials.

You can set the default editor git uses for commit, interactive rebase, etc. And
define a global ignore file, and now, add any files you want in a repo, scripts,
notes, prompts, and dont be afraid of push them.

```
[core]
	editor = nvim
	excludesFile = ~/.gitignore
```

For diffs and merges, I use `nvimdiff`. I used to use nvim plugin for that, but
git already has decent tools. There are other tools besides `nvimdiff` in case
you dont use nvim.

Commands to run it: `git difftool`, `git mergetool`

```
[diff]
	tool = nvimdiff

[merge]
	tool = nvimdiff
	conflictstyle = zdiff3

[mergetool]
	keepBackup = false
	layout = BASE,MERGED + BASE,LOCAL + BASE,REMOTE
```

Besides my configuration, there is my workflow, I mostly use
`rebase-merging`, you know, it keeps the history clean. then `squash-merge`,
then `merge`.

That said, rebasing can be tricky. Especially on large projects with a lots of
changes per day, and you can smell the conflicts coming, that's when I opt for
`--no-rabase` which is basically a merge, it saves time and keeps me sane.

Another important command is `git reflog` you can literally mess up everything
in your repo, reset, rebase, accidentally delete somehing important, and still
undo it. This command keeps track of where your HEAD has been. Now you don't
need to clone the repo again; basically, everything can be fixed. 

And `cherry-pick` is useful when you need a specific commit in another branch.
Instead of copying changes manually, you just take that commit and apply it
where you need it. It’s cleaner and reduces mistakes than doing it manually (I
broke develop doing it manually).

Finally, commit messages. They matter a lot. A good message explains why
something changed. That saves time later when you’re trying to understand what
happened without digging through code.

There's a lot I still have to learn, but this is working for me right now.
