
### Git commands
- **Clone:** bring a repository that is hosted somewhere else
- **Add:** track your files and changes in git
- **Commit:** save your files in git
- **Push:** upload commits to a remote repo, like github
- **Pull:** download changes from remote repo to your local machine, the opposite of push.

**1. Clone a repository:**
```
$ Git clone git@github.com:alyraluca/Portofolio.git
```
**2. List all the files in the folder:**
```
$ ls -la
```
See the status of all the files (if they have changes that are not commited)
```
$ git status
```
**3. Push changes to the github**
Initiate an existing git repository:
```
$ git init
```
Add the files to the list of things to push:
```
$ git add .
```
Commit / save it locally / put it on hold all the files/files changes:
```
$ git commit -m "Title of the commit." -m "Longer description."
```
Push the files/changes live to github:
```
$ git push origin main
or
$ git push origin master
or
$ git push
```
**4. Create a new online repository from a local folder:**
```
$ git init
$ git add .
$ git commit -m "Title"
```
Create an empty repository on github and copy the ssh link:
```
$ git remote add origin git@github.com:alyraluca/Portfolio.git
```
Show all the remote repositories that I connected to:
```
$ git remote -v
```
Push the changes:
```
$ git push origin master
or
$ git push origin main
```

**5. Git branching**
- Usefull if we have new features to our apps
- We don't whant it to break our code
- This new feature is not finished yet
- Usefull if having multiple people working on the same repository
- Hot fix branch: to fix bugs or small errors in our code

Shows how many branches we have, shows a * next to the one we are on:
```
$ git branch
```
Exit from the branching:
```
$ q
```
Create a new branch called 'feature-readme-instructions':
```
$ git checkout -b feature—readme-instructions
```
Switch between branches:
```
$ git checkout master
or
$ git checkout main
or
$ git checkout feature-readme-intructions
```
Shows what changes we made / compares codes versions:
```
$ git diff feature-readme-intructions (name of the other branch we want to compare code to)
```
Push to the feature-readme-instructions branch:
```
$ git push –u origin feature—readme-instructions
```
Pull request from the main branch once our `pull request` was aproved and the branches merged:
```
$ git pull 
```
Delete the other branch:
```
$ git branch -d feature-readme-instructions
```
Add and commit at the same time (only works for modified files, NOT created):
```
$ git commit -am "message"
```
Merge/combine code from 'master' to 'feature-readme-instructions' (actualizar codigo so we are not to left behind):
```
$ git merge master
```
Fix merge conflics if we made changes to the same line:
- We can do it from visual-studio


**6. Undoing git:**
Undo 'add .'/stage command:
```
$ git reset
```
Undo a 'commit' / unstage last commit:
```
$ git reset HEAD~1
```
Undo a specific 'commit' :
```
$ git reset 32jk432jb5j345hj435vhj (hash of the commit we want to undo)
```
See a log of all your commits and hash code:
```
$ git log
```
Undo a push and remove all the changes made  :
```
$ git reset --hard 32jk432jb5j345hj435vhj (hash of the commit)
```

**7. Autentification SSH**
Check ig your SSH Key is Loaded:
```
$ ssh-add-l
```
Test the SSH Connection:
```
$ ssh -T git@github.com
```
Generate a **`ssh key`** on your computer:
```
$ ssh-keygen -t rsa -b 4096 -C "alyraluca@gmail.com"
```
Enter name for the key file. Enter passphrase.
```
$ testkey (name of the key file)
```
Search for the keys:
```
$ ls | grep testkey (name of the key file we entered before)
```
Print the public key that was generated:
```
$ cat testkey.pub
```
- Copy the key that appears on the terminal by highlighting it.
- Go to github.com
- Go to settings
- Go to SSH keys
- Create a new SSH key
- Paste the key you just created
- Save it
- Let your local git command know about your ssh key:
  - Start the SSH agent:
    ```
    $ eval "$(ssh-agent -s)"
    ```
  - Then add your SSH key to the agent:
    ```
    $ ssh-add ~/.ssh/testkey
    ```

Make your key persistent:
```
$ eval "$(ssh-agent -s)" && ssh-add ~/.ssh/testkey
```

**8. Pull requests**
- When we don't have access rights to the repository
- If we don't own the repository
- Have other people **`review`** our code before we merge it

Once we pushed changes to github from a different branch (`branching`), on github.com we get asked if we want to `open a pull request`.
The owner gets to `merge pull request`