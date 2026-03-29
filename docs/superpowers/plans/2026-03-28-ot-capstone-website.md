# Balance & Thrive Website Implementation Plan

> **For agentic workers:** REQUIRED: Use superpowers:subagent-driven-development (if subagents available) or superpowers:executing-plans to implement this plan. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build a 5-page static website (homepage + 4 topic pages) for an OT capstone occupational balance and wellness program for collegiate athletes.

**Architecture:** Plain HTML/CSS/JS with no build tools or dependencies. Shared `styles.css` for all visual design, shared `script.js` for accordion and hamburger menu interactivity. Each page is a standalone HTML file linking to the shared CSS and JS.

**Tech Stack:** HTML5, CSS3, vanilla JavaScript

**Spec:** `docs/superpowers/specs/2026-03-28-ot-capstone-website-design.md`

---

## Chunk 1: Foundation (CSS + JS + Homepage)

### Task 1: Create shared stylesheet (styles.css)

**Files:**
- Create: `styles.css`

- [ ] **Step 1: Create styles.css with CSS custom properties and reset**

Define all colors, fonts, and base reset styles at the top using CSS custom properties:

```css
:root {
  --navy: #0C1244;
  --light-blue: #69B3E7;
  --soft-blue-bg: #f0f6fc;
  --white: #FFFFFF;
  --dark-gray: #333333;
  --medium-gray: #666666;
  --light-gray: #888888;
  --font-stack: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, sans-serif;
}
```

Plus `*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }`, `html { scroll-behavior: smooth; }`, and base `body` styles (font-family, color, line-height).

- [ ] **Step 2: Add nav bar styles**

`.navbar` — white background, light blue 2px bottom border, flexbox with space-between, sticky top, z-index 100.
`.navbar .site-title` — navy, bold, font-size 1.25rem.
`.nav-links a` — dark gray, no underline, hover turns light blue.
`.nav-links a.active` — light blue color, font-weight 600.
`.hamburger` — hidden by default, display block at ≤768px.
`.nav-links.open` — mobile dropdown panel styles.

- [ ] **Step 3: Add hero section styles**

`.hero` — centered text, padding 80px 20px.
`.hero .label` — uppercase, letter-spacing 2px, light blue, small font.
`.hero h1` — navy, font-size 2.5rem, font-weight 800.
`.hero .subtitle` — medium gray, font-size 1.1rem, max-width 600px, margin auto.
`.btn-primary` — light blue background, white text, padding 12px 28px, border-radius 25px, hover darkens slightly.

- [ ] **Step 4: Add topic cards styles**

`.topics-section` — soft blue background, padding 60px 20px.
`.topics-grid` — display grid, 2 columns, gap 20px, max-width 800px, margin auto.
`.topic-card` — white background, left 3px solid light blue border, border-radius 4px, padding 20px, text-decoration none, transition shadow/transform.
`.topic-card:hover` — slight box-shadow and translateY(-2px).
`.topic-card .icon` — font-size 1.5rem.
`.topic-card h3` — navy.
`.topic-card p` — light gray, small font.

- [ ] **Step 5: Add about section and footer styles**

`.about-section` — white background, centered text, max-width 700px, padding 60px 20px.
`.footer` — navy background, white text, centered, padding 30px 20px, small font.

- [ ] **Step 6: Add topic page styles**

`.page-header` — padding 60px 20px, centered, navy heading, medium gray intro text.
`.accordion-item` — white background, margin-bottom 12px, border-radius 6px, overflow hidden.
`.accordion-header` — clickable button, full width, flexbox with heading left and chevron right, padding 18px 20px, navy text, hover soft blue bg. Chevron rotates 180deg when expanded.
`.accordion-body` — max-height 0, overflow hidden, transition max-height 0.3s ease. When `.accordion-item.open .accordion-body` — max-height 500px.
`.takeaways-box` — soft blue background, border-radius 8px, padding 24px, left light blue border.
`.download-btn` — light blue background, white text, rounded, centered.
`.topic-nav` — flexbox space-between, previous/next links styled as text links.

- [ ] **Step 7: Add responsive breakpoints**

At `max-width: 768px`:
- `.topics-grid` → single column
- `.nav-links` → hidden, `.nav-links.open` → flex column dropdown below nav
- `.hamburger` → display block
- `.hero h1` → font-size 1.8rem

At `max-width: 480px`:
- Reduce padding throughout
- `.hero h1` → font-size 1.5rem

- [ ] **Step 8: Verify styles.css in browser**

Open `styles.css` and confirm it parses without errors (no syntax issues). Confirm file is complete.

- [ ] **Step 9: Commit**

```bash
git add styles.css
git commit -m "feat: add shared stylesheet with full design system"
```

---

### Task 2: Create shared JavaScript (script.js)

