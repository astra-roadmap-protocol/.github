# ASTRA USER FLOW PAGES & UX PATTERNS
## Comprehensive Implementation Guide for Core User Journeys

---

## 📋 TABLE OF CONTENTS

1. **Flow Pages Selection**
2. **First-Time User Experience (FTUE)**
3. **Authentication Flows**
4. **Core User Journeys**
5. **UX Pattern Implementations**
6. **Page State Patterns**
7. **UI Component Specifications**
8. **Accessibility Guidelines**

---

# PART 1: SELECTED FLOW PAGES FOR ASTRA

## 🎯 PRIORITY FLOWS (MVP - Launch Phase)

### **Tier 1: Critical (Required for Launch)**

```
AUTHENTICATION & ONBOARDING:
├─ Signing Up & Onboarding (Priority: CRITICAL)
├─ Logging In (Priority: CRITICAL)
├─ Exploring Tutorial (Priority: HIGH)
├─ Account Creation & Verification (Priority: CRITICAL)
└─ Resetting Password (Priority: HIGH)

CORE PRODUCT:
├─ Adding & Creating (Roadmaps) (Priority: CRITICAL)
├─ Editing (Roadmaps) (Priority: CRITICAL)
├─ Exploring/Browsing (Roadmaps) (Priority: HIGH)
├─ AI Assisting (AI-powered features) (Priority: HIGH)
├─ Filtering & Sorting (Discovery) (Priority: HIGH)
└─ Searching (Finding content) (Priority: HIGH)

CONTENT MANAGEMENT:
├─ Adding & Creating Content (Priority: HIGH)
├─ Editing Content (Priority: HIGH)
├─ Publishing & Listing (Priority: HIGH)
├─ Deleting (Priority: MEDIUM)
└─ Bookmarking (Priority: MEDIUM)

SUBSCRIPTION & COMMERCE:
├─ Subscribing/Upgrade (Priority: HIGH)
├─ Checking Out (Priority: HIGH)
├─ Canceling Subscription (Priority: MEDIUM)
└─ Billing & Plans (Priority: HIGH)

SOCIAL & ENGAGEMENT:
├─ Sharing (Priority: MEDIUM)
├─ Adding & Inviting People (Priority: MEDIUM)
├─ Commenting (Priority: MEDIUM)
└─ Upvoting/Reactions (Priority: MEDIUM)
```

### **Tier 2: Important (Add Post-Launch)**

```
ACCOUNT MANAGEMENT:
├─ Profile Editing (Priority: MEDIUM)
├─ Connecting & Linking (OAuth) (Priority: MEDIUM)
├─ Personalizing & Customizing (Priority: MEDIUM)
└─ Uploading & Downloading (Priority: MEDIUM)

ADVANCED FEATURES:
├─ Design Editing (Visual customization) (Priority: MEDIUM)
├─ Media Editing (Priority: MEDIUM)
├─ Recording & Capturing (Priority: LOW)
└─ Scheduling (Priority: LOW)

MODERATION & SAFETY:
├─ Flagging & Reporting (Priority: MEDIUM)
├─ Banning & Blocking (Priority: MEDIUM)
└─ Feedback Submitting (Priority: MEDIUM)
```

### **Tier 3: Optional (Post-MVP)**

```
ADVANCED ENGAGEMENT:
├─ Quizzing (Interactive learning) (Priority: LOW)
├─ Joining & Applying (Groups/communities) (Priority: LOW)
├─ Chatting & Messaging (Direct communication) (Priority: LOW)
├─ Calling (Video/audio) (Priority: LOW)
└─ Deleting Account (Priority: LOW - compliance)
```

---

# PART 2: DETAILED FLOW SPECIFICATIONS

## 🚀 AUTHENTICATION FLOWS

### **FLOW 1: USER SIGNUP & ACCOUNT CREATION**

```
┌─ START: User arrives at landing page
│
├─ STEP 1: "Sign Up" Button Clicked
│  └─ Pattern: Call-to-Action Button (Large, Teal #208A91)
│     └─ Modal/Page: Sign Up Form
│
├─ STEP 2: Email Entry
│  ├─ Input Field: Email Address
│  │  ├─ Validation: Real-time email format check
│  │  ├─ Error State: "Invalid email format"
│  │  ├─ Success State: Green checkmark
│  │  └─ Helper Text: "We'll send you a confirmation link"
│  │
│  └─ Pattern: Form Input with Validation
│
├─ STEP 3: Password Creation
│  ├─ Input Field: Create Password
│  │  ├─ Requirements: 8+ chars, 1 uppercase, 1 number
│  │  ├─ Strength Meter: Visual indicator (weak/fair/strong)
│  │  ├─ Show/Hide Toggle: Eye icon
│  │  └─ Helper Text: "Requirements shown in real-time"
│  │
│  └─ Pattern: Password Input with Strength Indicator
│
├─ STEP 4: User Role Selection
│  ├─ Radio Buttons / Segmented Control:
│  │  ├─ Option 1: "Learner" (icon: student)
│  │  ├─ Option 2: "Educator" (icon: teacher)
│  │  ├─ Option 3: "Creator" (icon: artist)
│  │  └─ Selected state: Highlighted with Teal background
│  │
│  └─ Pattern: Segmented Control / Radio Button Group
│
├─ STEP 5: Terms Acceptance
│  ├─ Checkbox: "I agree to Terms of Service"
│  │  ├─ Link: "Terms of Service" (underlined, teal)
│  │  ├─ Link: "Privacy Policy" (underlined, teal)
│  │  └─ Error State: Red border if unchecked on submit
│  │
│  └─ Pattern: Checkbox with Links
│
├─ STEP 6: Form Submission
│  ├─ Button: "Create Account" (Full width, Teal)
│  │  ├─ Loading State: Spinner + "Creating account..."
│  │  ├─ Success State: Redirect to email verification
│  │  └─ Error State: Error message "Email already exists"
│  │
│  └─ Pattern: Primary Action Button with Loading State
│
├─ STEP 7: Email Verification
│  ├─ Message: "Check your email for verification link"
│  ├─ Resend Link: "Didn't receive it? Resend email" (teal link)
│  ├─ Countdown Timer: "Resend available in 60s"
│  │
│  └─ Pattern: Email Verification State
│
├─ STEP 8: Email Confirmed
│  ├─ Success Message: "Email verified! Welcome to ASTRA"
│  ├─ Auto-redirect: Onboarding tutorial (3 seconds)
│  │
│  └─ Pattern: Success State with Auto-Navigation
│
└─ END: Onboarding Tutorial Starts

ACCESSIBILITY:
├─ ARIA labels on all inputs
├─ Error messages associated with form fields
├─ Tab order: Top to bottom
├─ Keyboard support: Enter to submit
└─ Password requirements readable by screen readers

RESPONSIVE DESIGN:
├─ Mobile (< 768px): Full-screen modal, larger touch targets
├─ Tablet (768-1024px): Centered modal 80% width
└─ Desktop (> 1024px): Centered modal 500px width
```

