tags: git

date: 2021-09-26 18:06

---

# Using Remote Git Repository

```shell
# initialized
git init

# bind a remote repository
git remote
git remote add origin git@github.com:zixiang-chen/macrosay.git
git remote -v
git remote show origin

# basic commands
git add .
git status
git commit -m "first commit"
git log

# pull and push
git pull --allow-unrelated-histories origin main
git push origin main
```

#### references:

+ https://git-scm.com/book/en/v2/Git-Basics-Working-with-Remotes
+ https://stackoverflow.com/questions/37937984/git-refusing-to-merge-unrelated-histories-on-rebase
+ https://stackoverflow.com/questions/1270514/undoing-a-git-push
+ https://git-scm.com/book/en/v2/Git-Basics-Viewing-the-Commit-History
+ 

