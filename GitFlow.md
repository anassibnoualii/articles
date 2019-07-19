

**Step 1. Start from develop.**

   Assuming your main branch is called develop, make sure on your local machine you start there. It should have 
   your latest good code from you and your team. Start 
   there, and make sure you have the latest version .

**Step 2. Create a branch for your work.**

From your main branch (develop), create a new branch. In most clients this will also switch you to the new branch. If you’re operating from the console, you can do this:
`git checkout -b my-new-branch`

**Step 3. Write Code**

Now you’re ready to do whatever work you were planning on. Open  your editor of choice and make your changes.

**Step 4. Commit Often**

   * Any time you make some progress (code compiles, tests pass) or you just want to save where you are (end of the day, lunchtime), make a commit: `git commit -m 'make a meaningful message' `
   * Sync your changes with GitHub repository periodically `git push`.

**Step 5. Create a Pull Request**

When you’ve completed the work you set out to do in this branch (created a feature, fixed a bug), it’s time to merge your work back into your main branch. You do this with a Pull Request, which you can create.

When creating the pull request, you should give it a name that is probably similar to your branch. If your branch was “fix-login-bug” then your PR name might be “Fixed Login Bug”. If there is actually a GitHub issue associated with this problem, you can refer to it in the pull request by number. For instance “Fixes #123”. This will render as a link to that issue, and when this pull request is closed, it will close that issue as well.

**Step 6. Review the Pull Request**

Have a teammate (or you if no other option) review the pull request. A pull request is a conversation between team members to review the code, adding comments to improve the code, discusing the issues .... 

**Step 7. Merge**
Once you’re happy with the code, and perhaps you’ve had a reviewer Approve it, you’re ready to merge. In GitHub, you can configure what the big green merge button does, allowing merge commits.

**Step 8. Delete Branch**

After clicking the button, it’s safe to delete your branch on GitHub. You’ll still have a copy of the branch locally, which you can keep around for as long as you like. At some point, you’ll probably want to delete it, too.

**Step 9. Repeat**

Go back to step 1. You can quickly do this from the command line:

`git checkout develop` .

`git pull `
