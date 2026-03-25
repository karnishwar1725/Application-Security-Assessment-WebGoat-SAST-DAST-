🔐 Application Security Assessment – WebGoat (SAST & DAST)

📌 Overview

This project presents a comprehensive Application Security Assessment conducted on the WebGoat application using both:
	•	SAST (Static Application Security Testing) – SonarQube
	•	DAST (Dynamic Application Security Testing) – OWASP ZAP

The goal was to identify vulnerabilities in both source code and runtime behavior, providing a complete security evaluation.  ￼

⸻

🛠️ Tools Used

Tool	Type	Purpose
SonarQube	SAST	Static code analysis to detect bugs and vulnerabilities
OWASP ZAP	DAST	Dynamic testing of running application
WebGoat	Target App	Deliberately vulnerable web application


⸻

🔍 Key Findings

🔴 SAST (SonarQube Findings)

Blocker Issues
	•	Unclosed database resources (Prepared Statements)
	•	Unclosed file/ZIP resources
➡️ Can cause memory leaks and application crashes

Critical Issues
	•	Weak random number generation (java.util.Random)
➡️ Leads to predictable authentication tokens

Major Issues
	•	Incorrect conditional logic
	•	Improper string comparisons
	•	Potential null pointer exceptions
➡️ May break authentication or crash the app

Vulnerabilities
	•	Weak password encoding
	•	Improper JWT validation
	•	Unsafe XML parsing (XXE risk)
➡️ Risk of data exposure and authentication bypass

Security Hotspots
	•	Hardcoded passwords
	•	Unsafe HTTP methods
	•	Dynamic SQL queries (SQL Injection risk)
	•	Regex-based DoS (ReDoS)
	•	Weak cryptographic practices

⸻

🟠 DAST (OWASP ZAP Findings)

High-Risk Vulnerabilities
	•	SQL Injection
➡️ Attackers can extract or manipulate database data

Medium/High Issues
	•	Missing CSRF tokens
	•	Parameter tampering vulnerabilities
	•	Missing Content Security Policy (CSP)

Additional Misconfigurations
	•	Missing security headers (HSTS, X-Content-Type)
	•	Insecure cookie settings (HttpOnly, SameSite)
	•	Information disclosure (technology stack, timestamps)

⸻

⚖️ SAST vs DAST (Comparison)

Feature	SAST	DAST
Analysis Type	Source code	Running application
Detects	Code-level issues	Runtime vulnerabilities
Strength	Early detection	Real attack simulation
Limitation	False positives	Limited code visibility

➡️ Best Practice: Use both together for full coverage  ￼

⸻

🛡️ Key Security Recommendations
	•	Use SecureRandom instead of Random
	•	Implement parameterized queries
	•	Enforce strong password hashing (bcrypt / Argon2)
	•	Validate JWT signatures properly
	•	Disable external XML entities (XXE protection)
	•	Add CSRF protection tokens
	•	Configure security headers (CSP, HSTS)
	•	Avoid hardcoded credentials
	•	Implement input validation & sanitization

⸻

📊 Conclusion

The assessment revealed that the WebGoat application contains multiple exploitable vulnerabilities across both:
	•	Code level (SAST)
	•	Runtime behavior (DAST)

Combining both testing approaches provides a more accurate and complete security posture, highlighting the importance of secure coding and continuous security testing throughout the SDLC.  ￼

⸻

📚 References
	•	OWASP Top 10
	•	OWASP ZAP Documentation
	•	SonarQube Documentation
