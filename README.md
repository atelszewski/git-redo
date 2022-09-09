# git-redo - Process rebase todo list, non-interactively

`git-redo` is inspired by `git commit --amend`, with the goal of allowing
to edit any commit on the current branch - and not only the latest one.

One of the most important characteristics of `git-redo` is that it runs
non-interactively - i.e. the commit to be edited needs to be provided on
the command line - the traditional todo sequence editor is not shown.

Given the following sample history:

```
$ git log --oneline
15b7574 (HEAD -> main, origin/main, origin/HEAD) svn: Add
119836c git: Update
4f11c12 git: Update
9394c01 perforce: Update
334c034 git: Update
```

with `git-redo` one can _edit_ the desired commit quickly with:

```
$ git redo edit 9394c01
Stopped at 9394c01...  
You can amend the commit now, with

  git commit --amend 

Once you are satisfied with your changes, run

  git rebase --continue
```

Or _amend_ with:

```
$ git redo amend 9394c01
```

The change to be applied should  be staged in the index prior amending.
`git redo amend` will then:

- stash the change,
- switch to the desired commit,
- apply the change,
- and switch back to the current commit.
