# Stage 1 — Advanced Todo Card & Profile Card

**HNG Frontend Internship | Stage 1**

This stage has two parts submitted together. Both files are in this folder.

---

## Files

| File | Part | Description |
|------|------|-------------|
| `todo-card.html` | Stage 1a | Advanced Interactive Todo Card |
| `Profile_Card.html` | Stage 1b | Testable Profile Card |

---

## Live Demos

| Part | Live URL |
|------|----------|
| Stage 1a | [View on Vercel](#) |
| Stage 1b | [View on Vercel](#) |

> Replace `#` with your actual Vercel URLs once deployed.

---

---

## Stage 1a — Advanced Interactive Todo Card

### What Changed from Stage 0

| Feature | Stage 0 | Stage 1a |
|---------|---------|---------|
| Edit mode | Dummy `console.log` | Full form with Save / Cancel |
| Status | Display only | Interactive dropdown control |
| Priority | Badge only | Badge + animated left-border indicator |
| Description | Always visible | Collapsible with expand/collapse toggle |
| Time display | Basic | Granular: hours, minutes, overdue breakdown |
| Overdue state | Red text only | Red badge + red card border |
| Done state | Strike-through title | Timer stops, shows "Completed" |

---

### data-testid Attributes

**Carried over from Stage 0**
`test-todo-card`, `test-todo-title`, `test-todo-description`, `test-todo-priority`,
`test-todo-due-date`, `test-todo-time-remaining`, `test-todo-status`,
`test-todo-complete-toggle`, `test-todo-tags`, `test-todo-tag-work`,
`test-todo-tag-urgent`, `test-todo-edit-button`, `test-todo-delete-button`

**New in Stage 1a**
`test-todo-edit-form`, `test-todo-edit-title-input`, `test-todo-edit-description-input`,
`test-todo-edit-priority-select`, `test-todo-edit-due-date-input`,
`test-todo-save-button`, `test-todo-cancel-button`, `test-todo-status-control`,
`test-todo-priority-indicator`, `test-todo-expand-toggle`,
`test-todo-collapsible-section`, `test-todo-overdue-indicator`

---

### Features

**Edit Mode**
- Click Edit → inline form opens pre-filled with current values
- Save commits changes to title, description, priority, and due date
- Cancel fully restores previous values
- Focus returns to Edit button on close

**Status Transitions**
- Checkbox ↔ dropdown ↔ badge all stay in sync
- Checking → status becomes Done, timer shows "Completed"
- Unchecking → status reverts to Pending
- Setting dropdown to Done → checkbox becomes checked automatically

**Priority Indicator**
- Left border colour changes: red (High), amber (Medium), green (Low)
- Priority badge updates to match

**Expand / Collapse**
- Description collapsed by default
- Toggle shows "Show more" / "Show less" with animated arrow
- `aria-expanded` and `aria-controls` wired correctly

**Overdue Logic**
- Past due → red card border + Overdue badge appears
- Granular: "Overdue by 45 min", "Overdue by 2h 30m", "Overdue by 3 days"
- Done → shows "Completed", overdue badge hidden

---

### Accessibility

- All edit form fields have `<label for="">` ✅
- Status dropdown has `aria-labelledby` + `aria-label` ✅
- Expand toggle has `aria-expanded` + `aria-controls` ✅
- `aria-live="polite"` on time remaining ✅
- Visible `:focus-visible` on all interactive elements ✅

**Keyboard Tab Order**
```
Checkbox → Status control → Expand toggle → Edit → Delete → Save / Cancel (edit mode)
```

---

### Design Decisions

- DOM order drives keyboard order; CSS `order` property controls visual layout independently
- Single `state` object with a `savedState` snapshot enables reliable Cancel
- `render()` is the sole function that touches the DOM — clean unidirectional data flow
- Timer refreshes every 30 seconds; also recalculates immediately after Save

---

### Known Limitations

- Focus is not trapped inside the edit form (listed as optional bonus in the spec)
- Tags are hard-coded (no add/remove functionality in Stage 1)

---

---

## Stage 1b — Testable Profile Card

### data-testid Attributes

| testid | Element | Description |
|--------|---------|-------------|
| `test-profile-card` | `<article>` | Root card container |
| `test-user-name` | `<h2>` | Full name |
| `test-user-bio` | `<p>` | Short biography |
| `test-user-time` | `<time>` | Current epoch time in milliseconds |
| `test-user-avatar` | `<img>` | Profile photo |
| `test-user-social-links` | `<nav>` | Social links container |
| `test-user-social-twitter` | `<a>` | Twitter / X link |
| `test-user-social-github` | `<a>` | GitHub link |
| `test-user-social-linkedin` | `<a>` | LinkedIn link |
| `test-user-hobbies` | `<ul>` | Hobbies list |
| `test-user-dislikes` | `<ul>` | Dislikes list |

---

### Features

**Epoch Time**
- Displays `Date.now()` in milliseconds inside a `<time>` element
- Updates every 1 second
- `datetime` attribute also updates with a valid ISO string

**Avatar**
- Meaningful `alt` text describing the person and role
- Wrapped in semantic `<figure>` + `<figcaption>`

**Social Links**
- Open in a new tab with `target="_blank" rel="noopener noreferrer"`
- Each link has a descriptive `aria-label`

**Hobbies & Dislikes**
- Separate `<ul>` elements in separate `<section>` elements
- Green dots for hobbies, red dots for dislikes

---

### Semantic HTML Used

| Element | Purpose |
|---------|---------|
| `<article>` | Profile card root |
| `<figure>` + `<figcaption>` | Avatar with caption |
| `<h2>` | User name heading |
| `<nav>` | Social links region |
| `<section>` | Hobbies / Dislikes sections |
| `<ul>` + `<li>` | Lists |
| `<time datetime="...">` | Epoch time |

---

### Responsive Layout

| Breakpoint | Layout |
|-----------|--------|
| `< 600px` (mobile) | Avatar centred on top, name below — stacked |
| `≥ 600px` (tablet) | Avatar on the **left**, name + intro on the **right** |
| `≥ 1024px` (desktop) | Wider card, larger avatar and name font |

---

### Accessibility

- Avatar has meaningful `alt` text ✅
- All links have descriptive `aria-label` values ✅
- `aria-live="polite"` on the epoch time element ✅
- Visible `:focus-visible` outline on all links ✅
- Full keyboard navigation through all interactive elements ✅
- WCAG AA colour contrast throughout ✅

---

### Known Limitations

- Avatar is a generated placeholder — replace the `src` in `stage1b.html` with a real photo URL
- Twitter and LinkedIn `href` values are placeholders — update with real profile URLs

---

---

## Running Locally

No build tools needed. Open either file directly in your browser:

```bash
open todo-card.html
open Profile_Card.html
```

---

## Author

**Kaycee Attah** — Frontend Developer
GitHub: [@Kaycee-attah](https://github.com/Kaycee-attah)
