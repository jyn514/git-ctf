# git: the stupid version control system

## requests
- branches
- merges
- branch merges
- merge conflicts
- cthulhu merges

## Prior Knowledge
### Required
- CLI experience (`cd`, `ls`, `mv`, `rm`)
- The `git` binary ([download](https://git-scm.com/download) or your favorite package manager)

### Recommended
- Experience with UNIX commands (`grep`, `patch`, `diff`, `shasum`)
- Familiarity with at least one terminal-based editor (`nano`, `vi`, `emacs`)
- Familiarity with config files

## Part One: Basics
Just enough info to make this talk interactive.

### Concepts
- [version control](https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control)

### Commands
- [init](https://git-scm.com/docs/git-init)
- [clone](https://git-scm.com/docs/git-clone)
- [add](https://git-scm.com/docs/git-add)
- [commit](https://git-scm.com/docs/git-commit)
- [push/pull](https://git-scm.com/docs/git-push)
- [status](https://git-scm.com/docs/git-status)

## Part Two: Uses
Everyday uses for git. Should make you comfortable with branches and history.

### Concepts
- [branches](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell)
- [merges](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging)

### Commands
- [branch](https://git-scm.com/docs/git-branch)
- [checkout](https://git-scm.com/docs/git-checkout)
- [merge](https://git-scm.com/docs/git-merge)
- [tag](https://git-scm.com/docs/git-tag)
- [show](https://git-scm.com/docs/git-show)
- [diff](https://git-scm.com/docs/git-diff)
- [log](https://git-scm.com/docs/git-log)

### Third-Party Tools
- [GUIs](https://git-scm.com/downloads/guis)
- Hosting: github, gitlab, bitbucket
- [mergetool](https://git-scm.com/docs/git-mergetool)

## Part Three: Tips and Tricks
In depth concepts and uses for git. For power users.

### Concepts
- [specifying revisions](https://git-scm.com/docs/gitrevisions)
	- `<rev>`, one of
		- `<commit>`, a SHA1 sum
		- `<describe>`, any output of `git describe`
		- `<refname>`, one of
			- a branch/tag/remote name
			- \*HEAD, any of the refs used internally by git, including stashes
		- `<refname>`@{`<time>`} gives the tree at latest point before that time  
		  (or the first commit, if the repo was made after that time)  
		where `<time>` :: {yesterday|`<ordinal number>` `<unit>` [ago]|`<date>`}  
			where `<ordinal number>` :: {1, 2, 3 ... | one, two, three ...}  
			where `<unit>` :: {second|minute|hour|day|week|month|year}[s]  
			where `<date>` :: {`<isodate>`[-`<precise time>`]}  
				where `<isodate>` :: YYYY-MM-DD  
				where `<precise time>` :: HH:MM:SS  
		also, 'last' changes the output somehow and I have no idea why.
		- `<refname>`@{`<number>`} gives the `<number>` previous commit in that tree
		- @{`<number>`}, the `<number>` previous reflog checked out
		- @{-`<number>`}, which does something I can't figure out.
		- `<branch>`@{push|upstream} shows the latest known remote commit for `<branch>`  
		  this is the same as `<default {upstream|push}>`/`<branch>`.  
		  upstream differs from push IFF you have a triangular workflow
	- `<rev>`^`<number>`, the `<number>` *parent* of the commit  
	  (not the `<number>` *previous* commit; this is relevant for merge commits with multiple parents
	- `<rev>`~`<number>`, the `<number>` *previous* commit following first parents  
	where `<number>` :: {1, 2, 3 ...}
- [triangular workflows](https://cloud.githubusercontent.com/assets/1319791/8943755/5dcdcae4-354a-11e5-9f82-915914fad4f7.png)
  ([short explanation](https://blog.github.com/2015-07-29-git-2-5-including-multiple-worktrees-and-triangular-workflows/))
- [rebasing](https://git-scm.com/book/en/v2/Git-Branching-Rebasing)
- [fast-forwarding](https://stackoverflow.com/questions/9069061)
- [resetting](https://git-scm.com/book/en/v2/Git-Tools-Reset-Demystified)
- [octopus merges](https://stackoverflow.com/questions/6520905)
  ([see also](https://www.destroyallsoftware.com/blog/2017/the-biggest-and-weirdest-commits-in-linux-kernel-git-history))

### Commands
- [remote](https://git-scm.com/docs/git-remote)
- [bisect](https://git-scm.com/docs/git-bisect)
- [rebase](https://git-scm.com/docs/git-rebase)
- [stash](https://git-scm.com/docs/git-stash)
- [revert](https://git-scm.com/docs/git-revert)
- [reset](https://git-scm.com/docs/git-reset)
- [config](https://git-scm.com/docs/git-config)
- [reflog](https://git-scm.com/docs/git-reflog)


### Flags
- `--interactive`
- `--patch`: see [`git-apply`](https://git-scm.com/docs/git-reflog)
   and the original [`patch`](https://linux.die.net/man/1/patch)
- `--cached`

## Part Four: Plumbing and Pedantry
The lowest level of git. The commands are used internally by the porcelain.

### Concepts
- [blobs](https://git-scm.com/book/en/v2/Git-Internals-Git-Objects)
- [differential vs. incremental backups](https://en.wikipedia.org/wiki/Differential_backup)
- snapshots

### Commands
- [hash-object](https://git-scm.com/docs/git-hash-object)
- [cat-file](https://git-scm.com/docs/git-cat-file)
- [describe](https://git-scm.com/docs/git-describe)
- [ls-tree](https://git-scm.com/docs/git-ls-tree.html)
- [ls-remote](https://git-scm.com/docs/git-ls-remote.html)
