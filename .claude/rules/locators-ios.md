# iOS Locator Rules (Appium + WebDriverAgent)

## Priority order (MUST follow)
1. **-ios predicate string** (preferred)
2. **accessibility id** (only if stable id, not full sentence)
3. **-ios class chain**
4. **XPath** (last resort)

## Why predicate-first
- Faster and more stable than deep XPath
- Works well when elements expose `name/label/value`

## Predicate patterns
- Prefer `CONTAINS` with a **short, distinctive keyword** (10–25 chars), not full sentences:
  - ✅ `label CONTAINS "identify your face"`
  - ❌ `label == "We cannot identify your face in these photos..."` (too strict/fragile)
- When multiple matches exist, add `type` constraint:
  - `type == "XCUIElementTypeButton" AND label CONTAINS "Continue"`

## Accessibility id usage
- Use when dev provides stable identifiers:
  - `name == "showEidView"` => use accessibility id `"showEidView"`
- Avoid using full visible text as accessibility id (breaks with copy changes / localization).

## XPath rules (only if unavoidable)
- Keep XPath as short as possible.
- Avoid absolute paths through the whole hierarchy.
- Must include a comment in config explaining why predicate/class chain cannot be used.

## Localization note
If the app is multi-language, predicate-by-visible-text is fragile.
Prefer accessibility ids or semantic ids where possible.

## eKYC SDK Examples
- btn_start_face: predicate string with "showEidView"
- view_result: short predicate on visible text
- Avoid deep XPath chains for SDK UI elements
