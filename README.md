# github-playground-lab

![GitHub](https://img.shields.io/badge/GitHub-Learning%20Lab-181717?logo=github)
![Status](https://img.shields.io/badge/status-active-success)
![Contributions Welcome](https://img.shields.io/badge/contributions-welcome-brightgreen)

A **beginner-to-advanced Git + GitHub playground** that simulates a real open-source repository.  
Use it to practice collaboration with your **main account** (maintainer) and **demo account** (contributor).

## What this repository is

This is a safe training lab to practice:

- Git basics and commits
- Branching, merging, rebasing, cherry-picking
- Pull requests, code review, and conflict resolution
- Issues, labels, milestones, and release flow
- Fork + contribution workflow with 2 accounts
- GitHub Actions CI basics

## Quick start

```bash
git clone https://github.com/<your-main-account>/github-playground-lab.git
cd github-playground-lab
git checkout -b chore/first-practice
```

Make your first change:

```bash
echo "My first practice commit" >> practice/commits/log.txt
git add .
git commit -m "chore: add first practice entry"
git push -u origin chore/first-practice
```

Then open a PR to `main`.

## Learning roadmap (beginner -> advanced)

1. **Git Basics**: clone, status, add, commit, log
2. **Branches**: create, switch, merge
3. **PR Workflow**: open PR, request review, merge
4. **Conflicts**: create intentional conflict and resolve
5. **Rebase**: clean commit history with interactive rebase
6. **Cherry-pick**: move selected commits across branches
7. **Issues & Milestones**: plan work and close via PR
8. **Actions & Releases**: run CI, tag, and publish release notes

See `docs/` for step-by-step guides.

## Hands-on command reference

```bash
# Branching
git checkout -b feature/my-change
git switch main

# Commit lifecycle
git status
git add <file>
git commit -m "feat: my change"
git push -u origin feature/my-change

# Merge / Rebase
git merge feature/my-change
git rebase main
git rebase -i HEAD~3

# History and recovery
git log --oneline --graph --decorate
git revert <commit-sha>
git reset --soft HEAD~1
git reset --hard <commit-sha>
git reflog

# Advanced
git cherry-pick <commit-sha>
```

## Simulated GitHub workflow (realistic)

1. Create issue (`bug`, `feature`, or `docs`)
2. Assign issue + milestone
3. Create branch from issue: `feat/12-add-x`
4. Implement changes + tests
5. Push branch and open PR
6. Review + requested changes
7. Update PR and merge
8. Close issue automatically using PR text (`Closes #12`)
9. Tag release (`v0.1.0`) and update `CHANGELOG.md`

## Practice challenges

### Beginner
- [ ] Make first commit in `practice/commits/`
- [ ] Create and merge a branch
- [ ] Open your first PR using template

### Intermediate
- [ ] Create issue and assign it
- [ ] Link PR to issue with `Closes #<id>`
- [ ] Run and inspect GitHub Actions workflow
- [ ] Trigger and resolve a merge conflict

### Advanced
- [ ] Rebase a feature branch onto latest `main`
- [ ] Cherry-pick one commit from another branch
- [ ] Create annotated tag + GitHub release
- [ ] Simulate fork-based open-source contribution from second account

## Using 2 GitHub accounts (main + demo)

### Option A: Browser account switching

- Main account: acts as **maintainer** of this repo
- Demo account: acts as **external contributor**

### Option B: Local dual-identity setup

Configure identity per repository clone:

```bash
# In maintainer clone
git config user.name "Main Account"
git config user.email "main@example.com"

# In contributor clone (fork)
git config user.name "Demo Account"
git config user.email "demo@example.com"
```

### Fork contribution simulation

1. Log in with demo account and fork this repository
2. Clone fork, create branch, commit, push
3. Open PR from fork -> upstream main
4. Review/merge using main account

## Create merge conflicts intentionally

1. Create two branches from same base
2. Edit same line in `src/sample-feature.txt` differently
3. Merge first branch to `main`
4. Try merging second branch -> conflict appears

Resolve conflict:

```bash
git status
# edit conflicted file and keep final content
git add src/sample-feature.txt
git commit -m "fix: resolve merge conflict in sample-feature"
```

## Rebase practice

```bash
git checkout feature/rebase-practice
git fetch origin
git rebase origin/main
# resolve conflicts if needed
git rebase --continue
```

## Open-source collaboration style

- Read `CONTRIBUTING.md`
- Use issue + PR templates under `.github/`
- Keep commits focused and messages meaningful
- Ask for review, respond to feedback, update PR cleanly

## Suggested labels and milestones

Suggested labels:

- `good first issue`
- `help wanted`
- `bug`
- `enhancement`
- `documentation`
- `needs-review`

Suggested milestones:

- `v0.1 Beginner Flow`
- `v0.2 Collaboration`
- `v1.0 Complete Lab`

## Fake roadmap

- [x] v0.1: initial playground skeleton
- [ ] v0.2: advanced conflict/rebase labs
- [ ] v0.3: release and changelog exercises
- [ ] v1.0: full open-source simulation track

## Contributors

- Maintainer: `@your-main-account`
- Demo Contributor: `@your-demo-account`

---

If you complete all exercises, you will understand how real teams collaborate using Git and GitHub.
