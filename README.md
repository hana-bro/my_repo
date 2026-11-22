# my_repo
# About me

My repo about GitHub.

My name is Hanna Brodziak, I am a third-year bioinformatics student at JU.

I created this repo at November 22nd 2026.

Sources:
1. https://github.com/ylla-lab/BT4BR_2026
2. excersises on November 19th 2026

---

# Git summary

## Git commands

To clone repository into local folder, you first need to create a public ssh key:

**ssh-keygen -t ed25519 -C "your-email@example.com"**

Then paste the content of it into your GitHub account in keys section.

Now you can clone your repo by copying ssh link from your GitHub repo and using this command:

**git clone ssh_link**

Then you can start adding files into your GitHub project:

**git add file_name**

But to actually see it on your repo you need to commit it:

**git commit -m "message about this commit"**
- *-m* flag allows to write comments/info/message about what you changed/did in committed file

If you want to change your comment you can do it but only ONCE:

**git commit --amend -m "new comment"**

Before committing you can see the what files "are waiting" to be committed:

**git status**

After committing, you can finally push it into GitHub:

**git push origin main** 
- or just **git push** if you are on the main branch already

You can also check the differences between new and last commited version:

**git diff**

### Branches

It is safe to create another branch apart from main to freely work there and keeping main branch unchanged and handle merging conflicts:

1. **git branch new_branch_name**
2. changing to newly created branch: **git checkout new_branch**
- *checkout* also checks if you are up to date with changes on said branch
- you can use *switch* instead of *checkout*, it just changes branches

Then you work as usual, the difference would be with pushing:

**git push origin new_branch_name"**
- you need to specify the name of the branch, otherwise weird things happen
 - you don't need to specify the name of the branch if you are on the main branch

If you have couple of branches and you want to merge them:

1. first go to one branch: **git checkout branch_1**
2. then merge: **git merge branch_2**
3. you can get a merging conflict, to see its details: **git log --merge**
- it happens when Git doesn't know which version is correct and puts them in the same file - you can edit it, delete what you don't want and then commit as usual and push to branch that you are on

You can merge branches with main branch if you are satisfied with this branch content and want to make it main content from now on.

## Restoring

All the commits can be seen:

**git log --oneline**

You need to find the ID of the commit you want to go back to and then:

**git checkout ID**

But now we are in the "detached HEAD" state and nothing we do here will actually change on the main branch.
Some weird things happen here when you try to commit and push.
We need to create a separate branch for this commit to work on it and then use it:

**git switch -c commit_branch**

Now you can work, commit and push as usual on this branch.

You can compare this branch with main (or other branch):

**git switch main**

**git diff main..commit_branch**

To make our recovered version the main version make sure you are on the main branch and you don't have any uncommitted changes (**git status**), then:

**git restore --source=commit_branch --staged --worktree**
- you can add **:/** at the end of the command to apply changes int the whole repo
- you can add **-- name_of_file** at the end of the command if you only want to restore a single file
- **--worktree** updates our local repo

Then you can commit the restored version.

## Working on different devices

If you made some local changes on one device and pushed it into GitHub, you should pull them into your other device, because your local copy there would not be updated:

**git config --global pull.ff only**

**git pull**

You can also fetch repo from GitHub without affecting your local copy:

**git fetch**


# REMEMBER

1. Forking is creating a copy of a repo on your local device, but no changes from it will be applied on the original project.
2. If you are working as a team on a project, work on different branches - you can then merge them together and avoid the mess on the main or other branch by making many different commits of the same files.
