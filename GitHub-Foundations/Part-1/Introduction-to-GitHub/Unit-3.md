# Components of the GitHub Flow

## 1. Introduction

GitHub Flow builds on Git's fundamental concepts.

- **Git** provides tools to track, manage, and record changes over time.
- **GitHub** builds on Git by providing features such as branches, commits, pull requests, and visual collaboration tools.

The main components covered in this unit are branches, commits, pull requests, GitHub Flow, and Git flow.

## 2. Branches

A **branch** is an independent line of development within a repository. It allows developers to make changes without affecting the default branch (`main`).

Branches provide a safe environment to:

- Develop new features.
- Fix bugs.
- Experiment with changes.
- Test ideas before merging them into the default branch.

Changes made on a branch do not affect `main` until the branch is merged.

**Create and switch to a new branch using Git:**

```bash
git checkout -b newBranchName
```

This command creates a new branch and automatically switches to it.

## 3. Commits

A **commit** is a recorded change to one or more files on a branch.

Each commit contains identifying information, including:

- A unique ID (hash).
- A timestamp.
- The contributor responsible for the change.

Commits create a history of changes, making it easier to review the development process and track modifications.

**Create a commit:**

```bash
git commit -m "Add a helpful commit message"
```

### File states in Git

Files move through different states during the version control process.

| State | Description |
| --- | --- |
| **Untracked** | Git is not tracking the file yet. |
| **Unmodified** | The file is tracked but has not changed since its last commit. |
| **Modified** | The file has been changed, but the changes have not been staged. |
| **Staged** | Changes have been added to the staging area and are ready to be committed. |
| **Committed** | The changes have been recorded in the repository's database. |

**Important:** Tracked files can be unmodified, modified, staged, or committed as they move through the workflow.

The staging area (also called the **index**) holds changes selected for the next commit.

## 4. Pull Requests (PRs)

A **Pull Request (PR)** is a request to merge changes from one branch into another.

It allows developers to submit their work for review before integrating it into the target branch.

A pull request provides a space to:

- Review code and proposed changes.
- Receive feedback from team members.
- Discuss modifications.
- Request additional changes.
- Approve changes before merging.

### Important PR concepts

- **Base branch:** The branch that will receive the changes.
- **Compare branch:** The branch containing the proposed changes.
- **Draft Pull Request:** A pull request that is not ready for formal review.

Once the required reviews and approvals are completed, the compare branch can be merged into the base branch.

## 5. GitHub Flow

**GitHub Flow** is a simple and lightweight workflow for developing, reviewing, and integrating changes.

It is especially useful for collaboration and continuous delivery.

### GitHub Flow process

1. **Create a branch:** Make a separate branch for a feature, experiment, or bug fix.
2. **Make changes:** Develop and test your changes on that branch.
3. **Open a Pull Request:** Submit your changes for review and feedback.
4. **Review and improve:** Discuss feedback and make any necessary updates.
5. **Approve and merge:** Once the changes are ready and approved, merge the pull request into the default branch.
6. **Delete the branch:** Remove the completed branch to keep the repository clean.

**Workflow overview:**

`Create Branch → Make Changes → Open PR → Review → Merge → Delete Branch`

GitHub Flow keeps the process straightforward and allows teams to integrate changes frequently.

## 6. Git flow

**Git flow** is a more structured branching model designed for projects that use planned or versioned releases.

Unlike GitHub Flow, it uses several specific branch types to separate development, release preparation, and production fixes.

### Git flow branch types

