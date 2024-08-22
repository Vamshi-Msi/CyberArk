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

# Known limitations and pre-requisites are highlited in the below article

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

Navigate to **Administartion < Configuration Options < Options < Privilege Session Management < General Settings < Server Settings < Advanced Settings < SAML Settings**

**Configure required settings as listed below:**

- **SamlEnabled** = Yes

- **IdentityProviderLoginURL** = <Your IdP login URL> (for Azure this is https://login.microsoftonline.com/<tenantID>/saml2) 

- **httpsWhitelist** = Any domain that the client will contact during SAML authentication. The domain specified in IdentityProviderLoginURL and ServiceProviderName is whitelisted by default. 

Any URL that’s needed for the authentication to work needs to be added to the httpWhitelist parameter in the PVWA. For Azure it should look something like this:


**For Azure, whitelist below domains:**

aadcdn.msftauth.net,aadcdn.msftauthimages.net,aadcdn.msauthimages.net,logincdn.msftauth.net,login.live.com,msauth.net,aadcdn.microsoftonline-p.com,microsoftonline-p.com, aadcdn.msftauth.net,aadcdn.msauth.net,login.live.com


- **IdentityProviderCertificateSN** = <serialnumber of the SAML certificate from your IdP> 

- **ServiceProviderName** = The Entity ID of your SAML authentication application. It is recommended to set up a dedicated SAML application for PSM SAML Authentication.  
 
   **NOTE:** This Entity ID needs to be in all lower-case characters, and it’s recommended that you use your PSM FQDN (either the load balanced FQDN or the 
             single PSM FQDN if you only have one PSM in your environment) as per docs. So the format would be “https://psm-fqdn.domain.com”  

![image](https://github.com/user-attachments/assets/2273a7f5-9d24-4f06-a337-07e1e0bb2db8)


## PSM Configuration

On the PSM you need to import the SAML certificate into the appropriate certificate stores. If the SAML certificate is self-signed, you need to add it to the Trusted Root Certification Authorities store and you need to create a new certificate store called Trusted IdP and add the certificate there as well. 

**To create the new store, run this command in an administrative PowerShell:** 
 

     New-Item -Path "cert:\LocalMachine\Trusted IdP" 
 

If the SAML certificate is signed by a PKI or an actual CA server, then add the certificate chain to the appropriate certificate stores and the SAML certificate in the Trusted IdP store.


**Configuration is not completed! It's testing time...!**

RDP file for your reference has been uploaded 



https://github.com/user-attachments/assets/d0e6c874-8b8f-4514-9377-e8c801f8b15b
