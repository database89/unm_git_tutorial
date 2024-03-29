# A Tutorial on Forking, Branching, and Pull-Requesting


## 1. Fork This [Repository](https://github.com/database89/unm_git_tutorial)
Begin by forking [unm_git_tutorial](https://github.com/database89/unm_git_tutorial) repository in GitHub.

![Creating a Fork in GitHub](https://github.com/database89/unm_git_tutorial/blob/master/Tutorial/github_fork.png)

Next, clone your fork locally and replace `<username>` with your GitHub username. 
To get the HTTPS or SSH URL for your fork, simply select the green *Clone or Download* and copy the appropriate URL.
By default, Git aliases this forked repository with the keyword `origin`.

```bash
$ git clone git@github.com:<username>/unm_git_tutorial.git
```

Now, you can make changes to the forked repository by making changes locally and pushing them.
However, with how things are currently set up, if the original 
[unm_git_tutorial](https://github.com/database89/unm_git_tutorial) repository changes, then we have no way of updating our fork.
Ultimately, the goal of this exercise is to make changes to the original 
[unm_git_tutorial](https://github.com/database89/unm_git_tutorial) repository by way of a pull-request, while keeping the fork 
up-to-date. This issue can be resolved by adding a separate alias called `upstream` that refers Git to the original 
[unm_git_tutorial](https://github.com/database89/unm_git_tutorial) repository.

```bash
$ git remote add upstream git@github.com:database89/unm_git_tutorial.git
```

Just to keep everything in order, we check our remote URLs and see the code snippet that follows, 
where `<username>` is your GitHub username. Notice that `origin` is a reference to the forked repository, 
whereas `upstream` is a reference to the repository from which the fork was generated.

```sh
$ git remote -v

origin  git@github.com:<username>/unm_git_tutorial.git (fetch)
origin  git@github.com:<username>/unm_git_tutorial.git (push)
upstream  git@github.com:database89/unm_git_tutorial.git (fetch)
upstream  git@github.com:database89/unm_git_tutorial.git (push)
```

Now, your local repository has two unique remote URLs as indicated by `origin` and `upstream`.
This means that we must be explicit when pulling, pushing, merging, or fetching commits (e.g. `git pull` and `git push`
will not suffice). 
Recall that if our local repository has only one remote and we want to be explicit when pulling commits, we use the command
`git pull origin master` assuming `origin` is the remote repository URL and `master` doubles has the branchname in both 
our local and remote repositories.

When the local repository has two ore more unique remote URLs, we need to be explicit about the branch in the remote 
repository from/to we want to pull/push to/from the specified local branch. 
In an attempt to be explicit, we do not use the `pull` command, and instead utlize the combination of a `fetch` and `merge`. 
When fetching commits we can fetch commits from all remotes using `git fetch --all`, we can fetch commits from a specific remote by
`git fetch <remote_alias>`, or we can fetch commits explicitly in a specific branch in the remote by `git fetch <remote_alias>/<branchname>`.
When trying to merge commits, the command has the form `git merge <remote_alias>/<branchname> <local_branchname>` because in some cases it is possible for the local and remote branches to have different names. 
For example, your local branch might be a feature branch `myFeatureBranch` off `master` and you want `myFeatureBranch` to be in sync with `master`. In summary, the code snippet below shows how to explicity keep the local `master` branch in sync with `upstream/master` (where `upstream` refers to the remote URL of the repository, and 
`master` is the branchname).

```bash
## Keep local repo in sync with upstream
## git fetch <remote>
## git merge <remote>/<branch> <local_branch>
$ git fetch upstream                      # fetch all commits from all branches in upstream
$ git merge upstream/master master        # merge upstream/master with local master
```

The code snippet below shows a sample workflow:
```bash
## We just created a fork, so let's clone the forked repository.
## git clone git@github.com:<username>/<repo_name>.git
$ git clone git@github.com:<username>/unm_git_tutorial.git

## Add the upstream repository we want to be in sync with.
## git remote add upstream git@github.com:<upstream_username>/<repo_name>.git
$ git remote add upstream git@github.com:database89/unm_git_tutorial.git

## Make changes locally in a new feature branch and eventually promote the changes to the forked repository
$ git checkout master                 # checkout the master branch
$ git checkout -b myFeatureBranch     # create a new branch off of the master branch, and check it out
## Make changes to files until it's time to commit
$ git status
$ git add <file1> <file2> ... <fileN>
$ git commit -m "This is a meaningful commit message."
## If the new branch DOES NOT exist in the forked repo (you only do this once):
## git push -u <remote> <branchname>
## e.g. git push -u origin myFeatureBranch
## If the feature branch already exists:
$ git push origin myFeatureBranch

## At some point in the future, the original repository is updated.
## We want to sync those changes with our local repository and update the fork.
$ git fetch upstream                # fetch all commits from all branches in upstrea
$ git merge upstream/master master  # update the local master branch with upstream/master

## Getting ready to merge changes from the feature branch into the master branch
$ git checkout myFeatureBranch      # we were on master, so checkout myFeatureBranch
$ git merge master                  # merge the new commits from master (local) into myFeatureBranch (local)
## If there are merge-conflicts, resolve them. If not, then update the fork.
$ git checkout master               # were on myFeatureBranch, so checkout master
$ git merge myFeatureBranch         # since myFeatureBranch seems good, merge its commits into master
$ git push origin master            # only push the changes from the master branch to the fork

## Now, prepare a pull-request in GitHub to request that the changes from the fork get pulled into the
## the original repository.
```

## 2. Make Some Changes
Once you have cloned your fork locally, create a new branch that tracks `master` called `<username>`.
You will make your changes in this branch.

Navigate to `.../unm_git_tutorial/Tutorial/` and create a new file called 
`<username>.md`. You may do this using a GUI or text-editor that is readily available with your OS, or directly with
UNIX commands.

```bash
$ cd <some_path_specific_to_you>/unm_git_tutorial/Tutorial    # set the specified path to be the 'current directory'
$ touch <username>.md                                         # make an empty file called <username>.md
```

Open up the file and add some text. You might write something like "<Username> is editing <username>.md". 
When you're done, save the file. Then, commit your change(s) and push them to the fork.
```bash
$ git status
$ git add <username>.md
$ git commit -m "Created username.md file"
$ git push -u origin <username>
```

Now, go to your GitHub account and verify that the `<username>` branch was pushed to your fork.

## 3. Pull-Request
To verify that your branch was added to your fork you should see something like in the image below, except with your
branch's name. When you are ready to move forward with your pull-request, select the green **Pull-Request** button.
![Creating a Pull-Request 1](https://github.com/database89/unm_git_tutorial/blob/master/Tutorial/pull_request_1.png)


The image below is an example of what the next screen looks like. This is where you configure you pull-request.


![Creating a Pull-Request 2](https://github.com/database89/unm_git_tutorial/blob/master/Tutorial/pull_request_2.png)
1. Going from left to right you see the `dest_remote/dest_repo` and `dest_branch` <-- `source_remote/source_repo` and `source_branch`.
**Always check and confirm that this is correct.**
2. If everything looks correct and you're sure you want to go through with the pull-request, select this button.
**NOTE: Even if you go through with the pull-request you can still cancel it later.**
3. You can view all of the commits that are part of your pull-request here. You can view all of the changed files, and all of the line-by-line
changes.

When you are ready, submit the pull-request (you will be directed to a new screen). Wait for your pull-request to either be accepted or rejected.

Once your pull-request is accepted your feature is complete. To keep things from getting chaotic and messy, you may choose to delete your feature branch in your local repository.

```bash
$ git checkout master                   # checkout the master branch; you be on the branch you are deleting
$ git branch -d <username>              # delete your feature branch
$ git branch                            # view the list of branches that remain in your local repository
> * master
```
If you want to delete the branch from your fork on GitHub, you will need to use the GitHub interface. Select **Branches** in the menu at the top, and then select **All Branches**. To delete a branch, simply select the trash-can icon to the very right. 
**NOTE:** Deleting a branch in GitHub **does not** delete the branch from your local Git repository.

## 4. Update Your Fork
At some point your forked repository will become out-of-sync with the original repository (in most cases it will fall behind).
If you are actively working on code changes, it is important for your fork to be up-to-date. This means that you will need to
pull changes from the original repository and push them to your fork.

```bash
$ git checkout master                   # checkout the master branch so that it may be updated
$ git fetch upstream                    # fetch all commits from all branches in upstream
$ git merge upstream/master master      # merge changes from upstream/master into your local master branch

# If merge-conflicts resulted from the previous step, then resolve them. If not, move on.
# Update the fork (origin) with the latest changes from upstream
$ git push origin master
```

Now, you are well equipped to collaborate with others by forking projects!
