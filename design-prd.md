# Product Requirements Document (PRD): "Aura" Minimalist Blog Design System

## 1. Overview
This PRD outlines the **Aura** Design System, a unique, highly readable, and minimalist blog interface. It is synthesized by extracting the elegant breathability of traditional editorial layouts, the functional grid systems of modern SaaS platforms, and the bold, high-contrast visual hierarchy of digital agencies.

## 2. Core Design Principles
* **Editorial Elegance (Inspired by Chore):** Extensive whitespace, asymmetrical content flows, and sophisticated pairing of serif and sans-serif typography.
* **Functional Clarity (Inspired by Untitled UI):** Clean, utilitarian components like horizontal categorical navigation, prominent inline subscription modules, and distinct, interactive card states.
* **Brutalist Polish (Inspired by Dexfolio):** Oversized, bold headline typography, strict grid alignment, and vibrant accent colors used highly sparingly against a neutral canvas.

---

## 3. Design Tokens

### 3.1. Typography
The typography system relies on a high-contrast pairing to distinguish between UI/navigational elements and deep-reading content.

| Element | Font Family (Style) | Weight | Characteristics | Source Inspiration |
| :--- | :--- | :--- | :--- | :--- |
| **Hero Headlines (H1)** | Geometric Sans-Serif | Black/Extra Bold | Oversized, tight tracking, massive impact. | Dexfolio (Img 3) |
| **Article Headlines (H2-H3)** | Refined Serif | Regular/Medium | High-contrast, elegant, editorial feel. | Chore (Img 1) |
| **Body Copy** | Legible Sans-Serif | Regular | High line-height (1.6 - 1.8), optimal reading width (65-75 chars). | Dexfolio / Chore |
| **UI & Metadata** | Geometric Sans-Serif | Medium/Semi-Bold | Small, crisp, used for dates, tags, buttons. | Untitled UI (Img 2) |

### 3.2. Color Palette
A primarily monochromatic base to reduce cognitive load, punctuated by one vibrant accent.

* **Background Base:** `Soft Pearl` (`#FAFAFA`) – Reduces eye strain compared to pure white. (Chore)
* **Surface Base:** `Pure White` (`#FFFFFF`) – For elevated cards or floating elements. (Untitled UI)
* **Primary Text:** `Charcoal` (`#1A1A1A`) – High contrast without the harshness of pure black.
* **Secondary Text:** `Slate` (`#667085`) – For metadata, timestamps, and breadcrumbs.
* **Accent Color:** `Electric Indigo` (`#4F46E5`) – Used strictly for primary CTAs (e.g., "Send Comment", "Subscribe") and active states. (Dexfolio)

---

## 4. Core UI Components

### 4.1. Navigation & Discovery
* **Header:** Minimalist top bar featuring a logo on the left, primary navigation links in the center, and a dark, pill-shaped primary CTA button on the right.
* **Category Tabs:** Horizontal, scrollable text-link navigation (e.g., *View all, Design, Product, Development*) with a subtle active-state underline. (Untitled UI)
* **Inline Subscribe Bar:** A clean, horizontal input field coupled with a dark pill-shaped button ("Subscribe") placed below the main blog index headline. (Untitled UI)

### 4.2. Cards & Content Modules
* **Article Index Cards:** Large, edge-to-edge image cards. The bottom 25% of the card features a **frosted glass (backdrop-filter: blur)** overlay containing the author's name, date, and category in white text. (Untitled UI)
* **"You May Also Like" Cards:** Found at the bottom of articles. Distinctive, solid-color blocks (e.g., vibrant blue or deep navy) with white text, providing a visual break from the main white/grey reading experience. (Dexfolio)

### 4.3. Interactive Elements
* **Buttons:** Fully rounded (pill-shaped) for primary actions (black or accent color). Text links with right-pointing arrows (`Read post ↗`) for secondary discovery.
* **Avatars:** Small, circular, unbordered profile pictures placed adjacent to author names.

---

## 5. Page Layouts

### 5.1. Blog Index Page
* **Hero Section:** Left-aligned oversized Sans-Serif title ("Untitled Blog") with a smaller, secondary descriptive text block pushed to the right side of the grid.
* **Discovery:** Inline email subscription block immediately following the hero, followed by horizontal category tabs.
* **Grid:** A 2-column or 3-column masonry/grid layout utilizing the frosted-glass image cards.

### 5.2. Article Detail Page
* **Metadata:** Breadcrumb navigation at the very top (e.g., *Blog > News > Category*).
* **Hero Area (Split Design):**
    * *Left:* Massive Serif headline with small circular author avatar and timestamp below.
    * *Right:* Large featured illustration or photograph with subtle rounded corners.
* **Reading Layout (Asymmetrical):**
    * *Left Sidebar (Sticky):* A floating column containing minimalist social sharing icons (X, LinkedIn, Email) and an interactive "In this Article" Table of Contents. (Chore)
    * *Right/Center Column:* The main reading container. Narrow width for optimal reading.
* **Engagement Area:**
    * *Comments:* Nested, threaded comments section with a vibrant accent-colored "Send" button. (Dexfolio)
    * *Footer Discovery:* Large "You may also like" section utilizing the solid-color block cards to break the visual flow before the site footer.
