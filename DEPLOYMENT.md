# GitHub Pages Deployment Instructions

Follow these steps to deploy your User-Centered Design Guidance site to GitHub Pages.

## Prerequisites

- A GitHub account
- Git installed on your computer (optional, but recommended)

## Option 1: Deploy via GitHub Web Interface (Easiest)

### Step 1: Create a New Repository

1. Go to [GitHub](https://github.com) and sign in
2. Click the **+** button in the top right corner
3. Select **New repository**
4. Fill in the details:
   - **Repository name**: `ucd-guidance` (or any name you prefer)
   - **Description**: "User-Centered Design Guidance - Interactive web resource"
   - **Public** or **Private**: Choose based on your needs
   - **Do NOT** initialize with README (we already have one)
5. Click **Create repository**

### Step 2: Upload Files

1. On your new repository page, click **uploading an existing file**
2. Drag and drop ALL files from the `github-pages-site` folder:
   - `index.html`
   - `README.md`
   - `.gitignore`
3. Add a commit message: "Initial commit - UCD Guidance site"
4. Click **Commit changes**

### Step 3: Enable GitHub Pages

1. In your repository, click **Settings**
2. Scroll down to the **Pages** section (left sidebar)
3. Under **Source**:
   - Branch: Select `main`
   - Folder: Select `/ (root)`
4. Click **Save**
5. Wait 1-2 minutes for deployment
6. Your site URL will appear: `https://[your-username].github.io/[repository-name]/`

### Step 4: Verify Deployment

1. Click the provided URL or visit it in your browser
2. Your site should be live!

## Option 2: Deploy via Git Command Line

### Step 1: Initialize Git Repository

```bash
cd /path/to/github-pages-site
git init
git add .
git commit -m "Initial commit - UCD Guidance site"
```

### Step 2: Create GitHub Repository

1. Go to [GitHub](https://github.com) and create a new repository (as described in Option 1)
2. **Do NOT** initialize with README

### Step 3: Push to GitHub

```bash
git remote add origin https://github.com/[your-username]/[repository-name].git
git branch -M main
git push -u origin main
```

### Step 4: Enable GitHub Pages

Follow Step 3 from Option 1 above.

## Custom Domain (Optional)

If you want to use a custom domain:

1. In your repository **Settings** → **Pages**
2. Under **Custom domain**, enter your domain name
3. Click **Save**
4. Add a CNAME record in your domain's DNS settings pointing to:
   - `[your-username].github.io`

## Updating Your Site

### Via Web Interface:

1. Go to your repository on GitHub
2. Click on `index.html`
3. Click the pencil icon (Edit)
4. Make your changes
5. Scroll down and click **Commit changes**
6. Changes will be live in 1-2 minutes

### Via Git:

```bash
# Make changes to your files locally
git add .
git commit -m "Description of changes"
git push origin main
```

## Troubleshooting

### Site Not Loading

- Wait 2-3 minutes after enabling GitHub Pages
- Check that the branch is set to `main` in Settings → Pages
- Ensure `index.html` is in the root directory
- Clear your browser cache

### 404 Error

- Verify the repository name in your URL
- Check that GitHub Pages is enabled
- Ensure `index.html` exists in the root

### Changes Not Appearing

- Wait 1-2 minutes for GitHub Pages to rebuild
- Clear browser cache (Ctrl+Shift+R or Cmd+Shift+R)
- Check that you committed and pushed your changes

## GitHub Pages Limits

- Repository size: Up to 1 GB
- Site size: Up to 1 GB
- Bandwidth: 100 GB/month soft limit
- Builds: 10 builds per hour

## Need Help?

- [GitHub Pages Documentation](https://docs.github.com/en/pages)
- [GitHub Community Forum](https://github.community/)

---

**Note**: This is a static site with no server-side processing. All functionality works through client-side HTML, CSS, and JavaScript.
