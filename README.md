# Overcommit

[`overcommit` is a tool to manage and configure `git` hooks](https://github.com/brigade/overcommit).

We use `overcommit` in Nitro to guarantee that staged content from any commit meets a number of criteria. `overcommit` runs automatically anytime you use `git commit` in the `nitro-web` project. Configuration for `overcommit` can be found in a `.overcommit.yml` file located on root. Reviewing this file will give you a full breakdown of what `overcommit` looks for before accepting your commit.

Every hook that `overcommit` runs will result in 1 of 3 ways:

* A successful, green `OK`
* A yellow, passing `WARNING`
* A red, failing `FAILED`

If you only encounter `WARNING`s and `OK`s, your changes will be successfully commited. If you generate a `FAILED` hook, your changes will stay staged until you resolve the violation. (In some odd causes, `overcommit` will stash your changes. If you lose your work during `overcommit` execution, try `git stash pop` to retrieve your changes.)

For Nitro, some things that `overcommit` checks is that if you have added a migration(s), that it is in the correct location and has been run. It checks to make sure you have not created any Ruby linting offenses. And it also prevents you from commiting directly to master.
