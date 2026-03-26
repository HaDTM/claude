# Project Structure Rules

## Source of truth
- Tests live in: `tests/`
- Shared fixtures live in: `conftest.py`
- Utilities live in: `utils/`
- App binaries live in: `apps/` (`.ipa`, `.apk`)
- Artifacts:
  - `reports/` (page source dumps, debug text files)
  - `screenshots/` (on failure)
  - `logs/` (iOS syslog / Android logcat)

## Test file naming
- Use `tests/test_<feature>_<scenario>.py`
- Keep each test file focused on **one scenario family**.
- Prefer smaller tests over “mega tests”.

## Utility modules responsibilities
- `utils/platform_config.py`: centralized platform differences (locators, ids, timeouts)
- `utils/device_app_manager.py`: install/uninstall/cleanup
- `utils/device_log_capture.py`: syslog/logcat capture
- `utils/logger.py`: logging setup

## Anti-patterns
- Do not scatter `if platform == "ios"` across test code. Keep platform branching in `utils/` only.
- Do not write locators inline in tests (except temporary debugging).
