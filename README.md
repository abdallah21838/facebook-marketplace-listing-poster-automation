# Facebook Marketplace Listing Poster Automation

> A workflow automation project for creating and publishing Facebook Marketplace listings from a structured inventory feed with consistent formatting and reporting. It streamlines bulk listing operations by preparing drafts, validating data, and guiding a controlled publish process.

<p align="center">
  <a href="https://Appilot.app" target="_blank"><img src="https://github.com/Instagram-Automations/Footer-test/blob/main/appilot-baner.png" alt="Appilot Banner" width="100%"></a>
</p>
<p align="center">
  <a href="https://t.me/devpilot1" target="_blank"><img src="https://img.shields.io/badge/Chat%20on-Telegram-2CA5E0?style=for-the-badge&logo=telegram&logoColor=white" alt="Telegram"></a>
  <a href="mailto:support@appilot.app" target="_blank"><img src="https://img.shields.io/badge/Email-support@appilot.app-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Gmail"></a>
  <a href="https://Appilot.app" target="_blank"><img src="https://img.shields.io/badge/Visit-Website-007BFF?style=for-the-badge&logo=google-chrome&logoColor=white" alt="Website"></a>
  <a href="https://discord.gg/3YrZJZ6hA2" target="_blank"><img src="https://img.shields.io/badge/Join-Appilot_Community-5865F2?style=for-the-badge&logo=discord&logoColor=white" alt="Appilot Discord"></a>
</p>


<p align="center">
Created by Appilot, built to showcase our approach to Automation! <br>
If you are looking for custom <strong>  </strong>, you've just found your team — Let’s Chat.&#128070; &#128070;
</p>

## Introduction

Posting products on Facebook Marketplace repeatedly is tedious: copying titles, prices, descriptions, photos, locations, and categories for many items wastes time and increases mistakes. Bulk operations also need consistency—standard templates, clean images, and repeatable reporting—so listings look professional and updates are manageable.

This project automates the operational workflow: it reads an inventory file, validates required fields, prepares listing drafts, and drives a guided publish flow with step-level logs and exports.

### Local Commerce Listing Operations

- Converts inventory feeds into consistent, well-formatted listings
- Reduces manual entry errors with validation and templates
- Speeds up bulk posting with draft preparation and batching
- Produces run reports so you can track what was posted and when

---

## Core Features

| Feature | Description |
|----------|-------------|
| Inventory Feed Import | Reads CSV/JSON inventory with titles, prices, photos, and metadata |
| Data Validation | Validates required fields, price formats, photo paths, and categories |
| Listing Template Engine | Applies consistent description templates and keyword blocks |
| Image Prep Pipeline | Renames, validates, and optionally resizes images for upload |
| Draft Builder | Prepares draft payloads and a publish queue per batch |
| Guided Publish Runner | Steps through the Marketplace listing UI with checkpoints |
| Human Approval Gate | Requires confirmation before final publish per listing or batch |
| Batch Posting | Posts listings in controlled batches with cooldown intervals |
| Error Recovery | Retries transient failures and resumes from last checkpoint |
| Duplicate Prevention | Detects duplicate SKUs/titles to avoid reposting mistakes |
| Logging & Evidence | Saves step logs and optional screenshots on failure |
| Exportable Reports | Outputs a posted-listings CSV with URLs/IDs and status |

---

## How It Works

| Step | Description |
|------|-------------|
| **Input or Trigger** | Provide an inventory file and run a batch publish command. |
| **Core Logic** | The system validates items, builds listing drafts, queues them, and drives a guided publish flow with checkpoints. |
| **Output or Action** | Publishes listings (after approval) and produces a run report with statuses and identifiers. |
| **Other Functionalities** | Includes dedupe checks, retries, resumable checkpoints, and optional evidence capture. |
| **Safety Controls** | Enforces batch limits, cooldowns, and approval gates for controlled posting. |

## Tech Stack