### **FLOW 2: USER LOGIN**

```
┌─ START: User clicks "Log In"
│
├─ STEP 1: Email Entry
│  ├─ Input: Email Address
│  ├─ Pattern: Form Input with Validation
│  └─ Helper: "Enter your registered email"
│
├─ STEP 2: Password Entry
│  ├─ Input: Password (masked)
│  ├─ Show/Hide Toggle: Eye icon
│  └─ Pattern: Password Input
│
├─ STEP 3: Remember Me (Optional)
│  ├─ Checkbox: "Keep me logged in"
│  └─ Pattern: Checkbox
│
├─ STEP 4: Forgot Password Link
│  ├─ Link: "Forgot password?" (teal, underlined)
│  └─ Pattern: Text Link
│
├─ STEP 5: Form Submission
│  ├─ Button: "Log In" (Full width, Teal)
│  ├─ Loading State: Spinner + "Logging in..."
│  ├─ Success: Redirect to dashboard
│  └─ Error: "Invalid email or password"
│
├─ STEP 6: 2FA (Optional - If Enabled)
│  ├─ Message: "Enter 2FA code from your authenticator"
│  ├─ Input: 6-digit code
│  ├─ Pattern: Number Input
│  └─ Resend Option: "Didn't receive code?"
│
└─ END: Dashboard loads

STATES:
├─ Default State: Empty form, Log In button disabled
├─ Filled State: All fields populated, button enabled
├─ Loading State: Spinner, button disabled
├─ Error State: Red borders, error message below field
└─ Success State: Redirect to dashboard
```

### **FLOW 3: PASSWORD RESET**

```
┌─ START: User clicks "Forgot Password?"
│
├─ STEP 1: Email Entry
│  ├─ Input: Email Address
│  ├─ Message: "Enter the email associated with your account"
│  └─ Pattern: Form Input
│
├─ STEP 2: Submit Request
│  ├─ Button: "Send Reset Link"
│  ├─ Loading State: "Sending..."
│  └─ Success Message: "Check your email for reset link"
│
├─ STEP 3: Check Email
│  ├─ Message: "We sent a password reset link to [email]"
│  ├─ Helper: "Link expires in 24 hours"
│  ├─ Resend: "Resend link" (available after 60s)
│  └─ Pattern: Information Message
│
├─ STEP 4: Click Email Link
│  ├─ External link in email
│  ├─ Redirects to: Reset password page
│  └─ Token validation in URL
│
├─ STEP 5: New Password Entry
│  ├─ Input: New Password
│  │  ├─ Strength meter
│  │  └─ Requirements: 8+ chars, 1 uppercase, 1 number
│  │
│  ├─ Input: Confirm Password
│  │  ├─ Real-time match validation
│  │  └─ Error: "Passwords don't match"
│  │
│  └─ Pattern: Password Input with Validation
│
├─ STEP 6: Submit New Password
│  ├─ Button: "Reset Password"
│  ├─ Loading State: "Resetting..."
│  └─ Success: Redirect to login
│
└─ END: Login with new password

ERROR STATES:
├─ Invalid email: "No account found with this email"
├─ Expired link: "Reset link has expired, request a new one"
├─ Mismatched passwords: "Passwords don't match"
└─ Weak password: "Password doesn't meet requirements"
```

---

## 🎓 ONBOARDING FLOWS

### **FLOW 4: SIGNING UP & ONBOARDING TUTORIAL**

```
┌─ START: Email verified, user enters ASTRA for first time
│
├─ STEP 1: Welcome Screen
│  ├─ Visual: Large ASTRA logo (animated)
│  ├─ Headline: "Welcome to ASTRA"
│  ├─ Subheading: "Your learning journey starts here"
│  ├─ CTA: "Let's Get Started" (Large, Teal)
│  ├─ Pattern: Hero/Welcome State
│  └─ Skip Option: "Skip tutorial" (light gray text)
│
├─ STEP 2: Profile Completion (Quick)
│  ├─ Input 1: Full Name
│  │  └─ Placeholder: "Enter your name"
│  │
│  ├─ Input 2: Preferred Topic
│  │  └─ Dropdown: "Select what you want to learn"
│  │     ├─ Web Development
│  │     ├─ Data Science
│  │     ├─ Mobile Apps
│  │     ├─ AI/ML
│  │     └─ Other
│  │
│  ├─ Pattern: Form with Dropdown
│  └─ CTA: "Next" (Teal button)
│
├─ STEP 3: Interactive Tutorial
│  │
│  ├─ Tutorial Screen 1: "Create Your First Roadmap"
│  │  ├─ Visual: Animated demo showing + button
│  │  ├─ Text: "Click the + button to create a new learning roadmap"
│  │  ├─ Highlight: Box around + button with glow effect
│  │  ├─ Pattern: Tutorial Highlight
│  │  └─ CTA: "Next"
│  │
│  ├─ Tutorial Screen 2: "Explore Learning Paths"
│  │  ├─ Visual: Show sample roadmap with modules
│  │  ├─ Text: "Click any module to start learning"
│  │  ├─ Interactive: User clicks a module
│  │  ├─ Pattern: Interactive Tutorial
│  │  └─ CTA: "Next"
│  │
│  ├─ Tutorial Screen 3: "Use AI Assistant"
│  │  ├─ Visual: Chat bubble animation
│  │  ├─ Text: "Ask our AI anything about your learning path"
│  │  ├─ Example: Show sample AI response
│  │  ├─ Pattern: Feature Highlight
│  │  └─ CTA: "Next"
│  │
│  ├─ Tutorial Screen 4: "Share & Collaborate"
│  │  ├─ Visual: Share button animation
│  │  ├─ Text: "Share your roadmaps with others"
│  │  ├─ Pattern: Feature Highlight
│  │  └─ CTA: "Next"
│  │
│  └─ Tutorial Screen 5: "You're Ready!"
│     ├─ Visual: Confetti animation
│     ├─ Message: "You're all set to start learning"
│     ├─ Pattern: Success/Completion State
│     └─ CTA: "Go to Dashboard" (Primary)
│
├─ STEP 4: Onboarding Completion
│  ├─ Mark user as "onboarded"
│  ├─ Store completion timestamp
│  └─ Redirect to dashboard
│
└─ END: User lands on dashboard

PATTERN USAGE:
├─ Hero/Welcome State: Large text, clear CTA
├─ Tutorial Highlight: Spotlight effect, glow border
├─ Interactive Tutorial: Real action required
├─ Feature Highlight: Show capability
└─ Success/Completion: Celebratory animation

RESPONSIVE:
├─ Mobile: Full-screen onboarding, bottom sheet style
├─ Desktop: Centered modal
└─ Skip available on all screens
```

---

## 🎯 CORE PRODUCT FLOWS

