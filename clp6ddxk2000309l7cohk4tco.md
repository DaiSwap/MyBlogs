---
title: "Troubleshooting Guide: What to Do If Apache Is Not Running"
seoTitle: "troubleshoot apache"
datePublished: Mon Nov 20 2023 03:51:26 GMT+0000 (Coordinated Universal Time)
cuid: clp6ddxk2000309l7cohk4tco
slug: troubleshooting-guide-what-to-do-if-apache-is-not-running
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1700449909151/bf119826-3303-44c2-b8a5-c1401e764c31.jpeg
tags: server, apache, powershell, troubleshooting

---

## **Prerequisites**:

\- A Windows server where Apache is installed.

\- Access to the Windows PowerShell command line.

## Steps:

### Step 1: Check Apache Service Status

The first step is to check if Apache is currently running on your Windows server.

1\. Open Windows PowerShell with administrator privileges.

2\. Run the following command to check Apache's status:

`Get-Service -Name 'Apache2.4'`  

\# Replace with the actual service name if it's different

This command will display the status of the Apache service.

Notes:

\- If Apache is running, you'll see "Running" in the Status column.

\- If Apache is not running, proceed to Step 2.

### Step 2: Start Apache Service

If Apache is not running, you can try to start it.

1\. To start Apache, use the following command:

`Start-Service -Name 'Apache2.4'`  

\# Replace with the actual service name if it's different

This command attempts to start the Apache service.

2\. After starting Apache, check its status again with the command from Step 1.

Notes:

\- If Apache starts successfully, you should see "Running" in the Status column.

\- If Apache still fails to start, proceed to Step 3.

### Step 3: Check for Configuration Errors

Incorrect configurations can prevent Apache from starting. This step helps you identify and address configuration issues.

1\. Check the Apache error log for any configuration errors. The error log is typically located in the "logs" directory within your Apache installation folder. Use the 'cd' command to navigate to the directory:

`cd 'C:\path\to\your\apache\logs'`

`Get-Content error.log -Tail 20`  

\# Display the last 20 lines of the error log

2\. Review the error log for any specific error messages related to configuration issues. Address these issues by editing your Apache configuration files.

Notes:

\- Common configuration issues include syntax errors in Apache configuration files.

\- Make sure to back up your configuration files before making changes.

### Step 4: Test Apache Configuration

Apache provides a configuration test tool to check for errors without restarting the server.

1\. Run the following command to test your Apache configuration:

`httpd -t`

This command will check your Apache configuration files for errors.

2\. If there are errors, the tool will provide information to help you identify and correct the issues.

Notes:

\- Fix any errors identified by the configuration test tool.

### Step 5: Restart Apache

After making configuration changes or resolving issues, it's essential to restart Apache.

1\. Use the following command to restart Apache:

`Restart-Service -Name 'Apache2.4'`   

\# Replace with the actual service name if it's different

2\. Check the status of Apache again to ensure it's running correctly using the command from Step 1.

Notes:

\- Restarting Apache should resolve most issues related to the service not running.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700451907515/ac9a8b6e-4706-412b-a3ed-590b80fd8d30.png align="center")

## *Note: For the above*,

The error message "Windows could not start Apache2.4 on the local computer. For more information, review the event log. If this is a non-Microsoft service, contact the service vendor and refer to service-specific error code 1" which indicates that there is an issue preventing Apache from starting.

### 1\. Check Event Viewer:

\- Open the Windows Event Viewer- Win + X and Event Viewer from the menu.

\- In the Event Viewer, navigate to Windows Logs &gt; Application.

\- Look for an error message related to Apache or Apache2.4.

### 2\. Check for Port Conflicts:

\- Ensure that Apache is not trying to use a port that is already in use by another application.  Check this in the Apache configuration file (e.g., httpd.conf) where the port is specified. The default port is 80. If another application is using port 80, Apache won't start.The port can be changed in the configuration file.

### 3\. Check for File Permissions:

\- Make sure the user account under which Apache is running has the necessary permissions to access the Apache directories and files.

### 4\. Review Windows Services:

\- Open the Windows Services manager by pressing Win + R - typing services.msc, and pressing Enter.

\- Locate the Apache service (e.g., Apache2.4) and check its properties. Ensure that it's set to start automatically.

### 5\. Reinstall Apache:

\- If all else fails, consider uninstalling and reinstalling Apache. Make sure to back up your configuration files and data before doing this.