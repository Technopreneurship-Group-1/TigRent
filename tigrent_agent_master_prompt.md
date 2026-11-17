# Master Specification Prompt: TigRent Mobile Application Prototype

## Role & Objective
Act as a Principal Apple UI/UX Designer and Senior Full-Stack Mobile Engineer. Build a **100% functional, interactive, state-driven mobile application prototype** for **TigRent: A Digital Peer-To-Peer Rental System for Academic and Student Essentials within the UST Community**.

Every workflow, button, modal, financial calculation, and real-time exchange between **Borrower** and **Lender** must work end-to-end with reactive state and zero dead or placeholder buttons.

---

## 1. Strict Visual & Design Directives (100% Adherence Required)

### DON'TS (Strict Anti-Bloat & Anti-Template Guardrails)
* **No AI-Templated UI Designs:** Avoid generic SaaS dashboards, repetitive card grids, boilerplate layouts, or visually overcrowded screens. The aesthetic must feel handcrafted, cohesive, artistic, and purposefully engineered.
* **Zero Emojis or Generic AI Icons:** Do **not** use any Unicode emojis anywhere in the interface. Render all icons exclusively using bespoke, crisp inline vector SVGs modeled after Apple SF Symbols (`1.75px` stroke width, rounded caps, and optical balance).
* **No Unnecessary Whitespace or Cramped Gaps:** Maintain tight, rhythmic iOS spatial proportions (`8px` / `12px` / `16px` grid system) so content feels dense yet breathable.
* **Zero Misplaced or Stacked UI Components:** Ensure strict `z-index` layering, safe-area padding, and clean flex/grid alignment so floating bars, sheets, badges, and buttons never overlap or collide across any screen (Login, Marketplace, Active Rentals, Lender Hub, or Modals).
* **No Excessive Glassmorphism or Arbitrary Glows:** Use blur and glow effects strictly where functionally and aesthetically justified.

### DO'S (Apple Cupertino Craftsmanship & UST Theme)
* **Apple iOS Design Language & Smoothness:** Frame the app inside a native iOS mobile viewport (`390x844` responsive container) with Apple-grade typography (`-apple-system`, `SF Pro Display`, `Inter`), tactile spring transitions (`cubic-bezier(0.22, 1, 0.36, 1)`), iOS segmented controls, and smooth slide-up bottom sheets.
* **Creative Component Placements:** Use an asymmetric Bento discovery header, interactive status pills, floating live rental trackers, and contextual bottom drawers so users immediately understand how borrowing and lending work at a glance.
* **Smooth-Moving Ambient Background:** Implement a continuous, silky-smooth animated mesh gradient (`@keyframes ambientDrift`) behind the application layers that gently shifts warm Thomasian gold, cream, and parchment tones.
* **Refined Glass Components:** Use translucent Apple-style glass surfaces (`backdrop-filter: blur(22px) saturate(185%)` with subtle `1px` specular borders) for navigation docks, role switchers, mascot cards, and modal sheets.
* **University of Santo Tomas (UST) Color Palette:**
  * **Primary Backgrounds:** Warm Ivory (`#FAF8F3`) and Soft Parchment (`#F2ECE1`)
  * **Primary Typography & Contrast:** Deep Thomasian Obsidian (`#161412`) and Warm Espresso (`#5C5549`)
  * **UST Brand Accents:** Regent Gold (`#E5A000`), Sovereign Amber (`#F5B82E`), and Deep Gold (`#B87D00`)
  * **Semantic Status Colors:** Emerald (`#157F3B`) for Verified/Approved, Amber (`#D97706`) for Pending Extension, and Crimson (`#C92A2A`) for Overdue/Account Suspended.

