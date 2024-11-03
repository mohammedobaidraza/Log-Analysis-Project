# Log Analysis Project

## Project Overview

The objective is to analyze an authentication log file (`auth.log`) and generate four reports based on the activities of users.

### Reports

The following reports were generated from the `auth.log` file:

1. **Report 1: Successful Authentications**
   - This report outlines users who successfully logged into services, showing the usernames, the IP addresses they used, and the frequency of those logins.
   - **File:** `447-RAZA-R1.csv`
   - **Columns:** `USERNAME, SOURCE IP, OCCURRENCES`

2. **Report 2: Failed Authentications**
   - This report details the failed login attempts, showing the source IP, username, and the frequency of these failed attempts.
   - **File:** `447-RAZA-R2.csv`
   - **Columns:** `SOURCE IP, USERNAME, OCCURRENCES`

3. **Report 3: Legitimate Users’ Failed Authentications**
   - This report identifies failed login attempts by legitimate users who had successfully logged in before (from Report 1). It includes the username, source IP, geo-location details (country, region, and city), and occurrences.
   - **File:** `447-RAZA-R3.csv`
   - **Columns:** `USERNAME, SOURCE IP, REGION, CITY, OCCURRENCES`

4. **Report 4: Attack Sources by IP**
   - This report includes geo-location details for all failed login attempts (from Report 2). The columns list the source IP, country, region, city, and occurrences.
   - **File:** `447-RAZA-R4.csv`
   - **Columns:** `SOURCE IP, COUNTRY, REGION, CITY, OCCURRENCES`

## File Structure

- `447-RAZA-R1.csv` - Report on successful authentications.
- `447-RAZA-R2.csv` - Report on failed authentications.
- `447-RAZA-R3.csv` - Legitimate users' failed authentications.
- `447-RAZA-R4.csv` - Attack sources by IP.

## Requirements

- **Python:** Used for parsing the log file and generating the reports.
- **Geo-location Script:** IP addresses were processed using geo-location scripts provided by the course.

## How to Run the Project

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/log-analysis-project.git
   cd log-analysis-project
   ```
## Submission Information

This project was completed in fulfillment of the **Project 1: The Log Analyst** assignment. Each report has been named following the guidelines:

- `447-RAZA-R1.csv`
- `447-RAZA-R2.csv`
- `447-RAZA-R3.csv`
- `447-RAZA-R4.csv`
