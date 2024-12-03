# SSID KnownNetworks Plugin: Usage Guide

### Overview
The **SSID KnownNetworks** Watchman Monitoring plugin reports the list of known (preferred) Wi-Fi networks, along with details about their security type and hidden status. It provides output in **CSV**, **HTML**, or **plain text** formats.

---

## Installation

1. Save the plugin script as `_ssidknownnetworks.plugin` in the desired directory:
   ```bash
   /Library/MonitoringClient/Plugins/_ssidknownnetworks.plugin
   ```

2. Ensure the script is executable:
   ```bash
   chmod +x /Library/MonitoringClient/Plugins/_ssidknownnetworks.plugin
   ```

3. Optional: Save the associated plist file for the system to recognize the plugin.

---

## Command-Line Usage

Run the plugin script from the command line. By default, it outputs the list in **CSV format**.

### Basic Usage
```bash
./_ssidknownnetworks.plugin
```

### Output Format Options
Use the following flags to change the output format:

1. **CSV (default)**:
   ```bash
   ./_ssidknownnetworks.plugin
   ```
   Outputs a CSV-like table.

2. **HTML**:
   ```bash
   ./_ssidknownnetworks.plugin --html
   ```
   Outputs an HTML table.

3. **Plain Text**:
   ```bash
   ./_ssidknownnetworks.plugin --plain-text
   ```
   Outputs a simple text-based list with clear formatting.

---

## Output Examples

### CSV (`--csv`)
```csv
SSID, SecurityType, Hidden
HomeNetwork, WPA2 Personal
OfficeNetwork, WPA2 Enterprise, Hidden
GuestNetwork, Open
```

### HTML (`--html`)
```html
<table border='1'>
  <tr><th>SSID</th><th>SecurityType</th><th>Hidden</th></tr>
  <tr><td>HomeNetwork</td><td>WPA2 Personal</td><td></td></tr>
  <tr><td>OfficeNetwork</td><td>WPA2 Enterprise</td><td>Hidden</td></tr>
  <tr><td>GuestNetwork</td><td>Open</td><td></td></tr>
</table>
```

### Plain Text (default)
```
Known Wi-Fi Networks:
  - HomeNetwork: Secured: WPA2 Personal
  - OfficeNetwork: Secured: WPA2 Enterprise (Hidden)
  - GuestNetwork: Insecure
```

---

## How It Works

1. **Detects Wi-Fi Hardware Port**:
   - Identifies the active Wi-Fi interface (e.g., `Wi-Fi` or `AirPort`).

2. **Retrieves Preferred Networks**:
   - Lists all saved (preferred) Wi-Fi networks.

3. **Fetches Network Details**:
   - Queries the security type and hidden status for each SSID.

4. **Formats the Output**:
   - Presents the data in the selected format: CSV, HTML, or plain text.

---

## Known Issues

- **Missing Wi-Fi Interface**:
  - If the Wi-Fi hardware port is not found, the plugin exits with an error:
    ```bash
    Wi-Fi hardware port not found.
    ```

- **No Preferred Networks**:
  - If no preferred networks are saved, the plugin exits with an error:
    ```bash
    No preferred networks found on <Wi-Fi Port>.
    ```

- **Access to `com.apple.wifi.known-networks.plist`**:
  - Ensure the script has appropriate permissions to read the file:
    `/Library/Preferences/com.apple.wifi.known-networks.plist`

---

## Version History

| Version | Date       | Changes                                      |
|---------|------------|----------------------------------------------|
| 0.1     | 2018-11-09 | Initial Bash script version.                |
| 0.2     | 2024-12-02 | Updates Bash script version.                |
| 0.3     | 2024-12-03 | Converted script to Python.                 |

---

## Support

If you encounter any issues, feel free to contact me.
