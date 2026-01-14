# ASTRA VISUAL DESIGN SYSTEM
## Brand Guidelines, Design Specifications & Implementation

---

## 📋 TABLE OF CONTENTS

1. **Brand Identity Overview**
2. **Logo System (Reference-Based)**
3. **Color Palette & Specifications**
4. **Typography System**
5. **Component Design Library**
6. **Layout & Spacing System**
7. **UI Pattern Components**
8. **Dark Mode Implementation**
9. **Animation & Motion**
10. **Design Tokens (CSS Variables)**

---

# PART 1: BRAND IDENTITY

## 🎨 ASTRA BRAND ESSENCE

```
CORE VALUES:
├─ Modern: Sleek, contemporary, cutting-edge
├─ Intelligent: AI-powered, sophisticated
├─ Accessible: Clean, intuitive, welcoming
├─ Dynamic: Motion, energy, progress
└─ Trustworthy: Secure, reliable, professional

VISUAL PERSONALITY:
├─ Modern & minimalist (not corporate)
├─ Tech-forward but approachable
├─ Energetic but balanced
├─ Professional yet innovative
└─ Sophisticated with warmth
```

---

# PART 2: LOGO SYSTEM (REFERENCE-BASED)

## 🌟 PRIMARY LOGO DESIGN

### **Logo Structure Analysis**

```
ASTRA LOGO COMPOSITION:

Main Element: Geometric "A" with orbital ring
├─ Letter "A": Teal gradient geometric form
├─ Orbital Ring: Flowing curved path around A
├─ Color: Primary Teal (#208A91)
├─ Secondary: Lighter Teal accent (#32B8C6)
└─ Style: Modern, minimalist, tech-forward

Visual Characteristics:
├─ Clean geometric construction
├─ Subtle gradient for depth
├─ Flowing orbital motion implied by ring
├─ Balanced, symmetrical composition
├─ Stands alone at any size (16px to 1024px)
└─ Works in single color or gradient
```

### **Logo Variations**

```
1. PRIMARY LOGO (Full Color)
   ├─ Geometry: "A" + orbital ring
   ├─ Colors: Teal gradient (#208A91 to #32B8C6)
   ├─ Best Use: App icons, headers, main branding
   ├─ Minimum Size: 32px
   └─ Files: SVG, PNG (multiple sizes), PDF, EPS

2. MONOCHROME (Black)
   ├─ Geometry: Same as primary
   ├─ Color: Black #0F1419
   ├─ Best Use: Print, embroidery, screen print
   ├─ Minimum Size: 32px
   └─ Files: SVG, PDF, EPS

3. MONOCHROME (White)
   ├─ Geometry: Same as primary
   ├─ Color: White #FFFFFF
   ├─ Best Use: Dark backgrounds, dark mode
   ├─ Minimum Size: 32px (on dark background)
   └─ Files: SVG, PNG, PDF

4. MARK ONLY (Icon)
   ├─ Geometry: Orbital ring element
   ├─ Without: Letter "A" (if at very small sizes)
   ├─ Best Use: Favicon, avatar, tight layouts
   ├─ Minimum Size: 16px
   └─ Files: SVG, PNG

5. WITH WORDMARK
   ├─ Logo: "A" + ring (left)
   ├─ Text: "ASTRA" (right)
   ├─ Gap: 12-16px minimum
   ├─ Alignment: Center baseline
   └─ Use: Headers, social profiles, business cards

6. STACKED VERSION
   ├─ Logo: "A" + ring (top)
   ├─ Text: "ASTRA" (bottom)
   ├─ Gap: 10-12px
   ├─ Alignment: Center
   └─ Use: Vertical layouts, badges, signatures
```

### **Logo Protection Zone**

```
CLEAR SPACE:
├─ Minimum clear space: Half the logo height
├─ No other elements within this zone
├─ Applies on all sides
└─ Maintains logo breathing room

MINIMUM SIZE:
├─ Digital: 32px width (favicon: 16px minimum)
├─ Print: 0.5 inches (12.7mm)
├─ Mobile: 44px for tap targets
└─ Never smaller than these dimensions

COLOR USAGE:
├─ Color logo (preferred): Full teal gradient
├─ Dark backgrounds: White version
├─ Light backgrounds: Teal or black
├─ Avoid: Light teal on white
└─ Never: Changed colors or distorted geometry
```

---

