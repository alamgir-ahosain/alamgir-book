<h1>Rename a file</h1>

| Aspect                    | `git mv a.txt aa.txt`     | `mv a.txt aa.txt`                      |
| ------------------------- | ------------------------- | -------------------------------------- |
| Command type              | Git command               | OS / shell command                     |
| Git awareness             |  Yes             |  Not                      |
| Renames file              |  Yes                     |  Yes                                  |
| Stages changes            |  Automatically staged    |  Not staged                           |
| `git status` output       | `renamed: a.txt → aa.txt` | `deleted: a.txt` + `untracked: aa.txt` |
| Manual staging needed     |  No                      |  Yes (`git add`, `git rm`)            |
