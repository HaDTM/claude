# Testing Guide

This document serves as a brief overview of guidelines for testing our eKYC SDK automation framework using Pytest and Appium 2.0.

## Overview
- Use Pytest for structured testing.
- Implement Appium 2.0 with real devices for testing iOS and Android apps.

## Stress/Repeat Tests
- Design tests to automatically repeat a series of scenarios to identify potential failures under load.
- Utilize logging to capture test results for analysis.

## Artifacts Collection
- Ensure that logs, page-source dumps, and screenshots are captured during test runs to aid in debugging and analysis.

## Locator Strategy
- **iOS:** Use predicates wherever possible.
- **Android:** Prioritize resource-id and content-desc, using XPath as a fallback option.

## CI/CD Assumption
- This framework does not assume continuous integration or deployment workflows.

## Adding Test Scenarios
- Create a new test file in the `tests` directory.
- Follow the existing structure and naming conventions.

## Investigating Flaky Tests
- Focus on tests that fail intermittently:
  - Inspect logs and artifacts.
  - Check device background processes (like camera, rotation).
  - Evaluate how navigation and state persistence work during resumes.

## Conclusion
- This guide provides the foundation for effective testing within the eKYC SDK framework.