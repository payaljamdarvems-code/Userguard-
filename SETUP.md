# User Guard Setup Guide

## Quick Start (5 minutes)

### Step 1: Install Dependencies
```bash
cd /vercel/share/v0-project
pnpm install
```

### Step 2: Configure Environment Variables
The Supabase integration should have automatically set your environment variables. Verify they exist in your project settings:

Required variables:
- `NEXT_PUBLIC_SUPABASE_URL` - Your Supabase project URL
- `NEXT_PUBLIC_SUPABASE_ANON_KEY` - Public anonymous key
- `SUPABASE_SERVICE_ROLE_KEY` - Service role key (for backend)

### Step 3: Start Development Server
```bash
pnpm dev
```

The app will automatically:
1. Initialize Supabase database schema
2. Seed demo data for testing
3. Be available at `http://localhost:3000`

### Step 4: Test the Application
1. Open `http://localhost:3000` in your browser
2. Try one of the demo links:
   - `https://github.com/vercel/next.js` (should show as Safe)
   - `https://suspicious-bank-login.tk` (should show as Critical Risk)
3. View the analytics and alerts

## Manual Database Setup (Optional)

If automatic initialization doesn't work, run:

```bash
# Execute SQL schema creation
psql $POSTGRES_URL -f scripts/01_create_schema.sql

# Seed demo data
psql $POSTGRES_URL -f scripts/02_insert_demo_data.sql
```

Or use the Node.js setup script:
```bash
node scripts/setup_db.js
```

## Supabase Configuration

### Required Tables
The system automatically creates these tables:

1. **links_analyzed** - URL analysis results
2. **user_activity** - User behavior logs
3. **anomalies** - Detected anomalies
4. **alerts** - System alerts
5. **user_baselines** - Behavior baselines

### Database Structure
All tables are automatically created with:
- Primary keys
- Foreign key relationships
- Indexes for performance
- Timestamps for tracking

## Running in Production

### Build the Application
```bash
pnpm build
```

### Start Production Server
```bash
pnpm start
```

### Deploy to Vercel
```bash
# Install Vercel CLI
npm i -g vercel

# Deploy (automatically detects Next.js)
vercel deploy
```

## Troubleshooting

### Issue: "Missing environment variables"
**Solution**: 
- Check that Supabase integration is active in project settings
- Verify all required env vars are set in the Vars section
- Restart the dev server after adding variables

### Issue: "Database connection failed"
**Solution**:
- Verify Supabase is running and accessible
- Check `POSTGRES_URL` is correct
- Ensure service role key has admin permissions
- Try: `psql $POSTGRES_URL -c "SELECT 1"`

### Issue: "Tables don't exist"
**Solution**:
- Visit `http://localhost:3000/api/init` to trigger automatic setup
- Or manually run the SQL migration files
- Check Supabase dashboard for table creation errors

### Issue: "Demo data not loading"
**Solution**:
- Clear browser cache and reload
- Check if links_analyzed table has records: 
  ```sql
  SELECT COUNT(*) FROM links_analyzed;
  ```
- If empty, run `scripts/02_insert_demo_data.sql`

## File Structure

```
project/
├── app/
│   ├── page.tsx                 # Main dashboard
│   ├── layout.tsx               # Root layout
│   ├── globals.css              # Global styles
│   └── api/
│       ├── analyze/route.ts     # URL analysis endpoint
│       └── init/route.ts        # Database initialization
│
├── components/
│   ├── dashboard.tsx            # Main dashboard component
│   ├── alerts-panel.tsx         # Alerts display
│   ├── activity-timeline.tsx    # Activity history
│   └── charts/
│       ├── login-activity-chart.tsx
│       ├── behavior-trends-chart.tsx
│       └── anomaly-detection-chart.tsx
│
├── lib/
│   ├── url-analyzer.ts          # URL security analysis
│   └── analysis-cache.ts        # Result caching
│
├── scripts/
│   ├── 01_create_schema.sql     # Database schema
│   ├── 02_insert_demo_data.sql  # Demo data
│   ├── anomaly_detection.py     # ML anomaly detection
│   └── setup_db.js              # Database setup script
│
└── public/                       # Static assets
```

## Testing URLs

### Safe Domains (Expected: Green/Safe)
- `https://github.com/vercel/next.js`
- `https://www.amazon.com`
- `https://stackoverflow.com`

### High-Risk Domains (Expected: Red/Critical)
- `https://suspicious-bank-login.tk`
- `https://example-phishing-site.xyz`

## Next Steps

1. **Customize Analysis Rules**: Edit `lib/url-analyzer.ts` to add more security checks
2. **Add Authentication**: Use Supabase Auth to add user accounts
3. **Integrate Real Data**: Connect to actual login systems
4. **Deploy**: Push to GitHub and deploy via Vercel
5. **Monitor**: Set up alerts for high-risk activities

## Support Resources

- [Supabase Docs](https://supabase.com/docs)
- [Next.js Documentation](https://nextjs.org/docs)
- [Recharts Gallery](https://recharts.org/en-US)
- [Tailwind CSS](https://tailwindcss.com)

---

**Ready to secure your platform? Start analyzing links now!**
