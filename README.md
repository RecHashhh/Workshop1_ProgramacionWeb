# Workshop 1 — Website (only HTML)

**Web Applications — Semester II 2026**
Prof. Francisco Javier Hidrobo Torres
Yachay Tech University

**Author:** William Garzon — Information Technology, 10th semester

---

## Summary

A website of six interconnected pages built with **HTML5 only**. No CSS and no
JavaScript were used, as required by the assignment: presentation is left for a
later stage of the course.

The site is served locally by Apache through a virtual host that answers to
`http://workshop1.webapp`.

## Project structure

```
Actividad01_Workshop/
├── index.html              Home page (Activity 1)
├── README.md               This report
├── assets/                 Images
│   ├── perfil.jpg
│   ├── university.png
│   ├── ripconciv-*.png     Screenshots of the Ripconciv project
│   ├── centinela-*.jpeg    Screenshots of the Centinela project
│   └── map/                Campus photographs and official campus map
└── pages/
    ├── courses.html        Activity 2
    ├── schedule.html       Activity 3
    ├── contact.html        Activity 4
    ├── activities.html     Activity 5
    └── map.html            Activity 5
```

## Prerequisites

| Step | How it was done |
|---|---|
| `hosts` file | Added `127.0.0.1 workshop1.webapp` to `C:\Windows\System32\drivers\etc\hosts` |
| Resolution test | `ping workshop1.webapp` answers from `127.0.0.1` |
| Web server | XAMPP (Apache) installed on Windows 11 |
| Virtual host | `<VirtualHost *:80>` added to `httpd-vhosts.conf` |

Virtual host used:

```apache
<VirtualHost *:80>
    ServerName workshop1.webapp
    DocumentRoot "C:/.../Actividad01_Workshop"
    DirectoryIndex index.html
    <Directory "C:/.../Actividad01_Workshop">
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>
</VirtualHost>
```

A second virtual host for `localhost` was declared **before** this one. In
Apache, as soon as any `<VirtualHost>` is defined the global `DocumentRoot`
stops applying, so without it `http://localhost` would stop working.

`httpd.exe -t` returns **Syntax OK** and all pages answer **200 OK**.

## Activities completed

### Activity 1 — Home page (`index.html`)

Uses `<!DOCTYPE html>`, `<html>`, `<head>`, `<title>` and `<body>`, and inside
the body the six required semantic elements: `<header>`, `<nav>`, `<main>`,
`<section>`, `<article>` and `<footer>`.

Contains the author's name, degree program, semester, a personal description, a
profile photograph inside a `<figure>` with `<figcaption>`, and a list of
academic interests. Two `<article>` elements present personal projects with
their screenshots.

### Activity 2 — Courses (`pages/courses.html`)

The three courses of the current term, each with its official code, instructor,
main topics and three topics the student expects to learn.

| Code | Course | Instructor |
|---|---|---|
| CA57 | Programación Web | Francisco Javier Hidrobo Torres |
| CA56-TA24 | Procesos Estocásticos | Diego Hernán Peluffo Ordoñez |
| TM11 | Física II | Rosa Estefanía Almache Hernández / Julio César Chacón Torres |

Uses headings `<h1>`–`<h3>`, paragraphs, unordered lists for the syllabus
topics, ordered lists for the expected topics, and three external links.

### Activity 3 — Schedule (`pages/schedule.html`)

Two tables. The first is the weekly timetable from 07:00 to 18:59, where each
class spans its real duration using `rowspan`, and the header groups the five
weekdays using `colspan`. The second table lists every session with its day,
time, building, room and instructor.

Both tables use `<caption>`, `<thead>`, `<tbody>` and the deprecated `border`
attribute, which the assignment explicitly allows so the grid is visible without
CSS.

### Activity 4 — Contact form (`pages/contact.html`)

A student contact form addressed to the university. It has no backend: nothing
is submitted when the button is pressed.

Contains all the required fields — full name, email address, date of birth,
degree program, semester, reason for contact, message, acceptance checkbox and
submit button — plus national ID, student ID, attachment and urgency.

Ten different input types are used: `text`, `email`, `date`, `tel`, `number`,
`radio`, `checkbox`, `file`, `submit` and `reset`, together with two `<select>`
elements and one `<textarea>`. Fields are grouped in five `<fieldset>` elements
with their `<legend>`, and every `<label>` is associated to its control through
the `for` attribute.

### Activity 5 — Additional pages

**`pages/activities.html`** — student clubs, sport and recreation, and food on
campus, organised into categories with `<section>` and `<article>`.

**`pages/map.html`** — the campus: official campus map, academic buildings with
the rooms used for each class, heritage buildings and student housing. Nine
images with `<figure>` and `<figcaption>`.

Both pages include links that open in a new tab using
`target="_blank" rel="noopener"`, and both were added to the navigation menu of
every page on the site.

## Navigation

Every page carries the same `<nav>` with the six entries:

```
Home · Courses · Schedule · Activities · Map · Contact
```

Relative paths differ by level: `index.html` points to `pages/...`, while pages
inside `pages/` point to `../index.html` and to their siblings directly.

## Verification performed

| Check | Result |
|---|---|
| Tag balance across the 6 pages | no unbalanced tags |
| Internal links | 0 broken |
| Image references | 22 `<img>`, all resolve |
| Table geometry (`colspan`/`rowspan`) | both tables consistent at 6 columns per row |
| `<label for>` associations | 0 orphan labels |
| HTTP response of every page and asset | 200 OK |

Table geometry was verified with a script that simulates the browser's rendering
by counting `colspan` and `rowspan` row by row, since a wrong `rowspan` produces
a misaligned table that is easy to miss by eye.

## Notes

- Campus photographs and the campus map are official material published by
  Yachay Tech University, reproduced here for an academic assignment.
- Screenshots of the Ripconciv and Centinela projects correspond to software
  developed by the author.
