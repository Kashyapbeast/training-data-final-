# SMC L&D — Learning Analytics Desk

A single-page dashboard (`index.html`) covering:

- Monthly footfall (Footfall.xlsx)
- Regional performance (Region_Wise.csv)
- Department performance, top 12 + full sortable/searchable table (Department_Wise.csv)
- Pre vs post evaluation by trainer (Pre___Post_data.xlsx → Sheet1)
- Trainer feedback ratings + response volume (Feedback_to_be_calculated.xlsx → "Final feedback")

Every chart card is clickable and opens its source Google Sheet in a new tab.

## 1. Add your Google Sheets links

Open `index.html`, search for `SHEET_LINKS` near the bottom (inside the
`<script>` tag), and replace each placeholder with the real, shareable
URL of the matching Google Sheet:

```js
const SHEET_LINKS = {
  footfall:   "https://docs.google.com/spreadsheets/d/PASTE_FOOTFALL_SHEET_LINK_HERE/edit",
  region:     "https://docs.google.com/spreadsheets/d/PASTE_REGION_WISE_SHEET_LINK_HERE/edit",
  department: "https://docs.google.com/spreadsheets/d/PASTE_DEPARTMENT_WISE_SHEET_LINK_HERE/edit",
  prepost:    "https://docs.google.com/spreadsheets/d/PASTE_PRE_POST_SHEET_LINK_HERE/edit",
  feedback:   "https://docs.google.com/spreadsheets/d/PASTE_FEEDBACK_SHEET_LINK_HERE/edit",
  responses:  "https://docs.google.com/spreadsheets/d/PASTE_FEEDBACK_SHEET_LINK_HERE/edit"
};
```

If a sheet's sharing setting is "Restricted," only people already given
access will be able to open it after clicking through — set it to
"Anyone with the link" if you want any viewer of the site to open it.

## 2. Publish on GitHub Pages

1. Create a new GitHub repo (e.g. `smc-lnd-dashboard`).
2. Upload `index.html` to the repo root (drag-and-drop on github.com works fine).
3. Go to **Settings → Pages**.
4. Under **Build and deployment → Source**, choose **Deploy from a branch**.
5. Branch: `main`, folder: `/ (root)` → **Save**.
6. After ~1 minute your site is live at:
   `https://<your-username>.github.io/smc-lnd-dashboard/`

No build step, no dependencies to install — it's a static file that
loads Chart.js and fonts from public CDNs.

## 3. Updating the data later

All chart data is inlined as plain JS objects/arrays near the top of
the `<script>` tag (`FOOTFALL`, `REGION`, `DEPARTMENT`, `PREPOST`,
`FEEDBACK`). Edit those values directly and commit — no rebuild needed.