### **FLOW 5: CREATING A ROADMAP (AI-Powered)**

```
┌─ START: User clicks "+ Create Roadmap"
│
├─ STEP 1: Roadmap Type Selection
│  ├─ Options (Radio/Cards):
│  │  ├─ "GitHub Repository" (icon: GitHub)
│  │  ├─ "Topic" (icon: target)
│  │  ├─ "Course" (icon: book)
│  │  └─ "Custom" (icon: sparkles)
│  │
│  ├─ Pattern: Card/Radio Selection
│  └─ CTA: "Next"
│
├─ STEP 2: Input Based on Type
│  │
│  ├─ If GitHub:
│  │  ├─ Input: GitHub URL
│  │  │  ├─ Placeholder: "github.com/user/repo"
│  │  │  ├─ Validation: Real-time GitHub API check
│  │  │  └─ Success: "✓ Repository found"
│  │  │
│  │  ├─ Button: "Connect GitHub" (OAuth flow)
│  │  └─ Pattern: External Authentication
│  │
│  ├─ If Topic:
│  │  ├─ Input: Topic Name
│  │  │  ├─ Placeholder: "e.g., React Hooks, Machine Learning"
│  │  │  └─ Helper: "Be as specific as possible"
│  │  │
│  │  ├─ Input: Experience Level (Dropdown)
│  │  │  ├─ Beginner
│  │  │  ├─ Intermediate
│  │  └─ Advanced
│  │
│  └─ Pattern: Form with Dropdown
│
├─ STEP 3: AI Processing
│  ├─ Screen: Loading State
│  │  ├─ Animation: Animated spinner with dots
│  │  ├─ Message: "Analyzing your request..."
│  │  ├─ Progress: "Processing repository structure..." (if GitHub)
│  │  ├─ Pattern: Loading State with Progress
│  │  └─ Duration: 5-30 seconds
│  │
│  └─ Background: AI processes and generates roadmap
│
├─ STEP 4: AI Generation Preview
│  ├─ Screen: Preview generated roadmap
│  │  ├─ Visual: Roadmap diagram with modules
│  │  ├─ Header: "Your Learning Roadmap"
│  │  ├─ Sections:
│  │  │  ├─ Overview (brief description)
│  │  │  ├─ Learning Goals (3-5 key objectives)
│  │  │  ├─ Modules (expandable list)
│  │  │  └─ Estimated Time (total duration)
│  │  │
│  │  └─ Pattern: Preview/Details State
│  │
│  ├─ Actions:
│  │  ├─ Edit: "Customize" (modify title, description)
│  │  ├─ Regenerate: "Regenerate" (create new version)
│  │  ├─ Expand: Click module to see details
│  │  └─ Pattern: Action Buttons
│  │
│  └─ CTA: "Save Roadmap" (Primary, Teal)
│
├─ STEP 5: Save & Name
│  ├─ Input: Roadmap Title
│  │  ├─ Default: AI-suggested title
│  │  ├─ Editable: User can customize
│  │  └─ Helper: "Choose a memorable name"
│  │
│  ├─ Input: Description (Optional)
│  │  ├─ Placeholder: "Add notes about this roadmap"
│  │  └─ Character limit: 500 chars
│  │
│  ├─ Toggle: Make Public (Optional)
│  │  ├─ Default: Private
│  │  ├─ If enabled: Others can view/use
│  │  └─ Pattern: Toggle Switch
│  │
│  └─ CTA: "Save Roadmap" (Full width, Teal)
│
├─ STEP 6: Success
│  ├─ Message: "Roadmap created!" (Success toast)
│  ├─ Animation: Check mark animation
│  ├─ Auto-redirect: To roadmap detail page (2 seconds)
│  └─ Pattern: Success State
│
└─ END: Roadmap created, user views it

ACCESSIBILITY:
├─ ARIA labels on all inputs
├─ Loading state announced to screen readers
├─ Focus management throughout flow
└─ Keyboard shortcuts: Enter to submit forms

MOBILE OPTIMIZATION:
├─ Step-by-step modal layout
├─ Full-screen forms on small screens
├─ Larger touch targets (44px minimum)
└─ Simplified GitHub auth flow
```

### **FLOW 6: EXPLORING & FILTERING ROADMAPS**

```
┌─ START: User clicks "Explore" tab
│
├─ STEP 1: Discovery Dashboard
│  ├─ Header: "Discover Learning Paths"
│  ├─ Filter Bar: Category, Level, Time
│  │  ├─ Dropdown 1: Category
│  │  │  ├─ Web Development
│  │  │  ├─ Data Science
│  │  │  ├─ Mobile Apps
│  │  │  ├─ AI/ML
│  │  │  └─ All Categories
│  │  │
│  │  ├─ Dropdown 2: Experience Level
│  │  │  ├─ Beginner
│  │  │  ├─ Intermediate
│  │  │  ├─ Advanced
│  │  │  └─ All Levels
│  │  │
│  │  ├─ Dropdown 3: Duration
│  │  │  ├─ < 1 week
│  │  │  ├─ 1-4 weeks
│  │  │  ├─ 1-3 months
│  │  │  └─ All Durations
│  │  │
│  │  └─ Pattern: Dropdown Filters
│  │
│  ├─ Search Bar: "Search roadmaps..."
│  │  ├─ Pattern: Search Input with Icon
│  │  └─ Autocomplete: Show popular searches
│  │
│  └─ Sort Options:
│     ├─ "Trending" (default)
│     ├─ "Most Followed"
│     ├─ "Newest"
│     └─ "Rating"
│
├─ STEP 2: Results Grid/List
│  ├─ View Toggle: Grid / List (icon buttons)
│  │
│  ├─ Grid View (Default):
│  │  └─ Roadmap Cards (Responsive 2-4 columns):
│  │     ├─ Image: Category icon or preview
│  │     ├─ Title: "React Advanced Patterns"
│  │     ├─ Author: "by @JohnDoe"
│  │     ├─ Rating: "⭐ 4.8 (128 reviews)"
│  │     ├─ Meta: "8 modules • 4 weeks"
│  │     ├─ Description: Brief text (2 lines)
│  │     ├─ Hover State: Slight shadow increase, pointer cursor
│  │     └─ Pattern: Card Component
│  │
│  ├─ List View:
│  │  └─ Roadmap Rows:
│  │     ├─ Icon: Category icon (left)
│  │     ├─ Title: "React Advanced Patterns"
│  │     ├─ Info: "by @JohnDoe • 4.8⭐ • 8 modules • 4 weeks"
│  │     ├─ Description: Brief text (visible on hover)
│  │     └─ Pattern: List Item Component
│  │
│  └─ Pagination: "Load More" button or pagination controls
│
├─ STEP 3: Card Interaction
│  ├─ Click Card:
│  │  ├─ Navigate to: Roadmap detail page
│  │  └─ Pattern: Navigation
│  │
│  ├─ Hover Actions (Desktop):
│  │  ├─ "Preview" button (opens preview modal)
│  │  ├─ "Save" button (adds to favorites)
│  │  └─ "Share" button (copy link)
│  │
│  └─ Pattern: Card Actions
│
├─ STEP 4: Filtering Results
│  ├─ User selects filter option
│  ├─ Results update in real-time
│  ├─ Show result count: "Showing 24 roadmaps"
│  ├─ Empty state if no results: "No roadmaps match your filters"
│  └─ Pattern: Dynamic Filter Results
│
├─ STEP 5: Search
│  ├─ User types in search bar
│  ├─ Real-time autocomplete suggestions
│  ├─ Display results matching query
│  ├─ Highlight: Matching keywords in results
│  └─ Pattern: Search Results
│
└─ END: User browses roadmaps

STATES:
├─ Default: Trending roadmaps displayed
├─ Loading: Spinner in cards while loading
├─ Filtered: Results updated with selections
├─ Empty: "No results match your filters" message
├─ Hover: Card elevation increases
└─ Error: "Unable to load roadmaps" with retry button
```

