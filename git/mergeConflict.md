#Resolving a Git Merge Conflict

If you make a pull request on GitHub and cannot automatically merge, GitHub will give you the following instructions for resolving the merge conflict from the command line (all values in `[]` are placeholders):

1. git checkout -b [temp-branchname] master
2. git pull https://github.com/[user]/[repo].git master
3. git checkout master
4. git merge --no-ff [temp-branchname]
5. git push origin master

#BUT THERE IS DANGER!!!
GitHub makes it look like you can just copy/paste those commands and everything will be fine, but there are some **Critical Steps** missing. What you actually need to do is: 

1. git checkout -b [temp-branchname] master
2. git pull https://github.com/[user]/[repo].git master
3. **open your project in ATOM and resolve the conflicts (see below for details)**
4. **git add .**
5. **git commit -m 'Resolved merge conflict.'**
6. git checkout master
7. git merge --no-ff [temp-branchname]
8. git push origin master

##Resolving conflicts in the code
Git will insert merge conflict markers in your code to indicate the un-mergeable code. They look like this:

```
<<<<<<< HEAD
	[one version of the code]
=======
	[the other version]
>>>>>>> 2c31a0cff15d03740a8a7e9c27de0cff91381c	
```
Everything between `HEAD` and `=======` will be the version in the branch where you issued the `merge` command; the rest 