# PART 3: COLOR PALETTE

## 🎨 PRIMARY COLORS

```
PRIMARY TEAL (Brand Color):
├─ Name: ASTRA Teal
├─ Hex: #208A91
├─ RGB: 32, 138, 145
├─ HSL: 175°, 63%, 35%
├─ CMYK: 78, 5, 17, 43
├─ Usage: Logo, primary buttons, focus states, brand elements
└─ Psychology: Trust, intelligence, innovation

LIGHT TEAL (Hover/Accent):
├─ Hex: #32B8C6
├─ RGB: 50, 184, 198
├─ HSL: 176°, 54%, 49%
├─ Usage: Hover states, accents, secondary highlights
└─ Creates: Dynamic interaction feedback

DARK TEAL (Pressed/Active):
├─ Hex: #0D6B75
├─ RGB: 13, 107, 117
├─ HSL: 177°, 80%, 25%
├─ Usage: Pressed states, active tabs, emphasis
└─ Creates: Clear interaction hierarchy
```

## ⚪ NEUTRAL COLORS

```
WHITE (Pure):
├─ Hex: #FFFFFF
├─ RGB: 255, 255, 255
├─ Usage: Backgrounds, text on dark, cards

OFF-WHITE (Warm):
├─ Hex: #FAFAF9
├─ RGB: 250, 250, 249
├─ Usage: Subtle background variation, card backgrounds

LIGHT GRAY (UI):
├─ Hex: #F5F5F5
├─ RGB: 245, 245, 245
├─ Usage: Hover states, disabled backgrounds

GRAY (Borders):
├─ Hex: #E0E0E0
├─ RGB: 224, 224, 224
├─ Usage: Dividers, borders, subtle separation

DARK GRAY (Labels):
├─ Hex: #757575
├─ RGB: 117, 117, 117
├─ Usage: Secondary text, labels, metadata

CHARCOAL (Text):
├─ Hex: #0F1419
├─ RGB: 15, 20, 25
├─ Usage: Primary text, headings
└─ Contrast: 16:1 on white (WCAG AAA)

NEAR-BLACK (Dark Mode):
├─ Hex: #1A1A1A
├─ RGB: 26, 26, 26
├─ Usage: Dark mode backgrounds

BLACK (Very Dark):
├─ Hex: #000000
├─ RGB: 0, 0, 0
├─ Usage: Maximum contrast situations
```

## 🎨 STATUS COLORS

```
SUCCESS (Green):
├─ Hex: #4CAF50
├─ RGB: 76, 175, 80
├─ Usage: Success messages, positive states
└─ Contrast: 4.5:1 on white

ERROR (Red):
├─ Hex: #FF5459
├─ RGB: 255, 84, 89
├─ Usage: Error messages, destructive actions
└─ Contrast: 4.5:1 on white

WARNING (Orange):
├─ Hex: #E68159
├─ RGB: 230, 129, 89
├─ Usage: Warning messages, cautions
└─ Contrast: 4.5:1 on white

INFO (Blue):
├─ Hex: #2196F3
├─ RGB: 33, 150, 243
├─ Usage: Informational messages, help text
└─ Contrast: 4.5:1 on white
```

## 🌈 GRADIENT SPECIFICATIONS

```
PRIMARY GRADIENT (Teal):
├─ Direction: 135° (diagonal top-left to bottom-right)
├─ Start: #208A91 (Primary Teal)
├─ End: #32B8C6 (Light Teal)
├─ Usage: Logo backgrounds, button gradients, hero sections
└─ Effect: Modern, energetic

SECONDARY GRADIENT (Subtle):
├─ Direction: 90° (vertical)
├─ Start: #F5F5F5 (Light Gray)
├─ End: #FFFFFF (White)
├─ Usage: Card backgrounds, subtle depth
└─ Effect: Clean, minimalist

DARK GRADIENT (Night Mode):
├─ Direction: 45°
├─ Start: #1A1A1A
├─ End: #2D2D2D
├─ Usage: Dark mode backgrounds
└─ Effect: Sophisticated, easy on eyes
```

---

# PART 4: TYPOGRAPHY SYSTEM

## 📝 FONT FAMILIES

