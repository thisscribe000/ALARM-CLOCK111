# Design Guidelines

## Design Approach
**System-Based Design** using modern mobile-first principles, drawing inspiration from contemporary mobile app design patterns (iOS/Material Design hybrid). The application will prioritize clarity, touch-friendly interactions, and efficient information hierarchy.

## Core Design Elements

### Typography
- **Primary Font**: Inter (Google Fonts) - modern, highly legible at small sizes
- **Headings**: 
  - H1: 28px (1.75rem), font-weight 700
  - H2: 24px (1.5rem), font-weight 600
  - H3: 20px (1.25rem), font-weight 600
- **Body Text**: 16px (1rem), font-weight 400, line-height 1.6
- **Small Text**: 14px (0.875rem), font-weight 400

### Color System
- **Primary**: #36454F (charcoal blue-gray) - navigation, primary buttons, headers
- **Background**: #FFFFFF (white) - main card container
- **Page Background**: #F5F5F5 (light gray) - outer viewport
- **Text Primary**: #1F2937 (near black)
- **Text Secondary**: #6B7280 (medium gray)
- **Accent**: Derived from primary, lightened for hover states (#4A5A64)

### Layout System
**Tailwind Spacing Units**: Standardize on 2, 4, 6, 8, 12, 16, 24 (e.g., p-4, gap-6, mt-8)

**Mobile Container**:
- Max-width: 428px (iPhone 14 Pro Max width)
- Min-height: 100vh
- Background: White with subtle shadow (shadow-xl)
- Rounded corners: rounded-2xl (on larger screens)
- Padding: p-6 for main content areas

**Spacing Philosophy**:
- Consistent 16px (p-4) padding for content sections
- 24px (gap-6) between major components
- 32px (py-8) vertical section spacing

### Component Library

**Navigation**:
- Sticky header with primary color background
- Height: 64px (h-16)
- Logo/title left-aligned, icon buttons right-aligned
- Bottom tab bar for primary navigation (5 max items)

**Buttons**:
- Primary: Full primary color, white text, rounded-lg, h-12, font-medium
- Secondary: White background, primary border, primary text
- Minimum touch target: 44px height
- Full-width on mobile by default

**Cards**:
- White background, subtle border (border-gray-200)
- Rounded-xl, p-4 internal padding
- Shadow-sm for elevation
- 16px (gap-4) between cards in lists

**Forms**:
- Input fields: h-12, rounded-lg, border-gray-300
- Labels: text-sm, font-medium, mb-2
- Focus states: Primary color border (border-2)
- Error states: Red border with helper text below

**Icons**:
Use **Heroicons** (outline style for navigation, solid for actions)

### Animations
**Minimal & Purposeful**:
- Page transitions: Simple fade (200ms)
- Button press: Scale down slightly (transform scale-95)
- Loading states: Subtle pulse animation
- NO scroll-triggered animations or parallax effects

### Mobile-First Specifics

**Touch Targets**:
- Minimum 44px × 44px for all interactive elements
- Adequate spacing between clickable items (8px minimum)

**Scrolling**:
- Smooth scrolling enabled
- Sticky headers for context retention
- Pull-to-refresh pattern where applicable

**Content Density**:
- Single column layouts throughout
- Generous whitespace for readability
- List items: 72px minimum height for scanability

**Navigation Pattern**:
- Top navigation bar for context/actions
- Bottom tab bar for primary navigation (fixed position)
- No hamburger menus - prioritize visible navigation

## Images
**No hero image required** for this mobile-first application. Focus on:
- Avatar/profile images: Circular, 48px-64px diameter
- Card thumbnails: 16:9 or 1:1 aspect ratios, rounded-lg
- Icons as primary visual elements

This design creates a polished, native-feeling mobile web application with clear hierarchy, comfortable touch interactions, and professional aesthetics anchored by the sophisticated charcoal blue-gray primary color.