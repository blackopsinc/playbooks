# Blackscan Opensource Playbooks

This directory contains various security scanning playbooks for use with the Blackscan tool. Each scanner leverages the `$blackscan` environment variable as the target and stores results in the `/opt/blackscan/data/` directory.

## Available Scanners

### nmap_scanner
A comprehensive port scanner that identifies open ports, services, and potential vulnerabilities.
- Uses nmap with service detection and script scanning
- Performs a full port scan (-p-) with aggressive timing
- Stores results in `/opt/blackscan/data/nmap/`

### nuclei_scanner
Vulnerability scanner that uses templates to identify security issues across various categories.
- Scans for CVEs, exposures, vulnerabilities, misconfigurations, and technologies
- Uses templates from the nuclei-templates repository
- Stores results in `/opt/blackscan/data/nuclei/` categorized by vulnerability type

### ffuf_scanner
Web fuzzing tool for directory/path discovery and parameter testing.
- Automatically adds FUZZ keyword to target URLs if not present
- Validates and formats target URLs with proper protocol
- Supports customizable wordlists, rate limiting, and threading options
- Stores results in `/opt/blackscan/data/ffuf/` in JSON format

### sqlmap_scanner
SQL injection detection and exploitation tool.
- Tests for SQL injection vulnerabilities in web applications
- Runs with aggressive testing options (--level 3, --risk 2)
- Attempts database enumeration and data extraction if vulnerabilities are found
- Stores results in `/opt/blackscan/data/sqlmap/`

## Usage

```bash
# Set the target environment variable
export blackscan="example.com"          # For nmap and nuclei
export blackscan="https://example.com/page?param=FUZZ"  # For ffuf
export blackscan="https://example.com/page?param=test"  # For sqlmap

# Run a scanner
./nmap_scanner
./nuclei_scanner
./ffuf_scanner
./sqlmap_scanner
```
