# Git Cheat Sheet

This sheet is made for reference about git and all useful shell commands.
The information used in the sheet is from the [udacity](https://udacity.com) git and github course.

# Table of Contents

1. [First Time setup](#first-time-setip)
   ..1. [User name](##sets-up-git-with-your-name)
   ..2. [Email setup](##sets-up-git-with-your-email)
   ..3. [Colour setup](##makes-sure-that-git-output-is-coloured)
   ..4. [Conflict setup](##displays-the-original-state-in-confilct)
1. [editor setups](#editor-setups)
   ..1. [atom](##atom-editor-setup)
   ..2. [sublime](##sublime-text-setup)
   ..3. [vscode](##vscode-setup)

# First time use setup

## sets up Git with your name

`git config --global user.name "<Your-Full-Name>"`

---

## sets up Git with your email

`git config --global user.email "<your-email-address>"`

---

## makes sure that Git output is coloured

`git config --global color.ui auto`

---

## displays the original state in a conflict

`git config --global merge.conflictstyle diff3`

`git config --list`

---

# Editor setups

## atom editor setup

`git config --global core.editor "atom --wait"`

---

## Sublime text setup

`git config --global core.editor "'/Applications/Sublime Text 2.app/Contents/SharedSupport/bin/subl' -n -w"`

---

## VSCode Setup

`git config --global core.editor "code --wait"`

---

## create new repo local

`git init`

Use the git init command to create a new, empty repository in the current directory.

`$ git init`

Running this command creates a hidden .git directory. This .git directory is the brain/storage center for the repository. It holds all of the configuration files and directories and is where all of the commits are stored.

---

## clone a repo

`git clone <github-repo>`

Used to make an identical copy.

`git clone <github-repo> <your-project-name>`

Used to make an identical copy and rename the project.
This command:

1. takes the path to an existing repository
2. by default will create a directory with the same name as the repository that's being cloned
3. can be given a second argument that will be used as the name of the directory
4. will create the new repository inside of the current working directory

---

## check status of files

`git status`

This command will:

1. tell us about new files that have been created in the Working Directory that Git hasn't started tracking, yet
2. files that Git is tracking that have been modified
3. a whole bunch of other things that we'll be learning about throughout the rest of the course ;-)

---

## git log

`git log`

By default, this command displays:

1. the SHA
2. the author
3. the date
4. and the message
   ...of every commit in the repository. I stress the "By default" part of what Git displays because the git log command can display a lot more information than just this.

* **the SHA** - git log will display the complete SHA for every single commit. Each SHA is unique, so we don't really need to see the entire SHA. We could get by perfectly fine with knowing just the first 6-8 characters. Wouldn't it be great if we could save some space and show just the first 5 or so characters of the SHA?

* **the author** - the git log output displays the commit author for every single commit! It could be different for other repositories that have multiple people collaborating together, but for this one, there's only one person making all of the commits, so the commit author will be identical for all of them. Do we need to see the author for each one? What if we wanted to hide that information?

* **the date** - By default, git log will display the date for each commit. But do we really care about the commit's date? Knowing the date might be important occasionally, but typically knowing the date isn't vitally important and can be ignored in a lot of cases. Is there a way we could hide that to save space?

* **the commit message** - this is one of the most important parts of a commit message...we usually always want to see this

`git log --oneline` reduces the output to a single line

This command:

1. lists one commit per line
2. shows the first 7 characters of the commit's SHA
3. shows the commit's message

`git log --stat`

This command:

1. displays the file(s) that have been modified
2. displays the number of lines that have been added/removed
3. displays a summary line with the total number of modified files and lines that have been added/removed

`git log -p`

the git log -p output:

* 🔵 - the file that is being displayed
* 🔶 - the hash of the first version of the file and the hash of the second version of the file
  not usually important, so it's safe to ignore
* ❤️ - the old version and current version of the file
* 🔍 - the lines where the file is added and how many lines there are
  -15,83 indicates that the old version (represented by the -) started at line 15 and that the file had 83 lines
  +15,85 indicates that the current version (represented by the +) starts at line 15 and that there are now 85 lines...these 85 lines are shown in the patch below
* ✏️ - the actual changes made in the commit
  lines that are red and start with a minus (-) were in the original version of the file but have been removed by the commit
  lines that are green and start with a plus (+) are new lines that have been added in the commit

This command adds the following to the default output:

1. displays the files that have been modified
2. displays the location of the lines that have been added/removed
3. displays the actual changes that have been made

Git uses the command line pager, Less, to page through all of the information. The important keys for Less are:

1. to scroll down by a line, use j or ↓
2. to scroll up by a line, use k or ↑
3. to scroll down by a page, use the spacebar or the Page Down button
4. to scroll up by a page, use b or the Page Up button
5. to quit, use q

`git log --oneline --decorate --graph --all`

The --graph flag adds the bullets and lines to the leftmost part of the output. This shows the actual branching that's happening. The --all flag is what displays all of the branches in the repository.

Running this command will show all branches and commits in the repository

`git shortlog`

git shortlog displays an alphabetical list of names and the commit messages that go along with them. If we just want to see just the number of commits that each developer has made, we can add a couple of flags: -s to show just the number of commits (rather than each commit's message) and -n to sort them numerically (rather than alphabetically by author name).

`git shortlog -s -n`

shows short version

`git log --author=<author-name>` or `git log --author="<author-name>"`

will show only the commits made by that author

`git log --grep=<filter>`

will show all commits filtered on the grep input

---

## git show

`git show`
`git show <SHA>`

The git show command will show only one commit. So don't get alarmed when you can't find any other commits - it only shows one. The output of the git show command is exactly the same as the git log -p command. So by default, git show displays:

1. the commit
2. the author
3. the date
4. the commit message
5. the patch information

---

## git add

`git add -a` adds all to staging area

`git add .` adds all to the staging area

`git add <file_name>/<folder-name>` adds the file/folder to the staging area

---

## git commit

`git commit` opens up the editor is this is set. Look at [editor setups](#editor-setups)

`git commit -m "<your-message-here>"` bypasses the editor and you can pass your commit directly.

This command:

1. will open the code editor that is specified in your configuration

* (check out the Git configuration step from the first lesson to configure your editor)
  Inside the code editor:

1. a commit message must be supplied
2. lines that start with a # are comments and will not be recorded
3. save the file after adding a commit message
4. close the editor to make the commit

`git commit --amend`

#### Add Forgotten Files To Commit

Alternatively, git commit --amend will let you include files (or changes to files) you might've forgotten to include. Let's say you've updated the color of all navigation links across your entire website. You committed that change and thought you were done. But then you discovered that a special nav link buried deep on a page doesn't have the new color. You could just make a new commit that updates the color for that one link, but that would have two back-to-back commits that do practically the exact same thing (change link colors).

Instead, you can amend the last commit (the one that updated the color of all of the other links) to include this forgotten one. To do get the forgotten link included, just:

1. edit the file(s)
2. save the file(s)
3. stage the file(s)
4. and run git commit --amend

---

## git diff

`git diff` shows the changes since your last commit.

---

## git tag

`git tag`

this will verify the tag

`git tag -a v1.0`

this will add a tag to the branch your on at that moment.

`git tag -a v1.0 <SHA>`

add a tag to a different commit

`git tag -d v1.0` or `git tag --delete v1.0`

this will delete the tag useful if you misspelled

This command will:

1. add a tag to the most recent commit
2. add a tag to a specific commit if a SHA is passed

---

## git branch

`git branch`

displays a list of all branches

`git branch <branch-name>`

creates a new branch but you stay on the branch your on

`git branch -d <branch-name>`

this will delete the branch

It can be used to:

1. list all branch names in the repository
2. create new branches
3. delete branches

---

## git checkout

`git checkout <branch-name>`

will switch to that branch

`git checkout -b <branch-name>`

this will create a new branch and switch to it

---

## git merge

`git merge <name-of-branch-to-merge-in>`

this will merge the branches
When a merge happens, Git will:

1. look at the branches that it's going to merge
2. look back along the branch's history to find a single commit that both branches have in their commit history
3. combine the lines of code that were changed on the separate branches together
4. makes a commit to record the merge

`git reset --hard HEAD^`

This command is used to undo a merge "e.g. If you merged the wrong branch"

There are two types of merges:

1. Fast-forward merge – the branch being merged in must be ahead of the checked out branch. The checked out branch's pointer will just be moved forward to point to the same commit as the other branch.
2. the regular type of merge
   1. two divergent branches are combined
   2. a merge commit is created

---

## git revert

`git revert <SHA>`

This command:

1. will undo the changes that were made by the provided commit
2. creates a new commit to record the change

---

## git reset

⚠️ **Resetting Is Dangerous** ⚠️

You've got to be careful with Git's resetting capabilities. This is one of the few commands that lets you erase commits from the repository. If a commit is no longer in the repository, then its content is gone.

To alleviate the stress a bit, Git does keep track of everything for about 30 days before it completely erases anything. To access this content, you'll need to use the git reflog command.

**Relative Commit References**

There are special characters called "Ancestry References" that we can use to tell Git about these relative references. Those characters are:

* \^ – indicates the parent commit
* \~ – indicates the first parent commit
  Here's how we can refer to previous commits:

the parent commit – the following indicate the parent commit of the current commit

* HEAD^
* HEAD~
* HEAD~1

the grandparent commit – the following indicate the grandparent commit of the current commit

* HEAD^^
* HEAD~2

the great-grandparent commit – the following indicate the great-grandparent commit of the current commit

* HEAD^^^
* HEAD~3

`git reset <SHA>`

it can be used to:

1. move the HEAD and current branch pointer to the referenced commit
2. erase commits
3. move committed changes to the staging index
4. unstage committed changes

**Git Reset's Flags**

The way that Git determines if it erases, stages previously committed changes, or unstages previously committed changes is by the flag that's used. The flags are:

1. --mixed default working directory
2. --soft move changes to staging index
3. --hard move changes to trash

**Backup your branch**

`git branch backup`

this will make a backup

💡 **Back To Normal** 💡

If you created the backup branch prior to resetting anything, then you can easily get back to having the master branch point to the same commit as the backup branch. You'll just need to:

remove the uncommitted changes from the working directory
merge backup into master (which will cause a Fast-forward merge and move master up to the same point as backup)

```
git checkout -- index.html
git merge backup
```

---

# Remote repository

💡 **Always Use Topic Branches**

Remember that it's incredibly helpful to make all of your commits on descriptively named topic branches. Branches help isolate unrelated changes from each other.

So when you're collaborating with other developers make sure to create a new branch that has a descriptive name that describes what changes it contains.

## git remote

`git remote`

shows all remotes

`git remote -v`

will show all remotes + the paths

`git remote add <name-of-the-remote> <path-to-the-repository>`

This will add a path to the remote repository

`git remote rename <old-remote> <new-remote>`

## git push

`git push <remote-name> <branch-name>`

The git push command is used to send commits from a local repository to a remote repository.

## git pull

`git pull <remote-name> <branch-name>`

When git pull is run, the following things happen:

1. the commit(s) on the remote branch are copied to the local repository
2. the local tracking branch (origin/master) is moved to point to the most recent commit
3. the local tracking branch (origin/master) is merged into the local branch (master)

## git pull vs fetch

`git fetch origin master`

When git fetch is run, the following things happen:

1. the commit(s) on the remote branch are copied to the local repository
2. the local tracking branch (e.g. origin/master) is moved to point to the most recent commit

## git rebase

`git rebase -i <branch>` or `git rebase -i <number-of-commits>`

**The Rebase Command**

The git rebase command will move commits to have a new base. In the command git rebase -i HEAD\~3, we're telling Git to use HEAD~3 as the base where all of the other commits (HEAD\~2, HEAD\~1, and HEAD) will connect to.

The -i in the command stands for "interactive". You can perform a rebase in a non-interactive mode. While you're learning how to rebase, though, I definitely recommend that you do interactive rebasing.

**Ancestry References**

As a brief refresher, HEAD indicates your current location (it could point to several things, but typically it'll either point to a branch name or directly to a commit's SHA). The \~3 part means "three before", so HEAD\~3 will be the commit that's three before the one you're currently on. We're using this relative reference to a commit in the git rebase command.

# .gitignore

Globbing Crash Course
Let's say that you add 50 images to your project, but want Git to ignore all of them. Does this mean you have to list each and every filename in the .gitignore file? Oh gosh no, that would be crazy! Instead, you can use a concept called globbing.

Globbing lets you use special characters to match patterns/characters. In the .gitignore file, you can use the following:

* blank lines can be used for spacing
* \# - marks line as a comment
* \* \* matches 0 or more characters
* ? - matches 1 character
* [abc] - matches a, b, or c
* \*\* - matches nested directories - a/\*\*/z matches
  * a/z
  * a/b/z
  * a/b/c/z
    So if all of the 50 images are JPEG images in the "samples" folder, we could add the following line to .gitignore to have Git ignore all 50 images.

---

# Good commit messages

**Do**

1. do keep the message short (less than 60-ish characters)

* do explain what the commit does (not how or why!)
  **Do not**

1. do not explain why the changes are made (more on this below)
2. do not explain how the changes are made (that's what git log -p is for!)
3. do not use the word "and"

* if you have to use "and", your commit message is probably doing too many changes - break the changes into separate commits
* e.g. "make the background color pink and increase the size of the sidebar"

A good starting point is `"This commit will..."`

---

# .Git Directory Contents

We're about to take a look at the .git directory...it's not vital for this course, though, so don't worry about memorising anything, it's here if you want to dig a little deeper into how Git works under the hood.

Here's a brief synopsis on each of the items in the .git directory:

* **config file** - where all project specific configuration settings are stored.
  From the Git Book:

Git looks for configuration values in the configuration file in the Git directory (.git/config) of whatever repository you’re currently using. These values are specific to that single repository.

For example, let's say you set that the global configuration for Git uses your personal email address. If you want your work email to be used for a specific project rather than your personal email, that change would be added to this file.

* **description file** - this file is only used by the GitWeb program, so we can ignore it

* **hooks directory** - this is where we could place client-side or server-side scripts that we can use to hook into Git's different lifecycle events

* **info directory** - contains the global excludes file

* **objects directory** - this directory will store all of the commits we make
  refs directory - this directory holds pointers to commits (basically the "branches" and "tags")
