# AuditTV Handover Manual

Prepared by **Octotech**

This document is the handover guide for the AuditTV website and admin panel. It is written for operations staff, content editors, managers, and administrators who will manage the system after delivery.

- Live website: `http://audittv.az`
- Admin login: `http://audittv.az/#/admin`
- Format: Markdown reference manual

---

## 1. Purpose of This Manual

This manual explains:

- what the AuditTV platform includes
- which live pages are available
- how course access works
- how the admin panel should be used
- which technologies and libraries are used in the project
- what to check during daily operation

AuditTV uses hash-based routing, so live URLs commonly look like:

`http://audittv.az/#/page-name`

This is normal for this system.

---

## 2. System Overview

AuditTV includes two main parts:

### Public website

Visitors can:

- browse the homepage
- read blog posts
- listen to podcast episodes
- browse courses
- submit contact forms
- subscribe to newsletter updates
- request access to courses

### Admin panel

Admins can:

- edit public content
- manage blog posts
- manage podcast episodes
- manage courses and lessons
- review course requests, contact requests, and newsletter submissions
- configure SEO and SMTP settings
- manage admin users

---

## 3. User Roles

### Visitor

Any public user browsing the website without admin access.

### Course applicant

A visitor who submits a course registration request from a course detail page.

### Approved student

A course applicant whose request has been approved by an admin. This user can access the course player.

### Admin / content editor

A signed-in user with access to the admin panel. Depending on role, this user can edit content, process requests, or manage system settings and admin accounts.

---

## 4. Quick Start for Daily Use

For normal day-to-day operation, use this sequence:

1. Open the admin panel at `http://audittv.az/#/admin`
2. Log in with your admin account
3. Check `Requests` first
4. Review pending course applications and new messages
5. Open the relevant editor for blogs, podcasts, courses, or pages
6. Save your changes
7. Refresh the live website and verify the result
8. Log out after the session if needed

Recommended daily order:

1. Requests
2. Content updates
3. Final live-site check

---

## 5. Public Website Pages

### 5.1 Home page

- URL: `http://audittv.az/#/`
- Purpose: main landing page for visitors

Main content:

- hero section
- promotional benefit / downloadable area
- featured podcast section
- featured blog area
- FAQ section
- newsletter form

### 5.2 About page

- URL: `http://audittv.az/#/haqqimizda`
- Purpose: company / brand presentation page

### 5.3 Podcast page

- URL: `http://audittv.az/#/podcast`
- Purpose: list and search podcast episodes

Main behavior:

- users can search by title or description
- users can open an episode player modal
- episode play analytics are recorded in the backend

### 5.4 Blog page

- URL: `http://audittv.az/#/blog`
- Purpose: browse and search articles

Main behavior:

- category filtering
- keyword search
- link to detailed blog article pages

### 5.5 Education page

- URL: `http://audittv.az/#/tedris`
- Purpose: browse available courses

Main behavior:

- filter by level
- search by title / description / instructor
- open individual course detail pages

### 5.6 Contact page

- URL: `http://audittv.az/#/elaqe`
- Purpose: contact information and form submission

Main behavior:

- visitors can submit full name, email, phone, subject, and message
- requests are saved in the backend
- notifications may be emailed if SMTP is configured

---

## 6. Courses and Student Access

### 6.1 Course detail page

- URL pattern: `http://audittv.az/#/tedris/<course-id>`

Each course page includes:

- course title
- pricing
- instructor information
- module / lesson structure
- long description
- learning outcomes
- course access request modal

### 6.2 Course registration request flow

From the course detail page:

1. user opens the registration modal
2. user enters full name, email, phone number, and password
3. request is sent to the backend
4. request stays pending until approved or rejected

Important:

- course access is course-specific
- being approved for one course does not unlock all courses

### 6.3 Student sign-in

Students sign in from the course modal using:

- the same email used during registration
- the same password set during request submission

If the request is approved, the user is redirected to the course player.

### 6.4 Course player

- URL pattern: `http://audittv.az/#/tedris/<course-id>/player`

Available features:

- lesson playback
- lesson completion tracking
- last lesson memory
- course resources
- Q&A notes
- completion-based certificate download

### 6.5 Local storage usage in course area

The browser stores:

- current approved user email
- completed lessons
- last opened lesson
- local Q&A entries

If browser storage is cleared, this local memory is cleared too.

---

## 7. Contact and Newsletter Flows

### 7.1 Contact form

Public page:

- `http://audittv.az/#/elaqe`

Collected fields:

- full name
- email
- phone
- subject
- message

### 7.2 Newsletter subscription

Usually available on the homepage.

Collected field:

- email

### 7.3 Email notification note

