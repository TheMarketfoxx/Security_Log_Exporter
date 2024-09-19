# Windows RDP Failed Logon Tracker with IP Geolocation

This PowerShell script automates the process of monitoring Windows Event Viewer for failed Remote Desktop Protocol (RDP) logon attempts (Event ID 4625). It extracts the source IP address of each failed logon, queries an IP geolocation API to gather geographical data (latitude, longitude, state, country), and logs the information in a custom log file.

## Features
- **Real-time Monitoring**: Continuously monitors Windows Event Viewer for failed RDP logon attempts.
- **IP Geolocation**: Uses [ipgeolocation.io](https://ipgeolocation.io/) API to get geographical information (latitude, longitude, state, country) of the failed logon attempt's source IP.
- **Custom Logging**: Logs detailed information (IP, username, geolocation, timestamp) to a custom log file (`failed_rdp.log`).
- **Sample Log Data**: Generates sample log entries for training and testing purposes.
- **Retry Prevention**: Avoids duplicate log entries by checking if an event has already been logged.

## Usage
1. **Set up the API Key**: You need an API key from [ipgeolocation.io](https://ipgeolocation.io/). Replace `YourAPIkeyGOEShere` in the script with your actual API key.
2. **Run with Administrator Privileges**: Ensure you run this script with administrator privileges to access Windows Security Event Logs.
3. **Custom Log File Location**: The script generates and writes log entries to `C:\ProgramData\failed_rdp.log`. You can customize the location by modifying the `$LOGFILE_PATH` variable.

## Example Output in Log File
latitude:40.71455,longitude:-74.00714,destinationhost
,username
,sourcehost:72.45.247.218,state
York,country
States,label
States - 72.45.247.218,timestamp:2021-10-26 10:44:07


## Requirements
- **PowerShell**: This script is designed for PowerShell.
- **ipgeolocation.io API Key**: Sign up and get an API key from [ipgeolocation.io](https://ipgeolocation.io/).
- **Windows Event Viewer Access**: Administrator privileges are required to monitor Security Event Logs.

## How It Works
- The script uses a filter to capture Event ID 4625 (failed logon attempts) from Windows Event Viewer.
- For each failed logon, it extracts the source IP address and uses the [ipgeolocation.io API](https://ipgeolocation.io/documentation/ip-geolocation-api.html) to fetch the corresponding location details.
- It logs the event, including timestamp, username, destination host, source IP, and geographical location (latitude, longitude, state, country) in a custom log file for future analysis.

<img width="1321" alt="Screenshot 2024-09-18 2239132" src="https://github.com/user-attachments/assets/5f2b59c2-0e66-424d-93c2-28b029823f33">
