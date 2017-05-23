<properties  
    pageTitle="Cloud-based MFA/Installing or configuring Azure MFA NPS extension" 
    description="Instalación o configuración de extensiones para el servicio MFA (nube)" 
    service="microsoft.multifactorauthentication" 
    resource="" 
    authors="kgremban" 
    selfHelpType="generic" 
    supportTopicIds="32565586" 
    productPesIds="14947" 
    cloudEnvironments="public" 
 /> 

# <a name="installing-or-configuring-extensions-for-mfa-service-cloud"></a>Instalación o configuración de extensiones para el servicio MFA (nube)  
## <a name="recommended-steps"></a>**Pasos recomendados** 
Siga estos pasos para solucionar problemas habituales con la extensión NPS para Azure MFA: 

**Error en el token AAL**

1. Reinicie el servidor NPS. 
2. Compruebe que el certificado de cliente esté instalado según lo previsto. 
3. Compruebe que el certificado esté asociado a su inquilino en Azure AD. 
4. Compruebe que https://login.windows.net/ esté accesible desde el servidor que ejecuta la extensión. 

**Los registros de HTTP muestran que el usuario no encontró el error**

1. Compruebe que se está ejecutando AD Connect. 
2. Compruebe que el usuario esté presente en Windows Active Directory y Azure Active Directory. La presencia de un usuario viene determinada por el UPN o el identificador de inicio de sesión alternativo. Deben estar sincronizados en On-Prem AD y Azure AD. 

**NoDefaultAuthenticationMethodIsConfigured y ProofDataNotFound**

1. Compruebe que el usuario se ha registrado para Azure MFA y configure al menos un método de comprobación. 

**Hay errores de conexión de HTTP en los registros y se producen errores en todas las autenticaciones**

1. Compruebe que https://adnotifications.windowsazure.com sea accesible desde el servidor que ejecuta la extensión de NPS. 

## <a name="recommended-documents"></a>**Documentos recomendados** 
  
- [Integración de la infraestructura existente de NPS con Azure Multi-Factor Authentication](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-nps-extension) 
- [Resolución de mensajes de error de la extensión de NPS para Azure Multi-Factor Authentication](https://review.docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-nps-errors?branch=pr-en-us-10717)

