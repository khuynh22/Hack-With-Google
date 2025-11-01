# GitHub-AppSheet Integration Guide

This guide provides detailed instructions for integrating your GitHub repository with AppSheet to enable automation, data synchronization, and enhanced collaboration.

## Table of Contents

- [Overview](#overview)
- [Integration Methods](#integration-methods)
- [Method 1: Using Integrately (No-Code)](#method-1-using-integrately-no-code)
- [Method 2: Using CData Connect Cloud](#method-2-using-cdata-connect-cloud)
- [Method 3: Using n8n Workflow Automation](#method-3-using-n8n-workflow-automation)
- [Method 4: Using Google Apps Script](#method-4-using-google-apps-script)
- [Use Cases for This Project](#use-cases-for-this-project)
- [Troubleshooting](#troubleshooting)
- [Best Practices](#best-practices)

---

## Overview

While AppSheet doesn't natively support direct GitHub integration, there are several effective methods to connect the two platforms. This enables:

- **Version Control** - Track configuration changes
- **Issue Tracking** - Link device issues to GitHub
- **Automation** - Trigger actions based on events
- **Data Sync** - Keep repositories and apps in sync
- **Collaboration** - Coordinate between development and operations teams

---

## Integration Methods

### Comparison Table

| Method | Complexity | Cost | Best For | Code Required |
|--------|-----------|------|----------|---------------|
| Integrately | ⭐ Low | $ Free-$$$ | Simple automations | ❌ No |
| CData | ⭐⭐ Medium | $$$ | Live data access | ❌ No |
| n8n/Pipedream | ⭐⭐⭐ Medium-High | $ Free-$$ | Custom workflows | ⚠️ Minimal |
| Apps Script | ⭐⭐⭐⭐ High | Free | Full control | ✅ Yes |

---

## Method 1: Using Integrately (No-Code)

**Best for:** Quick setup, simple automations, non-technical users

### Prerequisites

- Integrately account ([Sign up here](https://integrately.com/))
- AppSheet account with API access
- GitHub account with repository access

### Step-by-Step Setup

#### 1. Create an Integrately Account

1. Visit [Integrately.com](https://integrately.com/)
2. Sign up for a free account
3. Navigate to "Integrations"

#### 2. Connect GitHub

1. Click "Add App" → Search for "GitHub"
2. Click "Connect"
3. Authorize Integrately to access your GitHub account
4. Select the repositories you want to integrate

#### 3. Connect AppSheet

1. Click "Add App" → Search for "AppSheet"
2. Click "Connect"
3. Enter your AppSheet API credentials:
   - App ID: Found in AppSheet app settings
   - API Key: Generate in AppSheet Account Settings → Integrations
4. Test the connection

#### 4. Create Automation Workflows

**Example 1: GitHub Issue → AppSheet Record**

```
Trigger: New issue created in GitHub repository
Action: Add row to AppSheet table

Mapping:
- Issue Title → Device Description
- Issue Body → Notes
- Issue Labels → Status
- Created Date → Timestamp
```

**Example 2: AppSheet Audit Log → GitHub Issue**

```
Trigger: New row added to AppSheet "Audit Logs" table
Action: Create GitHub issue

Mapping:
- Device ID → Issue Title
- Audit Notes → Issue Body
- Status → Labels
- Electrician Name → Assignee
```

#### 5. Test Your Integration

1. Create a test issue in GitHub
2. Verify it appears in AppSheet
3. Create a test audit log in AppSheet
4. Verify the GitHub issue is created

### Integrately Pricing

- **Free Plan:** 100 tasks/month
- **Starter:** $19.99/month - 1,500 tasks
- **Professional:** $39.99/month - 10,000 tasks
- **Business:** Custom pricing

---

## Method 2: Using CData Connect Cloud

**Best for:** Live data access, reporting, dashboard integration

### Prerequisites

- CData Connect Cloud account
- GitHub Personal Access Token
- AppSheet account

### Step-by-Step Setup

#### 1. Set Up CData Connection

1. Sign up at [CData Connect Cloud](https://www.cdata.com/cloud/)
2. Create a new connection to GitHub:
   - Connection Type: GitHub
   - Authentication: OAuth2 or Personal Access Token
3. Configure permissions:
   - Read access to issues
   - Read access to repositories
   - Read access to pull requests

#### 2. Configure Data Models

Create virtual tables for GitHub data:

**Issues Table:**
```
Columns:
- issue_number (Integer)
- title (Text)
- state (Text)
- created_at (DateTime)
- updated_at (DateTime)
- assignee (Text)
- labels (Text)
```

**Commits Table:**
```
Columns:
- sha (Text)
- message (Text)
- author (Text)
- date (DateTime)
- repository (Text)
```

#### 3. Connect AppSheet to CData

1. In AppSheet, go to Data → Add Data Source
2. Select "Cloud Database"
3. Choose CData Connect Cloud
4. Enter connection credentials
5. Select the tables you want to import

#### 4. Build Dashboards

Create AppSheet views using GitHub data:

**Development Activity Dashboard:**
- Chart showing commits over time
- List of open issues
- Pull request status

**Integration Monitoring:**
- Failed integrations
- Sync status
- Last update times

### CData Pricing

Contact CData for enterprise pricing - typically starts at $99/month

---

## Method 3: Using n8n Workflow Automation

**Best for:** Complex workflows, multiple integrations, developers

### Prerequisites

- n8n installation (self-hosted or cloud)
- GitHub account
- AppSheet API credentials

### Step-by-Step Setup

#### 1. Install n8n

**Self-Hosted (Docker):**
```bash
docker run -it --rm \
  --name n8n \
  -p 5678:5678 \
  -v ~/.n8n:/home/node/.n8n \
  n8nio/n8n
```

**Cloud:** Sign up at [n8n.cloud](https://n8n.cloud/)

#### 2. Create GitHub Credentials

1. In n8n, go to Credentials → Add Credential
2. Select "GitHub API"
3. Choose authentication method:
   - **OAuth2** (recommended)
   - **Personal Access Token**
4. Test connection

#### 3. Create AppSheet Credentials

1. In n8n, go to Credentials → Add Credential
2. Select "HTTP Header Auth"
3. Add header:
   - Name: `ApplicationAccessKey`
   - Value: Your AppSheet API key

#### 4. Build Workflows

**Example Workflow: Sync Device Issues**

```yaml
Workflow: Device Issue Tracker

Trigger: Webhook (from AppSheet)
  ↓
Filter: Only "Error" or "Warning" status
  ↓
Transform: Format data for GitHub
  ↓
GitHub: Create Issue
  ↓
AppSheet: Update record with issue number
```

**n8n Workflow JSON (Example):**

```json
{
  "nodes": [
    {
      "name": "Webhook",
      "type": "n8n-nodes-base.webhook",
      "position": [250, 300],
      "parameters": {
        "path": "appsheet-device-alert"
      }
    },
    {
      "name": "GitHub",
      "type": "n8n-nodes-base.github",
      "position": [450, 300],
      "parameters": {
        "resource": "issue",
        "operation": "create",
        "repository": "Hack-With-Google",
        "title": "={{ $json.device_id }}: {{ $json.status }}",
        "body": "Device Status Alert\n\nDevice ID: {{ $json.device_id }}\nStatus: {{ $json.status }}\nLocation: {{ $json.location }}\nNotes: {{ $json.notes }}"
      }
    }
  ]
}
```

#### 5. Set Up AppSheet Webhooks

1. In AppSheet, create a bot
2. Set trigger: When device status changes
3. Set action: Call webhook
4. URL: Your n8n webhook URL
5. Method: POST
6. Body template:
```json
{
  "device_id": "<<[Device ID]>>",
  "status": "<<[Status]>>",
  "location": "<<[Location]>>",
  "notes": "<<[Notes]>>"
}
```

### n8n Pricing

- **Self-Hosted:** Free (open source)
- **Cloud Starter:** $20/month
- **Cloud Pro:** $50/month

---

## Method 4: Using Google Apps Script

**Best for:** Maximum control, custom logic, Google Workspace integration

### Prerequisites

- Google account
- GitHub Personal Access Token
- AppSheet API key
- Basic JavaScript knowledge

### Step-by-Step Setup

#### 1. Create Apps Script Project

1. Go to [script.google.com](https://script.google.com/)
2. Create new project: "GitHub-AppSheet Sync"
3. Enable required services:
   - Drive API
   - Sheets API

#### 2. Set Up GitHub API

Create a function to interact with GitHub:

```javascript
/**
 * GitHub API Configuration
 */
const GITHUB_TOKEN = 'your_github_personal_access_token';
const GITHUB_REPO = 'khuynh22/Hack-With-Google';
const GITHUB_API_BASE = 'https://api.github.com';

/**
 * Create GitHub Issue
 */
function createGitHubIssue(title, body, labels = []) {
  const url = `${GITHUB_API_BASE}/repos/${GITHUB_REPO}/issues`;
  
  const payload = {
    title: title,
    body: body,
    labels: labels
  };
  
  const options = {
    method: 'post',
    headers: {
      'Authorization': `token ${GITHUB_TOKEN}`,
      'Accept': 'application/vnd.github.v3+json'
    },
    contentType: 'application/json',
    payload: JSON.stringify(payload)
  };
  
  try {
    const response = UrlFetchApp.fetch(url, options);
    const issue = JSON.parse(response.getContentText());
    Logger.log('Created issue #' + issue.number);
    return issue;
  } catch (error) {
    Logger.log('Error creating issue: ' + error);
    return null;
  }
}

/**
 * Get GitHub Issues
 */
function getGitHubIssues(state = 'open') {
  const url = `${GITHUB_API_BASE}/repos/${GITHUB_REPO}/issues?state=${state}`;
  
  const options = {
    method: 'get',
    headers: {
      'Authorization': `token ${GITHUB_TOKEN}`,
      'Accept': 'application/vnd.github.v3+json'
    }
  };
  
  try {
    const response = UrlFetchApp.fetch(url, options);
    const issues = JSON.parse(response.getContentText());
    return issues;
  } catch (error) {
    Logger.log('Error fetching issues: ' + error);
    return [];
  }
}
```

#### 3. Set Up AppSheet API

```javascript
/**
 * AppSheet API Configuration
 */
const APPSHEET_APP_ID = 'your_app_id';
const APPSHEET_API_KEY = 'your_api_key';
const APPSHEET_API_BASE = 'https://api.appsheet.com/api/v2';

/**
 * Add Row to AppSheet
 */
function addAppSheetRow(tableName, rowData) {
  const url = `${APPSHEET_API_BASE}/apps/${APPSHEET_APP_ID}/tables/${tableName}/Action`;
  
  const payload = {
    Action: 'Add',
    Properties: {
      Locale: 'en-US'
    },
    Rows: [rowData]
  };
  
  const options = {
    method: 'post',
    headers: {
      'ApplicationAccessKey': APPSHEET_API_KEY,
      'Content-Type': 'application/json'
    },
    payload: JSON.stringify(payload)
  };
  
  try {
    const response = UrlFetchApp.fetch(url, options);
    const result = JSON.parse(response.getContentText());
    Logger.log('Added row to ' + tableName);
    return result;
  } catch (error) {
    Logger.log('Error adding row: ' + error);
    return null;
  }
}

/**
 * Get AppSheet Data
 */
function getAppSheetData(tableName) {
  const url = `${APPSHEET_API_BASE}/apps/${APPSHEET_APP_ID}/tables/${tableName}/Action`;
  
  const payload = {
    Action: 'Find',
    Properties: {
      Locale: 'en-US',
      Selector: 'Filter(TableName, true)'
    }
  };
  
  const options = {
    method: 'post',
    headers: {
      'ApplicationAccessKey': APPSHEET_API_KEY,
      'Content-Type': 'application/json'
    },
    payload: JSON.stringify(payload)
  };
  
  try {
    const response = UrlFetchApp.fetch(url, options);
    const data = JSON.parse(response.getContentText());
    return data;
  } catch (error) {
    Logger.log('Error getting data: ' + error);
    return null;
  }
}
```

#### 4. Create Sync Functions

```javascript
/**
 * Sync Device Alerts to GitHub
 */
function syncDeviceAlertsToGitHub() {
  // Get alerts from AppSheet
  const alerts = getAppSheetData('DeviceAlerts');
  
  if (!alerts || !alerts.Rows) {
    Logger.log('No alerts found');
    return;
  }
  
  // Filter for new, unsynced alerts
  const newAlerts = alerts.Rows.filter(alert => !alert['GitHub Issue Number']);
  
  // Create GitHub issues for each alert
  newAlerts.forEach(alert => {
    const title = `${alert['Device ID']}: ${alert['Status']}`;
    const body = `
**Device Alert**

- **Device ID:** ${alert['Device ID']}
- **Status:** ${alert['Status']}
- **Location:** ${alert['Location']}
- **Timestamp:** ${alert['Timestamp']}
- **Notes:** ${alert['Notes']}
- **Electrician:** ${alert['Assigned Electrician']}

---
*Auto-generated from AppSheet Device Performance Monitoring*
    `;
    
    const labels = [alert['Status'].toLowerCase(), 'device-alert'];
    
    const issue = createGitHubIssue(title, body, labels);
    
    if (issue) {
      // Update AppSheet with issue number
      // Note: This requires an update action
      Logger.log(`Created issue #${issue.number} for device ${alert['Device ID']}`);
    }
  });
}

/**
 * Sync GitHub Issues to AppSheet
 */
function syncGitHubIssuesToAppSheet() {
  const issues = getGitHubIssues('open');
  
  if (!issues || issues.length === 0) {
    Logger.log('No issues found');
    return;
  }
  
  // Filter for device-related issues
  const deviceIssues = issues.filter(issue => 
    issue.labels.some(label => label.name === 'device-alert')
  );
  
  // Add to AppSheet
  deviceIssues.forEach(issue => {
    const rowData = {
      'GitHub Issue Number': issue.number,
      'Title': issue.title,
      'Status': issue.state,
      'Created': issue.created_at,
      'URL': issue.html_url
    };
    
    addAppSheetRow('GitHubIssues', rowData);
  });
}

/**
 * Set up time-based trigger
 */
function createTriggers() {
  // Run sync every hour
  ScriptApp.newTrigger('syncDeviceAlertsToGitHub')
    .timeBased()
    .everyHours(1)
    .create();
    
  ScriptApp.newTrigger('syncGitHubIssuesToAppSheet')
    .timeBased()
    .everyHours(1)
    .create();
}
```

#### 5. Set Up Web App for Webhooks

```javascript
/**
 * Handle POST requests from AppSheet webhooks
 */
function doPost(e) {
  try {
    const data = JSON.parse(e.postData.contents);
    
    // Validate webhook
    if (data.event === 'device_status_change') {
      const title = `${data.device_id}: Status Changed to ${data.new_status}`;
      const body = `
**Device Status Change**

- **Device ID:** ${data.device_id}
- **Old Status:** ${data.old_status}
- **New Status:** ${data.new_status}
- **Location:** ${data.location}
- **Timestamp:** ${new Date().toISOString()}

---
*Auto-generated alert from AppSheet*
      `;
      
      const labels = [data.new_status.toLowerCase(), 'status-change'];
      const issue = createGitHubIssue(title, body, labels);
      
      return ContentService.createTextOutput(JSON.stringify({
        success: true,
        issue_number: issue.number
      })).setMimeType(ContentService.MimeType.JSON);
    }
    
  } catch (error) {
    Logger.log('Error processing webhook: ' + error);
    return ContentService.createTextOutput(JSON.stringify({
      success: false,
      error: error.toString()
    })).setMimeType(ContentService.MimeType.JSON);
  }
}

/**
 * Deploy as web app
 */
function setupWebApp() {
  // 1. Click "Deploy" → "New Deployment"
  // 2. Select type: "Web app"
  // 3. Execute as: "Me"
  // 4. Who has access: "Anyone"
  // 5. Copy the web app URL
  // 6. Use this URL in AppSheet webhook configuration
}
```

#### 6. Deploy and Test

1. **Save the script**
2. **Deploy as web app:**
   - Click Deploy → New Deployment
   - Select type: Web app
   - Execute as: Your account
   - Who has access: Anyone
3. **Copy the web app URL**
4. **Configure AppSheet webhook** with this URL
5. **Test the integration:**
   - Trigger a device alert in AppSheet
   - Check if GitHub issue is created
   - Verify data sync

### Security Best Practices for Apps Script

```javascript
/**
 * Store sensitive data in Script Properties
 */
function setupSecureConfig() {
  const scriptProperties = PropertiesService.getScriptProperties();
  scriptProperties.setProperties({
    'GITHUB_TOKEN': 'your_token_here',
    'APPSHEET_API_KEY': 'your_key_here'
  });
}

/**
 * Get secure config
 */
function getConfig(key) {
  const scriptProperties = PropertiesService.getScriptProperties();
  return scriptProperties.getProperty(key);
}

// Use in code:
const GITHUB_TOKEN = getConfig('GITHUB_TOKEN');
```

---

## Use Cases for This Project

### 1. Device Issue Tracking

**Workflow:**
```
Device Status Change (AppSheet)
  → Trigger Webhook
  → Create GitHub Issue
  → Assign to Development Team
  → Track Resolution
  → Update AppSheet when Closed
```

**Benefits:**
- Centralized issue tracking
- Developer visibility
- Historical record
- Automated workflows

### 2. Version Control for Configuration

**Workflow:**
```
AppSheet Configuration Change
  → Export to JSON
  → Commit to GitHub
  → Track Changes Over Time
  → Rollback if Needed
```

**Benefits:**
- Configuration backup
- Change history
- Collaboration
- Disaster recovery

### 3. Automated Reporting

**Workflow:**
```
Daily Schedule
  → Query AppSheet Data
  → Generate Report
  → Commit to GitHub (docs folder)
  → Create Pull Request
  → Notify Team
```

**Benefits:**
- Automated documentation
- Historical reporting
- Team visibility
- Compliance

### 4. Development Deployment Pipeline

**Workflow:**
```
Code Merged to Main
  → Trigger Webhook
  → Update AppSheet Config
  → Run Tests
  → Deploy to Production
  → Update Status in AppSheet
```

**Benefits:**
- Automated deployment
- Reduced errors
- Faster releases
- Better tracking

---

## Troubleshooting

### Common Issues

#### 1. Authentication Failures

**Problem:** "401 Unauthorized" errors

**Solutions:**
- Verify API tokens are correct
- Check token hasn't expired
- Ensure proper scopes/permissions
- Regenerate tokens if needed

#### 2. Rate Limiting

**Problem:** "429 Too Many Requests"

**Solutions:**
- Implement exponential backoff
- Reduce sync frequency
- Cache responses
- Use webhooks instead of polling

```javascript
// Rate limiting example
function fetchWithRetry(url, options, maxRetries = 3) {
  for (let i = 0; i < maxRetries; i++) {
    try {
      return UrlFetchApp.fetch(url, options);
    } catch (error) {
      if (i === maxRetries - 1) throw error;
      Utilities.sleep((Math.pow(2, i) + Math.random()) * 1000);
    }
  }
}
```

#### 3. Data Sync Issues

**Problem:** Data not syncing properly

**Solutions:**
- Check field mappings
- Verify data types match
- Look for null/undefined values
- Add error logging

#### 4. Webhook Not Triggering

**Problem:** AppSheet webhook not reaching integration

**Solutions:**
- Verify webhook URL is correct
- Check webhook is enabled
- Test with manual trigger
- Review AppSheet logs
- Ensure web app is deployed

### Debug Tips

**Enable Detailed Logging:**

```javascript
function debugLog(message, data) {
  const timestamp = new Date().toISOString();
  Logger.log(`[${timestamp}] ${message}`);
  if (data) {
    Logger.log(JSON.stringify(data, null, 2));
  }
}
```

**Test Individual Functions:**

```javascript
function testGitHubConnection() {
  const issues = getGitHubIssues();
  debugLog('GitHub Issues Retrieved', issues);
}

function testAppSheetConnection() {
  const data = getAppSheetData('Devices');
  debugLog('AppSheet Data Retrieved', data);
}
```

---

## Best Practices

### 1. Security

- ✅ Never commit API keys to GitHub
- ✅ Use environment variables or secret management
- ✅ Implement proper authentication
- ✅ Use HTTPS for all connections
- ✅ Regularly rotate API tokens
- ✅ Implement IP whitelisting when possible

### 2. Error Handling

```javascript
function robustAPICall(apiFunction, ...args) {
  try {
    const result = apiFunction(...args);
    return { success: true, data: result };
  } catch (error) {
    Logger.log(`Error in ${apiFunction.name}: ${error}`);
    // Send notification
    sendErrorNotification(error);
    return { success: false, error: error.toString() };
  }
}
```

### 3. Performance

- ✅ Batch operations when possible
- ✅ Implement caching
- ✅ Use webhooks over polling
- ✅ Optimize API calls
- ✅ Monitor usage and costs

### 4. Monitoring

```javascript
function monitorIntegrationHealth() {
  const metrics = {
    last_sync: getLastSyncTime(),
    errors_count: getErrorCount(),
    success_rate: getSuccessRate()
  };
  
  if (metrics.success_rate < 0.95) {
    sendAlertToTeam(metrics);
  }
  
  return metrics;
}
```

### 5. Documentation

- ✅ Document all integrations
- ✅ Maintain setup guides
- ✅ Track configuration changes
- ✅ Update diagrams
- ✅ Keep credentials guide current

---

## Additional Resources

### Documentation

- [GitHub API Documentation](https://docs.github.com/en/rest)
- [AppSheet API Documentation](https://support.google.com/appsheet/answer/10105769)
- [Google Apps Script Guide](https://developers.google.com/apps-script)
- [n8n Documentation](https://docs.n8n.io/)

### Tools

- [Postman](https://www.postman.com/) - API testing
- [ngrok](https://ngrok.com/) - Webhook testing
- [Insomnia](https://insomnia.rest/) - API client

### Community

- [AppSheet Community](https://community.appsheet.com/)
- [GitHub Community](https://github.community/)
- [Stack Overflow](https://stackoverflow.com/)

---

## Support

Need help with integration?

- 📧 Email: timhuynhwork@gmail.com
- 💬 GitHub Discussions: [Create a discussion](../../discussions)
- 🐛 Bug Reports: [Open an issue](../../issues)

---

## Contributing

Found ways to improve this integration guide? We welcome contributions!

See [CONTRIBUTING.md](./CONTRIBUTING.md) for guidelines.

---

<p align="center">
  <strong>Built with ❤️ for seamless GitHub-AppSheet integration</strong>
</p>
