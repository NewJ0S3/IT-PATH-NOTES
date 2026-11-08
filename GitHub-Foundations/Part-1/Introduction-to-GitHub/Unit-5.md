# GitHub Platform Management

## 1. Introduction

GitHub provides platform management features that help users stay informed about repository activity, manage notifications, and publish websites.

This unit covers three main topics:

- **Notifications and subscriptions:** Control which repository activities generate notifications.
- **Threads and mentions:** Follow specific conversations and find discussions where you're mentioned.
- **GitHub Pages:** Publish static websites directly from a GitHub repository.

## 2. Managing Notifications and Subscriptions

**GitHub Notifications** keep users informed about important activity across repositories and teams.

You can subscribe to notifications for:

- Specific Issues, Pull Requests, or Gists.
- Repository activity, including Issues, Pull Requests, Releases, and Discussions.
- GitHub Actions workflow statuses.
- All activity within a repository.

### Automatic subscriptions

GitHub automatically subscribes you to certain conversations when you interact with them.

For example, you may become subscribed when you:

- Comment on an Issue or Pull Request.
- Open an Issue.
- Get assigned to a conversation.

You can also manually subscribe or unsubscribe from conversations depending on your interests.

### Managing subscriptions

GitHub provides several options to control repository notifications:

- **Subscribe:** Receive updates about a specific conversation.
- **Unsubscribe:** Stop receiving updates about a specific conversation.
- **Watch settings:** Control which activities generate repository notifications.
- **Custom settings:** Select specific activity types to follow.

Managing subscriptions helps reduce unnecessary notifications and keeps your attention on relevant work.

## 3. Subscribing to Threads and Finding Mentions

A **thread** is a conversation associated with an Issue, Pull Request, or Discussion.

You can subscribe to a thread even if you were not originally involved in the conversation.

### Subscribing to a thread

To follow a specific conversation:

1. Open the Issue, Pull Request, or Discussion.
2. Locate the right-hand sidebar.
3. Select **Subscribe**.

You will receive notifications when new activity occurs in that thread.

### Finding mentions

GitHub allows you to search for conversations where a specific user has been mentioned.

Use the search qualifier:

```git
mentions:username
```

Replace `username` with the GitHub username you want to search for.

For example:

```git
mentions:NewJ0S3
```

This helps locate Issues and Pull Requests where that user has been mentioned with an `@username` reference.

## 4. Filtering Notifications

GitHub provides different repository watch settings to control how many notifications you receive.

| Setting | Description |
| --- | --- |
| **Watching** | Receive notifications for all activity in the repository. |
| **Not watching** | Receive notifications mainly when you participate or are mentioned. |
| **Ignore** | Stop receiving notifications from the repository. |
| **Custom** | Choose specific activity types to receive notifications about. |

You can access these options by selecting **Watch** at the top of a repository page.

**Important:** Watching a repository provides broader notifications, while not watching limits notifications to conversations involving you.

## 5. Configuring Notification Delivery

GitHub allows you to choose where notifications are delivered.

### Notification channels

| Channel | Description |
| --- | --- |
| **Email** | Notifications are sent to your registered email address. |
| **Web** | Notifications appear in your GitHub dashboard. |
| **Mobile** | Push notifications are delivered through the GitHub mobile app. |
| **Custom notifications** | Configure specific notification events and delivery preferences. |

### Configuring notification settings

To manage your notification preferences:

1. Open your GitHub profile menu.
2. Navigate to **Settings**.
3. Select **Notifications**.
4. Configure your preferred notification channels and delivery options.

These settings help you control how and where GitHub communicates repository activity.

## 6. GitHub Pages

**GitHub Pages** is a static website hosting service that allows you to publish websites directly from a GitHub repository.

It can be used to create websites for:

- Personal portfolios.
- Organizations.
- Software projects.
- Documentation.
- Project landing pages.

### How GitHub Pages works

GitHub Pages takes website files from a repository and publishes them online.

It supports:

- **HTML:** Defines the structure and content of a website.
- **CSS:** Controls the website's appearance and layout.
- **JavaScript:** Adds interactivity and dynamic behavior.

Optionally, you can use a build process to generate the website before publication.

### Publishing a website

GitHub Pages allows you to specify:

- **Source branch:** The branch containing the website files.
- **Source folder:** The directory containing the files, such as `/docs`.

GitHub then hosts the published website, making it accessible through a public URL.

**Important:** GitHub Pages is designed for static websites. It does not directly run server-side applications or backend code such as Python, PHP, or Node.js.

### Practical uses for an IT student

GitHub Pages can be useful for:

- Creating an online IT portfolio.
- Publishing technical documentation.
- Presenting projects from your GitHub repositories.
- Sharing learning resources and study notes.
- Demonstrating HTML, CSS, and JavaScript skills.

## 7. Unit 5 — Key Concepts Review

| Concept | Main purpose |
| --- | --- |
| Notifications | Keep users informed about repository activity. |
| Subscriptions | Follow specific conversations or repository events. |
| Watching | Receive notifications for all repository activity. |
| Not watching | Receive notifications mainly for participation and mentions. |
| Ignore | Stop receiving repository notifications. |
| Custom | Select which activities generate notifications. |
| Mentions search | Find Issues and Pull Requests where a user is mentioned. |
| GitHub Pages | Host static websites directly from a GitHub repository. |

**Key takeaway:**

- Notifications help you stay informed.
- Subscriptions let you control which conversations you follow.
- Watch settings help manage notification volume.
- GitHub Pages allows you to publish static websites using repository files.
