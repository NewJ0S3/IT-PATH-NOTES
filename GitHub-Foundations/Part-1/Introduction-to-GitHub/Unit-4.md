# GitHub Is a Collaborative Platform

## 1. Introduction

Collaboration is one of GitHub's core principles. It provides tools that help developers organize projects, track changes, solve problems, and communicate with other contributors.

Two important collaboration features are:

- **GitHub Issues:** Used to track tasks, bugs, ideas, and feedback that require attention or action.
- **GitHub Discussions:** Used for questions, announcements, ideas, and general conversations within a project community.

The main difference is that Issues focus on **actionable work**, while Discussions focus on **communication and knowledge sharing**.

## 2. GitHub Issues

**GitHub Issues** are used to track and manage work related to a repository.

They help teams organize:

- Bugs and errors.
- New features and improvements.
- Tasks and project activities.
- Feedback and suggestions.
- Questions that require investigation or action.

### Creating an Issue

Issues can be created from several places:

- A repository.
- An item in a task list.
- A note in a project.
- A comment in an Issue or Pull Request.
- A specific line of code.
- A URL query.

### Creating an Issue from a repository

1. Navigate to the repository on GitHub.
2. Open the **Issues** tab.
3. Select **New issue**.
4. Choose an issue template or select **Blank issue**.
5. Enter a descriptive title.
6. Write a clear description of the problem or task.
7. Optionally assign users, add labels, associate milestones, or add the Issue to a project.
8. Select **Submit new issue**.

### Issue templates and forms

- **Issue templates:** Provide a predefined structure to help contributors report information consistently.
- **Issue forms:** Use structured fields to collect specific information in a standardized format.

### Managing Issues

GitHub provides several tools to improve Issue organization and collaboration:

- **Labels:** Categorize Issues by type, priority, or purpose.
- **Assignees:** Identify the person responsible for an Issue.
- **Milestones:** Group Issues according to project goals or deadlines.
- **Projects:** Organize and track Issues using project boards.
- **Mentions:** Notify specific contributors using `@username`.
- **Reactions:** Express feedback or acknowledge comments.

**Important:** Issues are not limited to bugs. They can represent any task or piece of work that needs to be tracked.

## 3. GitHub Discussions

**GitHub Discussions** is a collaborative forum for conversations that are not necessarily connected to specific code changes or actionable tasks.

They are useful for:

- Asking and answering questions.
- Sharing ideas and suggestions.
- Publishing announcements.
- Collecting community feedback.
- Sharing experiments and projects.
- Discussing general topics related to a repository.

Discussions can be public or private, depending on the visibility of the repository.

### Enabling Discussions

Repository owners and users with **Write access** can enable Discussions.

Steps:

1. Open the repository on GitHub.
2. Navigate to **Settings**.
3. Find the **Features** section.
4. Under Discussions, select **Setup discussions**.
5. Customize the welcome post to match the community.
6. Select **Start discussion**.

### Creating a Discussion

Any authenticated user who can view the repository can create a Discussion.

Steps:

1. Open the repository or organization.
2. Navigate to the **Discussions** tab.
3. Select **New discussion**.
4. Choose a category by selecting **Get started**.
5. Enter a title and write the discussion content.
6. Select **Start discussion**.

Every Discussion must belong to a category. Categories help organize conversations according to their purpose.

### Default Discussion Categories

| Category | Purpose | Format |
| --- | --- | --- |
| **Announcements** | Updates and news from maintainers. | Announcement |
| **General** | General topics related to the project. | Open-ended |
| **Ideas** | Suggestions for improvements or new features. | Open-ended |
| **Polls** | Collect community opinions through voting. | Poll |
| **Q&A** | Questions and answers from the community. | Question and Answer |
| **Show and tell** | Share projects, experiments, and creations. | Open-ended |

Repository maintainers can customize categories and pin important Discussions to make them more visible.

## 4. Managing Discussions

GitHub provides additional features to organize conversations and make useful information easier to find.

### Marking a comment as an answer

In a Q&A Discussion, the original author or someone with the appropriate permissions can mark a comment as the accepted answer.

This highlights the solution so other users can find it quickly.

An accepted answer can also be unmarked if necessary.

### Referencing a Discussion in a new Issue

Sometimes a conversation leads to a task that needs to be completed.

Instead of losing that information in a Discussion, you can convert it into an actionable Issue.

