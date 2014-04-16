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

Make sure the "base" field says _master_ and the "compare" field is _name-your-branch_

![a pull request](http://f.cl.ly/items/0Y1I383n1J4447130b36/Image%202014-04-15%20at%205.41.02%20PM.png)

There's a lot going on here. Take a minute to explore. You'll see the number of commits you're merging, how many files have changed, a diff of files that have changes and a bunch more.

Once you are satisfied with what you see, click on the **Create Pull Request** button.

If everything is well with the world, you'll see the green "Able to merge" message. 

![able to merge](http://f.cl.ly/items/3m37300o3L3C3t371i2X/Image%202014-04-15%20at%205.48.36%20PM.png)


Go ahead and click on "Send pull request." But you're not done quite yet. At this point, the code needs to be merged (accepted) into the _master_ branch. At this point you can click on the "Merge pull request" button.

![merge PR](http://f.cl.ly/items/2H2X173F2c0o011Q1h1e/Image%202014-04-15%20at%205.57.21%20PM.png)

If there are conflicts, you'll see this instead (I'll show you how to fix that later)

![unable to merge](http://f.cl.ly/items/2w2Q302V0b3x3f3c0u25/Image%202014-04-15%20at%206.04.23%20PM.png)

This may seem like a lot of effort for getting the code merged, but it helps keep conflicts at bay and once you get used to it, it's actually very quick.

### Doing it Right

In the previous step we just sent in the pull request and hoped for the best. The right way to go about it would be to make sure you don't have any conflicts before sending the request. 

Jump back on the terminal, then make some more changes to any of the files, create new files. Go nuts! Once you are done, go through the add/commit process.

```bash
git add .
git commit -m "Informative message here"
```

Now, before you push it up, make sure your code can merge properly with _master_.

```bash
git pull origin master
```

What you are doing here is bringing in the code from the remote _master_ branch into your own.

If something fails to automatically merge, you will be notified

![oops!](http://f.cl.ly/items/2C0U0i2x1i3c0E212I0S/Image%202014-04-15%20at%206.54.22%20PM.png)

This can be frustrating, but Git makes it very clear where to find the conflicts. In this case, the same part of `index.html` was changed so Git isn't sure which one to use. The conflicted file looks like this

![conflicted code](http://f.cl.ly/items/0h0U381L0x2A431q2A08/Image%202014-04-15%20at%206.58.23%20PM.png)

The code immediately following `HEAD` is our local code, the code between `========` and `657510f14da0d146da3e00299d59be9a7a5c24ac` is what we pulled from `master`

`HEAD` refers to your working state, `657510f14da0d146da3e00299d59be9a7a5c24ac` is a unique identifier for the commit you tried to merge in. 

To fix this, we can manually edit the code, or use a diff tool. In this case, I'm just going to fix it up manually. The code now looks like this:

![nailed it](http://f.cl.ly/items/1T0X141q3m2R361U3Y1l/Image%202014-04-15%20at%207.04.59%20PM.png)

Go through the add/commit motions

```bash
git add .
git commit -m "all fixed up"
```

Now when I pull from the remote `master` Git already knows which way it should merge.

```bash
git pull origin master
git push origin name-your-branch
```

When you do the pull request you know it will get an all green because you've already merged the latest from `master`

![all good in the hood](http://f.cl.ly/items/3n1m1Z0q1w1R3K2l1D3z/Image%202014-04-15%20at%207.31.01%20PM.png)

### Sum It Up

We just covered the basics that will get you up and running with Git. Let's do a recap.

* Branch out and work on your code
* Pull the latest from _master_ (or the main branch you're working against.)
* Push your own branch up to Github
* Submit a pull request
* Accept the pull request

### Part Deux - Ze GUI

Let's look at [Github for Mac](https://mac.github.com/).

After it's installed, you will see all the organizations you are part of, a list of available remote repos, and a shortcut to the local repos you've added to the app.

![github app](http://f.cl.ly/items/3z2Q0k1c3z1R100B0G0b/Image%202014-04-15%20at%207.46.07%20PM.png)

Add the local repo we've been working on

![add a repo](http://f.cl.ly/items/3k3E3l141n2h2X2m1S1o/Image%202014-04-15%20at%207.48.32%20PM.png)

### Creating a New Branch

![new branch](http://f.cl.ly/items/0k302p0B1f1z1t1d2C0P/Image%202014-04-15%20at%207.57.21%20PM.png)

Clicking **publish** is the equivalent of pushing the branch to the remote repo.

![push it](http://f.cl.ly/items/1y443S2G333g3C1A2b0X/Image%202014-04-15%20at%207.58.56%20PM.png)

Now that it's been published (pushed) let's make some code changes. Once you are done changing the code, hop back on the app and look at the "Changes" section.
