```
PRIMARY FONT (Headings & UI):
Name: Inter / System Stack
├─ Font Files: Inter-Regular, Inter-Medium, Inter-Bold
├─ Fallback: -apple-system, BlinkMacSystemFont, "Segoe UI"
├─ Weights: 400 (Normal), 500 (Medium), 600 (Bold), 700 (Extra Bold)
├─ Usage: Headings, buttons, navigation, labels
└─ Character: Modern, clean, highly legible

SECONDARY FONT (Body Text):
Name: Inter / System Stack
├─ Font Files: Inter-Regular, Inter-Medium
├─ Weights: 400 (Normal), 500 (Medium)
├─ Usage: Body paragraphs, descriptions, long-form text
└─ Character: Highly readable, excellent on-screen

MONOSPACE FONT (Code):
Name: JetBrains Mono / Courier New
├─ Font Files: JetBrainsMono-Regular, JetBrainsMono-Medium
├─ Fallback: Monaco, Menlo, Courier New
├─ Weights: 400, 500
├─ Usage: Code blocks, technical snippets
└─ Character: Professional, consistent-width
```

## 📐 TYPE SCALE

```
H1 (Page Title):
├─ Size: 48px / 3rem
├─ Weight: 700 (Bold)
├─ Line Height: 1.2 (58px)
├─ Letter Spacing: -0.02em
├─ Margin: 0 0 24px 0
└─ Usage: Main page headings

H2 (Section Title):
├─ Size: 36px / 2.25rem
├─ Weight: 600 (Semibold)
├─ Line Height: 1.3 (47px)
├─ Letter Spacing: -0.01em
├─ Margin: 0 0 20px 0
└─ Usage: Section headings

H3 (Subsection):
├─ Size: 28px / 1.75rem
├─ Weight: 600 (Semibold)
├─ Line Height: 1.4 (39px)
├─ Letter Spacing: 0
├─ Margin: 0 0 16px 0
└─ Usage: Subsection titles

H4 (Minor Heading):
├─ Size: 24px / 1.5rem
├─ Weight: 600 (Semibold)
├─ Line Height: 1.4 (34px)
└─ Usage: Component titles, card headers

Body Large:
├─ Size: 18px / 1.125rem
├─ Weight: 400 (Normal)
├─ Line Height: 1.5 (27px)
├─ Letter Spacing: 0.5px
└─ Usage: Large body text, prominent descriptions

Body Normal (Default):
├─ Size: 16px / 1rem
├─ Weight: 400 (Normal)
├─ Line Height: 1.6 (26px)
├─ Letter Spacing: 0
└─ Usage: Standard body text, descriptions

Body Small:
├─ Size: 14px / 0.875rem
├─ Weight: 400 (Normal)
├─ Line Height: 1.6 (22px)
├─ Letter Spacing: 0
└─ Usage: Secondary text, metadata, labels

Caption:
├─ Size: 12px / 0.75rem
├─ Weight: 500 (Medium)
├─ Line Height: 1.5 (18px)
├─ Letter Spacing: 0.4px
├─ Color: Gray #757575
└─ Usage: Captions, timestamps, hints

Overline:
├─ Size: 11px / 0.7rem
├─ Weight: 600 (Semibold)
├─ Line Height: 1.5 (17px)
├─ Letter Spacing: 1.5px
├─ Text Transform: Uppercase
├─ Color: Gray #757575
└─ Usage: Category labels, section dividers
```

---

# PART 5: COMPONENT DESIGN

## 🔘 BUTTON COMPONENTS

