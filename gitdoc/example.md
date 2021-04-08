Example: suppose master branch will be merge from prod branch
git checkout master
git merge origin/prod
git push origin master

Example - delete dev branch
 1st - checkout to another branch

 git checkout master

 2nd - delete from local

 git branch -d dev

 3rd - delete from remote

 git push origin --delete dev
