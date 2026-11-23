# Movie Box Unlocker

A Chrome / Edge / Brave / Chromium extension that intercepts `fetch` and `XMLHttpRequest` **in the page's own JavaScript context** and rewrites responses according to your rules.

## Install

1. Unzip or open this folder
2. Open Chrome → `chrome://extensions`
3. Enable **Developer mode** (top right)
4. Click **Load unpacked**
5. Select the project folder

## Features

- **Main-world injection** – intercepts the page’s own `fetch` / XHR (not just the content-script sandbox)
- **Built-in VIP rules** – automatically unlocks VIP/ad-free features on supported platforms
- **Popup** – quick toggle + rule list
- **Full dashboard in a separate tab** – click **Open in tab** in the popup, or right-click the icon → Options
- Match by URL / host / path (contains, equals, wildcard, regex)
- Method filter + status code override
- Static body or dynamic JS script
- Pure mock mode (no network request)
- Export / import rules as JSON
- Sample rules included

## How to open the full UI in a tab

- Click the extension icon → **Open in tab**
- Or: `chrome://extensions` → Movie Box Unlocker → **Details** → **Extension options**
- Or right-click the toolbar icon → **Options**

## Quick test

1. Make sure Interceptor is **ON**
2. Create a rule:
   - Match value: `httpbin.org/json` (contains)
   - Method: GET
   - Body mode: Static
   - Static body: `{"hello":"from Movie Box Unlocker"}`
   - Check **Serve without real request**
3. Open a new tab → DevTools → Console:
   ```js
   fetch("https://httpbin.org/json").then(r => r.json()).then(console.log)
   ```
4. You should see `{"hello":"from Movie Box Unlocker"}` instead of the real response.

## Notes

- Works on almost all sites. A few sites with strict CSP may block the injected script; refresh the page after installing.
- Does not intercept WebSockets or Service Worker requests.
- Rules live in `chrome.storage.local`.

## Uninstall

`chrome://extensions` → Movie Box Unlocker → Remove
