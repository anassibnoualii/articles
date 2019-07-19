****What should you check before you open a pull request****

1. **Does it build and all the unit tests pass?**

   * Run`mvn clean install`

1. **Do all cucumber tests pass?**

   * Run`mvn clean verify -PITestOnly` .

1. **Rebase before you open a pull request!**

   * You should rebase your branch on `develop` before you open a pull request to have all recent changes and to ease the merge (make sure you have the last version of the `develop` branch by running`git pull`. 

   * To rebase on develop branch run the following command `git rebase develop`
     
   * If you pushed your branch already to `origin` before, git will most likely tell you after the rebase that your local branch and the remote branch have diverged .
     This is expected! If you are sure that the remote branch does not contain any commits you don't have in your local, rebased version, you can safely push using `git push -f origin <branch-name>` to enforce overwrite.

   * Each pull request should add one feature or fix one bug. If you have multiple features or fixes in a pull request, you might get asked to split your request and open multiple pull requests instead.

1. **Describe what you changed in the pull request!**

   * When opening the pull request you should give a detailed description of what you changed and why. In some cases the individual commit messages are enough, but in most cases it is more convenient for the reviewers to have an overview of what has changed and what you intended with the changes.