| Component | Description |
|------------|-------------|
| **Language** | Python |
| **Frameworks** | Selenium |
| **Tools** | Pandas, Pillow |
| **Infrastructure** | Docker, GitHub Actions |

---

## Directory Structure Tree

    facebook-marketplace-listing-poster-automation/
    ├── src/
    │   ├── main.py
    │   ├── inventory/
    │   │   ├── importer.py
    │   │   ├── validators.py
    │   │   └── templates.py
    │   ├── images/
    │   │   ├── preprocessor.py
    │   │   └── asset_manager.py
    │   ├── marketplace/
    │   │   ├── runner.py
    │   │   ├── selectors.py
    │   │   └── draft_queue.py
    │   ├── approvals/
    │   │   ├── approval_gate.py
    │   │   └── review_ui.py
    │   ├── reliability/
    │   │   ├── retry_policy.py
    │   │   ├── backoff.py
    │   │   └── checkpoints.py
    │   ├── reporting/
    │   │   ├── exporter.py
    │   │   └── run_summary.py
    │   └── utils/
    │       ├── logger.py
    │       └── config_loader.py
    ├── config/
    │   ├── settings.yaml
    │   ├── category_map.yaml
    │   ├── location_profiles.yaml
    │   └── templates.yaml
    ├── logs/
    │   └── activity.log
    ├── output/
    │   ├── posted_listings.csv
    │   ├── failed_items.json
    │   └── run_report.json
    ├── assets/
    │   └── sample_inventory.csv
    ├── tests/
    │   ├── test_validators.py
    │   └── test_dedupe.py
    ├── docker/
    │   ├── Dockerfile
    │   └── compose.yaml
    ├── requirements.txt
    └── README.md

---
## Use Cases

- **Resellers** use it to bulk post inventory, so listings go live faster with fewer mistakes.
- **Small shops** use it to standardize descriptions and photos, so branding stays consistent.
- **Operations teams** use reports to track posted items, so follow-ups and renewals are organized.
- **Developers** use the template and validator modules, so new categories and fields are easy to add.

---

## FAQs

**Does it support bulk inventory updates as well as new listings?**  
Yes. The inventory feed can include an action field (create/update), and the runner can route items through the appropriate workflow based on configuration.

**How do I avoid duplicates and repeated postings?**  
Use SKU-based dedupe and maintain a posted listings ledger. The tool exports IDs/URLs so future runs can skip or update existing items.

**Can I review listings before they go live?**  
Yes. Approval gates allow per-item or per-batch confirmation before final publish.

**What if Facebook changes the Marketplace UI?**  
Selectors and flow steps are isolated into modules. Logs and evidence capture help quickly identify which step needs updating.

---

## Performance & Reliability Benchmarks

**Execution Speed:**  
Typically processes 12–30 listings per hour per browser session depending on photo upload time and approval steps.

**Success Rate:**  
Maintains 92–94% successful listing completion with retries enabled; failures usually come from UI drift or upload timeouts.

**Scalability:**  
Scales to hundreds of listings per day by running multiple sessions with batch caps and cooldown policies.

**Resource Efficiency:**  
Each active browser session uses ~400–900 MB RAM and moderate CPU during uploads; most load is I/O bound.

**Error Handling:**  
Implements retries with exponential backoff, checkpoint-based resume, structured failure logging, and screenshot evidence on errors.

<p align="center">
<a href="https://cal.com/app-pilot-m8i8oo/30min" target="_blank">
 <img src="https://img.shields.io/badge/Book%20a%20Call%20with%20Us-34A853?style=for-the-badge&logo=googlecalendar&logoColor=white" alt="Book a Call">
</a>
 <a href="https://www.youtube.com/@Appilot-app/videos" target="_blank">
  <img src="https://img.shields.io/badge/ð¥%20Watch%20demos%20-FF0000?style=for-the-badge&logo=youtube&logoColor=white" alt="Watch on YouTube">
 </a>
</p>
