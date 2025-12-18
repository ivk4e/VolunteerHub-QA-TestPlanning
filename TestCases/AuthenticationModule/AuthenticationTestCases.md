# Module: Authentication

## Test Scenario: AUTH-SC-01: Volunteer login

### Test Cases

- TC-AUTH-001: Successful volunteer login

**Preconditions:**
- The user should be registered as a volunteer
- The user is on the login page

**Test Data:**
- Email: valid email with which the volunteer has been registered
- Password: valid password


| Email                   | Password   |
|-------------------------|------------|
| volunteer@gmail.com     | Test@1234  |
| ivan@abv.bg             | Test@1235  |

**Steps:**
1. Open the Home page.
2. Select the "Вход" tab.
3. Enter a valid email in the "Имейл" field.
4. Enter a valid password in the "Парола" field.
5. Ensure the checkbox "Влизам като организация" is NOT selected.
6. Click "Вход" button.

**Expected Result:**
- The user is successfully authenticated. 
- The user is redirected to the all initiatives page.
- Volunteer navigation menu is displayed.

---

- TC-AUTH-002: Volunteer login with invalid credentials

**Preconditions:**
- The user should be on the login page

**Test Data:**


| Scenario description           | Email                  | Password  |
|--------------------------------|------------------------|-----------|
| Incorrect password             | volunteer@gmail.com    | Wrong@123 |
| Non-existing email             | volunteaer@gmail.com   | Test@1234 |
| Empty email field              |                        | Test@1234 |
| Empty password field           | volunteer@gmail.com    |           |
| Both fields empty              |                        |           |


**Steps:**
1. Open the Home page.
2. Select the "Вход" tab.
3. Enter a valid email in the "Имейл" field.
4. Enter a valid password in the "Парола" field.
5. Ensure the checkbox "Влизам като организация" is NOT selected.
6. Click "Вход" button.

**Expected Result:**
- The user is NOT successfully authenticated. 
- The user remains on the login page.
- An error message appears - "Невалидни данни за вход."

---

- TC-AUTH-003: Volunteer login with "Влизам като организация" checkbox selected

**Preconditions:**
- The user should be on the login page

**Test Data:**
- Email: valid email with which the volunteer has been registered
- Password: valid password


| Email                   | Password   |
|-------------------------|------------|
| volunteer@gmail.com     | Test@1234  |


**Steps:**
1. Open the Home page.
2. Select the "Вход" tab.
3. Enter a valid email in the "Имейл" field.
4. Enter a valid password in the "Парола" field.
5. Ensure the checkbox "Влизам като организация" IS selected.
6. Click "Вход" button.

**Expected Result:**
- The user is NOT successfully authenticated. 
- The user remains on the login page.
- An error message appears - "Невалидни данни за вход."

---

## Test Scenario: AUTH-SC-02: Organization login

### Test Cases

- TC-AUTH-004: Successful organization login

**Preconditions:**
- The organization should be registered
- The user is on the login page

**Test Data:**
- Email: valid email with which the organization has been registered
- Password: valid password


| Email                   | Password   |
|-------------------------|------------|
| volunteerOrg@gmail.com  | Test@1234  |


**Steps:**
1. Open the Home page.
2. Select the "Вход" tab.
3. Enter a valid email in the "Имейл" field.
4. Enter a valid password in the "Парола" field.
5. Ensure the checkbox "Влизам като организация" IS selected.
6. Click "Вход" button.

**Expected Result:**
- The organization is successfully authenticated. 
- The organization is redirected to the all initiatives page.
- Organization navigation menu is displayed.

---

- TC-AUTH-005: Organization login with invalid credentials (and wrong checkbox)

**Preconditions:**
- The user is on the login page
- The user is a registered organization

**Test Data:**

| Scenario description                            | Email                   | Password   | Checkbox "Влизам като организация" |
|-------------------------------------------------|-------------------------|------------|------------------------------------|
| Without selecting organization checkbox         | volunteerOrg@gmail.com  | Test@1234  | NOT selected                       |
| Incorrect password                              | volunteerOrg@gmail.com  | Wrong@123  | Selected                           |
| Non-existing email                              | unknownOrg@gmail.com    | Test@1234  | Selected                           |
| Empty email field                               |                         | Test@1234  | Selected                           |
| Empty password field                            | volunteerOrg@gmail.com  |            | Selected                           |

**Steps:**
1. Open the Home page.
2. Select the "Вход" tab.
3. Enter email and password according to the table.
4. Set the checkbox as indicated in the table.
5. Click the "Вход" button.

**Expected Result:**
- The organization is NOT authenticated.
- The user remains on the login page.
- An error message is displayed: "Невалидни данни за вход."
- Organization navigation menu is NOT visible.

---

## Test Scenario: AUTH-SC-03: Volunteer registration

### Test Cases

- TC-AUTH-006: Successful volunteer registration

**Preconditions:**
- The user is on the Home page
- The user is not registered yet

**Test Data:**
- Email: valid email
- Password: valid password


