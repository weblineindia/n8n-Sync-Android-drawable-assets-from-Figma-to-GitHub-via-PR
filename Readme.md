# Sync Android Drawable Assets from Figma to GitHub via PR (Multi-Density PNG)

This n8n workflow automatically fetches design assets (icons, buttons, etc.) from a Figma file, exports them into Android drawable folders for multiple screen densities (`mdpi`, `hdpi`, `xhdpi`, etc.), and commits them to a GitHub branch — creating a Pull Request with all updates.

It removes manual exporting, resizing, and uploading of assets, ensuring design and code stay perfectly in sync.

---

## Who’s It For

* Android and Flutter developers managing multi-density drawable assets
* Design and development teams automating asset delivery
* Mobile teams tired of manual export and upload workflows
* Projects where design assets change frequently and must stay in sync with code

---

## How It Works

1. Trigger the workflow manually, on a schedule, or via webhook
2. Fetch export URLs from a Figma file
3. Filter components to include only relevant nodes (e.g., `Icon`, `Button`)
4. Prepare Android drawable folders (`drawable-mdpi`, `drawable-hdpi`, etc.)
5. Map components to the correct density folders
6. Call the Figma API to export images for all required densities
7. Filter out invalid or empty export URLs
8. Download images as binary files
9. Normalize and rename files if required
10. Check for existing open Pull Requests to avoid duplicates
11. Commit files to a new GitHub branch and create a Pull Request

---

## How to Set Up

1. Create and connect a **Figma API token** in n8n (with access to the design file)
2. Copy the **Figma File Key** and, optionally, the parent **Node ID** containing assets
3. Connect your **GitHub account** in n8n using an OAuth token
4. Configure the target **GitHub repository and base branch**
5. Define:

   * Drawable folder structure (`drawable-mdpi`, `drawable-hdpi`, etc.)
   * File naming conventions
6. Run the workflow to fetch and prepare assets
7. Verify the generated Pull Request contains all updated drawable assets

---

## Requirements

| Tool / Input     | Purpose                                              |
| ---------------- | ---------------------------------------------------- |
| Figma API Token  | Fetch assets and export URLs from Figma              |
| Figma File Key   | Design file containing drawable assets               |
| GitHub Token     | Commit files and create Pull Requests                |
| n8n              | Workflow automation engine                           |
| Component Naming | Figma node names like `Icon`, `Button` for filtering |

---

## How to Customize

* Add more component types (e.g., `Avatar`, `Chip`, `Illustration`)
* Adjust folder structure for other platforms (iOS, Web, Flutter)
* Add image optimization (PNG compression) before committing
* Switch from PR creation to direct commits if required
* Trigger CI workflows after PR creation (GitHub Actions, Jenkins)

---

## Add-Ons

* **Slack notifications** when a Pull Request is created
* **Changelog updates** to append asset changes automatically
* **Image format conversion** (SVG → PNG, PNG → WebP)
* **Auto-tagging releases** based on asset updates

---

## Use Case Examples

* Automatically export updated icons from Figma as Android assets
* Designers update assets → developers receive a ready-to-merge PR
* Maintain consistency across screen densities with zero manual work
* Run this workflow as part of weekly design–development syncs

---

## Common Troubleshooting

| Issue                      | Possible Cause                         | Solution                                                  |
| -------------------------- | -------------------------------------- | --------------------------------------------------------- |
| Export URL is `null`       | No export settings defined in Figma    | Add export settings to each component in the Figma file   |
| Images missing in PR       | Incorrect merge or file naming logic   | Verify merge logic and ensure correct file extensions     |
| Duplicate PRs created      | Existing PR check missing or incorrect | Add a check for open PRs on the same branch               |
| Figma API errors (401/403) | Invalid or expired Figma token         | Regenerate the token and update credentials in n8n        |
| GitHub upload fails        | Incorrect path or binary handling      | Verify drawable folder paths and ensure valid binary data |

---

## Need Help?

If you’d like help setting up, customizing, or extending this workflow, our **WeblineIndia n8n automation experts** can assist with:

* Fine-tuning Figma export filters
* Improving file naming and folder mapping
* Integrating Slack or CI pipelines
* Adding support for iOS, Web, or Flutter assets

Happy automating 🚀
