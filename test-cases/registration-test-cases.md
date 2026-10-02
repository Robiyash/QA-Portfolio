# Mobile Registration — Test Cases

## Overview

This document contains manual test cases for a mobile application's user registration flow.

### Scope

The registration flow includes:

- Phone number input
- Verification code
- Validation
- Network conditions
- Application state changes
- Error handling

### Test Environment

- Platform: Android
- Test type: Manual
- Test level: Functional, negative, UI, usability, network
- Network: Wi-Fi / Mobile data

---

## Test Cases

### TC-001 — Registration with a valid phone number

Priority: High  
Type: Positive / Functional

Preconditions:
- The application is installed.
- The user is not registered.
- Internet connection is available.

Steps:
1. Open the application.
2. Tap the "Register" button.
3. Enter a valid phone number.
4. Tap "Continue".

Expected Result:
- The phone number is accepted.
- The user is redirected to the verification screen.
- A verification code is sent to the provided phone number.

---

### TC-002 — Registration with an empty phone number

Priority: High  
Type: Negative / Validation

Preconditions:
- The application is installed.
- The registration screen is open.

Steps:
1. Leave the phone number field empty.
2. Tap "Continue".

Expected Result:
- The user cannot continue.
- A validation message indicates that the phone number is required.

---

### TC-003 — Registration with an invalid phone number format

Priority: High  
Type: Negative / Validation

Steps:
1. Open the registration screen.
2. Enter an invalid phone number containing letters or unsupported characters.
3. Tap "Continue".

Expected Result:
- The application rejects the invalid input.
- A clear validation message is displayed.
- The user cannot proceed to verification.

---

### TC-004 — Registration with a phone number that is too short

Priority: Medium  
Type: Negative / Boundary

Steps:
1. Open the registration screen.
2. Enter a phone number with fewer digits than required.
3. Tap "Continue".

Expected Result:
- The application displays a validation error.
- The user cannot proceed until a valid phone number is entered.

---

### TC-005 — Registration with a phone number that is too long

Priority: Medium  
Type: Negative / Boundary

Steps:
1. Open the registration screen.
2. Enter a phone number containing more digits than allowed.
3. Tap "Continue".

Expected Result:
- The application prevents invalid input or displays a validation error.
- The user cannot proceed with an invalid phone number.

---

### TC-006 — Verification with an invalid code

Priority: High  
Type: Negative / Functional

Preconditions:
- A valid phone number has been submitted.
- The verification screen is displayed.

Steps:
1. Enter an incorrect verification code.
2. Tap "Verify" or "Continue".

Expected Result:
- The verification attempt is rejected.
- An appropriate error message is displayed.
- The user remains on the verification screen.

---

### TC-007 — Verification with an expired code

Priority: High  
Type: Negative / Functional

Preconditions:
- A verification code has been generated.
- The code has expired.

Steps:
1. Enter the expired verification code.
2. Tap "Verify".

Expected Result:
- The expired code is rejected.
- The application informs the user that the code has expired.
- The user is given an option to request a new code, if supported.

---

### TC-008 — Verification with an empty code

Priority: Medium  
Type: Negative / Validation

Steps:
1. Open the verification screen.
2. Leave the verification code field empty.
3. Tap "Verify".

Expected Result:
- The verification request is not submitted.
- A validation message indicates that the code is required.

---

### TC-009 — Repeated use of an incorrect verification code

Priority: High  
Type: Negative / Security

Steps:
1. Enter an incorrect verification code.
2. Submit the code.
3. Repeat the action several times using incorrect codes.

Expected Result:
- The application handles repeated failed attempts according to the defined security requirements.
