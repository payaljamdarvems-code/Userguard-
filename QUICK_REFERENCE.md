# User Guard 2.0 - Quick Reference Guide

## Getting Started (30 seconds)

1. **Open Browser**: http://localhost:3000
2. **See Futuristic Dashboard** with glowing neon elements
3. **Paste a URL** (or click demo buttons)
4. **Click "SCAN NOW"** button
5. **View Results** with color-coded risk assessment

---

## Quick Test URLs

### ✅ Safe Domain
```
https://github.com
→ GREEN badge
→ SECURE status
→ 100% trust score
```

### 🚨 Phishing Domain
```
https://paypal-verify.tk
→ RED badge
→ THREAT DETECTED
→ 0% trust score
```

### ✅ Normal Domain
```
https://google.com
→ GREEN badge
→ SECURE status
→ 100% trust score
```

---

## Dashboard Navigation

### Four Main Tabs

1. **OVERVIEW** 
   - Security analysis matrix
   - Activity timeline
   - Real-time metrics

2. **ANALYTICS**
   - Login activity chart
   - Behavior trends
   - User patterns

3. **ANOMALIES**
   - Threat visualization
   - Risk scoring
   - Severity levels

4. **ALERTS**
   - Security alerts
   - Color-coded severity
   - Dismissible items

---

## Color Meanings

