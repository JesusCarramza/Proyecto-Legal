# Estrategia del Sistema de Diseño: La Interfaz Soberana

## 1. Visión General y Estrella Polar Creativa
**Estrella Polar Creativa: "El Decreto Arquitectónico"**
Este sistema de diseño se aleja del aspecto de plantilla de "software como servicio" y se orienta hacia una experiencia editorial y arquitectónica. Está diseñado para sentirse tan estable como un juzgado de piedra y tan claro como un informe legal bien redactado. Logramos esto a través de la Asimetría Intencional y la Profundidad Tonal. Al usar márgenes amplios, diseños escalonados y tipografía de alto contraste, creamos una sensación de "El Curador Digital", un sistema que no solo almacena datos, sino que los presenta con autoridad y calma.

El objetivo es proporcionar un entorno de "Baja Carga Cognitiva" para los ciudadanos, mientras se mantiene un "Espacio de Trabajo de Alta Eficiencia" para los funcionarios judiciales. Rompemos la cuadrícula permitiendo que la tipografía de exhibición (display) se desborde hacia los márgenes y usando superficies en capas para definir la jerarquía sin necesidad de una sola línea de 1px.

---

## 2. Colores y Filosofía de Superficies
La paleta está arraigada en los azules profundos `primary` (#002045) y `tertiary` (#182033) para infundir respeto, equilibrados por una escala de grises sofisticada para mantener la neutralidad.

### The "No-Line" Rule
Standard UI relies on borders to separate content. **This design system prohibits 1px solid borders for sectioning.** Boundaries are defined solely through background color shifts.
*   **Action:** Place a `surface_container_lowest` (#ffffff) card against a `surface_container_low` (#f2f4f6) background. The shift in hex code is the divider.

### Surface Hierarchy & Nesting
Treat the UI as a series of physical layers. 
*   **Base Layer:** `surface` (#f7f9fb) – The canvas.
*   **Secondary Sectioning:** `surface_container` (#eceef0) – Use for sidebars or secondary content areas.
*   **Active Workspaces:** `surface_container_lowest` (#ffffff) – Use for the primary document or form the user is focusing on.
*   **Nesting:** When a form exists inside a container, use `surface_container_high` (#e6e8ea) for the input area to create an "etched" look rather than a bordered box.

### The "Glass & Gradient" Rule
To avoid a flat, "cheap" feel, use Glassmorphism for floating UI (like the AI assistant). 
*   **AI Assistant Bubble:** Use `surface_container_low` at 80% opacity with a `backdrop-blur-md`.
*   **Signature Gradients:** For primary CTAs, use a subtle linear gradient from `primary` (#002045) to `primary_container` (#1a365d) at a 135-degree angle. This adds "soul" and depth to critical actions.

---

## 3. Typography: The Editorial Voice
We use a dual-sans-serif approach to balance modern authority with extreme legibility.

*   **Display & Headlines (Manrope):** Used for case titles and major section headers. The wider aperture of Manrope feels modern and transparent. Use `headline-lg` (2rem) for case names to provide an "editorial" feel.
*   **Body & Labels (Inter):** Inter is used for all functional data. Its tall x-height ensures that complex legal text remains readable at `body-sm` (0.75rem).
*   **The Power Scale:** Use `display-md` (2.75rem) for empty states or landing hero text to create high-contrast, high-end visual interest.

---

## 4. Elevation & Depth
Depth is a functional tool, not a decoration.

*   **Tonal Layering:** Instead of shadows, stack `surface_container_low` on `surface`. This creates "soft lift."
*   **Ambient Shadows:** For "floating" elements like modals or the AI assistant, use a shadow with a `40px` blur and `4%` opacity, using the `on_surface` (#191c1e) color as the shadow base. It should look like a soft glow, not a dark drop.
*   **The Ghost Border:** If a separator is required for accessibility (e.g., high-contrast mode), use `outline_variant` at **10% opacity**. It should be felt, not seen.

---

## 5. Components & Interaction

### Structured Forms
*   **Inputs:** Do not use four-sided borders. Use a `surface_container_highest` background with a 2px `primary` bottom-border that activates on `:focus`.
*   **Layout:** Group related fields on `surface_container_low` "islands" to reduce visual noise.

### Data Tables (The Judicial Ledger)
*   **No Dividers:** Forbid horizontal lines. Use alternating row colors: `surface_container_lowest` and `surface_container`.
*   **Typography:** Header labels must use `label-sm` in `on_surface_variant` with 0.05em letter spacing for an "official" look.

### Conversational UI (The Assistant)
*   **Bubble Style:** User messages use `primary`. Assistant messages use `secondary_container` with a `backdrop-blur`.
*   **Asymmetry:** Assistant bubbles should be slightly wider and use a larger `xl` (0.75rem) border radius to distinguish from the rigid `md` (0.375rem) radius used for formal data.

### Status Indicators
*   **Admitted:** `primary_container` text on `primary_fixed` background.
*   **Pending:** `secondary` text on `secondary_container` background.
*   **Dismissed:** `on_error_container` text on `error_container` background.
*   **Style:** Use a pill shape (`full` radius) with `label-md` bold text.

### Buttons
*   **Primary:** Gradient of `primary` to `primary_container`. White text. `md` roundedness.
*   **Tertiary (Ghost):** No background or border. `on_surface` text with an underline that appears only on hover.

---

## 6. Do's and Don'ts

### Do
*   **DO** use whitespace (Scale `12` to `20`) to separate major judicial sections.
*   **DO** use `surface_dim` for "read-only" or "archived" case files to visually communicate finality.
*   **DO** align text-heavy legal documents to a maximum width of `65ch` (characters) for optimal reading.

### Don't
*   **DON'T** use 1px black or gray borders. This is the fastest way to make the system look "cheap."
*   **DON'T** use bright, saturated colors for anything other than status indicators. The system must feel "sober."
*   **DON'T** use standard shadows. If a component feels "flat," increase the background contrast between it and its parent container instead of adding a shadow.

---

## 7. TailwindCSS Configuration Snippet