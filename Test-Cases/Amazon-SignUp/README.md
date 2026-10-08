# Amazon Sign Up Form — Test Cases

Test design exercise: **64 test cases** for the Amazon Sign Up form, written against a specification using **equivalence partitioning** and **boundary value analysis**. The cases were designed, not executed against the live Amazon website.

Download the Excel version: [Amazon_SignUp_Test_Cases.xlsx](Amazon_SignUp_Test_Cases.xlsx)

## Specification rules

| Field | Rule |
|-------|------|
| First Name, Last Name | 1–64 characters; letters, numbers and special characters allowed; leading/trailing spaces trimmed |
| Mobile Number or Email | 5–256 characters; any characters allowed (no email-format validation) |
| Password | 8–16 characters; at least two of three types: letters, numbers, punctuation |
| Re-enter Password | Must match Password exactly (case-sensitive) |

## Coverage

| Area | Test cases |
|------|-----------:|
| First Name | 13 |
| Last Name | 10 |
| Mobile Number or Email | 14 |
| Password | 17 |
| Re-enter Password | 5 |
| Full Form | 5 |
| **Total** | **64** |

By type: Boundary 18 · Positive 24 · Negative 22

Default precondition for all cases: *Sign Up page is opened* (other preconditions are shown in the steps).

## First Name

| ID | Test case | Type | Priority | Steps | Expected result |
|----|-----------|------|----------|-------|-----------------|
| TC-01 | First Name field accepts input when entering 1 character | Boundary | High | 1. Enter 1 character into First Name field (e.g. 'A')<br>2. Fill all other fields with valid values<br>3. Click Continue | Form accepts the value; no validation message is shown for First Name |
| TC-02 | First Name field accepts input when entering 64 characters | Boundary | High | 1. Enter a string of exactly 64 characters into First Name field<br>2. Fill all other fields with valid values<br>3. Click Continue | Form accepts the value |
| TC-03 | First Name field rejects input when entering 65 characters | Boundary | High | 1. Enter a string of 65 characters into First Name field<br>2. Fill all other fields with valid values<br>3. Click Continue | Form blocks submission and shows a max-length validation message |
| TC-04 | First Name field rejects submission when field is left empty | Boundary | High | 1. Leave First Name field empty<br>2. Fill all other fields with valid values<br>3. Click Continue | Form blocks submission and shows a required-field validation message |
| TC-05 | First Name field accepts input when entering only letters | Positive | Medium | 1. Enter a value consisting only of letters (e.g. 'Michael')<br>2. Fill all other fields with valid values<br>3. Click Continue | Form accepts the value |
| TC-06 | First Name field accepts input when entering only numbers | Positive | Medium | 1. Enter a value consisting only of digits (e.g. '123456')<br>2. Fill all other fields with valid values<br>3. Click Continue | Form accepts the value, as digits are allowed per specification |
| TC-07 | First Name field accepts input when entering only special characters | Positive | Medium | 1. Enter a value consisting only of special characters (e.g. '@#$%')<br>2. Fill all other fields with valid values<br>3. Click Continue | Form accepts the value, as special characters are allowed per specification |
| TC-08 | First Name field accepts input when entering a combination of letters, numbers and special characters | Positive | Medium | 1. Enter a mixed value (e.g. 'Anna_2024!')<br>2. Fill all other fields with valid values<br>3. Click Continue | Form accepts the value |
| TC-09 | First Name field trims leading and trailing spaces | Positive | Low | 1. Enter a value with spaces before and after the text (e.g. '  Anna  ')<br>2. Fill all other fields with valid values<br>3. Click Continue | Leading and trailing spaces are removed automatically and the trimmed value is stored |
| TC-10 | First Name field treats whitespace-only input as empty | Negative | Low | 1. Enter only space characters into First Name field<br>2. Fill all other fields with valid values<br>3. Click Continue | Form treats the value as empty and blocks submission with a required-field message |
| TC-11 | First Name field behavior when entering a SQL injection string | Negative | High | 1. Enter a value such as "' OR '1'='1" into First Name field<br>2. Fill all other fields with valid values<br>3. Click Continue | Input is stored/escaped as plain text; no database error is exposed and no unintended query execution occurs |
| TC-12 | First Name field behavior when entering a script tag | Negative | High | 1. Enter a value such as '&lt;script&gt;alert(1)&lt;/script&gt;' into First Name field<br>2. Fill all other fields with valid values<br>3. Click Continue | Input is rendered as plain text/escaped; no script executes on the page |
| TC-13 | First Name field accepts input when entering non-English letters | Positive | Medium | 1. Enter a value using a non-Latin alphabet (e.g. Georgian 'გიორგი', Russian 'Анна', or Chinese '伟')<br>2. Fill all other fields with valid values<br>3. Click Continue | Form accepts the value, or shows a clear validation message if non-Latin letters are not supported (open question - see Open questions below) |

