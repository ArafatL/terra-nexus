# Deployment

Terra Nexus is one static file, so any static host works. GitHub Pages is the simplest because the code and the live site sit in the same place.

## 1. Create the repository

**In the browser (no Git needed)**

1. Sign in to GitHub and click **New repository**.
2. Name it `terra-nexus`, set it to **Public**, and leave "Add a README" unticked (this pack already has one).
3. Click **Create repository**.
4. On the empty repository page, click **uploading an existing file**.
5. Unzip `terra-nexus.zip` on your computer, open the `terra-nexus` folder, select everything inside it (including the `docs` folder) and drag it onto the page.
6. Commit message: `Initial commit: Terra Nexus dashboard and documentation`. Click **Commit changes**.

Files starting with a dot (`.gitignore`, `.nojekyll`) are hidden on some computers. If they don't upload, that's fine; the site still works.

**Or with Git from the command line**

```bash
cd terra-nexus
git init
git add .
git commit -m "Initial commit: Terra Nexus dashboard and documentation"
git branch -M main
git remote add origin https://github.com/<your-username>/terra-nexus.git
git push -u origin main
```

## 2. Turn on GitHub Pages

1. In the repository, go to **Settings → Pages**.
2. Under **Build and deployment**, choose **Deploy from a branch**.
3. Branch: `main`, folder: `/ (root)`. Click **Save**.
4. After one or two minutes the site is live at `https://<your-username>.github.io/terra-nexus/`.

## 3. Finish the repository page

1. On the repository home page, click the gear icon next to **About**.
2. Description: `ESG and carbon analytics blueprint: one dataset serving Board, operations and compliance views. React + Recharts.`
3. Website: tick **Use your GitHub Pages website**.
4. Topics: `esg`, `sustainability`, `carbon-accounting`, `dashboard`, `data-visualization`, `react`, `recharts`, `kpi`.
5. In the README, replace `<your-username>` in the live demo link with your GitHub username and commit.
6. Optional: on your GitHub profile, click **Customize your pins** and pin `terra-nexus`.

## Alternatives

**Netlify:** sign in, open app.netlify.com/drop, drag the `terra-nexus` folder in, then rename the site under Site configuration.

**Vercel:** import the GitHub repository at vercel.com/new. Framework preset: **Other**. No build command, output directory `.`.

## Check before sharing

- Open the live link in a private browser window and on a phone.
- Click through all eight tabs and the facility filter.
- Confirm the "illustrative data" banner shows at the top.