| First Name | Last Name | Email                  | Phone         | Password   | Confirm Password |
|------------|-----------|------------------------|---------------|------------|------------------|
| Ivan       | Ivanov    | volunteer@abv.bg       | +359888111222 | Test@1234  | Test@1234        |

**Steps:**
1. Open the Home page.
2. Select the "Регистрация (Доброволец)" tab.
3. Fill in all fields:
   - Име*
   - Фамилия*
   - Имейл*
   - Телефон
   - Парола*
   - Потвърждение на парола*
4. Click the "Регистрация" button.

**Expected Result:**
- The registration is successful.
- The user is redirected to the "Вход" tab.
- A success message is displayed - "Регистрацията е успешна".
- The volunteer can now log in using the registered email and password.

---

- TC-AUTH-007: Volunteer registration with invalid or missing data

**Preconditions:**
- The user is on the Home page
- The user is not registered yet

**Test Data:**


| First Name | Last Name | Email                  | Phone         | Password   | Confirm Password |
|------------|-----------|------------------------|---------------|------------|------------------|
| Ivan       | Ivanov    | invalid-email          | +359888111222 | Test@1234  | Test@1234        | // Invalid email format
| Ivan       | Ivanov    | volunteer@gmail.com    | 0888111222    | Test@1234  | Test@1234        | // Invalid phone number format
| Ivan       | Ivanov    | volunteer@gmail.com    | +359888111222 | Test@1234  | Test@12345       | // Mismatched passwords
| Ivan       | Ivanov    | volunteer@gmail.com    | +359888111222 | Test@1234  | Test@1234        | // Already registered email


**Steps:**
1. Open the Home page.
2. Select the "Регистрация (Доброволец)" tab.
3. Fill in the registration form according to the table.
4. Click the "Регистрация" button.

**Expected Result:**
- The registration is NOT successful.
- The user remains on the registration page.
- An appropriate error message is displayed depending on the scenario:
    - Missing required fields - highlight empty required fields
    - Invalid email format - "Невалиден имейл формат"
    - Invalid phone format - "Невалиден телефонен номер"
    - Mismatched passwords - "Паролите не съвпадат"
    - Already registered email - "Имейлът вече е регистриран"

---

## Test Scenario: AUTH-SC-04: Organization registration

### Test Cases

- TC-AUTH-007: Successful organization registration

**Preconditions:**
- The user is on the Home page
- The organization is not registered yet

**Test Data:**

- Име на организацията: EcoFriends
- Имейл за контакт: org@example.com
- Парола: Test@1234
- Потвърждение на парола: Test@1234
- ЕИК/Булстат: 123456789
- Тип организация: НПО
- Локация/Адрес: Sofia, Bulgaria
- Официален телефон за контакт: +359888111222
- Име на администратор: Ivan
- Фамилия на администратор: Ivanov
- Телефон на администратор: +359888111223

**Optional Test Data:**

**Steps:**
1. Open the Home page.
2. Select the "Регистрация (Организация)" tab.
3. Fill in all fields:
   - Име на организацията*
   - Имейл за контакт*
   - Парола* + Потвърждение*
   - ЕИК*/Булстат
   - Тип организация*
   - Локация/Адрес*
   - Официален телефон за контакт*
4. Fill in the administrator contact information:
   - Име*
   - Фамилия*
   - Телефон*
5. Click the "Регистрация" button.

**Expected Result:**
- The organization is successfully registered.
- If the admin email already exists as a user:
    - The existing user is assigned the role **Администратор** for this organization.
- If the admin email does not exist:
    - A new user profile is created.
    - The new user receives the base role **Доброволец** and the role **Администратор** for the organization.
- The user is redirected to the "Вход" tab.
- A success message is displayed: "Регистрацията е успешна".
- The organization can now log in using the registered email and password.

---

- TC-AUTH-008: Organization registration with invalid or missing data

**Preconditions:**
- The user is on the Home page
- The organization is not registered (except in the scenario with existing email)

**Test Data:**
#### 1. Existing user email
- Име на организацията: EcoFriends
- Имейл за контакт: existinguser@example.com
- Парола: Test@1234
- Потвърждение на парола: Test@1234
- ЕИК/Булстат: 123456789
- Тип организация: НПО
- Локация/Адрес: Sofia, Bulgaria
- Официален телефон за контакт: +359888111222
- Име на администратор: Ivan
- Фамилия на администратор: Ivanov
- Телефон на администратор: +359888111223

#### 2. Missing required fields
- Име на организацията: 
- Имейл за контакт: 
- Парола: 
- Потвърждение на парола: 
- ЕИК/Булстат: 
- Тип организация: 
- Локация/Адрес: 
- Официален телефон за контакт: 
- Име на администратор: 
- Фамилия на администратор: 
- Телефон на администратор: 

#### 3. Invalid EIK/Bulstat
- ЕИК/Булстат: 12345AB

#### 4. Invalid phone number
- Официален телефон за контакт: 0888111222