## Last Name

| ID | Test case | Type | Priority | Steps | Expected result |
|----|-----------|------|----------|-------|-----------------|
| TC-14 | Last Name field accepts input when entering 1 character | Boundary | High | 1. Enter 1 character into Last Name field (e.g. 'K')<br>2. Fill all other fields with valid values<br>3. Click Continue | Form accepts the value; no validation message is shown for Last Name |
| TC-15 | Last Name field accepts input when entering 64 characters | Boundary | High | 1. Enter a string of exactly 64 characters into Last Name field<br>2. Fill all other fields with valid values<br>3. Click Continue | Form accepts the value |
| TC-16 | Last Name field rejects input when entering 65 characters | Boundary | High | 1. Enter a string of 65 characters into Last Name field<br>2. Fill all other fields with valid values<br>3. Click Continue | Form blocks submission and shows a max-length validation message |
| TC-17 | Last Name field rejects submission when field is left empty | Boundary | High | 1. Leave Last Name field empty<br>2. Fill all other fields with valid values<br>3. Click Continue | Form blocks submission and shows a required-field validation message |
| TC-18 | Last Name field accepts input when entering a combination of numbers and special characters only | Positive | Medium | 1. Enter a value such as '2024_#7'<br>2. Fill all other fields with valid values<br>3. Click Continue | Form accepts the value, as digits and special characters are allowed per specification |
| TC-19 | Last Name field trims leading and trailing spaces | Positive | Low | 1. Enter a value with spaces before and after the text (e.g. '  Petrov  ')<br>2. Fill all other fields with valid values<br>3. Click Continue | Leading and trailing spaces are removed automatically and the trimmed value is stored |
| TC-20 | Last Name field behavior when entering emoji characters | Negative | Medium | 1. Enter a value containing an emoji (e.g. 'Smith😊')<br>2. Fill all other fields with valid values<br>3. Click Continue | Form either accepts or rejects consistently with First Name field rules and does not break page rendering |
| TC-21 | Last Name field accepts input when entering non-English letters | Positive | Medium | 1. Enter a value using a non-Latin alphabet (e.g. Georgian 'ბერიძე', Russian 'Иванова', or Chinese '王')<br>2. Fill all other fields with valid values<br>3. Click Continue | Form accepts the value, or shows a clear validation message if non-Latin letters are not supported (open question - see Open questions below) |
| TC-22 | Last Name field behavior when entering a SQL injection string | Negative | High | 1. Enter a value such as "' OR '1'='1" into Last Name field<br>2. Fill all other fields with valid values<br>3. Click Continue | Input is stored/escaped as plain text; no database error is exposed and no unintended query execution occurs |
| TC-23 | Last Name field behavior when entering a script tag | Negative | High | 1. Enter a value such as '&lt;script&gt;alert(1)&lt;/script&gt;' into Last Name field<br>2. Fill all other fields with valid values<br>3. Click Continue | Input is rendered as plain text/escaped; no script executes on the page |

## Mobile Number or Email