### **FLOW 7: EDITING A ROADMAP**

```
┌─ START: User opens roadmap and clicks "Edit"
│
├─ STEP 1: Enter Edit Mode
│  ├─ Button: "Edit" or pencil icon
│  ├─ Screen transitions to edit view
│  ├─ UI changes:
│  │  ├─ All inputs become editable
│  │  ├─ Delete buttons appear
│  │  ├─ Add module button becomes prominent
│  │  └─ Save/Cancel buttons appear at top/bottom
│  │
│  └─ Pattern: Edit Mode Activation
│
├─ STEP 2: Edit Roadmap Metadata
│  ├─ Input: Title (editable)
│  ├─ Input: Description (editable, multiline)
│  ├─ Dropdown: Category
│  ├─ Dropdown: Experience Level
│  ├─ Pattern: Form Inputs
│  └─ Real-time character count: "123/500 characters"
│
├─ STEP 3: Manage Modules
│  │
│  ├─ Existing Modules List:
│  │  └─ For each module:
│  │     ├─ Input: Module Title (editable)
│  │     ├─ Input: Description (editable)
│  │     ├─ Input: Duration (editable)
│  │     ├─ Button: Delete (icon with confirmation)
│  │     ├─ Handle: Drag to reorder (⋮⋮ icon)
│  │     └─ Pattern: Editable List Item with Drag
│  │
│  ├─ Add Module:
│  │  ├─ Button: "+ Add Module"
│  │  ├─ Action: Appends new empty module
│  │  ├─ Focus: Auto-focuses on new module title
│  │  └─ Pattern: Add Item Button
│  │
│  └─ Reorder:
│     ├─ Drag & Drop: Modules reorder smoothly
│     ├─ Pattern: Drag & Drop
│     └─ Numbers update automatically
│
├─ STEP 4: Edit Module Details (Optional)
│  ├─ Click Module Title:
│  │  ├─ Expands to show full details
│  │  ├─ Sub-inputs:
│  │  │  ├─ Learning objectives (bullet list)
│  │  │  ├─ Resources (links, videos)
│  │  │  ├─ Estimated time
│  │  │  └─ Difficulty level
│  │  │
│  │  └─ Pattern: Expandable Section
│  │
│  └─ Save happens automatically (debounced)
│
├─ STEP 5: Save Changes
│  ├─ Button: "Save" (Primary, Teal, full width)
│  ├─ Button: "Cancel" (Secondary, gray)
│  ├─ Auto-save indicator: "Saving..." or "All changes saved"
│  ├─ Loading state: Spinner in Save button
│  └─ Pattern: Primary/Secondary Buttons
│
├─ STEP 6: Save Success
│  ├─ Toast notification: "Roadmap updated!"
│  ├─ Exit edit mode
│  ├─ Return to view mode
│  └─ Pattern: Success Notification
│
└─ END: Roadmap edited, saved

UNSAVED CHANGES:
├─ Indicator: "You have unsaved changes" (yellow banner)
├─ Confirmation: If user tries to navigate away
├─ Message: "Do you want to save changes?"
├─ Options: "Save", "Discard", "Cancel"
└─ Pattern: Confirmation Dialog

ACCESSIBILITY:
├─ Focus management: Focus first input on edit
├─ Keyboard: Tab through all editable fields
├─ Screen readers: "Edit mode enabled"
└─ Unsaved changes announced
```

---

## 🛒 SUBSCRIPTION & COMMERCE FLOWS

### **FLOW 8: SUBSCRIBING TO PREMIUM**

