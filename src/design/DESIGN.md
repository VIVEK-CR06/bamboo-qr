# Design System Specification: The Molecular Pulse

## 1. Overview & Creative North Star
The Creative North Star for this design system is **"Organic Futurism."** 

We are moving away from the rigid, clinical grids of traditional e-commerce. Instead, we are treating the product detail page as a high-end digital editorial. The goal is to mirror the thermochromic nature of the product—fluid, reactive, and sophisticated. We achieve this through "Atmospheric Layering": using depth, soft glassmorphism, and a dark-mode-first approach to make the bamboo container feel like a piece of high-tech art. The layout must feel intentional and asymmetrical, focusing on large hero imagery that "breaks" the container boundaries to create a sense of scale and premium quality.

## 2. Colors & Tonal Logic
This system utilizes a reactive color palette that moves from the heat of activity to the coolness of rest.

*   **Thermochromic Core:** 
    *   **Cold (0°C):** `primary_container` (#880DAD) - Use for active highlights and "fresh" states.
    *   **Ambient (35°C):** `on_secondary` (#50145E) - Use for subtle depth and transitions.
    *   **Hot (70°C):** `surface_container_lowest` (#0E0E0E) - The base of the experience.
*   **The "No-Line" Rule:** We do not use 1px solid borders to separate sections. Structure must be defined through background shifts. For example, a `surface_container_low` section should sit directly against a `surface` background. The eye should perceive the boundary through the shift in value, not a stroke.
*   **Surface Hierarchy & Nesting:** Treat the UI as physical layers. 
    *   **Level 0 (Background):** `surface` (#131313)
    *   **Level 1 (Sections):** `surface_container_low` (#1C1B1B)
    *   **Level 2 (Cards):** `surface_container_high` (#2A2A2A)
*   **The Glass & Gradient Rule:** For floating elements (e.g., product quick-view, mini-carts), use **Glassmorphism**: `rgba(255, 255, 255, 0.05)` with a `20px` backdrop-blur. Apply a subtle gradient from `primary` to `primary_container` for CTAs to give them a "living" energy.

## 3. Typography: The Editorial Scale
We use a high-contrast pairing of **Manrope** for impact and **Inter** for utility.

*   **Display & Headlines (Manrope):** These should be bold and expressive. Use `display-lg` (3.5rem) for product names, tracking them slightly tighter (-2%) for a bespoke editorial feel.
*   **Body (Inter):** All body text (`body-md`, `body-lg`) must be set at **70% opacity** using the `on_surface_variant` token. This reduces visual noise and ensures the bold titles remain the focal point.
*   **Hierarchy:** 
    *   **Product Price:** `headline-lg` (Manrope) - Bold, unapologetic.
    *   **Description:** `body-lg` (Inter) - Generous line-height (1.6) for readability.
    *   **Labels:** `label-md` (Inter) - Uppercase with 0.05rem letter spacing for a technical, "futuristic" touch.

## 4. Elevation & Depth
Depth is achieved through **Tonal Layering** rather than traditional drop shadows.

*   **The Layering Principle:** To lift an element, move it up the surface scale. A `surface_container_highest` card on a `surface_dim` background provides all the "lift" needed.
*   **Ambient Shadows:** Where a floating effect is vital (like a pill-toggle), use an extra-diffused shadow: `box-shadow: 0 20px 40px rgba(0, 0, 0, 0.4)`. Never use pure black for shadows on colored surfaces; use a tinted version of the background.
*   **The "Ghost Border" Fallback:** If accessibility requires a boundary, use the `outline_variant` token at **15% opacity**. This creates a "glint" on the edge of the glass rather than a heavy container wall.
*   **Glow States:** Active selection cards should utilize a "Glowing Border." This is achieved with a 1px inner border using `primary` (#F0B0FF) and an outer `box-shadow` of 0 0 15px `primary_container` at 30% opacity.

## 5. Components

### Buttons & Toggles
*   **Primary CTA:** Pill-shaped (`rounded-full`). Background: `primary` (#F0B0FF), Text: `on_primary` (#54006D). No border.
*   **Toggle Buttons:** Pill-shaped containers using `surface_container_highest`. The active "pill" inside should use the Glassmorphism spec with a `title-sm` font.

### Card-Style Selection (Size/Color)
*   **Base State:** `surface_container_low` with a `md` (1.5rem) corner radius. 
*   **Selected State:** Apply the **Glowing Border** (see Section 4) and a subtle scale animation (1.02x). 
*   **Content:** Forbid divider lines within cards. Use `1.5rem` vertical padding to separate price from title.

### Input Fields
*   **Style:** Minimalist. Only a bottom border (0.5px) using `outline_variant`.
*   **Focus State:** The bottom border transitions to `primary` (#F0B0FF) with a soft glow beneath the text.

### Tooltips & Overlays
*   **Styling:** Always use the Glassmorphism spec. 
*   **Animation:** Use a "Slide and Fade" entry—starting 10px below the target and fading in over 300ms with a `cubic-bezier(0.2, 0, 0, 1)` easing.

## 6. Do's and Don'ts

### Do:
*   **Use Asymmetry:** Allow product images to overlap between two background color sections.
*   **Embrace Negative Space:** Use the `xl` (3rem) spacing token between major content blocks to let the "Premium" feel breathe.
*   **Animate State Changes:** Use smooth transitions (200ms+) for hover states on all interactive elements.

### Don't:
*   **Don't use 100% white:** Use `on_surface` (#E5E2E1) for a softer, more high-end feel. Pure #FFFFFF is too harsh for this dark theme.
*   **Don't use Divider Lines:** If you feel the need to add a line, increase the vertical margin instead.
*   **Don't use Standard Grids:** Avoid perfectly centered, boxy layouts. Offset your text blocks to create a more dynamic, editorial flow.