# Repositories
### [Adding a local existing project to Github using Command](https://help.github.com/en/github/importing-your-projects-to-github/adding-an-existing-project-to-github-using-the-command-line)
- 'git init' at local directory
- if local directory is empty and you simply want to add it with Github repository then pull the new stuffs from it, continue with <br>
/ ' git remote add origin ***git repository url*** '  # sets the new remote ; ' git remote -v ' # verifies the new remote url ; ' git pull origin master' # pull existing data from git 
- if your local directory has stuffs and Github repository empty<br>
/ 'git add . ' ; 'git commit -m "***yourmsg***" ' ; <br>
/ ' git remote add origin ***git repository url*** '  # sets the new remote ; ' git remote -v ' # verifies the new remote url ; <br>
/ ' git push origin master' # push from local to Github 


# Errors
### [Git Fatal: refusing to merge unrelated histories](https://ndb796.tistory.com/275)
- git pull 또는 push (상황에 따라 origin master) + '--allow-unrelated-histories'
