# User Guard - Advanced Link & Behavior Analysis Platform

User Guard is a comprehensive security analysis dashboard that performs deep analysis on URLs and detects anomalies in user behavior patterns. The platform combines URL security scanning with advanced anomaly detection algorithms to identify suspicious activities and potential threats.

## Features

### 🔐 URL Security Analysis
- **SSL/HTTPS Validation**: Checks for secure protocol usage
- **Domain Reputation Scoring**: Evaluates domain trustworthiness (0-100%)
- **Phishing Detection**: Identifies known phishing domains and suspicious patterns
- **Domain Spoofing Detection**: Detects homograph attacks and look-alike domains
- **Suspicious TLD Detection**: Flags high-risk top-level domains

### 📊 Analytics & Visualization
- **Login Activity Charts**: Visualize login attempts over time (successful vs failed)
- **Behavior Trends**: Track user success/failure rates across different users
- **Anomaly Detection Charts**: Scatter plot visualization of detected anomalies with severity levels
- **Activity Timeline**: Real-time activity feed with status indicators

### 🚨 Anomaly Detection Module
- **Hybrid Approach**: Combines threshold-based rules with Machine Learning (Isolation Forest)
- **Detected Anomalies**:
  - Unusual login times (outside user's normal pattern)
  - Multiple failed login attempts
  - Suspicious IP address changes
  - Unusual access patterns (ML-based)
- **Severity Levels**: Low, Medium, High, Critical

### 🔔 Alert System
- **Real-time Alerts**: Instant notifications for suspicious activities
- **Color-coded Severity**: Visual indicators (Green/Yellow/Red)
- **Alert Dashboard**: Dedicated alerts panel with dismissible notifications
- **Alert Types**: Phishing warnings, suspicious activity, status updates

## Architecture

### Technology Stack
- **Frontend**: Next.js 16, React 19, Tailwind CSS
- **Backend**: Next.js API Routes
- **Database**: Supabase (PostgreSQL)
- **Charts**: Recharts
- **Anomaly Detection**: Python with scikit-learn (Isolation Forest)
- **Authentication**: Supabase Auth

### Database Schema

#### Tables
- **links_analyzed**: Stores URL analysis results
- **user_activity**: Logs user login/access activities
- **anomalies**: Detected anomalies with severity levels
- **alerts**: System alerts for suspicious activities
- **user_baselines**: User behavior baselines for comparison

## Getting Started

### Prerequisites
- Node.js 18+ and pnpm
- Supabase account with PostgreSQL database
- Environment variables configured

### Installation

1. **Clone and install dependencies**:
   ```bash
   pnpm install
   ```

2. **Set up environment variables**:
   Create a `.env.local` file with:
   ```
   NEXT_PUBLIC_SUPABASE_URL=your_supabase_url
   NEXT_PUBLIC_SUPABASE_ANON_KEY=your_anon_key
   SUPABASE_SERVICE_ROLE_KEY=your_service_role_key
   ```

3. **Initialize the database**:
   The app automatically initializes the database on first run. Alternatively, run:
   ```bash
   pnpm run dev
   ```
   Then visit `http://localhost:3000` - the `/api/init` endpoint will be called automatically.

4. **Optional: Manual database setup**:
   ```bash
   # Using the SQL scripts
   node scripts/setup_db.js
   ```

### Running the Application

```bash
# Development mode
pnpm dev

# Build for production
pnpm build

# Start production server
pnpm start
```

Visit `http://localhost:3000` to access the dashboard.

## Usage

### Analyzing a URL

1. **Enter a URL** in the input field at the top
2. **Click "Analyze"** or press Enter
3. **View Results**:
   - Risk assessment with trust score
   - SSL/HTTPS status
   - Phishing risk indicators
   - Associated user activities
   - Detected anomalies
   - Active alerts

### Dashboard Navigation

- **Overview Tab**: Quick statistics and recent activities
- **Analytics Tab**: Login activity and behavior trend charts
- **Anomalies Tab**: Detailed anomaly detection results and severity analysis
- **Alerts Tab**: All system alerts with severity levels

### Demo Links

Pre-configured demo URLs to test the platform:
- `https://github.com/vercel/next.js` (Safe)
- `https://www.amazon.com` (Safe)
- `https://stackoverflow.com` (Safe)
- `https://suspicious-bank-login.tk` (High Risk)

## API Endpoints

### POST /api/analyze
Analyzes a URL and returns security assessment + associated activities + anomalies.

**Request**:
```json
{
  "url": "https://example.com"
}
```

**Response**:
```json
{
  "url": "https://example.com",
  "domain": "example.com",
  "sslValid": true,
  "domainScore": 0.95,
  "isPhishingRisk": false,
  "securitySummary": "Trusted domain - appears to be safe",
  "riskLevel": "safe",
  "activities": [...],
  "anomalies": [...],
  "alerts": [...]
}
```

### GET /api/init
Initializes the database with schema and demo data.

## Anomaly Detection

### Threshold-Based Rules
- **Failed Attempts**: 3+ failed logins trigger "high" severity
- **Unusual Time**: Logins outside user's typical 4-hour window
- **Suspicious IP**: Logins from IPs not in user's baseline

### Machine Learning (Isolation Forest)
- Trained on historical access duration patterns
- Detects statistical outliers in user behavior
- Confidence score provided for each anomaly

## Database Diagram

```
links_analyzed (main entity)
    ├── user_activity (many-to-one)
    │   └── anomalies (many-to-one)
    │       └── alerts (many-to-one)
    └── alerts (many-to-one, direct from link)
    
user_baselines (reference data for anomaly detection)
```

## Security Considerations

- ✅ HTTPS enforced for database connections
- ✅ Row-Level Security (RLS) ready in Supabase
- ✅ Service Role Key used only in backend API routes
- ✅ User data isolated per analysis session
- ✅ No sensitive data stored in browser

## Performance Optimizations

- Database indexes on frequently queried columns
- Analysis result caching (1-hour TTL)
- Lazy loading for chart data
- Efficient SQL queries with proper joins

## Future Enhancements

- [ ] User authentication & multi-user support
- [ ] Real-time WebSocket alerts
- [ ] Advanced ML models (Random Forest, Neural Networks)
- [ ] Browser history scanning
- [ ] Email link analysis
- [ ] Custom domain whitelisting/blacklisting
- [ ] Detailed reports and export functionality
- [ ] API rate limiting and abuse detection

## Troubleshooting

### Database Connection Issues
- Verify Supabase URL and keys in `.env.local`
- Check Supabase database is running
- Ensure firewall allows PostgreSQL connections

### Charts Not Displaying
- Verify data is being populated in database
- Check browser console for Recharts errors
- Ensure activities have valid `login_time` timestamps

### Anomaly Detection Not Working
- Verify user has activities in database
- Check anomaly detection script has sufficient data (5+ records)
- Review Python scikit-learn installation

## Contributing

1. Create a new branch for your feature
2. Make your changes
3. Test thoroughly
4. Submit a pull request

## License

MIT License - See LICENSE file for details

## Support

For issues or questions:
- Check the troubleshooting section
- Review the architecture documentation
- Inspect browser console logs
- Check server logs in terminal

---

**Built with ❤️ for security analysis and behavior monitoring**