| ID | Test case | Type | Priority | Steps | Expected result |
|----|-----------|------|----------|-------|-----------------|
| TC-24 | Mobile Number or Email field accepts input when entering 5 characters | Boundary | High | 1. Enter a 5-character value (e.g. 'a@b.c') into Mobile/Email field<br>2. Fill all other fields with valid values<br>3. Click Continue | Form accepts the value; no length validation message is shown |
| TC-25 | Mobile Number or Email field accepts input when entering 256 characters | Boundary | High | 1. Enter a value of exactly 256 characters into Mobile/Email field<br>2. Fill all other fields with valid values<br>3. Click Continue | Form accepts the value |
| TC-26 | Mobile Number or Email field rejects input when entering 257 characters | Boundary | High | 1. Enter a value of 257 characters into Mobile/Email field<br>2. Fill all other fields with valid values<br>3. Click Continue | Form blocks submission and shows a max-length validation message |
| TC-27 | Mobile Number or Email field rejects input when entering 4 characters | Boundary | High | 1. Enter a 4-character value into Mobile/Email field<br>2. Fill all other fields with valid values<br>3. Click Continue | Form blocks submission and shows a min-length validation message |
| TC-28 | Mobile Number or Email field rejects submission when field is left empty | Boundary | High | 1. Leave Mobile/Email field empty<br>2. Fill all other fields with valid values<br>3. Click Continue | Form blocks submission and shows a required-field validation message |
| TC-29 | Mobile Number or Email field accepts input when entering a standard email format | Positive | High | 1. Enter a standard email address (e.g. 'testuser2026@example.com')<br>2. Fill all other fields with valid values<br>3. Click Continue | Form accepts the value and proceeds with registration |
| TC-30 | Mobile Number or Email field accepts input when entering a mobile number with country code | Positive | High | 1. Enter a mobile number with country code (e.g. '+995555123456')<br>2. Fill all other fields with valid values<br>3. Click Continue | Form accepts the value and proceeds with registration |
| TC-31 | Mobile Number or Email field accepts input when entering an email without the @ symbol | Positive | Medium | 1. Enter a value such as 'testuserexample.com'<br>2. Fill all other fields with valid values<br>3. Click Continue | Form accepts the value, since any type of characters is allowed per specification, and no email-format validation is applied |
| TC-32 | Mobile Number or Email field accepts input when entering a mobile number with letters mixed in | Positive | Medium | 1. Enter a value such as '555abc1234'<br>2. Fill all other fields with valid values<br>3. Click Continue | Form accepts the value, since any type of characters is allowed per specification |
| TC-33 | Mobile Number or Email field behavior when entering an already registered account value | Negative | High | **Precondition:** An account already exists with the given email/mobile number<br>1. Enter the email/mobile number of an existing account<br>2. Fill all other fields with valid values<br>3. Click Continue | Form blocks submission and informs the user the account already exists |
| TC-34 | Mobile Number or Email field behavior when pasting text containing line breaks | Negative | Low | **Precondition:** A multi-line string is copied to clipboard<br>1. Paste the copied multi-line string into the field<br>2. Fill all other fields with valid values<br>3. Click Continue | Line breaks are stripped or the field rejects the paste without breaking the page layout |
| TC-35 | Mobile Number or Email field accepts input when entering special characters only | Positive | Low | 1. Enter a value such as '#$%^&amp;*()'<br>2. Fill all other fields with valid values<br>3. Click Continue | Form accepts the value, as any characters are allowed per specification |
| TC-36 | Mobile Number or Email field behavior when entering a SQL injection string | Negative | High | 1. Enter a value such as "' OR '1'='1" into Mobile/Email field<br>2. Fill all other fields with valid values<br>3. Click Continue | Input is stored/escaped as plain text; no database error is exposed and no unintended query execution occurs |
| TC-37 | Mobile Number or Email field behavior when entering a script tag | Negative | High | 1. Enter a value such as '&lt;script&gt;alert(1)&lt;/script&gt;' into Mobile/Email field<br>2. Fill all other fields with valid values<br>3. Click Continue | Input is rendered as plain text/escaped; no script executes on the page |

## Password

