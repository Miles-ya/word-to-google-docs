# Word to Google Docs Converter (WordToDocs.com)

<div align="center">

<img src="https://img.shields.io/badge/WordToDocs.com-2563eb?style=for-the-badge&logo=googledocs&logoColor=white" alt="WordToDocs Logo" height="40">

<h3>Clean Layout Normalizer & Google Drive Batch Automation Tool</h3>

<p align="center">
  <b>100% Client-Side In-Browser Conversion · Zero Server Uploads · Pixel-Perfect Tables · Free Forever</b>
</p>

<p align="center">
  <a href="https://wordtodocs.com/"><strong>Explore the Live Web App »</strong></a>
  <br />
  <br />
  <a href="#-key-features">Key Features</a> ·
  <a href="#-how-it-works">How It Works</a> ·
  <a href="#-comparison">Why WordToDocs</a> ·
  <a href="#-google-drive-batch-automation">Drive Script</a> ·
  <a href="#-deployment-guide">Deploy Your Own</a>
</p>

[![Website](https://img.shields.io/website?down_color=red&down_message=offline&up_color=success&up_message=online&url=https%3A%2F%2Fwordtodocs.com)](https://wordtodocs.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![GitHub Pages](https://img.shields.io/badge/Deploy-GitHub%20Pages-brightgreen?logo=github)](https://wordtodocs.com/)
[![Privacy First](https://img.shields.io/badge/Privacy-100%25%20Local%20Sandbox-emerald?logo=shield)](https://wordtodocs.com/)
[![No Dependencies](https://img.shields.io/badge/Dependencies-Zero%20Build%20Step-orange)](#tech-stack)

</div>

---

## 💡 What is WordToDocs?

**[WordToDocs.com](https://wordtodocs.com/)** is an ultra-fast, privacy-first single-page web utility that solves the #1 frustration of moving documents from **Microsoft Word (.docx) to Google Docs**: **broken layouts, distorted tables, scrambled font hierarchies, and data leaks to unverified third-party cloud servers.**

Unlike typical file converters that require you to upload proprietary files to remote backends, WordToDocs parses binary OpenXML (`.docx`) archives **100% locally inside your browser memory**. It translates Microsoft Word markup into normalized, semantic HTML5 designed specifically for Google Docs' internal clipboard engine.

---

## 🌟 Key Features

- 🛡️ **100% Client-Side Execution (Zero Uploads)**:
  Your documents never leave your device. All parsing and DOM cleaning happen inside your browser's local sandbox memory. Disconnect your Wi-Fi after opening the page—it will still work perfectly.
- 📊 **Lossless Complex Table Preservation**:
  Retains nested cells, column widths, padding, multi-line row headers, and border alignments without collapsed borders or shifted text.
- 📋 **Native Google Docs Clipboard Bridge**:
  Injects properly sanitized `text/html` and `text/plain` payloads directly into the system clipboard via the native Web Async Clipboard API. Simply hit `Ctrl+V` (or `Cmd+V`) in Google Docs for instant, formatted paste.
- ⚡ **Google Drive Batch Conversion Generator**:
  Includes a built-in generator that crafts customized Google Apps Script code to batch-convert entire folders of `.docx` files directly inside Google Drive with zero manual intervention.
- 🌓 **Modern Responsive UI with Dark Mode**:
  Built with Tailwind CSS, supporting dark/light mode toggle, mobile drag-and-drop, real-time live preview, and live word counter.
- 🔍 **Technical SEO Optimized**:
  Full Schema.org JSON-LD structured data (`WebApplication` + `FAQPage`), canonical tags, Open Graph meta tags, and natural keyword density.

---

## 📊 Comparison: Why WordToDocs?

| Feature | WordToDocs.com | Native Google Drive Upload | Standard Online Converters |
| :--- | :---: | :---: | :---: |
| **Server Upload Required?** | ❌ **No (100% Local)** | ✅ Yes (Stored in Cloud) | ⚠️ Yes (Sent to 3rd-Party Servers) |
| **Confidential Data Privacy** | 🟢 **100% Private (GDPR/HIPAA safe)** | 🟡 Subject to Google Terms | 🔴 High Risk (Unknown server retention) |
| **Complex Table Fidelity** | 🟢 **Clean Semantic Tables** | 🔴 Merged cells often glitch | 🟡 Frequent border/padding loss |
| **Registration / Sign-up** | ❌ **Never** | ✅ Google Account required | ⚠️ Often requires email or credits |
| **Batch Migration Tool** | 🟢 **Built-in Apps Script Generator**| ❌ Manual single-file convert | 💳 Expensive monthly subscription |
| **Cost** | 🟢 **100% Free Forever** | 🟢 Free with Storage Limit | 🔴 Freely throttled / Watermarked |

---

## 🛠️ Tech Stack & Architecture

- **Core Engine**: Pure vanilla JavaScript (ES6+) with [Mammoth.js](https://github.com/mwilliamson/mammoth.js) (browser client-side edition).
- **Styling**: [Tailwind CSS](https://tailwindcss.com/) (delivered via fast CDN, no Node.js build step needed).
- **Clipboard Pipeline**: Native `navigator.clipboard.write([ClipboardItem])` with dual `text/html` & `text/plain` MIME dispatch.
- **Delivery Format**: Self-contained, single-file architecture (`index.html`).

```text
[ User .docx File ]
        │
        ▼ (Local FileReader ArrayBuffer)
[ Mammoth.js Client-Side Parser ]
        │
        ▼ (Raw HTML AST)
[ DOMParser & Semantic Cleaner ]
  ├── Normalize Table Borders & Cell Padding
  ├── Strip Microsoft Junk Spans & Font Tokens
  └── Enforce Clean Header Hierarchy (H1-H3)
        │
        ├──────────────────────────────┐
        ▼                              ▼
[ Live Interactive Preview ]     [ Native Async Clipboard API ]
                                       │
                                       ▼ (Ctrl+V / Cmd+V)
                                 [ Google Docs Canvas ]
```

---

## ⚡ Google Drive Batch Automation

If you have dozens or hundreds of `.docx` files already stored inside Google Drive, converting them manually takes hours. WordToDocs generates ready-to-run Google Apps Script:

1. In WordToDocs, switch to the **Drive Batch Script Generator** tab.
2. Enter your Drive Folder Name or ID.
3. Choose what to do with the original files (`Keep in place`, `Trash`, or `Move to Converted_Archive`).
4. Copy the generated script and open [script.google.com](https://script.google.com).
5. Paste into `Code.gs`, click **Services (+)**, add **Drive API (v2)**, and click **Run**.
6. Google Drive will automatically convert all `.docx` files into native Google Docs in the cloud.

---

## 🚀 Deployment Guide

### Method 1: GitHub Pages (Recommended)

This repository is already configured with a `CNAME` for `wordtodocs.com`.

1. Fork or push this repository to GitHub.
2. Go to **Settings** > **Pages**.
3. Under **Build and deployment**:
   - **Source**: `Deploy from a branch`
   - **Branch**: `main` / `/ (root)`
4. Custom Domain will automatically read `wordtodocs.com`.
5. Check **Enforce HTTPS** once your DNS records propagate.

#### DNS Records Configuration for Custom Domain:
| Type | Name / Host | Points to / Value |
| :--- | :--- | :--- |
| **A** | `@` | `185.199.108.153` |
| **A** | `@` | `185.199.109.153` |
| **A** | `@` | `185.199.110.153` |
| **A** | `@` | `185.199.111.153` |
| **CNAME** | `www` | `<your-username>.github.io` |

---

### Method 2: Cloudflare Pages / Vercel / Netlify

Because WordToDocs is a zero-dependency static project, you can deploy it on any modern hosting provider in 5 seconds:

- **Build command**: *(leave blank)*
- **Output directory**: `.` or `/`
- **Root directory**: `/`

---

## 📄 License

Distributed under the MIT License. See [`LICENSE`](LICENSE) for more information.

---

<div align="center">
  <sub>Maintained by the <a href="https://wordtodocs.com/">WordToDocs.com</a> team. Google Docs and Google Drive are trademarks of Google LLC.</sub>
</div>
