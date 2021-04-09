### Push a project to new created git repo
```
1) Create .gitignore file and write file or folder name in it which you want to ignore
on git add
2) git init
3) git add .
4) git commit -m "first commit"
5) git remote add origin https://github.com/dipakongit/git_practis.git
6) git push origin master
```

###  Suppose you want to merge [dev] branch with [master] branch
```
1) git checkout master
2) git merge origin/dev
3) git push origin master
```

###  If you want to delete [dev] branch from both local and remote
```
 1) If you are in [dev] branch then checkout to another branch 
   
   git checkout master

 2) delete from local

   git branch -d dev

 3rd - delete from remote

   git push origin --delete dev
 ```

### If you want to return previous state after commit
```
1) Undo the current commit

  git reset --soft origin/master
  
3) Undo from staged area

  git reset .
```
