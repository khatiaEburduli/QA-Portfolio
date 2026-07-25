# SauceDemo - Login Test Cases

## Test Environment

- **Application:** SauceDemo
- **URL:** https://www.saucedemo.com/
- **Browser:** Google Chrome
- **Testing Type:** Manual Testing

---

## TC-001 - Verify login with valid credentials

| Field | Details |
|-------|---------|
| Test Case ID | TC-001 |
| Priority | High |
| Preconditions | User is on the Login page. |
| Test Steps | 1. Enter a valid username (`standard_user`).<br>2. Enter a valid password (`secret_sauce`).<br>3. Click the **Login** button. |
| Expected Result | User is successfully logged in and redirected to the Inventory page. |
| Actual Result | User was successfully logged in and redirected to the Inventory page.|
| Status | Passed |


## TC-002: Verify login with an invalid username

| Field | Details |
|-------|---------|
| Test Case ID | TC-002 |
| Title | Verify login with an invalid username |
| Priority | High |
| Preconditions | User is on the SauceDemo Login page. |
| Test Steps | 1. Enter an invalid username.<br>2. Enter a valid password.<br>3. Click **Login**. |
| Test Data | Username: `invalid_user`<br>Password: `secret_sauce` |
| Expected Result | An error message is displayed. |
| Actual Result | The application displayed the error message: **"Epic sadface: Username and password do not match any user in this service."** |
| Status | Passed |

---

## TC-003: Verify login with an invalid password

| Field | Details |
|-------|---------|
| Test Case ID | TC-003 |
| Title | Verify login with an invalid password |
| Priority | High |
| Preconditions | User is on the SauceDemo Login page. |
| Test Steps | 1. Enter a valid username.<br>2. Enter an invalid password.<br>3. Click **Login**. |
| Test Data | Username: `standard_user`<br>Password: `invalid_password` |
| Expected Result | An error message is displayed. |
| Actual Result | The application displayed the error message: **"Epic sadface: Username and password do not match any user in this service."** |
| Status | Passed |

---

## TC-004: Verify login with an empty username

| Field | Details |
|-------|---------|
| Test Case ID | TC-004 |
| Title | Verify login with an empty username |
| Priority | High |
| Preconditions | User is on the SauceDemo Login page. |
| Test Steps | 1. Leave Username empty.<br>2. Enter a valid password.<br>3. Click **Login**. |
| Test Data | Password: `secret_sauce` |
| Expected Result | An error message indicating that the username is required is displayed. |
| Actual Result | The application displayed the error message: **"Epic sadface: Username is required."** |
| Status | Passed |

---

## TC-005: Verify login with an empty password

| Field | Details |
|-------|---------|
| Test Case ID | TC-005 |
| Title | Verify login with an empty password |
| Priority | High |
| Preconditions | User is on the SauceDemo Login page. |
| Test Steps | 1. Enter a valid username.<br>2. Leave Password empty.<br>3. Click **Login**. |
| Test Data | Username: `standard_user` |
| Expected Result | An error message indicating that the password is required is displayed. |
| Actual Result | The application displayed the error message: **"Epic sadface: Password is required."** |
| Status | Passed |

---

## TC-006: Verify login with both fields empty

| Field | Details |
|-------|---------|
| Test Case ID | TC-006 |
| Title | Verify login with both fields empty |
| Priority | High |
| Preconditions | User is on the SauceDemo Login page. |
| Test Steps | 1. Leave Username and Password empty.<br>2. Click **Login**. |
| Test Data | None |
| Expected Result | An error message indicating that the username is required is displayed. |
| Actual Result | The application displayed the error message: **"Epic sadface: Username is required."** |
| Status | Passed |

---

## TC-007: Verify login using the Enter key

| Field | Details |
|-------|---------|
| Test Case ID | TC-007 |
| Title | Verify login using the Enter key |
| Priority | Medium |
| Preconditions | User is on the SauceDemo Login page. |
| Test Steps | 1. Enter valid credentials.<br>2. Press **Enter**. |
| Test Data | Username: `standard_user`<br>Password: `secret_sauce` |
| Expected Result | The user is successfully logged in. |
| Actual Result | The user was successfully logged in after pressing the Enter key. |
| Status | Passed |

---

## TC-008: Verify that the Password field masks entered characters

| Field | Details |
|-------|---------|
| Test Case ID | TC-008 |
| Title | Verify that the Password field masks entered characters |
| Priority | Medium |
| Preconditions | User is on the SauceDemo Login page. |
| Test Steps | 1. Click the Password field.<br>2. Enter a password. |
| Test Data | `secret_sauce` |
| Expected Result | Password characters are hidden. |
| Actual Result | Password characters were displayed as masked dots. |
| Status | Passed |

---

## TC-009: Verify the Tab order on the Login page

| Field | Details |
|-------|---------|
| Test Case ID | TC-009 |
| Title | Verify the Tab order on the Login page |
| Priority | Medium |
| Preconditions | User is on the SauceDemo Login page. |
| Test Steps | 1. Press the **Tab** key repeatedly.<br>2. Observe the focus order. |
| Test Data | None |
| Expected Result | Focus moves in the following order: Username → Password → Login button. |
| Actual Result | Focus moved in the expected order: Username → Password → Login button. |
| Status | Passed |
