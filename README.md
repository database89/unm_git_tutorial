# UNM Git Tutorial
A simple tutorial introducing students to Git and GitHub.

Also consider checking out Part [A](https://codeburst.io/git-good-part-a-e0d826286a2a) and [B](https://codeburst.io/git-good-a-practical-introduction-to-git-and-github-in-git-we-trust-f18fa263ec48) of another tutorial.

If you want some short but useful pointers to help reinforce or grow your skills, checkout [GitHub Guides](https://guides.github.com/).

## Topics
### 1. [Set up Git](https://help.github.com/en/github/getting-started-with-github/set-up-git#setting-up-git)

### 2. Setting up a GitHub account
Begin by creating a GitHub account [here](https://github.com/join?source=header-home). If you can, register with a .edu email address so that you can get the [GitHub Student Developer Pack](https://education.github.com/pack).

### 3. [Creating/Cloning a new repository](https://help.github.com/en/github/getting-started-with-github/create-a-repo)
Once you have a repository you want to clone, get the path of the repository and execute the following command. Do note that the repository path in the command represents [this](https://github.com/database89/unm_git_tutorial/) repository.

`git clone git@github.com:database89/unm_git_tutorial.git`

Once you have cloned the repository, be sure to checkout the correct branch. Executing `git branch -a` will show you all available branches. Once you have identified the branch of interest, run `git checkout <branch_name>` to select that particular branch.
### 4. Changing files and committing code


