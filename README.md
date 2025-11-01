# Device Performance Monitoring 📊⚡

[![AppSheet](https://img.shields.io/badge/Built%20with-AppSheet-blue?style=flat-square&logo=google)](https://www.appsheet.com/)
[![Google Workspace](https://img.shields.io/badge/Powered%20by-Google%20Workspace-green?style=flat-square&logo=google)](https://workspace.google.com/)
[![License](https://img.shields.io/badge/License-Proprietary-red?style=flat-square)](LICENSE)
[![Winner](https://img.shields.io/badge/🏆-1st%20Place%20Winner-gold?style=flat-square)]()

> 🏆 **Winner of Hack With Google 2023** - $5,000 Prize  
> A comprehensive device performance monitoring system built with AppSheet and Google Workspace

---

## 📋 Table of Contents

- [Introduction](#introduction)
- [Project Overview](#project-overview)
- [Key Features](#key-features)
- [Implementation Details](#implementation-details)
  - [Overview Dashboard](#a-overview-dashboard)
  - [Interactive Map](#b-interactive-map)
  - [Audit Log](#c-audit-log)
  - [Performance Charts](#d-performance-charts)
  - [Automated Bots](#e-automated-bots)
- [Business Impact](#business-impact)
- [Getting Started](#getting-started)
- [GitHub-AppSheet Integration](#github-appsheet-integration)
- [Future Roadmap](#future-roadmap)
- [Contributing](#contributing)
- [Team & Acknowledgments](#team--acknowledgments)
- [License](#license)

---

## 🎯 Introduction
This project was developed during the **Hack With Google** event, sponsored by BeMyApp, Google, and Onix. The hackathon focused on expanding knowledge about AppSheet and other generative AI features in Google Workspace, AppSheet, and Google Cloud products.

**Event Details:**
- **Tracks:** Independent Developer & Emerging Mid-Market
- **Theme:** Manufacturing
- **Result:** 🏆 1st Place Winner - $5,000 Prize
- **Event Link:** [Hack With Google](https://googleworkspace-hackathon.bemyapp.com/)

<img width="869" alt="Hack With Google Event" src="https://github.com/khuynh22/Hack-With-Google/assets/57774658/52633ea6-729e-47e2-a593-5c78f1e1ef84">

---

## 🚀 Project Overview
Our project leverages AppSheet to create a comprehensive device performance monitoring system that revolutionizes how companies and electricians manage utility infrastructure. The solution enables real-time tracking of meters and transformers in the field, allowing immediate reporting of:

- ⚠️ Artificial outages
- 📉 Non-technical losses
- ❌ Errors and warnings
- 📍 Device status and location

### 💡 Core Value Proposition

By implementing features such as interactive views, dashboards, performance graphs, and automated actions, along with integrations for Google Maps, OCR, and intelligent bots, our solution:

- ⚡ **Streamlines Operations** - Real-time monitoring and automated workflows
- 💰 **Optimizes Budget** - Reduces operational costs by up to 15%
- 📊 **Maximizes Performance** - Data-driven insights for better decision-making
- 🌱 **Promotes Energy Conservation** - Monitors and reduces energy consumption
- 🎯 **Saves Time** - Potential to save 30% of workload for over 1 million electricians in the US

---

## 💼 Business Impact

Our solution delivers measurable benefits to three key stakeholder groups:

### 🏭 Device Manufacturing Companies

**Impact on Testing & Quality:**
- ⏱️ **25% reduction** in testing time
- 💰 **15% cost savings** on average
- 📈 Real-time performance analysis during manufacturing
- ✅ Instant adjustments and optimizations
- 🎯 Improved device quality and customer satisfaction

**How it works:** Manufacturing companies can implement our product during device testing phases, enabling immediate identification and resolution of issues during the production process.

### ⚡ Utility Companies / Electricity Providers

**Impact on Operations:**
- 📉 **20% reduction** in outage durations
- 🔧 Decreased downtime and maintenance costs
- 🔍 Proactive monitoring of meters, transformers, and circuits
- 🎯 Improved service reliability for customers
- 📊 Better asset management and lifecycle tracking

**How it works:** Real-time monitoring allows utility companies to identify and respond to issues before they escalate into major outages.

### 👷 Electricians & Field Technicians

**Impact on Productivity:**
- ⏰ **30 minutes saved** per inspection (via OCR automation)
- 📈 **15% productivity increase**
- 📱 Digital audit logs replace physical paperwork
- 🤖 Automated form filling reduces manual data entry
- ✅ Reduced human errors in reporting

**How it works:** OCR technology automatically fills inspection forms from meter photos, allowing electricians to focus on critical tasks and handle more service requests efficiently.

---

## ✨ Key Features
- 📊 **Real-time Dashboard** - Comprehensive overview of device performance metrics
- 🗺️ **Interactive Google Maps Integration** - Visual device status tracking with color-coded pins
- 📝 **Digital Audit Logs** - Paperless inspection and maintenance records
- 🤖 **OCR Technology** - Automatic data extraction from device photos
- 📈 **Performance Analytics** - Filterable charts and graphs for data-driven decisions
- 🔔 **Automated Alert System** - Email notifications for status changes
- 📱 **Mobile-First Design** - Optimized for field technicians on-the-go
- ☁️ **Cloud-Based Storage** - Google Sheets integration for centralized data management

---

## 🔧 Implementation Details

The project is built entirely on **Google Products** (G-Suite, AppSheet) where the main interface is developed using AppSheet and data is managed in Google Sheets.

### 📱 Mobile Application Interface

![Mobile Interface](https://github.com/khuynh22/Hack-With-Google/assets/57774658/bcceae53-1079-4487-a2da-dac9501f9bff)

### a) Overview Dashboard
**Landing Page with Key Metrics:**

The dashboard provides at-a-glance insights into your device network:
- ⚡ Average Power consumption
- 📊 Number of Active Meters
- ⚠️ Number of Errors/Warnings
- 🔌 Power Outages in the last 24 hours

Each metric card is interactive - click to view detailed information and drill down into specific data points.

### b) Interactive Map
**Google Maps API Integration with Status Indicators:**

![Map View](https://github.com/khuynh22/Hack-With-Google/assets/57774658/a5a6d199-0c9e-436b-bb22-b0dbdb8f75ea)

The Map tab integrates Google Maps API to display real-time device locations and status:

**Color-Coded Status System:**
- 🟢 **Green Pin** - Device operating normally
- 🟡 **Yellow Pin** - Warning status, requires inspection
- 🔴 **Red Pin** - Device down or broken, immediate action needed

**Interactive Features:**
- Click on any pin to view/edit device information
- Update device status in real-time
- View technician visit history
- Add specific notes for each device
- Track who last inspected or repaired the device

This enables both electricians and management to respond to status changes as quickly as possible, minimizing downtime.

<p align="center">
  <img src="https://github.com/khuynh22/Hack-With-Google/assets/57774658/49f02609-3f78-4753-9059-83f6b98bc907" width="45%" />
  <img src="https://github.com/khuynh22/Hack-With-Google/assets/57774658/b19576ab-7d46-4387-9877-35a4ef6b6d34" width="45%" />
</p>

### c) Audit Log
**Digital Paperwork Replacement:**

![Audit Log](https://github.com/khuynh22/Hack-With-Google/assets/57774658/3a3ec58f-dcbf-4dc7-9e6f-1ab45b86c59e)

Eliminates physical paperwork by allowing electricians to modify and submit inspection forms directly through the app.

**Smart Features:**
- 📝 **Autofill Functionality** - Time-efficient for managing thousands of meters
- 📷 **OCR Integration** - Take a photo and automatically extract device information
- ✍️ **Digital Signatures** - Sign and submit instantly
- ✅ **Validation** - Quick review before submission
- ⏱️ **Time Savings** - Average 30 minutes saved per inspection

**How OCR Works:**
1. Electrician takes a photo of the device
2. System automatically reads and fills form fields
3. Technician reviews, signs, and submits
4. Data syncs to cloud storage instantly

This reduces both time spent and human errors in data entry.

### d) Performance Charts
**Data Visualization & Analytics:**

![Performance Charts](https://github.com/khuynh22/Hack-With-Google/assets/57774658/0362d34b-3dda-4a35-be61-dec0c8195894)

Integrated with Google Sheets to build comprehensive visual analytics:

**Features:**
- 📊 Overall device performance metrics
- 📅 Filterable by date and time ranges
- 🔍 Filter by specific device ID
- 📈 Trend analysis over time
- 💡 Data-driven insights for decision-making

Perfect for management to track performance, identify patterns, and make informed operational decisions.

### e) Automated Bots
**Intelligent Alert System:**

![Automated Bots](https://github.com/khuynh22/Hack-With-Google/assets/57774658/1ee0c569-a679-41c1-a5a7-dd98c5627821)

**Automated Response System:**
- 🔴 Detects when device status changes from Green → Yellow or Red
- 📧 Automatically sends customized emails to assigned electricians
- ⚡ Includes device details, location, and priority level
- 💰 Saves significant costs through rapid response
- 🎯 Reduces manual monitoring requirements

This automated notification system ensures that issues are addressed immediately, minimizing downtime and preventing cascading failures.

---

## 🚀 Getting Started

### Prerequisites

- AppSheet account (free or paid)
- Google Workspace account
- Access to Google Sheets

### Quick Setup

1. **Create an AppSheet Account**
   - Visit [AppSheet.com](https://www.appsheet.com/) and sign up

2. **Access the Application**
   - Click this link: [Device Performance Monitoring App](https://www.appsheet.com/start/23ffc642-1353-4874-ac16-c94ab17b59ba)
   - Copy the app to your AppSheet account

3. **Configure Data Source**
   - The template data is available in this repository (`Template Data.xlsx`)
   - Upload to your Google Drive and connect to AppSheet
   - Alternatively, create a new Google Sheet with the same structure

4. **Customize Settings**
   - Configure email addresses for automated notifications
   - Set up Google Maps API key (if not already configured)
   - Adjust OCR settings based on your meter types

### Data Structure

The application uses the following main data tables:
- **Devices** - Meter and transformer information
- **Audit Logs** - Inspection and maintenance records
- **Users** - Electricians and administrators
- **Alerts** - Status change notifications

See `Template Data.xlsx` in this repository for the complete data schema.

---

## 🔗 GitHub-AppSheet Integration

While AppSheet doesn't natively support direct GitHub integration, you can connect your GitHub repository to AppSheet using several methods:

### Option 1: Automation Platforms (Recommended for Most Users)

**Using Integrately (No-Code Solution):**
1. Sign up at [Integrately.com](https://integrately.com/)
2. Connect your GitHub and AppSheet accounts
3. Create automation workflows:
   - New GitHub issue → Create AppSheet record
   - AppSheet form submission → Create GitHub issue
   - GitHub commit → Update AppSheet data

**Benefits:**
- ✅ No coding required
- ✅ Pre-built templates
- ✅ 1-click setup
- ✅ Suitable for basic automations

### Option 2: Data Connection via CData

**For Live GitHub Data in AppSheet:**
1. Use [CData Connect Cloud](https://www.cdata.com/) to connect GitHub
2. Authenticate with OAuth2
3. Connect AppSheet to CData as a data source
4. Build dashboards using live GitHub data (issues, PRs, commits)

**Use Cases:**
- 📊 Project management dashboards
- 🐛 Bug tracking integration
- 📈 Development metrics reporting

### Option 3: Advanced Workflow Automation

**Using n8n or Pipedream (For Custom Workflows):**
- Build custom automations with visual workflow builders
- Connect multiple services (GitHub, AppSheet, Slack, etc.)
- Trigger actions based on complex conditions
- Suitable for advanced integration needs

**Example Workflows:**
- Deploy app updates when code is merged
- Sync issue tracking between GitHub and AppSheet
- Automated testing and deployment pipelines

### Option 4: Google Apps Script (For Developers)

For maximum control, use Google Apps Script to create custom integrations:
```javascript
// Example: Webhook handler for GitHub events
function doPost(e) {
  var payload = JSON.parse(e.postData.contents);
  // Process GitHub webhook
  // Update AppSheet via API
}
```

### Integration Benefits for This Project

Integrating GitHub with this AppSheet application could enable:
- 📝 **Version Control** - Track changes to app configuration
- 🐛 **Issue Tracking** - Link device issues to GitHub issues
- 📊 **Documentation** - Keep technical docs in GitHub, sync to app
- 🔄 **Automated Backups** - Backup AppSheet data to GitHub
- 👥 **Collaboration** - Coordinate development between teams

For detailed setup instructions, see [INTEGRATION.md](./INTEGRATION.md) (coming soon).

---

## 🗺️ Future Roadmap

We're developing this product into a fully functional solution with enhanced features:

### Phase 1: Enhanced Reporting
- [ ] Comprehensive outage reports
- [ ] Detailed billing integration
- [ ] Custom report builder
- [ ] Export to multiple formats (PDF, Excel, CSV)

### Phase 2: Advanced Mapping
- [ ] **Interactive Device Connections** - Click on a device to see all connected devices
- [ ] **Geo-Navigation** - Direct routing for technicians to device locations
- [ ] **Heat Maps** - Visualize outage patterns and high-risk areas
- [ ] **Network Topology View** - Understand device relationships

### Phase 3: Expanded Device Support
- [ ] Solar panel monitoring
- [ ] Battery storage systems
- [ ] EV charging stations
- [ ] Smart grid integration

### Phase 4: Enhanced Analytics
- [ ] Interconnected dynamic charts
- [ ] Predictive maintenance algorithms
- [ ] AI-powered anomaly detection
- [ ] Energy consumption optimization

### Phase 5: Improved OCR
- [ ] Train OCR for additional meter types
- [ ] Read more data points (currently: voltage and power)
- [ ] Support for handwritten notes
- [ ] Multi-language support

### Phase 6: Enterprise Features
- [ ] Multi-tenant architecture
- [ ] Role-based access control
- [ ] API for third-party integrations
- [ ] SLA tracking and compliance

---

## 🤝 Contributing

We're looking to expand this product! If you're interested in collaborating, here's how you can help:

### Ways to Contribute

- 💡 **Ideas & Feedback** - Share your thoughts on new features
- 🐛 **Bug Reports** - Found an issue? Let us know!
- 📖 **Documentation** - Help improve our docs
- 💼 **Business Partnerships** - Interested in deploying this solution?

### Contact

For collaboration opportunities, please reach out:

- 📧 Email: timhuynhwork@gmail.com
- 💼 LinkedIn: [Connect with the team](https://www.linkedin.com/)
- 🐛 Issues: Use GitHub Issues for bug reports and feature requests

### Development Guidelines

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request with detailed description

---

## 👥 Team & Acknowledgments

### The Power Rangers Team 🦸

Special thanks to our amazing team who worked together to create this award-winning solution!

### Event Organizers & Mentors

We extend our gratitude to:

- **Hayden & Google Team** - Technical guidance and platform support
- **Lucas & BeMyApp Team** - Event organization and mentorship
- **Solange Jacob & Onix Team** - Industry insights and support

This hackathon provided an invaluable learning opportunity and platform to showcase innovative solutions for the manufacturing and utility sectors.

---

## 📄 License
**Copyright © 2023 Khang Nguyen Huynh. All rights reserved.**

This project is proprietary software. Unauthorized copying, modification, distribution, or use of this software, via any medium, is strictly prohibited without explicit permission from the copyright holder.

For licensing inquiries, please contact: timhuynhwork@gmail.com

---

## 📚 Additional Resources

- 📖 [AppSheet Documentation](https://help.appsheet.com/)
- 🎥 [Project Presentation](./Hack%20With%20Google.pptx) - Download the PowerPoint
- 📊 [Template Data](./Template%20Data.xlsx) - Sample data structure
- 🔗 [Live App Demo](https://www.appsheet.com/start/23ffc642-1353-4874-ac16-c94ab17b59ba)

---

## ⭐ Support This Project

If you find this project helpful or interesting:

- ⭐ Star this repository
- 🔄 Share with your network
- 💬 Provide feedback and suggestions
- 🤝 Consider collaboration opportunities

---

<p align="center">
  <strong>Built with ❤️ using AppSheet and Google Workspace</strong>
  <br>
  <sub>Hack With Google 2023 Winner 🏆</sub>
</p>