```
┌─ START: User clicks "Upgrade" or views pricing
│
├─ STEP 1: Pricing Page
│  ├─ Header: "Choose Your Plan"
│  ├─ Subtext: "Start free, upgrade anytime"
│  │
│  ├─ Plan Cards (3 options):
│  │
│  ├─ Card 1: FREE PLAN
│  │  ├─ Price: "$0/month"
│  │  ├─ Badge: "Current Plan" (if user on free)
│  │  ├─ Features:
│  │  │  ├─ ✓ Create 5 roadmaps
│  │  │  ├─ ✓ Basic AI assistance
│  │  │  ├─ ✓ Share roadmaps
│  │  │  ├─ ✗ Advanced AI features
│  │  │  ├─ ✗ Priority support
│  │  │  └─ ✗ Custom branding
│  │  │
│  │  └─ Button: "Current Plan" (Disabled gray)
│  │
│  ├─ Card 2: PRO PLAN (Highlighted)
│  │  ├─ Price: "$9.99/month" or "$99/year"
│  │  ├─ Badge: "Most Popular" (orange)
│  │  ├─ Features:
│  │  │  ├─ ✓ Unlimited roadmaps
│  │  │  ├─ ✓ Advanced AI assistance
│  │  │  ├─ ✓ Team collaboration (5 members)
│  │  │  ├─ ✓ Analytics dashboard
│  │  │  ├─ ✓ Priority email support
│  │  │  └─ ✗ Custom branding
│  │  │
│  │  ├─ Button: "Upgrade to Pro" (Primary, Teal)
│  │  └─ Ribbon/Border: Highlighted with border
│  │
│  └─ Card 3: ENTERPRISE PLAN
│     ├─ Price: "Custom pricing"
│     ├─ Features:
│     │  ├─ ✓ Everything in Pro
│     │  ├─ ✓ Unlimited team members
│     │  ├─ ✓ Custom branding
│     │  ├─ ✓ Dedicated support
│     │  ├─ ✓ SSO/SAML
│     │  └─ ✓ Advanced analytics
│     │
│     └─ Button: "Contact Sales" (Secondary, gray)
│
├─ STEP 2: Billing Interval Toggle
│  ├─ Toggle: Monthly / Yearly
│  │  ├─ Monthly: "Pay monthly" (active)
│  │  ├─ Yearly: "Pay yearly (Save 20%)"
│  │  └─ Pattern: Toggle Switch
│  │
│  └─ Prices update in real-time
│
├─ STEP 3: Select Plan & Checkout
│  ├─ User clicks "Upgrade to Pro"
│  ├─ Navigate to: Checkout page
│  └─ Pattern: Primary CTA Button
│
├─ STEP 4: Checkout
│  ├─ Header: "Complete Your Purchase"
│  │
│  ├─ Order Summary (Right side on desktop):
│  │  ├─ Plan: "Pro Plan"
│  │  ├─ Interval: "Monthly"
│  │  ├─ Price: "$9.99/month"
│  │  ├─ Tax: "$0.00" (calculated)
│  │  ├─ Total: "$9.99"
│  │  └─ Pattern: Order Summary Card
│  │
│  ├─ Billing Information:
│  │  ├─ Email: Pre-filled
│  │  ├─ Name: Text input
│  │  ├─ Address: Text input
│  │  ├─ City: Text input
│  │  ├─ State: Dropdown
│  │  └─ Zip Code: Text input
│  │
│  ├─ Pattern: Form Inputs
│  └─ Helper text: "We never share your information"
│
├─ STEP 5: Payment Method
│  ├─ Card Information:
│  │  ├─ Card Number: Masked input, shows card type
│  │  ├─ Expiry: MM/YY format
│  │  ├─ CVC: 3-digit security code
│  │  └─ Pattern: Payment Card Inputs
│  │
│  ├─ Alternative Options:
│  │  ├─ Link: "PayPal" (external redirect)
│  │  ├─ Link: "Apple Pay" (if available)
│  │  └─ Pattern: Payment Method Options
│  │
│  └─ Secured badge: "Secured by Stripe" + lock icon
│
├─ STEP 6: Billing Agreement
│  ├─ Checkbox: "I agree to Recurring Billing"
│  │  ├─ Helper: "Your subscription will auto-renew monthly"
│  │  ├─ Helper: "You can cancel anytime"
│  │  └─ Links: "Terms" and "Cancellation Policy"
│  │
│  └─ Pattern: Checkbox with Links
│
├─ STEP 7: Submit Payment
│  ├─ Button: "Complete Purchase" (Full width, Teal)
│  ├─ Loading state: "Processing payment..."
│  ├─ SSL indicator: "🔒 Secure transaction"
│  └─ Pattern: Primary Action Button
│
├─ STEP 8: Payment Processing
│  ├─ Screen: Loading state
│  │  ├─ Message: "Processing your payment..."
│  │  ├─ Substeps shown (optional):
│  │  │  ├─ "Validating card..."
│  │  │  ├─ "Confirming subscription..."
│  │  │  └─ "Setting up your account..."
│  │  │
│  │  ├─ Pattern: Loading State with Progress
│  │  └─ Duration: 3-10 seconds
│  │
│  └─ If error: Show error message with retry option
│
├─ STEP 9: Success
│  ├─ Page: Success confirmation
│  │  ├─ Icon: Large checkmark animation
│  │  ├─ Headline: "Welcome to Pro!"
│  │  ├─ Message: "Your subscription is active"
│  │  ├─ Receipt email: "Confirmation sent to [email]"
│  │  │
│  │  ├─ Details:
│  │  │  ├─ Plan: Pro Plan
│  │  │  ├─ Renews: [Date]
│  │  │  ├─ Amount: $9.99/month
│  │  │  └─ Manage: Link to subscription settings
│  │  │
│  │  └─ Pattern: Success State
│  │
│  ├─ Buttons:
│  │  ├─ Primary: "Go to Dashboard"
│  │  └─ Secondary: "View Subscription Settings"
│  │
│  └─ Email: Sent to user with receipt and invoice
│
└─ END: Subscription active

ERROR STATES:
├─ Card declined: "Your card was declined. Try another payment method."
├─ Network error: "Connection error. Please try again."
├─ Invalid input: "Please check your billing information"
└─ All errors show retry button

ACCESSIBILITY:
├─ Form fields labeled with ARIA labels
├─ Error messages associated with inputs
├─ Focus management in checkout flow
├─ Keyboard navigation supported
└─ Screen reader announces success
```

### **FLOW 9: CANCELING SUBSCRIPTION**

```
┌─ START: User clicks "Manage Subscription" > "Cancel Plan"
│
├─ STEP 1: Confirmation Modal
│  ├─ Header: "We're sorry to see you go"
│  ├─ Message: "You're about to cancel your Pro subscription"
│  │
│  ├─ Details:
│  │  ├─ Plan: "Pro Plan"
│  │  ├─ Next renewal: "[Date]"
│  │  ├─ Info: "You'll lose access to Pro features immediately"
│  │  └─ Info: "Your data will be available for 30 days"
│  │
│  ├─ Pattern: Confirmation Dialog
│  └─ CTA: "Cancel Subscription" (Destructive, red)
│
├─ STEP 2: Feedback (Optional)
│  ├─ Question: "What's the reason for canceling?"
│  │  ├─ Too expensive
│  │  ├─ Don't need the features
│  │  ├─ Using another service
│  │  ├─ Temporary (plan to return)
│  │  └─ Other
│  │
│  ├─ Textarea: "Tell us more (optional)"
│  │  └─ Placeholder: "We'd love to hear your feedback"
│  │
│  └─ Pattern: Survey/Feedback
│
├─ STEP 3: Retention Offer (Optional)
│  ├─ Offer: "Hold on, we have a special offer"
│  ├─ Message: "Get 50% off for 3 months"
│  │
│  ├─ Buttons:
│  │  ├─ "Accept Offer" (Teal)
│  │  └─ "No, Cancel Anyway" (Gray)
│  │
│  └─ Pattern: Retention Dialog
│
├─ STEP 4: Process Cancellation
│  ├─ If offer accepted: Continue with discounted plan
│  ├─ If declined: Process cancellation
│  ├─ Loading state: "Processing cancellation..."
│  └─ Pattern: Loading State
│
├─ STEP 5: Cancellation Confirmation
│  ├─ Message: "Your subscription has been canceled"
│  ├─ Details:
│  │  ├─ Effective immediately
│  │  ├─ Data retention: "30 days"
│  │  ├─ Reactivate link: "Reactivate subscription"
│  │  └─ Support: "Questions? Contact support"
│  │
│  ├─ Pattern: Success State
│  └─ CTA: "Done" or "Back to Settings"
│
├─ STEP 6: Email Confirmation
│  ├─ Email sent to user
│  ├─ Contains:
│  │  ├─ Cancellation confirmation
│  │  ├─ Data retention information
│  │  ├─ Reactivation link
│  │  └─ Support contact information
│  │
│  └─ Pattern: Transactional Email
│
└─ END: Subscription canceled

STATES:
├─ Default: Show current subscription and cancel option
├─ Confirmation: Ask if user really wants to cancel
├─ Feedback: Collect reason for cancellation
├─ Offer: Show retention offer
├─ Processing: Loading state
├─ Success: Show confirmation message
└─ Email: Send confirmation email

REACTIVATION:
├─ User can reactivate anytime within 30 days
├─ Link in cancellation email
├─ Option in account settings
└─ Restores plan to same tier
```

