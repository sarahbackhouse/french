# Français — Phrase Practice

A static French phrase quiz for GitLab Pages using Tailwind CSS via CDN and a Catppuccin-inspired dark theme.

## Features
- English → French, French → English, or mixed practice
- Score, accuracy, and progress
- Answers accept missing accents and ignore case/extra spaces
- Optional alternative answers in JSON
- French character palette
- Loads JSON decks from `phrases/` using `fetch()`
- Paste custom JSON and export the current deck

## Project structure
```text
.
├── index.html
├── .gitlab-ci.yml
└── phrases/
    ├── index.json
    ├── everyday.json
    ├── school.json
    └── hobbies.json
```

## Add a deck
Create a JSON array in `phrases/travel.json`:
```json
[
  {
    "english": "Where is the station?",
    "french": "Où est la gare ?",
    "hint": "A location question",
    "alternatives": { "french": ["Où se trouve la gare ?"] }
  }
]
```
Then add an entry to `phrases/index.json`:
```json
[
  { "name": "Travel", "file": "travel.json", "description": "Useful travel phrases." }
]
```
A static website cannot automatically list directory contents, so the manifest is the deck catalogue.

## Run locally
Do not open `index.html` directly via `file://`; `fetch()` needs a web server. From the project folder:
```bash
python3 -m http.server 8000
```
Open `http://localhost:8000`.

## Deploy to GitLab Pages
Commit the project to a GitLab repository and push to its default branch. `.gitlab-ci.yml` copies `index.html` and the `phrases/` directory into `public/` and publishes it with Pages. Check **Build > Pipelines** and **Deploy > Pages** in GitLab if needed.

Tailwind CDN is convenient for a small project; a production app could compile Tailwind locally.
