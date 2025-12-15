# MangaDex Read Status Filter for Advanced Search

[![Tampermonkey](https://img.shields.io/badge/Tampermonkey-Userscript-blue?logo=tampermonkey)](https://www.tampermonkey.net/)
[![JavaScript](https://img.shields.io/badge/JavaScript-ES6-yellow?logo=javascript)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)

Tampermonkey userscript that adds a **filter based on user reading status** (Reading, Completed, Dropped, etc.) to the **MangaDex Advanced Search** page.  
This script helps users filter manga according to the statuses stored in their MangaDex account.

---

## ✨ Features
- Adds a **Read Status** dropdown next to the Reset filter button.
- Supported statuses:
  - All
  - Not Added
  - Reading
  - On Hold
  - Plan to Read
  - Dropped
  - Re‑Reading
  - Completed
- **Apply** button to instantly hide/show manga according to status.
- **Set Config** button to save MangaDex OAuth credentials (username, password, client_id, client_secret).
- Configuration is stored **persistently** using Tampermonkey storage.
- Filter remains active when:
  - Navigating **Back/Forward** in the browser.
  - Switching pages (page=1 → page=2, etc.).
- Automatically reapplies the last selected status after reload/back/page change.
- Interactive popup with animations for configuration and notifications.

---

## 📦 Installation
1. **Install Tampermonkey**
   - Download and install [Tampermonkey](https://www.tampermonkey.net/) in your browser.

2. **Obtain MangaDex Credentials**
   - Visit [MangaDex API Personal Clients](https://api.mangadex.org/docs/02-authentication/personal-clients).
   - Log in with your MangaDex account.
   - Create a **Personal Client**.
   - Save the following information:
     - `client_id`
     - `client_secret`
   - Make sure you also know your MangaDex **username** and **password**.

3. **Install the Script**
   - Install the script directly from [GreasyFork](https://greasyfork.org/en/scripts/559036-mangadex-read-status-filter-for-advanced-search).
   
   <img width="1532" height="723" alt="image" src="https://github.com/user-attachments/assets/04073568-60c4-4ac1-a98a-93ff5bcc22da" />
4. **Configure the Script**
   - Open the [MangaDex Advanced Search](https://mangadex.org/titles) page.
   - Click the **Set Config** button.
   - Enter:
     - Username
     - Password
     - Client ID
     - Client Secret
   - Click **Save** → credentials are stored in Tampermonkey.
   - Refresh the page to log in again.

5. **Use the Filter**
   - Select a reading status from the **Read Status** dropdown.
   - Click **Apply** → manga will be filtered accordingly.
   - Navigate to other pages (page=2, page=3, etc.) → filter is automatically reapplied.
   - Click **Reset filters** to clear all filters.

---

## 🛠️ Technology
- **Tampermonkey API**: `GM_xmlhttpRequest`, `GM_setValue`, `GM_getValue`
- **MangaDex API**:
  - `POST /token` for login
  - `GET /manga/status` for bulk status
  - `GET /manga/status?statuses[]=` for filtered status
- **JavaScript ES6** with async/await
- **MutationObserver** to detect MangaDex SPA navigation
- **History API** (`pushState`, `replaceState`, `popstate`) to detect page changes

---

## 📖 Example Screenshots
- **Read Status** dropdown and other buttons next to Reset button  
  <img width="1048" height="235" alt="image" src="https://github.com/user-attachments/assets/db44ae21-a10c-4c1c-89dd-bd5dff9ada55" />

- **Set Config** popup for credentials  
  <img width="464" height="498" alt="image" src="https://github.com/user-attachments/assets/70dc70da-ffd0-43a8-97dc-23b5fd21532c" />

---

## 👤 Credit
- Author: **dapakyuu**
- GitHub: [https://github.com/dapakyuu/mangadex_readstatus_filter](https://github.com/dapakyuu/mangadex_readstatus_filter)

---

## 📜 License
MIT License – free to use, modify, and distribute with proper credit.

---

## 📝 Additional Notes
- This script requires a MangaDex account and OAuth credentials to fetch reading statuses.
- If the manga list is still loading, the filter will retry automatically after a few seconds.
- Future improvements may include:
  - Adding a loading indicator when applying filters.
  - Saving filter preferences per user.
  - Integration with favorite manga lists.
