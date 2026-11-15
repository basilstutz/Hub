# Basil Stutz – private hub

A personal hub hosted on GitHub Pages. The movie list is stored **encrypted** in
`data.enc.json`. Without the password, the site and this repository only show
unreadable data, so the repository can safely be public.

## Setup (about 10 minutes)

### 1. Create the repository
1. On GitHub, click **New repository**.
2. Name it, for example, `hub`. **Public** works on the free plan because the data is encrypted.
3. Upload `index.html` (and this README) and commit.

### 2. Turn on GitHub Pages
1. In the repository, open **Settings → Pages**.
2. Under *Build and deployment*, choose **Deploy from a branch**, branch `main`, folder `/ (root)`, then **Save**.
3. After a minute, your site is live at `https://<your-username>.github.io/hub/`.

### 3. Create an access token (lets the page save changes)
1. GitHub → your avatar → **Settings → Developer settings → Personal access tokens → Fine-grained tokens → Generate new token**.
2. **Repository access:** *Only select repositories* → pick `hub`.
3. **Permissions → Repository permissions → Contents:** *Read and write*. Leave everything else as it is.
4. Pick an expiration. When it expires, create a new token and paste it into Settings again.
5. Generate it and copy the token (it starts with `github_pat_`).

### 4. First start
1. Open your site and click **Settings**. Owner and repository are filled in automatically.
2. Paste the token, click **Test connection**, then **Save settings**.
3. Choose your password and click **Create my hub**. This creates `data.enc.json` in the repository.

### Other devices
- Open the site and enter your password. You can view the list right away.
- To **edit** on that device, add the token in Settings there too.
- Tick *Keep me unlocked on this device* only on devices that are yours.

## Good to know
- **There is no password reset.** If you forget the password, the list can't be decrypted. Use a password you'll remember, such as a short sentence.
- **Security:** AES-256-GCM encryption with a key derived from your password (PBKDF2-SHA256, 600,000 iterations). The token lives only in your browser, never in the repository.
- **Delay without a token:** devices without a token read the file through GitHub Pages, which can take about a minute to show changes. Devices with a token always load the latest version.
- **Search engines:** the page asks them not to index it (`noindex`).
- **Custom domain later** (for example `basilstutz.ch`): add it under Settings → Pages, then write `owner` and `repo` into the `CONFIG` line near the top of the script in `index.html`, because they can only be detected automatically on `github.io`.
- **Adding more hub sections:** the sidebar is ready for them. Each new section can store its data in the same encrypted file.