### Interactive Tiger Mascot ("Tomasito")
* **Visual Design:** Create an artistic, multi-layered custom SVG mascot named **Tomasito** modeled after the fluffy, chubby-cheeked, smiling baby tiger cub reference photo (warm amber and cream fur, dark tiger stripes, cute pink triangle nose, rosy cheeks, and happy squinting eyes).
* **Golden Under-Glow Effect:** Place a warm, breathing golden radial glow (`filter: blur(10px)`) directly underneath Tomasito so he visually pops off his glass container.
* **Hover & Tap Interactivity:**
  * Hovering over Tomasito must trigger a smooth physical micro-animation (ear perk, slight head tilt, paw lift, and intensified golden under-glow).
  * Clicking or tapping Tomasito must cycle through context-aware speech bubbles offering UST campus rental trends, smart suggestions, and reminders (e.g., *"Roque Ruaño midterms alert: Scientific calculators & drafting tubes are up 48% today!"*, *"Beato Angelico students are looking for Canon DSLRs—list yours to earn passive income!"*, *"Maintain a 4.8+ rating to unlock your Verified Trusted Lender badge!"*).

---

## 2. Core Functional Requirements & End-to-End Business Logic

### A. Student Verification & Onboarding (RegForm AY Check + SheerID)
* Build an interactive Login & Verification workflow accessible both at launch and via the top verification status pill:
  1. **Primary Student Evidence:** Inputs for **UST Student Email** (`@ust.edu.ph`), **Student ID Number** (e.g., `2023-148291`), **Full Name**, and **UST College/Building**.
  2. **Registration Form (RegForm) Academic Year Validation:** The system maintains an active system academic year set to **`AY 2026-2027`**. When a Borrower or Lender uploads/submits their RegForm, the system extracts the RegForm's Academic Year and validates whether it matches the current system academic year (`AY 2026-2027`).
  3. **SheerID Student Verification Pipeline:** Simulate an automated **SheerID** enrollment verification check (similar to Spotify/Apple Music student verification) that cross-checks the Student ID, UST Email, and RegForm Academic Year.
* **Interactive Test States:** Provide a 1-click toggle inside the verification modal allowing evaluators to test:
  * **Valid RegForm (`AY 2026-2027`):** Passes SheerID + AY validation, awards the **Verified Student** badge, and unlocks borrowing and lending privileges.
  * **Expired/Invalid RegForm (`AY 2024-2025`):** Fails validation with a clear error banner blocking unverified transactions until a valid current-year RegForm is submitted.

### B. Unconstrained Dual-Role Exchange (Borrower Mode ↔ Lender Hub)
* Provide a persistent, smooth segmented control at the top of the app allowing instant switching between **Borrower Mode** and **Lender Hub** backed by a single unified reactive state store.
* Any action taken by the Borrower (booking an item, requesting an extension, cancelling a booking, or rating the lender) must immediately reflect in the Lender Hub—and vice versa—without page reloads or constraints.

### C. Equipment Discovery, Daily Pricing & Mandatory Terms & Conditions
* **Campus Equipment Marketplace:** Include realistic UST rental listings across categories (*Calculators, Cameras & Media, Drafting & Architecture, Org Projectors & Audio, Lab & Med Gear*) with campus pickup hubs (*Roque Ruaño Lobby, Beato Angelico Lobby, Frassati Lobby, Main Building, Tan Yan Kee Student Center*).
* **Lender-Defined Daily Pricing:** Pricing depends on the lender's daily rate (`₱/day`) and how many days the item will be borrowed (`1 to 14 days`). Dynamically calculate:
  $$\text{Total Rental Fee} = \text{Daily Rate} \times \text{Rental Days}$$
  $$\text{Total Upfront Payment} = \text{Total Rental Fee} + \text{Refundable Security Deposit}$$
