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
      - [Default text editor](#default-text-editor)
    - [Using the `git` command](#using-the-git-command)
    - [Starting a new repository](#starting-a-new-repository)
    - [`.gitignore`](#gitignore)
    - [README and your first commit](#readme-and-your-first-commit)
    - [Remote repositories](#remote-repositories)
      - [Remote tracking](#remote-tracking)
      - [Cloning](#cloning)
  - [Command-line Advanced](#command-line-advanced)
    - [Branches](#branches)
    - [Merging](#merging)
    - [Stash/Pop](#stashpop)
    - [Merge Conflicts](#merge-conflicts)
    - [Resetting](#resetting)
    - [Reverting](#reverting)
    - [Rebasing](#rebasing)
    - [Forking](#forking)
    - [Pull Requests](#pull-requests)
  - [Reference](#reference)
    - [Terminology](#terminology)
    - [Commands](#commands)
    - [Other Tutorials and Websites](#other-tutorials-and-websites)
      - [Generic](#generic)


This tutorial and reference is in no way exhaustive. However, we do hope you still find it useful. Start here, however if you can't find the answer to your question *~~Google~~ DuckDuckGo is your friend*.

## What is it?

First, you need to know what `git` is and why you need it. It's not the only solution on the market, but it's one of the most popular. Source-control management (SCM) is a way to manage source code. If you ever have code you need to share with others, post online, or keep a history of, you will want an SCM. In the past, people would just self version files and hope they don't get mixed up, or they would just share code via emails and the likes. This it not a great way of doing things and gets quickly out of hand.

That's why we use and SCM and why we use `git`. To keep track of your code and changes, and to allow for others to collaborate on code. As long as everyone follows proper `git` etiquette, then there's usually nothing that goes wrong. It's easy to see when and what someone changed in the history and whether it's the reason your program no longer compiles. You can integrate repositories with build systems as well so you can automate testing and building of new code, as well as deploy changes quickly. It's the reason people in the industry use it.

## History

Every program has a purpose and a story. `git` was "lovingly" created out of the need for a better way to manage code and code history. By better, I mean free and open source. The Linux kernel was previously using BitKeeper, a proprietary SCM system that they had been using to maintain the project since 2002. The copyright holder of BitKeeper, Larry McVoy, had withdrawn free use of the product after claiming that Andrew Tridgell had created SourcePuller by reverse engineering the BitKeeper protocols. The same incident also spurred the creation of another version-control system, Mercurial (`hg`). It's been maintained since 2005.

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

#### Default text editor

By default, `git` will probably be associated with `vim`. This is a hard to use command-line only text editor if you've never used it before. However, if you have a cheat sheet available or someone to help you, it can be pretty easy to get around in once you know the commands and keyboard shortcuts. However, not everyone will want to use `vim`. Maybe you like `nano`, or maybe you'd rather use something graphical like Atom or VS Code. Well, this command is for you:
```
git config --global core.editor "path/to/editor --wait_flag"
```
This is a little generic and might not be very useful without context. `git` will only open a text editor up if it needs input for a reason or another. Most commonly, this will happen when you make a new commit and don't specify a message. That means the text editor will need to be opened in a specific way for it to integrate with `git` properly. Here are some common editors and their respective commands:
- Atom:
  - `git config --global core.editor "atom --wait"`
- VS Code:
  - `git config --global core.editor "code --wait"`
- Sublime Text:
  - `git config --global core.editor "'C:/Program Files (x86)/sublime text 3/subl.exe' -w"`
- Notepad++:
  - `git config --global core.editor "'C:/Program Files (x86)/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin"`

### Using the `git` command

While the rest of this tutorial will go into setting up a repo and so on, the most helpful thing you should know is how to get to the help menu.

`git --help` will open up a documentation or print out the possible commands. This can then be extended to something like `git init --help` which will give you specific documentation on the `init` subcommand.

Another very useful command is `git status`. This will query the local repository for changes and status, printing them out.

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

#### Remote tracking

So, now that you have a running `git` repo, you want to now push it somewhere online to live. Keep in mind that you can do this with any currently populated folder. A great example of this is that you started to add code and you now want to turn it into a `git` repo. You can run `git init`, `git add .`, `git commit` and be ready to push it to a remote repo. But first, we need to set the remote.

Before you set it however, you need to create it within the remote tracker. There are many `git` services, the most popular being GitHub, followed by GitLab and probably BitBucket. There are many smaller ones, or you can even set up your own on a server.

Let's say you want to do this on GitHub. First, you will need an account. Once you register and login, you can then create a new one by clicking the "+" in the upper right corner or by finding the "New" button. You can also visit [github.com/new](https://github.com/new). 

Once there, name it whatever you want. Set it to private or public, and ***DO NOT*** initialize your repository. Just create an empty one. We do this so that you can push an already existing repo to GitHub.

Now to finally set up remote tracking:
```
git remote add origin REMOTE_URL
```
where `REMOTE_URL` is the url of the online, uninitialized git repository.

Once done, rerun the `git push` command. It will aks you for your credentials (GitHub username and password), and then it will push up the changes. If all went well, you can refresh the online repository, and you should now have the changes posted.

What if you already had a remote however and you wanted to change it to a new one? Say you made a project on GitLab and you want to move it to GitHub. Same story. Set up an uninitialized GitHub repo and then run:
```
git remote set-url origin REMOTE_URL
```
Then push like before.

Ok. You can now initialize local folders as `git` repos as well as push then to new online hosts. What if you want to get a repo hosted online to use on your local machine?

#### Cloning

This is simple. In fact, if you don't want to initialize local repos and then push changes online, it might be easier to first initialize a repo online and then clone.

To clone, run the following:
```
git clone REMOTE_URL
```
where `REMOTE_URL` is the `git` url of the remote repository hosted online. This will clone it into a new folder by the name of the `.git` file that the URL had. e.g. `https://github.com/OS2G/git-good.git` will clone into a new folder named `git-good`. If `git-good` already exists, the clone will fail. Your option is to clone elsewhere, or instead, specify the name. You can do this like so:
```
git clone REMOTE_URL OUTPUT_DIR
```
where `OUTPUT_DIR` is the name of the folder you would like to clone into.

This concludes the basics of `git` command-line. You know how to make new repos and get existing ones, how to make new commits, pull changes, and push your own. You also know you can always get help for every command as well as get the status of the repo.

Now, onto the stuff everyone has questions about.

## Command-line Advanced

### Branches

`git` keeps a timeline of code, and timelines can branch. This is effectively parallel universes. In one universe, your coin got heads, in the branching universe, it got tails. The same is true with `git`. A branch is a split copy of the code with different changes than the main copy, typically for development and organizational purposes. It's smart to branch your code so that collaborators don't get in each other's ways.

This can also be set up as a protection measure. Say you want to keep `main` as your default stable branch. Only code that is functional and builds is in `main`. To keep this true, you make a new branch named `dev` that you regularly push changes to. If someone pushes something to `dev` that happens to break the code, then the code in `main` is safe and untouched. When the code in `dev` has been thoroughly tested and is ready to be pulled into `main`, a merge is performed, or a pull request made.

Anyways, there are a number of way to view, switch, and manage branches in a repository. The basic command that manages and views branches is:
```
git branch
```
Make sure you run this without anything after the `branch`. This will list all branches available locally. However, if you wanna see branches on the remote as well, you will first need to run:
```
git fetch --all
```
which will get all the meta-data for every branch. Now, if you run `git branch`, you will see all of the branches both locally and on remote.

Now, say you want to create a new branch:
```
git branch BRANCH_NAME
```
where `BRANCH_NAME` is the name of the branch you would like to create. Once created, you can now manage it.

Let's say you accidentally created it and now you need to delete it:
```
git branch -d BRANCH_NAME
```

Maybe you just misnamed the branch, you can rename it like so:
```
git branch -m OLD_BRANCH NEW_BRANCH
```
This is actually a move command. Similar to Unix systems, there's not dedicated

What if you want to switch to switch to a newly created branch? You need to check it out:
```
git checkout BRANCH_NAME
```
If you run `git status`, it will tell you what branch you are tracking.

Now, programmers are lazy, so they made a shortcut to both create and switch to a branch in one go:
```
git checkout -b BRANCH_NAME
```
The `-b` flag tells `checkout` to create the branch you want to check out.

The last key to all of this is making the new branch visible on remote. To do so, you need to push any new commits on the branches with a new push command:
```
git push origin BRANCH_NAME
```
This will tell `push` to push to the URL at `origin` and to push the branch `BRANCH_NAME`.

So, you can create, view, check out, and manage branches. What if you have been on a branch a while and now want to merge the changes into another branch.

### Merging

There are a number of methods you can "merge" branches. The classic is a simple `merge` command however.

What you need to do is `checkout` the branch you wish to merge *into*. Then, you will need to `merge` from the branch you specify:
```
git merge BRANCH_NAME
```
where BRANCH_NAME is the branch you wish to merge *from* in to the *current* branch. This is important. The branch you have checked out that is printed in `git status` will have `BRANCH_NAME` merged into it.

Once the merge completes, you may need to commit changes (it may prompt you automatically for a commit message), and then you need to push the changes.

Merging can be a nasty process however, which may lead to something called a *merge conflict*. This is what all users of `git` dread.

### Stash/Pop

### [Merge Conflicts](https://docs.github.com/en/github/collaborating-with-issues-and-pull-requests/about-merge-conflicts)

Oh no! You tried to pull changes from remote or you just tried merging branches and you just got a *merge conflict*. What do you do? Do you delete you repository and re-clone? Do you scream in agony because all of your work is destroyed?

Maybe. At least that's what I did before I understood the flow `git` requires to keep things smooth. 

First. How to prevent merge conflict hell when pulling new code.
1. `git add changed_files`
2. `git commit`
3. `git pull`
4. MERGE CONFLICT!

But this is fine. You just committed your code. You can simply run:
```
git merge --abort
```
if you want to cancel the merge, which should resolve and undo the merge request.

Even if you didn't commit you code before hand, or you were merging two branches, you can still try to `git merge --abort` to undo the changes. This will not always work however, so keep that in mind. If you're *really* paranoid, you can make a backup of your local repo before you decide to pull changes or make any merges, just so that you have a way to get back to an old working repo.

But you will inevitably have to merge code anyways. You need the newest changes anyways, so how do you manually merge files?

Well, `git` came up with a way to signify changes between commits in files. If you're using a graphical program (which I would recommend exactly for this problem), then you can see code diffs (differences) and then choose which segment of code you wish to keep between files. This is still a long process and takes a while to complete, but it's still much better than the alternative:
1. Generate a list of the files affected by the merge conflict using `git status`. In this example, the file styleguide.md has a merge conflict.
```
> # On branch branch-b
> # You have unmerged paths.
> #   (fix conflicts and run "git commit")
> #
> # Unmerged paths:
> #   (use "git add ..." to mark resolution)
> #
> # both modified:      styleguide.md
> #
> no changes added to commit (use "git add" and/or "git commit -a")
```
2. Open your favorite text editor, and navigate to the file that has merge conflicts. Some text editors and IDEs have plugins that make it easier to manage and see all the places you have conflicts. VS Code is a good option for instance.
3. To see the beginning of the merge conflict in your file, search the file for the conflict marker `<<<<<<<`. When you open the file in your text editor, you'll see the changes from the HEAD or base branch after the line `<<<<<<< HEAD`. Next, you'll see `=======`, which divides your changes from the changes in the other branch, followed by `>>>>>>> BRANCH-NAME`. In this example, one person wrote "open an issue" in the base or HEAD branch and another person wrote "ask your question in IRC" in the compare branch or branch-a.
```
If you have questions, please
<<<<<<< HEAD
open an issue
=======
ask your question in IRC.
>>>>>>> branch-a
```
4. Decide if you want to keep only your branch's changes, keep only the other branch's changes, or make a brand new change, which may incorporate changes from both branches. Delete the conflict markers <<<<<<<, =======, >>>>>>> and make the changes you want in the final merge. In this example, both changes are incorporated into the final merge:
```
If you have questions, please open an issue or ask in our IRC channel if it's more urgent.
```
5. Now, you need to add, or stage the files you've fixed using `git add .`
6. And finally, `git commit` and `git push`.

What if you made some changes but decided you didn't like them, and now you can't pull new changes from remote because you haven't committed your changes? That's where `reset` comes into play.

### Resetting

There are times you want to undo changes you have made to a git repo. This can be within git as it's tracking files, or maybe the physical files themselves. This is where `git reset` comes into play. It is a *dangerous* command. It can be destructive if you do something wrong.

There are a few use cases for it however.

*WIP*

### Reverting

### Rebasing

### Forking

Forking is a simple but useful tool. The nice thing about `git` is that you can publish code online. While you do have the ability keep your repo private, many people like hosting public projects. In a way, it's like a portfolio, showing off your achievements and work with a history of the steps you took to get there. More importantly, it encourages collaboration.

What if you want to make changes to someone's repository you have no maintainer access to? While a public repository will always let you clone the repo, you will not be able to push any changes unless you were given permission to do so. This is where forking comes in. A fork in a road is a branch into two paths. By "forking" the project, you create a fork in the road where the project now takes on a different direction. This direction is led by you, the forker. There are a number of reasons you may want to fork a project. The two most common are:
1. The project's maintainer no longer maintains the code. You wish to continue where she left off, so you fork and continue the work.
2. You wish to make a pull request.

Forking isn't done within `git` however. You need to go to the website, such as GitHub, and click the fork button on a repository. You can manually "fork" however by cloning, setting a new remote, and pushing the code to the new remote. However, this is all done with the website automatically, so it's much easier that way.

### Pull Requests

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
#### Generic
- https://git-scm.com/book/en/v2
- https://git-scm.com/docs
- https://docs.github.com/en/github/using-git
- https://www.atlassian.com/git/tutorials