| ID | Test case | Type | Priority | Steps | Expected result |
|----|-----------|------|----------|-------|-----------------|
| TC-38 | Password field accepts input when entering 8 characters | Boundary | High | 1. Enter an 8-character password combining letters and numbers (e.g. 'Abcdef12')<br>2. Enter the same value in Re-enter Password<br>3. Fill all other fields with valid values<br>4. Click Continue | Form accepts the password |
| TC-39 | Password field accepts input when entering 16 characters | Boundary | High | 1. Enter a 16-character password combining letters and punctuation (e.g. 'Abcdefgh!!!!!!!!')<br>2. Enter the same value in Re-enter Password<br>3. Fill all other fields with valid values<br>4. Click Continue | Form accepts the password |
| TC-40 | Password field rejects input when entering 7 characters | Boundary | High | 1. Enter a 7-character password<br>2. Match it in Re-enter Password<br>3. Fill all other fields with valid values<br>4. Click Continue | Form blocks submission and shows a min-length validation message |
| TC-41 | Password field rejects input when entering 17 characters | Boundary | High | 1. Enter a 17-character password<br>2. Match it in Re-enter Password<br>3. Fill all other fields with valid values<br>4. Click Continue | Form blocks submission and shows a max-length validation message |
| TC-42 | Password field rejects input when entering only letters | Negative | High | 1. Enter a password consisting only of letters, 8-16 characters (e.g. 'AbcdEfgh')<br>2. Match it in Re-enter Password<br>3. Fill all other fields with valid values<br>4. Click Continue | Form blocks submission, since a single character type is not enough - at least two of letters/numbers/punctuation are required |
| TC-43 | Password field rejects input when entering only numbers | Negative | High | 1. Enter a password consisting only of digits, 8-16 characters (e.g. '12345678')<br>2. Match it in Re-enter Password<br>3. Fill all other fields with valid values<br>4. Click Continue | Form blocks submission, since a single character type is not enough |
| TC-44 | Password field rejects input when entering only punctuation marks | Negative | Medium | 1. Enter a password consisting only of punctuation marks, 8-16 characters (e.g. '!!!!!!!!')<br>2. Match it in Re-enter Password<br>3. Fill all other fields with valid values<br>4. Click Continue | Form blocks submission, since a single character type is not enough |
| TC-45 | Password field accepts input when entering letters and numbers combined, without punctuation | Positive | High | 1. Enter a password such as 'Passw0rd1'<br>2. Match it in Re-enter Password<br>3. Fill all other fields with valid values<br>4. Click Continue | Form accepts the password, since any two of the three character types is sufficient |
| TC-46 | Password field accepts input when entering letters and punctuation combined, without numbers | Positive | High | 1. Enter a password such as 'Password!!'<br>2. Match it in Re-enter Password<br>3. Fill all other fields with valid values<br>4. Click Continue | Form accepts the password, since any two of the three character types is sufficient |
| TC-47 | Password field accepts input when entering numbers and punctuation combined, without letters | Positive | High | 1. Enter a password such as '12345678!!'<br>2. Match it in Re-enter Password<br>3. Fill all other fields with valid values<br>4. Click Continue | Form accepts the password, since any two of the three character types is sufficient |
| TC-48 | Password field accepts input when entering a combination of letters, numbers and multiple punctuation marks | Positive | Medium | 1. Enter a password such as 'Ab1!Cd2&amp;Ef3#'<br>2. Match it in Re-enter Password<br>3. Fill all other fields with valid values<br>4. Click Continue | Form accepts the password, as any punctuation marks are allowed per specification |
| TC-49 | Password field trims leading and trailing spaces before validation | Positive | Low | 1. Enter a password with a leading and trailing space (e.g. ' Passw0rd! ')<br>2. Match the trimmed value in Re-enter Password<br>3. Fill all other fields with valid values<br>4. Click Continue | Leading and trailing spaces are trimmed and the remaining value is validated against the length and character rules |
| TC-50 | Password field behavior when a space character is entered in the middle of the password | Negative | Medium | 1. Enter a password with a space in the middle (e.g. 'Pass word1')<br>2. Match it exactly in Re-enter Password<br>3. Fill all other fields with valid values<br>4. Click Continue | Form behavior is verified against the actual rule (open question: whether a middle space is allowed, and if allowed, whether it counts as a valid character type; see Open questions below) |
| TC-51 | Password field behavior when entering emoji or non-English characters | Negative | Medium | 1. Enter a password containing emoji or non-Latin letters (e.g. 'Passw0rd😊' or 'Пароль1!')<br>2. Match it in Re-enter Password<br>3. Fill all other fields with valid values<br>4. Click Continue | Form either accepts or rejects consistently (open question: whether emoji/non-Latin characters count as valid letters; see Open questions below) |
| TC-52 | Password field behavior when entering a SQL injection string | Negative | High | 1. Enter a value such as "' OR '1'='1" into the Password field<br>2. Match it in Re-enter Password<br>3. Fill all other fields with valid values<br>4. Click Continue | Input is stored/escaped as plain text; no database error is exposed and no unintended query execution occurs |
| TC-53 | Password field behavior when entering a script tag | Negative | High | 1. Enter a value such as '&lt;script&gt;alert(1)&lt;/script&gt;' into the Password field<br>2. Match it in Re-enter Password<br>3. Fill all other fields with valid values<br>4. Click Continue | Input is rendered as plain text/escaped and treated as a regular password string; no script executes on the page |
| TC-54 | Password field masks entered characters | Positive | Low | 1. Enter any valid password into the Password field<br>2. Observe the field content | Entered characters are displayed as masked dots/asterisks by default |

