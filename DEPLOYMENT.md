# Deploying to Vercel

This guide will help you deploy your Daily Fuck app to Vercel.

## Prerequisites

1. A Vercel account (sign up at [vercel.com](https://vercel.com))
2. Your code pushed to a Git repository (GitHub, GitLab, or Bitbucket)

## Method 1: Deploy via Vercel Dashboard (Recommended)

### Step 1: Push to Git Repository

If you haven't already, initialize a git repository and push to GitHub/GitLab/Bitbucket:

```bash
# Initialize git (if not already done)
git init

# Add all files
git add .

# Commit
git commit -m "Initial commit"

# Add your remote repository (replace with your repo URL)
git remote add origin https://github.com/yourusername/your-repo.git

# Push to repository
git push -u origin main
```

### Step 2: Import Project to Vercel

1. Go to [vercel.com](https://vercel.com) and sign in
2. Click **"Add New..."** → **"Project"**
3. Import your Git repository
4. Vercel will auto-detect it's a Create React App project
5. Configure settings:
   - **Framework Preset**: Create React App (auto-detected)
   - **Root Directory**: `./` (leave as default)
   - **Build Command**: `npm run build` (auto-detected)
   - **Output Directory**: `build` (auto-detected)
   - **Install Command**: `npm install` (auto-detected)

### Step 3: Deploy

1. Click **"Deploy"**
2. Wait for the build to complete (usually 1-2 minutes)
3. Your app will be live at a URL like: `your-project-name.vercel.app`

## Method 2: Deploy via Vercel CLI

### Step 1: Install Vercel CLI

```bash
npm install -g vercel
```

### Step 2: Login to Vercel

```bash
vercel login
```

### Step 3: Deploy

From your project directory:

```bash
# Deploy to production
vercel --prod

# Or deploy to preview first
vercel
```

Follow the prompts:
- Set up and deploy? **Yes**
- Which scope? (Select your account)
- Link to existing project? **No** (for first deployment)
- Project name? (Enter a name or press Enter for default)
- Directory? **./** (press Enter)
- Override settings? **No** (press Enter)

## Environment Variables (if needed)

If you need to add environment variables later:

1. Go to your project on Vercel dashboard
2. Navigate to **Settings** → **Environment Variables**
3. Add any required variables

## Automatic Deployments

Once connected to Git:
- **Production**: Every push to `main`/`master` branch
- **Preview**: Every push to other branches or pull requests

## Custom Domain (Optional)

1. Go to **Settings** → **Domains**
2. Add your custom domain
3. Follow DNS configuration instructions

## Troubleshooting

### Build Fails

- Check build logs in Vercel dashboard
- Ensure `package.json` has correct build script
- Verify all dependencies are listed in `package.json`

### Routing Issues

The `vercel.json` file includes rewrites to handle React Router (if you add it later). For now, it ensures all routes serve `index.html`.

### Local Testing

Test the production build locally:

```bash
npm run build
npm install -g serve
serve -s build
```

## Notes

- Vercel automatically handles HTTPS
- Builds are cached for faster deployments
- Preview deployments are created for every commit
- The app uses client-side routing, so all routes are handled by the `vercel.json` rewrite rules
