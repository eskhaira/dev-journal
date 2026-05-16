## Start session

1. cd ~/code/dev-journal # navigate to the repo
2. git checkout main # make sure you're on main
3. git pull # sync with GitHub before starting
4. git status # confirm clean state before branching

## Create a branch

5. `git checkout -b <branch-name>` # branch off main

## Do the work

6. edit files in VS Code
7. git status # see what changed (run this often)
8. git diff # see exact line-by-line changes

## Save a snapshot

9. git add . # stage all changes for the next commit
10. `git commit -m "<area>: <what changed>"`

## Share with github

11. `git push -u origin <branch-name>` # FIRST push of a new branch # The -u sets the connection. # Future pushes from this branch: # just `git push`

## Open a pull request

12. `Go to github.com/<user>/<repo>`
13. Click "Compare & pull request" banner (or Pull Requests > New)
14. `Set base: main, compare: <branch-name>`
15. Read the diff. Form expectations. Verify them.
16. Write a real title and description
17. Click "Create pull request"

## Review and iterate (if needed)

18. Read your own diff one more time
19. If reviewer requests changes: - edit files locally - git add . && `git commit -m "<area>: <fix>"` - git push # no -u needed now - changes appear on the same PR automatically

## Merge

20. On the PR page, click "Merge pull request"
21. Confirm merge
22. Click "Delete branch" (the GitHub copy)

## Clean up Locally

23. git checkout main
24. git pull # sync with the merged main
25. `git branch -d <branch-name>` # delete local branch
26. git status # confirm clean state 27. git branch # confirm only main remains

END OF CYCLE — back to home base, ready for next branch
