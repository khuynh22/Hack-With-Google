# Setup Guide - Device Performance Monitoring

This guide will walk you through setting up the Device Performance Monitoring application from scratch.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Quick Start](#quick-start)
- [Detailed Setup](#detailed-setup)
- [Configuration](#configuration)
- [Testing Your Setup](#testing-your-setup)
- [Troubleshooting](#troubleshooting)
- [Next Steps](#next-steps)

---

## Prerequisites

Before you begin, ensure you have:

### Required Accounts

- ✅ **Google Account** - For accessing Google Workspace
- ✅ **AppSheet Account** - Free or paid tier ([Sign up here](https://www.appsheet.com/))
- ✅ **Google Drive Access** - For storing data

### Recommended Tools

- 📱 Mobile device (iOS/Android) - For testing mobile features
- 💻 Desktop computer - For setup and configuration
- 🌐 Modern web browser - Chrome, Firefox, or Safari

### Knowledge Level

- ⭐ **Beginner** - No coding required for basic setup
- ⭐⭐ **Intermediate** - For customization and advanced features
- ⭐⭐⭐ **Advanced** - For integrations and custom development

---

## Quick Start

Get up and running in 5 minutes:

### Step 1: Create AppSheet Account

1. Visit [AppSheet.com](https://www.appsheet.com/)
2. Click "Get Started" or "Sign Up"
3. Use your Google account to sign in
4. Complete the registration process

### Step 2: Copy the App

1. Click this link: [Device Performance Monitoring App](https://www.appsheet.com/start/23ffc642-1353-4874-ac16-c94ab17b59ba)
2. Click "Copy app" button
3. Choose your account
4. Name your copy (e.g., "My Device Monitor")

### Step 3: Set Up Data

1. Download [`Template Data.xlsx`](./Template%20Data.xlsx) from this repository
2. Upload to your Google Drive
3. In AppSheet, go to Data → Data Sources
4. Click "Add" and select the uploaded file
5. Grant necessary permissions

### Step 4: Test the App

1. Click "Preview" in AppSheet
2. Explore the interface
3. Try creating a test device
4. Check the map view
5. Test the audit log

**Congratulations! 🎉** Your basic setup is complete.

---

## Detailed Setup

For a more comprehensive setup with customization:

### Part 1: Account Setup (10 minutes)

#### 1.1 Create Google Workspace (If Needed)

If you don't have Google Workspace:

1. Visit [Google Workspace](https://workspace.google.com/)
2. Choose a plan (Business Starter recommended)
3. Set up your domain (or use free Gmail account)
4. Create user accounts for your team

#### 1.2 Set Up AppSheet

**Free Tier:**
- Good for: Testing, personal use
- Limitations: Limited users, basic features

**Paid Tiers:**
- Starter: $5/user/month - Basic automation
- Core: $10/user/month - Full features
- Enterprise: Custom pricing - Advanced features

**Setup Steps:**

1. Go to [AppSheet Pricing](https://www.appsheet.com/pricing)
2. Choose your tier
3. Complete payment (if applicable)
4. Verify email address
5. Set up your workspace

### Part 2: Data Setup (20 minutes)

#### 2.1 Understanding the Data Structure

The app uses the following tables:

**Devices Table:**
```
- Device ID (Key, Text)
- Device Type (Text: Meter, Transformer, Circuit)
- Location (LatLong)
- Status (Text: Green, Yellow, Red)
- Voltage (Number)
- Power (Number)
- Last Inspection (DateTime)
- Assigned Electrician (Ref to Users)
- Notes (LongText)
```

**Audit Logs Table:**
```
- Log ID (Key, Text)
- Device ID (Ref to Devices)
- Electrician (Ref to Users)
- Inspection Date (DateTime)
- Status Before (Text)
- Status After (Text)
- Actions Taken (LongText)
- Photo (Image)
- Signature (Image)
```

**Users Table:**
```
- User ID (Key, Text)
- Name (Text)
- Email (Email)
- Role (Text: Admin, Electrician, Viewer)
- Phone (Phone)
- Active (Yes/No)
```

**Alerts Table:**
```
- Alert ID (Key, Text)
- Device ID (Ref to Devices)
- Alert Type (Text)
- Timestamp (DateTime)
- Acknowledged (Yes/No)
- Resolved (Yes/No)
```

#### 2.2 Prepare Your Data

**Option A: Use Template Data**

1. Download `Template Data.xlsx` from this repository
2. Open in Excel or Google Sheets
3. Review the sample data
4. Customize with your own data
5. Save the file

**Option B: Create New Google Sheet**

1. Go to [Google Sheets](https://sheets.google.com/)
2. Create new spreadsheet: "Device Monitoring Data"
3. Create sheets for each table:
   - Devices
   - AuditLogs
   - Users
   - Alerts
4. Add column headers (see structure above)
5. Add sample data (at least 3-5 rows per table)

#### 2.3 Upload and Connect Data

**Upload to Google Drive:**

1. Go to [Google Drive](https://drive.google.com/)
2. Create folder: "AppSheet Apps"
3. Upload your data file
4. Right-click → Share → Set permissions

**Connect to AppSheet:**

1. In AppSheet editor, click "Data"
2. Click "+ Add New Data"
3. Select "Google Sheets" (or Excel if using OneDrive)
4. Browse to your file
5. Select all sheets/tables
6. Click "Add to app"
7. Wait for import to complete

#### 2.4 Verify Data Import

1. Go to Data → Tables
2. Check each table has imported correctly
3. Verify column types are correct
4. Fix any errors or warnings

### Part 3: App Configuration (30 minutes)

#### 3.1 Configure Tables

**For Each Table:**

1. **Set Key Column:**
   - Data → Select table → Key Column
   - Choose unique identifier (usually ID field)

2. **Set Label Column:**
   - Choose what displays in lists (e.g., "Device ID" for Devices)

3. **Configure Column Types:**
   - Text, Number, Date, Image, etc.
   - Set appropriate types for each column

4. **Set Up References:**
   - Link tables together (e.g., Audit Log → Device)

#### 3.2 Configure Views

**Dashboard View:**

1. UX → Views → Dashboard
2. Type: Dashboard
3. Add cards for:
   - Average Power
   - Active Meters Count
   - Errors/Warnings Count
   - Outages (24 hours)

**Map View:**

1. UX → Views → Map
2. Type: Map
3. Location column: Device Location
4. Color based on: Status
5. Color rules:
   - Green = Status is "Green"
   - Yellow = Status is "Yellow"
   - Red = Status is "Red"

**List Views:**

1. Devices List:
   - Type: Table
   - Sort by: Device ID
   - Filter: Show active only

2. Audit Logs List:
   - Type: Table
   - Sort by: Inspection Date (descending)
   - Group by: Device

**Form Views:**

1. Device Form:
   - Type: Form
   - Show columns: All except system fields
   - Read-only: Device ID, Last Inspection

2. Audit Log Form:
   - Type: Form
   - Initial values: Current user, current date
   - Required fields: Device ID, Status

#### 3.3 Set Up Actions

**Action 1: Report Issue**

```
Name: Report Issue
For a record of: Devices
Do this: Create a new row in Alerts
Set values:
  - Device ID = [_THISROW].[Device ID]
  - Alert Type = "Manual Report"
  - Timestamp = NOW()
```

**Action 2: Complete Inspection**

```
Name: Complete Inspection
For a record of: AuditLogs
Do this: Set the values of some columns
Set these columns:
  - Status After = [Status After]
  - Inspection Date = NOW()
Then: Go to another view → Dashboard
```

**Action 3: Send Alert Email**

```
Name: Send Alert
For a record of: Devices
Do this: Send email
To: [Assigned Electrician].[Email]
Subject: Device Alert - [Device ID]
Body: 
  Device [Device ID] has changed to [Status] status.
  Location: [Location]
  Please investigate immediately.
```

#### 3.4 Configure Automation (Bots)

**Bot 1: Status Change Alert**

1. Automation → Bots → Create Bot
2. Name: "Status Change Monitor"
3. Event: Data Change → Devices → Updates Only
4. Condition: 
   ```
   [_THISROW_BEFORE].[Status] <> [_THISROW_AFTER].[Status]
   ```
5. Process: Run actions → Send Alert Email

**Bot 2: Daily Summary**

1. Create Bot: "Daily Summary"
2. Event: Schedule → Daily at 8:00 AM
3. Process: Send email with summary

**Bot 3: Create Audit Alert**

1. Create Bot: "Auto Alert on Status Change"
2. Event: Data Change → Devices
3. Condition: `[Status] = "Red"`
4. Process: Add row to Alerts table

#### 3.5 Enable Features

**Enable OCR:**

1. UX → Views → Audit Log Form
2. For "Photo" column
3. Enable: "Extract values with OCR"
4. Configure extraction rules:
   - Voltage → Look for numbers near "V"
   - Power → Look for numbers near "W" or "kW"

**Enable GPS:**

1. Data → Devices table → Location column
2. Type: LatLong
3. Enable: "Auto-capture location"

### Part 4: Security & Permissions (15 minutes)

#### 4.1 Set Up Users

1. **Add Users:**
   - Data → Users table
   - Add entries for your team members
   - Include: Name, Email, Role

2. **Enable Authentication:**
   - Settings → Security → Authentication
   - Turn on: Require sign-in
   - Choose: Google authentication

3. **Set User Permissions:**
   - Settings → Users → Whitelist
   - Add allowed email addresses
   - Or use: Anyone in domain

#### 4.2 Configure Access Levels

**Role-Based Security:**

```
Admin:
  - Can view all data
  - Can edit all data
  - Can manage users
  - Can configure app

Electrician:
  - Can view assigned devices
  - Can create audit logs
  - Can update device status
  - Cannot delete data

Viewer:
  - Can view dashboards
  - Can view reports
  - Cannot edit anything
```

**Implement with Expressions:**

1. Data → Security Filters
2. For Devices table:
   ```
   OR(
     [_USERROLE] = "Admin",
     AND(
       [_USERROLE] = "Electrician",
       [Assigned Electrician].[Email] = USEREMAIL()
     ),
     [_USERROLE] = "Viewer"
   )
   ```

### Part 5: Customization (Optional, 20 minutes)

#### 5.1 Branding

1. **App Name & Icon:**
   - Settings → Information
   - Name: Your company name
   - Icon: Upload logo

2. **Color Theme:**
   - UX → Brand
   - Primary color: Your brand color
   - Accent color: Complementary color

3. **Loading Screen:**
   - UX → Brand → Logo
   - Upload company logo

#### 5.2 Custom Formulas

**Calculate Days Since Last Inspection:**

```
Column: Days Since Inspection
Type: Number
Formula: 
  TODAY() - [Last Inspection]
```

**Determine Priority Level:**

```
Column: Priority
Type: Text
Formula:
  IFS(
    [Status] = "Red", "Critical",
    AND([Status] = "Yellow", [Days Since Inspection] > 7), "High",
    [Status] = "Yellow", "Medium",
    TRUE, "Low"
  )
```

#### 5.3 Advanced Features

**Predictive Alerts:**

Create a virtual column that predicts when maintenance is due:

```
Column: Predicted Maintenance Date
Type: Date
Formula:
  [Last Inspection] + 90
```

**Cost Tracking:**

Add columns to track maintenance costs and ROI.

---

## Configuration

### Environment Variables

If using integrations, set these up:

**AppSheet API:**
- App ID: Found in Settings → Integrations
- API Key: Generate in Account → API

**Google Maps:**
- API Key: [Google Cloud Console](https://console.cloud.google.com/)
- Enable: Maps JavaScript API, Geocoding API

**Email Settings:**
- SMTP: Use Google Workspace SMTP
- From Address: notifications@yourdomain.com

### Integration Settings

See [INTEGRATION.md](./INTEGRATION.md) for detailed integration setup.

---

## Testing Your Setup

### Functional Testing Checklist

**Dashboard:**
- [ ] Metrics display correctly
- [ ] Cards are clickable
- [ ] Data refreshes

**Map View:**
- [ ] Pins display at correct locations
- [ ] Colors match status
- [ ] Click on pin shows details
- [ ] Can edit from map

**Forms:**
- [ ] Can create new device
- [ ] Can create audit log
- [ ] OCR extracts data (if enabled)
- [ ] Validation works
- [ ] Required fields enforced

**Automation:**
- [ ] Status change triggers alert
- [ ] Email is sent correctly
- [ ] Alert appears in Alerts table

**Mobile:**
- [ ] App works on phone
- [ ] GPS captures location
- [ ] Camera works for photos
- [ ] Forms are mobile-friendly

### Test Scenarios

**Scenario 1: New Device Registration**

1. Open app
2. Navigate to Devices
3. Click "Add New"
4. Fill in all fields
5. Save
6. Verify device appears in list
7. Check on map

**Scenario 2: Field Inspection**

1. Navigate to map
2. Click on a device
3. Change status to "Yellow"
4. Create audit log
5. Take photo
6. Test OCR
7. Submit
8. Verify alert is sent

**Scenario 3: Emergency Alert**

1. Change device status to "Red"
2. Verify:
   - Email sent to electrician
   - Alert created
   - Dashboard updated
   - Bot triggered

---

## Troubleshooting

### Common Issues

#### Issue: Data Not Showing

**Symptoms:** Tables are empty or data doesn't appear

**Solutions:**
1. Check data source connection
2. Verify Google Sheets permissions
3. Sync data: Data → Sync
4. Check security filters

#### Issue: Map Not Displaying

**Symptoms:** Map view is blank or pins don't show

**Solutions:**
1. Verify location data format (lat, long)
2. Check Google Maps API key
3. Enable Maps API in Google Cloud
4. Check browser permissions for location

#### Issue: OCR Not Working

**Symptoms:** Photos don't extract data

**Solutions:**
1. Verify OCR is enabled for column
2. Check image quality
3. Ensure good lighting in photo
4. Configure extraction patterns
5. Test with clear, high-contrast images

#### Issue: Emails Not Sending

**Symptoms:** Alert emails don't arrive

**Solutions:**
1. Check email addresses are correct
2. Verify bot is enabled
3. Check bot conditions
4. Test email action manually
5. Check spam folders

#### Issue: App is Slow

**Symptoms:** Long load times, laggy interface

**Solutions:**
1. Reduce number of records
2. Add filters to views
3. Optimize formulas
4. Archive old data
5. Upgrade AppSheet tier

### Getting Help

**Support Resources:**

1. **AppSheet Documentation:**
   - [https://help.appsheet.com/](https://help.appsheet.com/)

2. **Community Forum:**
   - [https://community.appsheet.com/](https://community.appsheet.com/)

3. **YouTube Tutorials:**
   - Search for "AppSheet tutorials"

4. **Contact Project Team:**
   - Email: timhuynhwork@gmail.com

---

## Next Steps

After completing setup:

### 1. Production Deployment

- [ ] Import real device data
- [ ] Add all team members
- [ ] Configure production settings
- [ ] Set up backup schedules
- [ ] Document processes

### 2. Training

- [ ] Train electricians on mobile app
- [ ] Train admins on dashboard
- [ ] Create user guides
- [ ] Record training videos
- [ ] Set up support channel

### 3. Monitoring

- [ ] Set up usage monitoring
- [ ] Track key metrics
- [ ] Review bot logs
- [ ] Monitor email delivery
- [ ] Check data quality

### 4. Optimization

- [ ] Gather user feedback
- [ ] Identify bottlenecks
- [ ] Optimize slow views
- [ ] Add requested features
- [ ] Improve workflows

### 5. Integration

- [ ] Set up GitHub integration (see [INTEGRATION.md](./INTEGRATION.md))
- [ ] Connect to other systems
- [ ] Automate reporting
- [ ] Set up dashboards
- [ ] Enable analytics

### 6. Scaling

- [ ] Plan for growth
- [ ] Optimize data structure
- [ ] Add automation
- [ ] Improve performance
- [ ] Upgrade tier if needed

---

## Additional Resources

### Documentation

- 📖 [README.md](./README.md) - Project overview
- 🔗 [INTEGRATION.md](./INTEGRATION.md) - GitHub integration guide
- 🤝 [CONTRIBUTING.md](./CONTRIBUTING.md) - Contribution guidelines

### Templates

- 📊 [Template Data.xlsx](./Template%20Data.xlsx) - Sample data structure
- 📈 [Hack With Google.pptx](./Hack%20With%20Google.pptx) - Project presentation

### Support

- 💬 [GitHub Discussions](../../discussions) - Ask questions
- 🐛 [GitHub Issues](../../issues) - Report bugs
- 📧 Email: timhuynhwork@gmail.com

---

## Checklist

Use this checklist to ensure complete setup:

### Pre-Setup
- [ ] Google account created
- [ ] AppSheet account created
- [ ] Downloaded template data

### Data Setup
- [ ] Data uploaded to Google Drive
- [ ] Connected to AppSheet
- [ ] Tables configured
- [ ] Sample data added

### App Configuration
- [ ] Views configured
- [ ] Actions created
- [ ] Bots enabled
- [ ] Security set up

### Testing
- [ ] Functional tests passed
- [ ] Mobile app tested
- [ ] Automation working
- [ ] Emails sending

### Deployment
- [ ] Real data imported
- [ ] Users added
- [ ] Training completed
- [ ] Documentation created

---

<p align="center">
  <strong>Setup complete! Start monitoring your devices. 📊⚡</strong>
  <br>
  <sub>Need help? Contact timhuynhwork@gmail.com</sub>
</p>
