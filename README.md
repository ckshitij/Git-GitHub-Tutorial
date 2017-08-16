# Version control with Git and GitHub

## Git and GitHub: The Mile High view

- Git is the most popular program used for __"version control."__ Git lets you _save snapshots of your project_ as you build it. Each time you save a snapshot, it shows you how the version you just saved differs from the previous version. You can (and will) use Git on any kind of project, whether it's a simple website or complex iOS app.

- Git on its own is useful, but if you want to work from multiple computers or collaborate with friends, simply saving a snapshot to your local machine isn't enough; you need to save a version to a server in the cloud that your co-workers can access. For that, you'll use __GitHub__, the _most popular service for hosting code remotely_. After saving a snapshot to Git, you'll __"push it"__ to GitHub and then you'll _have a copy stored on their servers_. If you then switched to a new computer (or if a collaborator logged in from a different computer), you could __"pull"__ a copy from GitHub, and work from exactly where you left off.

## Installing Git and GitHub
+ First, you'll need a GitHub account. Create an account by clicking [this link](https://github.com/) and following their instructions.

+ Next, you need to install Git. One approach is installing GitHub's Mac or Windows interface (or GUI), and letting their GUI take care of the rest (note that you could use their GUI to control Git, but you will learn how to control Git from the command line as most developers do).

## Mac Users

+ Newer Mac's come with git installed. To test if you have git already, open the terminal program and type ```git --version.``` That should give you a version number. The specific number isn't overly important, and you can check with your mentor to ensure you are up to date.

