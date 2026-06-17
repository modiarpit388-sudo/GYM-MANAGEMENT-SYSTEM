# GYM-MANAGEMENT-SYSTEM# 🏋️ Enhanced Gym Attendance Management System

A modern and responsive Gym Attendance Management System built with **Flask**, **SQLite**, **HTML**, **CSS**, and **Bootstrap 5**.

---

## ✨ Features

✅ Secure Login Authentication

✅ Interactive Dashboard

✅ Add Attendance Records

✅ View Attendance History

✅ Session-Based Logout

✅ SQLite Database Integration

✅ Responsive Modern UI

✅ Easy Deployment

---

## 📸 Project Preview

### Login Page

* Modern glassmorphism design
* Secure authentication
* Responsive layout

### Dashboard

* Attendance statistics
* Quick navigation cards
* User-friendly interface

### Attendance Records

* Add new attendance
* View attendance history
* Organized data table

---

## 🏗️ System Architecture

```text
┌─────────────────┐
│      User       │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  Web Browser    │
└────────┬────────┘
         │ HTTP Request
         ▼
┌─────────────────┐
│   Flask Server  │
│     app.py      │
└────────┬────────┘
         │
 ┌───────┴────────┐
 │                │
 ▼                ▼
Templates      SQLite DB
(HTML/CSS)    database.db
 │                │
 └───────┬────────┘
         ▼
  Attendance Data
```

---

## 📂 Project Structure

```text
gym-attendance-system/
│
├── app.py
├── config.py
├── requirements.txt
├── README.md
├── database.db
│
├── static/
│   ├── css/
│   │   └── style.css
│   │
│   ├── js/
│   │   └── main.js
│   │
│   └── images/
│       ├── logo.png
│       └── gym-bg.jpg
│
├── templates/
│   ├── base.html
│   ├── login.html
│   ├── dashboard.html
│   └── attendance.html
│
└── database/
    └── init_db.py
```

---

## ⚙️ Technologies Used

| Technology  | Purpose              |
| ----------- | -------------------- |
| Python      | Backend Logic        |
| Flask       | Web Framework        |
| SQLite      | Database             |
| HTML5       | Structure            |
| CSS3        | Styling              |
| Bootstrap 5 | Responsive Design    |
| JavaScript  | Frontend Interaction |

---

## 🔐 Login Credentials

```text
Username : admin
Password : admin1234
```

---

## 🚀 Installation Guide

### 1️⃣ Clone Repository

```bash
git clone https://github.com/yourusername/gym-attendance-system.git
```

### 2️⃣ Move Into Project

```bash
cd gym-attendance-system
```

### 3️⃣ Install Dependencies

```bash
pip install flask
```

or

```bash
pip install -r requirements.txt
```

### 4️⃣ Run Application

```bash
python app.py
```

### 5️⃣ Open Browser

```text
http://127.0.0.1:5000
```

---

## 🗄️ Database Design

### Attendance Table

| Column      | Type    |
| ----------- | ------- |
| id          | INTEGER |
| member_name | TEXT    |
| date        | TEXT    |

---

## 🔄 Application Flow

```text
Login
  │
  ▼
Dashboard
  │
  ├── Add Attendance
  │
  ├── View Records
  │
  └── Logout
```

---

## 🎨 UI Highlights

* Clean Dashboard Cards
* Modern Gradient Backgrounds
* Responsive Layout
* Mobile Friendly Design
* Professional Color Palette
* Easy Navigation

---

## 🌟 Future Enhancements

* Member Registration
* QR Code Attendance
* Attendance Analytics
* Email Notifications
* PDF Report Generation
* Admin Role Management

---

## 👨‍💻 Author

Developed using Flask and SQLite for learning and portfolio purposes.

---

## 📜 License

This project is open-source and available under the MIT License.
