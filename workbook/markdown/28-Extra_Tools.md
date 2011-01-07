# Extra Git Tooling

## git extras

[Git Extras](https://github.com/visionmedia/git-extras) are a series of commands that composite core Git functionality that would typically be accomplished in multiple command executions.

* `git summary`
    * The number of files, commits, authors
* `git changelog`
    * The recent changes written to a CHANGELOG file
* `git commits-since`
* `git count`
    * Total number of commits to the repo
* `git delete-branch`
    * Delete a branch locally and remotely
* `git delete-submodule`
    * Completely remove a submodule
* `git delete-tag`
    * Delete a tag locally and remotely
* `git fresh-branch`
* `git graft`
* `git ignore`
* `git release`
* `git contrib`
* `git repl`
* `git undo`
    * Undo the last commit via a reset
* `git update-extras`
* `git setup`
* `git touch`
    * Touch a file and add it to the staging area


## git-flow

[Git flow](https://github.com/nvie/gitflow) is a set of commands that standardizes a *workflow of branching* with Git.

It leverages core Git to begin and merge branches for integrations, features, and bug fixes.

* `git-flow init`
    * Start a new flow
* `git flow release`
    * Complete a flow


## Hub

[Hub is a set of scripts](https://github.com/defunkt/hub) that offer GitHub specific shortcuts to Git. These scripts can be invoked via the command `hub` or mapped on to the normal `git` command via a Git alias. In the second situation, all normal Git commands are passed through to the regular `git` command.

* `hub clone`
* `hub remote add`
* `hub fetch`
* `hub cherry-pick`
* `hub fork`
* `hub create`
* `hub init`
* `hub push`
* `hub browse`
* `hub compare`
* `hub submodule`
* `hub help`

If `hub` is mapped as an alias to `git`, you can get help by typing `git help hub`


# Williams Misc Git Tools

[William maintains a set of scripts](http://git-wt-commit.rubyforge.org/) that offer visualizations into the history of a Git repository.

* `git-wtf` understand the current state of your git repository.
* `git-publish-branch` publish a branch to a remote repository.
* `git-rank-contributors` rank all authors by patch size.
* `git-show-merges` show which branches are merged into the current branch.

