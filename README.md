# VULSCANNER is a powerful, multi-faceted tool designed for security professionals, developers, and penetration testers to perform automated security assessments of web applications. It combines intelligent crawling, port scanning, extraction of email, and a suite of vulnerability detection techniques to identify common web security issues with detailed reporting.


What the Tool Does

    Domain Resolution and Port Scanning:
    The scanner starts by resolving the target domain to its IP address. It then scans the host using Nmap for open ports within the common range (1-1024), helping identify exposed network services that might be attack vectors.

    Recursive Website Crawling:
    The tool efficiently crawls the target website, following internal links up to a configurable maximum depth. It collects all reachable URLs and extracts exposed email addresses from page content, helping expose potential information leaks.

    Vulnerability Detection:
    For every collected URL, the scanner performs a variety of security checks, including:

        SQL Injection (SQLi) Detection:
        It injects carefully crafted SQL payloads into URL parameters and analyzes differences in web responses and response times to detect both boolean-based and blind SQL Injection vulnerabilities.
