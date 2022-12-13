# Adding and Committing

```
git status
```

> gives info on the current status of a git repo and its contents

```
git init
```

> create a new git repo

- _before running git init, use git status to verify you are not currently inside a repo_
- _to delete a repo, locate the associated .git directory and delete it_

```
git add file1 file 2
```

> to add specific files to the staging area. separate files with spaces to add multiple files at once

```
git add .
```

> to stage all change at once

```
git commit -m "my message"
```

> the -m flag allows us to pass in an inline commit msg

```
git commit --amend
```

> "redo" the previous commit

---

# Branches and Merging

```
git branch
```

> - view your existing branches
> - default git branch is master/main
> - "\*" indicates the branch you are currently on

```
git branch <branch-name>
```

> make a new branch based upon the current HEAD

- _it does not switch you to that branch (the HEAD stays the same)_

```
git switch <branch-name>
```

> switch to that branch

```
git checkout <branch-name>
```

> switch to that branch

```
git switch -c <branch-name>
```

> create a new branch and switch to it in one go.

```
git branch -v
```

> to view more into about each branch

**Branch Merging:**

```
git switch <receiving-branch>
git merge <branch to be merged>
```

> switch to the branch you want to merge into before using git merge to merge changes from a specific branch into the current branch.

_fast-forward merge:_

- _It will take the commits from the branch being merged and place them at the tip of the branch you're merging into. This creates a linear history, which is also the main advantage of using fast-forward merge._

- _It will create a merge commit at the tip of the branch you're merging into, optionally referencing the branch being merged in the commit message. This has the advantage of keeping track of branches more explicitly than fast-forward merge.GitHub, on the other hand, uses non fast-forward merge by default._

```
git branch -d <branch-name>
```

> deletes the branch

---

# Git Diff

```
git diff
```

> lists all the changes in our working directory that are not staged for the next commit

```
git diff HEAD
```

> lists all changes in the working tree since your last commit both staged and unstaged

**_Git Diff Output_**
| code | explanation |
| --- | --- |
|`diff --git a/style/app.css b/style/app.css`|which files are being compared. Git also declares one file as "A" and the other as "B"|
|`index 72b1nh17..h5js99h 110655`|the first two numbers are the hashes of the two files being compared|
|`--- a/style/app.css`|file A gets a minus sign|
|`+++ b/style/app.css`|file B gets a plus sign|
|`@@ -22,6 +22,10 @@ h1{`|chunk header found between @@ and @@. from file A, 6 lines are extracted starting from line 22|
|`margin-top: 50px;`||
|`position: relative;`||
|`padding: 15px;`||
|<r>- font-size: 60px;</r>|lines that begin with - come from file A|
|<r>- font-weight: bold;}</r>|red stands for removed|
|<g>+ cursor: default;<g>|lines that begin with + come from file B|
|<g>+ -webkit-touch-callout: none;</g>|green stands for added|
|<g>+ -webkit-user-select: none;</g>||
|<g>-moz-user-select: none;</g>||
|`background: #bbada0;`||
|`border-radius: 6px;`||
|`width: 500px`||

---

```
git diff -staged
git diff -cached
```

> "show me what will be included in my commit if I run git commit right now"

```
git diff HEAD <filename>
git diff --staged <filename>
```

> to view changes within a specific file

```
git diff branch1 ..branch2
```

> list changes between tips of branch1 and branch2

```
git diff commit1hash ..commit2hash
```

> list the changes between the two commits

---

# Stash

```
git stash
```

> take all the uncommitted changes (staged and unstaged) and stash them, reverting the changes in your working copy.

```
git stash pop
```

> remove the most recent stashed changes in your stash and re-apply them to your working copy

```
git stash apply
```

> apply whatever is stashed away, without removing it from the stash. This can be useful if you want to apply stashed changes to multiple branches.

```
git stash -u
```

> tell git stash to include untracked files (files that you have never checked in to Git)

```
git stash list
```

> to view all stashes

```
git stash apply stash@{2}
```

> applying specific stashes.

```
git stash drop stash@{2}
```

> to delete a particular stash

```
git stash clear
```

> to clear out all stashes.

---

# Checkout, Restore, Reset and Revert

```
git checkout <commit-hash>
```

