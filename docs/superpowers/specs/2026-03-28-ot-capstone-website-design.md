# OT Capstone Website — Design Spec

## Overview

A multi-page informational website for an occupational therapy capstone research project conducted at Westminster College, New Wilmington, PA. The site serves as a resource for an occupational balance and wellness educational program designed for collegiate athletes.

## Audience

- Athletic department director (primary distributor)
- Coaches (via director)
- Capstone professors and faculty (reviewers)

## Technical Approach

Plain HTML/CSS/JS — no build tools, no frameworks, no dependencies. Portable and easy to host anywhere.

## File Structure

```
jenna_capstone/
├── index.html              # Homepage
├── time-management.html    # Time Management topic page
├── sleep-hygiene.html      # Sleep Hygiene topic page
├── nutrition.html          # Nutrition Habits topic page
├── stress-management.html  # Stress Management / Mindfulness page
├── styles.css              # Shared stylesheet
├── script.js               # Shared JavaScript
└── assets/                 # Images, downloadable files (future)
```

## Visual Design

**Style: Modern & Warm (Option B)**

- Sans-serif typography throughout (system font stack: -apple-system, BlinkMacSystemFont, Segoe UI, etc.)
- White navigation bar with light blue (#69B3E7) bottom accent line
- White/light backgrounds with soft blue (#f0f6fc) section accents
- Left-bordered cards with light blue accent
- Rounded buttons with light blue background and white text
- Clean, airy layout with generous whitespace

**Color Palette (inspired by Westminster College, subtle — no heavy branding)**

| Color        | Hex     | Usage                                      |
|--------------|---------|---------------------------------------------|
| Navy Blue    | #0C1244 | Headings, text, strong emphasis             |
| Light Blue   | #69B3E7 | Accents, borders, buttons, active nav links |
| Soft Blue BG | #f0f6fc | Section backgrounds, card backgrounds       |
| White        | #FFFFFF | Page background, nav background             |
| Dark Gray    | #333333 | Body text                                   |
| Medium Gray  | #666666 | Subtitles, secondary text                   |
| Light Gray   | #888888 | Tertiary text, descriptions                 |

## Program Name & Copy

- **Program name / site title:** "Balance & Thrive"
- **Nav title:** "Balance & Thrive"
- **Hero heading:** "Occupational Balance & Wellness"
- **Hero subtitle:** "An evidence-based educational program helping collegiate athletes thrive on and off the field."
- **Page `<title>` format:** "Page Name | Balance & Thrive"

## Page Designs

### Homepage (index.html)

1. **Nav bar** — white background, "Balance & Thrive" left-aligned, page links right-aligned, light blue bottom border
2. **Hero section** — centered text on white background
   - Small uppercase label: "For Collegiate Athletes"
   - Large bold heading: "Occupational Balance & Wellness"
   - Subtitle: "An evidence-based educational program helping collegiate athletes thrive on and off the field."
   - "Get Started" button — smooth-scrolls to the topic cards section below
3. **Topic cards section** — 2x2 grid of cards, each with:
   - Left blue border accent
   - Emoji icon, topic title, short description
   - Clickable — links to respective topic page
   - Card details:
     - ⏰ Time Management — "Strategies for balancing athletics, academics, and self-care"
     - 🌙 Sleep Hygiene — "Evidence-based practices for better rest and recovery"
     - 🥗 Nutrition Habits — "Fueling your body for performance and well-being"
     - 🧘 Stress Management — "Mindfulness and resilience techniques for daily life"
4. **Brief about section** — short paragraph about the program and its OT foundations
5. **Footer** — "Balance & Thrive — An Occupational Balance & Wellness Educational Program | Research conducted at Westminster College, New Wilmington, PA | Capstone Project, Doctor of Occupational Therapy"

### Topic Pages (shared template)

Each of the 4 topic pages follows the same layout:

1. **Nav bar** — same as homepage, current page highlighted with light blue color
2. **Page header** — topic title, brief intro paragraph
3. **Content sections** — 3 expandable/collapsible accordion sections per page, each with:
   - A descriptive heading indicating the content category
   - Placeholder body text explaining what content will go there
   - Accordion starts collapsed; click to expand/collapse
   - Uses `aria-expanded` and `aria-controls` attributes for accessibility
   - Keyboard accessible (Enter/Space to toggle)
4. **Key Takeaways box** — highlighted soft blue box with 3-4 placeholder bullet points
5. **Downloadable resource placeholder** — one styled button per page, text: "Download [Topic] Worksheet (Coming Soon)", links to `#` for now; files will go in `assets/` as `time-management-worksheet.pdf`, etc.
6. **Navigation links** — "Previous Topic" / "Next Topic" links at bottom
   - Canonical topic order: Time Management → Sleep Hygiene → Nutrition Habits → Stress Management
   - First page has no "Previous"; last page has no "Next"
7. **Footer** — same as homepage

### Placeholder Accordion Sections Per Topic

**Time Management:**
1. "Why Time Management Matters for Athletes"
2. "Practical Scheduling Strategies"
3. "Balancing Priorities: Athletics, Academics, and Self-Care"

**Sleep Hygiene:**
1. "The Science of Sleep and Athletic Performance"
2. "Building a Healthy Sleep Routine"
3. "Common Sleep Challenges and Solutions"

**Nutrition Habits:**
1. "Nutrition Fundamentals for Athletes"
2. "Meal Planning and Healthy Eating Strategies"
3. "Hydration and Recovery Nutrition"

**Stress Management / Mindfulness:**
1. "Understanding Stress in Collegiate Athletics"
2. "Mindfulness Techniques and Practices"
3. "Building Long-Term Resilience"

## Interactive Elements

- **Expandable/collapsible sections** — click heading to reveal/hide content; CSS transitions for smooth animation; vanilla JS toggle; `aria-expanded` and `aria-controls` for screen readers; keyboard accessible via Enter/Space
- **Download buttons** — styled placeholder buttons with "Coming Soon" label; will link to actual files when ready
- **Smooth scrolling** — CSS `scroll-behavior: smooth` for anchor links
- **Hover effects** — subtle scale/shadow transitions on cards and buttons

## Responsive Design

- Desktop-first layout
- Responsive breakpoints for tablet (~768px) and mobile (~480px)
- Topic cards stack to single column on mobile
- Nav collapses to a hamburger menu on mobile
  - Hamburger icon (three lines) replaces nav links
  - Click toggles a dropdown panel below the nav bar
  - Panel shows nav links stacked vertically
  - Click outside the panel or on a link closes it
  - Uses `aria-expanded` on the toggle button

## Icons

All topic icons use native emoji characters — no image files or SVG icon libraries needed:
- ⏰ Time Management
- 🌙 Sleep Hygiene
- 🥗 Nutrition Habits
- 🧘 Stress Management

## Content Strategy

All content is placeholder for now. Each topic page will have structured placeholder sections that can be swapped with real educational content later. Placeholder text will clearly indicate what type of content belongs in each section (e.g., "[Placeholder: Add evidence-based strategies for building a sleep routine here]").

## Constraints

- No external dependencies (no CDN links, no npm packages)
- Must work when opened as local files or served from any static host
- No server-side code required
- Semantic HTML with proper heading hierarchy (h1 → h2 → h3)
- ARIA attributes on interactive elements (accordions, hamburger menu)
- Keyboard-navigable interactive elements
- Alt text placeholders on any future images
