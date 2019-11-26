<!-- 

# Git Overview Page - Hub page that includes:

- What is Git?
- Why use Git?
- Install/Download Git
- GitHub Cheat Sheet link
- Mini command tutorial (click through for more)
- Mini GitHub call to action (why use GitHub)
- Mini GitHub tutorial (click through for more)

# General Specs
- Title: Git Guide
- URL: /git-guide/
- Meta Description: Everything you need to know about Git, from getting started to advanced commands and workflows.
- Focus Keyword: git (110,000)
- Secondary Keywords: what is git (8,100), how to use git (2,400) 
- Word Count: 1200+
- **The focus keyword should be in the page title, url, h1 and throughout body copy.**
- The secondary keywords are semantic variations of the focus keyword and are great to use in h2, h3 and other headings.
- Written from a marketing perspective, should have an informal voice and not be exclusively technical.
- Doesn’t need to exhaustively cover the technical intricacies of the specific git command – should be beginner friendly and include a lot of the “why” and a general overview of the “how”. Can link out to more in-depth technical resources where appropriate.

-->

# Git Guide

Everything you need to know about Git, from getting started to advanced commands and workflows.

## What is Git?

Git is distributed version control software. Version control is a way to save changes over time without overwriting previous versions. Being distributed means that every developer working with a Git repository has a copy of that entire repository - every commit, every branch, every file. If you're used to working with centralized version control systems, this is a big difference!

Whether or not you've worked with version control before, there are a few things you should know before getting started with Git:

- Branches are lightweight and cheap, so it's OK to have many of them
- Git stores changes in SHA hashes, which work by compressing text files. That makes Git a very good version control system (VCS) for software programming, but not so good for binary files like images or videos.
- Git repositories can be connected, so you can work on one locally on your own machine, and connect it to a shared repository. This way, you can push and pull changes to a repository and easily collaborate with others.

## Why Use Git?

Version control is very important - without it, you risk losing your work. With Git, you can make a "commit", or a save point, as often as you'd like. You can also go back to previous commits. This takes the pressure off of you while you're working. Commit often and commit early, and you'll never have that gut sinking feeling of overwriting or losing changes.

There are many version control systems out there - but Git has some major advantages.

- Like we mentioned above, Git uses SHA compression, which makes it very fast. As long as you're working with text files, you won't need to worry about how many files you have, how big they are, or how many commits you make. Git can handle it!
- Git can handle merge conflicts, which mean that it's OK for multiple people to work on the same file at the same time. This opens up the world of development in a way that isn't possible with centralized version control. You have access to the entire project, and if you're working on a branch, you can do whatever you need to and know that your changes are safe.
- Speaking of branches, Git offers a lot of flexibility and opportunity for collaboration with branches. By using branches, developers can make changes in a safe sandbox. Instead of only committing code that is 100% sure to succeed, developers can commit code that might still need help. Then, they can push that code to the remote and get fast feedback from integrated tests or peer review. Without sharing the code through branches, this would never be possible.
- Ease of roll back - if you make a mistake, it's OK! Commits are immutable, meaning they can't be changed. (*Note: You _can_ change history, but it will create new replacement commits instead of editing the existing commits. More on that later!*) This means that if you do make a mistake, even on an important branch like master, it's _OK_. You can easily revert that change, or roll back the branch pointer to the commit where everything was fine. The benefits of this can't be overstated. Not only does it create a safer environment for the project and code, but it fosters a development environment where developers can be braver, trusting that Git has their back.

## Getting Started With Git

Depending on your operating system, you may already have Git installed. <!--[Link to installing Git.]--> But, getting started means more than having the software! To get started, it's important to know the basics of how Git works. You may choose to do the actual work within a terminal, an app like GitHub Desktop, or through GitHub.com. (*Note: while you can interact with Git through GitHub.com, your experience may be limited. Many local tools can give you access to the most widely used Git functionalities, though only the terminal will give you access to them all.)

