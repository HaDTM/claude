# Android Locator Rules (Appium + UiAutomator2)

## Priority order (MUST follow)
1. **resource-id** (By.ID)
2. **content-desc** (accessibility id)
3. **UiAutomator** textContains/descriptionContains (fallback)
4. **XPath** (last resort)

## Why id/desc-first
- Most stable across layout changes
- Fast
- Less brittle than hierarchy-based XPath

## Text-based fallback
Use only if id/desc is not available:
- `textContains("...")`
- `descriptionContains("...")`

## XPath rules (only if unavoidable)
- Avoid absolute hierarchy XPaths.
- Prefer attribute-based XPath (short), but still treat as fallback.
- Add a comment explaining why ID/desc cannot be used.

## Consistency
All Android locators must be stored centrally (config), not embedded in tests.
