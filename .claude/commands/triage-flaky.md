# Command: Triage a Flaky Test (Mobile eKYC)

## Goal
Identify root cause of intermittent failures and fix deterministically.

## Checklist
1. **Reproduce**
   - Run with repeat:
     - `pytest <test> --count=20 -v -s`

2. **Collect artifacts**
   - screenshot
   - page source
   - syslog/logcat
   - timestamps for when it failed

3. **Classify common flaky causes**
   - Timing/waits (element appears later than expected)
   - Permission dialogs (camera/photos/NFC)
   - App in background / resume state not restored
   - Rotation transitions (layout reflow)
   - Camera session not ready / SDK state machine delays
   - Device performance / thermal throttling

4. **Fix strategy (preferred order)**
   - Add a deterministic wait for a **state anchor element**
   - Assert correct screen before interacting
   - Improve locator stability (reduce XPath, use predicate/id/desc)
   - Reset app state only if necessary (avoid over-resetting)
   - Add targeted retries only around known transient SDK steps (document why)

5. **Validate**
   - Re-run repeat after fix (`--count=20`)
   - Confirm artifacts are still produced on failures

## Output expectation
A flaky test should become:
- stable, or
- documented with a clear reason + mitigation (device limitation, known SDK issue).
