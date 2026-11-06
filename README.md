# Links

A personal page of website shortcuts. Add or delete links in the browser and they
are saved to `links.json` in this repo, so the same list appears on every device.

## How it works

- `index.html` — the page. It reads `links.json` from GitHub on load and shows the list.
- `links.json` — the single source of truth for the links.

When you add or remove a link, the page commits the updated `links.json` straight
back to this repository using the GitHub API, so no manual file uploads are needed.
Any other device that opens the page fetches the latest `links.json` and shows the
same list.

## One-time setup (per device)

Saving requires a GitHub token, which is stored only in that browser:

1. Open the page and expand **⚙ GitHub sync setup**.
2. Create a fine-grained token at
   [github.com/settings/personal-access-tokens/new](https://github.com/settings/personal-access-tokens/new):
   - Repository access: **Only select repositories** → `jqw22/links`
   - Repository permissions: **Contents → Read and write** (nothing else)
   - Pick an expiry; when it runs out, saves fail with "token is invalid or expired"
     and you just create a new one and paste it in.
3. Paste the token and click **Save settings**.

Owner (`jqw22`), repo (`links`), branch (`main`) and path (`links.json`) are
pre-filled. The token is never sent anywhere except GitHub.

Without a token the page still works as a viewer, and edits are kept in the
browser only (with a **Download backup** option) until a token is added.

## Editing

Click **Edit Links** to show the add/delete controls, and **Done Editing** when
finished. In edit mode each heading has a **Rename** button; renaming a heading
moves its links to the new name and saves like any other change. Renaming to an
existing heading's name merges the two. Headings are listed A to Z. Use **↻ Reload from GitHub** to pull the latest list.
