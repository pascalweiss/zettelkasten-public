#public
An open-source identity and access management (IAM) system. It provides authentication, authorisation (see [[Authentication and authorization]])and user-management for applications and services. It provides features such as SSO (single-sign-on), OAuth2 (social login), etc. 

### SPI - Extending Keycloaks functionality
Keycloak provides a framework for extending its functionality. Therefore it provides various interfaces, i.e. SPI (Service Provider Interface), which can then be applied by the keycloak application.

Common SPIs in Keycloak are:
- Authentication SPI: For custom authentication flows
- Event Listener SPI: For integrating Keycloak via a messaging system.
- Theme SPI: For creating custom UI themes. 


### Related Links
- https://medium.com/@mesutpiskin/two-factor-authentication-via-email-in-keycloak-custom-auth-spi-935bbb3952a8


### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

