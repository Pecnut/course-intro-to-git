# Interdisciplinary Research Computing: Introduction to Git
Introduction to Git course for the Interdisciplinary Research Computing I-Explore module at Imperial College

1 × 2 hour class, delivered through YouTube videos

## On completion of this workshop you will be able to:
* Use Git on your own machine as a method of version control
* Use Git to synchronise the files on your own machine with those on a remote server (both pushing to the server and pulling from the server)
* Use Git to collaborate with other users on a project, including dealing with merge conflicts

This introductory course will *not* cover **branching**.

## Prerequisites
* No programming experience is required.
* We are going to be using the [GitHub desktop app](https://desktop.github.com/), so please install this on your machine before starting.

## Course materials

### 1. Motivation and Git vs GitHub

Motivation 1: Backups and previous versions. Relevant for coding but also LaTeX, for example.

How often have you found yourself in this situation?

You're writing a document and you save it. Maybe you write some more. Once again you save.

That evening, you have a brilliant idea. You open up your laptop, type in your genius, and save.

Early next morning, you wake in a sweat. What were you thinking? You have to get rid of the rubbish you wrote last night. But what exactly did you write? Was it this? That?

This is where VERSION CONTROL comes in.

A version control system starts with a BASE version of your file, and then keeps track of the CHANGES you make. You can get to any version of your document by 'playing back' the changes.

In this way, multiple people can make changes [animation]

And as long as these changes don't CONFLICT with each other, these changes can be MERGED.

A version control system creates a permanent record of all changes to your document. Each change is called a COMMIT (you decide when that happens) and the system stores WHO made the change, and WHEN, along with a brief description of the change.

This record is called a REPOSITORY, or REPO, and repositories can be synchronised across computers, and therefore across users.

This is normally done by putting a copy of the repository online - in a central hub - and making sure everyone synchronises their repository with the remote, online version. This could be you on another computer, or someone you're working with.

GitHub is one of the most popular online hosting services for repositories, but there are others like BitBucket and GitLab.

If you don't want to synchronise between computers, you don't need to use an online host. Git - just Git - will run on your computer and you can use the full functionality that a version control system brings without going anywhere near the internet. And it's free.

This is how we're going to start - by running Git on our own computers as local version-control systems. Collaboration will come later!

What do we need to get started? Git can be run from the command line, but we're going to use the desktop application provided by GitHub - it's called GitHub Desktop! You can get it from:

* Windows/macOS: [desktop.github.com](https://desktop.github.com)
* Linux: [github.com/shiftkey/desktop](https://github.com/shiftkey/desktop)
* Old version for 32-bit Windows installations: [github.com/ahmelsayed/desktop/releases/tag/Windows-32bit](https://github.com/ahmelsayed/desktop/releases/tag/Windows-32bit)

So now you're ready to go.

But - once more - why should you use a version control system? Two great reasons:

1. It allows an unlimited 'undo'
2. It allows multiple people to work on something AT THE SAME TIME.

And Git is the most popular software for version control.

### 2. Using GitHub Desktop for the first time

You can download the GitHub Desktop software from:
* Windows/macOS: [desktop.github.com](https://desktop.github.com)
* Linux: [github.com/shiftkey/desktop](https://github.com/shiftkey/desktop)
* Old version for 32-bit Windows installations: [github.com/ahmelsayed/desktop/releases/tag/Windows-32bit](https://github.com/ahmelsayed/desktop/releases/tag/Windows-32bit)

When you open it for the first time, you will be greeted by a welcome screen:

![Welcome screen (on Windows)](images/welcome-screen.png)

You don't need to create an account with GitHub to use this software - after all, Git can run on your own computer without any connection to the internet. But later we are going to be collaborating with each other by pushing our files to GitHub as a central online repository. So now is a good time to sign in, or if you don't yet have an account with GitHub, to create one.

To create a free account:
* Click 'Create your free account'. The GitHub website loads, where you can enter your details.
* On the second screen, you can scroll down to 'Complete setup'.
* Verify your email address.
* Go back to GitHub Desktop, and choose either to 'Sign in to GitHub.com', or 'Sign in to GitHub.com using your username and password.'

On the next screen, you'll be asked for a name and email address that will be associated with all your commits:

![Configure Git screen (on Windows)](images/configure-git-screen.png)

This is a built-in feature of Git: all commits are associated with a name and email address. By default, GitHub provides you with a private `@users.noreply.github.com` email address which doesn't accept email, but does provide you with a unique identifier.

You will be ready to go when you see the home screen, which will (operating system depending) look something like this:

![Home screen (on Windows)](images/home-screen.png)

### 3. Getting started

I want you to join in as we go. Then I'll give you an exercise, and tell you how I did it.

Join in:
* Create a new repository in the GitHub Desktop client
* Idea: Birthday party.
* Files to create in Atom:
    * Text file: List people to invite, `invite.txt`
    * Text file: List of people to not allow under any circumstances, `banned.txt`
    * Text file: List of people coming, `coming.txt`
    * Picture: Photo you want to send to invite people, `last_year.jpg`
* Go to app - your changes are STAGED, ready to be committed.
* Commit! (With a description - don't repeat the change, try to explain WHY)

(Do this now if you haven't done so already)

* Make a change - see the difference in the GitHub desktop app.
* Commit the change.
* Look at the history tab (we'll use this later to revert changes)

Your turn:
* Add some more people to the lists
* Add another file - "possible themes"
* Replace the picture with another picture of the same name - see what happens

### 4. Reverting changes

The joy of Git is that you can try changing things without worrying that you won't be able to get back to where you started from. This is especially comforting for programming.

* Add people to the banned list. Commit.
* History tab > Right click > Revert this Commit.

What if you don't commit before you revert?
* No changes to see! But if you try to revert another change, it will give you an error message. Better to commit first.
* You can "discard changes" from the changes screen, but this is harder to fix if you decide discarding was a mistake (your changed file ends up in your operating system's Recycle Bin). Better to commit first.

What if you don't save before you revert?
* You will lose your changes.

Your turn:
* Create a new file, "present_ideas.txt", commit it, then revert it.

Demo:
* What about reverting multiple commits?
* Reverting UNDOES CHANGES, it doesn't take you back to a previous version.
* To get back to a previous version, you have to do it *one at a time*.
* Otherwise, you'll get a mess (demo)

* Why does this work? Where are my old versions? The .git folder

So we can now make changes, COMMIT them, and REVERT them. Next up, we're going to tell Git to ignore some files.

### 5. Ignoring files

There are occasions when we don't necessary want Git to back up, or track, files in a repository. Some examples are:
* Files containing sensitive data (e.g. personal details or API tokens)
* Files that your operating system makes (.DS_Store)
* Very large files that you don't want to sync with other people (maybe big data files)

Join in:
* Go to Repository > Repository Settings > Ignored Files
* `*.jpg` `*.png` `cake_recipes/*.*`
* Delete the image in the repository. No change!
* Create the `cake_recipes` folder and place a file in there.

Your turn:
* Add a folder "addresses" in which all text files will be ignored.
* Add some text files to the addresses folder and try to commit.

Extension: You can add exceptions using the `!`

And that's all you need for local version control! We can now COMMIT, REVERT, and IGNORE. Next up, we're going to place files on the GitHub website.

### 6. Pushing to GitHub

Time to look at sharing our code with other people. We're going to PUSH our code to a REMOTE repository on GitHub. GitHub allows repositories to be PUBLIC or PRIVATE, so even if we don't want to share, this has the benefit of backing up our code somewhere safe.

Remember that the key idea behind sharing is getting everyone to synchronise their repositories with a repository on a central hub - GitHub in our case.

* You will need a GitHub account. Sign up at [github.com](https://github.com/).
* Then sign in to GitHub by going to:
    * On Mac: GitHub Desktop > Preferences > Account > Sign in.
    * On Windows: File > Options > Account > Sign in.

* We're going to publish our repository to GitHub. Click "Publish repository"
* Let's check it out. Repository > View on GitHub.
* Make a change to our files.
* Push to GitHub.

Your turn:
* Make a change to one of your files, commit, and push.

Join in:
* Now we'll make a change on the website, and pull the change to your computer.
* Edit a text file
* Look - the button has changed. It now says `Pull origin` with a number saying how many commits are not in our local copy of the repository.
* Look - it works.

Your turn: something...

### 7. Collaborating through GitHub

We're now going to see what it's like to collaborate on a project. For this, you need to get into pairs. One member of the pair will be the OWNER, and the other will be a COLLABORATOR. Our goal is for the collaborator to make a change to the owner's repository, which will be fully synchronised. You'll switch roles afterwards to see this process both ways round.

Join in:
* Owner gives the collaborator access on GitHub.
    * Repository > View on GitHub. Settings > Collaborators > enter their username.
* Collaborator might get an email, but you can go to github.com/notifications to accept access.
* Collaborator goes File > Clone Repository. Should come up in list. Happy with local path? Then click CLONE.

Now the collaborator can make a change!
* Add your name to the list of invited people
* Commit
* Push origin
* See that it's changed on github
* Owner can now pull.
* Check out the history tab.

* Swap.

Tips on collaborating:
* Always pull before changing anything on your own machine
* Commit LITTLE and OFTEN.

Let's stay in our pairs in order to see what happens when we try editing something at the same time.


### 8. Conflict resolution

The great thing about Git is that people can work in parallel on the same project. Despite your best efforts, at some point you're probably going to step on someone's toes!

Git is pretty good at avoiding this - you can normally edit the same text file at the same time, so long as you don't try to edit the same parts, but sometimes your changes are going to overlap.

 In Git, this is called a CONFLICT, and Git offers us a mechanism to RESOLVE these overlapping changes.

 Let's make a conflict on the last repository you played with in your pair.

[ CHECK THIS WORKS !!]

 Join in:
 * Person 1: At the bottom of the invited people's list, add someone. Save.
 * Person 1: Commit and push to GitHub.
 * Person 2: WITHOUT Pulling, add someone to the invited people's list and save.
 * Person 2: Commit. (This works because we are committing locally). But then try to push to GitHub.

 This doesn't work because the push button has become "Pull origin". Git has detected that your changes overlap with the changes in the remote repository, and you are going to have to resolve this first.

 We have to PULL the changes from GitHub, MERGE them into our copy, and then PUSH that back to GitHub.

Join in:
 * Person 2: Try pulling

 Looks like this:
 ```
+<<<<<<< HEAD
 My version
+=======
+On GitHub
+>>>>>>> hexadecimal number
 ```

 * Person 2: Remove the markers added by Git and reconcile the changes. Atom makes this easy for us!
 * Person 2: Save the changes. Commit. Push. Happy days.

 Git has tracked how we have merged the files. Look at history.

 * Swap round.

 What if the conflict file is not text-based? How about two photos which have the same name?

 [ NEED TO SEE WHAT HAPPENS ]

 Despite Git's useful conflict resolution tools, dealing with conflicts is still slow and people can make mistakes. By committing small and often, you reduce the chances of having merge conflicts.

### 9. Things we are not covering

* branching
* releases
* Git integration in your favourite IDE