```
PRIMARY BUTTON (Teal):
┌─────────────────────────────┐
│     Create Roadmap          │
└─────────────────────────────┘

Specifications:
├─ Background: #208A91 (Teal)
├─ Text: #FFFFFF (White)
├─ Size: 48px height (touch-friendly)
├─ Padding: 12px 24px
├─ Border Radius: 8px
├─ Font Size: 16px / Medium weight
├─ Cursor: Pointer
├─ Transition: All 150ms ease-out

States:
├─ Default: Background #208A91
├─ Hover: Background #32B8C6 (lighter)
├─ Active/Pressed: Background #0D6B75 (darker)
├─ Disabled: Opacity 50%, cursor not-allowed
├─ Focus: 2px solid #208A91 outline, 2px offset
└─ Loading: Spinner icon, button disabled

Usage:
├─ Primary actions
├─ Call-to-action buttons
├─ Form submission
└─ Next/Continue actions


SECONDARY BUTTON (Gray):
┌─────────────────────────────┐
│        Cancel               │
└─────────────────────────────┘

Specifications:
├─ Background: #F5F5F5 (Light Gray)
├─ Text: #0F1419 (Charcoal)
├─ Border: 1px solid #E0E0E0
├─ Size: 48px height
├─ Padding: 12px 24px
├─ Border Radius: 8px
├─ Font Size: 16px / Medium weight

States:
├─ Default: #F5F5F5 background
├─ Hover: #E0E0E0 background
├─ Active: #D0D0D0 background
├─ Disabled: Opacity 50%
└─ Focus: 2px solid outline

Usage:
├─ Secondary actions
├─ Cancel buttons
├─ Alternative options
└─ Less important actions


OUTLINE BUTTON (Transparent):
┌─────────────────────────────┐
│       Learn More            │
└─────────────────────────────┘

Specifications:
├─ Background: Transparent
├─ Text: #208A91 (Teal)
├─ Border: 2px solid #208A91
├─ Size: 48px height
├─ Padding: 12px 24px
├─ Border Radius: 8px

States:
├─ Default: Transparent, teal border
├─ Hover: #F5F5F5 background
├─ Active: #E0E0E0 background
└─ Focus: Double border effect

Usage:
├─ Tertiary actions
├─ Links styled as buttons
└─ Less prominent calls-to-action


DESTRUCTIVE BUTTON (Red):
┌─────────────────────────────┐
│         Delete              │
└─────────────────────────────┘

Specifications:
├─ Background: #FF5459 (Red)
├─ Text: #FFFFFF (White)
├─ Size: 48px height
├─ Padding: 12px 24px
├─ Border Radius: 8px

States:
├─ Default: #FF5459
├─ Hover: #E63B42
├─ Active: #CC1F25
└─ Disabled: Opacity 50%

Usage:
├─ Dangerous actions
├─ Delete/remove
├─ Destructive operations
└─ Requires confirmation before action
```

## 📝 FORM COMPONENTS

```
TEXT INPUT:
┌─────────────────────────────┐
│ Enter your email address    │
└─────────────────────────────┘

Specifications:
├─ Height: 48px
├─ Padding: 12px 16px
├─ Border: 1px solid #E0E0E0
├─ Border Radius: 8px
├─ Font Size: 16px
├─ Background: #FFFFFF
├─ Color: #0F1419

States:
├─ Default: Border #E0E0E0
├─ Focused: Border #208A91, shadow
├─ Error: Border #FF5459, error text
├─ Success: Border #4CAF50, checkmark
├─ Disabled: Background #F5F5F5, opacity 50%
└─ Placeholder: Color #999999, opacity 60%

Features:
├─ Clear icon on focus (if filled)
├─ Label above field
├─ Helper text below
├─ Error message in red
└─ Character counter (if applicable)


SELECT / DROPDOWN:
┌─────────────────────────────┐
│ Select Category          ▼  │
└─────────────────────────────┘

Specifications:
├─ Height: 48px
├─ Padding: 12px 16px
├─ Border: 1px solid #E0E0E0
├─ Border Radius: 8px
├─ Arrow Icon: Right-aligned

Dropdown Menu:
├─ Background: #FFFFFF
├─ Border: 1px solid #E0E0E0
├─ Item Height: 40px
├─ Item Padding: 12px 16px
├─ Hover: #F5F5F5 background
├─ Selected: Checkmark + teal highlight
└─ Scroll: If > 6 items

Options:
├─ Web Development
├─ Data Science
├─ Mobile Apps
├─ AI/ML
└─ Other


CHECKBOX:
☑ I agree to Terms of Service

Specifications:
├─ Size: 20px × 20px
├─ Border: 2px solid #E0E0E0
├─ Border Radius: 4px
├─ Background (checked): #208A91
├─ Checkmark: White

States:
├─ Unchecked: Gray border
├─ Checked: Teal background, white checkmark
├─ Hovered: Border #208A91
├─ Disabled: Opacity 50%
└─ Focus: 2px blue outline

Usage:
├─ Agreements/terms
├─ Multiple selections
├─ Feature toggles
└─ Opt-in options


RADIO BUTTON:
◉ Learner     ○ Educator

Specifications:
├─ Size: 20px × 20px circle
├─ Border: 2px solid #E0E0E0
├─ Selected: Teal border + teal dot

States:
├─ Default: Gray border
├─ Selected: Teal border, teal center dot
├─ Hovered: Darker border
├─ Disabled: Opacity 50%
└─ Focus: Outline ring

Usage:
├─ Single selection from group
├─ Exclusive options
├─ User role selection
└─ Plan selection
```

