##Useful Github Tips

###Git push without username and password

####1.Generate an SSH key
```bash
cd ~                 #Your home directory
ssh-keygen -t rsa    #Press enter for all values
```
####2.Associate the SSH key with the remote repository
Goto github's setting

####3.Set your remote URL to a form that supports SSH
```bash
git remote show origin
git remote set-url origin git+ssh://git@github.com/username/reponame.git
```
