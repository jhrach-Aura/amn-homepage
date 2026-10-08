# PRD: AZ MVD Now (AMN) Homepage — Prototype Iteration

| | |
|---|---|
| **Status** | Draft v0.1 |
| **Date** | 2026-10-07 |
| **Owner** | Jon Hrach |
| **Stakeholders** | TBD (ADOT MVD product owner, UX research, content, accessibility) |
| **Scope** | Prototype iteration and usability testing only — not a production build |
| **Source prototype** | [AZMVDNow-responsive-prototype.html](../AZMVDNow-responsive-prototype.html) (copied from "AMN Homepage Grayscale Prototype 1.html") |

---

## 1. Overview & purpose

AZ MVD Now (AMN) is Arizona MVD's online services portal. The homepage is the front door for
residents who want to finish MVD business online: renewing a registration, booking an
appointment, applying for a Travel ID, or responding to a letter from MVD.

"Grayscale Prototype 1" is a clickable, responsive concept of a redesigned homepage. This PRD
records what the prototype contains today, defines the requirements for the next rounds of
prototyping, and sets out what usability research must validate. It does not cover a
production build.

## 2. Problem statement

Many customers come to the AMN homepage with a single task in mind, and they often don't know
whether that task needs an account. The homepage has to:

- Help people find the service they need quickly, whether they browse or search.
- Make it clear which services guests can use without signing in, and which need an account.
- Persuade people to create an account by showing what they get from it.
- Tell people who received a compliance letter exactly what to do next.
- Work on phones and in languages other than English.

## 3. Goals and non-goals

### Goals (for this prototype phase)
1. Validate the information architecture: the 5-tab global nav and its menu taxonomy.
2. Validate findability of the top tasks from the hero tiles, Guest Services, nav, and search.
3. Make the difference between the guest path and the sign-in path clear.
4. Validate the "Got a Letter from MVD?" step-by-step guidance.
5. Confirm the layout and interactions work from small phones (≤410px) up to wide desktops.
6. Produce a prototype that is ready for testing and meets WCAG 2.1 AA at prototype fidelity.

### Non-goals
- Production implementation, CMS integration, or deployment.
- Real authentication (Azure AD B2C) integration.
- A real search backend or analytics instrumentation.
- Rebuilding the downstream service pages that tiles and menus link to.

## 4. Target users

| Persona | Needs from the homepage |
|---|---|
| **Returning account holder** | Sign in fast; find documents, receipts, plates and titles. |
| **Guest / one-off task** | Renew a registration, get a permit, or view receipts without an account. |
| **New to Arizona** | Learn how to transfer a license and register a vehicle. |
| **Letter recipient** | Understand a compliance letter and what action to take. |
| **Traveler** | Get an Arizona Travel ID (REAL ID) before flying. |
| **Non-English speaker** | Switch the page to Spanish, French, Chinese, and other languages. |
| **Mobile user** | Do all of the above on a phone. |

## 5. Key user tasks (test scenarios)

1. Renew a vehicle registration without signing in.
2. Schedule an MVD appointment.
3. Start a Travel ID application.
4. You received a letter from MVD. Find out what to do.
5. Find the nearest MVD office or an Authorized Third Party.
6. Order a specialty or personalized plate.
7. Find out whether you need an account, then create one.
8. Switch the page to Spanish.
9. Search for "driver license renewal" and open the result.

## 6. Prototype inventory (current state)

The page, top to bottom:

