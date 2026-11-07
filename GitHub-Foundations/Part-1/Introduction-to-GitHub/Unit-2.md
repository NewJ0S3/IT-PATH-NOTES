# 1. What is GitHub?

GitHub is a cloud-based developer platform built around Git, a distributed version control system.

Git manages project versions and tracks changes, while GitHub provides tools for hosting repositories, collaboration, automation and software development.

GitHub's platform is built around five main pillars:

## The five pillars of GitHub Enterprise

| Pillar | Description | Main features |
| --- | --- | --- |
| AI | Integrates artificial intelligence into software development. | Copilot, Copilot Chat, Copilot Agents. |
| Collaboration | Helps developers work together efficiently. | Repositories, Issues, Pull Requests. |
| Productivity | Automates repetitive tasks and development workflows. | CI/CD, automation. |
| Security | Integrates security throughout the development process. | CodeQL, Secret Scanning, Dependabot. |
| Scale | Supports a large developer community and scalable projects. | Open-source contributions, enterprise development. |

Important terminology:

- CI/CD (Continuous Integration / Continuous Delivery): Practices and automation tools that help integrate, test and deliver software.
- CodeQL: A code analysis tool used to identify security vulnerabilities.
- Dependabot: Helps identify and update vulnerable or outdated dependencies.
- Secret Scanning: Detects exposed credentials, API keys and other secrets.

## . What is a Repository?

A Repository (Repo) is a storage location containing all the files of a project and their revision history.

Repositories allow developers to:

- Store project files.
- Track changes over time.
- Manage different versions.
- Collaborate with other developers.
- Organize and document projects.

### Creating a Repository

To create a repository on GitHub:

1. Navigate to GitHub.com.
2. Select the `+` menu in the upper-right corner.
3. Choose New repository.
4. Select the repository owner (personal account or organization).
5. Enter a repository name and optional description.
6. Choose its visibility.
7. Select Create repository.

### Repository Visibility

| Type | Description |
| --- | --- |
| Public | Accessible to everyone on the internet. |
| Private | Accessible only to you and people you explicitly grant access to, subject to organization permissions. |

Important: Public repositories are useful for portfolios and open-source projects. Private repositories are useful for projects that should have restricted access.

## 3. How to Clone a Repository

Cloning means creating a local copy of a remote repository on your computer.

This allows you to work locally and synchronize your changes with GitHub.

### Steps to clone a repository

1. Open the repository on GitHub.
2. Select the Code button.
3. Copy the repository URL using HTTPS, SSH or GitHub CLI.
4. Open your terminal.
5. Navigate to the directory where you want to save the repository.
6. Execute:

```git
git clone <repository-url>
```

7.Enter the repository directory:

```git
cd <repository-name>
```

Example:

```git
git clone https://github.com/user/project.git

cd project
```

Key takeaway: `git clone` downloads the repository and its history, creating a local copy that you can work with.

## 4. How to Add Files to a Repository

You need at least Write access to add files to a repository.

GitHub allows you to create new files or upload existing ones directly through its website.

### Steps to create a new file

1. Navigate to your repository.
2. Select Add file.
3. Choose Create new file.
4. Enter the filename and extension.
5. Add the file contents.
6. Use Preview to review the content.
7. Select Commit changes.

### Understanding Commit Changes

When committing a new file, GitHub asks you to:

- Commit message: Write a short description explaining the changes.
- Branch selection: Choose whether to commit to the current branch or create a new one.

If working on the default branch, the course recommends creating a new branch and then opening a Pull Request.

You can finish by selecting:

- Commit changes: Save the changes directly.
- Propose changes: Create a proposed change through a new branch and Pull Request workflow.

Remember: A commit records your changes in the repository history.

## 5. What are Gists?

Gists are a GitHub feature that allows users to share small pieces of code, notes, scripts or configuration files.

They work like lightweight Git repositories, supporting version control, cloning and forking.

### Types of Gists

| Type | Description |
| --- | --- |
| Public Gist | Visible to everyone and discoverable through GitHub search. |
| Secret Gist | Not publicly listed or searchable, but accessible to anyone who has its URL. |

Security warning

