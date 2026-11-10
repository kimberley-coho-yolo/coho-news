# One-time setup (about 45 minutes, $0)

Everything below is done in a web browser. Hosting is GitHub Pages (free), and the question form is Google Forms now, switching to Microsoft Forms once the Microsoft 365 tenant is live.

## 1. Create the GitHub account (10 min)

1. Go to github.com and sign up using a **shared work mailbox** (e.g. it-admin@…), not a personal address, so the site doesn't leave with any one person.
2. Turn on two-factor sign-in: **Settings → Password and authentication → Enable two-factor authentication**. Use an authenticator app or a passkey. Save the recovery codes somewhere safe (password manager).
3. Optional but recommended: create a free **Organization** (top-right **+ → New organization → Free**) called something like `cohogroup`, and add one backup owner (e.g. your IT contractor) so you're never locked out.

## 2. Upload the site (10 min)

1. Click **+ → New repository**. Name: `coho-news`. Owner: your organization. Visibility: **Public** (free Pages needs this; see "What's visible" below). Click **Create repository**.
2. On the new empty repository page, click **uploading an existing file**.
3. Unzip `coho-news-site.zip` on your computer, open the `coho-news` folder, select **everything inside it** (including the `_layouts`, `_posts`, `_drafts` and `assets` folders) and drag it into the browser.
4. Click **Commit changes**.

## 3. Turn on the website (5 min)

1. In the repository, go to **Settings → Pages**.
2. Under **Build and deployment**, Source: **Deploy from a branch**. Branch: **main**, folder **/ (root)**. Click **Save**.
3. Wait 1 to 2 minutes and refresh. The page shows your address, e.g. `https://cohogroup.github.io/coho-news/`.
4. Because that address ends in `/coho-news/`, open `_config.yml`, click the pencil, set `baseurl: "/coho-news"`, and commit. (Skip this if you set up a custom address in step 5.)
5. Tick **Enforce HTTPS** once it becomes available.

## 4. Lock it down (5 min)

In the repository **Settings**:

- **General → Features:** untick Wikis, Issues, Discussions and Projects (fewer places for anyone to post).
- **Collaborators / Members:** only you and your backup owner should have write access. Members of the public can view files but **cannot change anything**.
- **Branches → Add branch ruleset** (optional): block force pushes and deletion on `main`. This means history can never be wiped.
- **Code security:** leave Dependabot alerts on.

## 5. Optional: a nicer address like news.cohogroup.com (free)

Once DNS admin access for cohogroup.com is confirmed (it's on the migration plan):

1. Ask whoever manages DNS to add a **CNAME** record: `news` → `cohogroup.github.io` (use your organization or username).
2. In **Settings → Pages → Custom domain**, enter `news.cohogroup.com`, Save, then tick **Enforce HTTPS**.
3. In `_config.yml`, set `baseurl: ""`.
4. Also **verify the domain** for your organization (**Organization settings → Pages → Add a domain**). This stops anyone else claiming the subdomain.

## 6. Set up the question form (10 min)

**Now (still on Google):**

1. Create a Google Form with: Name (optional), Site or department (optional), Your question (required).
2. **Settings → Responses:** turn off "Restrict to users in Coho Group" so drivers without a company login can answer. Turn off collecting email unless you want it.
3. **Responses tab → three dots → Get email notifications for new responses.**
4. Click **Send → `< >`** (embed), copy just the link inside `src="…"`. Paste it into `form_embed_url` in `_config.yml`. Paste the normal share link into `form_link_url`. Commit.

**After the Microsoft 365 tenant is ready (from Feb 2027):** rebuild the same form in Microsoft Forms, set **Who can fill out this form → Anyone can respond**, use **Collect responses → Embed** for the link, and swap the two links in `_config.yml`. Responses then live inside your own tenant.

## 7. Send the link to staff

Email the address, put a QR code on depot noticeboards, and add the link to the driver app.

---

## What's visible, and what's protected

| | |
|---|---|
| **Can anyone change the site?** | No. It's a static site: there's no login page, database or admin panel on it to attack. Changes only come through your GitHub account, protected by two-factor sign-in. |
| **Can anyone read it?** | Anyone with the link. It's hidden from search engines, but not password-protected. The source files on GitHub are also publicly viewable. |
| **So, what not to post** | Costs and budgets, supplier names under negotiation, people's personal details, and details of how our security is configured. Post what staff need to know and do. |
| **Where do form answers go?** | Into your Google (later Microsoft) account, not the website, so nothing sensitive is stored on the site. |
| **If something goes wrong** | Every change is recorded. Open the file → **History** to see who changed what, and restore an earlier version. |

Add the site and the GitHub account to the application register, so it's covered by the ISO 27001 asset inventory.