* **Mandatory Terms & Conditions (Borrower & Lender Digital Contract):** Before completing a booking (or publishing a new listing), require the user to inspect and check a mandatory agreement covering:
  1. **Damaged Equipment Policy:** If the borrower damages the item, repair costs or full replacement value are deducted from the security deposit and billed according to the agreed condition log.
  2. **Late Return & Unreturned Item Policy:** Returning an item past the promised date/time incurs an automatic daily late penalty (`25% of daily rate per hour` or `1.5x daily rate per overdue day`) deducted from the deposit.
  3. **Campus Meetup & Inspection Protocol:** Both parties verify equipment condition upon handoff at the designated UST lobby.
* **PayMongo Digital Checkout:** Support seamless payment selection via **GCash** or **Maya** with instant reference number generation.

### D. Rental Extension Request Workflow (Borrower Request → Lender Approve/Reject)
* **Borrower Side:** On any active rental card, include a **"Request Extension"** button where the borrower selects additional days (`+1 to +5 days`), sees the exact extension cost based on the lender's daily rate, adds a note, and submits the request.
* **Lender Side:** In **Lender Hub**, highlight incoming extension requests with interactive **"Approve Extension"** and **"Reject Request"** buttons:
  * **Approve:** Automatically extends the return due date, adds the extension fee to the rental total, recalculates the lender's net payout, and notifies the borrower.
  * **Reject:** Retains the original return deadline and alerts the borrower to return the item as scheduled.

### E. Refund, Cancellation & Deposit Settlement Logic
* Include an interactive **"Cancel / Refund & Settlement"** sheet on rentals that calculates and executes exact refunds:
  * **Early Borrower Cancellation (`>24 hrs` before pickup):** `100%` refund of rental fee + `100%` security deposit back to GCash/Maya.
  * **Late Borrower Cancellation (`<24 hrs` before pickup):** `80%` refund of rental fee + `100%` security deposit (`20%` retained as lender compensation).
  * **Lender Cancellation:** `100%` full refund to the borrower + automatic trust rating penalty applied to the lender.
  * **Return Condition & Damage/Late Deduction Calculator:** When marking an item returned, allow testing Normal Return (`100%` deposit refunded) vs. Late or Minor Damage Return (automatically deducts the penalty/repair fee from the deposit and refunds the remainder).

### F. Mutual Rating System, "Verified Trusted Lender" Badge & Low-Rating Account Suspension
* **Two-Way Rating System:** Upon rental completion, allow **Borrower to rate Lender** and **Lender to rate Borrower** (`1 to 5` SVG stars + reliability tags + review comment).
* **"Verified Trusted Lender" Badge:** Automatically grant and display the gold **Verified Trusted Lender** badge on user profiles and equipment listings when a lender maintains a rating of `4.8★` or higher with verified transactions.
* **Automatic Account Pause / Suspension on Low Ratings:**
  * If a Borrower or Lender receives consecutive low ratings causing their trust rating to drop below `3.0★`, automatically transition their account into a **Paused / Suspended** state.
  * When paused/suspended, display a prominent warning banner, disable new borrowing and lending actions, and provide an interactive **"Submit Appeal / Reset Trust Demo"** flow so evaluators can test both the locked state and account restoration.

### G. Lender Studio, 10% Commission & TigRent Premium (`₱99/month`)
* **List New Equipment:** Allow lenders to publish new items with title, category, daily price (`₱/day`), security deposit, and UST pickup building, immediately adding the item to the live marketplace.
* **Revenue & Commission Ledger:** Show Gross Earnings, the **10% TigRent Platform Commission** deducted per successful rental, and Net Payout to GCash/Maya.
* **TigRent Premium (`₱99/month`):** Include an interactive upgrade toggle for lenders that unlocks Featured Listing placement, demand analytics, bulk equipment management for student organizations, and promotional discount badges.

---

## 3. Deliverable Format
Provide the complete, self-contained application in a single `index.html` file containing semantic HTML5, modern CSS3 (with Tailwind CSS utilities and custom Apple glass/animation rules), and clean vanilla JavaScript pre-loaded with realistic UST student profiles, equipment listings, active rentals, and pending extension requests so every feature is immediately testable.