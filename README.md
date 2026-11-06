# Champions BTE Website

Source repository for the Champions website revamp deployed at **https://champions-bte.pages.dev**.

## Project status

- **GitHub repository:** `RammyJo/champions-bte` (`main`)
- **Cloudflare Pages project name:** `champions` (this is different from the public subdomain)
- **Production URL:** https://champions-bte.pages.dev
- **Publishing method:** Cloudflare Pages Direct Upload; there is no native GitHub build integration configured.
- **Website source code:** Not yet imported. The live site is NOT generated from the files currently in this repository.

> **Important:** Do not run the deployment workflow until the original working website source code has been pushed to this repository and the build has been verified. The existing live site must not be overwritten with a placeholder.

## Import the current website

1. Locate the original Champions BTE website project folder on the computer that built and uploaded the site to Cloudflare. Cloudflare's deployed static files are not necessarily the original editable source.
2. Copy the actual website files into the root of this repository, including `package.json`, lockfile, configuration, `src/`, `public/`, and any other required project files. Do **not** commit `.env` files, credentials, API tokens or `node_modules/`.
3. Verify that the project's build command creates a `dist/` directory containing `index.html`. If it produces a different folder, adjust the deployment workflow and this README to match.
4. Test locally, then commit and push to `main`.
5. Configure these GitHub Actions repository secrets under **Settings → Secrets and variables → Actions**:
   - `CLOUDFLARE_API_TOKEN`: a scoped Cloudflare API token with **Cloudflare Pages: Edit** access to the account.
   - `CLOUDFLARE_ACCOUNT_ID`: the Cloudflare account ID for the existing `champions` project.
6. Manually start **Actions → Deploy Champions BTE → Run workflow** only after validating the build and checking that the deployment targets the existing `champions` Pages project.

## Deployment safety

The deployment workflow is **manual-only** (`workflow_dispatch`). A GitHub push will **not** publish automatically. This safeguards the current site while its original source is being recovered and synchronized. After a full, successful deployment, you may deliberately add a `push` trigger for continuous deployment.

## Deployment command

```sh
npx wrangler@4 pages deploy dist --project-name=champions --branch=main
```

Always verify the Pages **project name** is `champions` before deploying. The public hostname is `champions-bte.pages.dev`.
