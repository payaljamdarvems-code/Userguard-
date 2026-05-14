# User Guard - Complete Testing Guide

## How to Test the Application

### 1. Access the Application
Open your browser and go to: `http://localhost:3000`

You should see:
- Clean, professional hero section with gradient background
- URL input field with "Analyze" button
- Three feature cards (Security Check, Anomaly Detection, Real-time Alerts)
- Three demo URL buttons at the bottom

### 2. Test Safe Domains

#### Test Case 1: GitHub (Trusted Domain)
1. Click the "github.com" demo button
2. OR paste: `https://github.com`
3. Click "Analyze" button

**Expected Result**:
- ✓ Risk Level: **SAFE** (green badge)
- ✓ Trust Score: 100%
- ✓ SSL/TLS: ✓ Valid
- ✓ Domain Reputation: 100%
- ✓ Phishing Risk: None
- ✓ Activities, anomalies, and alerts should display in dashboard

#### Test Case 2: Google (Trusted Domain)
1. Click the "google.com" demo button
2. OR paste: `https://google.com`
3. Click "Analyze" button

**Expected Result**:
- ✓ Risk Level: **SAFE** (green badge)
- ✓ Trust Score: 100%
- ✓ SSL/TLS: ✓ Valid

### 3. Test Phishing Domains

#### Test Case 3: Phishing Domain Detection
1. Click the "phishing-site.tk" demo button
2. OR paste: `https://paypal-verify.tk`
3. Click "Analyze" button

**Expected Result**:
- ✓ Risk Level: **CRITICAL** (red badge)
- ✓ Trust Score: 0% (red)
- ✓ SSL/TLS: ✓ Valid (HTTPS still secure, but domain is malicious)
- ✓ Domain Reputation: 0%
- ✓ Phishing Risk: **Detected**
- ✓ Security Summary shows: "High-risk domain: Known phishing domain, Suspicious TLD, Contains phishing keywords"

#### Test Case 4: Manual Phishing Test
1. Paste: `https://suspicious-bank-login.tk`
2. Click "Analyze" button

**Expected Result**:
- ✓ Risk Level: **CRITICAL** (red badge)
- ✓ Multiple red flags detected

### 4. Test Dashboard Tabs

After running any analysis, test the following tabs:

#### Overview Tab
- Should show "Recent Activity" with a timeline
- Each activity card has:
  - Status badge (Success/Failed)
  - User ID and IP address
  - Timestamp
  - Duration in seconds

#### Analytics Tab
- **Login Activity Over Time**: Bar chart showing successful vs failed logins by hour
- **User Behavior Trends**: Area chart showing success/failure rates per user
- Both charts should have:
  - ✓ Gradient fills
  - ✓ Animated bars/areas
  - ✓ Interactive tooltips on hover
  - ✓ Legend

#### Anomalies Tab
- **Anomaly Detection**: Scatter plot showing detected anomalies
- Points color-coded by severity:
  - 🔴 Red = High severity
  - 🟡 Amber = Medium severity
  - 🔵 Blue = Low severity
- Hover to see anomaly details and score

#### Alerts Tab
- Security alerts panel showing:
  - Alert title and description
  - Severity badge (critical/warning/info)
  - Timestamp
  - Close button (X) to dismiss

### 5. Test UI/UX Features

#### Responsive Design
1. Open in full desktop view (> 1024px)
   - All three stat cards should display in a row
   - Four tabs should show in the TabsList

2. Resize to tablet view (768px - 1024px)
   - Layout should adapt gracefully
   - Text should remain readable

3. Resize to mobile view (< 768px)
   - Stat cards should stack vertically
   - Tabs should collapse to icons only
   - Input field should be mobile-friendly

#### Dark/Light Mode
- All colors should adapt properly
- Text contrast should remain high
- Charts should be readable in both modes

#### Interactive Elements
- Hover over stat cards → subtle shadow effect
- Hover over alert cards → shadow and highlight
- Hover over chart bars/lines → color intensification
- Demo URL buttons → color change on hover
- "New Analysis" button → returns to input screen

### 6. Test Loading States

1. Paste a URL and click "Analyze"
2. Watch for:
   - ✓ Button shows loading spinner
   - ✓ Button text changes to "Analyzing"
   - ✓ Button is disabled during loading
   - ✓ After completion, displays results

