## Danil trying to ruin the readme
# Git Workshop

## Create a repository from GitHub and editing it online

GitHub has an introductory [exercise](https://docs.github.com/en/get-started/start-your-journey/hello-world), try it out

## Create a repository locally first

Since Git is a distributed VCS, you can create a repository locally, and work there before ever deciding to publish on GitHub.
Follow the instructions [here](local-repo.md) to try that out.

## Play with local branches

Have a look at the workshop slides about branches, merging and rebasing.

In a local repo, create multiple diverging branches, then try merging, cherry-picking and rebasing them onto each other.

## Stashing

- Create two branches in your repository
- Start changing the files with one of the branches checked out
- Before staging or commiting, you decide that you meant for these changes to actually go on the other branch

Using commits, cherry-picking and hard reset, you could put these changes into a commit only on this other branch.
This would look like (don't bother doing this, or do if you want...):
- commit these changes on the current branch (1) (`git commit -am "message"`)
- checkout the other branch (2) (`git checkout branch2`)
- cherry-pick that commit onto branch (2) (`git cherry-pick branch1` or `git cherry-pick branch1^..branch1`?)
- checkout back to branch 1 (`git checkout branch1`)
- hard reset to the penultimate commit (`git reset --hard HEAD^`)

However, you don't have to commit onto the first branch just to remove it later, instead Git has a "stashing" feature to storing changes aside without commiting.
Using that instead would look like:
- `git stash`
- `git checkout branch2`
- `git stash pop`
- `git commit -am "message"`

## Force pushing

Recall that some Git operations change the order of history (such as `git reset --hard HEAD^` to pretend the last commit did not happen). The default branch on a GitHub repo will be "protected" and disallow you from pushing a branch does not only add extra commits (i.e. does not "change history" and annoy other people using that branch).

However you are still in charge, and not the machine, so it's good to make sure to assert your dominance on it every so often and do what **you** want.
Either do this on a non-default (non-protected) branch, or remove the protection from the main branch (browse settings on GitHub).
Then you can force push: ``git push -f``.

## Create a pull request

Create a pull request to this repository. Find GitHub's [instructions](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request) for this.

Make sure that the pull request is well formatted and is very convincing to me as to why *I* should bother using your contribution and what problem it solves.
For this workshop, adding puns may constitute a valid reason, however project maintainers in the wild may need genuine good reasons from you (make sure to look at the project's `CONTRIBUTING.md` file first).

## Resolve a merge conflict

Do the previous task (create a pull request), but after forking, wait for somebody else to submit a pull request, have it accepted, and then make a change that intersects theirs.

Next merge the new changes into your fork and resolve the conflict.

## Rebase your fork (possibly more involved, skip if not in mood)

Repeat the previous task, but this time only do the Git operations on your PC and rebase your changes onto the updates to this repo, instead of merging.
*Depending on how you do this, it could involve removing protection of a branch on GitHub, and some **force** pushing*.

## Explore your editors Git integration

Especially if using VSCode, try to see if you can do/see the following things in your IDE (possibly after installing an extension/plugin):

- See "hunks" (i.e. changes, additions, deletions since the last commit)
- Git blame info (see which lines come from which commit, and hence the author)
- Git Log (view of past revisions, possibly in a tree view)
  - Revert a commit (create a new commit undoing the changes from a certain other commit)
  - Hard reset to a commit (rewind time to a certain commit)
 
##  Squashing commits

Did you know that GitHub has a limit to the size of files it can receive in a commit?
Google what that size is and commit file to your repository that is larger than this.
Git itself does not have this limitation, it's artificial from GitHub (for obvious reasons).
Try pushing this commit to GitHub and see it fail. Panicking, you decide to revert this last commit (`git revert HEAD`).
Try pushing again. Failing again? Even if the current version does not contain the large file, it is still in the last commit which GitHub would have to store if it accepted your push.

One way to get around this is to squash the commits in a way to skip over the part in history where that large file existed (Google/ChatGPT is your friend again).
 
## Set up an SSH key with GitHub

Retyping passwords can be annoying when pushing to GitHub, a standard way of getting around this doing this is with SSH keys.
An upside of doing this is that you can use the same process to avoid remembering passwords when SSHing onto a remote server too.
Try GitHub's instructions [here](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent).
Now you can use the "ssh" link instead of "https" when cloning a repo from GitHub.

## Go oldschool with patch files

Try sharing changes without using GitHub??

- Have two people clone the same repository
- Now person 1 add some commits
- Create a patch file for these commits (Google is your friend)
- Send that patch file via email to person 2
- Person 2 apply the patch file
- Both people check that the Git logs now match

## Check out Edi Uni's GitLab server

Edinburgh Uni has it's own GitLab instance (similar to GitHub) for research. Why not try it out? [ecdf](https://git.ecdf.ed.ac.uk/users/sign_in)

## Juggling multiple remotes

Try cloning my fork of "mathematics in lean": `git clone [https://github.com/glams-lean-2024/formal-2024](https://github.com/lnay/mathematics_in_lean)`.

Let's suppose we want to rebase thet changes onto the new changes on the repository it was forked from (mathematics in lean).

Add an extra remote "mil" corresponding to the original project: `git remote add mil https://github.com/leanprover-community/mathematics_in_lean`.
Update the references for the remote (`git fetch (--all ?)`). Now you can rebase the current branch onto the original project: `git rebase mil/master`.
Feel free to be brutal in the merge conflict resolution, this is just an exercise, the end product does not need to actually work.

## Managing multiple Git identities

Do you have multiple GitHub/GitLab accounts? Check out this blog [post](https://dev.to/milhamh95/how-to-set-multiple-git-identities-with-git-config-4m66)
to configure your commit user names and emails to change depending on which directory your repo is.
