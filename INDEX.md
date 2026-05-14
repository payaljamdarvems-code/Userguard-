# User Guard - Complete Index

## 📋 Documentation Files

### Getting Started
- **[README.md](./README.md)** - Complete feature overview and usage guide
  - Feature descriptions
  - Architecture overview
  - Getting started instructions
  - API endpoints
  - Database schema

- **[SETUP.md](./SETUP.md)** - Configuration and deployment guide
  - Quick start (5 minutes)
  - Environment setup
  - Database configuration
  - Production deployment
  - Troubleshooting

- **[PROJECT_SUMMARY.md](./PROJECT_SUMMARY.md)** - Project overview and technical details
  - Completed features checklist
  - Project structure
  - Technology stack
  - Data flow diagrams
  - Future enhancements

- **[.env.example](./.env.example)** - Environment variables template
  - Copy to `.env.local` and fill with your values
  - Supabase configuration
  - Database credentials

## 🗂️ Source Code Structure

### Frontend Components (`/components`)
- **dashboard.tsx** - Main dashboard with tabs
  - Overview, Analytics, Anomalies, Alerts views
  - Statistics cards
  - Activity timeline

- **alerts-panel.tsx** - Alert notifications
  - Severity color coding
  - Dismissible alerts
  - Alert history

- **activity-timeline.tsx** - User activity timeline
  - Success/failure indicators
  - IP and user agent display
  - Chronological ordering