There are _many_ ways to use Git, which doesn't necessarily make it easier! But, the fundamental Git workflow has a few main steps. You can practice all of these in the [Introduction to GitHub Learning Lab course](https://lab.github.com/githubtraining/introduction-to-github).

### Create a branch

The main branch is usually called `master`. We want to work on _another_ branch, so we can make a pull request and make changes safely. To get started, create a branch off of `master`. Name it however you'd like - but we recommend naming branches based on the function or feature that will be the focus of this branch. One person may have several branches, and one branch may have several people collaborate on it - branches are for a purpose, not a person. Wherever you currently "are" (wherever HEAD is pointing, or whatever branch you're currently "checked out" to) will be the parent of the branch you create. That means you can create branches from other branches, tags, or any commit! But, the most typical workflow is to create a branch from `master` - which represents the most current production code.

### Make change (and make a commit)

Once you've created a branch, and moved the HEAD pointer to it by "checking out" to that branch, you're ready to get to work. Make the changes in your repository using your favorite text editor or IDE. 

Next, save your changes. You're ready to start the commit! Commits have two phases to help you craft commits properly. Commits should be logical, atomic units of change that represent a specific idea. But, not all humans work that way. You may get carried away and end up solving two or three problems before you remember to commit! That's OK - Git can handle that. Once you're ready to craft your commits, you'll use `git add <FILENAME>` to specify the files that you'd like to "stage" for commit. Without adding any files, the command `git commit` won't work. Git only looks to the staging area to find out what to commit. Staging, or adding, files, is possible through the command line, and also possible with most Git interfaces like GitHub Desktop by selecting the lines or files that you'd like to stage.

<!--Image of staging area, working directory, and history-->

You can also use a handy command, `git add -p`, to walk through the changes and separate them out, even if they're in the same file.

Once you've staged the files that you want to include in your commit, you're ready. Whether you commit in a tool like GitHub Desktop, or through your command line, the commit message is important. Commit messages should be short and descriptive of your change. If you are looking through your repository's history, you'll be guided by the commit messages, so they should tell a story. Commits in the command line can include the message with the following format:

- `git commit -m "commit message here"`

Commit messages should be present tense and directive, like the following examples:

- `git commit -m "create file structure for Git guides"`
- `git commit -m "translate Git cheat sheet into German"`
- `git commit -m "update broken URL to Git resources"`

If you'd like to include more context in your commit messages, you can have an extended commit message.

Commit messages include lots of metadata in addition to the message, like the author, timestamp, and more.

Remember, commits happen on the branch that you're currently checked out to (wherever HEAD is pointing) so it's always a good idea to run `git status` before making a commit, to check that you're checked-out to the branch that you intend to be.

### Push your changes to the remote

So far, if you've made a commit locally, you're the only one that can see it. To let others see your work and begin collaboration, you should "push" your changes using `git push`. If you're pushing from a branch for the first time that you've created locally, you may need to give Git some more information. `git push -u origin [branch-name]` tells Git to push the current branch, and create a branch on the remote that matches it with the same name - and also, create a relationship with that branch, so that `git push` will be enough information in the future.

By default, `git push` only pushes the branch that you're currently checked out to.

Sometimes, if there has been a new commit on the branch on the _remote_, you may be blocked from pushing. Don't worry! Start with a simple `git pull` to incorporate the changes on the remote into your own local branch, resolve any conflicts or finish the merge from the remote into the local branch, and then try the push again.

### Open a pull request

Pushing a branch, or new commits, to a remote repository is enough if a pull request already exists, but if it's the first time you're pushing that branch, you should open a new pull request. A pull request is a comparison of two branches - typically `master`, or the branch that the feature branch was created from, and the feature branch. This way, like branches, pull requests are scoped around a specific function or addition of work, rather than the person making the changes or amount of time the changes will take.