| Color | Meaning |
|-------|---------|
| 🟢 Cyan (#00d9ff) | Safe / Normal / Active |
| 🟡 Magenta (#ff00ff) | Warning / Medium Risk |
| 🔴 Red (#ff0055) | Critical / Threat |
| 🟢 Green (#00ff88) | Success / Secure |
| 🟠 Orange (#ffaa00) | Caution / Review |

---

## Features at a Glance

### URL Analysis
- ✅ SSL validation
- ✅ Domain reputation (0-100%)
- ✅ Phishing detection
- ✅ Suspicious TLD check
- ✅ Security summary

### Dashboard
- ✅ 4 stat cards with animations
- ✅ Interactive charts
- ✅ Real-time alerts
- ✅ Activity timeline
- ✅ Severity indicators

### Design
- ✅ Cyberpunk aesthetic
- ✅ Glowing animations
- ✅ Smooth transitions
- ✅ Responsive layout
- ✅ Dark theme

---

## Common Actions

### Analyze a URL
```
1. Click input field (glowing border appears)
2. Type or paste URL
3. Press Enter or click "SCAN NOW"
4. View results instantly
```

### Try Demo
```
1. Click [GitHub] [Phishing] or [Google]
2. Analyze completes automatically
3. See different risk levels
```

### Switch Dashboard View
```
1. Click any tab: > OVERVIEW, > ANALYTICS, > ANOMALIES, > ALERTS
2. View updates smoothly
3. Explore different data
```

### Review Activity
```
1. Go to OVERVIEW tab
2. Scroll to "ACTIVITY TIMELINE"
3. See event history
4. Note timestamps & results
```

### Check Charts
```
1. Go to ANALYTICS tab
2. View LOGIN ACTIVITY chart (bar chart)
3. View BEHAVIOR TRENDS chart (area chart)
4. Hover for tooltips
```

### See Threats
```
1. Go to ANOMALIES tab
2. View scatter plot
3. Check severity colors (cyan/pink/red)
4. Click points for details
```

---

## Mobile Usage

### Mobile Features
- ✅ Full responsive design
- ✅ Touch-friendly buttons
- ✅ Readable at all sizes
- ✅ Optimized spacing
- ✅ Smooth animations

### Mobile Tips
1. Use landscape for better charts
2. Tap buttons with full finger
3. Swipe to navigate tabs
4. Pinch to zoom if needed

---

## Keyboard Shortcuts

| Key | Action |
|-----|--------|
| Enter | Submit URL (from input field) |
| Tab | Navigate elements |
| Tab + Enter | Activate buttons |
| Esc | May dismiss modals (if any) |

---

## Performance Tips

### For Best Experience
1. Use modern browser (Chrome, Firefox, Safari, Edge)
2. Ensure JavaScript is enabled
3. Allow enough vertical space (1024px+ recommended)
4. Use stable internet connection
5. Clear cache if styles look wrong

### Optimize Performance
- Disable heavy browser extensions
- Use hardware acceleration
- Close unnecessary tabs
- Update browser to latest

---

## Troubleshooting

### Page Not Loading
```
✓ Check URL: http://localhost:3000
✓ Refresh browser (Ctrl+R / Cmd+R)
✓ Clear cache (Ctrl+Shift+Del)
✓ Restart dev server
```

### Chart Not Showing
```
✓ Wait for page to fully load
✓ Check browser console (F12)
✓ Ensure JavaScript enabled
✓ Try different browser
```

### Button Not Responding
```
✓ Check if URL is entered
✓ Wait for current analysis
✓ Refresh page
✓ Try demo button instead
```

### Colors Look Wrong
```
✓ Check monitor color profile
✓ Ensure dark theme enabled
✓ Refresh browser cache
✓ Try different browser
```

---

## File Structure Quick Ref

```
/app
  page.tsx              ← Main page (hero + input)
  globals.css           ← Color theme + animations
  layout.tsx            ← Layout wrapper
  /api
    /analyze            ← Analysis endpoint

/components
  dashboard.tsx         ← Results dashboard
  alerts-panel.tsx      ← Alert display
  activity-timeline.tsx ← Event log
  /charts
    login-activity-chart.tsx
    behavior-trends-chart.tsx
    anomaly-detection-chart.tsx
```

---

## Keyboard Navigation

### Tab Through Elements
- Input field
- SCAN button
- Demo buttons
- Tab buttons
- Chart elements

### Activate with Space/Enter
- Buttons
- Tab navigation
- Interactive elements

---

## Accessibility Features

✅ **Screen Reader Support**
- Semantic HTML
- ARIA labels
- Alt text on icons

✅ **High Contrast**
- WCAG AA compliant
- Clear text/background
- Color + icon indicators

✅ **Keyboard Navigation**
- Tab between elements
- Enter to activate
- Logical tab order

---

## Customization Basics

### Change Primary Color
Edit `/app/globals.css`:
```css
--primary: #00d9ff;     /* Change this value */
--accent: #00d9ff;      /* And this */
```

### Adjust Animation Speed
Edit keyframe animations:
```css
animation: fadeIn 0.5s;  /* Change 0.5s to desired time */
```

### Modify Text Content
Edit component JSX files:
```jsx
<h1>USER GUARD</h1>  // Edit header text
```

---

## Browser Console

### Check Logs
1. Open DevTools (F12 or Cmd+Opt+I)
2. Go to Console tab
3. Look for [v0] prefixed logs
4. Check for errors/warnings

### Debug Mode
```javascript
// Check in console:
console.log([v0] messages show progress
```

---

## API Endpoints

### Analyze URL
```bash
curl -X POST http://localhost:3000/api/analyze \
  -H "Content-Type: application/json" \
  -d '{"url":"https://example.com"}'
```

Response:
```json
{
  "url": "https://example.com",
  "domain": "example.com",
  "riskLevel": "safe",
  "domainScore": 1,
  "isPhishingRisk": false,
  "securitySummary": "..."
}
```

---

## Stats Display

### Four Metrics Shown
1. **TOTAL ACTIVITIES**: Event count
2. **ANOMALIES**: Detected threats
3. **ACTIVE ALERTS**: Critical items
4. **SECURE SCORE**: Trust percentage

### Color Coding
- 🟦 Cyan for counts
- 🟥 Red for threats
- 🟨 Orange for caution
- 🟢 Green for success

---

## Getting Help

### Documentation Files
- `FUTURISTIC_REDESIGN.md` - Design details
- `SHOWCASE.md` - Feature showcase
- `TRANSFORMATION_COMPLETE.md` - Technical summary
- This file - Quick reference

### Inspect Code
- Read component comments
- Check globals.css for styles
- Review API implementations
- Explore chart configurations

---

## Version Info

- **Version**: 2.0 - Futuristic Edition
- **Status**: Production Ready ✅
- **Last Updated**: 2024
- **Browser Support**: All modern browsers

---

## Quick Links

- Home: http://localhost:3000
- API Test: POST to `/api/analyze`
- Docs: See .md files in root
- Code: Inspect `/app` and `/components`

---

## Remember

✨ **User Guard is designed to:**
- Quickly analyze URL security
- Detect threats and anomalies
- Provide professional dashboard
- Look futuristic and impressive
- Work on all devices

🛡️ **Perfect for:**
- Security analysis
- Threat detection
- User behavior monitoring
- Professional presentations
- Security awareness

---

**That's it!** You're ready to use User Guard 2.0. 
Start analyzing links now! 🚀

