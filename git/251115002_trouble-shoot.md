## Stash

Temporarily saves uncommitted changes

- $ git stash
- $ git stash push {filename}

- $ git stash pop
- $ git stash pop {index}
- $ git stash apply

- $ git stash list

- $ git stash drop {index}

## Rename

Edit file name or file location

- $ mv a.md b.md

## Undo

Undo changes in the working directory

- $ git restore {filename}
- $ git restore .    # whole changes

## Unstaging

Move changes from the staging area back to the working directory

- $ git reset HEAD {filename}
- $ git rm -f {filename}    # unstage and remove the file

## Edit commit message

- $ git commit --amend    # edit commit message right before
- $ git rebase -i <commit>    # edit commit message before
- $ git rebase --continue
- $ git rebase --abort    # cancel rebase

## Reset commit

Rewriting history by deleting recent commits

- $ git reset --hard HEAD~<num of commits>    # delete the last <num> commits
- $ git push -f origin <branch>    # force-push rewritten history to remote

## Revert commit

Undo commits by creating new commits that reverse them

- $ git revert --no-commit HEAD~<num of commits>    # prepare to revert the last <num> commits
- $ git commit    # create a revert commit
- $ git push origin <branch>    # push the reverted history

- Revert creates new commits, making it safe for collaboration
- Use '--no-edit' to skip the commit message
- Use '-m' for reverting merge commits