---

## 📱 SOCIAL & ENGAGEMENT FLOWS

### **FLOW 10: SHARING A ROADMAP**

```
┌─ START: User clicks "Share" button on roadmap
│
├─ STEP 1: Share Modal Opens
│  ├─ Header: "Share This Roadmap"
│  ├─ Roadmap preview: Title, icon, brief description
│  │
│  └─ Pattern: Modal Dialog
│
├─ STEP 2: Copy Link
│  ├─ Section: "Get Link"
│  │  ├─ Copy input: Shows current URL (read-only)
│  │  ├─ Copy button: "Copy Link" (with copy icon)
│  │  ├─ Success feedback: "Copied!" (briefly shows)
│  │  └─ Pattern: Copy to Clipboard
│  │
│  ├─ Generated short link option:
│  │  ├─ Button: "Create Short Link"
│  │  ├─ Shows: Shortened URL
│  │  └─ Pattern: Link Generation
│  │
│  └─ QR Code option:
│     ├─ Button: "Generate QR Code"
│     ├─ Shows: QR code image
│     ├─ Download button: "Download QR Code"
│     └─ Pattern: QR Code Generation
│
├─ STEP 3: Social Share
│  ├─ Section: "Share on Social"
│  │
│  ├─ Social buttons (row):
│  │  ├─ Facebook icon (blue)
│  │  ├─ Twitter icon (light blue)
│  │  ├─ LinkedIn icon (professional blue)
│  │  ├─ WhatsApp icon (green)
│  │  └─ Email icon (gray)
│  │
│  └─ Pattern: Social Share Buttons
│
├─ STEP 4: Social Share Action
│  ├─ If user clicks social button:
│  │  ├─ Pre-filled message: "Check out this learning roadmap on ASTRA"
│  │  ├─ Includes link
│  │  ├─ Opens social platform (new tab)
│  │  ├─ Pre-populates share dialog
│  │  └─ Pattern: External Share
│  │
│  └─ Tracking: Analytics recorded for share
│
├─ STEP 5: Embed Option (Optional)
│  ├─ Section: "Embed"
│  ├─ Code block: Shows embed code (read-only)
│  ├─ Copy button: "Copy Embed Code"
│  ├─ Helper: "Add this roadmap to your website"
│  └─ Pattern: Code Snippet
│
├─ STEP 6: Sharing Permissions
│  ├─ Section: "Visibility"
│  │
│  ├─ Radio options:
│  │  ├─ "Private" - Only me
│  │  ├─ "Link" - Anyone with the link
│  │  ├─ "Public" - Everyone (searchable)
│  │  └─ Pattern: Radio Button Group
│  │
│  ├─ Current selection: Indicated by checkmark
│  └─ Change: Click to update
│
├─ STEP 7: Advanced Sharing (Optional)
│  ├─ Section: "Share with Specific People"
│  │
│  ├─ Input: "Enter email addresses"
│  │  ├─ Placeholder: "user@example.com"
│  │  ├─ Add multiple: Press Enter or click button
│  │  ├─ List: Shows added emails with remove button
│  │  └─ Pattern: Tag/Chip Input
│  │
│  ├─ Permissions dropdown:
│  │  ├─ "Can View" (read-only)
│  │  ├─ "Can Edit" (can modify)
│  │  └─ Pattern: Dropdown
│  │
│  ├─ Button: "Send Invites" (Teal)
│  └─ Notification: "Invites sent" (success)
│
├─ STEP 8: Sharing Activity
│  ├─ Section: "Sharing Activity" (if public)
│  │  ├─ Stats: "Shared 3 times"
│  │  ├─ Stats: "10 people viewed"
│  │  ├─ Stats: "Viewed in 5 countries"
│  │  └─ Pattern: Analytics/Stats
│  │
│  └─ List: Shows recent shares (if applicable)
│
└─ END: Modal closes, sharing complete

STATES:
├─ Default: Link displayed, social buttons ready
├─ Copied: "Copied!" feedback
├─ Short link generated: Shows shortened URL
├─ QR generated: Shows QR code
├─ Social share: Opens new tab
├─ Invites sent: Success message
└─ Error: "Failed to generate link, please try again"

ACCESSIBILITY:
├─ ARIA labels on all buttons
├─ Copy to clipboard announced
├─ Social buttons clearly labeled
└─ Modal can be closed with Escape key
```

---

## 📊 UX PATTERN IMPLEMENTATIONS

### **KEY UX PATTERNS FOR ASTRA**

#### **PATTERN 1: FORM VALIDATION**

```
REAL-TIME VALIDATION:
├─ As user types, validate input
├─ Show error messages inline
├─ Display success indicators (checkmarks)
├─ Update submit button state based on form validity

FIELD STATES:
├─ Empty: Gray border, placeholder text
├─ Focused: Blue border, label animated up
├─ Valid: Green checkmark, green border
├─ Error: Red border, error message in red
├─ Disabled: Gray background, no interaction
└─ Success: Green checkmark, green accent

ERROR MESSAGES:
├─ Display below field
├─ Color: Red (#FF5459 or similar)
├─ Icon: Warning icon (⚠)
├─ Message: Specific and actionable
├─ Examples:
│  ├─ "Email is already registered"
│  ├─ "Password must contain at least 1 uppercase letter"
│  └─ "This field is required"

EXAMPLES:
├─ Email: Regex validation + async check for duplicates
├─ Password: Strength meter, real-time requirements check
├─ URL: Format validation, optional resource check
└─ Phone: Format validation with country code support
```

#### **PATTERN 2: LOADING STATES**

```
SKELETON LOADING:
├─ Use for page content
├─ Show placeholder shapes
├─ Gray placeholder color (#E0E0E0)
├─ Subtle animation: Shimmer effect
├─ Duration: Until content loads
└─ Example: Card skeleton, text skeleton lines

SPINNER LOADING:
├─ Use for button actions
├─ Animated spinner icon (rotating)
├─ Color: Primary Teal (#208A91)
├─ Button disabled during load
├─ Show loading text: "Loading..."
└─ Duration: Until action completes

PROGRESS LOADING:
├─ Use for long operations
├─ Progress bar: Visual indication
├─ Percentage: "45% complete"
├─ Substeps: "Validating..." → "Processing..." → "Finalizing..."
├─ Estimated time (optional): "About 30 seconds remaining"
└─ Duration: Until 100% complete

STATES:
├─ Skeleton: Page loading
├─ Spinner: Action in progress
├─ Progress: Long-running operation
└─ Success: Complete
```

