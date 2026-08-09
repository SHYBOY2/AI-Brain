---
title: "Download for Linux — Antigravity"
tags: [source, reference, linux, installation, antigravity, software]
created: 2026-08-09
updated: 2026-08-09
source_file: "raw/processed/Download for Linux.md"
source_url: "https://antigravity.google/download/linux"
source_count: 1
sources: []
---

# Download for Linux — Antigravity

**Source:** antigravity.google | **Type:** Installation reference

## Summary

Step-by-step instructions for installing the Antigravity package on Linux systems. Covers both Debian/Ubuntu-based (deb) and Red Hat/Fedora/SUSE-based (rpm) distributions.

## deb-based (Debian, Ubuntu)

```bash
# 1. Add repository
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://us-central1-apt.pkg.dev/doc/repo-signing-key.gpg | \
  sudo gpg --dearmor --yes -o /etc/apt/keyrings/antigravity-repo-key.gpg
echo "deb [signed-by=/etc/apt/keyrings/antigravity-repo-key.gpg] https://us-central1-apt.pkg.dev/projects/antigravity-auto-updater-dev/ antigravity-debian main" | \
  sudo tee /etc/apt/sources.list.d/antigravity.list > /dev/null

# 2. Update cache
sudo apt update

# 3. Install
sudo apt install antigravity
```

## rpm-based (Red Hat, Fedora, SUSE)

```bash
# 1. Add repository
sudo tee /etc/yum.repos.d/antigravity.repo << EOL
[antigravity-rpm]
name=Antigravity RPM Repository
baseurl=https://us-central1-yum.pkg.dev/projects/antigravity-auto-updater-dev/antigravity-rpm
enabled=1
gpgcheck=0
EOL

# 2. Update cache
sudo dnf makecache

# 3. Install
sudo dnf install antigravity
```

## Related Wiki Pages

- [[wiki/Antigravity]] — Antigravity software entity page
