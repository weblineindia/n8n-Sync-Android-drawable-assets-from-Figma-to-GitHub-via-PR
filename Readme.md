# Sync Android drawable assets from Figma to GitHub via PR (multi-density PNG)

This n8n workflow automatically fetches design assets (icons, buttons) from a Figma file, exports them into Android drawable asset folders for different screen densities (such as `mdpi`, `hdpi`, etc.), and commits them to a GitHub branch — creating a Pull Request with all updates. :contentReference[oaicite:1]{index=1}

---

## Who’s It For

- Android and Flutter developers managing multi-density drawable assets
- Design and development teams wanting to automate asset delivery
- Mobile teams tired of manually exporting, resizing, and uploading design assets
- Projects where design changes frequently and assets must stay in sync with code :contentReference[oaicite:2]{index=2}

---

## How It Works

1. Trigger the workflow manually or via schedule/webhook.
2. Fetch all export URLs from a Figma file.
3. Filter components to extract only relevant items like `Icon` and `Button`.
4. Prepare Android drawable folders (e.g., `drawable-mdpi`, `drawable-hdpi`).
5. Map and merge fetched components with folder structure.
6. Call Figma API to get the images for all required densities.
7. Filter out invalid URLs.
8. Download all images as binary files.
9. Rename and adjust file names if needed.
10. Ensure no duplicate Pull Requests are created.
11. Commit the files to a new branch and create a GitHub Pull Request. :contentReference[oaicite:3]{index=3}

---

## How to Set Up

1. Create and connect your **Figma API token** in n8n (ensure it has access to the design file).
2. Copy the **Figma File Key** and optionally the parent **node ID** where your assets reside.
3. Connect your **GitHub account** in n8n (OAuth Token).
4. Prepare a **GitHub branch** to upload the assets.
5. Configure your **drawable folders** and file naming logic in the workflow.
6. Run the workflow to fetch and prepare assets.
7. Confirm the Pull Request is generated with drawable assets. :contentReference[oaicite:4]{index=4}

---

## Requirements

| Tool                   | Purpose                                                                                           |
| ---------------------- | ------------------------------------------------------------------------------------------------- |
| Figma API Token        | To fetch assets and export URLs                                                                   |
| GitHub Token           | To commit files and create Pull Requests                                                          |
| n8n                    | Workflow automation engine                                                                        |
| Figma File Key         | Design file to export from                                                                        |
| Node Names in Workflow | Nodes like `Icon`, `Button` matching your export categories :contentReference[oaicite:5]{index=5} |

---

## How to Customize

- Add more component types to extract (e.g., `Avatar`, `Chip`).
- Change folder structure for different platforms (iOS, Web).
- Include image optimization before upload (e.g., compress PNGs).
- Switch from PR creation to direct commits if preferred.
- Add CI triggers after PR creation (Slack notifications, Jenkins, GitHub Actions). :contentReference[oaicite:6]{index=6}

---

## Add-Ons

- **Slack Notification Node** — Notify teams when a PR is created.
- **Commit Summary Update** — Append a summary of updated assets to `CHANGELOG.md`.
- **Image Format Conversion** — Convert assets between formats (SVG → PNG, PNG → WebP).
- **Auto-Tagging** — Tag the GitHub release based on asset count or changes. :contentReference[oaicite:7]{index=7}

---

## Use Case Examples

- Automatically export new design icons from Figma as Android assets.
- Designers update icons — developers receive a PR with ready-to-merge assets.
- Maintain consistency across densities without manual effort.
- Integrate this workflow into weekly design-dev sync routines. :contentReference[oaicite:8]{index=8}

---

## Common Troubleshooting

| Issue                      | Possible Cause                                     | Solution                                                                                                         |
| -------------------------- | -------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| Export URL is `null`       | Figma node has no export settings                  | Add export settings to each component in Figma                                                                   |
| Images not appearing in PR | Incorrect merge or file naming                     | Reconfirm merge logic and ensure file extensions are correct                                                     |
| Duplicate PR created       | Workflow does not properly check existing branches | Update condition node to check for existing open PRs                                                             |
| Figma API errors (403/401) | Invalid or expired Figma token                     | Regenerate token and update n8n credentials                                                                      |
| GitHub upload fails        | Path incorrect or binary mismatch                  | Ensure correct folder structure (`drawable-mdpi`, etc.) and valid binaries :contentReference[oaicite:9]{index=9} |

---

## Need Help?

If you’d like help setting up, customizing, or expanding this workflow, reach out to our **WeblineIndia** n8n automation team!  
We can help with:

- Fine-tuning Figma export filters
- Improving file naming and folder mapping
- Integrating Slack or CI pipelines
- Adding support for other platforms (iOS, Web) :contentReference[oaicite:10]{index=10}

Happy automating! 🚀
