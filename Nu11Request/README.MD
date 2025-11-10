
# Nu11Request — Burp-to-Browser Request Opener

**by nu11secur1ty**

---

## Overview

**Nu11Request** is a lightweight, auditable Python utility that converts raw HTTP requests (copied or exported from tools like Burp Suite or browser developer tools) into a saved request file and a one‑click "opener" script. The opener script parses the saved request, constructs the equivalent full URL (using either an absolute request-target or Host + path), and opens that URL in the user's default web browser.

This tool is ideal for pentesters, bug bounty hunters, and web developers who need a quick, repeatable way to validate reflected payloads, redirects, and encoded query strings in a real browser environment.

---

## Features

- Interactive paste interface: paste a raw HTTP request and terminate with a single `.` on its own line.
- Saves the original raw request to disk for auditing and reuse.
- Generates a standalone opener script that:
  - Parses the request-line and headers.
  - Builds a full URL (absolute request-target or `Host + path`).
  - Honors `:scheme` and `X-Forwarded-Proto` headers when present.
  - Prompts for confirmation before opening the URL.
- Cross-platform: works on Windows, macOS, and Linux (opens the system default browser).
- Minimal dependencies: generator and opener rely on Python standard library only (no extra pip packages required).
- Safe-by-default: the opener constructs and opens URLs but does **not** send network requests (unless you extend it).

---

## Quick Start

1. Save the generator script (for example, `Nu11Request.py`) that was provided with this project.

2. Run the generator:
   ```bash
   python Nu11Request.py
   ```

3. Paste your raw HTTP request (e.g. from Burp). End the paste with a single line containing only:
   ```
   .
   ```

4. Accept default filenames or provide your own when prompted. The generator will:
   - Save the raw request to a text file (default `saved_request.txt`).
   - Create the opener script (default `open_request_url.py` or the name you choose).

5. Run the opener to construct and open the URL:
   ```bash
   python open_request_url.py
   ```
   Confirm when prompted and the target URL will open in your browser.

---

## Example Workflow

- Capture a reflected XSS payload or open-redirect URL in Burp.
- Copy the raw GET request from Burp and paste it into the generator.
- Run the generated opener script to immediately open the exact encoded URL in a real browser and verify visual rendering or redirect behavior.

---

## Security & Responsible Use

- **Only** test systems you own or have explicit permission to test.
- The base opener **does not** actively send or automate attacks — it simply opens constructed URLs in a browser — but any extensions that send requests (e.g., via `requests`) change the risk profile.
- Use discretion when opening payloads that may contain explicit content, tracking resources, or external mixed content.

---

## Extensibility Ideas

- Optional `requests`-based mode to fetch the response and open the returned HTML locally (useful for non-GET requests).
- Toggle to automatically try `http://` if `https://` fails.
- GUI front-end (Tkinter or a small Flask web UI) for managing multiple saved requests and one-click opening.
- Batch mode to generate openers for multiple saved requests in a directory.

---

## Developer Notes

- Parsing supports both absolute-form and origin-form request-targets.
- Default URL scheme is `https` unless `:scheme` or `X-Forwarded-Proto` is present.
- The generator is intentionally simple and produces small, readable Python scripts that are easy to review and adapt.

---

## License

MIT License — feel free to fork and adapt. Include attribution to **nu11secur1ty** when publishing derived works.

```
MIT License

Copyright (c) 2025 nu11secur1ty

Permission is hereby granted, free of charge, to any person obtaining a copy
...
```

(Include a full MIT text in your repo if you publish publicly.)

---

## Attribution & Contact

**Nu11Request** — by **nu11secur1ty**  
For improvements, feature requests, or contributions, open an issue or submit a pull request on the project's repository.

