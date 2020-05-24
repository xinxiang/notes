# Remove a directory from the repository but keep its local copy
```
mv path/to/dir/dir_to_remove path/to/dir/dir_to_remove.bk
git rm -r path/to/dir/dir_to_remove
git commit -m'....'
git push
mv path/to/dir/dir_to_remove.bk path/to/dir/dir_to_remove
Add path/to/dir/dir_to_remove in .gitignore
```
