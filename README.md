# Repo Guide (eKYC SDK Automation)

This repository contains a **Pytest + Appium 2** automation framework for **eKYC SDK** (Face Capture & NFC) on **real iOS/Android devices**.

## What matters most
- **Stability > coverage**: prioritize reliable, repeatable tests (stress/repeat).
- **Artifacts-first debugging**: every failure should have enough evidence (screenshot + page source + device logs).
- **Locator discipline**:
  - iOS: **predicate-first**, avoid long XPath.
  - Android: **resource-id/content-desc first**, XPath last.

## Where to look
- Rules: `.claude/rules/*`
- Playbooks (commands): `.claude/commands/*`
- Tests: `tests/`
- Common utilities: `utils/`
- Artifacts: `reports/`, `screenshots/`, `logs/`

If you add or modify tests, follow the playbook in `.claude/commands/add-test.md`.

## Rules & Standards
See `.claude/rules/` for detailed guidelines on:
- Project structure (project-structure.md)
- Testing conventions (testing.md)
- Locator priorities (locators-ios.md, locators-android.md)
- Debugging artifacts (debugging.md)
