# Unit 2

## 1. What is Version Control?

A Version Control System (VCS) is a tool that tracks changes made to files over time. It allows developers to manage different versions of a project and collaborate without overwriting each other's work.

Main purposes:

- Track who made changes, when, and why.
- Restore previous versions of files or entire projects.
- Allow multiple developers to work simultaneously.
- Experiment with new features without affecting the main project.
- Keep a history of the project's development.

### What can you do with Version Control?

| Feature | Description |
| --- | --- |
| Change History | See what changed, when and who changed it. |
| Commit Messages | Document the reason behind each change. |
| Version Recovery | Restore previous versions of files or projects. |
| Branches | Develop features independently without affecting the main project. |
| Merge | Combine changes from different branches. |
| Tags | Mark specific versions, such as software releases. |

**SCM (Software Configuration Management):** A broader discipline that includes version control and other practices for managing software configuration.

## 2. What is Git?

Git is a free, open-source, distributed version control system (DVCS).

- Created primarily by Linus Torvalds, the creator of Linux.
- Fast, flexible and highly scalable.
- Tracks changes and manages project history.
- Allows developers to collaborate on projects.

### Distributed vs. Centralized Version Control

There are two main types of version control systems:

| Centralized VCS | Distributed VCS (Git) |
| --- | --- |
| Project history is stored on a central server. | Every developer has a complete local copy of the project history. |
| Requires access to the central server for many operations. | Most operations can be performed offline. |
| Server failure can affect the entire team. | Developers retain their local repositories if the server goes down. |
| Examples: CVS, SVN, Perforce. | Example: Git. |

**Key takeaway:** Git allows you to work offline, save changes locally and synchronize them with a remote repository when an internet connection is available.

## 3. Essential Git Terminology

These are the fundamental concepts you need to understand before working with Git.

| Term | Definition |
| --- | --- |
| Working Tree | The project directory containing all the files and folders you are currently working on. |
| Repository (Repo) | The database where Git stores project history and metadata. Located in the hidden `.git` directory. |
| Bare Repository | A repository without a working tree, commonly used for sharing or backups. |
| Hash | A unique identifier generated from data using a hash function. Git uses hashes to identify objects and detect changes. |
| Object | A data structure stored in Git. There are four main types: Blob, Tree, Commit and Tag. |
| Commit | A snapshot of the project at a particular point in time, recording changes in the repository history. |
| Branch | An independent line of development that allows changes to be made without affecting other branches. |
| HEAD | A reference indicating the current position in the repository, normally the latest commit of the current branch. |
| Remote | A reference to another Git repository, usually hosted on a remote server. |
| Origin | The default name Git assigns to the remote repository when cloning a project. |

### Git Objects

Git stores information using four main object types:

| Object | Purpose |
| --- | --- |
| Blob | Stores the contents of a file. |
| Tree | Represents a directory, storing filenames, permissions and references to other objects. |
| Commit | Represents a snapshot of the project and connects it to the repository history. |
| Tag | Stores metadata associated with a specific version, usually pointing to a commit. |

### Understanding Hashes

Git uses hash functions to generate identifiers for objects.

- Traditionally, Git uses SHA-1 (160 bits).
- Modern Git also supports SHA-256 (256 bits).
- Hashes help Git identify objects and detect changes in file contents.

Important: If a file's timestamp changes but its contents remain identical, its content hash remains the same.

## 4. Branches and Commits

Branches are one of Git's most important features.

A branch allows developers to work on different features, bug fixes or experiments independently.

Example:

- `main`: The main development branch.
- `feature-login`: A branch for developing a login system.
- `bug-fix`: A branch for fixing an existing problem.

Once the work is complete, changes can be combined using a process called merging.

!image.png

Important terminology:

- **Commit:** Saves a snapshot of your changes in the repository.
- **HEAD:** Points to the current position in the repository.
- **Main:** The default branch on GitHub and many other platforms.
- **Merge:** Combines changes from different branches.
- **Tag:** Identifies a particular version, for example `v1.0`.

## 5. The Git Command Line (CLI)

Git can be used through different graphical interfaces (GUIs), such as:

- GitHub Desktop.
- Visual Studio Code.
- Other Git-compatible applications.

However, the Command Line Interface (CLI) is particularly important.

Advantages of using the CLI:

1. Provides access to all Git functionality.
2. Works consistently across Windows, Linux and macOS.
3. Helps troubleshoot errors that graphical interfaces might not expose clearly.
4. Develops practical skills commonly required in IT and software development.

Recommendation: Learn Git commands directly through the terminal, even if you also use Visual Studio Code or GitHub Desktop.

## 6. Git vs. GitHub

Although they are closely related, Git and GitHub are not the same thing.

!image.png

Git

A distributed version control system that tracks changes and manages repositories.

!image.png

GitHub

A cloud-based platform that uses Git to host repositories and facilitate collaboration.

| Git | GitHub |
| --- | --- |
| Version control software. | Online collaboration platform. |
| Manages local repositories. | Hosts remote repositories. |
| Tracks changes and commits. | Provides tools for teamwork and project management. |
| Works offline. | Requires internet for its online services. |

### Main GitHub Features

- **Issues:** Track bugs, tasks and improvements.
- **Discussions:** Communicate and exchange ideas.
- **Pull Requests:** Propose and review changes before merging them.
- **Notifications:** Receive updates about repository activity.
- **Labels:** Categorize issues and pull requests.
- A**ctions:** Automate workflows, testing and deployment (CI/CD).
- **Forks:** Create your own copy of another repository.
- **Projects:** Organize and manage tasks.
- **Copilot:** AI-powered coding assistant.
- **Codespaces:** Cloud-based development environments.

## 7. Key Takeaways – What You Must Remember

These are the most important concepts from this unit:

1. **VCS:** Tracks changes and allows you to recover previous versions of a project.
2. **Git:** A distributed version control system.
3. **Distributed:** Every developer has a complete local repository history.
4. **Repository:** Stores project history and metadata.
5. **Commit:** Records a snapshot of the project.
6. **Branch:** Allows independent development.
7. **Merge:** Combines changes from different branches.
8. **Remote:** References another repository.
9. **Origin:** Default remote name when cloning a repository.
10. **GitHub:** An online platform for hosting Git repositories and collaborating.

Remember: Git is the version control system; GitHub is a platform built around Git.

## 8. Knowledge Check

Test your understanding before moving to the next unit.

Unit 2 Quiz

1.What is the main purpose of a Version Control System?

- [ ]  To compile source code
- [x]  To track and manage changes to files
- [ ]  To host websites

2.What makes Git a distributed VCS?

- [ ]  It requires a central server for every operation
- [x]  Every developer has a complete local repository history
- [ ]  It only works online

3.Where does Git store repository history and metadata?

- [x]  In the .git directory
- [ ]  In the main branch
- [ ]  In GitHub Issues

4.What is a branch used for?

- [ ]  Deleting old commits
- [x]  Creating independent lines of development
- [ ]  Uploading files to GitHub

5.What is the difference between Git and GitHub?

- [ ]  They are exactly the same
- [x]  Git is a VCS; GitHub is a hosting and collaboration platform
- [ ]  GitHub is a programming language