Steps:

1. Open the Discussion.
2. Select the three-dot (`...`) menu.
3. Choose **Reference in new issue**.
4. Confirm the Issue title and description.

This connects community conversations with trackable project work.

### Pinning a Discussion

Maintainers can pin important Discussions to the top of the Discussions page.

Pinned Discussions are useful for highlighting:

- Important announcements.
- Frequently asked questions.
- Relevant community information.
- Ongoing conversations.

To pin a Discussion:

1. Open the Discussion.
2. Select the three-dot (`...`) menu.
3. Choose **Pin discussion**.

## 5. GitHub Issues vs. GitHub Discussions

Understanding when to use each feature is essential for effective collaboration.

| Feature | GitHub Issues | GitHub Discussions |
| --- | --- | --- |
| Main purpose | Track and manage work. | Communicate and share information. |
| Typical use | Bugs, tasks, improvements. | Questions, ideas, announcements. |
| Structure | Action-oriented. | Conversation-oriented. |
| Organization | Labels, assignees, milestones, projects. | Categories and pinned discussions. |
| Expected outcome | A task that can be addressed or completed. | Knowledge sharing or community interaction. |

### When should you use each one?

**Use Issues when:**

- You find a bug that needs fixing.
- You want to implement a new feature.
- You need to track a specific task.
- You want to organize improvements to a project.

**Use Discussions when:**

- You want to ask a general question.
- You want feedback about an idea.
- You want to announce something.
- You want to share knowledge or discuss a topic.

**Key takeaway:**

Issues track work that needs attention. Discussions provide a space for communication and collaboration.

A Discussion can also lead to an Issue when a conversation identifies something that needs to be implemented or fixed.

---

## Unit 4 — Knowledge Check

Test your understanding before checking the answer key.

### Questions

**1. What is the primary purpose of GitHub Issues?**

- [ ]  A) Hosting websites.
- [x]  B) Tracking bugs, tasks, ideas, and feedback.
- [ ]  C) Managing user passwords.
- [ ]  D) Creating Git branches.

**2. Which of the following is NOT a typical way to create an Issue?**

- [ ]  A) From a repository.
- [ ]  B) From a comment in a Pull Request.
- [ ]  C) From a specific line of code.
- [x]  D) By merging a branch automatically.

**3. What is the purpose of an Issue template?**

- [ ]  A) To delete outdated Issues.
- [x]  B) To provide a predefined structure for reporting information.
- [ ]  C) To automatically assign every Issue to a developer.
- [ ]  D) To create a new repository.

**4. What is the difference between Issue templates and Issue forms?**

- [x]  A) Templates provide predefined content, while forms collect information through structured fields.
- [ ]  B) Templates are private, while forms are public.
- [ ]  C) Templates track commits, while forms track branches.
- [ ]  D) There is no difference.

**5. What is the main purpose of GitHub Discussions?**

- [ ]  A) Managing code commits.
- [ ]  B) Merging branches.
- [x]  C) Providing a space for questions, ideas, announcements, and conversations.
- [ ]  D) Tracking every modification to a file.

**6. Which permission is required to enable Discussions in a repository?**

- [ ]  A) Read access only.
- [x]  B) Write access or repository ownership.
- [ ]  C) No authentication is required.
- [ ]  D) Administrator access to GitHub itself.

**7. Which Discussion category is designed for questions and answers?**

- [ ]  A) General.
- [ ]  B) Ideas.
- [ ]  C) Polls.
- [x]  D) Q&A.

**8. What happens when a comment is marked as an answer in a Q&A Discussion?**

- [ ]  A) The entire Discussion is deleted.
- [x]  B) The comment is highlighted as the accepted answer.
- [ ]  C) A new branch is created.
- [ ]  D) The comment becomes a Pull Request.

**9. What is the purpose of pinning a Discussion?**

- [ ]  A) To permanently close the Discussion.
- [ ]  B) To move it to the Issues tab.
- [x]  C) To make important conversations more visible at the top of the Discussions page.
- [ ]  D) To prevent users from commenting.

**10. What should you do if a Discussion identifies a task that needs to be completed?**

- [ ]  A) Delete the Discussion.
- [x]  B) Convert or reference it in a new Issue.
- [ ]  C) Create a new repository.
- [ ]  D) Close all related Pull Requests.
