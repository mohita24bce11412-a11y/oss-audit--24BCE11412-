# oss-audit--24BCE11412-

# OSS Audit — Python Programming Language
## Open Source Software Capstone Project | VIT Bhopal
 
| Field | Details |
|-------|---------|
| **Student Name** | Mohita Nagar |
| **Registration Number** | 24BCE11412 |
| **Course** | Open Source Software (OSS NGMC) |
| **Chosen Software** | Python Programming Language |
| **License** | PSF License v2 |
 

##Repository Structure
```
oss-audit-[rollnumber]/
├── README.md
├── script1_system_identity.sh
├── script2_foss_inspector.sh
├── script3_disk_auditor.sh
├── script4_log_analyzer.sh
└── script5_manifesto.sh
```

---
##Description of each script

###Script 1 — System Identity Report 
(script1_system_identity.sh)
This script prints a structured overview of the Linux environment, similar to a welcome screen. It includes details such as OS distribution, kernel version, current user, home directory, uptime, current date/time, and the license governing the operating system (GPL).

**Shell concepts used:** variables, command substitution $(), file checking, text processing using grep, cut, tr, and formatted output with echo.
---

###Script 2 — FOSS Package Inspector (script2_foss_inspector.sh)
This script verifies whether a given software package (default: python3) exists on the system. If found, it extracts relevant details like version and description using system package managers (dpkg or rpm). A case block is used to display a short insight about the package.

**Shell concepts used:** conditional statements, case selection, package queries (dpkg -s / rpm -qi), piping with grep, default arguments using ${1:-value}.

###Script 3 — Disk and Permission Auditor (script3_disk_auditor.sh)
This script iterates through key Linux directories such as /etc, /var/log, /home, etc., and reports their disk usage, ownership, and permission settings. It also checks for Python-related directories like binaries or libraries.

**Shell concepts used:** array-based loops, directory checks [ -d ], commands like ls -ld, du -sh, data extraction using awk, and formatted printing via printf.
---
###Script 4 — Log File Analyzer (script4_log_analyzer.sh)
This script processes a given log file line by line to count how many entries match a specified keyword (default: "error"). It also displays the last few matching entries and includes a retry mechanism if the file is temporarily inaccessible.

**Shell concepts used:** while read loop, conditional checks, counters, positional arguments $1, $2, case-insensitive search using grep -i, and output filtering with tail.
---
###Script 5 — Open Source Manifesto Generator (script5_manifesto.sh)
This interactive script collects user input through prompts and generates a short personalised statement reflecting open-source values. The output is saved in a uniquely named text file and displayed.

**Shell concepts used:** read -p for input, variable concatenation, file writing using > and >>, date handling, and command substitution using $(whoami).
---
##Dependencies
All scripts are designed to run on a standard Linux system with bash. No external installations are required.

| Utility | Used In | Typically Provided By |
|---------|---------|-----------------------|
| `bash` | All scripts | Pre-installed on all Linux systems |
| `uname`, `uptime`, `date`, `whoami` | Script 1, 5 | `coreutils` (pre-installed) |
| `dpkg` | Scripts 2, 3 | Pre-installed on Debian/Ubuntu |
| `rpm` | Scripts 2, 3 | Pre-installed on RHEL/Fedora/CentOS |
| `grep`, `awk`, `cut`, `tr` | Scripts 1, 2, 3, 4 | `grep`, `gawk`, `coreutils` (pre-installed) |
| `du`, `ls`, `printf` | Script 3 | `coreutils` (pre-installed) |
| `tail` | Script 4 | `coreutils` (pre-installed) |
 ---
## How to Run Each Script on Linux
 
### Step 1 — Clone the repository
```bash
git clone (https://github.com/mohita24bce11412-a11y/oss-audit--24BCE11412-.git)
cd oss-audit-24BCE11412
```
 
### Step 2 — Make scripts executable
```bash
chmod +x *.sh
```
 
### Step 3 — Run each script
 
**Script 1 — System Identity Report**
```bash
./script1_system_identity.sh
```
 
**Script 2 — FOSS Package Inspector**
```bash
# Check default package (python3)
./script2_foss_inspector.sh
 
# Check a specific package
./script2_foss_inspector.sh git
./script2_foss_inspector.sh firefox
```
 
**Script 3 — Disk and Permission Auditor**
```bash
./script3_disk_auditor.sh
```
> Note: Some directory sizes (like `/var/log`) may show `N/A` without `sudo` due to read permissions.
 
**Script 4 — Log File Analyzer**
```bash
# Basic usage — search for 'error' (default keyword)
./script4_log_analyzer.sh /var/log/syslog
 
# Search for a custom keyword
./script4_log_analyzer.sh /var/log/syslog warning
 
# On systems using journald instead of syslog:
./script4_log_analyzer.sh /var/log/kern.log error
```
 
**Script 5 — Open Source Manifesto Generator**
```bash
./script5_manifesto.sh
```
Follow the three interactive prompts. Your manifesto will be saved as `manifesto_[username]_[timestamp].txt` in the current directory.
 
---
Notes
Scripts 1, 3, and 5 can be executed directly without arguments.
Script 2 optionally takes a package name as input.
Script 4 requires a valid log file path.
Some directories (like /var/log) may require elevated permissions to access complete data.
In minimal environments, package manager commands may not be available — this is expected behavior.
