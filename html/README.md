# Workshop 1 — Website (only HTML)

**Web Applications · Semester II 2026 · Yachay Tech University**
William Garzon — Information Technology, 10th semester
Prof. Francisco Hidrobo

---

## What this folder contains

A website of **six interconnected pages written in HTML5 only**. There is no
CSS and no JavaScript here: that is the point of the workshop. Every page is
judged on its markup, so the work went into structure rather than appearance.

The styled version of this same site is in the `HTML+CSS` folder, which is
Workshop 2.

## Structure

```
HTML/
├── index.html          Home page                  (Activity 1)
├── assets/             Images
│   ├── perfil.jpg      Profile photograph
│   ├── university.png  Yachay Tech logo
│   ├── ripconciv-*     Screenshots of the Ripconciv project
│   ├── centinela-*     Screenshots of the Centinela project
│   └── map/            Campus photographs and the official campus map
└── pages/
    ├── courses.html                               (Activity 2)
    ├── schedule.html                              (Activity 3)
    ├── contact.html                               (Activity 4)
    ├── activities.html                            (Activity 5)
    └── map.html                                   (Activity 5)
```

## The pages

| File | Activity | What it holds |
|---|---|---|
| `index.html` | 1 | Name, degree program, semester, personal description, photograph and academic interests. Uses the six required semantic elements. |
| `pages/courses.html` | 2 | The three enrolled courses with instructor, syllabus topics and three topics expected to learn. Headings `h1`–`h3`, ordered and unordered lists, external links. |
| `pages/schedule.html` | 3 | Weekly timetable as a table, using `rowspan` and `colspan`, plus a second table with the location and instructor of every session. |
| `pages/contact.html` | 4 | Student contact form with ten input types, five `fieldset` groups and every `label` bound to its control. No backend: nothing is submitted. |
| `pages/activities.html` | 5 | Student clubs, sport and food on campus, organised into categories. |
| `pages/map.html` | 5 | The campus: official map, academic buildings, heritage buildings and student housing. |

## Navigation

Every page carries the same menu:

```
Home · Courses · Schedule · Activities · Map · Contact
```

Relative paths differ by level: `index.html` points into `pages/…`, while the
pages inside `pages/` point back to `../index.html` and reach each other
directly.

## Prerequisites

The site was served locally through Apache with a virtual host answering to
`workshop1.webapp`:

- `127.0.0.1 workshop1.webapp` added to the `hosts` file
- `ping workshop1.webapp` answers from `127.0.0.1`
- XAMPP (Apache) installed, with the virtual host declared in
  `httpd-vhosts.conf` and this folder as its `DocumentRoot`

A second virtual host for `localhost` was declared **before** it: in Apache,
as soon as any `<VirtualHost>` exists the global `DocumentRoot` stops applying,
and `http://localhost` would otherwise stop working.

## How to open it

Open `index.html` in a browser. No server is required — it is plain HTML.

## Notes

- Campus photographs and the campus map are official material published by
  Yachay Tech University, reproduced here for an academic assignment.
- Screenshots of the Ripconciv and Centinela projects correspond to software
  developed by the author.