## 📍 CARD COMPONENT

```
┌──────────────────────────────┐
│  React Advanced Patterns     │
│  by @JohnDoe                 │
│                              │
│  Master React hooks and      │
│  performance optimization... │
│                              │
│  ⭐ 4.8 (128)  8 modules    │
│  4 weeks • Intermediate      │
│                              │
│  [Preview]  [Save]  [Share]  │
└──────────────────────────────┘

Specifications:
├─ Background: #FFFFFF (white) or #F5F5F5 (light)
├─ Border: 1px solid #E0E0E0
├─ Border Radius: 12px
├─ Padding: 20px
├─ Shadow: 0 1px 3px rgba(0,0,0,0.1)
├─ Transition: Shadow 150ms ease

States:
├─ Default: Subtle shadow
├─ Hover: Elevated shadow (0 4px 12px rgba)
├─ Active: #208A91 border
└─ Loading: Skeleton placeholder

Internal Layout:
├─ Title: 18px bold, #0F1419
├─ Subtitle: 14px medium, #757575
├─ Description: 14px normal, #424242, 2 lines
├─ Meta: 12px medium, #999999
├─ Actions: Button group, spaced
└─ Gap: 12px between sections

Responsive:
├─ Desktop: 300px width
├─ Tablet: Full width or 2 per row
└─ Mobile: Full width, stacked
```

---

# PART 6: LAYOUT & SPACING SYSTEM

## 📐 SPACING SCALE

```
SPACING VALUES (Based on 4px grid):

4px (xs):
├─ Use: Tight spacing, small gaps
├─ Example: Icon padding, tight groups
└─ CSS: gap: 4px;

8px (sm):
├─ Use: Small spacing, grouped elements
├─ Example: Button groups, form fields
└─ CSS: gap: 8px;

12px (base):
├─ Use: Standard spacing, most common
├─ Example: Component padding, text spacing
└─ CSS: gap: 12px;

16px (md):
├─ Use: Medium spacing, component separation
├─ Example: Card padding, section gaps
└─ CSS: gap: 16px;

20px (lg):
├─ Use: Large spacing, major sections
├─ Example: Page sections, large containers
└─ CSS: gap: 20px;

24px (xl):
├─ Use: Extra large spacing, clear separation
├─ Example: Page margins, major dividers
└─ CSS: gap: 24px;

32px (2xl):
├─ Use: Major section separation
├─ Example: Page sections, hero spacing
└─ CSS: gap: 32px;

48px (3xl):
├─ Use: Major page division
├─ Example: Full-page sections
└─ CSS: gap: 48px;

64px (4xl):
├─ Use: Large screen sections
├─ Example: Featured sections
└─ CSS: gap: 64px;
```

## 📏 BREAKPOINTS

```
Mobile (< 640px):
├─ Layout: Single column, full width
├─ Padding: 16px sides
├─ Font Sizes: Reduced slightly
├─ Components: Full width, stacked
└─ Navigation: Bottom or hamburger menu

Tablet (640px - 1024px):
├─ Layout: 2 columns possible
├─ Padding: 24px sides
├─ Components: 2 per row
├─ Cards: Medium size, readable
└─ Navigation: Visible sidebar or tabs

Desktop (1024px - 1280px):
├─ Layout: 3+ columns
├─ Padding: 32px sides
├─ Max Width: 1200px content
├─ Components: Multiple columns, organized
└─ Navigation: Permanent sidebar

Large Desktop (> 1280px):
├─ Layout: Full multi-column
├─ Padding: 48px+ sides
├─ Max Width: 1400px
├─ Whitespace: Generous spacing
└─ Typography: Optimal reading width
```

---

# PART 7: DARK MODE IMPLEMENTATION

## 🌙 DARK COLOR PALETTE

