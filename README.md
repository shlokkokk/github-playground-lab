# GitHub Playground Lab

![GitHub](https://img.shields.io/badge/GitHub-Learning%20Lab-181717?logo=github)
![Status](https://img.shields.io/badge/status-active-success)
![Contributions Welcome](https://img.shields.io/badge/contributions-welcome-brightgreen)

This repository is a **full Git + GitHub practice lab** for learning beginner, intermediate, and advanced workflows in one place.

Use it to practice:

- making your first commit
- creating and merging branches
- opening pull requests
- creating and resolving merge conflicts
- rebasing branches
- creating releases
- using GitHub Actions
- creating, assigning, and closing issues
- simulating a real open-source contribution with **2 GitHub accounts** when needed

---

## Table of contents

1. [How to use this repo](#how-to-use-this-repo)
2. [What you will learn](#what-you-will-learn)
3. [Recommended setup](#recommended-setup)
4. [Practice order](#practice-order)
5. [Beginner labs](#beginner-labs)
6. [Intermediate labs](#intermediate-labs)
7. [Advanced labs](#advanced-labs)
8. [Two-account open-source simulation](#two-account-open-source-simulation)
9. [Bonus practice ideas](#bonus-practice-ideas)
10. [Reset and repeat](#reset-and-repeat)

---

## How to use this repo

This repo is meant to be used like a sandbox.

You should:

1. create a repository from this project or fork it
2. clone it locally
3. follow the labs in order
4. repeat the same exercises until the commands and GitHub UI flow feel natural

You do **not** need 2 accounts for everything.

Use:

- **1 account** for normal Git and GitHub practice
- **2 accounts** only when you want to simulate real open-source contribution, external pull requests, maintainer review, or fork-based collaboration

---

## What you will learn

By the end of this lab, you should understand:

- how local Git commands connect to GitHub
- how branches help isolate work
- how pull requests are used to review and merge changes
- how issues connect planning to code changes
- how merge conflicts happen and how to fix them
- how rebasing changes commit history
- how releases and tags are created
- how GitHub Actions runs automation
- how maintainers and contributors collaborate across 2 accounts

---

## Recommended setup

### 1. Create your accounts

You need:

- **Main account** = maintainer / repo owner
- **Second account** = contributor / open-source contributor simulation

You only need the second account for the later labs.

### 2. Keep the accounts separate

Best options:

- use two different browser profiles
- or use one normal browser window and one private/incognito window
- or use two completely different browsers

This makes it much easier to stay logged into the correct account.

### 3. Clone the repository locally

Clone with your main account first:

```bash
git clone https://github.com/<your-main-account>/github-playground-lab.git
cd github-playground-lab
```

### 4. Set your Git identity

For your maintainer clone:

```bash
git config user.name "Your Main Account Name"
git config user.email "your-main-email@example.com"
```

If you later create a second clone for the contributor account:

```bash
git config user.name "Your Second Account Name"
git config user.email "your-second-email@example.com"
```

Check your identity:

```bash
git config user.name
git config user.email
```

### 5. Learn the commands you will use a lot

```bash
git status
git branch
git switch -c <branch-name>
git checkout -b <branch-name>
git add .
git commit -m "your message"
git push -u origin <branch-name>
git pull origin main
git log --oneline --graph --decorate
```

### Command meaning (quick but complete)

- `git status`  
  shows what changed, what is staged, and what branch you are on.

- `git branch`  
  lists local branches. the `*` mark shows your current branch.

- `git switch -c <branch-name>`  
  creates a new branch and moves you to it.

- `git checkout -b <branch-name>`  
  older command that does the same create-and-switch action.  
  use this if you are on older Git versions or tutorials that still use `checkout`.

- `git add .`  
  stages your local file changes for the next commit.

- `git commit -m "your message"`  
  creates a local snapshot of staged changes.

- `git push -u origin <branch-name>`  
  pushes your local branch to GitHub **and** sets an upstream link.
  - `-u` means `--set-upstream`
  - this tells Git: "this local branch tracks `origin/<branch-name>`"
  - after this first push, you can usually run just `git push` and `git pull`
  - if you skip `-u`, the push can still work, but later `git push`/`git pull` may ask you to specify branch + remote explicitly

- `git pull origin main`  
  fetches latest `main` from GitHub and merges it into your current branch.

- `git log --oneline --graph --decorate`  
  shows short commit history with branch/tag pointers and graph view.

### `git switch` vs `git checkout` (important)

- `git switch` is focused only on branch switching/creation and is easier for beginners.
- `git checkout` is older and does multiple jobs (switch branches + restore files), so it can feel confusing.
- in this lab we mostly use `git switch` for clarity, but knowing both helps when reading older docs or teams using older Git habits.

---

## Practice order

Follow this order for the best learning flow:

### Beginner

1. Make first commit
2. Create a branch
3. Merge a branch
4. Open pull request
5. Create issue
6. Assign issue
7. Close issue via PR

### Intermediate

8. Use GitHub Actions
9. Create merge conflict
10. Resolve conflict

### Advanced

11. Rebase branch
12. Create release
13. Simulate open-source contribution from second account

---

## Beginner labs

### Lab 1: Make your first commit

### Goal

Create a small local change, commit it, and push it to GitHub.

### Steps

1. Open the repo in your terminal.
2. Create a file for your first practice note.

```bash
mkdir -p practice
echo "My first GitHub Playground Lab commit" >> practice/first-commit.txt
```

3. Check what changed.

```bash
git status
```

4. Add the file.

```bash
git add practice/first-commit.txt
```

5. Create the commit.

```bash
git commit -m "docs: add first practice commit note"
```

6. Push your current branch.

If you are on `main` and just practicing privately:

```bash
git push origin main
```

If you prefer safer practice, create a branch first and push that instead.

### What you should learn

- `git status` shows changed files
- `git add` stages changes
- `git commit` saves a snapshot locally
- `git push` sends commits to GitHub

### Challenge

- [ ] Make a second commit with a different message
- [ ] View the commit history with `git log --oneline`

---

### Lab 2: Create a branch

### Goal

Create a branch for new work instead of working directly on `main`.

### Steps

1. Start from the default branch.

```bash
git switch main
git pull origin main
```

2. Create a new branch.

```bash
git switch -c feat/branch-practice
```

3. Make a small change.

```bash
echo "Practicing branch creation" >> practice/branch-practice.txt
```

4. Commit the change.

```bash
git add practice/branch-practice.txt
git commit -m "docs: add branch practice note"
```

5. Push the branch.

```bash
git push -u origin feat/branch-practice
```

### What you should learn

- branches let you work safely
- each branch can hold one topic of work
- pushing with `-u` connects your local branch to the remote branch

### Challenge

- [ ] Create another branch with a different name
- [ ] Switch back and forth using `git switch`

---

### Lab 3: Merge a branch

### Goal

Merge completed branch work into `main`.

### Steps

1. Finish your work on the feature branch.
2. Switch to `main`.

```bash
git switch main
git pull origin main
```

3. Merge the branch.

```bash
git merge feat/branch-practice
```

4. Push the updated `main`.

```bash
git push origin main
```

5. Delete the branch if you want cleanup practice.

```bash
git branch -d feat/branch-practice
git push origin --delete feat/branch-practice
```

### What you should learn

- merging combines branch history
- local branch deletion does not delete remote branch automatically
- branch cleanup is part of normal workflow

### Challenge

- [ ] Merge a second branch
- [ ] Compare merge commit behavior versus squash merge in GitHub UI

---

### Lab 4: Open a pull request

### Goal

Practice the normal GitHub review flow.

### Steps

1. Create a new branch.

```bash
git switch main
git pull origin main
git switch -c docs/pr-practice
```

2. Make a change.

```bash
echo "Pull request practice" >> practice/pr-practice.txt
git add practice/pr-practice.txt
git commit -m "docs: add PR practice file"
git push -u origin docs/pr-practice
```

3. Go to the repository on GitHub.
4. GitHub should show a **Compare & pull request** button.
5. Click it.
6. Set:
   - **base** = `main`
   - **compare** = `docs/pr-practice`
7. Write:
   - a clear title
   - a short description of what changed
8. Click **Create pull request**.

### What you should learn

- a PR compares one branch to another
- PRs are where review and discussion happen
- the branch stays separate until it is merged

### Challenge

- [ ] Edit the PR description after opening it
- [ ] Leave a comment on your own PR
- [ ] Merge it through the GitHub UI instead of CLI

---

### Lab 5: Create an issue

### Goal

Learn how work is tracked before coding starts.

### Steps

1. Open the **Issues** tab on GitHub.
2. Click **New issue**.
3. Give it a title like:
   - `Add practice lab for GitHub Actions`
4. Write a description:
   - what you want to add
   - why it matters
   - what success looks like
5. Submit the issue.

### What you should learn

- issues are for planning, bugs, ideas, and tasks
- issues can be linked to branches and PRs

### Challenge

- [ ] Create one bug issue and one feature issue
- [ ] Add labels if your repo has them

---

### Lab 6: Assign an issue

### Goal

Practice task ownership.

### One-account version

1. Open the issue.
2. Find the **Assignees** section on the right side.
3. Assign yourself.

### Two-account version

Use this when both accounts have access to the repo.

1. Open the issue using the main account.
2. In **Assignees**, select the second account.
3. Save the assignment.

### What you should learn

- issue assignment shows who is responsible
- maintainers often assign work to contributors

### Challenge

- [ ] Reassign an issue from one account to another
- [ ] Create a label like `good first issue`

---

### Lab 7: Close an issue via PR

### Goal

Automatically close an issue when a PR is merged.

### Steps

1. Create a new issue first.
2. Copy its issue number. Example: `#12`
3. Create a branch for that issue.

```bash
git switch main
git pull origin main
git switch -c docs/12-close-issue-via-pr
```

4. Make a change.

```bash
echo "This branch closes issue #12" >> practice/issue-close.txt
git add practice/issue-close.txt
git commit -m "docs: add issue closing practice"
git push -u origin docs/12-close-issue-via-pr
```

5. Open a PR.
6. In the PR description, write:

```text
Closes #12
```

7. Merge the PR.
8. Go back to the issue and confirm it closed automatically.

### What you should learn

- GitHub can auto-close issues from PR text
- the keywords `Closes`, `Fixes`, and `Resolves` are very useful

### Challenge

- [ ] Close 2 different issues with 2 different PRs
- [ ] Test `Fixes #<number>` instead of `Closes #<number>`

---

## Intermediate labs

### Lab 8: Use GitHub Actions

### Goal

Learn how GitHub automation runs on pushes and pull requests.

### Easiest practice path

If this repo already has a workflow:

1. Open the **Actions** tab.
2. Open the `Lab 8 Actions Practice` workflow.
3. Click any workflow run.
4. Inspect:
   - event type
   - branch
   - jobs
   - steps
   - logs
5. Re-run the workflow if GitHub allows it.

### Create-your-own workflow path

If you want to practice building a workflow from scratch:

1. Create a branch.

```bash
git switch main
git pull origin main
git switch -c ci/first-workflow
```

2. Create `.github/workflows/practice.yml`
3. Add a simple workflow that runs on `push` and `pull_request`
4. Make it print a message or list repository files
5. Commit and push
6. Open a PR
7. Open the **Actions** tab and inspect the run

### What to look at in Actions

- workflow name
- trigger event
- runner OS
- job name
- each step log
- success or failure status

### Challenge

- [ ] Trigger a workflow from a push
- [ ] Trigger a workflow from a pull request
- [ ] Purposely break a workflow and read the logs

---

### Lab 9: Create a merge conflict

### Goal

Intentionally create a conflict so you can learn what it looks like.

### Steps

1. Start from `main`.

```bash
git switch main
git pull origin main
```

2. Create branch A.

```bash
git switch -c conflict/branch-a
mkdir -p practice/conflicts
echo "Version from branch A" > practice/conflicts/example.txt
git add practice/conflicts/example.txt
git commit -m "docs: add conflict example from branch A"
git push -u origin conflict/branch-a
```

3. Switch back to `main`.

```bash
git switch main
```

4. Create branch B from the same base.

```bash
git switch -c conflict/branch-b
echo "Version from branch B" > practice/conflicts/example.txt
git add practice/conflicts/example.txt
git commit -m "docs: add conflict example from branch B"
git push -u origin conflict/branch-b
```

5. Merge branch A into `main` first.

```bash
git switch main
git merge conflict/branch-a
git push origin main
```

6. Now try to merge branch B.

```bash
git merge conflict/branch-b
```

7. Git should stop and report a conflict.

### What you should learn

- conflicts happen when Git cannot safely combine overlapping changes
- conflict markers appear inside the file

### Challenge

- [ ] Create another conflict using a different file
- [ ] Try creating a conflict in a PR through GitHub UI

---

### Lab 10: Resolve a conflict

### Goal

Fix the conflict from Lab 9 correctly.

### Steps

1. Run:

```bash
git status
```

2. Open the conflicted file.
3. You will see markers like:

```text
<<<<<<< HEAD
content from current branch
=======
content from incoming branch
>>>>>>> conflict/branch-b
```

4. Replace the entire conflict section with the final content you want.

Example:

```text
Version from branch A and branch B
```

5. Stage the resolved file.

```bash
git add practice/conflicts/example.txt
```

6. Finish the merge.

```bash
git commit -m "docs: resolve practice merge conflict"
```

7. Push the resolved result.

```bash
git push origin main
```

### What you should learn

- you must edit the file manually or with a merge tool
- `git add` marks the conflict as resolved
- the merge commit completes the process

### Challenge

- [ ] Resolve a conflict inside a PR instead of local CLI
- [ ] Use `git log --oneline --graph --decorate` to inspect the merge history

---

## Advanced labs

### Lab 11: Rebase a branch

### Goal

Learn how to move your branch onto a newer base commit.

### Steps

1. Start from updated `main`.

```bash
git switch main
git pull origin main
git switch -c feat/rebase-practice
```

2. Make 2 small commits.

```bash
echo "rebase line 1" >> practice/rebase.txt
git add practice/rebase.txt
git commit -m "docs: add first rebase practice line"

echo "rebase line 2" >> practice/rebase.txt
git add practice/rebase.txt
git commit -m "docs: add second rebase practice line"
```

3. Go back to `main` and create a new commit there so your branch becomes outdated.

```bash
git switch main
echo "main branch changed" >> practice/main-update.txt
git add practice/main-update.txt
git commit -m "docs: add main branch update for rebase practice"
git push origin main
```

4. Return to your feature branch.

```bash
git switch feat/rebase-practice
```

5. Rebase onto `main`.

```bash
git rebase main
```

6. If there is a conflict:
   - fix the file
   - run `git add <file>`
   - run `git rebase --continue`

7. Push the rebased branch.

Because history changed, use:

```bash
git push --force-with-lease origin feat/rebase-practice
```

### What you should learn

- rebase rewrites commit history
- rebasing keeps history linear
- `--force-with-lease` is safer than `--force`

### Challenge

- [ ] Use `git rebase -i HEAD~2`
- [ ] squash 2 commits into 1
- [ ] rewrite a commit message during interactive rebase

---

### Lab 12: Create a release

### Goal

Practice tags and GitHub releases.

### Steps

1. Make sure `main` is up to date.

```bash
git switch main
git pull origin main
```

2. Create an annotated tag.

```bash
git tag -a v0.1.0 -m "First learning lab release"
```

3. Push the tag.

```bash
git push origin v0.1.0
```

4. Open GitHub.
5. Go to **Releases**.
6. Click **Draft a new release** if GitHub does not already open one for the pushed tag.
7. Select tag `v0.1.0`
8. Add release notes:
   - what was practiced
   - what was learned
   - what is next
9. Publish the release.

### What you should learn

- tags point to specific commits
- releases are GitHub's polished version of shared milestones
- annotated tags are better than lightweight tags for real projects

### Challenge

- [ ] Create `v0.2.0` later after more practice
- [ ] write release notes based on merged PRs

---

## Two-account open-source simulation

This is the most realistic lab in the repository.

Use:

- **Main account** as the maintainer
- **Second account** as the outside contributor

### Lab 13: Simulate an open-source contribution from a second account

### Goal

Practice the real public GitHub contribution flow.

### Part A: Maintainer setup

1. Log into the **main account**.
2. Make sure this repository is visible to the second account.
3. Create an issue like:
   - `Add extra beginner challenge to README`
4. Optionally add labels like:
   - `good first issue`
   - `documentation`

### Part B: Contributor fork

1. Log into the **second account**.
2. Open the original repository.
3. Click **Fork**.
4. Create a fork under the second account.

### Part C: Contributor local clone

1. Clone the forked repository, not the upstream repo.

```bash
git clone https://github.com/<your-second-account>/github-playground-lab.git
cd github-playground-lab
git config user.name "Your Second Account Name"
git config user.email "your-second-email@example.com"
```

2. Add the original repository as `upstream`.

```bash
git remote add upstream https://github.com/<your-main-account>/github-playground-lab.git
git remote -v
```

### Part D: Contributor branch and change

1. Create a branch.

```bash
git switch -c docs/contributor-practice
```

2. Make the requested change.
3. Commit it.

```bash
git add .
git commit -m "docs: add contributor practice update"
```

4. Push to the fork.

```bash
git push -u origin docs/contributor-practice
```

### Part E: Contributor opens PR

1. Open the fork on GitHub.
2. Click **Compare & pull request**.
3. Make sure:
   - **base repository** = main account repo
   - **base branch** = `main`
   - **head repository** = second account fork
   - **compare branch** = `docs/contributor-practice`
4. Reference the issue number in the PR description if needed.
5. Submit the PR.

### Part F: Maintainer review

1. Switch back to the **main account**.
2. Open the PR.
3. Review:
   - files changed
   - commit history
   - comments
   - checks
4. Leave review feedback.

You can practice:

- comment only
- request changes
- approve the PR

### Part G: Contributor updates PR

1. Switch back to the second account local clone.
2. Make another small change.
3. Commit and push again to the same branch.

```bash
git add .
git commit -m "docs: address PR review feedback"
git push
```

4. Watch the PR update automatically.

### Part H: Maintainer merges PR

1. Use the main account.
2. Approve the PR if needed.
3. Merge it.
4. Confirm the branch can be deleted.
5. Delete the branch.

### Part I: Sync the fork after merge

From the second account clone:

```bash
git switch main
git fetch upstream
git merge upstream/main
git push origin main
```

### What you should learn

- contributors usually work in forks
- maintainers review and merge into upstream
- a PR can be updated many times before merge
- keeping a fork synced is part of open-source workflow

### Challenge

- [ ] Open 2 contributor PRs from the second account
- [ ] Ask the maintainer account to request changes on one of them
- [ ] Close one PR without merging

---

## Bonus practice ideas

If you finish everything above, try these too:

- [ ] cherry-pick one commit from one branch to another
- [ ] revert a bad commit with `git revert`
- [ ] compare **merge commit**, **squash merge**, and **rebase merge**
- [ ] create a draft pull request
- [ ] add labels and milestones to issues
- [ ] create a project board for issues and PRs
- [ ] write a better `CONTRIBUTING.md`
- [ ] create a PR template
- [ ] practice reviewing code from the second account

---

## Reset and repeat

If you want to repeat labs:

1. create a fresh branch for each new practice attempt
2. delete old practice branches after merging
3. create new files instead of overwriting old notes
4. keep a simple changelog of what you learned

Useful cleanup commands:

```bash
git branch
git branch -d <branch-name>
git push origin --delete <branch-name>
git fetch --all --prune
```

---

## Suggested challenge checklist

### Beginner

- [ ] make first commit
- [ ] create a branch
- [ ] merge branch
- [ ] open pull request
- [ ] create issue
- [ ] assign issue
- [ ] close issue via PR

### Intermediate

- [ ] use GitHub Actions
- [ ] create merge conflict
- [ ] resolve conflict

### Advanced

- [ ] rebase branch
- [ ] create release
- [ ] simulate open-source contribution from second account

---

## Final goal

If you finish this lab fully, you will have practiced most of the Git and GitHub flows that people use in real projects:

- solo development
- team collaboration
- issue planning
- pull request review
- conflict resolution
- release flow
- open-source contribution

That is the point of this repo: **learn by doing, not by only reading**.
