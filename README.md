# Chess Trainer on GitHub Pages

GitHub Pages hosts the page for free. Online play (usernames, ratings, leaderboards, live games) uses Google Firebase's free plan, since GitHub Pages can only serve files. Everything else (puzzles, training, analysis, play vs computer) works even before you set up Firebase.

Setup takes about 10 minutes. You need a GitHub account and a Google account.

## 1. Put the page on GitHub Pages

1. On github.com, click **New repository**. Name it, for example `chess-trainer`, make it **Public**, and create it.
2. Click **Add file → Upload files**, drag in `index.html`, `firebase-config.js`, `firestore.rules` and this README, then click **Commit changes**.
3. Go to **Settings → Pages**. Under "Build and deployment", set Source to **Deploy from a branch**, Branch to **main** and folder to **/ (root)**, then click **Save**.
4. After a minute your site is live at `https://YOUR-USERNAME.github.io/chess-trainer/`.

## 2. Turn on online play with Firebase

1. Go to https://console.firebase.google.com and click **Create a project** (you can turn off Google Analytics).
2. On the project page, click the **</>** (Web) icon to add a web app. Give it any nickname and click **Register app**. You'll see a `firebaseConfig` block with `apiKey`, `authDomain`, `projectId` and so on.
3. On GitHub, open `firebase-config.js`, click the pencil icon to edit it, copy those values into the matching lines, and commit.
4. In Firebase, go to **Build → Authentication → Get started → Sign-in method**, choose **Anonymous**, turn it on and save.
5. Still in Authentication, open **Settings → Authorized domains** and add `YOUR-USERNAME.github.io`.
6. Go to **Build → Firestore Database → Create database**. Pick a location near you and start in **production mode**.
7. Open the **Rules** tab, replace everything with the contents of `firestore.rules`, and click **Publish**.

Reload your site, go to **Online**, pick a username, and share the link with friends.

## Good to know

- The Firebase values in `firebase-config.js` are meant to be public. The rules you published are what protect the data: players can only change their own profile and rating, and only the two players in a game can change it.
- Each browser is signed in anonymously and remembers you. If someone clears their browser data, they get a new account and need a new username.
- Ratings are worked out by each player's own browser, so a determined cheater could change theirs. For a game between friends that's fine.
- Firebase's free plan has daily limits (about 50,000 reads a day). That's plenty for a group of friends; you'd only need to think about it with many players online all day.
- To update the page later, upload the new `index.html` over the old one. Keep your edited `firebase-config.js`.
