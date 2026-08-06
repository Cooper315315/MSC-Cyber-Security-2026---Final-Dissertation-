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

## 📈 Experiment Results

Scanning was conducted against both DVWA and bWAPP, with results analysed across five quantitative metrics.

**Vulnerability Count per Tool**

| Target | Burp Suite Professional | OWASP ZAP | Nikto |
|---|---|---|---|
| bWAPP | 20 unique (~16%) | 24 unique (~19%) | 20 unique (~16%) |
| DVWA | 31 unique (~57%) | 29 unique (~53%) | 17 unique (~31%) |

OWASP ZAP produced the highest raw count on bWAPP, while Burp Suite Professional led on DVWA — but raw count alone did not indicate overall scanner quality.

**Severity Distribution**

Burp Suite Professional consistently identified the most High severity, confirmed-exploitable vulnerabilities (e.g. SQL injection, PHP code injection) on both targets. OWASP ZAP detected zero High severity findings on bWAPP and only one on DVWA, with its detections spread more evenly across Medium, Low and Informational categories. Nikto's report format does not assign severity ratings by design, so OWASP/CWE mapping was used to infer relative risk.

**OWASP Top 10:2025 Coverage**

| Target | Burp Suite Professional | OWASP ZAP | Nikto |
|---|---|---|---|
| bWAPP | A01, A02, A03, A04, A05 | A01, A02, A05 | A01, A02, A03 |
| DVWA | A01, A02, A03, A04, A05 | A01, A02, A03, A05 | A01 |

Burp achieved the broadest coverage on both targets, uniquely detecting A04 (Cryptographic Failures). No single tool, or combination of all three, achieved full OWASP Top 10:2025 coverage.

**Tool Overlap and Exclusivity**

Across both targets, over 85–94% of individual findings were detected by only one scanner. On DVWA, of 77 combined detections, only 4 were shared by more than one tool — strong evidence that the three scanners are complementary rather than redundant.

**Scan Duration**

| Scanner | bWAPP | DVWA |
|---|---|---|
| Burp Suite Professional | ~90 min | ~90 min |
| OWASP ZAP | ~30 min | ~30 min |
| Nikto | ~6 min | ~5.5 min |

Nikto was fastest but shallowest; Burp's longer runtime enabled deeper crawling, authentication handling and payload confirmation, though ZAP's shorter duration was also partly driven by tool stability issues encountered during testing.

## 🧾 Conclusion

The findings confirm that **no single automated DAST tool provides complete vulnerability visibility**. Burp Suite Professional was the strongest individual scanner — delivering the deepest application-layer detection, the most High severity confirmed findings, and the broadest OWASP Top 10:2025 coverage. OWASP ZAP was a valuable but less consistent scanner, contributing strong raw detection volume but weaker high-risk confirmation, partly constrained by runtime limitations. Nikto, while narrower in scope, added meaningful server-level coverage that neither application-layer scanner replicated.

Critically, the overlap analysis showed that the three tools were **highly complementary**, with the vast majority of findings unique to a single scanner — reinforcing that a multi-tool DAST strategy detects substantially more vulnerabilities than any single tool alone. The study also highlights that severity ratings are **not directly comparable across scanners**, since Burp Suite Professional and OWASP ZAP apply different underlying classification logic, and that scanner configuration and runtime allowances materially influence detection outcomes. The overall conclusion is that automated scanning delivers valuable but incomplete security assurance, and must be combined with multiple tools, informed interpretation of results, and broader human-led security review.
