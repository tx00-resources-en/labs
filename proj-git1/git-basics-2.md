### Git basics 2

### Using Git with Command Line

To start using Git, we are first going to open up our Command shell.

For Windows, you can use Git bash, which comes included in Git for Windows. For Mac and Linux you can use the built-in terminal.

The first thing we need to do, is to check if Git is properly installed:

```bash
    git --version
    git version 2.38.1.windows.1
```

If Git is installed, it should show something like `git version X.Y`

### Configure Git

Now let Git know who you are. This is important for version control systems, as each Git commit uses this information:

```bash
    git config --global user.name "My Name"
    git config --global user.email "my.name@metropolia.fi"
```

Change the user name and e-mail address to your own. You will probably also want to use this when registering to GitHub later on.

**Note:** Use `global` to set the username and e-mail for **every repository** on your computer.

If you want to set the username/e-mail for just the current repo, you can remove `global`

---

### Creating Git Folder

Now, let's create a new folder for our project:

```bash
    mkdir myproject
    cd myproject
```

`mkdir` **make**s a **new directory**.

`cd` **changes** the **current working directory**.

Now that we are in the correct directory. We can start by initializing Git!

**Note:** If you already have a folder/directory you would like to use for Git:

Navigate to it in command line, or open it in your file explorer, right-click and select "Git Bash here"

---

### Initialize Git

Once you have navigated to the correct folder, you can initialize Git on that folder:

```bash
    git init
    Initialized empty Git repository in /Users/user/myproject/.git/
```

You just created your first Git Repository!

**Note:** Git now knows that it should watch the folder you initiated it on.

Git creates a hidden folder to keep track of changes.

#### Test Yourself

Insert the missing part of the command to check which version of Git (if any) is installed.

```bash
git ...

```

---

### Git Adding New Files

You just created your first local Git repo. But it is empty.

So let's add some files, or create a new file using your favorite text editor. Then save or move it to the folder you just created.

For this example, I am going to use a simple HTML file like this:

```html
<!DOCTYPE html>

<html>
  <head>
    <title>Hello World!</title>
  </head>
  <body>
    <h1>Hello world!</h1>
    <p>This is the first file in my new Git Repo.</p>
  </body>
</html>
```

And save it to our new folder as `index.html`.

Let's go back to the terminal and list the files in our current working directory:

```bash
    ls
```

`ls` will **list** the files in the directory. We can see that `index.html` is there.

Then we check the Git `status` and see if it is a part of our repo:

```bash
    git status
```

Now Git is **aware** of the file, but has not **added** it to our repository!

Files in your Git repository folder can be in one of 2 states:

- Tracked - files that Git knows about and are added to the repository
- Untracked - files that are in your working directory, but not added to the repository

When you first add files to an empty repository, they are all untracked. To get Git to track them, you need to stage them, or add them to the staging environment.

#### Test Yourself

Check the status of the Git:

```bash
git ...
```

---

### Git Staging Environment

One of the core functions of Git is the concepts of the Staging Environment, and the Commit.

As you are working, you may be adding, editing and removing files. But whenever you hit a milestone or finish a part of the work, you should add the files to a Staging Environment.

**Staged** files are files that are ready to be **committed** to the repository you are working on. You will learn more about `commit` shortly.

For now, we are done working with `index.html`. So we can add it to the Staging Environment:

```bash
    git add index.html
```

The file should be **Staged**. Let's check the status::

```bash
    git status
    On branch master

    No commits yet

    Changes to be committed:
      (use "git rm --cached ..." to unstage)
        new file: index.html
```

Now the file has been added to the Staging Environment.

---

#### Git Add More than One File

You can also stage more than one file at a time. Let's add 2 more files to our working folder. Use the text editor again.

A `README.md` file that describes the repository (recommended for all repositories):

```markdown
# hello-world

Hello World repository for Git tutorial  
This is an example repository for the Git tutoial on https://www.w3schools.com

This repository is built step by step in the tutorial.
```

A basic external style sheet (`bluestyle.css`):

```css
body {
  background-color: lightblue;
}

h1 {
  color: navy;
  margin-left: 20px;
}
```

And update `index.html` to include the stylesheet:

```html
<!DOCTYPE html>

<html>
  <head>
    <title>Hello World!</title>

    <link rel="stylesheet" href="bluestyle.css" />
  </head>
  <body>
    <h1>Hello world!</h1>
    <p>This is the first file in my new Git Repo.</p>
  </body>
</html>
```

Now add all files in the current directory to the Staging Environment:

```bash

    git add --all
```

