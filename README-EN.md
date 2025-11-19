# xiaYue_Pro - Burp Suite Authorization Bypass Detection Plugin

> Version: 2.3  
> Maintained by: NOVASEC Team  
> Compatibility: Burp Suite Professional 2020.1+

## 🚀 Plugin Overview

xiaYue_Pro is an authorization bypass vulnerability detection plugin designed for Burp Suite. It automatically detects broken access control issues in web applications. By comparing responses under different privilege levels, it quickly identifies potential authorization problems, providing powerful automation for security testers.

## ✨ Key Highlights

### 1. 🎯 Smart Authorization Bypass Detection
- Multiple privilege comparison: automatically compares responses in original, low-privilege, and unauthenticated states
- Smart deduplication: MD5-based deduplication on URL path, HTTP method, and parameter names to avoid repeated checks
- Response length analysis: automatically analyzes response length differences to rapidly identify access control failures

### 2. 🔍 Advanced Filtering System
- HTTP method filtering: batch-filter specific HTTP methods (e.g., OPTIONS, HEAD)
- API path filtering: precise filtering for specified paths, supports wildcard matching
- Whitelist mechanism: flexible whitelist configuration, supports batch configuration across multiple domains
- Static resource filtering: automatically filters images, CSS, JS, and other static resources to improve efficiency

### 3. 🛠️ Parameter Replacement Engine
- Intelligent parameter replacement: supports dynamic replacement for parameters in GET and POST requests
- Multi-format support: compatible with `application/x-www-form-urlencoded`, JSON, and more
- Batch rule configuration: supports multi-line replacement rules, format: `param=new_value`

### 4. 📊 Visualized Data Presentation
- Real-time data table: clear tabular display with clickable rows to view detailed packets
- Smart sorting: sort by ID, method, URL, response length, and more
- Difference markers: automatically annotate response length differences using symbols
  - `✔` indicates same length (possible authorization bypass)
  - `==>` displays the exact difference value

### 5. 🔐 Authentication Information Management
- Low-privilege authentication: configure low-privilege user authentication information (Cookie, Token, etc.)
- Unauthenticated configuration: set authentication fields to remove
- Universal Cookie: support common cookie configuration applicable to multiple scenarios
- Right-click extraction: quickly extract authentication info from requests via context menu

### 6. 💾 Configuration Persistence
- Auto save: all settings are automatically saved to local files
- Restore on restart: automatically restores last configuration after restarting Burp Suite
- Quick configuration: context menu provides a fast configuration dialog
- Configuration migration: supports import and export of configuration files

### 7. ⚡ Performance Optimizations
- Smart caching: pre-splitting filter arrays to avoid repeated string operations
- Asynchronous processing: non-blocking request handling; does not affect Burp Suite performance
- Memory management: automatically cleans old data to prevent memory overflow
- Debug optimizations: removes redundant log output to improve runtime efficiency

## 🎨 UI Features

### Main Interface Layout
```
┌─────────────────────────────────────────────────────────────┐
│                    xiaYue_Pro V2.3                         │
├─────────────────────────────────────────────────────────────┤
│  [Start Plugin] [Clear List] [Enable Whitelist] [Auto Save Results] │
│  [Enable HTTP Method Filtering] [Enable API Path Filtering] [Advanced Settings] │
├─────────────────────────────────────────────────────────────┤
│  Authorization Info Area (resizable)                        │
│  Parameter Replacement Configuration Area (resizable)       │
│  Unauthenticated Fields Area (resizable)                    │
├─────────────────────────────────────────────────────────────┤
│  Original Packet | Low-Privilege Packet | Unauthenticated Packet     │
│  [Request] [Response] | [Request] [Response] | [Request] [Response] │
└─────────────────────────────────────────────────────────────┘
```

### Table Column Description
| Column | Description | Sorting |
|-------|-------------|---------|
| # | Request ID | ✅ |
| Method | HTTP method | ✅ |
| URL | Request address | ✅ |
| Original Length | Original response length | ✅ |
| Low-Priv Length | Low-privilege response length | ✅ |
| Unauth Length | Unauthenticated response length | ✅ |

