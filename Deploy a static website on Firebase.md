
---
## What is Firebase?

Firebase is an app development platform that provides various tools and services to help you develop high-quality apps, grow your user base, and earn more money. Here are some of the key services offered by Firebase:

### Services for Development

- **Realtime Database**: Store and sync data in real-time.
- **Authentication**: Reduce friction with robust authentication.
- **Cloud Messaging**: Deliver and receive messages across platforms.
- **Storage**: Store files with ease.
- **Hosting**: Deliver web content faster.
- **Test Lab**: Test in the lab, not on the users.
- **Crash Reporting**: Keep your app stable.

## Getting Started with Firebase

1. Go to the [Firebase Console](https://console.firebase.google.com).
2. Create a project on the Firebase Console.
3. Install Firebase Tools on your system:
   - Install Node.js from [nodejs.org](https://nodejs.org/en/download/).
   - Open the command prompt by pressing `Ctrl + R`, then typing `cmd`.
   - Run the command: `npm install -g firebase-tools`.
   - This should install Firebase Tools on your machine.

## Logging In, Choosing a Project, and Setting the Path

1. Open the command prompt.
2. Create a separate folder at your preferred location on your computer and navigate to this folder using the `cd` command.
3. When you are in the correct directory, run the command: `firebase login` and log in using the same email with which you created the Firebase project.
4. Run the command: `firebase init`
   - Choose the service as Hosting (optionally with Git) - use the spacebar to select and press Enter to move further.
   - Choose an existing project and select the relevant project created in step 1.
   - For the public folder, keep it by default as `public`.
   - Keep other options as default.

## Making Your Website Live

1. Move your correct files to the same directory where Firebase was initialized in the last step.
2. Run the command: `firebase deploy`.

---