| # | Section | Content | Interactions |
|---|---|---|---|
| 1 | **Header / global nav** | AZ MVD Now logo; tabs: Vehicle, Driver License & ID, Title, **Voter Registration** (a direct link with no menu), Other, Help; **Sign In / Sign Up** button | Hover or click opens a dropdown menu, and items with children open a flyout submenu. Esc or a click outside closes it. Below a breakpoint the tabs collapse into a hamburger that opens a 3-level accordion. Menu items and Sign In only show a "Prototype: …" toast. |
| 2 | **Alerts** | A slim strip (about 45px) directly under the header, outside the hero. Collapsed by default, it shows "⚠ **3 alerts:** Register to vote · Office hours · New service" and *View alerts*. Expanded, each alert has a bold title, a one-sentence message, and a descriptive link. | *View alerts* / *Hide alerts* toggle (`aria-expanded`). Each alert has its own dismiss button and the summary updates; focus moves to the next alert, or to the H1. With one alert left, its full text shows inline with no toggle; with none, the strip disappears. On mobile the summary shortens to "3 alerts" and *View*. Kept quiet on purpose so it doesn’t compete with the hero. |
| 3 | **Hero** | H1 "Arizona MVD Services Without Leaving Home"; sub "Take care of your MVD business online—quickly and securely." | 6 quick-service tiles: Registration Renewal, Schedule an Appointment, Voter Registration, Travel ID Application, New to Arizona, ADOT Website. **See More** scrolls to Guest Services. |
| 4 | **Travel ID promo** | "Get Airport-Ready with an Arizona Travel ID" + supporting copy | **Apply Now** (primary), **Learn More** (link) |
| 5 | **Account activation pitch** | "Do More with an AZ MVD Now Account" + 4 benefits: Skip the office visit · All documents in one place · Manage plates and titles · Pay and track receipts | Benefit icons scale on hover. **Sign Up** CTA (intro: "Sign up in minutes to get these benefits:"), plus a note: "Moving to Arizona? Visit an MVD office first, then sign up." (The client prefers "Sign Up" here, even though the writing guide calls for "Activate".) (The heading was "New to AZ MVD Now?", which new residents could confuse with "New to Arizona".) |
| 6 | **Got a Letter from MVD?** | Written for "stressed and complex" visitors (DUI or complex compliance letters). H2 and intro, then 4 numbered step cards: Sign in to AZ MVD Now ("No account? Activate it first.") → Find your letter → Scan the QR code → Review your compliance issues. Below the cards is an action row: **Sign In to View Your Letter** plus a quiet "Have a court order? Contact MVD before you act on it." note. | Static, with no hover or accordion. Cards show 4 across, 2×2 at ≤1100px, and 1 column at ≤620px; on mobile the steps come before the CTA. New-tab links show an external icon and screen-reader text. The desert-highway photo was removed because it didn’t match the content; the image file is still in the prototype file. |
| 7 | **Guest Services** | "No account needed. You’ll verify your identity using your existing MVD record." 8 tiles: Registration Renewal, Voter Registration, View Plate Gallery, Restricted 3-Day Permit, De-Insure Vehicle, Payment Summary, View Receipts, Aircraft Renewal | **View All / View Less** collapses the grid. |
| 8 | **Need Help?** | 6 cards: Contact Arizona MVD, Find an MVD Location, View Video Library, Provide Feedback, Report Fraud, Visit azdot.gov | External links |
| 9 | **Footer** | ADOT logo, "All Rights Reserved.", links: Forms and Publications, Privacy Statement, Help, Text Message Policy | Language picker (English, Español, Français, 中文) that loads Google Translate |
| — | **Search results view** (alternate state) | "Results" / "No Results Found", list of matches, "Frequently Searched" (Registration Renewal, Driver License Renewal, Schedule an Appointment), "Search azdot.gov/MVD" fallback, **Back to Home** | Prefix match against a fixed list of services built from the nav taxonomy plus extra services. **There is currently no search input in the page**, so this view can't be reached (see §10). |

### Visual design (as built)
- **Typefaces:** Roboto, Inter, Open Sans.
- **Palette:** navy `#1C3E61`; teal `#2D6D67` / `#459892`; CTA orange `#B25E1C`; tint `#E9F3F2`;
  secondary text `#5a5f73`. The file is named "Grayscale", but the build is in color (see open questions).
- **Responsive:** 13 breakpoints from 410px to 2010px; the tile grids and the letter-step row reflow.

## 7. Information architecture (global nav)

- **Vehicle**
  - Registration — Registration Renewal · Registration Reinstatement · Registration Replacement with Decal · Registration Refund
  - Plates — Specialty and Personalized Plates · Plate Replacement · Disability Placard Replacement · Duplicate Plate · Plate Order Status · Change Plate Background
  - Permits — 30-Day General Use Permit · Restricted 3-Day Permit
  - Off-Highway Decals — Off-Highway Decal Issue/Renewal · Off-Highway Decal Replacement · Required Course: Safe & Ethical Riding in Arizona
  - Motor Vehicle Record
  - Vehicle Fees/Taxes Paid
  - Emissions
  - Fleet Management
  - Watch Your Car
