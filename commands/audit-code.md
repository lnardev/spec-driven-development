Run a comprehensive security audit on target: ${1:-entire workspace}

Steps:
1. Activate security-audit skill.
2. Review auth, data flow, input sanitization, and potential injection points.
3. Check dependencies and permission boundaries.
4. Output concise vulnerability matrix with severity (High/Med/Low) and remediation.
