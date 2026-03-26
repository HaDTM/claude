# Debugging & Artifacts Rules

## Must-have artifacts on failure
- Screenshot (current screen)
- Page source dump (XML)
- Device logs
  - iOS: syslog
  - Android: logcat

## Naming conventions (recommended)
- Screenshot:
  - `screenshots/FAIL_<test_name>_<YYYYMMDD_HHMMSS>.png`
- Page source:
  - `reports/page_source_<test_name>_<YYYYMMDD_HHMMSS>.xml` (or `.txt`)
- Logs:
  - `logs/<test_name>_<PASS|FAIL>_<YYYYMMDD_HHMMSS>.log`

## When to dump page source
- Always on failure
- Additionally after major transitions:
  - launching SDK view
  - after permission dialogs
  - after background/resume
  - after rotation

## Anti-patterns
- Do not “fix” flaky failures without evidence.
- Do not increase timeouts blindly; verify what the app is actually doing via logs/page source.
