# Team Collaboration Guide

## Push Procedure (Sending Changes)

1. Check the status of your changes:
   ```bash
   git status
   ```
2. Stage the files you want to commit:
   ```bash
   git add <file>
   ```
3. Create a commit with a meaningful message:
   ```bash
   git commit -m "Short description of the change"
   ```
4. Pull latest changes before pushing to avoid conflicts:
   ```bash
   git pull origin <branch>
   ```
5. Push your changes to the remote repository:
   ```bash
   git push origin <branch>
   ```

## Pull Procedure (Fetching Changes)

### git fetch — download without merging
```bash
git fetch origin
```
Downloads new commits from the remote but does **not** modify your working directory. Use this to inspect changes before integrating them.

### git pull — download and merge
```bash
git pull origin <branch>
```
Equivalent to `git fetch` + `git merge`. Updates your local branch with the latest remote changes.

### When to use which?
- **fetch** — when you want to review remote changes first (`git log origin/main..main`)
- **pull** — when you trust the incoming changes and want to integrate immediately

## How to Create a PR / MR

1. Push your feature branch to the remote:
   ```bash
   git push -u origin feature/your-feature-name
   ```
2. Go to GitHub / GitLab and open a **Pull Request** (GitHub) or **Merge Request** (GitLab).
3. Fill in the PR/MR template:
   - **Title** — short summary of the change
   - **Description** — what was changed and why
   - **Reviewers** — assign at least one team member
4. Wait for the code review and CI checks to pass.
5. After approval, merge the PR/MR (prefer **"Merge commit"** or **"Squash and merge"** depending on team convention).
6. Delete the feature branch after merging.

## Best Practices for Team Collaboration

- **One feature = one branch.** Keep branches focused and short-lived.
- **Pull before you push.** Always sync with the remote before pushing to minimize conflicts.
- **Write clear commit messages.** First line: max 50 characters, imperative mood. Optional body after a blank line.
- **Review code before merging.** Every PR/MR should be reviewed by at least one other team member.
- **Never force-push to shared branches** (main, develop). Force-push is only acceptable on your own feature branches.
- **Use .gitignore.** Keep secrets, build artifacts, and IDE config out of the repository.
- **Tag releases.** Use semantic versioning (v1.0.0, v1.1.0) to mark production releases.
- **Resolve conflicts locally.** If a merge conflict occurs, resolve it on your machine, test, then push.
