# 📋 Git Workflow & Branching Strategy

This document outlines the Git workflow and branching strategy for the Crowd-Connect project.

## Branch Structure

```
main (production-ready)
  ├── develop (integration branch)
  ├── feature/feature-name
  ├── fix/issue-name
  ├── docs/documentation-name
  └── refactor/refactor-name
```

## Branch Naming Convention

| Type | Pattern | Example |
|------|---------|---------|
| Feature | `feature/<feature-name>` | `feature/campaign-filtering` |
| Bug Fix | `fix/<issue-name>` | `fix/jwt-token-expiry` |
| Documentation | `docs/<doc-name>` | `docs/api-documentation` |
| Refactoring | `refactor/<component>` | `refactor/auth-middleware` |
| Performance | `perf/<optimization>` | `perf/database-indexes` |
| Testing | `test/<test-name>` | `test/user-validation` |

## Main Branches

### `main` (Production)
- Always stable and production-ready
- Only accepts PRs from `develop`
- Tagged with versions (v1.0.0, v1.1.0, etc.)
- Protected branch - requires code review

### `develop` (Development)
- Latest development changes
- Integration branch for features
- Accepts PRs from feature branches
- Should be relatively stable

## Feature Branch Workflow

### Creating a Feature Branch

```bash
# Update main and develop
git checkout main
git pull origin main
git checkout develop
git pull origin develop

# Create and checkout feature branch
git checkout -b feature/your-feature-name

# Or if creating from main
git checkout -b feature/your-feature-name origin/main
```

### Working on Feature

```bash
# Make changes, add files
git add .

# Commit with clear message
git commit -m "feat(module): description of changes"

# Keep branch updated with develop
git fetch origin
git rebase origin/develop

# Push to remote
git push origin feature/your-feature-name
```

### Pull Request Process

```bash
# Create PR on GitHub
# 1. Go to repository
# 2. Click "New Pull Request"
# 3. Select base: develop, compare: feature/your-feature-name
# 4. Add title and description
# 5. Request reviewers
# 6. Wait for approval and CI checks

# After approval, merge
git checkout develop
git pull origin develop
git merge feature/your-feature-name
git push origin develop

# Delete feature branch
git branch -d feature/your-feature-name
git push origin --delete feature/your-feature-name
```

## Bug Fix Workflow

```bash
# Create fix branch from develop
git checkout develop
git pull origin develop
git checkout -b fix/issue-name

# Make fixes, commit
git add .
git commit -m "fix(module): description of fix"

# Create PR to develop (same as feature branch)
```

## Release Workflow

```bash
# Create release branch from develop
git checkout -b release/v1.1.0 origin/develop

# Update version numbers
# Update CHANGELOG.md
git add .
git commit -m "chore: prepare release v1.1.0"

# Push and create PR to main
git push origin release/v1.1.0

# After approval, merge to main
git checkout main
git pull origin main
git merge --no-ff release/v1.1.0

# Tag the release
git tag -a v1.1.0 -m "Release version 1.1.0"
git push origin v1.1.0

# Merge back to develop
git checkout develop
git merge release/v1.1.0

# Delete release branch
git branch -d release/v1.1.0
```

## Commit Message Format

Follow conventional commits:

```
<type>(<scope>): <subject>

<body>

<footer>
```

### Types
- `feat` - New feature
- `fix` - Bug fix
- `docs` - Documentation
- `style` - Code style
- `refactor` - Code refactoring
- `perf` - Performance
- `test` - Tests
- `chore` - Build/tooling

### Examples

```bash
git commit -m "feat(campaigns): add search functionality"
git commit -m "fix(auth): resolve email verification bug"
git commit -m "docs(readme): update installation steps"
git commit -m "refactor(utils): simplify validation functions"
git commit -m "test(donations): add payment processing tests"
```

## Rebase vs Merge

### Prefer Rebase for Feature Branches

```bash
# Keep history clean
git rebase origin/develop
```

### Use Merge for Release Branches

```bash
# Preserve merge history
git merge --no-ff release/v1.1.0
```

## Common Commands

```bash
# View branches
git branch -a

# Switch branch
git checkout branch-name

# Create and checkout branch
git checkout -b branch-name

# Delete local branch
git branch -d branch-name

# Delete remote branch
git push origin --delete branch-name

# Rename branch
git branch -m old-name new-name

# View commit history
git log --oneline --graph --all

# View changes
git diff
git diff branch1 branch2

# Undo changes
git reset HEAD file.js
git checkout -- file.js

# Stash changes
git stash
git stash pop

# Squash commits
git rebase -i HEAD~3

# Cherry pick commit
git cherry-pick commit-hash
```

## GitHub Configuration

### Branch Protection Rules (main)

- Require pull request reviews before merging
- Require status checks to pass
- Require branches to be up to date before merging
- Dismiss stale pull request approvals when new commits are pushed
- Require code review from code owners

### Branch Protection Rules (develop)

- Require pull request reviews before merging
- Require status checks to pass

## Conflict Resolution

```bash
# If conflicts occur during rebase
git status  # See conflicted files

# Edit files to resolve conflicts
# Then:
git add .
git rebase --continue

# If you want to abort
git rebase --abort
```

## Best Practices

✅ **DO:**
- Use descriptive branch names
- Keep branches focused on single features
- Commit frequently with clear messages
- Keep branches updated with base branch
- Delete merged branches
- Provide meaningful PR descriptions
- Request code reviews

❌ **DON'T:**
- Commit directly to main
- Use vague branch names (`update`, `fix-stuff`)
- Mix multiple features in one PR
- Force push to shared branches
- Leave stale branches
- Ignore code review feedback

## Troubleshooting

### Accidentally committed to main

```bash
# Create feature branch from current commit
git branch feature/your-feature

# Reset main to previous commit
git reset --hard origin/main
```

### Need to undo recent commit

```bash
# Soft undo (keep changes)
git reset --soft HEAD~1

# Hard undo (discard changes)
git reset --hard HEAD~1
```

### Revert a published commit

```bash
git revert commit-hash
git push origin branch-name
```

---

For more help, check [CONTRIBUTING.md](CONTRIBUTING.md) or open an issue.
