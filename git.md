### Git 
- https://git-school.github.io/visualizing-git/
- https://learngitbranching.js.org/
- https://education.github.com/git-cheat-sheet-education.pdf
- https://about.gitlab.com/images/press/git-cheat-sheet.pdf

### Workflow
    - Working Directory → changes not yet staged
    - Staging Area (Index) → git add
    - Repository → git commit

### CLI
- Configuration
    ```sh
    git config --global user.name "Your Name"         # Set your name
    git config --global user.email "you@example.com"  # Set your email
    git config --global core.editor "code --wait".    # Set VS Code as default editor
    git config --list                                 # View Git config settings
    ```
- Repository Management
    ```sh
    git init                                          # Initialize a new Git repository
    git clone <url>                                   # Clone a repo from a remote URL
    ```
- Basic Snapshotting
    ```sh
    git add <file>                                    # Stage a specific file
    git add .                                         # Stage all changes in the directory
    git status                                        # Show status of working directory
    git commit -m "Message"                           # Commit staged changes with a message
    git commit -am "Message"                          # Add and commit tracked files in one step
    ```
- Difference
    ```sh
    git diff                                          # Show changes in working directory (unstaged changes)
    git diff --cached                                 # Show changes that are staged (ready to commit) 
    git diff --staged                                 # Show changes that are staged (ready to commit)  
    git diff HEAD                                     # Compare working directory vs last commit
    git diff <commit1> <commit2>                      # Compare changes between two commits
    git diff branch1..branch2                         # Compare different branches
    ```
- History & Logs
    ```sh
    git log                                           # Show commit history
    git log --oneline                                 # Condensed log (one line per commit)
    git show <commit>                                 # Show details of a commit
    git diff                                          # Show unstaged changes
    git diff --staged                                 # Show staged changes
    ```
- Branching & Merging
    ```sh
    git branch                                        # List all local branches
    git branch -m master main                         # Rename Branch master -> main
    git branch <name>                                 # Create a new branch
    git checkout <branch>                             # Switch to a branch
    git switch <branch>                               # Alternative to checkout (modern)
    git switch -c <branch>                            # Create and switch to a new branch
    git merge <branch>                                # Merge a branch into current, "forked" or branched timeline
    git rebase <branch>                               # Move/Transfer commits onto another checkout branch, Clean, straight history
    ```
- Remote Repositories
    ```sh
    git remote -v                                     # Show remote URLs
    git remote add <name> <url>                       # Add a new remote
    git fetch                                         # Download changes from remote
    git pull                                          # Fetch and merge from remote
    git push                                          # Push changes to remote
    git push -u origin <branch>                       # Push and set upstream for a branch
    ```
- Undo & Reset
    ```sh
    git checkout -- <file>                            # Discards changes in the working directory for specified file and restores it to the state from the index (staging area). If you have not stashed it then changes are gone.
    git restore <file>                                # Modern way to discard changes in Working Directory, changes lost in WD until stashed
    git --staged restore <file>                       # Modern way to unstage changes (keeps changes in Working Directory) or you can say git add undo
    git reset <file>                                  # Same as git --staged restore i.e. unstage a staged file
    git reset --hard                                  # Reset all changes (destructive)
    git revert <commit>                               # Create a new commit that undoes one
    ```
- Stashing
    ```sh
    git stash                                         # Stash current changes
    git stash apply                                   # Re-apply latest stash
    git stash list                                    # List all stashes
    git stash drop                                    # Delete a stash
    ```
- Tagging
    ```sh
    git tag                                           # List tags
    git tag <tagname>                                 # Create a new tag
    git tag -a <tagname> -m "message"                 # Create annotated tag
    git push origin <tagname>                         # Push a specific tag
    git push origin --tags                            # Push all tags
    ```
- Clean Up
    ```sh
    git clean -f                                      # Remove untracked files
    git gc                                            # Cleanup unnecessary files and optimize
    ```
- Submodules
    ```sh
    git submodule add <url>                           # Add a new submodule
    git submodule update --init                       # Initialize and update submodules
    ```