```
DARK BACKGROUNDS:
├─ Primary Dark: #0F1419 (Main background)
├─ Surface Dark: #1A1A1A (Cards/panels)
├─ Elevated Dark: #2D2D2D (Popovers/dialogs)
└─ Overlay Dark: rgba(0, 0, 0, 0.8)

DARK TEXT:
├─ Primary Text: #F5F5F5 (Main text)
├─ Secondary Text: #B0B0B0 (Muted text)
├─ Tertiary Text: #808080 (Metadata)
└─ Links: #32B8C6 (Light teal)

DARK BORDERS:
├─ Default Border: #333333
├─ Subtle Border: #1F1F1F
├─ Highlight Border: #208A91 (Teal focus)
└─ Error Border: #FF5459

DARK COMPONENTS:
├─ Button Primary: #208A91 (unchanged)
├─ Button Secondary: #2D2D2D (dark gray)
├─ Input Background: #1A1A1A
├─ Input Border: #333333
└─ Card Background: #1F1F1F
```

## 🔄 DARK MODE TOGGLE

```
TOGGLE LOCATION:
├─ Position: Top-right corner
├─ Icon: Sun (light mode) / Moon (dark mode)
├─ Size: 24px icon in 40px button
├─ Keyboard: Cmd+Shift+L (macOS), Ctrl+Shift+L (Windows)
└─ Persistence: Save to localStorage

IMPLEMENTATION:
├─ CSS Variable Swap: Change :root variables
├─ Smooth Transition: 150ms color transition
├─ No Flash: Apply on page load from storage
└─ System Preference: Default to system setting
```

---

# PART 8: ANIMATION & MOTION

## ⚡ ANIMATION PRINCIPLES

```
DURATION GUIDELINES:
├─ Instant: 0ms (no delay perception)
├─ Snappy: 100ms (UI feedback)
├─ Normal: 150-200ms (transitions)
├─ Moderate: 300-400ms (larger changes)
├─ Gentle: 500-800ms (subtle effects)
└─ Slow: 1000ms+ (entrance animations)

EASING FUNCTIONS:
├─ Instant: linear (no easing)
├─ UI Feedback: ease-out (quick response)
├─ Smooth Transitions: cubic-bezier(0.4, 0, 0.2, 1)
├─ Bouncy: cubic-bezier(0.68, -0.55, 0.265, 1.55)
└─ Slow Reveal: ease-in-out (symmetric)

EXAMPLES:

Button Hover (100ms):
transition: all 100ms ease-out;

Modal Entrance (300ms):
animation: slideUp 300ms ease-out;

Card Hover (150ms):
transform: translateY(-4px);
box-shadow: 0 8px 16px rgba(0,0,0,0.1);

Loading Spinner (2000ms):
@keyframes spin {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}
```

## 🎬 MICRO-INTERACTIONS

```
BUTTON CLICK FEEDBACK:
├─ Visual: Slight scale down (0.98)
├─ Duration: 100ms
├─ Easing: ease-out
├─ Effect: Tactile, responsive feel
└─ Code: transform: scale(0.98);

FORM ERROR SHAKE:
├─ Animation: Horizontal shake
├─ Distance: ±4px
├─ Duration: 300ms
├─ Timing: Twice per cycle
└─ Effect: Attention-grabbing

INPUT FOCUS GLOW:
├─ Effect: Subtle glow on focus
├─ Color: Teal #208A91
├─ Opacity: Gradually fade in
├─ Duration: 150ms
└─ Box-shadow: 0 0 0 3px rgba(32,138,145,0.2)

SUCCESS CHECKMARK:
├─ Animation: Scale + fade
├─ From: Scale 0, opacity 0
├─ To: Scale 1, opacity 1
├─ Duration: 400ms
└─ Easing: elastic (bounce effect)

LOADING PULSE:
├─ Animation: Opacity pulse
├─ From: opacity 0.5
├─ To: opacity 1
├─ Duration: 1.5s
├─ Repeat: infinite
└─ Easing: ease-in-out
```

---

# PART 9: DESIGN TOKENS (CSS VARIABLES)

## 🎨 CSS CUSTOM PROPERTIES

