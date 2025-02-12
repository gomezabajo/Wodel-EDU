# Wodel-EDU
Wodel-EDU website

## Configuring Jekyll GitHub Pages Environment

The Jekyll GitHub Pages environment is configured in the `.github/workflows/jekyll-gh-pages.yml` file. This file contains the workflow for building and deploying the Jekyll site to GitHub Pages.

### Configuring GitHub Pages

To configure GitHub Pages for your repository, follow these steps:

1. Go to the "Settings" tab in your GitHub repository.
2. In the left sidebar, click on "Pages" under the "Code and automation" section.
3. Under "Source", select the branch you want to use for GitHub Pages (e.g., `gh-pages`).
4. Click "Save" to apply the changes.

### Triggering the Workflow

The workflow is triggered on pushes to the `main` branch. You can also manually trigger the workflow from the Actions tab in your GitHub repository. To do this, follow these steps:

1. Go to the "Actions" tab in your GitHub repository.
2. Select the "Deploy Jekyll with GitHub Pages dependencies preinstalled" workflow from the list on the left.
3. Click the "Run workflow" button on the right.
4. Select the branch you want to run the workflow on (default is `main`).
5. Click the "Run workflow" button to start the workflow.
