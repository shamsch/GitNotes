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
