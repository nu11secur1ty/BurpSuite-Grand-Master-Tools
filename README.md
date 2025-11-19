<!-- HERO / HEADER -->
<p align="center">
  <img alt="BurpSuite-Grand-Master-Tools" src="https://github.com/nu11secur1ty/BurpSuite-Grand-Master-Tools/blob/main/docs/wallpaper.png" width="795" />
</p>

<h1 align="center">BurpSuite-Grand-Master-Tools</h1>

<p align="center">
  <strong>By <code>nu11secur1ty</code></strong> — A modular toolkit that transforms Burp captures into instant, repeatable actions.  
  <em>Convert. Reuse. Open. Automate.</em>
</p>

<p align="center">
  <!-- Badges (replace with actual links) -->
  <img alt="GitHub release" src="https://img.shields.io/badge/release-v1.0-blue.svg" />
  <img alt="License" src="https://img.shields.io/badge/license-MIT-brightgreen.svg" />
  <img alt="Python" src="https://img.shields.io/badge/python-3.8%2B-yellow.svg" />
  <a href="https://github.com/nu11secur1ty/BurpSuite-Grand-Master-Tools/stargazers"><img alt="GitHub stars" src="https://img.shields.io/github/stars/nu11secur1ty/BurpSuite-Grand-Master-Tools?style=social" /></a>
</p>

---

## 🚀 Elevator pitch

**BurpSuite-Grand-Master-Tools** is a lightweight, auditable, and extensible toolkit for pentesters and bug bounty hunters. Start fast with tools like **Nu11Request** — convert Burp-captured HTTP requests into real, browsable URLs with one click — then build an arsenal of modules to automate the rest of your Burp workflow.

---

## ✨ Why it matters

- Save time reconstructing request targets and query payloads.  
- Reproduce and validate findings in a real browser quickly.  
- Keep raw requests saved and auditable for reporting and collaboration.  
- Minimal, auditable Python scripts — easy to review, fork, and extend.

---

## 🔧 Core features (v1.0)

- **Nu11Request**: Paste a Burp request → save it → generate an opener script that builds the full URL and opens it in your browser.  
- Supports both **absolute-form** and **origin-form** request-targets.  
- Honors `:scheme` and `X-Forwarded-Proto` headers when present.  
- Safe-by-default: opener does **not** send network requests — it only opens constructed URLs.  
- Pure Python (standard library) — no heavy dependencies.

---

## 📦 Quick start

```bash
# 1. clone the repo
git clone https://github.com/nu11secur1ty/BurpSuite-Grand-Master-Tools.git
cd BurpSuite-Grand-Master-Tools

# 2. run the generator and paste a Burp GET request (end with a single line containing ".")
python make_request_and_url_opener.py

# 3. run the generated opener script (example: open_request_url.py)
python open_request_url.py
