# TEP Distribution — Time Clock

A self-contained, single-file web app for tracking employee clock-in/clock-out times. No backend, no installation, no dependencies. Open the HTML file in a browser and go.

Built for TEP Distribution LLC. Runs on any modern browser. Designed for a single shared workstation where employees clock in/out and admins manage the workforce.

---

## Features

**For employees**
- Tile-grid selection — tap your name to begin
- PIN-protected clock in / clock out (4–6 digit PIN)
- Live elapsed timer while clocked in
- Status indicator showing who's currently on the clock

**For admins (PIN-gated)**
- Add, edit, and delete employees with role and PIN
- KPI dashboard: total employees, currently clocked in, weekly hours, monthly hours
- Monthly calendar view with hours per day, filterable by employee
- Click any day to drill into individual entries
- Edit or delete any time entry (with audit "edited" badge)
- CSV export for payroll
- Configurable admin PIN and company name

**Design**
- Dark neon-blue theme matching TEP Distribution branding
- Live clock in the header
- Responsive — works on desktop, tablet, and mobile
- Toast notifications for every action

---

## Quick start

1. **Download** `index.html`
2. **Open** it in any modern browser (Chrome, Firefox, Safari, Edge)
3. **Bookmark** it for one-click access
4. Default admin PIN is `1234` — change it immediately under Admin → Settings

That's it. No installation, no server, no accounts.

---

## How data is stored

All data lives in the browser's **`localStorage`**. This means:

- ✅ Data persists across browser closes, computer restarts, and weeks of use
- ✅ No internet connection needed
- ✅ No data leaves the machine
- ⚠️ Data is tied to **one browser on one computer**. Different machines have separate data.
- ⚠️ Clearing browser cache/site data will wipe everything. Export CSV regularly.

**Recommended setup:** dedicate one PC or tablet near the clock-in station. Bookmark `index.html`. All employees use that same browser.

---

## Deployment options

### Option 1: Local file (simplest, recommended)

Download `index.html` and open it directly. Bookmark `file:///path/to/index.html`. Done.

### Option 2: GitHub Pages (free hosting)

1. Push this repo to GitHub
2. Settings → Pages → Source: `main` branch, `/` (root)
3. Your app is live at `https://YOUR-USERNAME.github.io/tep-timeclock/`

Still uses localStorage per-browser. Different devices = different data.

### Option 3: Netlify drag-and-drop

Drop `index.html` on [app.netlify.com/drop](https://app.netlify.com/drop). Get a URL instantly. Same per-browser data behavior.

### Option 4: Multi-device sync (advanced)

If you need data shared across multiple computers/phones, the app needs a real backend. See `MIGRATION.md` (or open an issue) for the Supabase migration path — roughly 30 minutes of work.

---

## Usage

### Setting up employees

1. Click **Admin** tab
2. Enter admin PIN (`1234` by default — change it in Settings)
3. Click **+ Add Employee**
4. Enter name, role, and a 4–6 digit PIN they'll remember
5. Repeat for each team member

### Daily clock in/out

1. Employee clicks the **Clock In/Out** tab (or just the bookmark loads here)
2. Taps their tile
3. Enters their PIN
4. Hits the big **CLOCK IN** button (or **CLOCK OUT** if already in)

### Payroll workflow

1. Friday afternoon → open the app on the admin PC
2. **Admin → Recent Entries → Export CSV**
3. Open in Excel/Sheets, pivot by employee, send to bookkeeper

### Editing time entries

Mistake on a clock-out? Forgot to clock in?

1. Admin → scroll to the **Schedule Calendar** or **Recent Entries**
2. Click the entry → **Edit**
3. Adjust clock-in or clock-out times
4. Save — entry is flagged with an "edited" badge for the audit trail

---

## File structure

```
tep-timeclock/
├── index.html      # The entire app — HTML, CSS, JS in one file
├── README.md       # You are here
├── LICENSE         # MIT
└── .gitignore
```

That's the whole project. No `node_modules`, no build step, no dependencies beyond Google Fonts (loaded from CDN at runtime).

---

## Security notes

- **Admin PIN gates the admin panel.** All admins share the same PIN. Fine for a small operation; not appropriate for 50+ people.
- **Employee PINs gate clock-in/out.** They're stored locally in plaintext. If you need real authentication, this app isn't the right tool.
- **Anyone with browser access can see the employee list.** Don't put this on a public kiosk without a screen lock.
- **No transmission of data anywhere.** Everything stays in localStorage on that one machine.

---

## Browser compatibility

Tested on:
- Chrome / Edge 90+
- Firefox 88+
- Safari 14+

Requires:
- localStorage support (universal since ~2010)
- ES6+ JavaScript (universal since ~2017)
- CSS custom properties (universal since ~2018)

Should work on anything made in the last 8 years.

---

## Roadmap

Possible additions if/when needed:
- Geofencing (GPS check on clock-in to prevent buddy-punching)
- Break tracking (clock out for lunch, auto-deduct)
- Overtime alerts
- Photo verification (selfie on clock-in)
- Multi-device sync via Supabase backend
- QuickBooks / Gusto / ADP payroll integration

---

## License

MIT — see `LICENSE` file.

---

## Built for TEP Distribution LLC

Single-purpose tool, intentionally minimal. If it ever feels like the wrong shape for what you need, fork it or replace it. The whole app is in one HTML file — easy to read, easy to modify.
