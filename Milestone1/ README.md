# Milestone 1 — User Authentication Module

## 📌 Project Overview

Milestone 1 focuses on developing a secure **User Authentication Module** using Streamlit. The application provides user registration, login, password recovery, JWT-based session management, OTP email verification, and an Admin Dashboard for managing registered users.

The application is designed to run through **Google Colab** and is made publicly accessible using **ngrok**. Sensitive credentials such as JWT secrets, ngrok authentication tokens, and Gmail App Passwords are securely stored using **Google Colab Secrets**.

---

## 🎯 Objectives

The main objectives of Milestone 1 are:

* Build a complete user authentication system.
* Implement Login and Signup functionality.
* Implement Forgot Password using Security Question and Email OTP.
* Use JWT for secure session management.
* Add mandatory-field and password validation.
* Provide separate User and Admin Dashboards.
* Secure sensitive credentials using Colab Secrets.
* Make the Streamlit application publicly accessible using ngrok.

---

## ✨ Features Implemented

### 1. Login Page

The Login page allows registered users to log in using:

* Username/Email
* Password

Features include:

* Mandatory field validation.
* Generic error message for invalid credentials.
* JWT token generation after successful login.
* Redirect to the User Dashboard after successful authentication.

---

### 2. Signup Page

New users can create an account by providing:

* Username
* Email
* Password
* Confirm Password
* Security Question
* Security Answer

Validation includes:

* All fields are mandatory.
* Username must be unique.
* Email format validation.
* Password strength validation.
* Confirm Password must match Password.

The security question and answer are stored for use during password recovery.

---

### 3. Forgot Password

The Forgot Password page provides two recovery methods.

#### 🔐 Security Question Recovery

The user can:

1. Enter their username.
2. Answer the security question created during signup.
3. Verify the answer.
4. Create a new password.

#### 📧 OTP Recovery

The user can:

1. Enter their registered email address.
2. Receive a one-time password (OTP) through email.
3. Enter and verify the OTP.
4. Create a new password.

Both recovery methods follow the same password validation rules.

---

### 4. JWT Session Management

JSON Web Tokens (JWT) are used to manage authenticated user sessions.

After successful login:

* A JWT session token is generated.
* The token is stored in Streamlit session state.
* The token is validated before displaying the Dashboard.
* Logout clears the active session.
* Users must log in again to receive a fresh JWT.

---

### 5. User Dashboard

After successful authentication, users are redirected to the Dashboard.

The Dashboard displays:

* Welcome message.
* Logged-in username/email.
* Logout option.

The Logout option clears the session and returns the user to the Login page.

---

### 6. Admin Dashboard

The application contains a separate Admin Dashboard.

The Admin account is defined directly in the application code and is separate from normal user signup.

After successful Admin login, the Admin can view:

* Registered usernames.
* Registered email addresses.

**Password information is never displayed in the Admin Dashboard.**

---

## ✅ Validation Rules

### Mandatory Fields

All required fields in Login, Signup, and Forgot Password forms must be completed before submission.

### Email Validation

The email must follow the required format, with:

* At least 2 letters before `@`.
* At least 2 letters between `@` and the final dot.
* At least 2 letters after the final dot.

Example:

`ab@cd.ef`

### Password Validation

Passwords must contain:

* Minimum 8 characters.
* At least one uppercase letter.
* At least one lowercase letter.
* At least one number.
* At least one special character.

The Confirm Password field must exactly match the Password field.

---

## 🛠️ Technology Stack

| Technology           | Purpose                               |
| -------------------- | ------------------------------------- |
| Python               | Application development               |
| Streamlit            | Web application and UI                |
| JWT                  | Session authentication                |
| Google Colab         | Development and execution environment |
| ngrok                | Public URL/tunneling                  |
| Gmail SMTP           | OTP email delivery                    |
| Google Colab Secrets | Secure credential storage             |

---

## 🔐 Security Configuration

Sensitive information is **not hard-coded** in the notebook.

The following values are stored using Google Colab Secrets:

