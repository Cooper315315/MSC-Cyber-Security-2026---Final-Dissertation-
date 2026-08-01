***

# Quantitative Performance Analysis of Web Application Security Testing Tools

## 📖 Dissertation Background

Web applications remain one of the most heavily targeted systems by attackers due to their public accessibility and the sensitive data they process. The OWASP Top 10 (2025) continues to highlight recurring risks such as Broken Access Control, Security Misconfiguration and Injection as persistent threats across web applications. Automated Dynamic Application Security Testing (DAST) tools are widely adopted to detect these vulnerabilities because they can be run quickly, require no source code access, and integrate into CI/CD pipelines. However, prior research shows that different DAST tools often produce inconsistent results when scanning the same target — differing in vulnerability counts, severity classification and OWASP category coverage. This dissertation investigates that inconsistency through a controlled, side-by-side comparison of three DAST tools against two deliberately vulnerable web applications.

## ❓ Research Questions

**Primary Research Question:**
Under the same deliberately vulnerable web application and identical scanning conditions, how do multiple automated web application security testing tools compare in terms of the number and severity of vulnerabilities detected?

**Secondary Research Questions:**
1. For each tool, how many of the detected vulnerabilities are unique to that tool, and how many are also detected by at least one other tool?
2. How are the detected vulnerabilities distributed across severity levels (High, Medium, Low and Informational) for each tool?
3. To what extent do the detections from each tool cover the OWASP Top 10 (2025) risk categories and associated CWE identifiers on the selected target applications?

## 🧪 Research Method

The study uses a **controlled experimental design** within an isolated virtual lab environment. Each DAST tool is configured identically in terms of scan scope, authentication and scanning policy, then run against each target application for a minimum of three scan iterations following a repeated-measures protocol. Scan outputs are exported in structured formats (XML/HTML), parsed using Python, and compiled into a Vulnerability Analysis Dataset for descriptive and comparative statistical analysis.

## 🛠️ Tools Used

**Security testing tools:**
- Burp Suite Professional
- OWASP ZAP (Zed Attack Proxy)
- Nikto

**Target applications:**
- DVWA (Damn Vulnerable Web Application)
- bWAPP (Buggy Web Application)

**Supporting technologies:**
- Python (Pandas, Matplotlib) for data parsing and analysis
- Virtual machine environment (isolated lab) for controlled testing

## 📊 Key Metrics for Evaluation

- **Vulnerability count per tool** — total and unique detections per tool, per target
- **Severity distribution** — breakdown of High, Medium, Low and Informational findings
- **OWASP Top 10:2025 coverage** — number of distinct OWASP categories detected per tool
- **Tool overlap and exclusivity** — vulnerabilities found by multiple tools vs. exclusively by one
- **Scan duration** — average time taken per tool, per target, across scan iterations

***

Let me know if you'd like this adapted into a proper `README.md` file for direct upload to your repository, or if you want a shorter version for the main GitHub profile page versus a longer one for the specific dissertation repo.