Using `--all` instead of individual filenames will `stage` all changes (new, modified, and deleted) files.

```bash
    git status
    On branch master

    No commits yet

    Changes to be committed:
      (use "git rm --cached ..." to unstage)
            new file:   README.md
            new file:   bluestyle.css
            new file:   index.html
```

Now all 3 files are added to the Staging Environment, and we are ready to do our first `commit`.

**Note:** The shorthand command for `git add --all` is `git add -A`

#### Test Yourself

Add index.html to the Stating Environment:

```bash
git ... index.html
```

---

### Git Commit

Since we have finished our work, we are ready move from `stage` to `commit` for our repo.

Adding commits keep track of our progress and changes as we work. Git considers each `commit` change point or "save point". It is a point in the project you can go back to if you find a bug, or want to make a change.

When we `commit`, we should **always** include a **message**.

By adding clear messages to each `commit`, it is easy for yourself (and others) to see what has changed and when.

```bash
    git commit -m "First release of Hello World!"
    [master (root-commit) 221ec6e] First release of Hello World!
     3 files changed, 26 insertions(+)
     create mode 100644 README.md
     create mode 100644 bluestyle.css
     create mode 100644 index.html
```

The `commit` command performs a commit, and the `-m "_message_"` adds a message.

The Staging Environment has been committed to our repo, with the message:  
`"First release of Hello World!"`

---

#### Git Commit without Stage

Sometimes, when you make small changes, using the staging environment seems like a waste of time. It is possible to commit changes directly, skipping the staging environment. The `-a` option will automatically stage every changed, already tracked file.

Let's add a small update to index.html:

```html
<!DOCTYPE html>

<html>
  <head>
    <title>Hello World!</title>

    <link rel="stylesheet" href="bluestyle.css" />
  </head>
  <body>
    <h1>Hello world!</h1>
    <p>This is the first file in my new Git Repo.</p>
    <p>A new line in our file!</p>
  </body>
</html>
```

And check the status of our repository. But this time, we will use the `--short` option to see the changes in a more compact way:

```bash
    git status --short
     M index.html
```

**Note:** Short status flags are:

- ?? - Untracked files
- A - Files added to stage
- M - Modified files
- D - Deleted files

We see the file we expected is modified. So let's commit it directly:

```bash
    git commit -a -m "Updated index.html with a new line"
    [master 09f4acd] Updated index.html with a new line
     1 file changed, 1 insertion(+)
```

**Warning:** Skipping the Staging Environment is not generally recommended.

Skipping the stage step can sometimes make you include unwanted changes.

#### Git Commit Log

To view the history of commits for a repository, you can use the `log` command:

```bash
    git log
    commit 09f4acd3f8836b7f6fc44ad9e012f82faf861803 (HEAD -> master)
    Author: w3schools-test
    Date:   Fri Mar 26 09:35:54 2021 +0100

        Updated index.html with a new line

    commit 221ec6e10aeedbfd02b85264087cd9adc18e4b26
    Author: w3schools-test
    Date:   Fri Mar 26 09:13:07 2021 +0100

        First release of Hello World!
```

#### Test Yourself

Commit the changes to the current repository with the message "First release!

```bash
git  ... ...  "First release!"

```

---

### Git Help

If you are having trouble remembering commands or options for commands, you can use Git `help`.

There are a couple of different ways you can use the `help` command in command line:

- `git _command_ -help` -  See all the available options for the specific command
- `git help --all` -  See all possible commands

Let's go over the different commands.

#### Git -help See Options for a Specific Command

Any time you need some help remembering the specific option for a command, you can use `git _command_ -help`:

```bash
    git commit -help
    usage: git commit [] [--] ...

        -q, --quiet           suppress summary after successful commit
        -v, --verbose         show diff in commit message template

```

**Note:** You can also use `--help` instead of `-help` to open the relevant Git manual page

#### Git help --all See All Possible Commands

To list all possible commands, use the `help --all` command:

**Warning:** This will display a very long list of commands

```bash
    $ git help --all
    See 'git help ' to read about a specific subcommand

    Main Porcelain Commands
       add                  Add file contents to the index
       am                   Apply a series of patches from a mailbox
       archive              Create an archive of files from a named tree
```

**Note:** If you find yourself stuck in the list view, `SHIFT + G` to jump the end of the list, then `q` to exit the view.

#### Test Yourself

Show the possible options for the `status` command in command line:

```bash
git ... ...
```

---

### Links

- [w3schools](https://www.w3schools.com/git/git_getstarted.asp?remote=github)