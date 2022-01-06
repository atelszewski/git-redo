- Properly parse command line options, specifically ensure
  they exist at all (for now, `set -u` catches such errors).
- Allow multiple command/hash pairs on the command line --
  execute multiple actions in single invocation.
- Add man page.

- `amend`:

  - As of now, `amend` sub-command uses the default stash for stashing
    the changes to be applied. Consider using a separate stash.
  - Detail what `git` commands are executed during amend.
  - Consider allowing to abort on-going and to continue interrupted
    `amend` command (like `rebase` does).
  - `--no-edit` is passed by default to underlying `git commit --amend`
    command. Consider making it optional, to allow for $EDITOR to be
    invoked.
