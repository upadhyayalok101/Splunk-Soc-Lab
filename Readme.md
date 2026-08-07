# 🔍 Splunk Logs — ACEP SOC Lab

Welcome to the training package dataset directory. All manuals, answer keys, and project directory structures have been removed and flattened to leave only the necessary Splunk data files.

---

## 📋 Splunk Dataset Upload Reference

Below is a reference guide for uploading the 14 flattened files in this directory to Splunk:

### 1. Standard Event Logs (Index: `main`)

For each of the following files, navigate to **Settings ➔ Add Data ➔ Upload** in Splunk. Set the **Index** to `main` and choose the corresponding **Source Type**:

| # | File Name | Recommended Source Type | Description / Use Case |
| :---: | :--- | :---: | :--- |
| **1** | `windows_security_logs.csv` | `csv` | Windows Security event logs (logins, privilege escalations, etc.) |
| **2** | `sysmon_events.csv` | `csv` | Advanced Windows system activity (process creation, network connections) |
| **3** | `auth.log` | `syslog` | Authentication logs (ssh, login attempts, pam sessions) |
| **4** | `syslog.log` | `syslog` | General system log messages |
| **5** | `cron.log` | `syslog` | Scheduled job execution logs |
| **6** | `firewall_logs.csv` | `csv` | Network firewall traffic logs |
| **7** | `vpn_logs.csv` | `csv` | Virtual Private Network connection/session details |
| **8** | `proxy_logs.csv` | `csv` | Web proxy/HTTP access records |
| **9** | `dns_logs.csv` | `csv` | Domain Name System query resolution logs |
| **10** | `email_logs.csv` | `csv` | Email transaction/SMTP logs |
| **11** | `powershell_logs.csv` | `csv` | PowerShell execution and script block logs |
| **12** | `file_access_logs.csv` | `csv` | Object and file access audits |
| **13** | `usb_activity_logs.csv` | `csv` | External media / USB insertion and activity |

---

### 2. Lookup Tables (File-based Lookup)

The following file is a lookup table to map and enrich usernames with employee details (real name, job title, department, etc.):

*   **File Name:** `user_accounts.csv`
*   **Splunk Configuration Steps:**

> [!IMPORTANT]
> Make sure to configure the lookup table properly to allow mapping fields like `user` or `username` to employee attributes.

1. **Upload Lookup Table:**
   - Go to **Settings ➔ Lookups ➔ Lookup table files ➔ New Lookup Table File**.
   - Set **Destination App** to `search`.
   - Upload the `user_accounts.csv` file.
   - Save the destination filename as `user_accounts.csv`.

2. **Define Lookup:**
   - Go to **Settings ➔ Lookups ➔ Lookup definitions ➔ New Lookup Definition**.
   - Set the name to `user_accounts.csv`.
   - Set **Type** to `File-based`.
   - Set **Lookup file** to `user_accounts.csv`.
   - Save.

---