If SMTP is configured correctly:

- form events can send notification emails
- request submissions can send email alerts

If SMTP fails:

- the request may still be stored in the database
- the email notification may fail separately

---

## 8. Admin Access

### 8.1 Admin login

- URL: `http://audittv.az/#/admin`

Login steps:

1. open the admin login page
2. enter username and password
3. submit the form
4. after success, the system stores the admin session token locally
5. user is redirected to the admin dashboard

### 8.2 Session behavior

- invalid or missing token redirects the user back to login
- logout removes the local admin token
- admin routes are protected

### 8.3 Sidebar structure

Main groups:

- Pages
- Podcast
- Content
- System

These groups open the related admin screens.

---

## 9. Admin Panel Guide

## 9.1 Dashboard / homepage editor

- Admin URL: `http://audittv.az/#/admin/dashboard`
- Controls public page: `http://audittv.az/#/`

Used for:

- homepage hero content
- benefit card
- homepage facts
- homepage podcast section
- FAQ items
- guide / PDF upload history

Typical workflow:

1. open dashboard
2. edit the homepage section you need
3. upload files if required
4. save
5. refresh the live homepage

## 9.2 Generic content manager

- Admin URL pattern: `http://audittv.az/#/admin/content?section=<section-name>`

Examples:

- `http://audittv.az/#/admin/content?section=about`
- `http://audittv.az/#/admin/content?section=contact`
- `http://audittv.az/#/admin/content?section=privacyPolicy`
- `http://audittv.az/#/admin/content?section=termsOfUse`

Used for structured editing of sections such as:

- home
- about
- podcast
- faq
- contact
- privacy policy
- terms of use
- navigation
- topics
- services
- clients

Main features:

- text editing
- URL editing
- image / file uploads
- changed-only filtering
- empty-only filtering
- search inside fields

## 9.3 Podcast manager

- Admin URL: `http://audittv.az/#/admin/podcasts`
- Controls public page: `http://audittv.az/#/podcast`

Used for:

- podcast page header
- podcast description
- episode creation
- episode editing
- thumbnail upload
- media URL management

Main episode fields:

- title
- description
- duration
- date
- host
- thumbnail
- video / media URL

## 9.4 Podcast analytics

- Admin URL: `http://audittv.az/#/admin/podcast-stats`

Used for:

- monitoring podcast play activity
- comparing time ranges
- identifying popular episodes
- reviewing host distribution

## 9.5 Blog manager

- Admin URL: `http://audittv.az/#/admin/blogs`
- Controls public page: `http://audittv.az/#/blog`

Used for:

- blog page header
- new post creation
- post editing
- image upload
- article block editing

Main blog post fields:

- title
- category
- date
- author
- image
- status
- content blocks

Supported content block types:

- heading
- paragraph
- list
- quote
- image

## 9.6 Education manager

- Admin URL: `http://audittv.az/#/admin/education`
- Additional editor URL: `http://audittv.az/#/edit-class?new=1`
- Controls public page: `http://audittv.az/#/tedris`

Used for:

- course list management
- course detail content
- module and lesson editing
- resource management
- pricing and instructor information
- perks and outcomes

Main course areas:

- card information
- detail information
- modules and lessons
- downloadable resources
- course perks

Main fields include:

- title
- instructor
- price
- duration
- level
- thumbnail
- rating
- short description
- long description
- student count
- modules
- lessons
- resources

## 9.7 Requests manager

- Admin URL: `http://audittv.az/#/admin/requests`

Used for:

- course requests
- contact submissions
- newsletter submissions

Main actions:

- detail view
- approve
- reject
- resolve
- delete
- Excel export

Recommended handling order:

1. check new course requests
2. check urgent contact messages
3. review newsletter submissions when needed
4. export Excel if reporting is required

## 9.8 SEO, SMTP, and footer settings

- Admin URL: `http://audittv.az/#/admin/settings`

Used for:

- SEO title
- SEO description
- canonical URL
- keyword list
- SMTP host and port
- SMTP sender details
- notification recipient emails
- site logo
- footer links and footer content

Recommended process:

1. update SEO if page identity changes
2. configure SMTP carefully
3. run SMTP test
4. save
5. submit a test contact form from the public site

## 9.9 Admin users

- Admin URL: `http://audittv.az/#/admin/users`

Used for:

- creating admin accounts
- updating roles
- changing display names
- enabling or disabling users
- resetting passwords
- deleting users

Good practice:

- disable users instead of deleting them when temporary access removal is enough

## 9.10 Recommended daily admin workflow

1. Log in
2. Open Requests
3. Process applications and messages
4. Update homepage or campaign content if needed
5. Publish blog or podcast updates
6. Validate live pages
7. Log out

