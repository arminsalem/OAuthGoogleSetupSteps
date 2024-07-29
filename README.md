# OAuth 2.0 Setup for Google Cloud

This guide will help you set up OAuth 2.0 for your application using Google Cloud. Follow these steps to configure OAuth 2.0 in development or production mode.

## Table of Contents
1. [Create a Google Cloud Project](#1-create-a-google-cloud-project)
2. [Enable APIs](#2-enable-apis)
3. [Set Up OAuth Consent Screen](#3-set-up-oauth-consent-screen)
4. [Create OAuth 2.0 Credentials](#4-create-oauth-20-credentials)
5. [Download and Store Client Secrets](#5-download-and-store-client-secrets)
6. [Integrate OAuth 2.0 in Your Application](#6-integrate-oauth-20-in-your-application)
7. [Handle Authentication and Authorization](#7-handle-authentication-and-authorization)
8. [Set Up Environment Variables](#8-set-up-environment-variables)
9. [Testing and Deployment](#9-testing-and-deployment)
10. [Verify OAuth Consent Screen](#10-verify-oauth-consent-screen)

## 1. Create a Google Cloud Project
1. Visit the [Google Cloud Console](https://console.cloud.google.com/).
2. Click the project drop-down and select **New Project**.
3. Enter the project name and select the billing account and organization if applicable.
4. Click **Create**.

## 2. Enable APIs
1. Navigate to **API & Services** > **Library**.
2. Enable the APIs that your app will use (e.g., Google Drive API, Gmail API).

## 3. Set Up OAuth Consent Screen
1. Navigate to **API & Services** > **OAuth consent screen**.
2. Choose the user type (Internal or External).
3. Fill out the required information:
    - **App name**
    - **User support email**
    - **Developer contact information**
4. Add **Scopes** your app will request.
5. Configure OAuth consent screen details like branding information.
6. Save and continue.

## 4. Create OAuth 2.0 Credentials
1. Navigate to **API & Services** > **Credentials**.
2. Click **Create Credentials** and select **OAuth 2.0 Client IDs**.
3. Configure the OAuth consent screen if not done already.
4. Fill in the details:
    - **Application type**: Choose the appropriate type (Web application, Android, iOS).
    - **Name**: Give it a name (e.g., Web Client).
    - **Authorized redirect URIs**: Add the URIs that users will be redirected to after authentication (e.g., `http://localhost:3000/callback` for development, `https://yourapp.com/callback` for production).
5. Click **Create**.

## 5. Download and Store Client Secrets
1. Once created, download the JSON file containing your client ID and client secret.
2. Store this file securely; it will be needed for your application to authenticate with Google.

## 6. Integrate OAuth 2.0 in Your Application
- **Backend Setup**: Use libraries like `google-auth-library` for Node.js, `google-api-python-client` for Python, or equivalent for your tech stack.
- **Frontend Setup**: For web applications, you can use libraries like `@react-oauth/google` for React or the standard Google API libraries.

## 7. Handle Authentication and Authorization
1. Direct users to the Google OAuth 2.0 endpoint to authenticate.
2. Handle the redirect with the authorization code.
3. Exchange the authorization code for an access token.

## 8. Set Up Environment Variables
Store sensitive information like client IDs and secrets in environment variables.

Example for a `.env` file:
```dotenv
GOOGLE_CLIENT_ID=your-client-id
GOOGLE_CLIENT_SECRET=your-client-secret
GOOGLE_REDIRECT_URI=http://localhost:3000/api/auth/callback/google # or your production URL