- **Driver License & ID**
  - Arizona Travel ID (REAL ID)
  - Driver License — Application · Replacement · Renewal · Record · At-home Permit Test
  - Identification Card — Application · Replacement
  - Commercial Driver License (CDL) — Application · Replacement · Renewal · Medical Status Verification
  - Mobile ID Management
- **Title**
  - Title Viewer · Title Information (Other Vehicles) · eTitle Transfer · Title Replacement · Sold Notice · Bill of Sale
- **Voter Registration** (top-level link to the AZ MVD Now voter registration page; moved out of Other)
- **Other**
  - Change Address · Aircraft Registration Renewal · Manage Insurance · Manage Compliance Issues · Compliance Issues Timeline · View Receipts · Dealer Licensing and Services · Apply for an Organization Account
- **Help**
  - Schedule an Appointment · Contact Us · MVD Invitation Code · Find an MVD Location · Provide Feedback · Report Fraud · View Video Library · View Forms

## 8. Functional requirements (next prototype iteration)

Priority: **P0** = required for the next usability round, **P1** = should have, **P2** = nice to have.

### Global navigation
- **FR-01 (P0)** Six top-level nav items that match §7: five tabs with dropdown menus and flyout submenus, plus **Voter Registration** after Title as a direct link with no chevron. Hovering it closes any open menu. Below 1140px the nav collapses to the hamburger so all six items never wrap onto two rows.
  *Acceptance:* each menu opens on click and on hover. It closes on Esc, on a click outside, and on mouse-leave after a short delay.
- **FR-02 (P0)** The menus are fully keyboard operable: Tab or arrow keys move between tabs and items, Enter or Space opens a menu, and focus returns to the tab when a menu closes.
- **FR-03 (P0)** On mobile, a hamburger opens a 3-level accordion with the same taxonomy, and only one branch is open at each level. Voter Registration is a plain row that opens its page and closes the drawer.
- **FR-04 (P1)** Menu leaf items go to a stub page or a real destination URL instead of only showing a toast, so testers can confirm they reached the right place.
- **FR-05 (P0)** The **Sign In / Sign Up** button is always visible in the header at every breakpoint.

### Alert banner
- **FR-06 (P0)** Support 1–3 simultaneous alerts in a slim summary strip under the header, collapsed by default (count plus titles), so alerts don’t push down or compete with the hero and service tiles. No separate banners and no carousel. Each alert has a short title, a one-sentence message, and a descriptive link (not "Learn More"). Use no exclamation points. The region is a labeled `section`, not `role="alert"`.
- **FR-07 (P1)** A native toggle button (*View alerts* / *Hide alerts*, `aria-expanded` + `aria-controls`) reveals the alert details. Each alert is dismissible with a button labeled "Dismiss alert: <title>", and focus moves sensibly after dismissal. A single remaining alert shows inline without a toggle. (P2: dismissed alerts stay hidden for the session.)

### Hero and quick tiles
- **FR-08 (P0)** The hero shows ≤6 top-task tiles. The tile set must be justified by task data (TBD).
- **FR-09 (P0)** Each tile links to a stable destination. No hard-coded OAuth URLs (see §10).
- **FR-10 (P1)** **See More** scrolls to Guest Services and moves focus to that section heading.

### Travel ID promo
- **FR-11 (P0)** **Apply Now** goes to a stable Travel ID entry point. **Learn More** goes to the azdot.gov Travel ID page.

### Account sign-up pitch
- **FR-12 (P0)** Show four account benefits and a **Sign Up** CTA that goes to the activation entry point ("Sign Up" is a deliberate exception to the writing guide’s "Activate" term). Under the CTA, tell new residents they need to visit an MVD office before they can sign up, and link to the New to Arizona page. Don’t use "New to…" wording in this section.
- **FR-13 (P1)** Benefit hover effects are decorative only, and the content is the same without hover.

