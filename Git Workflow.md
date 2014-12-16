# Git Workflow  
## Table of Contents
[1. Branches](#branches)  
&nbsp;&nbsp;&nbsp;&nbsp;
[1.1. Master Branch](#master-branch)  
&nbsp;&nbsp;&nbsp;&nbsp;
[1.2. Development Branch](#development-branch)  
&nbsp;&nbsp;&nbsp;&nbsp;
[1.3. Feature Branch](#feature-branch)  
[2. Pull Requests](#pull-requests)  
[3. Merging](#merging)  
[4. Code Review](#code-review)  
[5. Tags and Versioning](#tags)  
[6. Issues](#issues)

<a id="branches"></a>
## 1. Branches

<a id="master-branch"></a>
### 1.1. Master Branch   
This is also called the deployment or production branch. Branching out from this branch, except the development branch, is prohibited.

<a id="development-branch"></a>
### 1.2. Development Branch
This is the parent branch for all the feature branches and the one and only child branch of the master branch. Do not make any changes on this branch.

```git
# Do a pull command to get the latest updates from the remote copy.
$ git pull origin development
```

<a id="feature-branch"></a>
### 1.3. Feature Branch
Developer works on this branch for the implementation of a certain feature. Naming should be descriptive as much as possible.

**How to create a feature branch:**

```git
# Gets the latest updates from the remote copy of the development branch. 
$ git pull origin development

# Creates locally a new child branch with a name 'feature-branch-name' 
# from the development branch.
$ git checkout -b feature-branch-name development

# Shows the current checkout branch indicated by the asterisk.
$ git branch
  development
* feature-branch-name
  master
  
# Pushes your newly created local branch to the repository.
# The -u argument is necessary for argument-less git-pull.
# For more details about -u, visit http://bit.ly/1GpOFxo.
$ git push -u origin feature-branch-name
```  

**Take note in pushing changes:**  

```git
# Navigates to a particular branch
$ git checkout feature-branch-name

# This will push changes from the current branch.
$ git push
```
```git
# This will push changes from all local branches 
# to matching branches in the remote.
$ git push origin
```
```git
# This will make sure that if the developer wants
# to push the changes made in 'feature-branch-name-2'.
$ git branch
  development
  feature-branch-name
* feature-branch-name-2
  master
$ git push 
```
```git
# This is the preferred way of pushing the changes that
# is by specifying the branch.
$ git push origin feature-branch-name
```

<a id="pull-requests"></a>
## 2. Pull Requests
Pull requests are used to manage changes made from contributors or developers [[1]](http://yangsu.github.io/pull-request-tutorial/).  
  
Once a pull request is sent, project maintainers can review the set of changes and discuss potential modification [[2]](https://help.github.com/articles/using-pull-requests/#article-platform-nav). In other words, when a developer has filed a pull request it means that he/she is requesting the project maintainer to pull the changes from his/her branch to another branch (also from repo to another repo) [[3]](https://www.atlassian.com/git/tutorials/making-a-pull-request).  
  
Before filing a pull request, you must compare the source branch/repo to the destination branch/repo and if there are changes to the destination branch/repo, merge with and test the changes from the destination repo [[4]](https://confluence.atlassian.com/display/BITBUCKET/Work+with+pull+requests).

**General Process:** [[5]](https://www.atlassian.com/git/tutorials/making-a-pull-request/how-it-works)    
>
1. A developer creates the feature in a dedicated branch in their local repo.  
2. The developer pushes the branch to a repository.  
3. The developer files a pull request.  
4. The team reviews the code, discusses it, and alters it.  
5. The project maintainer merges the feature into the official repository and closes the pull request.

<a id="merging"></a>
## 3. Merging

<a id="code-review"></a>
## 4. Code Review

<a id="tags"></a>
## 5. Tags

<a id="issues"></a>
## 6. Issues