#### **PATTERN 3: EMPTY STATES**

```
COMPONENTS:
├─ Icon: Relevant to context (large, 64-128px)
├─ Headline: "No roadmaps yet"
├─ Description: "Explain why it's empty and what to do"
├─ CTA Button: "Create Your First Roadmap"
├─ Helper text: "It only takes 30 seconds"

VARIATIONS:
├─ First-time empty: Show onboarding
├─ Filtered empty: "No results match your filters"
├─ Search empty: "No results for '[query]'"
├─ Error empty: "Unable to load content. Retry?"
└─ No data: Different icon and message

MESSAGING:
├─ Friendly tone
├─ Clear explanation
├─ Actionable CTA
├─ Possibly show example

EXAMPLE (No Roadmaps):
├─ Icon: Road/path icon
├─ Headline: "Create Your First Learning Roadmap"
├─ Description: "Start by uploading a GitHub repo or describing a topic you want to learn"
├─ Button: "Create Roadmap"
└─ Help text: "Learn more about roadmaps"
```

#### **PATTERN 4: SUCCESS STATES**

```
TOAST NOTIFICATIONS:
├─ Position: Top-right (mobile: full-width bottom)
├─ Duration: 4 seconds (auto-dismiss)
├─ Icon: Green checkmark
├─ Color: Green accent (#4CAF50 or similar)
├─ Message: Concise action confirmation
├─ Dismissible: Click X to close
└─ Examples:
   ├─ "Roadmap created!"
   ├─ "Changes saved"
   ├─ "Invitation sent"
   └─ "Copied to clipboard"

FULL SCREEN SUCCESS:
├─ Used for major actions (payments, signups)
├─ Icon: Large animated checkmark (64-128px)
├─ Headline: "Success!"
├─ Description: Details about what happened
├─ CTA: "Next step" or "Done"
└─ Examples:
   ├─ Payment confirmation
   ├─ Account created
   └─ Subscription activated

INLINE SUCCESS:
├─ Used in forms
├─ Green checkmark next to field
├─ Green text: "✓ Looks good!"
└─ Field disabled/locked after confirmation
```

#### **PATTERN 5: ERROR STATES**

```
ERROR MESSAGES:
├─ Position: Inline with field (forms) or toast (general)
├─ Color: Red accent (#FF5459 or #DC3545)
├─ Icon: Warning or X icon
├─ Content: 
│  ├─ What went wrong (specific)
│  ├─ Why it happened (explanation)
│  └─ How to fix it (actionable)
│
├─ Example:
│  ├─ Bad: "Error"
│  ├─ Good: "Email is already registered. Try logging in or use a different email."
│  └─ Better: "Email already registered. Want to log in instead?"

FIELD ERRORS (Forms):
├─ Red border around field
├─ Error message below field
├─ Field focused when form submitted with errors
└─ Error indicator icon (⚠)

GENERAL ERRORS:
├─ Toast notification
├─ Red background
├─ Dismiss option: X or auto-dismiss after 6s
├─ Action: "Retry" or "Go back"
└─ Support link: "Contact support if issue persists"

ERROR TYPES:
├─ Network error: "Connection lost. Check your internet and try again."
├─ Server error: "Something went wrong on our end. Please try again."
├─ Validation error: "Please check the highlighted fields"
├─ Permission error: "You don't have access to this resource"
└─ Not found: "This roadmap no longer exists"
```

#### **PATTERN 6: CONFIRMATION DIALOGS**

```
STRUCTURE:
├─ Header: Question or confirmation needed
├─ Message: Explain what will happen
├─ Details (optional): Additional information
├─ Buttons: Action options

BUTTONS:
├─ Primary (Destructive): "Delete", "Cancel Subscription" (red)
├─ Secondary (Safe): "Keep", "Don't delete" (gray)
├─ Tertiary (Alternative): "Learn more" (text link)
└─ Default focus: Safe option

EXAMPLES:

EXAMPLE 1 (Delete):
├─ Title: "Delete Roadmap?"
├─ Message: "Are you sure? This cannot be undone."
├─ Details: "Name: 'React Advanced Patterns'"
├─ Buttons:
│  ├─ "Delete" (Red, destructive)
│  └─ "Cancel" (Gray, safe)

EXAMPLE 2 (Confirm Action):
├─ Title: "Make Roadmap Public?"
├─ Message: "Anyone with the link will be able to view this roadmap."
├─ Details: "You can change this anytime in settings."
├─ Buttons:
│  ├─ "Make Public" (Teal, confirm)
│  └─ "Keep Private" (Gray, safe)

EXAMPLE 3 (Unsaved Changes):
├─ Title: "Unsaved Changes"
├─ Message: "You have unsaved changes. Leave anyway?"
├─ Buttons:
│  ├─ "Save" (Teal, primary)
│  ├─ "Discard" (Red, destructive)
│  └─ "Cancel" (Gray, safe)
```

---

## 📄 PAGE STATE PATTERNS

### **FILTER & SORTING PATTERN**

```
FILTER BAR LAYOUT:
├─ Position: Top of content area
├─ Background: Light gray or white
├─ Layout: Horizontal scrollable on mobile

FILTER OPTIONS:
├─ Dropdowns (closed state):
│  ├─ Label: "Category"
│  ├─ Selected value: "All Categories"
│  ├─ Icon: Chevron down
│  └─ Tap/click: Opens dropdown menu
│
├─ Dropdowns (open state):
│  ├─ List: All options
│  ├─ Checkmarks: Selected options
│  ├─ Search: "Filter options..." (for long lists)
│  └─ Click outside: Closes dropdown
│
├─ Toggle: "Show archived" (on/off)
│  ├─ Icon: Eye icon
│  ├─ Label: "Show Archived"
│  └─ Animated toggle switch
│
├─ Search: "Search content..."
│  ├─ Input field
│  ├─ Icon: Magnifying glass
│  └─ Real-time filtering
│
└─ Clear all: "Clear Filters" link
   └─ Appears when filters applied

SORT OPTIONS:
├─ Dropdown: "Sort By"
├─ Options:
│  ├─ Trending (default)
│  ├─ Most Popular
│  ├─ Newest
│  ├─ Rating
│  ├─ Duration (ascending)
│  └─ Duration (descending)
│
└─ Ascending/Descending toggle (if applicable)

RESULTS:
├─ Count: "Showing 24 of 156 roadmaps"
├─ No results: Empty state with message
├─ Loading: Skeleton cards while filtering
└─ Real-time update: Results change as filters applied
```

### **SEARCH PATTERN**

