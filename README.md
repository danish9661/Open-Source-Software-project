# Open Source Audit Capstone Project

Course: Open Source Software (OSS NGMC)  
Institution: VITyarthi

## Student Details

- Student Name: [Fill Your Name]
- Registration Number: [Fill Registration Number]
- Slot: [Fill Slot]
- Date of Submission: [Fill Date]
- Chosen Software: Apache HTTP Server
- Execution Platform: Fedora Linux 43

## Repository Contents

- scripts/01_system_identity_report.sh
- scripts/02_foss_package_inspector.sh
- scripts/03_disk_permission_auditor.sh
- scripts/04_log_file_analyzer.sh
- scripts/05_open_source_manifesto_generator.sh
- report/Open_Source_Audit_Report_Draft.md
- OSSCapstoneProject.docx.pdf (assignment brief)

## Project Objective

This project audits one open-source software project (Apache HTTP Server) from technical and philosophical perspectives.  
It also demonstrates practical Linux shell scripting through five scripts aligned with the course units.

## Dependencies

Use Fedora Linux 43 with these tools:

- bash
- coreutils (uname, whoami, uptime, date, du, cut)
- grep
- gawk
- rpm
- dnf
- systemd (systemctl)
- Apache HTTP Server package: httpd

## Setup and Execution

1. Open a Fedora 43 terminal and move to your project folder.
2. Install required packages:

   sudo dnf update -y
   sudo dnf install -y httpd git grep gawk coreutils curl

3. Start and enable Apache service:

   sudo systemctl enable --now httpd
   sudo systemctl status httpd

4. Make scripts executable:

   chmod +x scripts/*.sh

5. Run scripts one by one:

   ./scripts/01_system_identity_report.sh
   ./scripts/02_foss_package_inspector.sh httpd
   ./scripts/03_disk_permission_auditor.sh
   curl -I http://localhost
   curl -I http://localhost/nonexistent
   ./scripts/04_log_file_analyzer.sh /var/log/httpd/access_log GET
   ./scripts/04_log_file_analyzer.sh /var/log/httpd/error_log error
   ./scripts/05_open_source_manifesto_generator.sh

6. If you get permission errors on logs, rerun only Script 4 with sudo:

   sudo ./scripts/04_log_file_analyzer.sh /var/log/httpd/error_log error

## Script 1: System Identity Report

File: scripts/01_system_identity_report.sh

Purpose:
- Displays Linux distro, kernel, user, home directory, uptime, date/time, and license note.

Run:

./scripts/01_system_identity_report.sh

Concepts used:
- Variables
- Command substitution
- Output formatting

## Script 2: FOSS Package Inspector

File: scripts/02_foss_package_inspector.sh

Purpose:
- Checks whether a package is installed.
- Prints package metadata.
- Uses a case statement to show package philosophy notes.

Run examples:

./scripts/02_foss_package_inspector.sh httpd
./scripts/02_foss_package_inspector.sh mariadb
./scripts/02_foss_package_inspector.sh git

Concepts used:
- if-then-else
- case statement
- rpm or dpkg checks
- grep filtering

## Script 3: Disk and Permission Auditor

File: scripts/03_disk_permission_auditor.sh

Purpose:
- Loops through key Linux directories.
- Prints owner/group/permissions and total size.
- Checks Apache config directory permissions.

Run:

./scripts/03_disk_permission_auditor.sh

Concepts used:
- for loop
- du
- ls -ld
- awk and cut

## Script 4: Log File Analyzer

File: scripts/04_log_file_analyzer.sh

Purpose:
- Reads a log file line by line.
- Counts keyword matches.
- Implements retry logic for empty files.
- Prints last 5 matching lines.

Run examples:

./scripts/04_log_file_analyzer.sh /var/log/httpd/access_log GET
./scripts/04_log_file_analyzer.sh /var/log/httpd/error_log error

Concepts used:
- command-line arguments
- while read loop
- if-then checks
- counters and arithmetic

## Script 5: Open Source Manifesto Generator

File: scripts/05_open_source_manifesto_generator.sh

Purpose:
- Asks three interactive questions.
- Generates a personalized manifesto paragraph.
- Saves output to a timestamped .txt file.

Run:

./scripts/05_open_source_manifesto_generator.sh

Concepts used:
- read for user input
- string composition
- file write using > and >>
- date command

## Fedora 43 Test Flow

1. Confirm Fedora version:

   cat /etc/fedora-release

2. Install and start Apache:

   sudo dnf install -y httpd
   sudo systemctl enable --now httpd

3. Verify Apache process and service user:

   ps aux | grep httpd
   id apache

4. Execute Scripts 1 to 5 in order.
5. Before Script 4, create a few local requests so the log has lines:

   curl -I http://localhost
   curl -I http://localhost/nonexistent

6. Capture screenshots of commands and outputs for report evidence.

## How to Keep Submission Original and Viva-Ready

1. Run every command yourself on Fedora 43 and capture your own outputs.
2. Replace placeholder text with your own reflections, including what failed and what you fixed.
3. Add your own comparison points in Part D based on your test experience.
4. Keep terminal screenshots with visible username, timestamp, and command history.
5. Practice explaining each script logic in your own words before submission.

## Notes for Final Submission

- Fill all placeholders in this README.
- Include this README in your public GitHub repository.
- Add screenshots and your observations from your own Linux execution.
- Convert report/Open_Source_Audit_Report_Draft.md into PDF after personalization.

## Academic Integrity Reminder

Understand every script and be ready to explain it in a short viva.  
Personalize the report with your own Linux outputs, reflections, and conclusions.