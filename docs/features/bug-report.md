---
title: Bug Report
description: Submit bug reports directly from the Bambuddy UI
---

# Bug Report

Submit bug reports directly from the Bambuddy UI without leaving the application.

---

## :material-bug: Overview

The in-app bug report feature provides a quick way to report issues:

- **One-click access** — Floating bug button in the bottom-right corner
- **Screenshot support** — Upload, paste from clipboard, or drag & drop images
- **Automatic diagnostics** — System info and debug logs collected automatically
- **Privacy-first** — All sensitive data is sanitized before submission
- **GitHub integration** — Reports create GitHub issues automatically

---

## :material-send: Submitting a Report

1. Click the red **bug icon** in the bottom-right corner of any page
2. **Describe the issue** — What went wrong? Steps to reproduce?
3. **Add a screenshot** (optional) — Upload a file, paste from clipboard (Ctrl+V), or drag & drop an image onto the upload area. Images are automatically compressed to JPEG.
4. **Add your email** (optional) — If provided, your email will be included in a collapsed section of the GitHub issue so the maintainer can follow up.
5. Click **Submit**

---

## :material-file-search: What Happens After Submit

After you click Submit, Bambuddy automatically:

1. **Enables debug logging** temporarily (if not already enabled)
2. **Queries all connected printers** for fresh status data
3. **Waits 30 seconds** to collect diagnostic logs (a countdown timer is shown)
4. **Sanitizes all logs** — Removes printer names, serial numbers, IP addresses, credentials, and other sensitive data
5. **Submits to GitHub** — Creates an issue with your description, screenshot, system info, and sanitized logs
6. **Restores normal logging** if debug was not previously enabled

---

## :material-shield-lock: Data Privacy

The bug report includes a detailed, expandable privacy notice explaining exactly what data is collected.

### Included in the report

- App version, OS, architecture, Python version
- Database statistics (counts only)
- Printer models, nozzle counts, firmware versions
- Connectivity status
- Integration status (Spoolman, MQTT, Home Assistant)
- Non-sensitive settings
- Network interface count
- Docker details
- Dependency versions
- Sanitized application logs (last 200 lines)

### Never included

- Printer names or serial numbers
- Access codes or passwords
- IP addresses
- Email addresses (except your own, if you provide it)
- API keys or tokens
- Webhook URLs
- Hostnames or usernames

---

## :material-server: How It Works

Bug reports are submitted through a secure relay service on `bambuddy.cool`. This relay:

- Holds the GitHub API token server-side (never shipped in the application)
- Uploads screenshots and log files to GitHub
- Creates issues with appropriate labels
- Rate-limited to prevent abuse (5 reports per hour)

Your Bambuddy instance never needs a GitHub token — the relay handles all GitHub communication.