+ If you get an error, then you will need to visit [GitHub for Mac](https://desktop.github.com/) then download and open the application. You'll be greeted with a setup window; enter the same credentials that you used for GitHub (don't worry about the 2-factor authentication at this point). In the same pop-up, there is an advanced tab. In the advanced tab, click ```Install Command Line Tools```. You can also access the same menu by clicking the application name, and opening the preferences.

+ Installing the command line tools will prompt you for your administrator password, and then you'll be ready to use Git from the command line.

+ From here on out, try not to use the GUI to help you get used to using the command line. As a developer, there are many powerful tools at your disposal that require the command line, so getting used to it now will be very beneficial.

## Windows GUI Install

+ Visit [GitHub for Windows](https://desktop.github.com/) Website and follow their installation instructions. 
+ Once you've installed and opened it, you'll be greeted with a setup window; enter the same credentials that you used for GitHub (don't worry about the 2-factor authentication at this point). 
+ Once you have finished the walkthrough, you won't need to use the GUI anymore. You may notice that the installer also installed a second program called ```Git bash```. 
+ This is a unix style terminal application that will allow you to interact with Git and your computer using the same commands as a Mac or Linux.

## Configuring Git
+ First, save your user name and Email in Git. You'll only have to do this once. Make sure the username and Email matches the credentials of your GitHub account. Use the following commands:
  ```sh
    git config --global user.name "Kshitij Chaurasiya"
    git config --global user.email kshitij.chaurasiya@gmail.com
  ```
## Initializing a Git Repository

+ We're going to learn how to initialize. This refers to when you add Git's version control to a project.

+ To do this, let's quickly create a throwaway project that we can push to GitHub. From the command line, navigate to your projects folder, and then create a new folder called __"first_push"__ by running `mkdir first_push`. Now run `cd first_push` to move inside folder.

+ Next we need to create a file inside of this folder, because Git doesn't pay attention to empty folders. Enter the command `touch README.md`. It's a common convention to add a file __called README.md__. .md is the suffix for [__Markdown files__](https://daringfireball.net/projects/markdown/), and Markdown is a language that looks a lot like plain text, but that gets translated into HTML. You'll probably want to learn Markdown at some point in your career as a frontend developer, but don't worry about that for now.

+ For good measure, let's add some text to README.md. You can do this by opening the file in [__Sublime Text__](https://www.sublimetext.com/) and saving some text, or you can try doing this from the command line with `echo "foo bar bizz bang" >> README.md`.

+ Now that we have a throwaway project, we're ready to initialize. Verify that you're inside of your `first_push` folder by printing your working directory (are you still saying 'pwd' out loud?). If you aren't, navigate there.

+ Now, use the `git init` command to __"initialize" the repository__:
  ```sh
    $ cd projects/first_push/
    $ git init
    Initialized empty Git repository in /home/Desktop/projects/first_push/.git/
  ```
+ Notice how Git tells you that you created the repository in the .git directory. This is a new directory that Git creates where all of the history for the project will be stored. The existence of a .git directory is also used to inform Git that you are working within a repository. The dot at the start of the directory name indicates that it is a hidden directory (you won't see it if you open the folder in a graphical interface).

## Checking Status and Branches
+ Take a look at what Git sees when a new repository is initialized. To do that, type `git status` into your command line. This command will soon be your best friend when using Git: it tells you everything you need to know about the current state of the repository. It's similar to `pwd` in that it doesn't cause anything to change; rather it's a sort of check for where you are:
  ```sh
    $ git status
    # On branch master
    #
    # Initial commit
    #
    # Untracked files:
    #   (use "git add <file>..." to include in what will be committed)
    #
    #       README.md
    #
    nothing added to commit but untracked files present (use "git add" to track)
  ```
+ First it tells you that you're working on the __master branch__. A single repository can have multiple branches, each containing a different version of the code. It's common to use master as the stable branch, which contains production-ready code (the code powering your actual, live product), and a development branch which is used as you develop new features (code not shipped to users until it's ready). For now, just use the master branch and do all your development on that.

## "Saving" your Progress
+ The next important piece of information Git gives when you type `git status` is the status of the files. Currently you have one __ "untracked" file__. Untracked files are ones that are inside the repository but not under version control. To take a step back, when you save a Word document, you only need to do one thing: __hit "save."__ In Git, saving a file requires two steps: _telling Git to track the file (what's called, "adding" it), and then saving it (what's called "committing")_.

+ Generally you don't want to have untracked files within your repository. So use `git add` followed by the file name to tell Git to track any changes made to the files. Type the following two lines:

  ```sh
    $ git add README.md
  ```
+ Now see what's changed in your status:
  ```sh
    $ git status
    # On branch master
    #
    # Initial commit
    #
    # Changes to be committed:
    #   (use "git rm --cached <file>..." to unstage)
    #
    #       new file:   README.md
    #
   ```
+ Now that Git is tracking your README.md, you can commit it to store this particular snapshot of your project. Try committing the changes using the `git commit` command:
  ```sh
    $ git commit -m "Initial commit"
    [master (root-commit) f9ba0e4] Initial commit
    1 file changed, 0 insertions(+), 0 deletions(-)
    create mode 100644 README.md
   ```
 + The file has been committed successfully. To confirm that everything was committed properly, type `git status`:
   ```sh
     $ git status
     # On branch master
     nothing to commit, working directory clean
   ```
 + When you see `nothing to commit, working directory clean`, you know that all your recent work was committed.
 
## Saving your Snapshot to GitHub
+ Now that you have your first Git repo up and running you want to send it to GitHub so your co-workers can start adding to it. Go to the [__create new repository__](https://github.com/new) page, fill in the information for your repository, and hit Create Repository:

![img1](https://github.com/ckshitij/HowToUse-Git-Github/blob/master/img1.png)

+ When you have created the GitHub repository you will be shown a screen with some instructions for linking your Git repository with the remote GitHub repository: 

![img2](https://github.com/ckshitij/HowToUse-Git-Github/blob/master/img2.png)

+ Because you have an existing repository set up on your computer, follow the second set of instructions. First, add the GitHub repository as a remote to your local Git repository using the `git remote add` command (copy the command from GitHub rather than here):
  ```sh
    $ git remote add origin https://github.com/ckshitij/first_push.git
  ```
+ A remote is a copy of your local repository which is held somewhere else (on GitHub's servers, in this case). You can push changes to a remote or pull changes from a remote to make sure that your local and remote repositories stay in sync. You can have more than one remote for a single repository. For example, you may have a remote which belongs to a collaborator so you can pull changes they have made into your local repository. Or you may have a separate remote which you will push to in order to deploy the latest version of your code.
+ Here you are creating a remote called origin. This is the name that is conventionally given to your main remote. You should push changes up to your origin remote on a regular basis so you have an up-to-date backup of your code and its history.

## Push your commits to the GitHub repository.
+ Now back on the command line, send your changes to the remote repository using the git push command. If it asks for your password, and you notice that it doesn't seem to respond as you type, know that the terminal is registering your keystrokes; as a security feature, it won't provide visual feedback that reveals the length of your password.
  ```sh
    $ git push origin master
    Username for 'https://github.com': ckshitij
    Password for 'https://ckshitij@github.com':
    Counting objects: 3, done.
    Writing objects: 100% (3/4), 235 bytes | 0 bytes/s, done.
    Total 3 (delta 0), reused 0 (delta 0)
    To https://github.com/ckshitij/first_push.git
    * [new branch]      master -> master
    Branch master set up to track remote branch master from origin.
  ```
+ This command is doing a couple of things. First, it will create the master branch in the remote repository because it does not currently exist. Then it sends the most recent snapshot of the newly created master branch so the copy on GitHub matches our local copy.

+ Try visiting your repository on the GitHub website. You should see that your local files and change history are now available to view online.

## Pulling from GitHub
+ There's one more basic function of Git you need to know: how to pull from a remote repository so that your version matches the version on a remote server. To do so, you'll use the `git pull` command, pulling from the master branch. Type the following command:
  ```sh
    $ git pull origin master
    Already up-to-date.
  ```
 + Since the repo you're pulling from is already the same as your local repo, git compares the two and notifies you that your local version is up-to-date. If the remote version were different than your local version, it would overwrite your local version with any updated changes, such as a new feature or bug fix that a co-worker had developed.
 
## Git Cheatsheet
+ _Use this cheatsheet as a reference for each of the steps in the basic git workflow_.

+ _How to commit your work for the first time in a new project_:

  + __Initialize a repository__: type `git init`. Command line should say "Initialized empty Git repository"
  + __Check the repository__: type `git status`. It should show you the untracked files.
  + __Save your progress__: track the file by adding it using git add followed by each of the filenames, one at a time.
  + __Check what has changed__: type `git status`.
  + __Commit the changes__: type `git commit -m "commit message"`.
  + Success! If you type git status You should see __"nothing to commit, working directory clean".__

+ _Pushing your snapshot to GitHub_:

  + Go to github.com and _create a new repository_
  + Add GitHub repository as a __remote branch__: Use `git remote add origin git@github.com...`(follow GitHub's instructions for this line)
  + __Send changes to repository__: type `git push origin master` to send your committed changes.
  + __To pull from GitHub__: Use the command `git pull` to keep your version up-to-date with the remote version
