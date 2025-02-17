# Weekly SBOM Update

This repository uses a GitHub Actions workflow to fetch and update the Software Bill of Materials (SBOM) for `care` and `care_fe` every week on **Sunday**, deploying the data to GitHub Pages.

The latest SBOM data is available at: [https://ohcnetwork.github.io/care_sbom/](https://ohcnetwork.github.io/care_sbom/)

**NOTE:** To access SBOM data, navigate to `/care/{version}/sbom.json` (e.g., `/care/v3.0.0/sbom.json`)

## Workflow Overview

The workflow, defined in [`.github/workflows/fetch-sbom.yml`](.github/workflows/fetch-sbom.yml), has two main jobs:

### 1. `fetch-sbom` Job
- **Checkout repository**
- **Fetch latest release versions** of `care` and `care_fe` using the GitHub API
- **Create SBOM directories** if they don’t exist and fetch SBOM data
- **Commit & push changes** if updates are found

### 2. `deploy-sbom` Job
- Deploys SBOM data to GitHub Pages using `peaceiris/actions-gh-pages@v4`

## Workflow Triggers
- **Scheduled:** Runs every Sunday at midnight IST (18:30 UTC Saturday)
- **Manual Dispatch:** Can be triggered manually

## Permissions
- `contents: write` – Commit & push changes
- `pages: write` – Deploy SBOM data

## License
This project is licensed under the [MIT License](LICENSE).
