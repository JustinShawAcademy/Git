# Git

Git has become the overwhelming industry standard for version control in software development. Whether the use case for Git is individual productivity or teamwork collaboration, it is used ubiquitously in projects.

**For Collaboration:**
1. **Seamless Teamwork:** Git allows multiple developers to work on the same codebase simultaneously without overwriting each other's changes. Each person can work on their own "branch" of the project, and then these individual contributions can be merged together.
I created this documentation for myself and others as it covers the basics to advanced Git topics.

2. **Code Review and Feedback:** Platforms built on Git (like GitHub, GitLab, Bitbucket) facilitate pull requests (or merge requests). This allows team members to review each other's code, suggest improvements, and ensure code quality before changes are integrated into the main project.

**For Individuals:**
1. **Version Control and History:**: Git meticulously tracks every change made to your files. You can see who made what change, when, and why (if good commit messages are used). This detailed history is invaluable for understanding how a project evolved.

2. **Undo Mistakes (Time Machine for Code:)** If you introduce a bug, make a bad design decision, or simply want to revert to a previous working state, Git allows you to easily "go back in time" to any point in your project's history. This safety net encourages experimentation without fear of breaking things permanently.

## Git Init and Hidden Folder
### `git init`: The Birth of a Git Repository
The `git init` command is the very first step you take when you want to start tracking a project (directory/folder) with Git. It's how you tell Git, "Hey, I want to manage this directory and its contents using version control."

Here was have a folder called `gitlearn` that contains `gitone`, `gittwo`, and `gitthree` as subdirectories for my examples

![alt text](assets/image.png)

Let's go into `gitone` as the folder we want to start version controling

![alt text](assets/image2.png)

By using `git status`, it confirms that we are not currently in a Git repository, and therefore it's safe to proceed with `git init`. 

> **Question:** But before we do `git init`, how does `git status` know that `gitone` isn't a Git repository? After all, `gitone` looks like an empty folder. It knows because there isn't a `.git` (hidden) file inside of `gitone`. Once we `git init`, Git will create the `.git` file

![alt text](assets/image3.png)

> **Note:** `ls -la`  provides a comprehensive, detailed list of ALL files and directories (including hidden ones) within the current directory. After `git init` we can see that a hidden file inside `gitone` has been created.

The `.git `folder is the **heart and soul of a Git repository**. It's a hidden directory that Git creates when you initialize a new repository (`git init`) or clone an existing one (g`it clone`). without it, all the necessary information and history for Git to manage your project's version control wouldn't be possible

## Git Add, Commints and Logs
### `git add`: Staging Changes for Commit
Now, we add two files into `gitone`, `textone.txt` and `texttwo.txt`. By using `git status` we can tell that these files are not being tracked by git. But how can we do that?

![alt text](assets/image4.png)

`git add` takes the changes from our working directory (in this case, `gitone`) and moves them to the staging area (also known as the "index"). The staging area acts as a temporary buffer or a "draft" for the next commit. That simple.

![alt text](assets/image5.png)

### `git commit`: Locking in Code Changes
`git commit` takes all the changes staged with `git add` and creates a permanent, immutable snapshot of the project at that moment, complete with a unique ID and descriptive message. This action officially records the progress, adding it to the repository's historical timeline.

We see below that `testtwo.txt` did not get commited into the repo as it was not part of `git add` staging process.

![alt text](assets/image6.png)

### `git log`: Tracing Every Step in The Repository's History
`git log` views the history of commits in the repository. It essentially shows a detailed record of every "save point" (git commit) that has been made, giving  valuable insight into how the project has evolved.

![alt text](assets/image7.png)

## Git Internal Workings and Configs
### `git config`: Setting Username & Email in Git
Notice in the image above, Git knows our name and even email in the logs. How is this possible? Well it's because the `~/.gitconfig` file.

```
# Updating our ~/.gitconfig file
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

### `.gitignore`: Ignoring Files and Directories in Git

![alt text](assets/image8.png)
In `gitone`, I have created 2 files and 1 folder that cannot be commited due to the private contents (hypothetically in this case). How can we be safe that they are never commited?

![alt text](assets/image9.png)

```
# Write inside .gitignore
.env
sensitive.txt
sensitive-folder/
```

By writing the files and folders I don't want to add and commit inside `.gitignore`, we can see it does not come up as an option anymore for tracking (seen with `git status`)

![alt text](assets/image10.png)

For big projects, `.gitignore` templates can be found on [gitignore.io](https://www.toptal.com/developers/gitignore)





