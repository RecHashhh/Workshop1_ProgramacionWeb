# Workshop 2 — Website (HTML + CSS)

**Web Applications · Semester II 2026 · Yachay Tech University**
William Garzon — Information Technology, 10th semester
Prof. Francisco Hidrobo

**Live site:** https://rechashhh.github.io/Workshop1_ProgramacionWeb/

---

## What this folder contains

The same six-page site of Workshop 1, now with a stylesheet. The markup barely
changed: what changed is that presentation moved out of the document and into
`css/style.css`.

**No JavaScript is used anywhere.** Everything that reacts to a click — the
welcome sequence, the image viewer, the zoom — is built with `:target` and a
hidden checkbox, which are the only two mechanisms CSS has for reacting to
user input.

## Structure

```
HTML+CSS/
├── index.html          Home page
├── courses.html        The three enrolled courses
├── schedule.html       Weekly timetable
├── activities.html     Clubs, sport and food on campus
├── map.html            The campus
├── contact.html        Student contact form
├── css/
│   └── style.css       The single stylesheet
└── assets/
    ├── fonts/          Manrope, self-hosted
    ├── projects/       Screenshots of the systems in the projects grid
    ├── map/            Campus photographs and the official campus map
    └── …               Profile photo, logos, project screenshots
```

The six pages sit at the same level here, so the links between them are direct
names with no `../`.

## What was added over Workshop 1

### Design tokens

Every colour, measure and duration is declared once in `:root` and referenced
by name. Changing the accent colour means editing one line, and the whole site
repaints: headings, links, table headers, buttons, focus rings and list
markers.

The accent is the school's institutional red, `#a4161a`.

### Two themes

A `@media (prefers-color-scheme: dark)` block redefines **only the tokens**.
Not one component rule is duplicated. Text contrast was computed for every
foreground-and-background pair in both themes: the worst case is 5.74:1, above
the 4.5:1 that WCAG AA requires.

### Self-hosted typeface

Manrope ships inside `assets/fonts/`, so the site renders identically without
an internet connection. Monospace is used where the content really is data:
labels, hours, course codes and table headers.

### A welcome sequence with no JavaScript

On arrival the visitor meets a single large **PRINT** button. Pressing it shows
a greeting that types itself out character by character, and after a few
seconds the screen fades on its own and leaves the site at its home section.

- The button is an anchor pointing to `#hello`
- `:target` is the one CSS selector that reacts to a click
- The typing effect animates the element's width in discrete `steps()`, one per
  character, which only works in a monospaced face because the `ch` unit
  assumes every character is the same width
- The screen removes itself with an animation ending in `visibility: hidden`

It only appears on a first visit: any active `:target` retires it.

### An image viewer

Every content image opens full screen: 13 on the home page, 8 on the map. The
viewer has a close button, previous and next arrows, a panel with the caption
and description, and a zoom toggle built from a hidden checkbox and its label.
Closing returns to the thumbnail you came from.

### A colour per subject

Each course carries its own pastel, repeated across the timetable, the session
table and its course page, so one subject can be followed from page to page.
Colour is never the only cue: every cell still carries the course code written
inside it.

### Cross-page navigation

Every timetable block links to its course page; each course links to the
schedule and to the map; the map links back to both.

### Accessibility

- A skip link is the first focusable element on every page
- The active menu entry carries `aria-current="page"`, and the CSS styles it
  from that same attribute
- Menu links are at least 44 pixels tall
- Every interactive element shows a focus ring
- `prefers-reduced-motion` cancels the typing effect and every transition

## How to open it

Open `index.html` in a browser, or visit the live site linked above. No server
is required.

## Notes

- Campus photographs and the campus map are official material published by
  Yachay Tech University, reproduced here for an academic assignment.
- Screenshots of the Ripconciv and Centinela projects correspond to software
  developed by the author.