### Got a Letter from MVD?
- **FR-14 (P0)** Show the steps as a static numbered list (`<ol>`), all visible without interaction, so stressed visitors can scan them quickly. No hover-to-reveal content.
- **FR-15 (P0)** Make the steps the visual focus, and give the section one primary action (*Sign In to View Your Letter*). Step 1 links to account activation. The court-order note links to Contact MVD and stays visually quieter than the steps. Keep the tone steady and factual, with no exclamation points.
- **FR-16 (P1)** Steps name screens exactly as they appear in the product and nav (*Your Account* › *Your Documents*, *Other* › *Manage Compliance Issues*). These labels need confirming against the live AZ MVD Now UI.

### Guest Services
- **FR-17 (P0)** Show the guest-accessible services, every one with a working destination (De-Insure Vehicle currently uses `#`). Make it clear that no account is needed but guests must verify their identity against an existing MVD record, which means they must have done business with MVD before.
- **FR-18 (P1)** **View All / View Less** shows how many tiles are hidden and announces the change to screen readers.

### Need Help?
- **FR-19 (P0)** Six help cards, each with a label, a one-line description, and an external link indicator.

### Search
- **FR-20 (P0)** Add a visible search input (header or hero; placement TBD) wired to the existing results logic, with type-ahead suggestions (max 8).
- **FR-21 (P0)** The results view shows the match count, the query, result links, and **Back to Home**. The no-results view shows "Frequently Searched" plus an azdot.gov/MVD fallback.
- **FR-22 (P2)** The search tolerates synonyms and typos (for example, "tags" → plates, "REAL ID" → Travel ID).

### Footer and language
- **FR-23 (P0)** Footer links work. Footer "Help" currently uses `#`.
- **FR-24 (P1)** The language picker translates the page and remembers the choice for the session. The set of languages is TBD.

## 9. Non-functional requirements

- **Accessibility:** WCAG 2.1 AA at prototype fidelity:
  - Interactive elements are native `button`/`a` elements, not `div role="button"`.
  - Focus is visible on every control.
  - Teal and orange text and fills are checked for 4.5:1 contrast on white and tint backgrounds.
  - Hover-only behavior always has a click or keyboard equivalent.
  - External links that open in a new tab say so.
  - Images have meaningful alt text.
  - Respect `prefers-reduced-motion` for tile lift and scale effects.
- **Responsive:** All sections are usable from 320px to 2560px with no horizontal scroll.
  Touch targets are ≥44×44px.
- **Performance:** The prototype loads in under 3s on a typical connection. Translation scripts load only when needed (already lazy).
- **Content:** Plain language at about an 8th-grade reading level, and consistent service names across the nav, tiles, and search.
- **Privacy:** No real customer data, and no live tokens in links.

## 10. Known issues and gaps in Prototype 1

1. **No search input.** The search and results logic exists, but no field is rendered, so the results view can't be reached.
2. **Stale OAuth links.** The "Travel ID Application" tile and "Apply Now" link to Azure B2C authorize URLs with hard-coded `state`, `nonce`, and `code_challenge` values. These links will fail, and the values should not be shared. Replace them with stable entry URLs.
3. **Placeholder links.** De-Insure Vehicle and footer Help use `href="#"`.
4. **Toast-only actions.** Nav menu items and Sign In / Sign Up only show a "Prototype: …" toast.
5. **Duplication.** Registration Renewal and Voter Registration appear in both the hero and Guest Services. Travel ID appears both as a hero tile and as its own promo section.
6. ~~**Alert content.** "Alert!" has no body message.~~ Fixed: replaced with the multi-alert region and sample content (FR-06).
7. **Accessibility.** Tabs, menu items, and the language picker are `div role="button"` elements. The letter section now uses native `button`, `ol`, and `h3` elements. Keyboard support depends on a custom handler and needs an audit.
8. **Third-party dependency.** Google Translate is used for localization. Its accuracy and privacy implications need review.
9. **Naming mismatch.** The file is called "Grayscale", but it uses the full color palette.

## 11. Research plan and success metrics

| Method | Purpose |
|---|---|
| Moderated usability test (5–8 participants per round, desktop and mobile) | Task success on the §5 scenarios |
| Tree test of the §7 taxonomy | Nav findability without visual design |
| First-click test on the hero and Guest Services | Tile labeling and placement |
| Accessibility walkthrough (keyboard + screen reader) | FR-02, FR-14, and §9 |