| Branch | Purpose |
| --- | --- |
| **master** | Contains production-ready code. |
| **develop** | Holds the latest development work for the next release. |
| **feature/*** | Used to develop new features. Created from `develop` and merged back when completed. |
| **release/*** | Used to prepare a new production release, including final testing and minor fixes. |
| **hotfix/*** | Used to fix critical production issues. Created from `master`. |

*Note: `master` is the older default branch name. Many modern repositories use `main` instead.*

### How the Git flow process works

1. Developers create **feature branches** from `develop` to work on new functionality.
2. When a release is approaching, a **release branch** is created from `develop`.
3. Final testing and minor bug fixes take place on the release branch.
4. Once ready, the release branch is merged into `master` and tagged with a version number.
5. The release branch is also merged back into `develop` to keep both branches synchronized.
6. If a critical production problem occurs, a **hotfix branch** is created from `master`. After fixing the issue, it is merged into both `master` and `develop`.

### When to use Git flow

Git flow is particularly suitable for:

- Projects with scheduled or versioned releases.
- Software that maintains multiple production versions.
- Enterprise or regulated environments.
- Projects that require structured release planning.

It is considered more heavyweight than GitHub Flow because it requires managing more branches.

**Important:** Traditional Git flow assumes merge commits when integrating branches. Using rebase or squash merges can interfere with its expected branch structure and history.

## 7. GitHub Flow vs. Git flow

| Feature | GitHub Flow | Git flow |
| --- | --- | --- |
| Complexity | Simple and lightweight | More structured |
| Main focus | Frequent integration and delivery | Planned releases |
| Branch structure | Usually short-lived feature branches | Several specific branch types |
| Development | Changes are merged into the default branch | Development work is integrated into `develop` |
| Best suited for | Continuous delivery and collaboration | Versioned releases and structured projects |

**Key takeaway:**

- **GitHub Flow:** Simplicity, collaboration, and frequent integration.
- **Git flow:** Structure, release management, and multiple development stages.

---

## Unit 3 — Knowledge Check

Test your understanding before checking the answers.

### Questions

**1. What is the primary purpose of a Git branch?**

- [ ]  A) To permanently store a backup of the repository.
- [x]  B) To develop changes without affecting the default branch.
- [ ]  C) To delete outdated commits.
- [ ]  D) To automatically merge code.

**2. What information is associated with a commit?**

- [x]  A) A unique ID, timestamp, and contributor.
- [ ]  B) Only the name of the modified file.
- [ ]  C) The repository password.
- [ ]  D) The branch creation date only.

**3. What does the `git checkout -b newBranchName` command do?**

- [ ]  A) Deletes an existing branch.
- [ ]  B) Creates a commit.
- [x]  C) Creates a new branch and switches to it.
- [ ]  D) Merges a branch into `main`.

**4. What is the staging area used for?**

- [ ]  A) Storing deleted files.
- [x]  B) Preparing selected changes for the next commit.
- [ ]  C) Publishing changes directly to GitHub.
- [ ]  D) Creating new repositories.

**5. What is the purpose of a Pull Request?**

- [x]  A) To request that changes from one branch be merged into another.
- [ ]  B) To create a local repository.
- [ ]  C) To automatically delete a branch.
- [ ]  D) To download a repository.

**6. What is a Draft Pull Request?**

- [ ]  A) A pull request that has already been merged.
- [x]  B) A pull request that is not yet ready for review.
- [ ]  C) A pull request without commits.
- [ ]  D) A request to delete a repository.

**7. Which sequence correctly represents GitHub Flow?**

- [ ]  A) Commit → Delete branch → Create branch → Merge.
- [x]  B) Create branch → Make changes → Open PR → Review → Merge → Delete branch.
- [ ]  C) Create repository → Delete commits → Open PR → Push.
- [ ]  D) Merge → Create branch → Review → Commit.

**8. Which branch contains the latest development work in traditional Git flow?**

- [ ]  A) `master`
- [ ]  B) `feature`
- [x]  C) `develop`
- [ ]  D) `hotfix`

**9. From which branch is a hotfix branch created in Git flow?**

- [ ]  A) `develop`
- [x]  B) `master`
- [ ]  C) `release`
- [ ]  D) `feature`

**10. What is the main difference between GitHub Flow and Git flow?**

- [ ]  A) GitHub Flow does not support commits.
- [ ]  B) Git flow does not support branches.
- [x]  C) GitHub Flow is lightweight, while Git flow provides a more structured release process.
- [ ]  D) They are exactly the same workflow.
