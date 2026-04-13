# 📋 ShiftBoard — Retail Staff Planner

A free, browser-based staff scheduling tool for retail teams. No server needed — runs entirely in the browser and saves data locally.

---

## 🚀 Getting Started on GitHub Pages

### Step 1 — Create a GitHub repository

1. Go to [github.com](https://github.com) and sign in (or create an account)
2. Click **New repository** (top-right `+` button)
3. Name it something like `shiftboard` or `staff-planner`
4. Set it to **Public** (required for free GitHub Pages)
5. Click **Create repository**

### Step 2 — Upload the file

1. Inside your new repo, click **Add file → Upload files**
2. Drag and drop `index.html` into the upload area
3. Scroll down and click **Commit changes**

### Step 3 — Enable GitHub Pages

1. In your repo, click **Settings** (top tab)
2. Scroll down to **Pages** in the left sidebar
3. Under **Source**, select **Deploy from a branch**
4. Under **Branch**, choose `main` and `/ (root)` then click **Save**
5. Wait ~1 minute, then your app will be live at:

```
https://YOUR-USERNAME.github.io/YOUR-REPO-NAME/
```

That's it — the app is now hosted and accessible from any device.

---

## 📥 Staff Import File Format

You can bulk-import staff using a plain `.txt` file. Download the template from the app (Import tab → **⬇ Template**) or create your own using this format:

```
# Lines starting with # are comments and are ignored
# Format: Name | Skills | Start | End

Alice Johnson   | till, floor, supervisor | 09:00 | 17:30
Bob Smith       | stock, delivery         | 06:00 | 14:00
Carol White     | floor, fitting, service | 10:00 | 18:00
David Brown     | till, floor             | 12:00 | 20:00
Emma Wilson     | supervisor, till        | 08:00 | 16:00
```

### Rules
| Field | Details |
|-------|---------|
| **Name** | Full name of the staff member |
| **Skills** | Comma-separated list (see below) |
| **Start** | 24-hour format, e.g. `09:00` or `9:00` |
| **End** | 24-hour format, e.g. `17:30` |

### Available Skills

| Skill ID | Zone Assigned To |
|----------|-----------------|
| `till` | Checkout / Till |
| `floor` | Shop Floor |
| `stock` | Stock Room |
| `fitting` | Fitting Rooms |
| `service` | Customer Service |
| `supervisor` | Flexible — fills where needed most |
| `delivery` | Delivery / Goods In |

- Staff can have **multiple skills** — the planner uses them all
- Skills earlier in the list have higher priority when assigning zones
- A supervisor or multi-skilled member will be assigned based on what the floor needs most

---

## 🗓️ How the Planner Works

### Time slots
- The schedule is broken into **30-minute intervals**
- The visual grid shows every slot for the full day
- Times outside a staff member's shift show blank

### Break scheduling
- Staff on shifts **longer than 4 hours** automatically receive a break
- Default break is **45 minutes** (shown as 2 slots in the grid for clarity — exact times shown on hover and in Print view)
- Break is placed at the **midpoint of each shift**, within the configurable break window (default 11:00–15:00)

### Zone assignment
- Each time slot, the planner assigns every working staff member to the best zone for their skills
- **Minimum coverage** is respected first (e.g. Till always has at least 1 person if available)
- After minimums are met, remaining staff are assigned based on best skill match
- If a staff member has no skills that match any zone, they're assigned to the highest-priority zone

---

## ⚙️ Settings

Available under the **Settings** tab:

| Setting | Default | Description |
|---------|---------|-------------|
| Day Start | 08:00 | Start of the planning day |
| Day End | 21:00 | End of the planning day |
| Break Length | 45 min | Duration of each staff break |
| Earliest Break | 11:00 | Earliest a break can start |
| Latest Break End | 15:00 | Latest a break can end |
| Min Shift for Break | 4 hrs | Shortest shift that gets a break |
| Zone minimums | Varies | Min staff required per zone per slot |

---

## 💾 Saving & Exporting

- All data **auto-saves** in your browser's local storage
- Use **Settings → Export JSON** to back up your staff list and schedule
- Use **Settings → Import JSON** to restore a backup
- The **Print** tab shows individual cards per staff member — use your browser's print function (`Ctrl/Cmd + P`) to print or save as PDF

---

## 📝 Tips

- **Add a role** (optional) to each staff member — it appears on printed schedules
- You can **edit any staff member** at any time — just regenerate the schedule after changes
- If two staff members have the same name, the import will skip the duplicate
- The colour assigned to each staff member is just for the grid — it doesn't mean anything

---

## 🛠️ Customising

The entire app is in one file (`index.html`). To change zone names, colours, or default settings, open the file in any text editor and look for the `DEFAULT_ZONES` and `SKILLS` arrays near the top of the `<script>` section.
