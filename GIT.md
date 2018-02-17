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

---

## git diff

`git diff` shows the changes since your last commit.

---

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
