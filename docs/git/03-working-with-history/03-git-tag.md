
<h1>Git Tags</h1>

* Used to **mark specific commits** (usually releases)
* Tags point to a **commit snapshot**
* Commonly used for **versioning** (e.g., `v1.0.0`)




<h3> Common Commands</h3>

```bash
git tag                                  # List all tags

git tag <tag-name>                       # Create a tag on current commit
git tag -a <tag-name> -m "Release 1.0"   # Create an annotated tag

git tag <tag-name> <commit-hash>         # Tag a specific commit
git push origin <tag-name>               # Push a tag to remote

git tag -d <tag-name>                    # Delete local tag
git push origin :<tag-name>              # Delete remote tag
```

![alt text](image/tag.png)
