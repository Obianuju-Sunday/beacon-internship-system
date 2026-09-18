# BEACON - Student Internship & Skill Profiling System

A full-stack web application connecting students with internship opportunities and organizations looking to recruit talented interns. Built with Node.js, Express, PostgreSQL, and EJS.

🔗 **Live Demo:** https://internship-system-j3su.onrender.com

![App Homepage](images/homepage.png)

---

## 📋 Table of Contents

- [BEACON - Student Internship \& Skill Profiling System](#beacon---student-internship--skill-profiling-system)
  - [📋 Table of Contents](#-table-of-contents)
  - [✨ Features](#-features)
  - [🛠️ Tech Stack](#️-tech-stack)
  - [Database Schema](#database-schema)
  - [Prerequisites Installation](#prerequisites-installation)
    - [Install Node.js](#install-nodejs)
    - [Install PostgreSQL](#install-postgresql)
    - [Verify PostgreSQL is Running](#verify-postgresql-is-running)
  - [🚀 Setup Guide](#-setup-guide)
    - [Step 1: Extract the Project](#step-1-extract-the-project)
    - [Step 2: Install Dependencies](#step-2-install-dependencies)
    - [Step 3: Create the Database](#step-3-create-the-database)
    - [Step 4: Import Database Schema](#step-4-import-database-schema)
    - [Step 5: Configure Environment Variables](#step-5-configure-environment-variables)
    - [Step 6: Start the Application](#step-6-start-the-application)
    - [Step 7: Open in Browser](#step-7-open-in-browser)
  - [👤 Test Accounts](#-test-accounts)
  - [📸 Screenshots](#-screenshots)
  - [🔐 Security Features](#-security-features)
    - [Authentication](#authentication)
    - [Data Protection](#data-protection)
    - [API Security](#api-security)
    - [Database Security](#database-security)
  - [🛠️ Troubleshooting](#️-troubleshooting)
    - [Installation Issues](#installation-issues)
    - [Runtime Issues](#runtime-issues)
  - [📁 Project Structure](#-project-structure)
  - [👥 For Panel Members (Defence Evaluation)](#-for-panel-members-defence-evaluation)
    - [Quick Start (10 minutes)](#quick-start-10-minutes)
    - [Key Features to Demonstrate](#key-features-to-demonstrate)
  - [Key Learning Outcomes](#key-learning-outcomes)
  - [Future Improvements](#future-improvements)
  - [👩‍💻 Author](#-author)
  - [📜 License](#-license)

---

## ✨ Features

- **Student Registration & Authentication** - Secure signup with JWT tokens and bcrypt password hashing
- **Organization Registration** - Companies create profiles to post internship opportunities
- **Role-Based Access Control** - Different dashboards and permissions for students vs organizations
- **Internship Management** - Organizations can post, edit, and manage internship listings
- **Application System** - Students browse internships and apply with cover letters
- **Application Tracking** - Real-time status tracking (pending/accepted/rejected)
- **Skill Profiling** - Students add and manage skills with proficiency levels
- **Student Evaluation** - Organizations view student profiles with skills for informed hiring
- **Responsive Design** - Works seamlessly on desktop and mobile devices
- **Multi-Tab Security** - SessionStorage prevents account conflicts across browser tabs
- **Security** - Input validation, sanitization, SQL injection prevention, JWT authentication

---

## 🛠️ Tech Stack

**Backend:**
- Node.js (JavaScript runtime)
- Express.js (Web framework)
- PostgreSQL (Relational database)
- JWT (Stateless authentication)
- Bcrypt (Password hashing)
- Express-validator (Input validation)

**Frontend:**
- EJS (Server-side templating)
- HTML5 & CSS3
- Vanilla JavaScript
- SessionStorage (per-tab session management)

**Deployment:**
- Render (Cloud hosting)

---

## Database Schema

**7 tables with proper relationships:**

1. **users** - Authentication and role management
2. **student_profiles** - Student information and details
3. **organisation_profiles** - Company information
4. **skills** - Available skills catalog
5. **student_skills** - Student-skill relationships (many-to-many)
6. **internships** - Internship postings
7. **applications** - Student applications to internships

**Features:**
- Proper foreign keys for referential integrity
- UNIQUE constraints on critical fields
- CASCADE deletes for data consistency
- Normalized schema (3NF)

---

## Prerequisites Installation

Before running Beacon, install Node.js and PostgreSQL.

### Install Node.js

**For Windows:**
1. Visit https://nodejs.org/
2. Download LTS version (v16 or higher)
3. Run installer and follow prompts
4. Keep default settings
5. Verify in Command Prompt:
```bash
node --version
npm --version
```

**For Mac:**
```bash
# Using Homebrew (install if needed: /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)")
brew install node

# Verify
node --version
npm --version
```

**For Linux (Ubuntu/Debian):**
```bash
sudo apt update
sudo apt install nodejs npm

# Verify
node --version
npm --version
```

---

### Install PostgreSQL

**For Windows:**
1. Visit https://www.postgresql.org/download/windows/
2. Download PostgreSQL 12 or higher
3. Run installer
4. **IMPORTANT:** Remember the password for 'postgres' user (needed later!)
5. Keep default settings (port 5432)
6. Verify in Command Prompt:
```bash
psql --version
```

**For Mac:**
```bash
# Using Homebrew
brew install postgresql

# Start service
brew services start postgresql

# Verify
psql --version
```

**For Linux (Ubuntu/Debian):**
```bash
sudo apt update
sudo apt install postgresql postgresql-contrib

# Start service
sudo systemctl start postgresql
sudo systemctl enable postgresql

# Verify
psql --version
```

---

### Verify PostgreSQL is Running

**Linux/Mac:**
```bash
sudo systemctl status postgresql
```

**Windows:**
- Open Services app (services.msc)
- Look for "postgresql-x64-xx" and verify it's running
- OR test connection:
```bash
psql -U postgres -c "SELECT 1;"
```

---

## 🚀 Setup Guide

Once Node.js and PostgreSQL are installed, follow these 7 steps:

### Step 1: Extract the Project
```bash
cd /path/to/beacon-internship-system
```

### Step 2: Install Dependencies
```bash
npm install
# Downloads all required packages (2-3 minutes)
```

### Step 3: Create the Database
```bash
# Login to PostgreSQL
sudo -u postgres psql
# (On Windows: psql -U postgres)

# Inside PostgreSQL terminal:
CREATE DATABASE student_internship_system;
\q
# Exit PostgreSQL
```

**Expected:** No errors, just confirmation.

### Step 4: Import Database Schema
Creates all tables with relationships:
```bash
sudo -u postgres psql -d student_internship_system -f database/schema.sql
# (On Windows: psql -U postgres -d student_internship_system -f database/schema.sql)
```

**Expected:** Multiple "CREATE TABLE" messages, no errors.

### Step 5: Configure Environment Variables
```bash
# Copy example file
cp .env.example .env

# Edit with your PostgreSQL password
nano .env
# (On Windows: Open .env in Notepad)
```

**Update these values:**
```
PORT=3000
NODE_ENV=development
DB_USER=postgres
DB_PASSWORD=postgres ← Your PostgreSQL password
DB_HOST=localhost
DB_PORT=5432
DB_NAME=student_internship_system
JWT_SECRET=your_super_secret_key_change_this
JWT_EXPIRES_IN=24h
```


Save and close.

### Step 6: Start the Application
```bash
npm start
```

**Expected output:**
```
Server running on port 3000
Database connected successfully
```

### Step 7: Open in Browser
```
http://localhost:3000
```
🎉 **You should see the Beacon homepage!**

---

## 👤 Test Accounts

**Student Account:**
- Email: `joy.test@gmail.com`
- Password: `TestPass@123`
- Permissions: Browse internships, apply, manage skills

**Organization Account:**
- Email: `techvision.new@gmail.com`
- Password: `OrgPass@789`
- Permissions: Post internships, review applications, evaluate students

---

## 📸 Screenshots

**Figure 1: Homepage**
![Homepage](images/homepage.png)
Welcome page with login and registration options

**Figure 2: Login Page**
![Login](images/login.png)
Secure authentication with email and password

**Figure 3: Student Browse Internships**
![Browse Internships](images/student-browse.png)
Students view all available internship opportunities

**Figure 4: Apply Modal**
![Apply Modal](images/apply-modal.png)
Application form with cover letter submission

**Figure 5: Student Skill Profile**
![Skill Profile](images/student-skill-profile.png)
Students manage their skills with proficiency levels

**Figure 6: My Applications**
![My Applications](images/my-applications.png)
Student dashboard showing application status

**Figure 7: Student Profile**
![Student Profile](images/student-profile.png)
Complete student profile with education and contact info

**Figure 8: Organization Dashboard**
![Org Dashboard](images/org-dashboard.png)
Organization internship management interface

**Figure 9: Organization Internship Applications**
![Org Applications](images/org-applications.png)
Review all applications for a specific internship

**Figure 10: Organization Student Profile**
![Org Student Profile](images/org-student-profile.png)
Detailed student view for organizations with skills

**Figure 11: Organization Profile**
![Org Profile](images/org-profile.png)
Organization company profile page

---

## 🔐 Security Features

### Authentication
✅ JWT token authentication (24-hour expiration)
✅ Password hashing with bcrypt (10 salt rounds)
✅ Password complexity requirements (uppercase, lowercase, number, symbol)
✅ Role-based access control (student/organization)

### Data Protection
✅ Input validation with express-validator
✅ HTML entity escaping (XSS prevention)
✅ Parameterized SQL queries (SQL injection prevention)
✅ UNIQUE constraints on critical fields
✅ No sensitive data in API responses

### API Security
✅ Protected routes with authentication middleware
✅ IDOR prevention (ownership verification in all queries)
✅ SessionStorage for per-tab security (prevents account conflicts)
✅ Proper HTTP status codes
✅ Error messages don't expose system details

### Database Security
✅ Normalized schema (3NF)
✅ Foreign key constraints
✅ CASCADE deletes for data integrity
✅ UNIQUE constraints prevent duplicates

---

## 🛠️ Troubleshooting

### Installation Issues

**"npm: command not found"**
- Node.js not installed properly
- Reinstall from https://nodejs.org/

**"psql: command not found"**
- PostgreSQL not installed
- Windows: Add to PATH (C:\Program Files\PostgreSQL\15\bin)
- Mac: `brew install postgresql`
- Linux: `sudo apt install postgresql`

**"FATAL: database does not exist"**
- Database not created in Step 3
```bash
sudo -u postgres psql
CREATE DATABASE student_internship_system;
\q
```

**"FATAL: Peer authentication failed for user 'postgres'"**
- PostgreSQL authentication issue
```bash
sudo -u postgres psql
# (Or on Windows: psql -U postgres)
```

**"connection refused" or "could not connect to server"**
- PostgreSQL not running
```bash
# Linux/Mac
sudo systemctl start postgresql

# Windows: Start from Services app (services.msc)
```

### Runtime Issues

**"Port 3000 already in use"**
- Another app using port 3000
- Edit `.env` and change `PORT=3001`
- Restart: `npm start`

**"npm ERR! Cannot find module"**
- Dependencies not installed
```bash
rm -rf node_modules package-lock.json
npm install
```

**Login fails with correct credentials**
1. Verify PostgreSQL is running
2. Check .env has correct DB password
3. Verify database exists: `sudo -u postgres psql -l`
4. Restart application

**Stylesheets not loading**
- Hard refresh: Ctrl+Shift+R (Windows) or Cmd+Shift+R (Mac)
- Check browser console (F12) for errors

---

## 📁 Project Structure
```
beacon-internship-system/
├── database/
│ └── schema.sql # Database schema with all tables
├── images/ # Screenshot assets
│ ├── apply-modal.png
│ ├── homepage.png
│ ├── login.png
│ ├── my-applications.png
│ ├── org-applications.png
│ ├── org-dashboard.png
│ ├── org-profile.png
│ ├── org-student-profile.png
│ ├── student-browse.png
│ ├── student-profile.png
│ └── student-skill-profile.png
├── src/
│ ├── config/
│ │ └── db.js # PostgreSQL connection config
│ ├── controllers/ # Business logic
│ │ ├── applicationController.js
│ │ ├── authController.js
│ │ ├── internshipController.js
│ │ ├── skillController.js
│ │ └── userController.js
│ ├── middleware/ # Authentication & validation
│ │ ├── auth.js # JWT verification
│ │ └── validators.js # Input validation rules
│ ├── routes/ # API & page routes
│ │ ├── applicationRoutes.js
│ │ ├── authRoutes.js
│ │ ├── dashboardRoutes.js
│ │ ├── internshipRoutes.js
│ │ ├── pages.js
│ │ ├── skillRoutes.js
│ │ └── userRoutes.js
│ └── views/ # EJS templates
│ ├── auth/
│ │ ├── login.ejs
│ │ ├── registerOrganisation.ejs
│ │ └── registerStudent.ejs
│ ├── layouts/
│ │ ├── footer.ejs
│ │ └── navbar.ejs
│ ├── org/
│ │ ├── applicationDetails.ejs
│ │ ├── internshipApplications.ejs
│ │ ├── orgDashboard.ejs
│ │ └── profile.ejs
│ ├── student/
│ │ ├── browseInternships.ejs
│ │ ├── myApplications.ejs
│ │ ├── skillProfile.ejs
│ │ └── student-profile.ejs
│ ├── error.ejs
│ └── home.ejs
├── .env.example # Environment variables template
├── .gitignore # Git ignore rules
├── package.json # Dependencies & scripts
├── package-lock.json
├── README.md # This file
└── server.js # Application entry point
```


---

## 👥 For Panel Members (Defence Evaluation)

### Quick Start (10 minutes)

1. **Extract CD contents**
2. **Follow "Setup Guide" above** (5-10 minutes)
3. **Use test accounts** (listed above) to explore features
4. **Review database** in `database/schema.sql`
5. **Check security** in `src/middleware/validators.js` and controllers
6. **Test complete flow:**
   - Student: Register → Login → Add Skills → Browse → Apply → Check Status
   - Organization: Register → Login → Post Internship → Review Applications → Accept/Reject

### Key Features to Demonstrate

- End-to-end user workflows
- Secure JWT authentication with bcrypt password hashing
- Role-based access control (different dashboards)
- Database relationships and referential integrity
- Input validation and SQL injection prevention
- Responsive mobile design (resize to see hamburger menu)
- Multi-tab session security
- Skill profiling system
- Application tracking with real-time status

---

## Key Learning Outcomes

This project demonstrates:
- Building secure authentication systems with JWT
- Designing relational databases with multiple relationships
- Implementing role-based access control (RBAC)
- Connecting backend APIs to frontend views
- Input validation and sanitization
- Full-stack web application development
- Handling multi-tab sessions with sessionStorage
- Database normalization and integrity constraints
- Code organization and professional architecture

---

## Future Improvements

- Admin dashboard for approving organizations
- Email notifications for application updates
- Advanced search and filtering by skills
- Resume/portfolio file uploads
- AI-powered skills matching algorithm
- Messaging system between students and organizations
- Analytics dashboard for organizations
- Mobile app (React Native)
- Video interview scheduling
- Application timeline visualization

---

## 👩‍💻 Author

**Sunday Obianuju Joy**

- **LinkedIn:** www.linkedin.com/in/obianuju-sunday
- **GitHub:** https://github.com/Obianuju-Sunday
- **Email:** obianujusunday43@gmail.com
- **Institution:** Dr. Ogbonnaya Onu Polytechnic, Aba.
- **Program:** National Diploma in Computer Science (ND2)
- **Matriculation Number:** ND2024/22480/1/CS
- **Supervisor:** Dr. Oju Onuoha

---

## 📜 License

This project is open source and available under the MIT License.

---

**Last Updated:** September 2026

**Version:** 1.0.0

**Status:** ✅ Ready for Defence