#### 5. Mismatched passwords
- Парола: Test@1234
- Потвърждение на парола: Test@12345

#### 6. Invalid location (outside Bulgaria)
- Локация/Адрес: Berlin, Germany

#### 7. Missing contact person data
- Име на администратор: 
- Фамилия на администратор: 
- Телефон на администратор: 

**Steps:**
1. Open the Home page.
2. Select the "Регистрация (Организация)" tab.
3. Fill in the registration form according to the scenario.
4. Click the "Регистрация" button.

**Expected Result:**
- Registration is NOT successful.
- The user remains on the registration page.
- Appropriate error messages are displayed according to the scenario:
    - Existing email - "Имейлът вече е регистриран"
    - Missing required fields - highlight empty required fields
    - Invalid EIK/Bulstat - "Невалиден ЕИК/Булстат"
    - Invalid phone - "Невалиден телефонен номер"
    - Mismatched passwords - "Паролите не съвпадат"
    - Invalid location - "Локацията трябва да е в България"
    - Missing contact person data - "Попълнете данните на администратор"

---

## Test Scenario: AUTH-SC-05: Forgot password

- TC-AUTH-009: Successful password reset via email link

**Preconditions:**
- The user is registered with a valid email.
- The user has access to the registered email inbox.

**Test Data:**
- Email: user@example.com
- New Password: NewPass@123
- Confirm New Password: NewPass@123

**Steps:**
1. Open the Home page.
2. Click on "Забравена парола" link in the "Вход" tab.
3. Enter the registered email address in the provided field.
4. Click the "Изпрати" button.
5. Open the email inbox and locate the password reset email.
6. Click on the password reset link provided in the email.
7. Enter the new password in the "Парола" field.
8. Enter the new password again in the "Потвърждение на парола" field.
9. Click the "Запази" button.

**Expected Result:**
- A confirmation message is displayed: "Паролата е успешно променена".
- The user can now log in with the new password.
- The old password is no longer valid for login.

---

- TC-AUTH-010: Forgot password with valid registered email

**Preconditions:**
- The user is registered with a valid email.
- The user is on the Home page, "Вход" tab is selected.

**Test Data:**
- Email: volunteer@abv.bg

**Steps:**
1. Click on the "Забравена парола" link in the "Вход" tab.
2. Enter the registered email address in the provided field.
3. Click the "Изпрати" button.
4. Open the email inbox and locate the password reset email.
5. Click on the password reset link provided in the email.

**Expected Result:**
- A password reset email is successfully sent to the registered email address.
- A confirmation message is displayed: "Инструкции за смяна на парола бяха изпратени на имейлът ви."
- The user can proceed to reset the password via the link.

---

TC-AUTH-011: Forgot password (negative scenarios)

**Preconditions:**
- The user is on the Home page.
- The "Вход" tab is selected.

**Test Data and Scenarios:**

| Scenario             | Email                   |
|----------------------|-------------------------|
| Non-existing email   | nonexisting@example.com |
| Empty email field    |                         |
| Invalid email format | invalid-email-format    |

**Steps:**
1. Click on the "Забравена парола" link in the "Вход" tab.
2. Enter the email address according to the scenario.
3. Click the "Изпрати" button.

**Expected Result:**
- Non-existing email:
  - User remains on the forgot password page.
  - Error message: "Имейлът не е регистриран."
- Empty email field:
  - User remains on the forgot password page.
  - Error message: "Моля, въведете имейл."
- Invalid email format:
  - User remains on the forgot password page.
  - Error message: "Невалиден имейл."

---

TC-AUTH-012: Expired link

**Preconditions:**
- The user is registered with a valid email.
- The user has received a password reset email.

**Test Data and Scenarios:**

| Scenario | New Password | Confirm New Password | Notes |
|----------|-------------|-------------------|-------|
| Expired link | NewPass@123 | NewPass@123 | The reset link has expired |

**Steps:**
1. Open the Home page.
2. Click on the "Забравена парола" link in the "Вход" tab.
3. Enter the registered email address and request a password reset.
4. Click on the password reset link in the email.
5. Enter the new password and confirm password according to the scenario.
6. Click the "Запази" button.

**Expected Result:**
- Expired link:
  - User cannot reset the password.
  - An error message is displayed: "Линкът за смяна на парола е изтекъл."

---

TC-AUTH-013: Mismatched passwords

**Preconditions:**
- The user is registered with a valid email.
- The user has received a password reset email.

**Test Data and Scenarios:**

| Scenario             | New Password| Confirm New Password|
|----------------------|-------------|---------------------|
| Mismatched passwords | NewPass@123 | DifferentPass@123   | 

**Steps:**
1. Open the Home page.
2. Click on the "Забравена парола" link in the "Вход" tab.
3. Enter the registered email address and request a password reset.
4. Click on the password reset link in the email.
5. Enter the new password and confirm password.
6. Click the "Запази" button.

**Expected Result:**
- Mismatched passwords:
  - User cannot reset the password.
  - An error message is displayed: "Паролите не съвпадат."

---
