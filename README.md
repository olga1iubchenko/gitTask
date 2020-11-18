**Commit Message Convention**

There are many ideologies on what a good commit message should look like. Based on my own experience and some advice found here and here, this is what I believe a good commit message should include:
Subject line should be a summary of changes in 50 characters or less
The body of the commit message should focus on why the changes are being made as well as how the changes address the issue and any implications or side effects caused by the change
If a lot of explanation is necessary format the message so that its clear and easy to read (i.e. bullet points, new line separation between paragraphs, etc.)

**Create a Template**

This step is not necessary but, it allows you to replace the default commit message prompt with something more useful to your team. Like…some guidelines for a good commit message.
1.Create a template file (e.g. /.git/.prepare-commit-msg)
2. Set the commit template in the .gitconfig file: git config --global commit.template /.git/.prepare-commit-msg. This will insert the following configuration in your .gitconfig file:
[commit]
        template =  /.git/.prepare-commit-msg
 
**Create a hook** 

1. Create a directory to store your hooks: mkdir ~/hooks
2. Create file titled prepare-commit-msgin the hooks directory.
3. Make the file executable: chmod 755 prepare-commit-msg
4. Add script into prepare-commit-msg

**Test**

After you’ve saved the prepare-commit-msg file you can then cd into your Git repo and test out your new customization. Create or change a file in your repo and run git commit and you should see your new template (if you created one) and the addition of the branch name at the beginning of the commit message.

test