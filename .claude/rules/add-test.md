# Command: Add a New Test Scenario

## Goal
Add a new eKYC scenario test that is stable and debuggable on real devices.

## Steps
1. **Define scenario**
   - What is the expected behavior?
   - What is the fail condition?
   - What artifacts do you need to prove it?

2. **Choose scope**
   - Prefer minimal steps to reach the assertion point.
   - Avoid unnecessary navigation.

3. **Add/adjust locators**
   - Update centralized locator config only (no inline locators).
   - Follow locator rules:
     - iOS: predicate-first
     - Android: id/desc-first

4. **Implement waits**
   - Use explicit waits.
   - Avoid arbitrary sleeps.

5. **Add assertions**
   - Assert both:
     - “We are on the expected screen/state”
     - “Expected result is shown / error handled”

6. **Artifacts**
   - Ensure screenshot + page source + logs are captured on failure.

7. **Run stability**
   - Run locally with repeat:
     - `pytest <test_file> --count=10 -v`
   - If flaky, use the triage playbook.

## Definition of done
- Passes at least 10 repeats without intermittent failures (or a known, documented device issue).
- Produces useful artifacts when it fails.
