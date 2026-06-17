<div align="center">

<img src="https://img.shields.io/badge/⚡-GymPulse-5b6bff?style=for-the-badge&labelColor=080b12&color=5b6bff" alt="GymPulse" height="42"/>

# GymPulse — Gym Attendance Management System

**A modern, dark-themed gym management web app built with Flask & SQLite.**  
Track members, log attendance, and visualize your gym's activity — all from one slick dashboard.

[![Python](https://img.shields.io/badge/Python-3.8+-3776AB?style=flat-square&logo=python&logoColor=white)](https://python.org)
[![Flask](https://img.shields.io/badge/Flask-2.3+-000000?style=flat-square&logo=flask&logoColor=white)](https://flask.palletsprojects.com)
[![SQLite](https://img.shields.io/badge/SQLite-3-003B57?style=flat-square&logo=sqlite&logoColor=white)](https://sqlite.org)
[![License](https://img.shields.io/badge/License-MIT-22c55e?style=flat-square)](LICENSE)
[![Status](https://img.shields.io/badge/Status-Active-22c55e?style=flat-square)]()

</div>

---

## ✨ Features

| Feature | Description |
|---|---|
| 🔐 **Secure Login** | Session-based admin authentication with password visibility toggle |
| 📊 **Live Dashboard** | Animated KPI cards, weekly activity bar chart, membership donut chart |
| 👥 **Member Management** | Add, search, filter, toggle active/inactive, delete members with fitness goals |
| ✅ **Attendance Logging** | Check-in / check-out with session notes and auto-prefilled timestamps |
| ⏱️ **Duration Tracking** | Auto-computed session durations per visit |
| 📅 **Smart Filters** | Filter attendance by member name or date |
| 🌙 **Dark Theme** | Deep steel dark UI with electric violet gradients and neon green accents |
| 📱 **Responsive** | Mobile-friendly layout with collapsible sidebar |
| ⚡ **Live Clock** | Real-time clock in the topbar, updates every second |
| 🎯 **Fitness Goals** | Track each member's goal: Weight Loss, Muscle Gain, Cardio, etc. |

---

## 🖼️ Screenshots

> **Dashboard** — KPI cards with animated counters, canvas-rendered charts, top member leaderboard

```
┌──────────────────────────────────────────────────────────────────┐
│  ⚡ GymPulse         Dashboard        Thu, 18 Jun 2026  ● Live  │
├──────────┬───────────────────────────────────────────────────────┤
│          │  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌─────────┐ │
│ ◈ Dash   │  │  Total   │ │  Active  │ │  Today   │ │  Total  │ │
│ ◉ Members│  │ Members  │ │ Members  │ │ Check-ins│ │Check-ins│ │
│ ◎ Attend │  │   126    │ │   118    │ │    24    │ │   892   │ │
│          │  └──────────┘ └──────────┘ └──────────┘ └─────────┘ │
│ ─────── │  ┌─────────────────────────┐ ┌──────────────────────┐ │
│  Admin   │  │   Weekly Activity       │ │  Membership Split    │ │
│  Online  │  │  ▁▃▅▇▅▆█              │ │     ◉ Donut chart    │ │
│          │  └─────────────────────────┘ └──────────────────────┘ │
│ ↩ Logout │  Recent Check-ins · Top Members · Quick Actions      │
└──────────┴───────────────────────────────────────────────────────┘
```

---

## 🚀 Quick Start

### 1. Clone the repo

```bash
git clone https://github.com/yourusername/gym-attendance.git
cd gym-attendance
```

### 2. Install dependencies

```bash
pip install flask
```

Or with a virtual environment (recommended):

```bash
python -m venv venv
source venv/bin/activate        # Linux / macOS
venv\Scripts\activate           # Windows

pip install -r requirements.txt
```

### 3. Run the app

```bash
python app.py
```

### 4. Open in your browser

```
http://127.0.0.1:5000
```

---

## 🔑 Default Login

| Field | Value |
|---|---|
| **Username** | `admin` |
| **Password** | `admin1234` |

> 💡 Change `ADMIN_USER` and `ADMIN_PASS` in `app.py` before deploying.

---

## 📁 Project Structure

```
gym-attendance/
│
├── app.py                  # Flask application & routes
├── requirements.txt        # Python dependencies
├── README.md               # This file
├── .gitignore
│
├── templates/
│   ├── base.html           # Base layout (sidebar, topbar, flash messages)
│   ├── login.html          # Split-screen login page with animated orbs
│   ├── dashboard.html      # KPI cards, charts, activity feed
│   ├── members.html        # Member cards with inline status toggle
│   └── attendance.html     # Attendance log table with duration calculator
│
└── static/
    ├── css/
    │   └── style.css       # Full dark theme (500+ lines, CSS custom props)
    └── js/
        └── main.js         # Live clock, chart renderers, counter animations
```

---

## 🗄️ Database Schema

The app uses **SQLite** (auto-created as `gym.db` on first run) with two tables:

```sql
-- Members table
CREATE TABLE members (
    id              INTEGER PRIMARY KEY AUTOINCREMENT,
    name            TEXT NOT NULL,
    email           TEXT UNIQUE NOT NULL,
    phone           TEXT,
    membership_type TEXT DEFAULT 'Monthly',   -- Monthly | Quarterly | Annual
    join_date       TEXT NOT NULL,
    status          TEXT DEFAULT 'Active',    -- Active | Inactive
    goal            TEXT DEFAULT 'General Fitness',
    avatar_color    TEXT DEFAULT '#5b6bff'    -- Random accent per member
);

-- Attendance table
CREATE TABLE attendance (
    id          INTEGER PRIMARY KEY AUTOINCREMENT,
    member_id   INTEGER NOT NULL REFERENCES members(id),
    check_in    TEXT NOT NULL,    -- HH:MM
    check_out   TEXT,             -- HH:MM (nullable if still in gym)
    date        TEXT NOT NULL,    -- YYYY-MM-DD
    notes       TEXT              -- Optional session notes
);
```

> **Demo data** is seeded automatically on first launch: 6 members + sample attendance records so the dashboard looks alive immediately.

---

## 🛣️ Routes

| Method | Route | Description |
|---|---|---|
| `GET / POST` | `/` | Login page |
| `GET` | `/logout` | Clear session |
| `GET` | `/dashboard` | Main dashboard with stats & charts |
| `GET / POST` | `/members` | List + add members |
| `POST` | `/members/delete/<id>` | Delete member + their records |
| `POST` | `/members/toggle/<id>` | Toggle Active ↔ Inactive (AJAX) |
| `GET / POST` | `/attendance` | List + log attendance |
| `POST` | `/attendance/delete/<id>` | Delete attendance record |

---

## 🎨 Design System

The UI is built on a custom dark design system with CSS custom properties:

```css
--bg:       #080b12   /* Page background — deep space */
--bg2:      #0e1117   /* Cards and sidebar */
--blue:     #5b6bff   /* Primary accent */
--violet:   #7c3aed   /* Gradient partner */
--green:    #22c55e   /* Success / active states */
--orange:   #f97316   /* Warning / highlight */
--purple:   #a855f7   /* Charts and badges */
```

**Typography:**
- Display / headings → `Space Grotesk` (800 weight, tight letter-spacing)
- Body / UI → `Inter` (400–600 weight)

**Signature element:** Canvas-rendered charts (no Chart.js dependency) — a bezier-curve area chart for weekly activity and a segmented donut for membership breakdown, both drawn in pure vanilla JS.

---

## ⚙️ Configuration

All config lives at the top of `app.py`:

```python
app.secret_key = 'gym_secret_key_2024'   # Change this!
DB_PATH        = 'gym.db'
ADMIN_USER     = 'admin'
ADMIN_PASS     = 'admin1234'
```

---

## 📦 Dependencies

```
flask>=2.3.0
```

That's it. No ORM, no heavy frontend framework, no paid libraries. Pure Flask + SQLite + vanilla JS.

---

## 🛡️ Security Notes

- Sessions use Flask's signed cookie store — change `secret_key` in production
- No user registration — single hardcoded admin account
- SQL queries use parameterized statements (no injection risk)
- Passwords are compared in plaintext — suitable for local/internal use only

---

## 🗺️ Roadmap

- [ ] Member profile photos
- [ ] Export attendance to CSV / PDF
- [ ] Email / SMS check-in reminders
- [ ] Multi-staff login with role levels
- [ ] Monthly revenue tracking
- [ ] Mobile PWA support

---

## 🤝 Contributing

Pull requests are welcome! For major changes, open an issue first.

```bash
# Fork → clone → branch → commit → push → PR
git checkout -b feature/your-feature
git commit -m "feat: add your feature"
git push origin feature/your-feature
```

---

## 📄 License

MIT © 2024 — free to use, modify, and distribute.

---

<div align="center">

Built with ⚡ Flask · SQLite · Vanilla JS · Pure CSS

**[⭐ Star this repo](https://github.com/yourusername/gym-attendance)** if it helped you!

</div>
