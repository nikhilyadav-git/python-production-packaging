### Git 
- https://education.github.com/git-cheat-sheet-education.pdf
- https://about.gitlab.com/images/press/git-cheat-sheet.pdf

### Concepts
- repositories
- commits
- branches
- merging
- tags

### CLI
```sh
# initilize git repo/workspace
- git init 
# show status of files workspace, staged or commited
- git status 
# stage the changes that we want to persist to our git history 
- git add <filename> 
# difference b/w workspace and staging dir
- git diff <filename> 
# for new file use cached flag to find difference b/w workspace and staging dir
- git diff --cached <filename> 
# commit changes
- git commit -m 'commit message' 
# show list of commits
- git log 
# time travel, not to commit any pending changes else time travel is not possible
```