---

## 10. Saving and Publishing

General rule:

- changes are not final until saved

After saving:

- public pages should reflect the latest stored content
- uploaded files usually appear as relative URLs such as `/uploads/...`

Recommended publishing sequence:

1. update content
2. save
3. reload the public page
4. confirm the result visually

---

## 11. Technology and Libraries

This section lists the actual libraries used in the AuditTV project and what they are used for.

### 11.1 Frontend libraries

| Library | Usage |
|---|---|
| `react` | Main frontend framework |
| `react-dom` | Renders the React application in the browser |
| `react-router-dom` | Routing for public pages, course pages, and admin pages |
| `lucide-react` | Icon library used across the website and admin panel |
| `quill` | Rich text editor used in blog editing |
| `xlsx` | Excel export in the requests manager |

### 11.2 Backend libraries

| Library | Usage |
|---|---|
| `express` | Backend API server |
| `cors` | Cross-origin request handling |
| `better-sqlite3` | SQLite database connection and storage layer |
| `multer` | File and image upload handling |
| `nodemailer` | SMTP email sending |

### 11.3 Build and development tools

| Tool | Usage |
|---|---|
| `vite` | Frontend development server and build tool |
| `@vitejs/plugin-react` | React integration for Vite |
| `typescript` | Typed frontend development |
| `@types/node` | Node.js type definitions |

### 11.4 Native Node.js modules used

| Module | Usage |
|---|---|
| `fs` | File and directory operations |
| `path` | Safe file path resolution |
| `crypto` | Password hashing and secure token-related functions |

### 11.5 Database and storage summary

Main stored data includes:

- site content
- course requests
- form submissions
- podcast events
- admin users
- admin sessions

Uploads are stored in the uploads directory and content is also synchronized with sitemap files where required.

---

## 12. Troubleshooting

### Student cannot open the course player

Check:

- whether the request exists
- whether the request status is `approved`
- whether the student is using the same email used during request creation

### Contact form records exist but emails are not arriving

Check:

- SMTP host
- SMTP port
- SMTP username and password
- sender email
- recipient notification emails
- SMTP test result

### Admin is redirected back to login

Check:

- whether the admin token is missing or invalid
- whether the account is still active

### Content changes do not appear on the website

Check:

- whether the save action completed successfully
- whether the correct editor screen was used
- whether the public page was refreshed

### Uploaded media does not appear correctly

Check:

- whether upload returned a valid URL
- whether the form was saved after upload
- whether the public page path is correct

---

## 13. Working Recommendations

- keep naming consistent for courses, posts, and podcast episodes
- avoid changing course IDs after course requests already exist
- test SMTP before relying on public forms
- check pending requests regularly
- review mobile layout when long text is added
- use clean and optimized file names for uploads

---

## 14. Page and Task Reference

| Area | URL | Main usage |
|---|---|---|
| Home | `http://audittv.az/#/` | Public landing page |
| About | `http://audittv.az/#/haqqimizda` | About / company page |
| Podcast | `http://audittv.az/#/podcast` | Podcast listing and playback |
| Blog | `http://audittv.az/#/blog` | Blog listing |
| Education | `http://audittv.az/#/tedris` | Course listing |
| Course detail | `http://audittv.az/#/tedris/<course-id>` | Course information and access request |
| Course player | `http://audittv.az/#/tedris/<course-id>/player` | Protected student lesson player |
| Contact | `http://audittv.az/#/elaqe` | Contact page and form |
| Admin login | `http://audittv.az/#/admin` | Admin authentication |
| Dashboard | `http://audittv.az/#/admin/dashboard` | Homepage editing |
| Content manager | `http://audittv.az/#/admin/content?section=<section-name>` | Structured section editing |
| Blog manager | `http://audittv.az/#/admin/blogs` | Blog publishing |
| Podcast manager | `http://audittv.az/#/admin/podcasts` | Podcast content management |
| Podcast analytics | `http://audittv.az/#/admin/podcast-stats` | Podcast performance review |
| Education manager | `http://audittv.az/#/admin/education` | Course and lesson management |
| Requests manager | `http://audittv.az/#/admin/requests` | Requests review and processing |
| Settings | `http://audittv.az/#/admin/settings` | SEO, SMTP, branding, footer |
| Admin users | `http://audittv.az/#/admin/users` | Admin account management |

---

## 15. Final Note

This repository version of the manual is intended to be the clean Markdown reference copy of the AuditTV handover documentation.

If needed later, this file can be:

- expanded with screenshots
- converted into PDF
- split into separate public and admin manuals
- versioned further as the system evolves
