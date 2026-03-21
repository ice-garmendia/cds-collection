---
name: cd-collection-regression
description: Regression testing skill for the CD Collection web app (ice-garmendia.github.io/cds-collection). Use this skill whenever the user wants to test, validate, or QA the CD collection app after making changes — including after uploading a new index.html, adding features, or fixing bugs. Triggers on phrases like "test the app", "run regression", "check if everything works", "QA the changes", "validate the app".
---

# CD Collection — Regression Test Skill

This skill guides structured regression testing of the CD Collection app at:
**https://ice-garmendia.github.io/cds-collection/**

Run through each section after any change to `index.html`. Mark each test ✅ PASS / ❌ FAIL / ⚠️ PARTIAL.

---

## 1. LOAD & THEME

| # | Test | Steps | Expected |
|---|------|-------|----------|
| 1.1 | App loads | Open URL | No console errors, collection tree visible |
| 1.2 | Dark mode default | Open URL fresh | Background dark (#0a0a14) |
| 1.3 | Toggle to light | Click ☀️ | Full UI switches to light theme — header, tree rows, popups |
| 1.4 | Toggle back to dark | Click 🌙 | Full UI switches back to dark |
| 1.5 | Tree rows light mode | Toggle light, expand Queen > Album | Rows show light background, not black |

---

## 2. NAVIGATION & TREE

| # | Test | Steps | Expected |
|---|------|-------|----------|
| 2.1 | Artist level expands | Click "Queen" | Categories appear below |
| 2.2 | Singles grouping | Expand Queen | CD3 + CD5 grouped as "Singles" |
| 2.3 | Category icons | Expand any artist | SVG icons visible next to Album, Singles, Compilation, etc. |
| 2.4 | Title level | Expand Album > A Night at the Opera | Shows "(1975)" after title |
| 2.5 | Title order | Check titles within Album | Ordered by Original Year ascending |
| 2.6 | Disc order | Expand any title with multiple discs | Ordered by Issue Year, then UK > Europe > Japan > USA |
| 2.7 | Country flags | Expand any disc row | Flag emoji visible next to country name |
| 2.8 | Artist order | Check root level | Queen, Freddie Mercury, Brian May, Roger Taylor, The Cross, Smile, Queen+ |
| 2.9 | Collapse | Click open artist | Tree collapses |

---

## 3. SEARCH

| # | Test | Steps | Expected |
|---|------|-------|----------|
| 3.1 | Search in Collection | Type "Highlander" | Tree filters to matching discs |
| 3.2 | Search in Wantlist | Go to Wantlist tab, type artist name | Wantlist filters correctly |
| 3.3 | Clear search | Delete search text | Full tree restored |
| 3.4 | Search by ID | Type "CD-0004" | Highlander Selection appears |
| 3.5 | No results | Type "xyzxyz" | Empty tree, no crash |

---

## 4. POPUP

| # | Test | Steps | Expected |
|---|------|-------|----------|
| 4.1 | Open popup | Click any disc | Immersive popup opens with blur background |
| 4.2 | Photo carousel | Open Highlander (CD-0004) | 3 photos visible, arrows + dots navigate |
| 4.3 | Photo contain | Check photo display | Full image visible, not cropped |
| 4.4 | Country flag in popup | Check Country field | Flag emoji + country name (e.g. 🇬🇧 UK) |
| 4.5 | Issue year shown | Check popup fields | Issue year always shows (not "—") |
| 4.6 | Close popup | Click ✕ or outside | Popup closes, no crash |
| 4.7 | Share button | Click ⎘ Share | "✓ Copied!" appears, URL in clipboard |
| 4.8 | Share URL works | Open copied URL | App loads and popup opens automatically |
| 4.9 | Recently added tag | Move item from Wantlist, open popup | "✦ Recently added" badge visible |
| 4.10 | Tag clears on close | Close and reopen popup | "✦ Recently added" badge gone |

---

## 5. ADMIN MODE

| # | Test | Steps | Expected |
|---|------|-------|----------|
| 5.1 | Lock icon visible | Look at header | 🔒 icon visible next to ☀️/🌙 |
| 5.2 | Wrong password | Click 🔒, type wrong password | "Incorrect password" error, modal stays open |
| 5.3 | Correct password | Enter correct password | Modal closes, 🔓 appears green |
| 5.4 | Values visible | Log in, check tree | € values visible on artist/category/title/disc rows |
| 5.5 | Values hidden | Log out, check tree | All € values hidden |
| 5.6 | Total value hidden | Check header without login | Total value shows "—" |
| 5.7 | Total value visible | Check header with login | Total value shows €XX,XXX |
| 5.8 | Add CD button | Log in | "+ Add CD" button appears |
| 5.9 | Add CD hidden | Log out | "+ Add CD" button gone |
| 5.10 | Edit/Delete buttons | Log in, hover any card | Edit + Delete buttons appear on hover |
| 5.11 | Statistics locked | Log out, click Statistics tab | 🔒 "Admin access required" message |
| 5.12 | Statistics unlocked | Log in, click Statistics tab | Charts and KPIs visible |
| 5.13 | Log out | Click 🔓 | Returns to 🔒, values hidden again |

---

## 6. WANTLIST

| # | Test | Steps | Expected |
|---|------|-------|----------|
| 6.1 | Wantlist tab | Click "Wantlist" | 131 items in same tree structure |
| 6.2 | Star badge | Expand any disc | ★ icon in gold on each item |
| 6.3 | Same tree structure | Check Wantlist | Same Artist > Category > Title > Disc hierarchy |
| 6.4 | Search in Wantlist | Type in search bar | Filters wantlist items |
| 6.5 | Move to Collection | Log in, open any wantlist popup | "→ Move to Collection" button visible |
| 6.6 | Move confirmation | Click Move to Collection | Confirmation dialog appears |
| 6.7 | Move executes | Confirm move | Item disappears from Wantlist |
| 6.8 | Item in Collection | Go to Collection, search for moved item | Item appears with ✦ New badge |
| 6.9 | Move back | Log in, open moved item in Collection | "← Wantlist" button visible |
| 6.10 | Move back any item | Open any Collection item (not moved) | "← Wantlist" button also visible |
| 6.11 | Reverse move | Confirm move back | Item appears in Wantlist, gone from Collection |

---

## 7. STATISTICS

| # | Test | Steps | Expected |
|---|------|-------|----------|
| 7.1 | KPI cards | Log in, open Statistics | 8 KPI cards visible |
| 7.2 | Bar charts | Check charts | Records by country + by artist bars render |
| 7.3 | Donut charts | Check charts | Commercial vs Promo + by category donuts render |
| 7.4 | Artist × Category | Check table | Matrix with all artists and categories |
| 7.5 | Light mode charts | Toggle light, open Statistics | Charts visible in light mode |

---

## 8. NON-HAPPY PATHS

| # | Test | Steps | Expected |
|---|------|-------|----------|
| 8.1 | Broken photo | Open disc without photos | Colored placeholder with initials |
| 8.2 | Click outside modal | Click overlay of admin modal | Modal stays open (no accidental close) |
| 8.3 | Cancel move | Click Move, then Cancel in confirm | Nothing happens, item stays |
| 8.4 | Share then back | Open share URL, close popup | App works normally |
| 8.5 | Switch tabs mid-search | Type search, switch to Wantlist | Search applies to Wantlist |
| 8.6 | Log in then switch theme | Log in, toggle light/dark | Admin mode preserved |
| 8.7 | Move item, log out | Move item, then log out | Item stays in Collection but no admin buttons |
| 8.8 | Empty search | Type spaces only | No crash |

---

## QUICK SMOKE TEST (5 min)
For fast validation after minor changes, run only:
1.1, 1.3, 2.1, 2.3, 3.1, 4.1, 4.6, 5.3, 5.5, 6.1, 6.5, 8.1

## FULL REGRESSION (~20 min)
Run all tests in order after major changes.

---

## REPORTING

When reporting results, use this format:

```
## Regression Run — [DATE]
### Version: index.html uploaded [DATE]
### Tester: [NAME]

| Section | Pass | Fail | Partial |
|---------|------|------|---------|
| 1. Load & Theme | X | X | X |
| 2. Navigation | X | X | X |
| ... | | | |

### Failed tests:
- 3.2 ❌ Search in Wantlist — search bar not visible
- 5.11 ⚠️ Statistics locked — shows blank instead of lock message

### Notes:
[Any observations]
```