- **charts/** - Data visualizations
  - `login-activity-chart.tsx` - Bar chart of logins by hour
  - `behavior-trends-chart.tsx` - Line chart of user trends
  - `anomaly-detection-chart.tsx` - Scatter plot of anomalies

### API Routes (`/app/api`)
- **analyze/route.ts** - URL analysis endpoint
  - Analyzes URLs for security
  - Fetches associated activities
  - Returns comprehensive report

- **init/route.ts** - Database initialization
  - Creates tables if they don't exist
  - Seeds demo data
  - Validates Supabase connection

### Pages (`/app`)
- **page.tsx** - Main dashboard UI
  - URL input form
  - Risk assessment display
  - Dashboard integration
  - Demo links

- **layout.tsx** - Root layout
  - Metadata and SEO
  - Font configuration
  - Theme colors

### Utilities (`/lib`)
- **url-analyzer.ts** - Security analysis engine
  - SSL validation
  - Domain reputation scoring
  - Phishing detection
  - Homograph attack detection
  - TLD analysis

- **analysis-cache.ts** - Result caching
  - Cache management
  - TTL-based expiration
  - Memory-based storage

### Scripts (`/scripts`)
- **01_create_schema.sql** - Database schema
  - Table definitions
  - Relationships
  - Indexes

- **02_insert_demo_data.sql** - Demo data
  - Sample URLs
  - Test activities
  - Baseline users

- **anomaly_detection.py** - ML anomaly detection
  - Isolation Forest implementation
  - Threshold-based rules
  - Hybrid detection

- **setup_db.js** - Database setup helper
  - SQL execution
  - Error handling

- **seed-db.ts** - TypeScript seeding
  - Type-safe data insertion

## 🚀 Quick Start Commands

```bash
# Install dependencies
pnpm install

# Start development server (auto-initializes DB)
pnpm dev

# Build for production
pnpm build

# Start production server
pnpm start
```

## 🌐 Application Routes

| Route | Type | Purpose |
|-------|------|---------|
| `/` | Page | Main dashboard |
| `/api/analyze` | POST | Analyze URL |
| `/api/init` | GET | Initialize database |

## 📊 Database Tables

### links_analyzed
```sql
id, url (unique), domain_name, ssl_valid, domain_reputation_score,
is_phishing_risk, security_summary, analysis_date, created_at, updated_at
```

### user_activity
```sql
id, link_id (FK), user_id, activity_type, ip_address, user_agent,
login_time, duration_seconds, success, created_at
```

### anomalies
```sql
id, activity_id (FK), anomaly_type, severity, anomaly_score,
description, detection_method, created_at
```

### alerts
```sql
id, anomaly_id (FK), link_id (FK), alert_type, severity, title,
message, is_read, created_at
```

### user_baselines
```sql
id, user_id (unique), avg_login_hour, common_ips[], common_user_agents[],
avg_failed_attempts, baseline_created_at, updated_at
```

## 🔧 Configuration Files

| File | Purpose |
|------|---------|
| `package.json` | Dependencies and scripts |
| `tsconfig.json` | TypeScript configuration |
| `tailwind.config.ts` | Tailwind CSS setup |
| `next.config.mjs` | Next.js configuration |
| `postcss.config.mjs` | CSS processing |

## 📦 Key Dependencies

| Package | Version | Purpose |
|---------|---------|---------|
| next | 16.2.0 | Framework |
| react | 19 | UI library |
| tailwindcss | 4.2.0 | Styling |
| @supabase/supabase-js | 2.104.1 | Database client |
| recharts | 2.15.0 | Charts library |
| lucide-react | 0.564.0 | Icons |
| zod | 3.24.1 | Validation |

## 🎯 Feature Checklist

### URL Security Analysis
- [x] SSL/HTTPS validation
- [x] Domain reputation scoring
- [x] Phishing detection
- [x] Domain spoofing detection
- [x] Suspicious TLD detection
- [x] Security summary generation

### Anomaly Detection
- [x] Threshold-based rules
- [x] Isolation Forest ML
- [x] Failed login detection
- [x] Unusual time detection
- [x] Suspicious IP detection
- [x] Access pattern detection
- [x] Severity classification

### Dashboard
- [x] Statistics cards
- [x] Login activity chart
- [x] Behavior trends chart
- [x] Anomaly scatter plot
- [x] Activity timeline
- [x] Alerts panel
- [x] Tab navigation

### Backend
- [x] URL analysis API
- [x] Database integration
- [x] Automatic initialization
- [x] Demo data seeding
- [x] Error handling

### Documentation
- [x] README with features
- [x] Setup guide
- [x] API documentation
- [x] Database schema docs
- [x] Troubleshooting guide

## 🔐 Security Measures

- Environment variables for secrets
- Service role key for backend only
- No sensitive data in client code
- SQL injection prevention (Supabase)
- HTTPS/SSL validation in analysis

## 📈 Performance Optimizations

- Database indexing on key columns
- Result caching with TTL
- Lazy component loading
- Recharts optimization
- API response compression

## 🧪 Testing

### Demo URLs Available
- Safe: github.com, amazon.com, stackoverflow.com
- Risky: suspicious-bank-login.tk, example-phishing-site.xyz

### Test Scenarios
- URL analysis accuracy
- Activity display
- Anomaly detection
- Alert generation
- Chart interactions

## 🔗 External Resources

- [Next.js Docs](https://nextjs.org/docs)
- [Supabase Docs](https://supabase.com/docs)
- [Recharts Gallery](https://recharts.org)
- [Tailwind CSS](https://tailwindcss.com)
- [React Documentation](https://react.dev)

## 📞 Troubleshooting

Common issues and solutions:

| Issue | Solution |
|-------|----------|
| Missing env vars | Check `.env.local` and project settings |
| DB connection failed | Verify Supabase URL and keys |
| Tables don't exist | Visit `/api/init` or check Supabase dashboard |
| Charts not showing | Ensure data exists in database |
| Build errors | Run `pnpm install` and rebuild |

## 🚀 Deployment

### Local Development
```bash
pnpm dev
# http://localhost:3000
```

### Production Build
```bash
pnpm build
pnpm start
```

### Vercel Deployment
```bash
vercel deploy
```

## 📅 Version History

- **v1.0.0** (Current)
  - Initial release
  - All core features implemented
  - Comprehensive documentation
  - Production-ready code

## 📝 Notes

- All timestamps are stored in UTC
- Risk levels: safe, warning, critical
- Severity levels: low, medium, high, critical
- Database uses PostgreSQL via Supabase
- Frontend is fully typed with TypeScript

## 🎓 Learning Path

1. Start with README.md for overview
2. Follow SETUP.md for installation
3. Check PROJECT_SUMMARY.md for architecture
4. Review source code in order:
   - components/
   - lib/
   - app/api/
   - scripts/
5. Experiment with the dashboard
6. Review and modify analysis rules

---

**User Guard - Comprehensive Link Analysis & Behavior Anomaly Detection**

For questions or issues, refer to the relevant documentation file above.