Secret Gists are NOT completely private. Never store passwords, API keys, tokens or other sensitive information in them.

### Main Features of Gists

- Version Control: Tracks changes and allows you to review previous versions.
- Forking: Creates a copy of another user's Gist.
- Cloning: Downloads a local copy to your computer.
- Embedding: Allows code snippets to be embedded into websites and blogs.
- Markdown Support: Supports formatted text, headings, links and images.
- Collaboration: Allows sharing, commenting and forking.

### Common Use Cases

- Sharing code snippets and quick solutions.
- Storing configuration files.
- Sharing scripts and templates.
- Documenting errors and debugging information.
- Providing examples in tutorials.

### Cloning a Gist

``` git
git clone https://gist.github.com/your-gist-id.git
```

When should you use a Gist instead of a Repository?

- Gist: Small snippets, scripts and individual files.
- Repository: Complete projects with multiple files, folders and documentation.

## 6. What are Wikis?

A Wiki is a documentation section available within GitHub repositories.

It allows developers to create and maintain detailed documentation about their projects.

### Wiki vs. README

| README | Wiki |
| --- | --- |
| Provides a quick introduction to the project. | Provides more detailed documentation. |
| Usually explains what the project does and how to get started. | Explains how the project works, its design and principles. |
| Located in the repository. | Available through the repository's Wiki tab. |

### Managing Wiki Pages

Creating a page:

1. Navigate to the repository.
2. Select the Wiki tab.
3. Select Create the first page or New Page.
4. Enter a title and content.
5. Select Save Page.

Editing a page:

1. Open the Wiki page.
2. Select Edit.
3. Modify its content.
4. Select Save Page.

Deleting a page:

Unlike creating or editing, deleting a Wiki page requires using Git:

1. Clone the Wiki repository.
2. Remove the corresponding file.
3. Push the changes.

Important: If the main repository is private, its Wiki is accessible only to people with at least Read access.

## 7. What are Feature Previews?

Feature Previews allow GitHub users to test experimental features before their official release.

They provide early access to new functionality and allow users to provide feedback.

### How to enable or disable Feature Previews

1. Navigate to your GitHub profile.
2. Open the profile dropdown menu.
3. Select Feature preview.
4. Browse the available experimental features.
5. Enable or disable the features you want to test.

## 8. Key Takeaways – What You Must Remember

These are the most important concepts from Unit 2:

| Concept | What to remember |
| --- | --- |
| GitHub | Cloud-based platform built around Git. |
| Repository | Stores project files and revision history. |
| Public Repository | Accessible to everyone. |
| Private Repository | Access restricted to authorized users. |
| Clone | Creates a local copy of a repository. |
| Write Access | Permission required to add or modify repository files. |
| Commit Message | Describes the changes recorded in a commit. |
| Gist | Lightweight repository for sharing small code snippets and files. |
| Fork | Creates your own copy of another repository or Gist. |
| Wiki | Provides detailed project documentation. |
| Feature Preview | Allows testing experimental GitHub features. |
| CI/CD | Automates software integration, testing and delivery. |

## 9. Knowledge Check

Test your understanding before moving to the next unit.

1.What is GitHub?

- [ ]  A programming language
- [x]  A cloud-based platform built around Git
- [ ]  A centralized version control system

2.What is a repository?

- [ ]  A tool for writing code
- [x]  A storage location containing project files and revision history
- [ ]  A type of Git branch

3.What command creates a local copy of a remote repository?

- [ ]  git push
- [ ]  git commit
- [x]  git clone

4.Are Secret Gists completely private?

- [ ]  Yes, only the owner can access them
- [x]  No, anyone with the URL can access them
- [ ]  Yes, they are encrypted automatically

5.What is the main purpose of a GitHub Wiki?

- [ ]  Hosting executable applications
- [ ]  Storing passwords
- [x]  Providing detailed project documentation

6.What does Dependabot help with?

- [x]  Identifying and updating vulnerable or outdated dependencies
- [ ]  Creating repository branches
- [ ]  Writing project documentation

7.What is a Feature Preview?

- [ ]  A repository backup
- [x]  Early access to experimental GitHub features
- [ ]  A Git commit
