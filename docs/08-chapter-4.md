# **Chapter IV: Product Design**

This chapter presents the Software Architecture & Design proposal for HipoSim, translating the User Stories and the Impact Map identified in Chapter III into concrete design decisions: the visual style system shared across all products, the information architecture that organizes content for each role, the UX/UI design for the Landing Page, the Web Application and the Mobile Application, and the technical design of the solution — Domain-Driven Software Architecture, Object-Oriented Design and Database Design.

## **4.1. Style Guidelines**

This section establishes a shared, centralized visual language for all HipoSim products — the Landing Page, the Web Application and the Native Mobile Application — so that assets, fonts, colors and tone remain consistent regardless of the platform a user or visitor is on. As mandated by the course's technical constraints, the team adopts **Material Design** as the base design system, adapted through **PrimeVue** for the web, and translated natively for iOS and Android on mobile.

### **4.1.1. General Style Guidelines**

**Branding.** The product name, HipoSim, communicates its two defining traits directly: "Hipo-" (hipotecario) states the domain, and "-Sim" states the nature of the tool — a simulator, not a bank. The logo and wordmark (see Chapter II, competitive analysis) avoid any visual association with a specific financial institution, reinforcing the product's core value proposition: independence from any single bank.

**Tone of communication.** Because HipoSim handles a high-stakes financial decision for someone with little to no prior credit experience, the tone is deliberately calibrated to build trust without intimidating the user:

| Dimension | Position adopted | Rationale |
|---|---|---|
| Fun ↔ Serious | Leans **Serious**, with approachable language | Mortgage terms (TCEA, grace period, amortization) are inherently technical; the tone must not trivialize a 15-20 year financial commitment. |
| Formal ↔ Casual | **Semi-formal** | Formal enough to convey credibility on financial figures, casual enough to avoid sounding like bank legal copy. |
| Respectful ↔ Irreverent | **Respectful** | The user is making a first-time, high-anxiety decision; no room for irony or sarcasm in copy. |
| Enthusiastic ↔ Serene | Leans **Serene** | The product's differentiator is transparency and calm clarity, not excitement or urgency-driven persuasion. |

**Typography.** The type scale follows Material Design 3 type tokens (Display, Headline, Title, Body, Label), using a single humanist sans-serif family (Roboto, the default typeface bundled with PrimeVue's Material theme) across all products, to keep numeric data (interest rates, currency amounts, TCEA percentages) legible at small sizes on mobile.

**Colors.** The palette separates brand color from semantic/status color, in line with Material Design color roles:

| Role | Usage |
|---|---|
| Primary | Navigation, primary CTAs ("Simular ahora", "Guardar simulación") |
| Secondary / Accent | Highlights inside the results view (e.g., TCEA callout) |
| Success | Confirmation states (benefit applies, simulation saved) |
| Warning | Non-blocking alerts (e.g., TCEA above a configured threshold, per the in-app notification defined in Chapter I) |
| Error | Form validation errors |
| Neutral / Surface | Backgrounds, cards, dividers |

Color combinations for text and interactive elements must meet **WCAG AA contrast ratios**, in line with the Accessibility (a11y) requirement described later in this chapter.

**Spacing.** An 8px baseline grid (Material Design standard) is used for all spacing, padding and component sizing decisions, to keep alignment consistent between the Figma design files and the PrimeVue/native implementations.

### **4.1.2. Web Style Guidelines**

The Web Application and the Landing Page follow **Responsive Web Design**, targeting three breakpoints: mobile (< 768px), tablet (768px-1024px) and desktop (> 1024px), on a 12-column fluid grid.

UI components for the Web Application are sourced from **PrimeVue** (Material theme) to guarantee consistency and reduce custom CSS: stepper/wizard components for the multi-step simulation form (client data → property data → credit parameters → results), data tables for the amortization schedule and the simulation history, cards for scenario comparison, and toast/banner components for the in-app threshold notification.

The Landing Page, built with plain HTML5/CSS3/JavaScript, mirrors the same color, type and spacing tokens as the Web Application (documented as shared CSS custom properties) even though it does not depend on PrimeVue, so that a Visitante does not perceive a visual discontinuity when moving from the Landing Page into the registered product.

### **4.1.3. Mobile Style Guidelines**

Both mobile platforms share the same brand tokens (color, type scale ratios, iconography) defined in 4.1.1, but each adapts its navigation and interaction patterns to the conventions its users already expect from native apps.

#### **4.1.3.1. iOS Mobile Style Guidelines**

On iOS, layout follows Apple's Human Interface Guidelines for structure and gesture conventions (bottom tab bar for primary navigation, safe-area-aware layouts, swipe-back navigation, native modal sheets for the simulation wizard steps), while visual styling (color, elevation, type) stays aligned with the Material-based system defined for the product, not the default iOS visual style — consistent with the single Design System applied across web and mobile.

#### **4.1.3.2. Android Mobile Style Guidelines**

On Android, both structure and visual styling follow Material Design guidelines natively: bottom navigation bar, a Floating Action Button (FAB) for the primary "New simulation" action from the history screen, and Material elevation/shadow conventions for cards (scenario comparison) and the results sheet.
## **4.2. Information Architecture**
### **4.2.1. Organization Systems**
### **4.2.2. Labeling Systems**
### **4.2.3. SEO Tags and Meta Tag**
### **4.2.4. Searching Systems**
### **4.2.5. Navigation Systems**
## **4.3. Landing Page UI Design**
### **4.3.1. Landing Page Wireframe**
### **4.3.2. Landing Page Mock-up**
## **4.4. Mobile Applications UX/UI Design**
### **4.4.1. Mobile Applications Wireframes**
### **4.4.2. Mobile Applications Wireflow Diagrams**
### **4.4.3. Mobile Applications Mock-ups**
### **4.4.4. Mobile Applications User Flow Diagrams**
## **4.5. Mobile Applications Prototyping**
### **4.5.1. Android Mobile Applications Prototyping**
### **4.5.2. iOS Mobile Applications Prototyping**
## **4.6. Web Applications UX/UI Design**
### **4.6.1. Web Applications Wireframes**
### **4.6.2. Web Applications Wireflow Diagrams**
### **4.6.3. Web Applications Mock-ups**
### **4.6.4. Web Applications User Flow Diagrams**
## **4.7. Web Applications Prototyping**
## **4.8. Domain-Driven Software Architecture**
### **4.8.1. Software Architecture Context Diagram**
### **4.8.2. Software Architecture Container Diagrams**
### **4.8.3. Software Architecture Components Diagrams**
## **4.9. Software Object-Oriented Design**
### **4.9.1. Class Diagrams**
### **4.9.2. Class Dictionary**
## **4.10. Database Design**
### **4.10.1. Relational/Non-Relational Database Diagram**
