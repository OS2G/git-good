# `git` Good: how to do version control

- [`git` Good: how to do version control](#git-good-how-to-do-version-control)
  - [What is it?](#what-is-it)
  - [History](#history)
  - [How does one get it?](#how-does-one-get-it)
    - [Command-line Solutions](#command-line-solutions)
      - [Linux](#linux)
        - [Debian based](#debian-based)
        - [Arch based](#arch-based)
        - [The rest](#the-rest)
      - [macOS](#macos)
      - [Windows](#windows)
    - [Graphical Solutions](#graphical-solutions)
      - [Git for Windows](#git-for-windows)
      - [GitHub Desktop](#github-desktop)
      - [GitKraken](#gitkraken)
      - [IDE Integrations](#ide-integrations)
  - [Command-line Basics](#command-line-basics)
    - [Before starting](#before-starting)
      - [Who are you?](#who-are-you)
      - [Line endings](#line-endings)
    - [Starting a new repository](#starting-a-new-repository)
    - [`.gitignore`](#gitignore)
    - [README and your first commit](#readme-and-your-first-commit)
    - [Remote repositories](#remote-repositories)
  - [Reference](#reference)
    - [Terminology](#terminology)
    - [Commands](#commands)
    - [Other Tutorials and Websites](#other-tutorials-and-websites)


This tutorial and reference is in no way exhaustive nor is it the best. However, we do hope you still find it useful. There are plenty of tutorials and references online however you should check out if you have questions and can't find the answer. *~~Google~~ DuckDuckGo is your friend*.

## What is it?

First, you need to know what `git` is and why you may need it. It's not the only solution on the market, but it's one of the most popular. Source-control management (SCM) is a way to manage source code. If you ever have code you need to share with others, post online, or keep a history of, you will want an SCM. In the past, people would just self version files and hope they don't get mixed up, or they would just share code via emails and the likes. This it not a great way of doing things and gets quickly out of hand.

That's why we use and SCM and why we use `git`. To keep track of your code and changes, and to allow for others to collaborate on code. As long as everyone follows proper `git` etiquette, then there's usually nothing that goes wrong. It's easy to see when and what someone changed in the history and whether it's the reason your program no longer compiles. You can integrate repositories with build systems as well so you can automate testing and building of new code, as well as deploy changes quickly. It's the reason people in the industry use it.

## History

Every program has a purpose and a story. `git` was "lovingly" created out of the necessity for a better way to manage code and code history. By better, I mean free and open source. The Linux kernel was previously using BitKeeper, a proprietary SCM system that they had been using to maintain the project since 2002. The copyright holder of BitKeeper, Larry McVoy, had withdrawn free use of the product after claiming that Andrew Tridgell had created SourcePuller by reverse engineering the BitKeeper protocols. The same incident also spurred the creation of another version-control system, Mercurial (`hg`). It's been maintained since 2005.

The name has no real original meaning, but many people have given it meaning depending on their mood, such as:
- random three-letter combination that is pronounceable, and not actually used by any common UNIX command. The fact that it is a mispronunciation of "get" may or may not be relevant.
- stupid. contemptible and despicable. simple. Take your pick from the dictionary of slang
- "global information tracker": you're in a good mood, and it actually works for you. Angels sing, and a light suddenly fills the room.
- "goddamn idiotic truckload of sh*t": when it breaks

This all doesn't really matter however. What you're here to do is learn how to use it.

## How does one get it?

`git` was and always will be, at its core, a command-line based program. People aren't command-line adept however. They like to see colors, visuals, and buttons they can click on. Because of this, countless GUI based programs have been spurred which run the `git` protocol. However, it's important to know how to get around on a terminal.

### Command-line Solutions

If you're on Linux or macOS, you might already have it. Just open up a Terminal and type in `git --version` to see if you get any output. If you get a "Command not found" error, then you'll need to install it. In Windows, you will have to install it; it doesn't come prebaked.

#### Linux

This depends entirely on your distribution.

##### Debian based

```
sudo apt install git
```

##### Arch based

```
sudo pacman -S git
```

##### The rest

Either add it in, or just look it up. Arch and Debian are the two I know off the top of my head ;)

#### macOS

If you're running 10.9 or higher, you will have `git` preinstalled. Otherwise, you can install [Xcode command line tools](https://osxdaily.com/2014/02/12/install-command-line-tools-mac-os-x/) to get it installed. If you have Homebrew, you can also get it through that:
```
brew install git
```

#### Windows

You can get it via the installer [here](https://git-scm.com/download/win). Or you can install it trough Chocolatey:
```
choco install git
```

If you're running the installer, you will be bombarded with a lot of options for configuration. You can leave the defaults and be good to go, or you can tune it to your liking. What I recommend is that you:
1. Don't install the graphical front end
2. Set it up to keep the same line endings as remote (Windows and UNIX have different ways of telling applications when a line ends)

### Graphical Solutions

If you're like most people, you'll want an easy way to run git. This doesn't mean you'll be able to do everything using buttons, but your most common tasks can be done so.

#### Git for Windows

The same installer you used to get `git` on Windows has its own GUI frontend. It's not great and I really wouldn't recommend it.

#### GitHub Desktop

While it has GitHub in its name, it's actually able to work with any `git` repository. So, if you're at UNL using their GitLab, you can do so with GitHub Desktop. It's a great and simple application and an easy way to run `git`. You can download it [here](https://desktop.github.com/). They have a version for every OS and it works more or less the same. You can also install it through a package manager if you would like to.

#### GitKraken

GitKraken is a proprietary solution. They've got a free version that allows you to work with any public repositories hosted on GitHub, GitLab and BitBucket, as well as local repositories. However, they will not work with custom GitLab instances like UNL's, nor any private repository. It has a really good UI and a lot of advanced features. Sadly, that's as good as it gets. The fact that you need to pay for it when you want to work in private repositories makes it a deal-breaker for most. However, if you still want to get it, you can do so from [here](https://www.gitkraken.com).

#### IDE Integrations

Many IDEs and even text editors have integrations for `git`. They are far from equal however. IntelliJ IDEA has a fairly well made one with a very good code diff function, as does VS Code and Atom. That's as much as I know however. Some IDEs have some pretty bad integrations, like eclipse. You might be better off just grabbing something like GitHub Desktop or just using the command line.

## Command-line Basics

The reference is all fine and well and might get you want you need in a pinch, but maybe you don't know much about `git` at all. Let's get down to basics then.

### Before starting

#### Who are you?

Hold your keyboard! The nice thing about histories is that you know *who* made certain changes to the code base and how you can contact them. Of course, these don't need to be real credentials, but it's both useful and required.

To set up your credentials for all projects:
```
git config --global user.name "Linus Torvalds"
git config --global user.email "linus@null.dev"
```

To set up your credentials for a single project (overrides global settings):
```
git config user.name "Linus Torvalds"
git config user.email "linus@null.dev"
```

#### [Line endings](https://docs.github.com/en/github/using-git/configuring-git-to-handle-line-endings)

If you plan to work with others, or even different systems, you will inevitably run into a line ending issue. Windows and Unix based systems (Linux/macOS) specify what the end of a line should be denoted as. In UNIX it's `LF` while in windows it's `CRLF`. Because of this, certain windows programs won't know what to do with files made in UNIX and the same goes for some UNIX programs with Windows files.

Thankfully, `git` has a way to fix this. I recommend just letting `git` take care of it:
```
git config --global core.autocrlf true
```
This will configure Git to ensure line endings in files you checkout are correct for Windows. For compatibility, line endings are converted to Unix style when you commit files.

### Starting a new repository

Contrary to popular belief, you don't need an online or remote repository to get started. `git` is a distributed code management system. That means that every copy of a git repository can act as a remote for any other copy. You can even change the remote with ease or have multiple remotes (mirrors). Because of this, let's start with making a repository from scratch.

1. Create a new folder to hold your code: `mkdir folderName`
2. Initialize it as a `git` repository: `git init`

There, you're done. You now have a working `git` repository. You can now add files, make changes, and track history with commits. Before you do any of that, you'll want to make a `.gitignore`.

### [`.gitignore`](https://git-scm.com/docs/gitignore)

People are lazy, especially programmers. We're so lazy we came up with automated solutions to our problems so we no longer have to do them ourselves.

Problem: We want `git` to ignore certain files and folders regardless of what commands we run.
Solution: `.gitignore` file.

1. Why does it have a period in the front if its name?
   - In UNIX based systems, any file or folder that starts with a period is tagged as hidden. `.gitignore` is meant to be out of the way, which is why it's hidden.
2. How do you use it?
   - It utilizes a [Regular Expression](https://git-scm.com/docs/gitignore#_pattern_format) format that matches all files and folders with certain names or patterns. 
   - There are also ready made templates for certain projects you can download [here](https://github.com/github/gitignore)

Example:

Say you want to ignore all files that end with `.jpg` because you don't want pictures in your code repository. Lets say you also want to ignore the folder `build` and also any `.txt` files in `src` that start with `prv_`. Your `.gitignore` would look like this:
```
build/
src/prv_*.txt
*.jpg
```

### README and your first commit

Since it's usually a good idea to give people some basic instructions and descriptions about your code, people have decided to start using READMEs. More specifically: `README.md`. The `.md` denotes that it's a [MarkDown](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) formatted file. Fun fact, this document you're reading right now is a MarkDown formatted README.

So, say you make a README with a basic description of your project. Now you want to add it to be tracked and then you want to make a commit:
1. `git add README.md`
2. `git commit -m "Added a description of the project"`
3. `git push`

First, what does `add` do? It tells `git` to track a file for changes. Any time tracked files are changed, they will be ready to be part of a new commit. You can shortcut adding all files with `git add .` where `.` stands for all files in current directory. Add is a recursive operation, so you will also add any subdirectories and their files.

Next, the commit. Every commit needs a message. If someone were to look at the history, they would want to know why you made certain changes in a commit. That's why the `-m ""` flag is used, where the message is in quotes. There is etiquette to commit messages, that will be talked about later. If you were to forget to use the `-m` flag and instead you only ran `git commit`, it would take you to your default text editor to write up a message. This will probably be `vim`, a non-intuitive but powerful command-line text editor. Some basics:
- Hit `i` to insert text. Arrow keys to get around. Write your commit message at the top.
- Hit `esc` to get out of edit mode and into command mode.
- Type `:wq` to write the changes and quit (while in command mode)

Finally, the push. You can do this after a number of commits, but if you're working in an online project, it's best to push right after you're done. In fact, you should first run a `git pull` before you do a `git push` so that you can get the latest online changes before you push the newest ones. Do this ***after*** you commit however.

But wait, we never set up a remote for our `git` to track! Your `git push` probably failed with some message about no remote to track. Indeed, the next step is to set up a remote repository.

### Remote repositories

*WIP*

## Reference

### Terminology

- Remote:
  - This is the online or distant copy of the repository.
- Local
  - This is the copy on the machine you are currently using.
- Clone:
  - Noun: A copy of the repository.
  - Verb: This is the act of getting a copy of the repository from remote. This effectively downloads the source code
- Commit:
  - Noun: It's a group of changes to the repository. A commit is usually a single point in the history or timeline of the repository as well. A snapshot.
  - Verb: This is the act of packaging your latest changes into a new snapshot, ready to be pushed to "remote"
- Pull:
  - The act of getting the latest changes from remote to local. Whenever the remote has changed, you must pull before you're able to commit and push.
- Push:
  - The act of pushing the latest changes from local to remote. This is what you do when you have just made a commit.
- Branch:
  - Timelines can branch. This is effectively parallel universes. In one universe, your coin got heads, in the branching universe, it got tails. The same is true with git. A branch is a split copy of the code with different changes than the main copy, typically for development and organizational purposes. It's smart to branch your code so that collaborators don't get in each other's ways.
- Merging/Rebasing:
  - The act of combining two branches into one. Merging and Rebasing are however slightly different and have their places.
- Pull Request:
  - A set of commits from another repository or branch, waiting to get pulled into the main branch.

### Commands
All of these sub-commands have to be started with `git`. e.g. `git status`.
| Command/Term | What it does |
| :------ | :----------- |
| `init`  | Initializes a local folder as a new repository |
| `status`| Shows all latest changes and whether there is anything to commit, pull, or push |
| `clone` | Clones/copies/downloads the remote directory to your local system |
| `git fetch --all` | Get status of all remote branches |
| `pull`  | Gets the latest changes from remote |
| `add`   | Adds a file to be tracked (untracked files will not be part of a commit) |
| `commit`| Creates a snapshot of the latest tracked changes |
| `push`  | Sends your latest commits to remote |
| `branch`| Lists the branches in your repository |
| `branch name` | Creates a new branch with the name "name" |
| `checkout name` | Switches to the branch "name" |
| `merge dev` | Merges the currently tracked branch into a branch named "dev" |
| `reset` | Resets the current branch to a certain state or commit. |

### Other Tutorials and Websites

- https://git-scm.com/book/en/v2
- https://git-scm.com/docs
- https://docs.github.com/en/github/using-git
- https://www.atlassian.com/git/tutorials
