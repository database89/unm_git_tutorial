# UNM Git Tutorial
A simple tutorial introducing students to Git and GitHub. This tutorial is sufficient to get you started with Git and GitHub, while
providing you the tools to be productive. Certain advanced concepts that involve changing Git's history are deliberately not covered in this tutorial. This tutorial is divide into two parts -- (1) a lecture based graph-theoretic understanding of Git and GitHub, and (2) hands-on exercises where you directly interact with Git and GitHub.

It is no coincidence that this Git tutorial is made available on GitHub! The intention here is for you to be able to have access to this repository and access or reference the materials as and when you please.

This tutorial is meant to serve as a thorough introduction to Git. Practice is the key to reaching expert-level! You may find yourself needing to  review the materials, learning Bash, or you may end up searching online for advanced techniques. Make Git work for you!

### Part 1: Lecture and Theory
While many students prefer examples and applications, the theory behind Git and GitHub is crucial to understanding the power of Git, the numerous things you can do with Git, and how you can think through tough scenarios. If you can understand the graph-theoretic notions that make up the backbone of Git, then you're all set to start using it. There is more power in understanding Git than simply knowing different sequences of commands. (Knowing the sequence of steps to start a car simply isn't adequate when your car doesn't start. It is also important to recognize symptoms so that you may identify the underlying problem.)

The lecture portion covers most Git basics, provides context-based visuals and examples, and introduces commands.

You can view the presentation slides [here](https://database89.github.io/unm_git_tutorial/Presentation/Introduction%20to%20Git%20for%20Version%20Control.pdf).

### Part 2: Exercises with Git and GitHub
The number of exercises and examples that we can get through is limited by the length of the class period. The goal is to go through two semi-involved examples/exercises. 

The [first exercise](https://github.com/database89/unm_git_tutorial/blob/master/Tutorial/Tutorial_Instructions.md) involves forking this repository, making some changes, updating the fork, generating a pull-request, and eventually updating your fork again. The purpose of this exercise is to use Git and GitHub simultaneously while learning about the collaborative power of GitHub as it pertains to deploying large scale projects, packages, and code-bases. This is a common use case for professionals.

The second exercise is much more general and open-ended. It involves creating a repository, making changes to files, promoting changes to the remote, branching, etc. This is the most common use case for students.

### Resources Worth Looking At
Also consider checking out [Part A](https://codeburst.io/git-good-part-a-e0d826286a2a) and [Part B](https://codeburst.io/git-good-a-practical-introduction-to-git-and-github-in-git-we-trust-f18fa263ec48) of another Git tutorial.

If you want some short but useful pointers to help reinforce or grow your skills, checkout [GitHub Guides](https://guides.github.com/).

If you need help with using markdown, try this [markdown cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet).

Some [simple Bash commands](https://hackernoon.com/top-10-bash-file-system-commands-you-cant-live-without-4cd937bd7df1).
Some [advanced Bash commands](https://dev.to/awwsmm/101-bash-commands-and-tips-for-beginners-to-experts-30je).

---

## Selected Topics for Getting Started
### 1. Greate a GitHub account
Begin by creating a GitHub account [here](https://github.com/join?source=header-home). If you can, register with a .edu email address so that you can get the [GitHub Student Developer Pack](https://education.github.com/pack).

### 2. [Set up Git](https://help.github.com/en/github/getting-started-with-github/set-up-git#setting-up-git)
Begin by downloading the latest version of Git for your system, [here](https://git-scm.com/downloads).

Once you're done installing Git, it is important to set your Git username for repositories. This "username" represents a string of characters that will identify you in commits. This string could be "John Doe" or some abbreviation like "johndoe" or "jdoe". Open up your terminal (or Git Bash) and type in the following commands, with your choice of username. **My personal preference is to keep the username identical to the GitHub username.**
```bash
# Set username
$ git config --global user.name "John Doe"

# Confirm username
$ git config --global user.name
> John Doe
```

You will want to setup the email address you want associated with your commits as well.
```bash
# Set email
$ git config --global user.email "email@example.com"

# Confirm email
$ git config --global user.email 
> email@example.com
```

Once you have set up your GitHub account you will need to authenticate GitHub from Git. When you connect to a GitHub repository from Git, you will need to authenticate with GitHub using either HTTPS or SSH. If you authenticate with HTTPS, you will be required to type in your password anytime Git connects to GitHub. If you authenticate with SSH, you must generate SSH keys on every computer you will use to access GitHub.
```bash
# Generate SSH Keys (follow the prompts... you can just hit Enter)
$ cd ~
$ ssh-keygen
```
Next, GitHub needs to be made aware of your computer's public key. You can access your computer's public key with the command shown below.
```bash
$ cat ~/.ssh/id_rsa.pub
```
Copy the output of the command (this is your public key). Now, you need to tell GitHub to authenticate using your public key. To do this, go to your GitHub account and follow [these instructions](https://help.github.com/en/github/authenticating-to-github/adding-a-new-ssh-key-to-your-github-account).

### 3. [Creating/Cloning a new repository](https://help.github.com/en/github/getting-started-with-github/create-a-repo)
Once you have a repository you want to clone, get the path of the repository and execute the following command. Do note that the repository path in the command represents [this](https://github.com/database89/unm_git_tutorial/) repository.

`git clone git@github.com:database89/unm_git_tutorial.git`

Once you have cloned the repository, be sure to checkout the correct branch. Executing `git branch -a` will show you all available branches. Once you have identified the branch of interest, run `git checkout <branch_name>` to select that particular branch.
### 4. Changing files and committing code


