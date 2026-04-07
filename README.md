# Gordon Concrete Pumping — Website

Astro website for Gordon Concrete Pumping. Built with [Astro](https://astro.build), deployed via GitHub Pages.

---

## Local Development

### Prerequisites

You need **Node.js** installed. Download it at [nodejs.org](https://nodejs.org) — grab the **LTS** version.

### Steps

1. Open a terminal (Command Prompt or PowerShell on Windows)
2. Navigate to this folder:
   ```
   cd "C:\Users\ysabe\OneDrive\Documents\JG Concrete Pumping\website"
   ```
3. Install dependencies:
   ```
   npm install
   ```
4. Start the dev server:
   ```
   npm run dev
   ```
5. Open your browser to `http://localhost:4321`

Any changes you save will reload automatically in the browser.

---

## Deploying to GitHub Pages

This is a step-by-step guide for someone who has not done this before.

---

### Step 1 — Create a GitHub Account

If you don't have one, go to [github.com](https://github.com) and sign up. It's free.

---

### Step 2 — Create a New Repository on GitHub

1. Log into GitHub
2. Click the **+** icon in the top-right corner → **New repository**
3. Fill in:
   - **Repository name**: `gordon-concrete-pumping` (or whatever you prefer — no spaces)
   - **Description**: Gordon Concrete Pumping website
   - **Public** (required for free GitHub Pages)
   - Do **NOT** check "Add a README file" (we already have one)
4. Click **Create repository**
5. **Copy your repository URL** — it will look like:
   ```
   https://github.com/yourusername/gordon-concrete-pumping.git
   ```

---

### Step 3 — Update `astro.config.mjs`

Before pushing, you need to tell Astro where it will be hosted.

Open the file `astro.config.mjs` in this folder and update:

```js
export default defineConfig({
  site: 'https://yourusername.github.io',       // ← replace with your GitHub username
  base: '/gordon-concrete-pumping',              // ← replace with your repo name
});
```

For example, if your GitHub username is `johndoe` and repo is `gordon-concrete-pumping`:
```js
export default defineConfig({
  site: 'https://johndoe.github.io',
  base: '/gordon-concrete-pumping',
});
```

Save the file.

---

### Step 4 — Install Git

If you don't have Git installed, download it at [git-scm.com](https://git-scm.com) and install it with default settings.

To check if it's installed, open a terminal and run:
```
git --version
```
You should see a version number like `git version 2.x.x`.

---

### Step 5 — Set Up Git in This Folder

Open a terminal in the `website` folder and run these commands one at a time:

```bash
git init
git add .
git commit -m "Initial website"
```

What this does:
- `git init` — turns this folder into a Git repository
- `git add .` — stages all files to be committed
- `git commit -m "..."` — saves a snapshot of the files

---

### Step 6 — Connect to GitHub and Push

Run these commands (replace with your actual GitHub URL from Step 2):

```bash
git remote add origin https://github.com/yourusername/gordon-concrete-pumping.git
git branch -M main
git push -u origin main
```

What this does:
- `git remote add origin ...` — links your local folder to the GitHub repository
- `git branch -M main` — renames the branch to "main" (GitHub's default)
- `git push -u origin main` — uploads your files to GitHub

You'll be asked to log in to GitHub. Use your username and password, or set up a personal access token if prompted (GitHub will guide you).

---

### Step 7 — Enable GitHub Pages

1. Go to your repository on GitHub: `https://github.com/yourusername/gordon-concrete-pumping`
2. Click **Settings** (top tab row)
3. In the left sidebar, click **Pages**
4. Under **Build and deployment** → **Source**, select **GitHub Actions**
5. Click **Save**

---

### Step 8 — Your Site Is Being Built

1. Go to the **Actions** tab in your repository
2. You should see a workflow running called **Deploy to GitHub Pages**
3. Wait for it to finish (usually 1–3 minutes) — it will show a green checkmark when done

Your site will be live at:
```
https://yourusername.github.io/gordon-concrete-pumping
```

---

### Step 9 — Making Changes in the Future

Whenever you make changes to the website files and want them to go live:

```bash
git add .
git commit -m "Describe what you changed"
git push
```

GitHub will automatically rebuild and redeploy the site.

---

## Custom Domain (Optional)

If you want to use a custom domain like `gordonconcretepumping.com`:

1. Purchase a domain from a registrar (Namecheap, GoDaddy, Cloudflare, etc.)
2. In GitHub → Settings → Pages → **Custom domain**, enter your domain
3. In your domain registrar's DNS settings, add these records:
   ```
   Type: A     Name: @     Value: 185.199.108.153
   Type: A     Name: @     Value: 185.199.109.153
   Type: A     Name: @     Value: 185.199.110.153
   Type: A     Name: @     Value: 185.199.111.153
   ```
4. Also add a CNAME record:
   ```
   Type: CNAME     Name: www     Value: yourusername.github.io
   ```
5. Check **Enforce HTTPS** in GitHub Pages settings
6. Update `astro.config.mjs`:
   ```js
   export default defineConfig({
     site: 'https://gordonconcretepumping.com',
     base: '/',   // ← change to '/' when using a custom domain
   });
   ```

DNS changes can take up to 24 hours to fully propagate.

---

## File Structure

```
website/
├── src/
│   ├── components/
│   │   ├── Header.astro       ← Navigation bar
│   │   └── Footer.astro       ← Footer
│   ├── layouts/
│   │   └── Layout.astro       ← Page wrapper (head, header, footer)
│   ├── pages/
│   │   ├── index.astro        ← Home page
│   │   ├── services.astro     ← Services page
│   │   ├── service-area.astro ← Service area page
│   │   ├── about.astro        ← About Jacob page (bio, education, experience)
│   │   └── contact.astro      ← Contact / quote form page
│   └── styles/
│       └── global.css         ← Global CSS variables and base styles
├── public/
│   └── favicon.svg            ← Browser tab icon
├── .github/
│   └── workflows/
│       └── deploy.yml         ← Automatic GitHub Pages deployment
├── astro.config.mjs           ← Astro configuration (update site + base!)
├── package.json               ← Project dependencies
├── .gitignore                 ← Files not uploaded to GitHub
└── README.md                  ← This file
```

---

## Things to Update Before Going Live

| Location | What to Update |
|---|---|
| `astro.config.mjs` | Your GitHub username and repo name |
| `src/components/Header.astro` | Phone number |
| `src/components/Footer.astro` | Phone number, email address |
| `src/pages/contact.astro` | Phone number, email address |
| `src/pages/index.astro` | Phone number (CTA button) |
| `src/pages/services.astro` | Phone number |
| `src/pages/pricing.astro` | Phone number |
| `src/pages/service-area.astro` | Phone number |
| `src/pages/about.astro` | Any additional personal details |
| All pages | Exact pump model/brand (currently "38-meter boom pump") |
