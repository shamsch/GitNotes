# Git Notes by Shamsur

It happens so often that I need to figure out an issue with Git, so I look it up on StackOverflow, find a solution, and forget about it. However, these issues recurr so often that I want to keep the solution that "worked" stored somewhere so I don't have to go through the trouble of searching through StackOverflow again. So here it is. Git and GitHub related issues that I encountered and found a solution for.

<hr/>

### Accidentially pushing a commit to GitHub aka remote repository or origin

This is a classic. It's pretty easy to fix this in local repo, but it takes a few steps to fix it in GitHub/remote/origin.

**Steps:**

1.  Find the git commit hash you want to return to in your remote and local repo.

`git log --oneline`

2. Say your hash is `308ae4d`, so to return to this commit, you need to do the following commands:

`git push origin +308ae4d:main`

3. That basically brings your remote repository back to that commit, but in the local repo, you will still have those changes as committed.

[Reference](https://stackoverflow.com/a/35291514/19196138)

<hr/>

### Resolving merge conflicts - choosing between incoming and current changes 
I had this situation where I had deleted some files in one branch that still existed in another. I had to merge the other branch into my current branch, but I had to choose between the incoming changes and the current changes. To resolve this, I had to do the following:

**Steps:**
1. Make sure you are in the branch you want to merge into.

2. `git merge other_branch_name`

3. `git checkout --ours file_name` if you want to keep the current changes.

    or, 

    `git checkout --theirs file_name` if you want to keep the incoming changes.
4. In my case, going for the former option would mean despite those files being deleted in the other branch with which the merge was done, I would still have those files in my current branch because I had not deleted them in the current branch. The latter option would mean I would have deleted those files in the current branch too in doing the merge. 

5. To wrap it up `git add .` and `git commit -m "Merge other_branch_name"` to commit the changes you made.

[Reference](https://linuxpip.org/git-accept-all-incoming-changes/#:~:text=all%20of%20them.-,Git%20%3A%20accept%20all%20current%20changes,will%20keep%20the%20original%20one.)

<hr/>

### WSL GIT finds all the files modified if they were created in Windows environment
Running `git status` on Windows will have all files staged and committed, but if you run it on WSL, it will show the same files are all modified. It is because of line endings. WSL thinks it is linux so it will use LF as the line endings. To fix this, you can do the following:

**Steps:**
1. Run the following command in WSL terminal:

`git config --global core.autocrlf true`

[Reference](https://github.com/microsoft/WSL/issues/184#issuecomment-209913528)

<hr/>
