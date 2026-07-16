# Meadows of Wright Farm HOA Website

This repository contains the source code for the Meadows of Wright Farm Homeowners Association website, built with [Jekyll](https://jekyllrb.com/) and [Decap CMS](https://decapcms.org/).

## Setup Instructions for the HOA Admin

This site is designed to run entirely on free tiers, using GitHub Pages for hosting and Decap CMS for easy content editing without touching code.

### 1. Push to GitHub
If you haven't already, push this codebase to a new public GitHub repository.

### 2. Enable GitHub Pages
1. Go to your repository on GitHub.
2. Click on **Settings** > **Pages** (in the left sidebar).
3. Under **Build and deployment**, set the **Source** to `Deploy from a branch`.
4. Select the `main` (or `master`) branch and click **Save**.
5. Within a few minutes, your site will be live at `https://<your-username>.github.io/<repo-name>/`.

### 3. Update Decap CMS Configuration
1. Open `admin/config.yml`.
2. Change the `repo:` value on line 3 to your exact GitHub repository path (e.g., `your-username/hoa-final`).
3. Commit and push this change.

### 4. Enable Authentication for Decap CMS (GitHub OAuth)
Because Decap CMS interacts with GitHub to save your edits, it needs an OAuth proxy. Choose **ONE** of the following free methods:

#### Option A: Using Netlify (Recommended & Easiest)
Netlify provides a built-in GitHub OAuth flow.
1. Create a free account on [Netlify](https://www.netlify.com/).
2. Click **Add new site** > **Import an existing project** and connect your GitHub repo.
3. Once deployed, go to **Site configuration** > **Access control** > **OAuth** and click **Install provider**.
4. Select GitHub and follow the prompts to generate a Client ID and Secret on GitHub, then paste them into Netlify.
5. You can now visit `https://<your-netlify-url>.netlify.app/admin/` to log in and edit content. The changes will automatically sync to GitHub and rebuild your main GitHub Pages site.

#### Option B: Using a Cloudflare Worker (No Netlify needed)
If you prefer not to use Netlify, you can run a free Cloudflare Worker to handle OAuth.
1. Follow the instructions at [decap-cms-github-oauth-cloudflare-worker](https://github.com/danielgindi/decap-cms-github-oauth-cloudflare-worker) to deploy the worker.
2. In your GitHub account, go to **Settings** > **Developer Settings** > **OAuth Apps** and create a new app.
3. Provide the Worker URL as the authorization callback URL.
4. Open `admin/config.yml` in this repository and add:
   ```yaml
   backend:
     name: github
     repo: your-username/hoa-final
     base_url: https://your-cloudflare-worker-url.workers.dev
   ```
5. Commit the change. You can now log in directly at `https://<your-username>.github.io/<repo-name>/admin`.

### 5. Setup the Contact Form
GitHub Pages does not have a backend server to process contact forms. We use a free third-party service like Formspree.
1. Sign up for a free account at [Formspree](https://formspree.io/).
2. Create a new form (e.g., "HOA Contact Form") and set the recipient email address.
3. Formspree will give you a unique endpoint URL (e.g., `https://formspree.io/f/xyzabcde`).
4. Edit the `contact.md` file in this repository and replace `https://formspree.io/f/your_formspree_id` with your unique URL.
5. Commit and push the change.

## Making Edits
Once configured, you do not need to edit code to update the site.
1. Navigate to your admin URL (e.g., `/admin/`).
2. Log in with GitHub.
3. Use the CMS interface to edit pages, add events, upload meeting minutes, or update board members.
4. Click **Publish** to save changes. The site will rebuild automatically!
