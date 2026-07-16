# Meadows of Wright Farm HOA Website

This repository contains the source code for the Meadows of Wright Farm Homeowners Association website. It is built using Jekyll (a static site generator) and Decap CMS (a Git-based content management system).

## Setup & Deployment Instructions

### 1. Push to GitHub
1. Create a new repository on GitHub (e.g., `hoa-final`).
2. Push all the files in this directory to your new `main` branch.

### 2. Enable GitHub Pages
1. Go to your repository's **Settings** tab on GitHub.
2. Click on **Pages** in the left sidebar.
3. Under "Build and deployment", set the **Source** to "Deploy from a branch".
4. Set the branch to `main` and the folder to `/(root)`.
5. Click **Save**. Within a few minutes, your site will be live at `https://your-username.github.io/hoa-final/`.
*Note: Make sure to update the `url` and `baseurl` in `_config.yml` if you aren't using a custom domain.*

### 3. Setup Decap CMS (Admin Panel)
To allow editing the site via `/admin`, you must configure a GitHub OAuth app. You have two free options:

#### Option A: Using a Free Netlify Account (Recommended for beginners)
1. Go to [Netlify.com](https://www.netlify.com/) and sign up for a free account.
2. Click "Add new site" -> "Import an existing project" -> connect your GitHub repo.
3. Once deployed on Netlify, go to **Site settings** -> **Identity** and click **Enable Identity**.
4. Scroll down to **Registration preferences** and set it to **Invite only**.
5. Scroll down to **External providers** and add **GitHub**.
6. (Optional) If you want the site to primarily live on GitHub Pages, you can just use the Netlify site for logging in.
7. Important: Make sure the script `<script src="https://identity.netlify.com/v1/netlify-identity-widget.js"></script>` is in your `admin/index.html`.

#### Option B: Using a Free Cloudflare Worker (No Netlify account needed)
1. Create a free Cloudflare account.
2. Deploy a Decap CMS GitHub OAuth proxy worker (e.g., [sveltia-cms-auth](https://github.com/sveltia/sveltia-cms-auth)).
3. Once deployed, open `admin/config.yml` and uncomment the `base_url` line, replacing it with your worker's URL:
   ```yaml
   base_url: https://your-worker-name.workers.dev
   ```
4. Comment out the Netlify identity widget script in `admin/index.html`.

### 4. Setup the Contact Form
GitHub Pages does not have a backend to process forms. We use Formspree.
1. Sign up for a free account at [Formspree](https://formspree.io/).
2. Create a new form (e.g., "HOA Contact Form") and set the recipient email address.
3. Formspree will give you an endpoint URL (e.g., `https://formspree.io/f/YOUR_ID`).
4. Open `contact.md` or go to the Admin panel and edit the Contact page, replacing `YOUR_FORMSPREE_ENDPOINT` with your actual endpoint URL.

### 5. Managing Content
Once setup is complete, you can go to `https://your-site-url.com/admin` to log in.
From the Decap CMS dashboard, you can:
- Edit the homepage tagline and announcements.
- Add or remove Board and Committee members.
- Post new upcoming events or delete past ones.
- Upload PDF documents (like meeting minutes or bylaws).
- Edit the text on the About, Contact, and FAQ pages.
