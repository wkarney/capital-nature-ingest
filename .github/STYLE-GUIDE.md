# Table of contents

1. [Branches](#branches)
2. [Commits](#commits)
3. [Merging](#merging)
4. [Rebasing](#rebasing)

## Branches

* Choose *short* and *descriptive* names:

  ```shell
  # good
  $ git checkout -b xml-to-json

  # bad - too vague
  $ git checkout -b data_fix
  ```

* It's also a fine idea to use issue #'s in the branch name. For example:

  ```shell
  # GitHub issue #15
  $ git checkout -b issue-15
  ```

* Use *hyphens* to separate words.

* Delete your branch from the upstream repository after it's merged, unless
  there is a specific reason not to.

  Tip: Use the following command while being on "master", to list merged
  branches:

  ```shell
  $ git branch --merged | grep -v "\*"
  ```

### Commits
The following defines how a commit message should be structured. Please reference the relevant GitHub issues in your commit message using GH1234 or #1234. Either style is fine.

 - an appropriately prefixed (see below) subject line with < 80 chars and the relevant issues(s)
 - one blank line.
 - optionally, a commit message body.

For the subject line, we'd prefer it if you prefixed the line with one of these acronyms:

 - ENH: Enhancement, new functionality
 - BUG: Bug fix
 - DOC: Additions/updates to documentation
 - TST: Additions/updates to tests
 - BLD: Updates to the build process/scripts
 - PERF: Performance improvement
 - CLN: Code cleanup

Here's an example:
```bash
git commit -m "TST: add test cases for foo (#1)"
```

## Merging
You rebase and merge when you want to integrate changes from one branch into another branch. The difference
between these two operations is that `git rebase` is destructive whereas `git merge` is not. There's
a great tutorial on these two operations [here](https://www.atlassian.com/git/tutorials/merging-vs-rebasing).

A common `git merge` use-case is when you want to integrate into your branch changes that have happened to master.

To do this, you need to “merge upstream master” in your branch:
  ```
  git checkout shiny-new-feature
  git fetch upstream
  git merge upstream/master
  ```
## Rebasing  
You might need to `git rebase` when you've made a pull request, received a review sometime later, and then had the PR
approved. In this case, you might have a "stale" PR - changes could have happened to `master` that aren't reflected in 
your approved branch. This [tutorial](https://github.com/edx/edx-platform/wiki/How-to-Rebase-a-Pull-Request) walks you 
through rebasing.