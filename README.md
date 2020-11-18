# Extra Mile 1
## Commit Message
**Commit Message Convention**

A good practice when working with agile and feature branches is to include the ticket number in the feature branch name as it’s good for traceability. If you’re using Jira to create your feature branches, you can create branches from the UI of the ticket and it will automatically have the ticket number prepended to the branch name. For this tutorial, we’ll assume this best practice is being followed. Therefore, if our branch was named “ABC-123-some-nice-feature”, we want to extract the ABC-123 segment and either prepend or append it to our commit message. This is where Git Hooks come in. Git Hooks are simply a way to trigger custom scripts when certain Version Control System (VCS) events occur and they can be found in the .git/hooks directory of your git based project.

**Step 1: Create the hook file**

Open up the .git/hooks directory of your project and you’ll see a handful of sample hook files for various VCS events. For our goal, we want to change the prepare-commit-msg.sample script which as the name suggests, is triggered when you make a git commit and prepare the commit message. Open this file with your favourite command-line text editor and delete all the commented out boilerplate code in there.

**Create a hook** 

Use following script from [hook example](https://github.com/olga1iubchenko/gitTask/blob/main/extraTask/hooks/prepare-commit-msg-example)  and copy its content to file to prepare-commit-msg (i.e. remove the .sample).
Now simply run git init to pick up the changes and try making a commit! You should see the ticket ID from your branch automatically prepended to your commit message.

**Going Global**
Firstly, set up a git template directory using the git config command. In this example we’re using the .git-templates folder we’ve created in our home directory:
```
git config --global init.templatedir '~/.git-templates'
```
Then create the hooks directory for global hooks in your template folder:
```
mkdir -p ~/.git-templates/hooks
```
Afterwards, copy your hooks into this newly created directory and ensure permissions are correctly set on the file
```
chmod a+x ~/.git-templates/hooks/prepare-commit-msg
```
Set the commit template in the .gitconfig file: 
```
git config --global commit.template  ~/.git-templates/hooks/prepare-commit-msg
```
This will insert the following configuration in your .gitconfig file:
```
[commit]
       template = ~/.git-templates/hooks/prepare-commit-msg ~/.git-templates/hooks/prepare-commit-msg
 ```
 Done! Now whenever you run git commit, it will prepend the first segments of the branch to the commit message! For existing projects, you just need to reinit the git directory (don’t worry, it won’t break anything!) by running the following in the project root directory:
 ```
 git init
 ```

**Test**

After you’ve saved the prepare-commit-msg file you can then cd into your Git repo and test out your new customization. Create or change a file in your repo and run git commit and you should see your new template (if you created one) and the addition of the branch name at the beginning of the commit message.

## Verifiaction on build status before commit

**Create hook**
*Tip:* please follow the steps described above to setup pre-commit hook.

Please find hook content in [pre-commit-example](https://github.com/olga1iubchenko/gitTask/blob/main/extraTask/hooks/pre-commit-example)

## Verifiaction of uncommited changes before push
*Tip:* please follow the steps described above to setup pre-push hook.

Please find hook content in [pre-push-example](https://github.com/olga1iubchenko/gitTask/blob/main/extraTask/hooks/pre-push-example)

*Note:* as far as pre-push is a local hook maybe additional restriction in pre-receive hook would be the good idea. But task states only this requirenment so implemented only for local.

# Copy repository to new repository
*Tip:* please follow the steps described above to setup pre-push hook.

Please find hook content in [clone-repository-example](https://github.com/olga1iubchenko/gitTask/blob/main/extraTask/hooks/clone-repository-example)