```
SEARCH BAR:
├─ Position: Top of page
├─ Layout: Full-width input
├─ Placeholder: "Search roadmaps, creators, topics..."
├─ Icon: Magnifying glass (left)
├─ Clear button: X icon (right, if text entered)
└─ Focus state: Blue border, shadow

AUTOCOMPLETE (As user types):
├─ Dropdown below search
├─ Shows:
│  ├─ "Recent searches" (first time)
│  ├─ "Suggested searches" (popular queries)
│  ├─ "Search results" (matching content)
│  └─ "Did you mean?" (if typo detected)
│
├─ Keyboard navigation:
│  ├─ Arrow keys: Navigate suggestions
│  ├─ Enter: Search for selected item
│  ├─ Escape: Close suggestions
│  └─ Click: Select suggestion
│
└─ Max 8 suggestions shown

RESULTS PAGE:
├─ Header: "Search results for '[query]'"
├─ Result count: "Found 42 results"
├─ Tabs (optional): "Roadmaps", "Creators", "Topics"
├─ Results list: Matching items
├─ Highlight: Search term highlighted in results
├─ No results: Empty state with suggestions
└─ Pagination: "Load More" or traditional pagination

SEARCH ANALYTICS:
├─ Track: Popular searches
├─ Track: Failed searches (no results)
├─ Use for: Auto-suggestions, trending topics
└─ Respect: User privacy (anonymized)
```

---

## 🎨 ACCESSIBILITY GUIDELINES

### **WCAG AA COMPLIANCE CHECKLIST**

```
COLOR CONTRAST:
├─ Text on background: 4.5:1 ratio minimum
├─ Large text (18pt+): 3:1 ratio minimum
├─ UI components: 3:1 ratio minimum
├─ Verify: Use WAVE or Color Contrast Analyzer
└─ Test: Light mode and dark mode

KEYBOARD NAVIGATION:
├─ All interactive elements: Tab-able
├─ Logical tab order: Left to right, top to bottom
├─ Focus indicator: Always visible (2px border, not removed)
├─ Focus trapping: Modals trap focus within dialog
├─ Escape key: Close modals and open menus
├─ Enter/Space: Activate buttons
└─ Arrow keys: Navigate lists and menus

SCREEN READERS:
├─ ARIA labels: All buttons and icons labeled
├─ ARIA descriptions: Form fields have labels
├─ ARIA live regions: Loading, success, error states announced
├─ Semantic HTML: Use <button>, <input>, <label>, etc.
├─ Skip links: "Skip to main content"
└─ Headings: Proper hierarchy (h1 > h2 > h3)

VISUAL DESIGN:
├─ Font size: Minimum 14px body text
├─ Line height: Minimum 1.5 for body text
├─ Letter spacing: Adequate for readability
├─ Line length: 50-75 characters for readability
├─ Avoid: All caps, excessive italics, underlines on links
└─ Icons: Never use color alone to convey meaning

FORM ACCESSIBILITY:
├─ Labels: Associated with form fields (<label for="id">)
├─ Errors: Announce to screen readers
├─ Required: Mark with * and announce
├─ Hints: Available via aria-describedby
└─ Focus: Managed properly throughout form

MOTION & ANIMATION:
├─ Respect: prefers-reduced-motion setting
├─ Avoid: Auto-playing animations
├─ Avoid: Flashing content (>3 times/second)
└─ Provide: Pause/stop controls for animations

TESTING:
├─ Screen reader: NVDA, JAWS, VoiceOver
├─ Tools: WAVE, Axe DevTools, Lighthouse
├─ Manual testing: Keyboard only navigation
├─ User testing: With people using assistive tech
└─ Automated: Accessibility checks in CI/CD
```

---

## 📱 RESPONSIVE DESIGN

### **BREAKPOINT STRATEGY**

```
MOBILE FIRST (< 640px):
├─ Single column layout
├─ Full-width inputs and buttons
├─ Touch targets: 44px minimum (48px preferred)
├─ Modals: Full-screen or bottom sheet
├─ Navigation: Hamburger menu or bottom nav
├─ Type: 16px minimum body text (prevent auto-zoom)
└─ Spacing: Generous (16px padding)

TABLET (640px - 1024px):
├─ Two column layout (if applicable)
├─ Wider inputs and comfortable spacing
├─ Cards: 2-3 per row
├─ Navigation: Visible or collapsible sidebar
└─ Modals: Centered, 70% width

DESKTOP (> 1024px):
├─ Multi-column layout
├─ Wider content area
├─ Cards: 3-4 per row
├─ Navigation: Visible sidebar
├─ Modals: 500-600px width
└─ Maximum content width: 1200-1400px

MEDIA QUERIES:
├─ @media (max-width: 640px) { ... }
├─ @media (min-width: 640px) { ... }
├─ @media (min-width: 1024px) { ... }
├─ @media (min-width: 1280px) { ... }
└─ Avoid: Fixed widths, horizontal scrolling
```

---

## ✅ IMPLEMENTATION CHECKLIST

### **FOR EACH FLOW**

```
DESIGN PHASE:
☐ Create wireframes
☐ Design mockups (mobile, tablet, desktop)
☐ Define all page states (default, loading, error, success)
☐ Create interaction documentation
☐ Validate contrast ratios (4.5:1 minimum)
☐ Annotate with measurements and colors
☐ Create accessibility notes

DEVELOPMENT PHASE:
☐ Build responsive layout
☐ Implement form validation
☐ Add loading states
☐ Add error handling
☐ Implement success states
☐ Add ARIA labels
☐ Test keyboard navigation
☐ Test with screen reader
☐ Test in multiple browsers
☐ Test on mobile devices

TESTING PHASE:
☐ Functional testing: All flows work correctly
☐ Accessibility testing: WCAG AA compliance
☐ Cross-browser testing: Chrome, Firefox, Safari, Edge
☐ Mobile testing: iOS Safari, Android Chrome
☐ Performance testing: Load times < 3 seconds
☐ User testing: Real users complete flows
☐ Analytics: Track user behavior

LAUNCH PHASE:
☐ Performance optimization
☐ Security review
☐ SEO optimization
☐ Analytics implementation
☐ Error monitoring setup
☐ Documentation complete
☐ Team training
☐ Launch!
```

---

## 📞 QUICK REFERENCE

### **FLOW SELECTION SUMMARY**

```
MUST HAVE (MVP - Launch):
✓ Signup & Onboarding
✓ Login
✓ Password Reset
✓ Create Roadmap
✓ Edit Roadmap
✓ Explore/Filter
✓ Subscribe
✓ Checkout
✓ Cancel Subscription

SHOULD HAVE (Phase 1):
✓ Profile Editing
✓ Sharing
✓ Inviting People
✓ Commenting
✓ Bookmarking
✓ Deleting Content

NICE TO HAVE (Phase 2+):
✓ Advanced Search
✓ Messaging
✓ Video Calling
✓ Team Management
✓ Analytics Dashboard
✓ Customization
```

---

**This comprehensive guide covers all critical user flows needed for ASTRA's launch and early growth. Each flow is production-ready with detailed specifications, accessibility considerations, and responsive design patterns.**

**Start with MVP flows, then add Phase 1 features, then expand to advanced features as your team grows.**