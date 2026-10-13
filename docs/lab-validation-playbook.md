# Blue–Red Lab Validation Playbook

## 1. Scope and preparation

Write down the owned test system, permission boundary, tool versions, expected telemetry source, and a rollback plan. Use an isolated VM or local container network. Avoid production or third-party targets.

## 2. Safe example: Windows logon telemetry

1. On your own Windows VM, verify security auditing and event collection are configured.
2. Sign in with a designated test account and record the approximate UTC time.
3. If appropriate, make only a small number of incorrect-password attempts; stop well before account lockout.
4. In your log platform, look for Windows Security Event IDs **4624** (successful logon) and **4625** (failed logon).
5. Compare the timestamps, host, account, and logon type to the expected activity. Note missing events and ingestion delays.

**Illustrative Splunk search** (adapt indexes and field names to your own data):

```spl
index=<YOUR_WINDOWS_INDEX> (EventCode=4624 OR EventCode=4625)
| stats count by host EventCode
```

Do not assume a matching event proves an attack. Interpret it in context.

## 3. Optional web telemetry exercise

Browse an intentionally vulnerable **local** training app while passively observing HTTP requests with a proxy. Record the endpoint, response code, and security headers. Do not test unrelated websites or attempt data extraction.

## 4. Evidence record

| Field | Value |
| --- | --- |
| Date and environment | Not yet recorded |
| Authorization and target | Not yet recorded |
| Hypothesis | Not yet recorded |
| Test action | Not yet recorded |
| Expected telemetry | Not yet recorded |
| Actual telemetry | Not yet recorded |
| Detection / alert outcome | Not tested |
| False positives and gaps | Not yet evaluated |
| Hardening recommendation | Not yet recorded |

## 5. Reporting

Write a short case study: objective → environment → authorized action → evidence → interpretation → remediation → retest. Redact IPs, usernames, tokens, and personal data. Never present proposed detections as validated results.