**Files:**
- Create: `script.js`

- [ ] **Step 1: Create script.js with accordion functionality**

On DOMContentLoaded, query all `.accordion-header` buttons. Add click listener to each that:
- Toggles `.open` class on parent `.accordion-item`
- Updates `aria-expanded` attribute on the button
- Supports keyboard activation (Enter/Space) — this is automatic since we use `<button>` elements

- [ ] **Step 2: Add hamburger menu toggle**

Query `.hamburger` button and `.nav-links`. Click listener toggles `.open` class on `.nav-links` and updates `aria-expanded` on hamburger. Click on a nav link closes the menu. Click outside the nav closes the menu (document click listener that checks if click target is outside `.navbar`).

- [ ] **Step 3: Add smooth scroll for Get Started button**

Query any `a[href^="#"]` links. Add click listener that calls `preventDefault()` and uses `element.scrollIntoView({ behavior: 'smooth' })`.

- [ ] **Step 4: Verify script.js**

Read through the file and confirm no syntax errors, proper event delegation, and all features are present.

- [ ] **Step 5: Commit**

```bash
git add script.js
git commit -m "feat: add shared JS for accordion, hamburger menu, and smooth scroll"
```

---

### Task 3: Create homepage (index.html)

**Files:**
- Create: `index.html`

- [ ] **Step 1: Create index.html with full page structure**

Write the complete HTML file with:
- `<!DOCTYPE html>`, lang="en", charset UTF-8, viewport meta
- `<title>Home | Balance & Thrive</title>`
- Link to `styles.css`
- Nav bar with "Balance & Thrive" title, links to all 5 pages (Home active), hamburger button (hidden desktop)
- Hero section with label "FOR COLLEGIATE ATHLETES", h1 "Occupational Balance & Wellness", subtitle paragraph, "Get Started" anchor button linking to `#topics`
- Topics section (`id="topics"`) with 2x2 grid of 4 topic cards, each linking to its page:
  - ⏰ Time Management — "Strategies for balancing athletics, academics, and self-care"
  - 🌙 Sleep Hygiene — "Evidence-based practices for better rest and recovery"
  - 🥗 Nutrition Habits — "Fueling your body for performance and well-being"
  - 🧘 Stress Management — "Mindfulness and resilience techniques for daily life"
- About section with placeholder paragraph about the program's OT foundations
- Footer with full attribution text
- Script tag linking to `script.js` before closing `</body>`

- [ ] **Step 2: Open index.html in browser and verify**

Open the file directly in a browser. Verify:
- Nav bar renders with white bg and blue accent line
- Hero text is centered and properly styled
- Topic cards display in 2x2 grid with blue left borders
- "Get Started" smooth-scrolls to topics section
- Footer displays correctly
- Hover effects work on cards and button

- [ ] **Step 3: Test responsive behavior**

Resize browser to ~768px and ~480px. Verify:
- Cards stack to single column
- Hamburger icon appears and toggles nav menu
- Text sizes adjust appropriately

- [ ] **Step 4: Commit**

```bash
git add index.html
git commit -m "feat: add homepage with hero, topic cards, and about section"
```

---

## Chunk 2: Topic Pages

### Task 4: Create Time Management page (time-management.html)

**Files:**
- Create: `time-management.html`

- [ ] **Step 1: Create time-management.html**

Full HTML file with:
- `<title>Time Management | Balance & Thrive</title>`
- Nav bar with "Time Management" link marked active
- Page header: h1 "Time Management", intro paragraph placeholder
- 3 accordion sections (all collapsed by default):
  1. "Why Time Management Matters for Athletes" — `<button>` header with `aria-expanded="false"`, `aria-controls` pointing to content div. Body has placeholder text: "[Placeholder: Add content about the importance of time management for collegiate athletes, including research findings and real-world impact.]"
  2. "Practical Scheduling Strategies" — same pattern, placeholder: "[Placeholder: Add specific scheduling strategies, tools, and techniques athletes can use to manage their time effectively.]"
  3. "Balancing Priorities: Athletics, Academics, and Self-Care" — placeholder: "[Placeholder: Add guidance on how to identify and balance competing priorities, with practical examples for athletes.]"
- Key Takeaways box with 3 placeholder bullet points
- Download button: "Download Time Management Worksheet (Coming Soon)" linking to `#`
- Topic nav: no "Previous", "Next: Sleep Hygiene →" linking to `sleep-hygiene.html`
- Footer (same as homepage)

- [ ] **Step 2: Open in browser and verify**

Verify nav highlights correct page, accordions expand/collapse on click, keyboard Enter/Space works, chevron rotates, takeaways box renders with blue bg, download button is styled, next topic link works.

- [ ] **Step 3: Commit**

```bash
git add time-management.html
git commit -m "feat: add Time Management topic page with accordion sections"
```

