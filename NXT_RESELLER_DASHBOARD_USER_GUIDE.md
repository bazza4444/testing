# NXT Reseller Dashboard - Complete User Guide

## Table of Contents
1. [Overview](#overview)
2. [Admin Guide](#admin-guide)
3. [End-User Guide](#end-user-guide)
4. [Technical Details](#technical-details)
5. [Troubleshooting](#troubleshooting)

---

## Overview

**NXT Reseller Dashboard** is a WHMCS plugin designed for managing IPTV/streaming reseller services. It consists of two main components:

- **Addon Module** (`NXTDashboard`): Provides admin-level management features
- **Server Module** (`NXTResellerPanel`): Handles service provisioning and customer-facing features

---

## Admin Guide

### Accessing the Plugin

1. **Login to WHMCS Admin Panel**
   - Navigate to your WHMCS installation URL
   - Login with admin credentials

2. **Access Addon Module**
   - Go to: **Addons → NXT Dashboard**
   - This is the main control panel for managing reseller accounts

3. **Configure Server Module**
   - Go to: **Setup → Products/Services → Servers**
   - Find "NXTResellerPanel" in the server list
   - Configure server connection details

### Admin Features

#### 1. Service Management
- **View all customer IPTV services**
- **Monitor service status** (Active, Suspended, Terminated)
- **Manage service expiry dates**
- **Update customer credentials**

#### 2. Product Configuration
- **Set up service packages** (different tiers/plans)
- **Configure DNS URLs** for streaming services
- **Set billing cycles** (Monthly, Quarterly, Annually)
- **Manage pricing** and recurring amounts

#### 3. Customer Account Management
- **Create new reseller accounts**
- **Suspend/Unsuspend services**
- **Update passwords** for customer accounts
- **View usage statistics** (if configured)

#### 4. Application Downloads
- **Configure download links** for various platforms:
  - Android
  - iOS
  - Windows
  - macOS
  - Linux

### Configuration Steps

#### Setting Up a New Product

1. **Navigate to Products/Services**
   ```
   Setup → Products/Services → Products/Services
   ```

2. **Create New Product**
   - Click "Create a New Product"
   - Select product group (or create new group)
   - Choose module: **NXTResellerPanel**

3. **Configure Product Details**
   - Set product name (e.g., "IPTV Premium Package")
   - Set pricing
   - Configure billing cycle
   - Set welcome email template

4. **Module Settings**
   - DNS URL: Enter your streaming service DNS
   - M3U Link settings: Enable/disable M3U playlist generation
   - Watch Stream URL: Configure web player URL
   - Application Links: Add download URLs for each platform

#### Managing Customer Services

1. **View Active Services**
   ```
   Clients → Products/Services
   ```

2. **Edit Service Details**
   - Click on service ID
   - View/modify:
     - Username
     - Password
     - Expiry date
     - Service status
     - Custom fields (e.g., MAG device ID)

3. **Suspend/Unsuspend Services**
   - Select service
   - Click "Suspend" or "Unsuspend" button
   - Add suspension reason if needed

#### Upgrade Management

1. **Enable Upgrade Options**
   - Configure upgrade paths in product settings
   - Set trial period expirations
   - Define upgrade pricing

2. **View Upgrade Requests**
   - Monitor pending upgrades in admin panel
   - Approve/reject upgrade requests

---

## End-User Guide

### Accessing Your Service

#### 1. Login to Client Area

```
https://your-whmcs-domain.com/clientarea.php
```

- Use your email and password to login
- Navigate to "My Services" or "My Products/Services"

#### 2. View Service Details

Once logged in, you'll see:

**Product Information Panel:**
- Package Name: Your subscription tier
- Username: Your IPTV login username
- Password: Your IPTV login password (click "Show" to reveal)
- DNS URL: Streaming service URL
- Expiry Date: When your service expires

**Billing Information Panel:**
- Product name and status
- Registration date
- Recurring amount
- Billing cycle (Monthly/Quarterly/Annual)
- Payment method
- First payment amount

### Using Your IPTV Service

#### Option 1: Watch Stream (Web Player)

1. **Click "Watch Stream!" button**
   - Automatically opens web player
   - Credentials are auto-filled
   - Start watching immediately

#### Option 2: Download Applications

1. **Click "Download Application" button**
2. **Select your platform:**
   - **Android**: Download APK, install on Android devices
   - **iOS**: Download from App Store link
   - **Windows**: Download Windows installer
   - **macOS**: Download Mac application
   - **Linux**: Download Linux package

3. **Install and Configure:**
   - Install the downloaded application
   - Open the app
   - Enter your credentials:
     ```
     Username: [your username from service details]
     Password: [your password from service details]
     DNS URL: [DNS URL from service details]
     ```

#### Option 3: Use M3U Playlist

1. **Locate "File Type" dropdown** (if enabled)
2. **Select your preferred format:**
   - **m3u**: Standard playlist format
   - **m3u_plus**: Enhanced format with EPG
   - **GigaBlue**: For GigaBlue receivers
   - **Enigma 2**: For Enigma2-based receivers
   - **DreamBox**: For DreamBox receivers
   - And many more specialized formats

3. **Copy the Playlist URL**
   - Click the "Copy" button next to the URL
   - Paste into your preferred IPTV player application

4. **Popular IPTV Players:**
   - **VLC Media Player** (Windows, Mac, Linux)
   - **Kodi** (Multi-platform)
   - **Perfect Player** (Android)
   - **GSE SMART IPTV** (iOS, Android)
   - **TiviMate** (Android TV)

### Managing Your Service

#### Update Password

1. **Navigate to service details**
2. **Click "Update" button** next to password
3. **Enter new password**
4. **Click "Save"**
5. Password will be updated immediately

#### Check Expiry Date

- Your expiry date is displayed in the service details panel
- You'll receive email notifications before expiration
- Renew early to avoid service interruption

#### Upgrade Subscription

1. **Look for "Upgrade Subscription" button** (if trial or eligible for upgrade)
2. **Click to view upgrade options**
3. **Select desired package**
4. **Complete payment**
5. Service will be upgraded automatically

### Using IPTV on Different Devices

#### Android TV / Fire TV

1. Download Android app from service details
2. Install using APK installer
3. Enter credentials
4. Enjoy on big screen

#### Smart TV

1. If app available, install from TV app store
2. Or use M3U playlist with TV's built-in player
3. Or use HDMI streaming device

#### Set-Top Boxes (Enigma2, DreamBox, etc.)

1. Select appropriate format from File Type dropdown
2. For auto-script options:
   - Copy the command
   - SSH into your receiver
   - Paste and execute command
   - Receiver will auto-configure

#### Mobile Devices

1. Download app from service details
2. Install on iOS/Android
3. Login with credentials
4. Stream on-the-go

---

## Technical Details

### File Structure

```
modules/
├── addons/
│   └── NXTDashboard/
│       ├── NXTDashboard.php (Main addon file - ionCube encoded)
│       ├── license.php
│       └── lib/ (Helper libraries)
│
└── servers/
    └── NXTResellerPanel/
        ├── NXTResellerPanel.php (Server module - ionCube encoded)
        ├── templates/
        │   ├── overview.tpl (Customer service view)
        │   ├── magtemplate.tpl (MAG device template)
        │   ├── error.tpl (Error display)
        │   └── newstyle.css (Styling)
        └── images/ (UI assets)
```

### Key Features

1. **Automatic Provisioning**
   - Creates IPTV accounts automatically when service ordered
   - Generates unique username/password pairs
   - Configures DNS and streaming URLs

2. **Multi-Format Support**
   - Generates M3U playlists in various formats
   - Supports auto-configuration scripts for receivers
   - Compatible with major IPTV platforms

3. **Application Management**
   - Centralized download portal for all platforms
   - Version control for applications
   - Platform-specific installation guides

4. **Billing Integration**
   - Automatic service suspension on payment failure
   - Grace period configuration
   - Upgrade/downgrade paths

### API Integration

The module integrates with IPTV panel APIs to:
- Create/delete user accounts
- Update credentials
- Check service status
- Retrieve expiry dates
- Generate M3U URLs

---

## Troubleshooting

### Common Issues

#### Issue 1: Cannot See Service Details

**Symptoms:**
- Blank page or missing information in service details

**Solution:**
1. Check if service status is "Active"
2. Verify server module is properly configured
3. Check WHMCS error logs: `configuration.php` debug mode

#### Issue 2: Watch Stream Button Not Working

**Symptoms:**
- Button present but nothing happens when clicked

**Solution:**
1. Check if "Watch Stream" URL is configured in product settings
2. Verify credentials are properly set
3. Test URL manually in browser

#### Issue 3: M3U Links Not Generating

**Symptoms:**
- Empty playlist URL or download fails

**Solution:**
1. Verify M3U URL is configured in module settings
2. Check if username/password are set correctly
3. Test M3U URL format manually

#### Issue 4: Applications Not Displaying

**Symptoms:**
- Download Application button shows empty modal

**Solution:**
1. Configure application links in product custom fields
2. Verify array structure in module configuration
3. Check if `$appdata` variable is populated

#### Issue 5: Password Update Not Working

**Symptoms:**
- Password update button doesn't save changes

**Solution:**
1. Check if API connection to IPTV panel is active
2. Verify user has permission to update password
3. Check WHMCS activity log for errors

### Debug Mode

Enable WHMCS debug mode for detailed error messages:

1. Edit `/path/to/whmcs/configuration.php`
2. Set: `$display_errors = "On";`
3. Set: `$error_reporting = E_ALL;`
4. Reproduce issue
5. Check error messages
6. **Important:** Disable debug mode after troubleshooting

### Getting Support

If you need additional support:

1. **Check WHMCS Logs**
   ```
   Admin Area → Utilities → Logs → Module Log
   Admin Area → Utilities → Logs → Activity Log
   ```

2. **Contact Plugin Developer**
   - Provide: WHMCS version, PHP version, error messages
   - Include: screenshots of issue
   - Describe: steps to reproduce

3. **Community Forums**
   - WHMCS Community: https://whmcs.community/
   - Search for similar issues
   - Post detailed question if needed

---

## Best Practices

### For Administrators

1. **Regular Backups**
   - Backup WHMCS database regularly
   - Keep copy of module files
   - Test restoration procedure

2. **Monitor Service Health**
   - Check API connectivity daily
   - Monitor service creation/suspension
   - Review error logs weekly

3. **Customer Communication**
   - Send setup guides after purchase
   - Notify before expiry dates
   - Provide clear upgrade paths

4. **Security**
   - Use strong admin passwords
   - Enable two-factor authentication
   - Keep WHMCS updated
   - Regularly review access logs

### For End-Users

1. **Save Your Credentials**
   - Store username/password securely
   - Note down DNS URL
   - Keep M3U link handy

2. **Test Before Expiry**
   - Ensure service works well before renewal date
   - Report issues early
   - Keep payment method updated

3. **Use Official Apps**
   - Download only from provided links
   - Avoid third-party modified apps
   - Keep apps updated

4. **Report Issues Promptly**
   - Contact support if streaming stops
   - Provide error messages/screenshots
   - Note when issue started

---

## Frequently Asked Questions (FAQ)

### General Questions

**Q: What is NXT Reseller Dashboard?**
A: It's a WHMCS plugin for managing IPTV/streaming reseller services, handling provisioning, billing, and customer access.

**Q: Do I need technical knowledge to use it?**
A: Admins need basic WHMCS knowledge. End-users need minimal technical skills - just install app and login.

**Q: Is it compatible with my WHMCS version?**
A: Check with plugin developer for compatibility matrix. Generally supports WHMCS 7.x and 8.x.

### For Administrators

**Q: How do I configure a new IPTV panel?**
A: Add server in WHMCS (Setup → Servers), select NXTResellerPanel module, enter API credentials.

**Q: Can I offer free trials?**
A: Yes, configure trial period in product settings, enable upgrade prompts.

**Q: How do I suspend services automatically?**
A: WHMCS handles this automatically based on billing configuration and payment status.

### For End-Users

**Q: Can I use service on multiple devices?**
A: Depends on your subscription plan. Check with your provider for simultaneous connection limits.

**Q: What happens if my service expires?**
A: Service will be suspended. Renew to reactivate immediately.

**Q: Can I change my password?**
A: Yes, use the "Update" button in service details panel.

**Q: Which IPTV player should I use?**
A: Any M3U-compatible player works. Popular choices: VLC, Perfect Player, GSE SMART IPTV.

---

## Quick Reference

### Admin Quick Links

```
Dashboard:        Addons → NXT Dashboard
Server Config:    Setup → Products/Services → Servers
Products:         Setup → Products/Services → Products/Services
Services:         Clients → Products/Services
Logs:             Utilities → Logs
```

### Customer URLs

```
Client Area:      https://your-domain.com/clientarea.php
View Services:    Client Area → My Services
Upgrade:          upgrade.php?type=package&id=[service_id]
Support:          submitticket.php
```

### Essential Information for Customers

**You will need:**
- Username (provided in service details)
- Password (provided in service details)
- DNS URL (provided in service details)
- M3U URL (generated in service details)

**Quick Start:**
1. Login to client area
2. Click "My Services"
3. Select your IPTV service
4. Download app OR copy M3U link
5. Enter credentials and start streaming

---

## Conclusion

The NXT Reseller Dashboard provides a complete solution for managing IPTV reseller services within WHMCS. With proper configuration and understanding of its features, both administrators and end-users can efficiently manage and enjoy their streaming services.

For the latest updates and additional features, consult the plugin developer's documentation and WHMCS marketplace listing.

---

**Document Version:** 1.0  
**Last Updated:** 2025  
**Created by:** AI Analysis of Plugin Structure

**Note:** This documentation is based on analysis of the plugin's structure and standard WHMCS practices. The actual PHP code is ionCube encoded and cannot be viewed directly. For specific API integration details or advanced configuration, contact the plugin developer.
