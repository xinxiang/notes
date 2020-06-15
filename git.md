# Keep an empty directory
```
touch log/.gitkeep

Add in .gitignore
**/log/*
!**/log/.gitkeep
```
Ref: https://stackoverflow.com/questions/4250063/how-to-gitignore-all-files-folder-in-a-folder-but-not-the-folder-itself

# Move a repository
```
git clone --mirror <url_of_old_repo>
cd <name_of_old_repo>
git remote add new-origin <url_of_new_repo>
git push new-origin --mirror
```
Ref: https://gist.github.com/niksumeiko/8972566

# Remove a directory from the repository but keep its local copy
```
mv path/to/dir/dir_to_remove path/to/dir/dir_to_remove.bk
git rm -r path/to/dir/dir_to_remove
git commit -m'....'
git push
mv path/to/dir/dir_to_remove.bk path/to/dir/dir_to_remove
Add path/to/dir/dir_to_remove in .gitignore
```