> - to view a previous commit in detached `HEAD` state.
> - use git log to view commit hashes and use the first 7 digits of a commit hash.

```
git checkout HEAD~1
```

> - `HEAD~1` refers to the commit before HEAD
> - `HEAD~2` refers to 2 commits before HEAD

```
git checkout HEAD <filename>
git checkout -- <filename>
```

> to discard any changes to that file, reverting back to the HEAD(when you last committed)

```
git restore <file-name>
```

> to restore the file to the contents in the `HEAD` (your last commit)

```
git restore --source HEAD~1 <file-name>

git restore --source <commit-hash> <file-name>
```

> instead of using HEAD as the restore point to restore to, you can use `HEAD~5` or even a commit hash.

```
git restore --staged <file-name>
```

> unstage a file from the next commit

```
git reset <commit-hash>
```

> reset the repo back to a specific commit. the commits are gone but the changes in the local directory are still intact.

```
git reset --hard <commit>
```

> - undo both the commit and the actual changes in your file.
> - git reset moves the branch pointer backwards, eliminating commits that could be a problem during reconciliation if others have history of those commits of yours.

```
git revert <commit-hash>
```

> creates a brand new commit which reverses the changes from a commit. Since this results in a new commit, you will be prompted to enter a commit message.

```
git checkout origin/master
```

> - switching to remote repo using remote named origin into a remote branch named master
> - you are in 'detached HEAD' state. You can look around, make experimental changes and commit them, and you can discard any commits you make in this.

---

# Remote branches, push

_**Remote**_

> is a URL where a hosted repository lives.

```
git remote -v
```

> displays a list of remotes.

```
git remote add <name> <url>
```

> adding a new remote

_When we clone a git repo the default remote name setup for us is called origin_

_Anytime you use `<name>` you are instructing Git that it refers to this particular Github repo `<url>`_

```
git remote rename <old> <new>
git remote remove <name>
```

```
git push <remote> <local-branch-to-push>
```

> local branch and remote branch are same branch names

```
git push <remote-name> <local-branch>:<remote-branch>
```

> - local branch and remote branch are different branches
> - example: `git push origin features:updates`

```
git push -u <remote> <branch>
```

> Sets up the upstream for the local branch so that we can push with just "git push" command instead of "git push origin main".

_**Steps to set up a local repo on Git and remote repo on GitHub and connecting them:**_

> - Create a new empty repo on GitHub
> - Copy the repo URL
> - Add a remote to your local repo, using the URL
> - push your changes up the remote

<img src="https://github.com/about-arun/learning/blob/git-github/images/working-of-git.png" width="500" >

```
git branch -r
```

> view the remote branches our local repository knows about.

_**Cloning Git Repo**_

> - On initial cloning of a remote branch into the local Git, only the main branch appears on our workspace (check using `"git branch"` command). By default, `main` branch is already tracking `origin/main` but the other branches are not being tracked.
> - The local repo knows about all the other remote branches in the remote repo.(check using `git branch -r` command)
> - `git switch <remote-branch-name>` will make a local branch and set it up to track the remote branch with the same name. same can be achieved using the old `git checkout --track <remote/branch>`.

```
git fetch <remote>
```

> - Fetches branches and history from a remote repo.
> - It only updates remote tracking branches.
> - If not specified `<remote> ` defaults to `origin`
> - Fetch downloads changes from a remote repo but those changes will not be automatically integrated into our working files.
> - From there one can use `git checkout <remote/branch-name>` to check out the branch in detached `HEAD` state.

```
git fetch <remote> <branch>
```

> Fetch specific branch from a remote.

```
git pull <remote> <branch>
```

> - Git pull = git fetch + git merge
> - It matters where we run this command from. Whatever branch we run it from is where the changes will be merged into.

```
git pull
```

> - `Remote` will default to origin
> - `Branch` will default to whatever tracking connection is configured in the current local branch you are at.

_git pull can result in merge conflicts. Not recommended if you have uncommitted changes_

---

# Workflows for Collaboration

_**Feature Branches**_

> - Rather than working directly on master/main, all new development should be done on separate branches.
> - Treat master/main as the official project history
> - Multiple teammates can collaborate on a single feature and share code back and forth without polluting the main branch.
> - Master/main branch wont contain broken code