| Secret Name       | Purpose                            |
| ----------------- | ---------------------------------- |
| `JWT_SECRET`      | Signing JWT session tokens         |
| `NGROK_AUTHTOKEN` | Authentication for ngrok           |
| `EMAIL_PASSWORD`  | Gmail App Password for sending OTP |
| `EMAIL_ADDRESS`   | Gmail account used to send OTP     |

Notebook access is enabled for these secrets so that the application can securely retrieve them at runtime.

---

## 🌐 ngrok Configuration

ngrok is used to expose the Streamlit application running in Google Colab through a public URL.

The ngrok authentication token is stored securely as:

`NGROK_AUTHTOKEN`

The token is retrieved from Colab Secrets instead of being written directly inside the notebook.

---

## 📧 Gmail OTP Configuration

The application uses a Gmail App Password to send OTP emails for password recovery.

A Gmail account with **2-Step Verification enabled** is required before creating the App Password.

The Gmail credentials are stored securely in Colab Secrets:

* `EMAIL_ADDRESS`
* `EMAIL_PASSWORD`

The actual email password is never stored in the repository.

---

## ▶️ How to Run the Application

### Step 1 — Open the Notebook

Open the Milestone 1 notebook in Google Colab.

### Step 2 — Configure Colab Secrets

Add the required secrets:

```text
JWT_SECRET
NGROK_AUTHTOKEN
EMAIL_PASSWORD
EMAIL_ADDRESS
```

Enable notebook access for each secret.

### Step 3 — Run the Notebook

Run the notebook cells from top to bottom.

The application will start the Streamlit server and create an ngrok public URL.

### Step 4 — Open the Application

Open the generated ngrok URL in a browser.

From the application, users can access:

* Login
* Signup
* Forgot Password
* User Dashboard
* Admin Dashboard

---

## 📁 Project Structure

```text
Infosys Repository/
│
└── Milestone1/
    │
    ├── README.md
    ├── FranchiseOps_AI_Milestone1.ipynb
    │
    └── screenshots/
        ├── login.png
        ├── signup.png
        ├── forgot_password_security.png
        ├── forgot_password_otp.png
        ├── otp_email.png
        ├── user_dashboard.png
        └── admin_dashboard.png
```

---

## 📸 Screenshots

### Login Page

![Login Page](screenshots/login.png)

### Signup Page

![Signup Page](screenshots/signup.png)

### Forgot Password — Security Question

![Forgot Password Security Question](screenshots/forgot_password_security.png)

### Forgot Password — OTP

![Forgot Password OTP](screenshots/forgot_password_otp.png)

### OTP Email

![OTP Email](screenshots/otp_email.png)

### User Dashboard

![User Dashboard](screenshots/user_dashboard.png)

### Admin Dashboard

![Admin Dashboard](screenshots/admin_dashboard.png)

---

## 🔍 Security Checklist

Before uploading the notebook to GitHub:

* Remove all hard-coded email addresses where applicable.
* Remove Gmail App Passwords.
* Remove ngrok authentication tokens.
* Remove JWT secrets.
* Remove Admin passwords if they were accidentally hard-coded outside the intended configuration.
* Clear all notebook outputs.
* Make sure no OTPs or private credentials are visible.
* Confirm that sensitive values are retrieved only through Colab Secrets.

---

## ✅ Milestone 1 Completion Checklist

* [x] Infosys Repository created
* [x] `Milestone1` folder created
* [x] README.md added
* [x] Login page implemented
* [x] Signup page implemented
* [x] Forgot Password — Security Question implemented
* [x] Forgot Password — OTP implemented
* [x] JWT session management implemented
* [x] User Dashboard implemented
* [x] Admin Dashboard implemented
* [x] Mandatory-field validation implemented
* [x] Email validation implemented
* [x] Password validation implemented
* [x] ngrok configured
* [x] Gmail App Password configured
* [x] Colab Secrets configured
* [x] Screenshots added
* [x] Sensitive information removed before repository upload

---

## 🏁 Conclusion

Milestone 1 successfully implements a complete authentication gateway using **Streamlit, JWT, ngrok, Gmail OTP, and Google Colab Secrets**. The module provides secure user registration, authentication, password recovery, session management, and separate user and administrator dashboards while keeping sensitive credentials protected.
