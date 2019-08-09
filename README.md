# Git Mob

Git subcommand that makes mob programming workflows easier

Inspired by [git-mob](https://www.npmjs.com/package/git-mob) but written as
simple shell scripts.

It uses `jq` to manipulate the `~/.git-coauthors` file.

# Installation

Ensure that [jq](https://stedolan.github.io/jq/download/) is installed an on
your `$PATH`.

Download and place the `git-mob` script in your `$PATH`. Somewhere like `~/bin/`
may work nicely.

# Usage

## Co authors

The `~/.git-coauthors` file is a database of the user information for all the
users who are going to be a part of one or more mob-programming sessions. This
does not indicate that set of users who are a part of the current
mob-programming session. See the next section to see the current mob-programming
users.

### List co-authors

```sh
git mob list
```

### Add new co-authors

```sh
git mob add-co-author da "Douglas Adams" "da@example.com"
```

### Delete existing co-author

```sh
git mob delete-co-author da
```

## Mob programming session

The information about a mob programming session is stored locally in a git
repository. The state of a mob-programming session is stored as a combination of
the state in `.git/config` and the contents of the `.git/git-mob-message`
template file.

### Current mob programming session users

```sh
git mob
```

### Change the current session of mob programmers

```sh
git mob -o <id1> <id2> <id3>
```

`id1`, `id2` and `id3` are ids of the users with which they are saved into the
`git-coauthors` file.

`-o` is an optional argument which specifies which user should be used as the
primary author of a commit. If the option is not specified, the user obtained
from `git config user.name` will be the primary author.

## Disable mob programming mode

```sh
git mob solo
```
