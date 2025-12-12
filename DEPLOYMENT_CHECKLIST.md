# ServiceNow Service Portal Deployment Checklist

## Pre-Deployment

### 1. Portal Theme Setup
- [ ] Navigate to **Service Portal → Themes**
- [ ] Create new theme or select existing theme
- [ ] Add `portal-theme/variables.scss` content to **Theme Variables**
- [ ] Add `portal-theme/global-styles.scss` content to **Theme CSS**
- [ ] Save and activate theme

### 2. Widget Deployment Order

#### Step 1: Deploy Component Widgets First
- [ ] **az-button** widget
  - [ ] Copy `widget.html` to Template tab
  - [ ] Copy `widget.client.js` to Client Script tab
  - [ ] Copy `widget.server.js` to Server Script tab
  - [ ] Copy `widget.scss` to CSS tab
  - [ ] Configure instance options from `widget.json`
  - [ ] Test widget in widget editor

- [ ] **az-message** widget
  - [ ] Copy all files as above
  - [ ] Test widget

- [ ] **az-card** widget
  - [ ] Copy all files as above
  - [ ] Test widget

#### Step 2: Deploy Layout Widgets
- [ ] **header-navigation** widget
  - [ ] Copy all files
  - [ ] Configure instance options
  - [ ] Test navigation functionality
  - [ ] Test mobile menu
  - [ ] Test language toggle

- [ ] **footer-content** widget
  - [ ] Copy all files
  - [ ] Test footer links
  - [ ] Test scroll-to-top button
  - [ ] Test social media icons

#### Step 3: Deploy Landing Section Widgets
- [ ] **landing-announcements** widget
  - [ ] Copy all files
  - [ ] Test announcements display

- [ ] **landing-banner** widget
  - [ ] Copy all files
  - [ ] Test banner display
  - [ ] Test button clicks

- [ ] **landing-find-program** widget
  - [ ] Copy all files
  - [ ] Test program list display
  - [ ] Test "Browse programs" button

- [ ] **landing-manage-program** widget
  - [ ] Copy all files
  - [ ] Test manage programs list

- [ ] **landing-help** widget
  - [ ] Copy all files
  - [ ] Test help section display

### 3. Page Configuration
- [ ] Navigate to **Service Portal → Pages**
- [ ] Create new page or import `landing-page.json`
- [ ] Configure page:
  - [ ] Set page ID: `landing_page`
  - [ ] Set URL suffix: `landing`
  - [ ] Set header widget: `header-navigation`
  - [ ] Set footer widget: `footer-content`
- [ ] Add page containers:
  - [ ] Container 1: Announcements widget (optional)
  - [ ] Container 2: Banner widget
  - [ ] Container 3: Find Program widget
  - [ ] Container 4: Manage Program widget
  - [ ] Container 5: Help widget
- [ ] Configure widget instances on page
- [ ] Set widget sizes (12 columns for full width)

### 4. Asset Verification
- [ ] Verify all images exist in ServiceNow:
  - [ ] `/images/landingPageLogo.svg`
  - [ ] `/images/az_footer_logo.svg`
  - [ ] `/images/PageBannerIllustartion.svg`
  - [ ] `/images/footer-facebook.svg`
  - [ ] `/images/footer_twitter_X.svg`
  - [ ] `/images/footer-insta.svg`
  - [ ] `/images/IDme-Logo.svg`
  - [ ] `/images/programs/icons-CFS.svg`
  - [ ] `/images/programs/icons-FA.svg`
  - [ ] `/images/programs/icons-AHCCCS.svg`
  - [ ] `/images/programs/icons-AS.svg`
  - [ ] `/images/programs/icons-HS.svg`
  - [ ] `/images/programs/jobService.svg`
  - [ ] `/images/programs/icon-LP-GHA.svg`
  - [ ] `/images/programs/icon-FindDES.svg`
  - [ ] `/images/programs/icon-NeedHelp.svg`

### 5. Font Verification
- [ ] Verify OpenSans fonts are available:
  - [ ] OpenSans-Regular
  - [ ] OpenSans-Bold
  - [ ] OpenSans-SemiBold
- [ ] If fonts not available, add to theme or use web fonts

## Post-Deployment Testing

### Functional Testing
- [ ] Landing page loads without errors
- [ ] Header displays correctly (desktop)
- [ ] Header displays correctly (mobile)
- [ ] Navigation menu works
- [ ] Dropdown submenus work
- [ ] Mobile hamburger menu opens/closes
- [ ] Language toggle switches content
- [ ] Footer displays correctly
- [ ] Footer links open (test external links)
- [ ] Scroll-to-top button works
- [ ] Banner section displays
- [ ] Banner buttons work
- [ ] Find Program section displays all 6 programs
- [ ] Manage Program section displays all 3 items
- [ ] Help section displays all 3 items
- [ ] All images load correctly
- [ ] Responsive design works on mobile
- [ ] Responsive design works on tablet
- [ ] Responsive design works on desktop

### Language Testing
- [ ] Default language (English) displays correctly
- [ ] Language toggle to Spanish works
- [ ] All text switches to Spanish
- [ ] Language persists in URL
- [ ] Page reload maintains language

### Accessibility Testing
- [ ] All images have alt text
- [ ] All buttons have aria-labels
- [ ] Keyboard navigation works
- [ ] Focus indicators visible
- [ ] Screen reader compatibility
- [ ] Color contrast meets WCAG AA

### Browser Testing
- [ ] Chrome (latest)
- [ ] Firefox (latest)
- [ ] Safari (latest)
- [ ] Edge (latest)
- [ ] Mobile browsers (iOS Safari, Chrome Mobile)

## Known Issues & Fixes

### Issue: Widget not displaying
**Fix**: Check widget JSON configuration, ensure all files are copied correctly

### Issue: Styles not applying
**Fix**: Verify portal theme is active, check CSS variable definitions

### Issue: Images not loading
**Fix**: Verify image paths, check ServiceNow attachment table

### Issue: Language not switching
**Fix**: Check URL parameter handling, verify server script language detection

### Issue: Mobile menu not working
**Fix**: Check Angular scope bindings, verify CSS transitions

## Rollback Plan

If issues occur:
1. Deactivate portal theme
2. Remove widgets from page
3. Restore previous page configuration
4. Document issues for fix

## Support Contacts

- ServiceNow Admin: [Contact]
- Development Team: [Contact]
- Migration Lead: [Contact]

## Deployment Sign-Off

- [ ] Pre-deployment checklist complete
- [ ] All widgets tested individually
- [ ] Page tested end-to-end
- [ ] Accessibility verified
- [ ] Browser compatibility verified
- [ ] Ready for production deployment

**Deployed By**: _________________  
**Date**: _________________  
**Approved By**: _________________