_**Pull Requests**_

> - Feature build into Github and not native to Git.
> - Allow devs to alert team-members to new work that needs to be reviewed
> - Provide a mechanism to approve or reject the work on a given branch
> - They also facilitate discussion and feedback on the specific commits.

_**Pull Request Merging**_

> - From your local repo, bring in the changes from remote repo and test.
>   - **_Step1:_** `git fetch origin` : Updates local repo to match remote repo. But the workspace won't be updated with latest files yet.
>   - **_Step2:_** `git switch new-feature` : Switch to the new-feature and bring it into the workspace for testing.
>   - **_Step3:_** `git merge main` : Merge the main branch into the new-feature branch. Resolve conflicts.
> - Merge the changes and update on Github
>   - **_Step4:_** `git switch main` : Switch into the main local branch.
>   - **_Step5:_** `git merge --no-ff new-feature` : Merge the tested+merged new-feature branch into the local main deliberately avoiding ff-merge to add commit message.
>   - **_Step6:_** `git push origin main` : Push the merged and tested local main into remote main.

_**Feature Branch PR Workflow:**_

> - Work locally on feature branch
> - Push up the feature branch to Github
> - Open a pull request using feature branch.
> - Wait for the PR to be approved and merged.

_**Fork & Clone workflow:**_

> - Fork the original project repo on Github
> - Clone the fork to my local machine
> - Add a remote pointing to the original project repo. Often named "upstream"
> - Make changes and add/commit on a feature branch on the local machine.
> - Push up the new feature branch to the forked repo. Usually called "origin".
> - Open a pull request to the original project repo containing the new work on my forked repo.
> - Hopefully the pull request is accepted and changes are merged in.

---

# Rebasing

```
git switch <feature-branch>
git rebase main
```

> - Moves the entire feature branch so that it begins at the tip of the master branch.
> - Instead of using merge commit, rebasing rewrites history by creating new commits for each of the original feature branch commits.

_NEVER rebase commits that have been shared with others_

```
git rebase -I HEAD~4
```

> - Interactive rebase -i option allows us to edit commits, add files, drop commits, etc.
> - Also specify how far back we want to rewrite commits
> - We are not rebasing onto another branch, instead we are rebasing a series of commits onto the HEAD they are currently based on.
> - Common commands to alter commits:
>   - _pick_ - use the commit.
>   - _reward_ - use the commit but edit the commit message.
>   - _edit_ - use commit, but stop for amending.
>   - _fixup_ - use commit contents but meld it into the next commit and discard the commit msg.
>   - _drop_ - remove commit and updates the workspace accordingly.

---

# Git tags

_**Lightweight tags**_

- Name/label that points to a particular commit.
- `git tag <tag-name>`
- Tagging a commit that `HEAD` references.

_**Annotated tags**_

- Store extra meta data including author's name and email, the date and a tagging msg.
- `git tag -a <tag-name>`
- Tagging a commit that `HEAD references.`

_**Semantic Versioning**_

- 2.4.1
  - 2 - Major release
  - 4 - minor release
  - 1 - patch release

```
git tag
```

> Will print the list of all tags in the current repo.

```
git tag -l
```

> View the state of a repo at a particular tag in detached HEAD state.

```
git tag <tag-name> <commit>
```

> Tagging older commits.

```
git tag -f <tag-name>
```

> Force to reuse a tag that is already referring to a commit.

```
git tag -d <tag-name>
```

> Deleting a tag

```
git push --tags
```

> By default git push command doesn’t transfer tags to remote servers.

---

# Reflogs

_Git keeps a record of when the tips of branches and other references were updated in the repo_

_Git only keeps reflogs on your local activity_

_Reflogs expire. Git cleans out old entries after around 90 days_

```
git reflog
```

> (defaults to HEAD reference)

```
git reflog show main
```

> To view the logs for the top of the main branch

_**Reflog references**_

- Access specific git refs using `name@{qualifier}`. Example: `git reflog show HEAD@{2}`
- Timed references:
  - `git reflog master@{one.week.ago}`
  - `git checkout bugfix@{2.days.ago}`
    - `git diff main@{1} main@{yesterday}`

_**Reflog for the Rescue**_

> Use reflog entries to access commit hashes that seem lost and are not appearing in git log.

---
