# Automatic semantic version tagging with GitHub Actions

This repo tests a CICD flow whereby merges to `master` always result in an automatic tagging with a semantic version increment.
The GitHub Action governing the automatic semver tagging is located in `.github/workflows/master.yml`.
The Action is built using the [semantics](https://github.com/stevenmatthewt/semantics) project.

When a developer creates a PR pointed at `master`, he/she should set the PR title with a prefix of `patch:`, `minor:`, or `major:`.
The GH Action worklow will look for a regex math on one of these prefixes to the commit message, and increment the tag accordingly.
Please note that Github sets the PR title to be the first line of a commit message when chosing to squash merge.
As such, setting the PR title to have the above suffix should automatically set the commit message to have that prefix.

If the content of this repo are being used in a new GH project, please note that you will first need to tag an initial commit with `v0.0.0` in order for the semantics package to pick up the latest semver appropriately.

Lastly, the GH Action workflow is drafted such that, in the case of a regex miss, a merge to master will default to incrementing the patch value.


