# Git Training @ 352 Media

### Before you start the training


* Sign up for an account at [Github](https://github.com/) and send the username to [nrosental@352media.com](mailto:nrosental@352media.com)
* Set up [Git](https://help.github.com/articles/set-up-git)
* Follow the steps on [this page](https://help.github.com/articles/generating-ssh-keys) to generate SSH keys and add them to your account.
* (optional) Install Github app for [Mac](https://mac.github.com/) or [Windows](https://windows.github.com/)
* (optional) go through the [Try Git course](http://try.github.io/levels/1/challenges/1)

### A few words before we start

This training assumes you have a Mac computer. If you don't, it'll still be useful but you'll need to make adjustments.

Most of the training focuses on using Git from the command line, with a repository on Github. We'll also cover some GUI options, but the intention is for you to learn the basics of the CLI.


### Terms

Some of the terms you'll hear (repeatedly) during the training session:

* **Git**: Duh! Git is a versioning system much like SVN. It allows teams (and even solo developers) to work on the same code base in a much more organized manner. The main difference with SVN is that it's decentralized (i.e. every collection of the code is hirerchally equal.)
* **Repo**: The collection of files that make up "the code."
* Branch: A version of your code that you can safely work on without messing up everyone else's work.
* **Master**: The main branch. It can be called anything, but everyone refers to it as _master_ by convention.
* **Origin**: The name usually given to the remote repo (in our case, Github.) Again, this is a widely used convention, but not a requirement.
* **Merge**: Adding the code from one branch onto another.
* **Push**: A Git command that sends your code from your local repo, to a remote repo.
* **Pull**: A Git command that brings the code in a remote repo to your local repo.
* **Commit**: Once you like what you coded, make it stick.
* **Clone**: Make a copy of a remote repo.

There are many more terms, but you'll sure hear this ones a lot.

### Let's Get a Repo

In the future you'll likely create repos for your own projects on Github, but for this training session I've already took care of that.

Open a terminal and issue the following commands

```bash
git clone git@github.com:nicdev/git-training.git
cd git-training 
ls
```

The first command copies the repo from Github into your local machine, the rest is just navigating to the local directory and viewing the files.

[insert screenshot of directory here]

### Branching Out

When you are working on a new feature, you will want to branch out. Once you branch, any change you make to your code won't affect anyone else. Once you like how your code works, you can merge your changes back into the _master_ branch.

Try it out

```bash
git checkout -b name-your-branch
```

`checkout` is the command to switch branches, `-b` indicates to create a new one, and `name-your-branch` is a placeholder; please use your own name.

Holy awesomeness Batman! You just created your own branch. Now you are free to change things around with no consequences whatsoever. I don't think you can say the same about most everything else in your life.

Go ahead. Pick any text editor and make a change to `index.html`. Add a `<div></div>` or some `<h1>Hello World</h1>` or something (don't forget to save the file.)

Now back to the terminal and do

```bash
git checkout master
```

Look at `index.html` again and **OMG!** all your changes are gone. See what I mean by no consequences? Jump back to the terminal and check out your own branch

```bash
git checkout name-your-branch
```

Boom! Your changes are back.

### Don't Be Afraid of Commitment

Now that you did your thing, you'll want to make sure your code sticks.

```bash
git status
git add .
git commit -m "Insert a descriptive message about your code change here. Wit optional."
```

The first command is so that you see what files changes and it's not really needed to commit your code. The second command _adds_ your changes; the `.` is like saying "add it all." The third and last command is the one that actually makes the changes part of the code base.

### Push It!

```bash
git push -u origin name-your-branch
```

This will send your branch up to Github. The `-u` switch isn't strictly necessary, but it tells your repo that the local branch _name-your-branch_ corresponds to the remote branch _name-your-branch_. In the next lesson you'll learn why this is useful.

Browse to the [repo on Github](https://github.com/nicdev/git-training) and look for your branch.

![your branch on ze githubs](http://f.cl.ly/items/2S2D2n2u1I3M1V212C2i/Image%202014-04-15%20at%205.12.57%20PM.png)

### Be Polite, Make a Request

At this point you probably notice that you can push directly to the _master_ branch. DON'T DO IT! The _master_ branch is the one everyone will consider as clean and up to date. Pushing directly to it is not nice. Instead, make a pull request.

Go back to Github, and click on **Pull Requests** or follow this [link](https://github.com/nicdev/git-training/pulls). Then click on the _New Pull Request_ button.

Make sure the "base" says _master_ and the "compare" 