---

### Task 5: Create Sleep Hygiene page (sleep-hygiene.html)

**Files:**
- Create: `sleep-hygiene.html`

- [ ] **Step 1: Create sleep-hygiene.html**

Same template as time-management.html with:
- `<title>Sleep Hygiene | Balance & Thrive</title>`
- Nav: "Sleep Hygiene" active
- h1: "Sleep Hygiene"
- Accordion sections:
  1. "The Science of Sleep and Athletic Performance" — "[Placeholder: Add content about sleep science, circadian rhythms, and how sleep impacts athletic performance and recovery.]"
  2. "Building a Healthy Sleep Routine" — "[Placeholder: Add evidence-based strategies for establishing consistent sleep schedules, bedtime routines, and sleep environment optimization.]"
  3. "Common Sleep Challenges and Solutions" — "[Placeholder: Add content addressing common sleep issues athletes face (travel, early practices, screen time) and practical solutions.]"
- Key Takeaways: 3 placeholder bullets
- Download: "Download Sleep Hygiene Worksheet (Coming Soon)"
- Topic nav: "← Previous: Time Management" | "Next: Nutrition Habits →"

- [ ] **Step 2: Open in browser and verify**

Same checks as Task 4. Also verify previous/next links navigate correctly.

- [ ] **Step 3: Commit**

```bash
git add sleep-hygiene.html
git commit -m "feat: add Sleep Hygiene topic page with accordion sections"
```

---

### Task 6: Create Nutrition Habits page (nutrition.html)

**Files:**
- Create: `nutrition.html`

- [ ] **Step 1: Create nutrition.html**

Same template with:
- `<title>Nutrition Habits | Balance & Thrive</title>`
- Nav: "Nutrition" active
- h1: "Nutrition Habits"
- Accordion sections:
  1. "Nutrition Fundamentals for Athletes" — "[Placeholder: Add content about macronutrients, micronutrients, and the unique nutritional needs of collegiate athletes.]"
  2. "Meal Planning and Healthy Eating Strategies" — "[Placeholder: Add practical meal planning tips, sample meal ideas, and strategies for healthy eating with a busy athlete schedule.]"
  3. "Hydration and Recovery Nutrition" — "[Placeholder: Add content about hydration guidelines, pre/post-workout nutrition, and recovery fueling strategies.]"
- Key Takeaways: 3 placeholder bullets
- Download: "Download Nutrition Habits Worksheet (Coming Soon)"
- Topic nav: "← Previous: Sleep Hygiene" | "Next: Stress Management →"

- [ ] **Step 2: Open in browser and verify**

Same checks as previous topic pages.

- [ ] **Step 3: Commit**

```bash
git add nutrition.html
git commit -m "feat: add Nutrition Habits topic page with accordion sections"
```

---

### Task 7: Create Stress Management page (stress-management.html)

**Files:**
- Create: `stress-management.html`

- [ ] **Step 1: Create stress-management.html**

Same template with:
- `<title>Stress Management | Balance & Thrive</title>`
- Nav: "Stress Management" active
- h1: "Stress Management & Mindfulness"
- Accordion sections:
  1. "Understanding Stress in Collegiate Athletics" — "[Placeholder: Add content about sources of stress for college athletes, the stress response, and how chronic stress affects performance and well-being.]"
  2. "Mindfulness Techniques and Practices" — "[Placeholder: Add practical mindfulness exercises, breathing techniques, meditation guidance, and body scan practices athletes can incorporate into their routines.]"
  3. "Building Long-Term Resilience" — "[Placeholder: Add content about developing coping strategies, building support networks, and creating sustainable stress management habits.]"
- Key Takeaways: 3 placeholder bullets
- Download: "Download Stress Management Worksheet (Coming Soon)"
- Topic nav: "← Previous: Nutrition Habits" | no "Next"

- [ ] **Step 2: Open in browser and verify**

Same checks. Verify no "Next" link appears on this last page.

- [ ] **Step 3: Commit**

```bash
git add stress-management.html
git commit -m "feat: add Stress Management topic page with accordion sections"
```

---

### Task 8: Create assets directory and final verification

**Files:**
- Create: `assets/` directory (empty, for future use)

- [ ] **Step 1: Create assets directory**

```bash
mkdir -p assets
```

- [ ] **Step 2: Full cross-page navigation test**

Open each page and verify:
- All nav links work and correct page is highlighted
- Previous/Next topic navigation is correct across all 4 topic pages
- Homepage "Get Started" scrolls to topics
- All topic cards on homepage link to correct pages
- Hamburger menu works on all pages at mobile width
- Accordions work on all topic pages

- [ ] **Step 3: Final commit**

```bash
git add assets/.gitkeep
git commit -m "feat: add assets directory for future downloadable resources"
```
