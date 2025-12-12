# Arizona ServiceNow Service Portal Migration

## Overview
This folder contains the complete migration of the Arizona React application to ServiceNow Service Portal (Angular 1.5).

## Migration Status: Phase 1 - UI Only

**Current Phase:** UI Migration Complete  
**Next Phase:** Backend Integration (GlideRecord → ServiceNow Database)

## Architecture

### Original Architecture
```
React UI (TypeScript/JSX)
    ↓
.NET REST API
    ↓
MongoDB Database
```

### Target Architecture (Phase 1)
```
ServiceNow Service Portal (Angular 1.5)
    ↓
[Mock Data / Static Data]
```

### Target Architecture (Phase 2 - Future)
```
ServiceNow Service Portal (Angular 1.5)
    ↓
ServiceNow GlideRecord (Server-side)
    ↓
ServiceNow Database (Tables)
```

## Folder Structure

```
Arizona servicePortal Migration/
├─ portal-theme/                    # Portal-level theming
│  ├─ variables.scss                # CSS variables
│  └─ global-styles.scss            # Global styles
│
├─ pages/                           # Service Portal Page definitions
│  └─ landing-page.json             # Landing page configuration
│
└─ widgets/                         # Service Portal Widgets
   ├─ layout/                       # Layout widgets
   │  ├─ header-navigation/         # Header with navigation menu
   │  └─ footer-content/            # Footer with links and social media
   │
   ├─ landing/                      # Landing page section widgets
   │  ├─ landing-announcements/     # Announcements display
   │  ├─ landing-banner/            # Hero banner section
   │  ├─ landing-find-program/       # Find programs section
   │  ├─ landing-manage-program/     # Manage programs section
   │  └─ landing-help/              # Help section
   │
   └─ components/                   # Reusable component widgets
      ├─ az-button/                  # Button component (primary, secondary, outline, link)
      ├─ az-message/                 # Message/alert component
      └─ az-card/                    # Card container component
```

## Widget Structure

Each widget contains:
- `widget.html` - Angular 1.5 template
- `widget.client.js` - Angular 1.5 controller (client-side logic)
- `widget.server.js` - Server-side script (data fetching - mock for Phase 1)
- `widget.json` - Widget configuration and instance options
- `widget.scss` - Widget-specific styles

## Deployment Instructions

### 1. Portal Theme Setup
1. Navigate to **Service Portal → Themes**
2. Create or edit the theme
3. Add `portal-theme/variables.scss` to theme variables
4. Add `portal-theme/global-styles.scss` to theme CSS

### 2. Page Setup
1. Navigate to **Service Portal → Pages**
2. Import `pages/landing-page.json` or create manually
3. Configure page to use `header-navigation` and `footer-content` widgets

### 3. Widget Deployment
For each widget in `widgets/`:
1. Navigate to **Service Portal → Widgets**
2. Create new widget or update existing
3. Copy contents from corresponding widget files:
   - HTML → Template tab
   - Client Script → Client Script tab
   - Server Script → Server Script tab
   - SCSS → CSS tab
   - JSON → Widget configuration

### 4. Widget Instance Configuration
1. Add widgets to page containers
2. Configure widget instance options as needed
3. Set widget sizes and responsive breakpoints

## Key Conversions

### React → Service Portal Angular 1.5

#### State Management
- `useState()` → `c.data` object in widget controller
- `useEffect()` → `c.server.get().then()` for data loading
- React Router → Service Portal `$location` service

#### API Calls
- `apiService.get()` → Mock data in `widget.server.js` (Phase 1)
- Phase 2: Replace with GlideRecord queries

#### Styling
- TailwindCSS classes → Bootstrap 3 grid + custom SCSS
- CSS modules → Widget SCSS files
- Global styles → Portal theme files

#### Components
- React components → Service Portal widgets
- Props → Widget instance options
- Children → `ng-transclude` directive

## Language Support

All widgets support English (en) and Spanish (es) via:
- Language detection from URL query parameter `?language=en` or `?language=es`
- Translations stored in `widget.server.js`
- Language switching via header widget

## Responsive Design

- Desktop: 1025px and above
- Tablet: 769px - 1024px
- Mobile: 768px and below

Uses Bootstrap 3 grid system with custom breakpoints.

## Phase 1 Limitations

- **Mock Data Only**: All data is static/mock in `widget.server.js`
- **No Backend Integration**: No GlideRecord queries yet
- **No Database Operations**: All data is hardcoded

## Phase 2 TODO

1. Replace mock data with GlideRecord queries
2. Create ServiceNow tables for:
   - Announcements
   - Benefits/Programs
   - Applications
   - User data
3. Implement Scripted REST APIs if needed
4. Data migration from MongoDB to ServiceNow

## Testing Checklist

- [ ] Portal theme loads correctly
- [ ] All widgets render without errors
- [ ] Header navigation works (desktop and mobile)
- [ ] Footer links open correctly
- [ ] Language toggle switches content
- [ ] Responsive design works on all breakpoints
- [ ] All images load correctly
- [ ] Buttons trigger correct actions
- [ ] Announcements display (if any)
- [ ] Landing page sections display correctly

## Notes

- All widgets use Angular 1.5 syntax (no ES6 in server scripts)
- Server scripts use Rhino JavaScript engine
- Client scripts use Angular 1.5 framework
- Bootstrap 3 grid system is used for layout
- CSS variables are defined in portal theme

## Support

For questions or issues with this migration, contact the ServiceNow development team.

