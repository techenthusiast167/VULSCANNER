**VULSCANNER** - is a powerful, multi-faceted tool designed for security professionals, developers, and penetration testers to perform automated security assessments of web applications. It combines intelligent crawling, port scanning, extraction of email, and a suite of vulnerability detection techniques to identify common web security issues with detailed reporting.


# What The Tool Does

- **Domain Resolution and Port Scanning**:

  The scanner starts by resolving the target domain to its IP address. It then scans the host using Nmap for open ports within the common range (1-1024), helping identify exposed network services that might be attack vectors.

- **Recursive Website Crawling**:
  
The tool efficiently crawls the target website, following internal links up to a configurable maximum depth. It collects all reachable URLs and extracts exposed email addresses from page content, helping expose potential information leaks.

- **Vulnerability Detection**:
  
For every collected URL, the scanner performs a variety of security checks, including:

  - *SQL Injection (SQLi) Detection*:

   It injects carefully crafted SQL payloads into URL parameters and analyzes differences in web responses and response times to detect both boolean-based and blind SQL Injection vulnerabilities.

  - *Cross-Site Scripting (XSS) Detection*:
    
    The scanner injects JavaScript payloads into URL query parameters and checks if these are reflected unescaped in the server responses, identifying reflected XSS vulnerabilities.

   - *Broken Access Control Checks*:
     
 Attempts to access common sensitive paths (e.g., /admin, /.env) directly, while carefully filtering out false positives by analyzing response status codes, redirects, and content to verify whether access controls are improperly implemented.
  
   - *CSRF Token Verification*:
     
   Analyzes HTML page forms to detect the absence of anti-CSRF tokens, crucial for preventing Cross-Site Request Forgery attacks.

   - *Security Headers Inspection*:
     
  Checks for missing important HTTP security headers like Content-Security-Policy, X-Frame-Options, Strict-Transport-Security, Referrer-Policy, etc., highlighting potential security misconfigurations.
  
   - *Open Redirect Detection*:
     
  Injects malicious redirect URLs into parameters commonly used for redirects and checks for unsafe redirection to external domains.
  
   - *SSL/TLS Validation*:
     
   Confirms the presence of HTTPS on the target site and validates SSL/TLS certificates for proper configuration and trustworthiness.
   
- **Concurrent Scanning**:
  
Uses Python’s ThreadPoolExecutor to perform multiple vulnerability checks on discovered URLs simultaneously, speeding up the scanning process.

- **Authentication Support**:
  
Supports HTTP Basic Authentication and form-based login flows to authenticate before scanning protected content areas.

- **Signal Handling for Graceful Exit**:
  
Handles user interrupt signals (e.g., Ctrl+C) gracefully to ensure clean shutdown and avoid corrupted scan states.


- **Comprehensive Reporting**:
  
Generates detailed reports in CSV and PDF formats, including enriched CVE information from public vulnerability databases to assist in prioritizing and remediation efforts.

- **User-friendly Terminal Output**:
  
Displays color-coded messages during scanning to highlight information, warnings, and critical vulnerabilities, enhancing usability and clarity.  




# Key Features Summary

**Feature	Description**

- **Intelligent recursive**: crawling	Crawls website pages up to configurable depth and extracts exposed emails.
Port scanning with Nmap	Identifies open ports on target IP to spot network exposure.

- **SQL Injection detection**: Detects boolean and blind SQLi via payload injection and response analysis.
  
- **Cross-Site Scripting detection**:	Finds reflected XSS vulnerabilities by injecting scripting payloads.

- **Broken Access Control detection**:	Checks for unauthorized access to sensitive endpoints with false positive filtering.
  
- **CSRF token presence check**:	Verifies if anti-CSRF tokens are present in web forms.
  
- **Security headers inspection**: Reports missing critical security HTTP headers like CSP, HSTS, X-Frame-Options, etc.
  
- **Open redirect scanning**: Detects unsafe external redirects via URL manipulation.
  
- **SSL/TLS validation**: Confirms HTTPS availability and validates TLS certificates.

- **Multi-threaded scanning**: Runs vulnerability detectors concurrently for faster results.
  
- **Authentication handling**:	Supports HTTP Basic and form-based login for scanning protected areas.
  
- **Detailed CSV and PDF reporting**:
Generates easily consumable and printable vulnerability reports with CVE linkage.



# Install Requirements & Dependencies 

**First Create your Virtual Environment**:

    virtualenv my_temp_venv
    source my_temp_venv/bin/activate 


**Install Dependencies**:

    pip install requests nmap pandas beautifulsoup4 fpdf2 colorama



- **requests** — for HTTP requests.

- **nmap** — Python wrapper for Nmap port scanner.
  
- **pandas** — for assembling and saving CSV reports.
  
- **beautifulsoup4** — for HTML/XML parsing for crawling/extracting information.
  
- **fpdf2** — for generating PDF reports (modern version of fpdf).
  
- **colorama** — for colored console output.

**Save The Tool**:

kindly save the tool script via the link https://gist.github.com/techenthusiast167/26c4a7edb0b0b9833f255d3a77acdc4a

**Example**:

- nano vulscanner.py
- Copy and paste in the script
- Press **ctrl + o, Enter, and ctrl + x** to exit



# How to run vulscanner ( Usage ):

**Basic scan**:

    python vulscanner.py https://example.com


**With Option**:

   **--max-depth 3**: Crawl up to 3 levels deep into the target site

**--severity-threshold 5.0**: Report vulnerabilities with severity 5.0 or higher only

**--auth-type basic**: Use HTTP Basic Auth

**--username USER**:  Username for authentication

**--password PASSWORD**: Password for authentication

**--auth-type form**: Use form-based login

**--login-url URL**: URL to submit login form for form auth

**--csv-report filename.csv**: CSV report output filename

**--pdf-report filename.pdf**: PDF report output filename


**Scan with options**:

    python vulscanner.py https://example.com --max-depth 3 --severity-threshold 5.0


**Use authentication**:

- HTTP Basic:

      python vulscanner.py https://example.com --auth-type basic --username admin --password secret


  - Form-based login:
 
        python vulscanner.py https://example.com --auth-type form --username admin --password secret --login-url https://example.com/login


- Customize report names:

      python vulscanner.py https://example.com --csv-report my_report.csv --pdf-report my_report.pdf




## Notes

- Only scan sites you are authorized to test.
  
- Adjust crawl depth and severity threshold for faster or more detailed scans.

- Review reports for detailed vulnerability information and remediation recommendations.

- Endeavor to use highly established vulnerability scanners to reassess the vulnerabilities generated by this tool. Performing such validation enhances the integrity and accuracy of the security assessment by minimizing the risk of overlooking critical vulnerabilities or accepting false positives. Leveraging multiple reputable scanners ensures comprehensive coverage and increases confidence in the identified security issues, facilitating prioritized and effective remediation efforts.

---

# Contributing

This project is open for contributions and improvements from the community. Whether you find bugs, have feature requests, or want to enhance existing functionality, your input is highly valued.

**Feel free to**:

**Submit issues** to report bugs or suggest enhancements.

**Fork the repository** or gist and create a pull request with your proposed changes.

Participate in improving documentation, adding new vulnerability checks, optimizing performance, or expanding compatibility.

Your contributions help make this tool more robust, reliable, and useful for everyone interested in web security.

Thank you for exploring the Ultimate Python Web Security Scanner! Together, we can build a stronger, more secure web ecosystem.

---



*Author: Tech Enthusiast*

*LinkedIn: http://linkedin.com/in/tech-enthusiast-669279263*



