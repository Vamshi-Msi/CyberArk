# CyberArk
In this demonstration we will configure SAML authentication for PSM for Windows

# Below is the reference of how the login flow works.

![alt text](https://github.com/Vamshi-Msi/CyberArk/blob/main/PSM%20for%20SAML.jpg?raw=true)

## SAML Auth For PSM Login Flow


- **User Requests Access:** The user tries to access the target application through PSM (Service Provider).

- **SP Sends SAML Request:** The service provider (PSM) generates a SAML request and redirects the user to the identity provider (IdP) for authentication.

- **User Authenticates:** The identity provider prompts the user to log in (if not already authenticated).

- **IdP Generates SAML Response:** Upon successful authentication, the identity provider creates a SAML response containing the user’s authentication status and attributes.

- **User Redirected Back to SP:** The identity provider sends the SAML response back to the service provider (PSM) via the user’s browser.

- **SP Grants Access:** The service provider (PSM) validates the SAML response and grants the user access to the requested server/application/database etc once the user details and the authorizations are validated by vault.

# Known limitations and pre-requisites are highlites in the below article

https://community.cyberark.com/s/article/Setting-up-SAML-Authentication-PSM-v14-with-Azure

## Steps:

# Create seperate enterprise application for SAML for PSM.


![image](https://github.com/user-attachments/assets/35f64a09-aaf1-4f76-977d-10b819963a4f)



![image](https://github.com/user-attachments/assets/499ca3f5-9693-4e15-b587-22307cce3629)



![image](https://github.com/user-attachments/assets/61c1733d-e38a-46d4-a4dd-ce181bd533c6)

 

![image](https://github.com/user-attachments/assets/dceedb17-ab0d-40b3-bbfd-93ccf99952c9)



![image](https://github.com/user-attachments/assets/a766d046-53ab-4d84-b208-a7365bf9fed2)



![image](https://github.com/user-attachments/assets/c27169b3-808c-4fc7-8ca8-0d4af8faafec)



![image](https://github.com/user-attachments/assets/b526e643-e813-4af1-bbaa-ea3fcfa54404)


![image](https://github.com/user-attachments/assets/dd4b4277-f5b7-4411-ae9f-03b287086d9a)


## PVWA Configuration

