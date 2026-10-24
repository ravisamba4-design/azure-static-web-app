# azure-static-web-app

A static site deployed to Azure Static Web Apps (Free plan) with automatic CI/CD from GitHub Actions.

**Live site:** https://black-sand-0f775890f.3.azurestaticapps.net

## Architecture

GitHub (main branch) -> GitHub Actions -> Azure Static Web Apps (Free)

Pull requests get their own preview environment, which is deleted when the PR is merged.

## What I built

- Created the Static Web App through the Azure portal and linked it to this repo
- Azure generated the GitHub Actions workflow in `.github/workflows/`
- Fixed a failed first deploy: the portal preset set `output_location: "/"`, which made the build look in the wrong place. For plain HTML it must be empty (`""`)
- Added `staticwebapp.config.json` with a navigation fallback, a 404 override and security headers
- Tested the PR preview environment workflow (feature branch, preview URL, merge, automatic cleanup)

## Teardown

    az group delete --name rg-swa-demo --yes --no-wait