Pull requests are the powerhouse of GitHub. Integrated tests can automatically run on pull requests, giving you immediate feedback on your code. Peers can give detailed code reviews, letting you know if there are changes to make, or if it's ready to go.

Make sure you start your pull requests off with the right information. Put yourself in the shoes of your teammates, or even of your future self. Include information about what this change relates to, what prompted it, what is already done, what is left to do, and any specific asks for help or reviews. Include links to relevant work or conversations. Pull request templates can help make this process easy by automating the starting content of the body of pull requests.

### Collaborate (get feedback from tests or peers, make more commits locally and then push them up and get more feedback)

Once the pull request is open, then the real fun starts. It's important to recognize that pull requests aren't meant to be open when work is _finished_. Pull requests should be open when work is _beginning_! The earlier you open a pull request, the more visibility the entire team has to the work that you're doing. When you're ready for feedback, you can get it by integrating tests or requesting reviews from teammates.

It's very likely that you will want to make more changes to your work. That's great! To do that, make more commits on the same branch. Once the new commits are present on the remote, the pull request will update and show the most recent version of your work.

### Merge into master

Once you and your team decide that the pull request looks good, you can merge it. By merging, you integrate the feature branch into the other branch (most typically the `master` branch). Then, `master` will be updated with your changes, and your pull request will be closed. Don't forget to delete your branch! You won't need it anymore. Remember, branches are lightweight and cheap, and you should create a new one when you need it based on the most recent commit on the `master` branch.

If you choose not to merge the pull request, you can also close pull requests with unmerged changes.

<!--- Potentially include Git workflow illustrations.-->
<!--- “Learning Git” CTA.-->

## How to Use Git

### Learning & Mastering Git Commands

If you're getting started with Git, a great place to start is the [Git Cheat sheet](https://github.github.io/training-kit/). It's translated into many languages, [open source as a part of the `github/training-kit` repository](https://github.com/github/training-kit), and a great starting place for the fundamentals on the command line.

<!--- Very simplified breakdown of the most basic commands with clear navigation to learn more about each one (this might be a good example).-->
Some of the most important and most used commands that you'll find there are:

- `git clone [url]`: Clone (download) a repository that already exists on GitHub, including all of the files, branches, and commits.
- `git status`: Always a good idea, this command shows you what branch you're on, what files are in the working or staging directory, and any other important information.
- `git branch`: This shows the existing branches in your local repository. You can also use `git branch [banch-name]` to create a branch from your current location, or `git branch --all` to see all branches, both the local ones on your machine, and the remote tracking branches stored from the last `git pull` or `git fetch` from the remote.
- `git checkout [branch-name]`: Switches to the specified branch and updates the working directory.
- `git add [file]`: Snapshots the file in preparation for versioning, adding it to the staging area.
- `git commit -m "descriptive message"`: Records file snapshots permanently in version history.
- `git pull`: Updates your current local working branch with all new commits from the corresponding remote branch on GitHub. `git pull` is a combination of `git fetch` and `git merge`.
- `git push`: Uploads all local branch commits to the remote.
  
<!-- Again, potentially include illustrations from individual command pages here or more general learning illustrations. -->

If you're looking for more GitHub specific technical guidance, check out [GitHub's help documentation](https://help.github.com/).

### Getting Started With GitHub

If you're wondering where Git ends and GitHub begins, you're not alone. They are tied closely together to make working with them both a seamless experience. While Git takes care of the underlying version control, GitHub is the collaboration platform built on top of it. GitHub is the place for pull requests, comments, reviews, integrated tests, and so much more. Most developers work locally to develop, and use GitHub for collaboration. That ranges from using GitHub to host the shared remote repository, to working with colleagues and capitalizing on features like protected branches, code review, GitHub Actions, and more.

The best place to practice using Git and GitHub is the [Introduction to GitHub Learning Lab course](https://lab.github.com/githubtraining/introduction-to-github).

If you already know Git and need to sign up for a GitHub account, head over to [github.com](https://github.com/).