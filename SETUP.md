# Putting the Christmas list online

The page runs on GitHub Pages. Gift reservations and family wishes are saved in
Firebase, Google's free database, so nobody needs an account to use the page.

## Part 1: Firebase (about 10 minutes)

1. Go to https://console.firebase.google.com and sign in with your Google account.
2. Click **Create a project**, name it something like `christmas-list`, and turn **off** Google
   Analytics (you don't need it). Click through to finish.
3. In the left menu, open **Build → Realtime Database** and click **Create Database**.
   Pick the location closest to you, choose **Start in locked mode**, and click **Enable**.
4. Open the **Rules** tab, delete everything there, paste in the whole contents of
   `database.rules.json` from this folder, and click **Publish**.
5. Click the gear icon next to **Project Overview** → **Project settings**. Under **Your apps**,
   click the web icon `</>`, give it any nickname, leave Hosting unticked, and click **Register app**.
6. Firebase shows a block that starts with `const firebaseConfig = {`. Copy everything from
   `{` to the matching `}`.
7. Open `index.html`, find the line `FIREBASE SETUP`, and replace the `firebaseConfig` object
   below it with what you copied. Make sure it has a `databaseURL` line. If it doesn't, copy the
   URL shown at the top of the Realtime Database **Data** tab and add it:
   `databaseURL: "https://....firebasedatabase.app",`

The `apiKey` in that config is safe to publish. It only identifies your project; the rules
from step 4 decide what people can change.

## Part 2: Update the live site

The site is live at https://superchariv.github.io/Christmas-Website/. After you paste the
Firebase config into `index.html`, upload the new `index.html` to the GitHub repository
(**Add file → Upload files**, then **Commit changes**). The live page updates within a couple
of minutes.

## Good to know

- Anyone with the link can reserve a gift by typing their name. Everyone sees who reserved it.
  Two people can't reserve the same gift. If someone tries to unreserve a gift that a different
  person reserved, the page asks them to confirm first.
- The page is public, so anyone with the link can see it. You'll also see what's been reserved
  and by whom, so look away if you want surprises.
- People can only remove wishes they added from the same phone or computer.
- To clear everything after Christmas, open the Realtime Database **Data** tab in Firebase and
  delete `taken` and `wishes`.