```css
:root {
  /* Colors - Primary */
  --color-primary: #208A91;
  --color-primary-light: #32B8C6;
  --color-primary-dark: #0D6B75;
  
  /* Colors - Neutral */
  --color-white: #FFFFFF;
  --color-off-white: #FAFAF9;
  --color-light-gray: #F5F5F5;
  --color-gray: #E0E0E0;
  --color-dark-gray: #757575;
  --color-charcoal: #0F1419;
  --color-black: #000000;
  
  /* Colors - Status */
  --color-success: #4CAF50;
  --color-error: #FF5459;
  --color-warning: #E68159;
  --color-info: #2196F3;
  
  /* Typography */
  --font-family-base: Inter, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
  --font-family-mono: "JetBrains Mono", Monaco, Courier New, monospace;
  
  --font-size-h1: 48px;
  --font-size-h2: 36px;
  --font-size-h3: 28px;
  --font-size-h4: 24px;
  --font-size-body-large: 18px;
  --font-size-body: 16px;
  --font-size-body-small: 14px;
  --font-size-caption: 12px;
  
  --font-weight-normal: 400;
  --font-weight-medium: 500;
  --font-weight-semibold: 600;
  --font-weight-bold: 700;
  
  --line-height-tight: 1.2;
  --line-height-normal: 1.5;
  --line-height-relaxed: 1.8;
  
  /* Spacing */
  --space-xs: 4px;
  --space-sm: 8px;
  --space-base: 12px;
  --space-md: 16px;
  --space-lg: 20px;
  --space-xl: 24px;
  --space-2xl: 32px;
  --space-3xl: 48px;
  
  /* Border Radius */
  --radius-sm: 4px;
  --radius-md: 8px;
  --radius-lg: 12px;
  --radius-full: 9999px;
  
  /* Shadows */
  --shadow-sm: 0 1px 3px rgba(0, 0, 0, 0.1);
  --shadow-md: 0 4px 12px rgba(0, 0, 0, 0.1);
  --shadow-lg: 0 8px 24px rgba(0, 0, 0, 0.12);
  --shadow-xl: 0 12px 32px rgba(0, 0, 0, 0.15);
  
  /* Transitions */
  --duration-fast: 100ms;
  --duration-normal: 150ms;
  --duration-slow: 300ms;
  --easing-standard: cubic-bezier(0.4, 0, 0.2, 1);
}

/* Dark Mode */
@media (prefers-color-scheme: dark) {
  :root {
    --color-white: #1A1A1A;
    --color-off-white: #1F1F1F;
    --color-light-gray: #2D2D2D;
    --color-charcoal: #F5F5F5;
    --color-black: #FFFFFF;
  }
}
```

---

# PART 10: IMPLEMENTATION GUIDE

## 🚀 HOW TO USE THESE GUIDELINES

### **For Designers (Figma/Adobe XD):**

```
1. SETUP:
   ├─ Create design components library
   ├─ Add color styles (primary, neutral, status)
   ├─ Create typography styles (H1-H6, body variants)
   ├─ Add spacing tokens to grid
   └─ Set up component library in Figma

2. DESIGN WORKFLOW:
   ├─ Start with grid (8px base)
   ├─ Use color palette only
   ├─ Apply typography styles
   ├─ Use components, not custom designs
   └─ Export for development

3. FILE ORGANIZATION:
   ├─ Pages: Colors, Typography, Components, Patterns, Exports
   ├─ Components: Buttons, Forms, Cards, Modals, etc.
   ├─ Variants: Default, Hover, Active, Disabled, Loading
   └─ Symbols: Reusable elements for consistency
```

### **For Developers (HTML/CSS):**

```
1. SETUP:
   ├─ Import CSS variables file
   ├─ Set up utility classes
   ├─ Create component classes
   └─ Configure build tooling

2. COMPONENT STRUCTURE:
   <button class="btn btn--primary">
     Create Roadmap
   </button>

3. STYLING APPROACH:
   ├─ Use CSS variables for colors
   ├─ Use utility classes for spacing
   ├─ Combine for consistency
   └─ Maintain component variants

4. DARK MODE:
   ├─ Add data-theme="dark" attribute
   ├─ CSS handles variable swap
   ├─ No JavaScript needed for styles
   └─ Save preference to localStorage
```

---

## ✅ QUALITY CHECKLIST

```
BEFORE LAUNCH:
☐ Logo exported in all formats (SVG, PNG, PDF, EPS)
☐ Color palette verified for accessibility (4.5:1 contrast minimum)
☐ Typography tested across all devices
☐ Components implemented in code
☐ Dark mode tested thoroughly
☐ Animations perform smoothly (60fps)
☐ Responsive design tested (mobile, tablet, desktop)
☐ Accessibility audit complete (WCAG AA)
☐ Design system documented
☐ Team trained on guidelines
```

---

**This design system is ready for implementation across all ASTRA products. Use these guidelines consistently to maintain a cohesive, professional brand experience.**

