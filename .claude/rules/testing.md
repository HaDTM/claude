# Testing Rules (Pytest + Appium)

## Goals
- Tests must be **repeatable** on real devices.
- Prefer **stable functional coverage** over brittle UI coverage.

## Pytest conventions
- Test names should describe intent: `test_<feature>_<expected_behavior>()`
- Use explicit assertions with meaningful messages.
- Keep setup/teardown in fixtures (do not copy/paste driver init).

## Markers (recommended)
Add markers to help local runs:
- `@pytest.mark.smoke` - minimal sanity
- `@pytest.mark.stability` - repeat/stress style
- `@pytest.mark.ios`, `@pytest.mark.android` - platform scoping
- `@pytest.mark.nfc`, `@pytest.mark.face` - feature scoping

## Repeat / stress runs
- Use `pytest-repeat` for stability:
  - Prefer `--count=5/10` during development
  - Use higher counts for regression/stability checks
- If a test is flaky, do not “fix” by adding random sleeps.
  - Fix waits, state handling, or app transitions.

## Wait strategy
- Prefer explicit waits (WebDriverWait) over hard sleeps.
- Any `sleep()` must have a comment explaining why no deterministic wait is possible.

## Timeouts
- Default timeouts should live in config (`utils/platform_config.py`).
- Keep timeouts reasonable, but allow longer waits for camera/NFC flows.

## eKYC SDK Specific
- Face capture should have longer timeout (30-60s camera setup)
- NFC on iOS requires manual CCCD placement (document as limitation)
- Use markers: @pytest.mark.face, @pytest.mark.nfc for organization
