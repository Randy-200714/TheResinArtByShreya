# The Craft Next Door – Premium Website Implementation Plan

Build a production-quality, single-page website for a luxury handmade resin art & gifting studio. Pure HTML + CSS + vanilla JS (no framework). The site follows a soft-luxury aesthetic with warm neutrals, emotional copy, and conversion-optimized layout.

## Project Structure

```
c:\Users\randy.LENOVO\Desktop\Craftweb\
├── index.html              ← Single-page site
├── assets/
│   ├── css/
│   │   ├── variables.css   ← Design tokens (colors, fonts, spacing)
│   │   ├── layout.css      ← Grid, sections, responsive breakpoints
│   │   └── components.css  ← Buttons, cards, accordion, nav, form
│   ├── js/
│   │   └── main.js         ← Mobile menu, scroll animations, accordion, carousel
│   └── images/             ← Generated images (hero, products, gallery, etc.)
```

---

## Proposed Changes

### 1. Design System – CSS Custom Properties

#### [NEW] [variables.css](file:///c:/Users/randy.LENOVO/Desktop/Craftweb/assets/css/variables.css)
Define all tokens in `:root`: color palette (#C19A6B gold, #A3B18A sage, #F7F3F0 ivory, #EAE2DF blush, #3E3E3E charcoal), typography scale (Playfair Display headings, Montserrat body), 8px-based spacing, button/card/shadow presets, transition easings.

#### [NEW] [layout.css](file:///c:/Users/randy.LENOVO/Desktop/Craftweb/assets/css/layout.css)
Global resets, section padding, `.container` max-width, 12-col CSS Grid, responsive breakpoints (<480, 480-768, ≥1024). Mobile-first stack → multi-column. Full-bleed utility for hero/gallery.

#### [NEW] [components.css](file:///c:/Users/randy.LENOVO/Desktop/Craftweb/assets/css/components.css)
- **Header/Nav** – fixed, glass-morphism bg, logo left, CTA right, hamburger on mobile
- **Buttons** – `.btn-primary` (gold fill), `.btn-secondary` (outline), hover lift/glow
- **Cards** – `.product-card` rounded, shadow, hover scale
- **Testimonial** – italic serif quote, name/city
- **FAQ Accordion** – expand/collapse, rotate chevron
- **Process Steps** – icon + text, horizontal on desktop, stacked on mobile
- **Inquiry Form** – styled inputs, file upload, gold submit button
- **Footer** – social icons, links, copyright
- **Scroll Animations** – `.reveal` class for fade-up on intersection

---

### 2. Imagery – AI-Generated Assets

Generate 6-8 images using `generate_image`:
| Name | Description |
|------|-------------|
| `hero_bg` | Artisan hands pouring resin over dried flowers in warm natural light |
| `product_resin_frame` | Elegant resin frame with preserved wedding bouquet on mantel |
| `product_name_art` | Custom resin name sign in nursery setting |
| `product_memorial` | Memorial resin heart with dried flowers, soft light |
| `product_home_decor` | Styled vignette of resin coasters and small art pieces |
| `gallery_1` – `gallery_4` | Lifestyle shots: artisan at work, couple with keepsake, close-ups |
| `founder_portrait` | Female artisan (Stuti) sketching designs in bright studio |

---

### 3. HTML – Single Page (`index.html`)

#### [NEW] [index.html](file:///c:/Users/randy.LENOVO/Desktop/Craftweb/index.html)

Semantic HTML5 with 10 landmark sections, each wrapped in `<section>`:

| # | Section | Key Elements |
|---|---------|--------------|
| 1 | **Hero** | H1, subheadline, primary + secondary CTA, trust micro-copy |
| 2 | **Social Proof** | Instagram-style gallery, 3 testimonial cards, trust stats |
| 3 | **Products** | 4 category cards (resin frames, name art, memorial, decor) |
| 4 | **Brand Story** | Craftsmanship, founder photo, quality guarantees |
| 5 | **Gallery** | Masonry/grid of 6+ images, lightbox on click |
| 6 | **How It Works** | 4 steps with SVG icons, connecting line |
| 7 | **Trust** | Extended testimonials, guarantee badges, payment icons |
| 8 | **FAQ** | 9 accordion items |
| 9 | **Final CTA** | Emotional closing + WhatsApp button |
| 10 | **Contact + Footer** | Inquiry form, WhatsApp/IG links, copyright |

SEO: `<title>`, meta description, Open Graph tags, proper heading hierarchy (single H1), alt text on all images, ARIA labels on interactive elements.

---

### 4. JavaScript – Interactions

#### [NEW] [main.js](file:///c:/Users/randy.LENOVO/Desktop/Craftweb/assets/js/main.js)

- **Mobile menu** – hamburger toggle, close on link/backdrop click
- **Scroll reveal** – IntersectionObserver adds `.active` to `.reveal` elements  
- **FAQ accordion** – toggle `.open` class, ARIA expanded/collapsed
- **Image lightbox** – overlay with enlarged image on gallery click, ESC/backdrop close
- **Smooth scroll** – anchor links scroll smoothly
- **Sticky CTA bar** – mobile bottom bar appears after scrolling past hero

---

## Verification Plan

### Browser Testing (primary method)

1. **Start a local server** from the project root:
   ```
   npx -y serve c:\Users\randy.LENOVO\Desktop\Craftweb
   ```
2. **Desktop visual check** – open browser at `http://localhost:3000`, scroll through all 10 sections, verify:
   - Layout matches soft-luxury aesthetic (colors, fonts, spacing)
   - All generated images render
   - Scroll fade-in animations trigger correctly
   - Hover effects on buttons and cards work
3. **Mobile responsive check** – resize browser to 375px width, verify:
   - Hero stacks properly, text readable
   - Hamburger menu opens/closes
   - Bottom CTA bar visible
   - All sections stack single-column
4. **Interaction testing**:
   - Click FAQ items → accordion expands/collapses
   - Click gallery images → lightbox opens, ESC closes
   - Click WhatsApp CTA → opens `wa.me` link
   - Smooth scroll on nav links
5. **Accessibility spot-check** – tab through interactive elements, verify focus outlines and ARIA attributes

> [!NOTE]
> No automated test suite. This is a static marketing site; all verification is visual/interactive via browser.