## 🚀 Usage

### 1. Basic Configuration
1. Start the plugin: check the "Start Plugin" checkbox
2. Configure authentication information:
   - Fill low-privilege user authentication information in the "Authorization Info" area
   - Fill fields to remove in the "Unauthenticated Fields" area
3. Configure parameter replacement: fill replacement rules in the "Parameter Replacement" area

### 2. Filtering Configuration
1. HTTP method filtering:
   - Check "Enable HTTP Method Filtering"
   - Enter methods to filter, separated by commas (e.g., `OPTIONS,HEAD`)
   - Click "Apply Method Filtering"

2. API path filtering:
   - Check "Enable API Path Filtering"
   - Enter paths to filter, separated by commas (e.g., `/api/admin/,/admin/`)
   - Click "Apply Path Filtering"

3. Whitelist configuration:
   - Enter domains in the "Whitelist Domains" input
   - Separate multiple domains with commas
   - Click "Enable Whitelist"

### 3. Context Menu Features
- Send to xiaYue detection: send selected requests to the plugin for analysis
- Extract authentication info: automatically extract authentication data from the request and populate configuration fields
- Quick configuration: open a quick config dialog to set multiple parameters at once

### 4. Data Viewing
- Click table rows: automatically display the corresponding request and response in the tabs on the right
- Header sorting: click table headers to sort ascending/descending
- Difference analysis: quickly identify authorization issues via response length differences

## 📋 Configuration Parameters

### Authentication Information Format
```
# Low-privilege authentication example
Cookie: JSESSIONID=test;UUID=1; userid=admin
Authorization: Bearer test_token
X-User-Id: 12345

# Fields to remove for unauthenticated state
Cookie
Authorization
Token
X-User-Id
```

### Parameter Replacement Rules
```
# Format: param=new_value
project_id=123123
user_id=999
token=new_token_value
```

### Filtering Configuration Examples
```
# HTTP method filtering
OPTIONS,HEAD,TRACE

# API path filtering
/api/admin/,/admin/,/user/profile/
```

## 🔧 Advanced Settings

### Performance Configuration
- Max log entries: limit the number of log entries kept in memory
- Enable verbose logging: control the level of log detail
- Output format: supports TEXT, JSON, CSV
- Auto cleanup: automatically clean old data

### Custom Configuration
- Static resource filtering: automatically filter common static file extensions
- Request deduplication: MD5-based smart deduplication of requests
- Response validation: automatically validate response effectiveness and skip empty responses

## 🚨 Notes

### Usage Recommendations
1. Configure filtering rules sensibly: avoid over-filtering that reduces detection coverage
2. Periodically clean data: clear historical data after long-term use
3. Back up configuration: regularly back up important settings
4. Permission testing: ensure the test environment's safety; avoid affecting production systems

### Compatibility
- Supports Burp Suite Professional 2020.1 and later
- Requires Java 8 or newer
- Recommended for use in testing environments

### Performance Considerations
- Enable filtering when handling large volumes of requests
- Periodically clean log data to free memory
- Avoid use in performance-sensitive environments

## 🆕 Changelog

### v2.3 (current)
- Added parameter replacement for GET and POST requests
- Optimized UI with resizable input boxes
- Performance optimizations; removed redundant log output
- Fixed configuration loading and UI synchronization issues

### v2.2
- Added HTTP method and API path filtering
- Implemented table sorting
- Improved configuration persistence mechanism
- Performance optimizations and code refactoring

### v2.1
- Core authorization bypass detection
- Basic authentication information management
- Data table display
- Context menu features

## 🤝 Support

If you encounter problems or have improvement suggestions, feel free to provide feedback:

- Issue reporting: describe the problem and reproduction steps in detail
- Feature suggestions: propose new feature requirements
- Bug reports: provide error logs and system environment information

## 📄 License

This plugin is intended solely for security testing and authorized penetration testing. Please comply with applicable laws and regulations. Do not use it for illegal purposes.

---

xiaYue_Pro — making authorization bypass detection simpler and more efficient! 🚀

