<h1> Remove File and Folder</h1>

```bash
git rm file.txt          # Delete file and stage the deletion
git rm -f file.txt       # Force delete file and stage the deletion
git rm --cached file.txt # Remove file from staging area but keep it locally
git rm -r folder_name    # Remove a folder and its contents
```

* `git rm` removes files **from Git and disk**
* `--cached` removes files **only from Git tracking**
