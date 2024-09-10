---
id: Cheatsheet
aliases: []
tags: []
---

## How to remove a file from git history

```zsh
git filter-branch --index-filter `git rm -rf --cached --ignore-unmatch path_to_file` HEAD
```