### 7. Test Error Handling

#### Test Case 5: Empty Input
1. Click "Analyze" without entering a URL
2. **Expected**: Error message: "Please enter a URL"

#### Test Case 6: Invalid URL
1. Paste: `not-a-url`
2. Click "Analyze"
3. **Expected**: Error message with details about invalid format

#### Test Case 7: Network Error (if backend is down)
1. Stop the dev server
2. Try to analyze a URL
3. **Expected**: Graceful error message

### 8. Browser Console Logs

Open browser DevTools (F12) and check the Console tab:

When analyzing a URL, you should see logs like:
```
[v0] Starting analysis for URL: https://github.com
[v0] Response status: 200
[v0] Analysis result received: {...}
```

For errors:
```
[v0] Analysis error: Error: Invalid URL format
```

### 9. Performance Testing

#### Chart Rendering
1. Switch between tabs rapidly
2. Charts should animate smoothly
3. No lag or stuttering observed

#### Data Loading
1. Multiple analysis requests
2. Each should complete in < 2 seconds
3. No memory leaks (check DevTools Memory tab)

### 10. Color System Verification

**Safe Domain Colors**:
- Green badge
- Green security icons
- Green text highlights

**Warning Colors**:
- Amber/orange badges
- Amber alert boxes
- Amber icons

**Critical Colors**:
- Red badges
- Red alert boxes
- Red error messages

### Expected Features Checklist

- [ ] Hero page displays with gradient background
- [ ] URL input accepts and validates URLs
- [ ] Demo buttons work and trigger analysis
- [ ] Safe domains show green "SAFE" badge
- [ ] Phishing domains show red "CRITICAL" badge
- [ ] Dashboard appears after analysis
- [ ] Stats cards display with proper colors and gradients
- [ ] Charts render with animations
- [ ] Tabs switch smoothly between views
- [ ] Alerts display with severity colors
- [ ] Activity timeline shows historical data
- [ ] New Analysis button returns to input screen
- [ ] Responsive design works on mobile/tablet/desktop
- [ ] Dark mode styling is correct
- [ ] No console errors

## Sample Test Scenarios

### Scenario 1: User Checks Safe Website
1. User visits site
2. Pastes: `https://github.com`
3. Clicks analyze
4. Gets confirmation website is safe
5. Reviews activity and behavior trends
6. **Expected outcome**: Green badge, 100% trust, no alerts

### Scenario 2: User Suspects Phishing
1. User receives suspicious link
2. Pastes: `https://paypal-verify.tk`
3. Clicks analyze
4. Gets instant warning: CRITICAL risk
5. Views security summary with reasons
6. Sees multiple red alerts
7. **Expected outcome**: Red badges, 0% trust, security alerts displayed

### Scenario 3: User Analyzes Multiple URLs
1. User analyzes: `https://google.com` → SAFE
2. Clicks "New Analysis"
3. User analyzes: `https://suspicious-bank-login.tk` → CRITICAL
4. Clicks "New Analysis"
5. User analyzes: `https://amazon.com` → SAFE
6. **Expected outcome**: Each analysis is isolated and accurate

## Troubleshooting

### Issue: Page won't load
- **Solution**: Check server is running with `pnpm dev`
- Verify port 3000 is accessible

### Issue: Charts don't animate
- **Solution**: Check browser supports CSS animations
- Try a modern browser (Chrome, Firefox, Safari, Edge)

### Issue: Colors look different
- **Solution**: Check light/dark mode setting
- Clear browser cache
- Check color system in `globals.css`

### Issue: API returns error
- **Solution**: Check console logs for detailed error message
- Verify URL format is correct
- Restart dev server if needed

## Success Criteria

✅ **All tests pass** if:
1. Safe domains show SAFE badge and green colors
2. Phishing domains show CRITICAL badge and red colors
3. Dashboard displays all data correctly
4. Charts animate smoothly
5. No console errors
6. Responsive design works
7. All interactive elements respond properly
8. Loading states show correctly

## Notes

- Test data is generated dynamically for demo purposes
- Phishing detection uses heuristic rules, not real databases
- In production, would integrate with real threat intelligence APIs
- Database persistence can be added by connecting Supabase

---

**Ready to test? Visit http://localhost:3000 now!**
