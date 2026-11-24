# App Screens

A generic taxonomy of mobile app screen types, applicable to most apps. Each category is a folder, and each screen type is a markdown file with its purpose, key elements, states & variations, design notes, technical considerations (for implementers), and reference links.

## Structure

```
App Screens
│
├── 01 Launch & Onboarding
│   ├── Splash Screen
│   ├── Welcome Carousel
│   ├── Onboarding Quiz
│   ├── Permissions Prompt
│   └── Feature Walkthrough
│
├── 02 Authentication
│   ├── Sign Up
│   ├── Log In
│   ├── OTP Verification
│   ├── Forgot Password
│   ├── Biometric Unlock
│   └── Account Recovery
│
├── 03 Core Navigation
│   ├── Home Dashboard
│   ├── Explore Browse
│   ├── Search
│   ├── Activity History
│   └── Profile Tab
│
├── 04 Content & Detail
│   ├── List Feed
│   ├── Detail Screen
│   ├── Media Player
│   ├── Gallery Image Viewer
│   ├── Map View
│   └── Stats Insights
│
├── 05 Create & Input
│   ├── Create New
│   ├── Edit Form
│   ├── Multi-step Wizard
│   ├── Pickers
│   ├── Camera Scan
│   └── Review Confirm
│
├── 06 Commerce & Payments
│   ├── Paywall Plan Selection
│   ├── Product Listing
│   ├── Product Detail
│   ├── Cart
│   ├── Checkout
│   ├── Order Confirmation
│   └── Orders & Billing History
│
├── 07 Communication & Social
│   ├── Notifications Inbox
│   ├── Chat Messages
│   ├── Comments Reviews
│   ├── Contacts Invite Referral
│   └── Share Sheet
│
├── 08 Profile & Settings
│   ├── Profile View
│   ├── Edit Profile
│   ├── Settings Hub
│   ├── Account & Security
│   ├── Notification Preferences
│   ├── Privacy & Data
│   ├── Appearance
│   ├── Help & Support
│   ├── About & Legal
│   └── Logout & Delete Account
│
├── 09 System & Feedback States
│   ├── Empty State
│   ├── Loading Skeleton
│   ├── Error State
│   ├── Success Celebration
│   ├── Confirmation Dialog
│   ├── Toasts & Banners
│   └── Force Update
│
└── 10 Engagement & Growth
    ├── Rate the App
    ├── Streaks & Achievements
    ├── Rewards & Coupons
    ├── Notification Opt-in Primer
    └── What's New
```

## Notes

- **Categories 1–3, 5, 8, 9 are near-universal** — almost every app has them. Categories 6, 7, and 10 appear based on the business model (subscription vs e-commerce vs social).
- **Modals vs screens**: many of these (pickers, confirmations, share) usually ship as bottom sheets or dialogs rather than full screens — decide per pattern.
- Each screen's markdown file follows the same template: Purpose, Key Elements, States & Variations, Design Notes, Technical Considerations, References.
