# Repository Analysis: KdkSupportPkg

## What is this?
This repository is an archive and distribution system for **macOS Kernel Debug Kits (KDKs)**.

## Why does it exist?
KDKs are specialized software packages from Apple used by developers to debug the macOS kernel.
*   **The Problem:** Apple hosts these behind a developer login, making it hard for automated tools to download them.
*   **The Solution:** This repository (and its original parent) downloads them once and re-hosts them on GitHub Releases, allowing tools to download them freely without a login.
*   **Primary User:** It is designed to support **OpenCore Legacy Patcher**, a tool that allows newer macOS versions to run on older Macs. The patcher needs these KDKs to build drivers for older hardware on macOS Ventura and later.

## How it works
This repository functions more like a database than a software program:
1.  **`manifest.json`**: This file is an index. It lists the available KDK versions and their direct download URLs. Tools read this file to know what is available.
2.  **GitHub Releases**: The actual `.dmg` files (the KDKs) are uploaded to the "Releases" section of this GitHub repository.

## Important Note on "Missing" Code
You might notice there isn't much actual code here. That is intentional but important to understand:
*   The automation logic (the code that checks Apple's site, downloads the KDK, and updates this repo) is **not included**.
*   The `.github/workflows/main.yml` file attempts to run a script (`run.py`), but it fetches that script from a *different, private repository* (referenced as `${{ secrets.CODE_REPO }}`).
*   **Conclusion:** As it stands, this local copy is a **static snapshot**. It will not update itself with new KDKs unless you also possess the external automation scripts and credentials.

## Summary
You have downloaded a "mirror" or "archive" configuration. It is useful as a reference for where KDKs are stored, but without the external backend scripts, it is a passive collection of data.