**Metrics (targets TBD):** task success rate, time on task, first-click accuracy, tree-test
directness, SUS score, and the share of participants who can correctly say whether a task needs an account.

## 12. Open questions

1. Was the search bar removed on purpose, and if not, where should it go?
2. Should the next round be a true grayscale wireframe, or keep the brand palette?
3. Which top tasks belong in the hero, based on traffic data, and should we remove the duplication with Guest Services?
4. Where will alert content come from, who orders the alerts, and how often will they change? What is the maximum number of alerts at once (the design assumes 3)?
5. Which languages are required, and is Google Translate acceptable?
6. Is "Prototype 1" one of several variants to compare in testing?
7. Which services truly don't need sign-in, and what does the guest identity-verification flow involve (which details are checked against the MVD record)? This needs confirming with MVD.
8. What are the stable entry URLs for Travel ID and account activation?
9. What exactly do new Arizona residents need before they can activate an account (for example, an Arizona driver license or ID from an office visit)? Confirm this before finalizing the new-resident note.

## 13. Next steps

1. Review this draft with stakeholders and resolve the §12 questions.
2. Prototype 2: fix the §10 issues and P0 requirements, especially search, links, and accessibility semantics.
3. Run the tree test on the §7 taxonomy alongside Prototype 2.
4. Run usability round 1, then update this PRD with findings and set metric targets.

---

## Appendix A: Link map (as built)

| Element | Destination |
|---|---|
| Hero: Registration Renewal / Guest: Registration Renewal | `azmvdnow.gov/guest/customeranonymous/titleregistration/registrationrenewal/search/vehicle` |
| Hero: Schedule an Appointment | `azmvdnow.gov/appointments` |
| Hero / Guest: Voter Registration | `azmvdnow.gov/guest/customeranonymous/voterregistration` |
| Hero: Travel ID Application, Promo: Apply Now | Azure B2C authorize URL (stale, see §10) |
| Hero: New to Arizona | `azdot.gov/mvd/services/driver-license-ID/new-to-arizona` |
| Hero: ADOT Website | `azdot.gov/mvd` |
| Promo: Learn More | `azdot.gov/mvd/services/driver-services/arizona-travel-id` |
| Create Your Account | `azmvdnow.gov/home` |
| Guest: View Plate Gallery | `azmvdnow.gov/plates` |
| Guest: Restricted 3-Day Permit | `azmvdnow.gov/guest/customeranonymous/titleregistration/permits/search/customer` |
| Guest: De-Insure Vehicle | `#` (placeholder) |
| Guest: Payment Summary | `azmvdnow.gov/guest/customeranonymous/titleregistration/vehiclepaymentsummary/search/customer` |
| Guest: View Receipts | `azmvdnow.gov/guest/customeranonymous/receipts/search/customer` |
| Guest: Aircraft Renewal | `azmvdnow.gov/guest/customeranonymous/aircraft/search` |
| Help: Contact Arizona MVD | `azdot.gov/mvd/contact-mvd` |
| Help: Find an MVD Location | `azdot.gov/mvd/mvd-hours-and-locations` |
| Help: View Video Library | `azmvdnow.gov/videos` |
| Help: Provide Feedback | `azmvdnow.gov/guest/customeranonymous/survey/search/customer` |
| Help: Report Fraud | `azmvdnow.gov/guest/incidentreport/select` |
| Help: Visit azdot.gov | `azdot.gov` |
| Footer: Forms and Publications | `azdot.gov/mvd/forms-library` |
| Footer: Privacy Statement | `azdot.gov/privacy-statement` |
| Footer: Help | `#` (placeholder) |
| Footer: Text Message Policy | `azmvdnow.gov/textmessagepolicy` |

## Appendix B: Prototype technical notes

- The file is a self-contained bundle (React 18 + "dc-runtime" template). Assets (2 PNG logos, 1 JPEG photo that is currently unused,
  web fonts) are embedded as gzip+base64 and unpacked at load time. It needs JavaScript to render.
- The page has two views, toggled by state: `home` and `results`/`noresults`. The search list is built from the nav taxonomy plus 7 extra services.
