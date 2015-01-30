# Git Convention

## 1. Commits
### 1.1 Creating commit messages
* Commit message begins with the defined prefix

```git
PREFIX:
Added | Implemented | Refactored | Optimized | Enhanced | Applied | Resolved | Removed

EXAMPLE:
> Added condition for comparing nil values
> Implemented forgot password feature
> Refactored login view controller according to the coding convention
> Optimized loading of images from server
> Enhanced scrolling experience
> Applied parallax in user profile
> Resolved on displaying no results upon searching
> Removed method because it is marked as deprecated
```
* Commit messages with related issue

```git
FORMAT:
<commit-message><space>(issue #<issue-number>)

EXAMPLE:
Added condition for comparing nil values (issue #43)
```

### 1.2. Editing commit messages
To edit the message of the last commit

```git
$ git commit --amend -m "Applied edit in commit message."
```

To edit the message of a specific commit

```git
# Rebasing starting from the first commits
$ git rebase -i --root

# Rebasing starting from desired commit to edit
# commit_id is the commit before the desired commit to edit
$ git rebase -i [commit_id]

# Change 'pick' to 'edit'.
# Change author of the commit
$ git commit --amend -m "Applied commit message edit."

# If you are only amending the message of a specified commit,
# just change 'pick' to 'reword'. Then, modified the commit
# message. Finally, saves it.

# Continue rebasing
$ git rebase --continue
```

### 1.3. Editing the author
To edit the author of the last commit  

```git
# Change author of the commit
$ git commit --amend --author "New Author Name <new-email@address.com>"
```

To edit the author of a specific commit

```git
# Rebasing starting from the first commits
$ git rebase -i --root

# Rebasing starting from desired commit to edit
# commit_id is the commit before the desired commit to edit
$ git rebase -i [commit_id]

# Change 'pick' to 'edit'.

# Change author of the commit
$ git commit --amend --author "New Author Name <new-email@address.com>"

# Continue rebasing
$ git rebase --continue
```

### 1.4. Combining commits
To combine commits

```git
$ git rebase -i --root

pick a370067 A
pick adcc327 B
pick 88863d3 C
pick 4b8af9b D
pick 6da0935 E

# Combine D and B.
# Edit and rearrange the commits accordingly.
# Then replace 'pick' with 'squash' in 'pick 4b8af9b D'
pick a370067 A
pick adcc327 B
squash 4b8af9b D
pick 88863d3 C
pick 6da0935 E

# Save the file and quit.

# Edit the necessary commit message for the combined B and D.
# Save the file and quit.

# In case there are conflict on files, this error appears:
# "error: could not apply caed537... Added water animals.".
# Just use the part having 'Added water animals'
#
# Example:
# >>>>>> HEAD
# The quick brown fox
# ======
# The quick brown fox jumps over the lazy dog.
# >>>>>> Added water animals
#
# Ignore the HEAD, retain the 'Added water animals'.

# Then do the usual
$ git add [file]

# Then, continue rebasing again
$ git rebase --continue
```

### 1.5. Updating commit contents
To update the content of a commit

```git
# Rebasing starting from the first commit.
$ git rebase -i --root

# Rebasing starting from desired commit to edit
# commit_id is the commit before the desired commit to edit
$ git rebase -i [commit_id]

# Change 'pick' to 'edit'.

# Edit the necessary files that involve for that commit.

# Then, do the usual.
$ git add [file]

# Amend the commit.
$ git commit --amend

# Then, save the commit.

# Continue rebasing
$ git rebase --continue

# There is chance that this rebase causes conflict to another
# commit. You have to fix it before to continue rebasing.

# Edit and fix the conflict on the related files.

# Then, do the usual
$ git add [file]

# Then, continue rebasing again
$ git rebase --continue
```

### 1.6. Reverting HEAD from a rebase
To revert to a specific head due to a bad rebase

```git
$ git reflog

# Suppose the old commit was HEAD@{5} in the ref log
git reset --hard HEAD@{5}
```

## 2. Issues
* Setting the title

```git
PREFIX: 
Add | Implement | Refactor | Optimize | Enhance | Apply | Resolve | Remove

EXAMPLE:
> Add avatar and cover photo in user profile
> Implement response caching in friend list
> Refactor for coding convention and documentation
> Optimize parsing models
> Enhance product name labels
> Resolve regarding with the redundancy of views
> Apply push navigation instead of modal
> Remove the files of the classes that are marked as deprecated
``` 

* The reporter must set the description of the issue. Do not submit the issue if there is no description.

## 3. Pull Requests
* Compare and review the differences of the source and destination branch.
* Try to spot issues that the reviewer might find and clean up those.
* Be descriptive with the title. Make it comprehensive. It can be rephrased from the issue title. As much as possible, the title should be related to the issue.
* Explain some details in the description on what you have done.
* Approve the pull requests once all the commits are approved.
* 

## 4. Branch Naming
```git
FORMAT:
<change-types>/<feature>/<detail>

CHANGE TYPES:
add | implement | refactor | optimize | enhance | apply | resolve | remove

FEATURE: 
lowercase words separated by dashes (-)

DETAIL:
lowercase words separated by dashes (-)

EXAMPLE:
> resolve/login/display-errors-from-response
> refactor/login/coding-convention-in-login-controller
> implement/forgot-password
> enhance/home/product-table-view-cells 
```
## 6. References
[1] https://www.reviewboard.org/docs/codebase/dev/git/clean-commits/  
[2] http://www.mutuallyhuman.com/blog/2011/01/10/clean-commits/  
[3] https://github.com/TryGhost/Ghost/wiki/Git-workflow  
[4] http://stackoverflow.com/questions/273695/git-branch-naming-best-practices  
[5] http://nvie.com/posts/a-successful-git-branching-model/  
[6] http://www.guyroutledge.co.uk/blog/git-branch-naming-conventions  
[7] http://makandracards.com/makandra/868-change-commit-messages-of-past-git-commits  
[8] https://help.github.com/articles/changing-a-commit-message/  
[9] http://stackoverflow.com/questions/750172/change-the-author-of-a-commit-in-git  
[10] http://blog.ajduke.in/2014/02/20/changing-commit-message-in-git/  
[11] http://sethrobertson.github.io/GitFixUm/fixup.html  
[12] http://nathanhoad.net/git-amend-your-last-commit  
[13] https://help.github.com/articles/resolving-merge-conflicts-after-a-git-rebase/  
[14] http://alblue.bandlem.com/2011/06/git-tip-of-week-rebasing.html  
[15] http://www.intertech.com/Blog/git-how-to-combine-non-consecutive-multiple-commits-into-one/  
[16] http://stackoverflow.com/questions/134882/undoing-a-git-rebase  
[17] https://medium.com/@porteneuve/getting-solid-at-git-rebase-vs-merge-4fa1a48c53aa  
[18] http://nearthespeedoflight.com/article/2013_07_10_pull_requests_volume_1__writing_a_great_pull_request
[19] http://blog.codeship.com/github-code-review/