## Re-enter Password

| ID | Test case | Type | Priority | Steps | Expected result |
|----|-----------|------|----------|-------|-----------------|
| TC-55 | Submission proceeds when Re-enter Password matches Password exactly | Positive | High | 1. Enter a valid password in Password field<br>2. Enter the identical value in Re-enter Password field<br>3. Fill all other fields with valid values<br>4. Click Continue | Form accepts both fields and registration proceeds |
| TC-56 | Submission is blocked when Re-enter Password does not match Password | Negative | High | 1. Enter a valid password in Password field<br>2. Enter a different valid value in Re-enter Password field<br>3. Fill all other fields with valid values<br>4. Click Continue | Form blocks submission and shows a 'passwords do not match' validation message |
| TC-57 | Submission is blocked when Re-enter Password is left empty | Negative | High | 1. Enter a valid password in Password field<br>2. Leave Re-enter Password field empty<br>3. Fill all other fields with valid values<br>4. Click Continue | Form blocks submission and shows a required-field validation message |
| TC-58 | Submission is blocked when Re-enter Password differs from Password only in letter case | Negative | Medium | 1. Enter 'Passw0rd!' in Password field<br>2. Enter 'passw0rd!' (different case) in Re-enter Password field<br>3. Fill all other fields with valid values<br>4. Click Continue | Form treats the values as non-matching (case-sensitive comparison) and blocks submission with a mismatch message |
| TC-59 | Re-enter Password field masks entered characters | Positive | Low | 1. Enter any value into the Re-enter Password field<br>2. Observe the field content | Entered characters are displayed as masked dots/asterisks by default |

## Full Form

| ID | Test case | Type | Priority | Steps | Expected result |
|----|-----------|------|----------|-------|-----------------|
| TC-60 | Registration proceeds when all fields are filled with minimum boundary values | Positive | High | 1. Enter 1-character First Name, 1-character Last Name, 5-character Mobile/Email, 8-character valid Password, matching Re-enter Password<br>2. Click Continue | Form accepts all values and registration proceeds |
| TC-61 | Registration proceeds when all fields are filled with maximum boundary values | Positive | High | 1. Enter 64-character First Name, 64-character Last Name, 256-character Mobile/Email, 16-character valid Password, matching Re-enter Password<br>2. Click Continue | Form accepts all values and registration proceeds |
| TC-62 | Registration is blocked when multiple required fields are left empty simultaneously | Negative | Medium | 1. Leave First Name and Password fields empty, fill the remaining fields with valid values<br>2. Click Continue | Form blocks submission and shows validation messages for both empty fields |
| TC-63 | Registration is blocked when all fields exceed their maximum length at the same time | Boundary | High | 1. Enter a 65-character First Name, 65-character Last Name, 257-character Mobile/Email, and 17-character Password (with matching Re-enter Password)<br>2. Click Continue | Form blocks submission and shows a max-length validation message for every field that exceeds its limit, without crashing or freezing the page |
| TC-64 | Page layout renders correctly when viewed at a mobile viewport width | Negative | Low | **Precondition:** Sign Up page is opened on a device/emulator with mobile screen width<br>1. Resize browser/open form on a mobile viewport<br>2. Inspect all fields and the Continue button | All fields and controls remain visible, aligned and usable without overlapping content |

## Open questions

Points where the specification is unclear and would be clarified with the product owner before testing:

- **TC-13 / TC-21:** are non-Latin letters (Georgian, Cyrillic, Chinese) allowed in First Name and Last Name?
- **TC-20:** are emoji allowed in name fields?
- **TC-50:** is a space allowed in the middle of the password, and does it count as a character type?
- **TC-51:** do emoji or non-Latin letters count as valid letters in the password?
