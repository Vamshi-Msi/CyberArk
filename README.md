# CyberArk
In this demonstration we will configure SAML authentication for PSM for Windows

# Below is the reference of how the login flow works.

![alt text](https://github.com/Vamshi-Msi/CyberArk/blob/main/PSM%20for%20SAML.jpg?raw=true)

## SAML Auth For PSM Login Flow


User Requests Access: The user tries to access the target application through PSM (Service Provider).

SP Sends SAML Request: The service provider (PSM) generates a SAML request and redirects the user to the identity provider (IdP) for authentication.

User Authenticates: The identity provider prompts the user to log in (if not already authenticated).

IdP Generates SAML Response: Upon successful authentication, the identity provider creates a SAML response containing the user’s authentication status and attributes.

User Redirected Back to SP: The identity provider sends the SAML response back to the service provider (PSM) via the user’s browser.

SP Grants Access: The service provider (PSM) validates the SAML response and grants the user access to the requested server/application/database etc once the user details and the authorizations are validated by vault.
