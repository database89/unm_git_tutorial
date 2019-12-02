# UNM Git Tutorial
A simple tutorial introducing students to Git and GitHub.

Also consider checking out Part [A](https://codeburst.io/git-good-part-a-e0d826286a2a) and [B](https://codeburst.io/git-good-a-practical-introduction-to-git-and-github-in-git-we-trust-f18fa263ec48) of another tutorial.

If you want some short but useful pointers to help reinforce or grow your skills, checkout [GitHub Guides](https://guides.github.com/).

## Topics
### 1. Greate a GitHub account
Begin by creating a GitHub account [here](https://github.com/join?source=header-home). If you can, register with a .edu email address so that you can get the [GitHub Student Developer Pack](https://education.github.com/pack).

### 2. [Set up Git](https://help.github.com/en/github/getting-started-with-github/set-up-git#setting-up-git)
Begin by downloading the latest version of Git for your system, [here](https://git-scm.com/downloads).

Once you're done installing Git, it is important to set your Git username for repositories. This "username" represents a string of characters that will identify you in commits. This string could be "John Doe" or some abbreviation like "johndoe" or "jdoe". Open up your terminal (or Git Bash) and type in the following commands, with your choice of username. My personal preference is to keep the username identical to the GitHub username.
```bash
# Set username
$ git config --global user.name "John Doe"

# Confirm username
$ git config --globa user.name
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


