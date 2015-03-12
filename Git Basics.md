# Git Basics  
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
[5. Tags and Versioning](#tags-and-versioning)  
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

**Deleting feature branches:**

```git
# Deletes a local branch
$ git branch -d feature-branch-name

# Deleting a remote branch
$ git push origin --delete feature-branch-name
```

<a id="pull-requests"></a>
## 2. Pull Requests
Pull requests are used to manage changes made from contributors or developers [[1]](http://yangsu.github.io/pull-request-tutorial/). These are living conversations that streamline the process of discussing, reviewing, and managing changes to code [[2]](https://github.com/features).  
  
Once a pull request is sent, project maintainers can review the set of changes and discuss potential modification [[3]](https://help.github.com/articles/using-pull-requests/#article-platform-nav). In other words, when a developer has filed a pull request it means that he/she is requesting the project maintainer to pull the changes from his/her branch to another branch (also from repo to another repo) [[4]](https://www.atlassian.com/git/tutorials/making-a-pull-request).  
  
Before filing a pull request, you must compare the source branch/repo to the destination branch/repo and if there are changes to the destination branch, **merge** with and **test** the changes from the destination branch [[5]](https://confluence.atlassian.com/display/BITBUCKET/Work+with+pull+requests). After a successful merge, conflict resolutions, and fixes on the affected changes (this might arise because of the merge), the developer can now file a pull request.

**General Process:** [[6]](https://www.atlassian.com/git/tutorials/making-a-pull-request/how-it-works)    
>
1. A developer creates the feature in a dedicated branch in their local repo.  
2. The developer pushes the branch to a repository.  
3. The developer files a pull request.  
4. The team reviews the code, discusses it, and alters it.  
5. The project maintainer merges the feature into the official repository and closes the pull request.

<a id="merging"></a>
## 3. Merging
After a pull request from a feature branch is being code reviewed and there are no problems, the project maintainer merge the feature branch into the development branch.

```git
# Switches to the development branch.
$ git checkout development

# Merges the current branch to the specified branch
# which is the 'feature-branch-name'.
# The '--no-ff' argument generates a merge commit.
# This is useful for documenting all merges done.
$ git merge --no-ff feature-branch-name
```

After a thorough testing on the development branch and there are no problems, the project maintainer can now merge the development branch into the master branch.

```git
$ git checkout master
$ git merge --no-ff development
```

<a id="code-review"></a>
## 4. Code Review
Code review helps disseminate knowledge across teams, catches bugs (or more likely poor architectural decisions) before they bite you, and provide opportunities to educate junior engineers [[7]](http://justinlilly.com/misc/state_of_githubs_code_review.html).

<a id="tags"></a>
## 5. Tags and Versioning
Tagging in Git is a great way to denote specific release versions of your code [[8]](http://gitready.com/beginner/2009/02/03/tagging.html). Naming of tags should be in this format:

```git
# Production
rel-v1.0.0
rel-v1.0.1
rel-v1.1.0

# Development
dev-v1.0.0.1
dev-v1.0.0.2
dev-v1.0.0.3
dev-v1.0.1.1
```
**Creating and pushing tags:**

```git
# Switches to the master branch
$ git checkout master

# Creates a tag
$ git tag -a rel-v1.0.0 -m "Created the first version."

# Shows all tags
$ git tag
rel-v1.0.0

# Pushing tags to the remote repo
$ git push --tags
 
# Pushing a specific tag
$ git push origin rel-v1.0.0
```

<a id="issues"></a>
## 6. Issues
Issues are a great way to keep track of tasks, enhancements, and bugs for your projects and they’re kind of like email—except they can be shared and discussed with the rest of your team [[9]](https://guides.github.com/features/issues/index.html).

* [Bitbucket](https://confluence.atlassian.com/display/BITBUCKET/Use+the+issue+tracker)  
* [GitHub](https://guides.github.com/features/issues/)
