---
title: "A Configuration Manager által használt portok |} Microsoft Docs"
description: "További tudnivalók az szükséges, és testre szabható a System Center Configuration Manager által használt portokról kapcsolatokhoz."
ms.custom: na
ms.date: 3/20/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c6777fb0-0754-4abf-8a1b-7639d23e9391
caps.latest.revision: 8
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 78caa69e10f5d386daab1e61e484d4d134469708
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="ports-used-in-system-center-configuration-manager"></a>A System Center Configuration Managerben használt portok

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager egy olyan elosztott ügyfél-kiszolgáló rendszer. A Configuration Manager elosztott jellege azt jelenti, hogy kapcsolatok hozhatók létre a Helykiszolgálók, helyrendszerek és ügyfelek között. Néhány kapcsolat használja, amelyek nem konfigurálhatók, és néhány támogatási egyéni portokkal megadott. Ellenőrizze, hogy a szükséges portok elérhetők, ha bármilyen Portszűrési technológiát, például a tűzfalakat, útválasztókat, proxykiszolgálókat vagy az IPsec használata.  

> [!NOTE]  
>  Ha az internetes ügyfeleket támogatja az SSL-hídképzést, portokra vonatkozó követelmények mellett a lehetséges is, hogy ahhoz, hogy néhány HTTP-műveletekre és a fejléc áthaladását a tűzfalon.   

 A port listák a Configuration Manager által használt, és nem tartalmaznak a szabványos Windows-szolgáltatásokra, például az Active Directory tartományi szolgáltatások vagy a Kerberos-hitelesítés csoportházirend-beállítások információt. További információ a Windows Server szolgáltatásairól és portjairól: [A Windows Server rendszer szolgáltatásainak áttekintése és a hálózati portokra vonatkozó követelmények](http://go.microsoft.com/fwlink/p/?LinkID=123652).  

##  <a name="BKMK_ConfigurablePorts"></a> Konfigurálható portok  
 A Configuration Manager lehetővé teszi, hogy a következő kommunikációtípusok a portok konfigurálását:  

-   Alkalmazáskatalógus webszolgáltatási pontjai számára az Alkalmazáskatalógus weboldal-elérési pontja  

-   A beléptetési proxypont és a beléptetési pont között  

-   IIS-t futtató ügyfél-hely rendszerek  

-   Az ügyfél és az internet között (proxykiszolgáló-beállításként)  

-   A szoftverfrissítési pont és az internet között (proxykiszolgáló-beállításként)  

-   A szoftverfrissítési pont és a WSUS-kiszolgáló között  

-   A helyrendszer és a helyrendszer-kiszolgáló között  

-   Jelentéskészítési szolgáltatási pontok  

    > [!NOTE]  
    >  Az SQL Server Reporting Services a jelentéskészítési szolgáltatási pont helyrendszerszerepkört a használt portok vannak konfigurálva. Ezeket a portokat használja a Configuration Manager által a jelentéskészítési szolgáltatási ponttal folytatott kommunikáció során. Győződjön meg arról, hogy tekintse át ezeket a portokat, amelyek meghatározzák az IP-szűrési adatainak az IPsec-házirendek, vagy a tűzfalakat konfigurálja.  

Alapértelmezés szerint az ügyfél helyrendszer-kommunikációhoz használt HTTP-port a 80-as porton, és az alapértelmezett HTTPS-port pedig a 443-as. Az ügyfél helyrendszer kommunikációhoz HTTP vagy HTTPS használt portok módosíthatja a telepítés során vagy a Configuration Manager-hely hely tulajdonságai.  

Az SQL Server Reporting Services a jelentéskészítési szolgáltatási pont helyrendszerszerepkört a használt portok vannak konfigurálva. Ezeket a portokat használja a Configuration Manager által a jelentéskészítési szolgáltatási ponttal folytatott kommunikáció során. Feltétlenül olvassa el ezeket a portokat, az IP-szűrési adatainak, vagy a tűzfalakat konfigurálja az IPsec-házirendek meghatározásakor van.  

##  <a name="BKMK_NonConfigurablePorts"></a> Nem konfigurálható portok  
A Configuration Manager nem teszi lehetővé a következő típusú kommunikációs portok konfigurálása:  

-   Hely és hely között  

-   Helyrendszer és helyrendszer között  

-   A Configuration Manager konzol az SMS-szolgáltató  

-   A Configuration Manager konzol és az Internet  

-   Kapcsolatok a felhőszolgáltatásokhoz, például a Microsoft Intune és a felhő alapú terjesztési pontok  

##  <a name="BKMK_CommunicationPorts"></a> A Configuration Manager ügyfelei és helyrendszerei által használt portok  
A következő részek a Configuration Manager-kommunikációhoz használt portokat. A címben szereplő nyilak a kommunikáció irányát jelzik:  

-   --> Azt jelzi, hogy az egyik számítógép kezdeményezi a kommunikációt, és a másik számítógép pedig mindig válaszol  

-   &lt;--> Azt jelzi, hogy bármelyik számítógép kezdeményezheti a kommunikációt  

###  <a name="BKMK_PortsAI"></a>Eszközintelligencia szinkronizálási pontja--> Microsoft  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Secure Hypertext Transfer Protocol (HTTPS)|--|443|  

###  <a name="BKMK_PortsAI-to-SQL"></a>Eszközintelligencia szinkronizálási pontja--> SQL Server  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|SQL TCP protokollon keresztül|--|1433 (lásd a 2. megjegyzést: **alternatív port elérhető**)|  

###  <a name="BKMK_PortsAppCatalogService-SQL"></a>Az Alkalmazáskatalógus webszolgáltatási pontja--> SQL Server  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|SQL TCP protokollon keresztül|--|1433 (lásd a 2. megjegyzést: **alternatív port elérhető**)|  

###  <a name="BKMK_PortsAppCatalogWebSitePoint_AppCatalogWebServicePoint"></a>Alkalmazáskatalógus weboldal-elérési pontja--> Alkalmazáskatalógus webszolgáltatási pontja  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Hypertext Transfer Protocol (HTTP)|--|80 (lásd a 2. megjegyzést: **alternatív port elérhető**)|  
|Secure Hypertext Transfer Protocol (HTTPS)|--|443 (lásd a 2. megjegyzést: **alternatív port elérhető**)|  

###  <a name="BKMK_PortsClient-AppCatalogWebsitePoint"></a>Ügyfél--> Alkalmazáskatalógus weboldal-elérési pontja  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Hypertext Transfer Protocol (HTTP)|--|80 (lásd a 2. megjegyzést: **alternatív port elérhető**)|  
|Secure Hypertext Transfer Protocol (HTTPS)|--|443 (lásd a 2. megjegyzést: **alternatív port elérhető**)|  

###  <a name="BKMK_PortsClient-ClientWakeUp"></a> Ügyfél -- &gt; Ügyfél  
 Az alábbi táblázatban felsorolt portokon kívül az ébresztési proxy ugyancsak Internet Control Message Protocol (ICMP) echo kérés üzenetek egy ügyfél egy másik ügyfél az ébresztési proxy konfigurálásakor.

Ezzel a kommunikációval ellenőrizhető, hogy a másik ügyfélszámítógép ébrenléti állapotban van-e a hálózatban. Az ICMP-t néha TCP/IP ping parancsnak is nevezik. Az ICMP-hez nem tartozik UDP- vagy TCP-protokollszám, és ezért nincs felsorolva a következő táblázatban. Az ébresztési proxy kommunikációjának sikerességéhez azonban az ezeken a számítógépeken működő állomásalapú tűzfalaknak vagy az alhálózaton belül lévő beavatkozó hálózati eszközöknek engedélyezniük kell az ICMP-forgalmat.  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Hálózati ébresztés|9 (lásd a 2. megjegyzést: **alternatív port elérhető**)|--|  
|Ébresztési proxy|25536 (lásd a 2. megjegyzést: **alternatív port elérhető**)|--|  

###  <a name="BKMK_PortsClient-PolicyModule"></a> Ügyfél -- &gt; Configuration Manager Házirend modulja (Hálózati eszközök tanúsítványigénylési szolgáltatása)  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Hypertext Transfer Protocol (HTTP)||80|  
|Secure Hypertext Transfer Protocol (HTTPS)|--|443|  

###  <a name="BKMK_PortsClient-CloudDP"></a>Ügyfél--> Felhőalapú terjesztési pont  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Secure Hypertext Transfer Protocol (HTTPS)|--|443|  

###  <a name="BKMK_PortsClient-DP"></a>Ügyfél--> Terjesztési pont  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Hypertext Transfer Protocol (HTTP)|--|80 (lásd a 2. megjegyzést: **alternatív port elérhető**)|  
|Secure Hypertext Transfer Protocol (HTTPS)|--|443 (lásd a 2. megjegyzést: **alternatív port elérhető**)|  

###  <a name="BKMK_PortsClient-DP2"></a>Ügyfél--> Csoportos küldésre konfigurált terjesztési pont  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Server Message Block (SMB)|--|445|  
|Csoportos küldési protokoll|63000-64000|--|  

###  <a name="BKMK_PortsClient-DP3"></a>Ügyfél--> PXE használatára konfigurált terjesztési pont  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Dynamic Host Configuration Protocol (DHCP)|67 és 68|--|  
|Trivial File Transfer Protocol (TFTP)|69 (lásd a 4. megjegyzést **Trivial FTP (TFTP) démon**)|--|  
|Boot Information Negotiation Layer (BINL)|4011|--|  

###  <a name="BKMK_PortsClient-FSP"></a>Ügyfél--> Tartalék állapotkezelő pont  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Hypertext Transfer Protocol (HTTP)|--|80 (lásd a 2. megjegyzést: **alternatív port elérhető**)|  

###  <a name="BKMK_PortsClient-GCDC"></a>Ügyfél--> Globális katalógus tartományvezérlője  
 A Configuration Manager-ügyfelek nem csatlakoznak globális katalóguskiszolgálóhoz, amikor a kiszolgáló egy munkacsoportban lévő számítógép, vagy amikor a kiszolgáló csak internetes kommunikációra van beállítva.  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Globális katalógus – LDAP|--|3268|  
|Globális katalógus – LDAP SSL|--|3269|  

###  <a name="BKMK_PortsClient-MP"></a>Ügyfél--> Felügyeleti pont  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Ügyfélértesítés (alapértelmezett kommunikáció a HTTP-re vagy a HTTPS-re való visszaváltás előtt)|--|10123 (lásd a 2. megjegyzést: **alternatív port elérhető**)|  
|Hypertext Transfer Protocol (HTTP)|--|80 (lásd a 2. megjegyzést: **alternatív port elérhető**)|  
|Secure Hypertext Transfer Protocol (HTTPS)|--|443 (lásd a 2. megjegyzést: **alternatív port elérhető**)|  

###  <a name="BKMK_PortsClient-SUP"></a>Ügyfél--> Szoftverfrissítési pont  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Hypertext Transfer Protocol (HTTP)|--|80 vagy 8530 (Lásd a 3. megjegyzést: **Windows Server Update Services**)|  
|Secure Hypertext Transfer Protocol (HTTPS)|--|443 vagy 8531 (Lásd a 3. megjegyzést: **Windows Server Update Services**)|  

###  <a name="BKMK_PortsClient-SMP"></a>Ügyfél--> Állapotáttelepítési pont  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Hypertext Transfer Protocol (HTTP)|--|80 (lásd a 2. megjegyzést: **alternatív port elérhető**)|  
|Secure Hypertext Transfer Protocol (HTTPS)|--|443 (lásd a 2. megjegyzést: **alternatív port elérhető**)|  
|Server Message Block (SMB)|--|445|  

###  <a name="BKMK_PortsConsole-Client"></a>A Configuration Manager konzol--> ügyfél  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Távvezérlés (vezérlő)|--|2701|  
|Távsegítség (RDP és RTC)|--|3389|  

###  <a name="BKMK_PortsConsole-Internet"></a>A Configuration Manager konzol--> Internet  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Hypertext Transfer Protocol (HTTP)|--|80|  

###  <a name="BKMK_PortsConsole-RSP"></a>A Configuration Manager konzol--> jelentéskészítési szolgáltatási pont  


|Leírás|UDP|TCP|
|-----------------|---------|---------|   
|Hypertext Transfer Protocol (HTTP)|--|80 (lásd a 2. megjegyzést: **alternatív port elérhető**)|  
|Secure Hypertext Transfer Protocol (HTTPS)|--|443 (lásd a 2. megjegyzést: **alternatív port elérhető**)|  

###  <a name="BKMK_PortsConsole-Site"></a>A Configuration Manager konzol--> helykiszolgáló  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|RPC (kezdeti kapcsolat a WMI-hez a szolgáltató rendszerhez)|--|135|  

###  <a name="BKMK_PortsConsole-Provider"></a>A Configuration Manager konzol--> SMS-szolgáltató  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|RPC végpontleképező|135|135|  
|RPC|--|DYNAMIC (Lásd a 6. megjegyzést: **Dinamikus portok**)|  

###  <a name="BKMK_PortsCertificateRegistationPoint_PolicyModule"></a>A Configuration Manager házirend modulja (hálózati eszközök tanúsítványigénylési szolgáltatása)--> Tanúsítványregisztrációs pont  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Secure Hypertext Transfer Protocol (HTTPS)|--|443 (lásd a 2. megjegyzést: **alternatív port elérhető**)|  

###  <a name="BKMK_PortsDist_MP"></a>Terjesztési pont--> felügyeleti pont  
 A terjesztési pont az alábbi esetekben kommunikál a felügyeleti ponttal:  

-   A jelentés a manuálisan előkészített tartalom állapotáról  

-   Jelentés készítése összegzett használati adatokról  

-   Jelentés készítése tartalomellenőrzésről  

-   A jelentés csomag letöltése (lekéréses terjesztési pont) állapota

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Hypertext Transfer Protocol (HTTP)|--|80 (lásd a 2. megjegyzést: **alternatív port elérhető**)|  
|Secure Hypertext Transfer Protocol (HTTPS)|--|443 (lásd a 2. megjegyzést: **alternatív port elérhető**)|  

###  <a name="BKMK_PortsEndpointProtection_Internet"></a>Endpoint Protection-pont--> Internet  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Hypertext Transfer Protocol (HTTP)|--|80|  

###  <a name="BKMK_PortsEP-to-SQL"></a>Endpoint Protection-pont--> SQL Server  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|SQL TCP protokollon keresztül|--|1433 (lásd a 2. megjegyzést: **alternatív port elérhető**)|  

###  <a name="BKMK_PortsEnrollmentProxyEnrollmentPoint"></a>Beléptetési proxypont--> beléptetési pont  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Secure Hypertext Transfer Protocol (HTTPS)|--|443 (lásd a 2. megjegyzést: **alternatív port elérhető**)|  

###  <a name="BKMK_PortsEnrollmentEnrollmentSQL"></a>Beléptetési proxypont--> SQL Server  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|SQL TCP protokollon keresztül|--|1433 (lásd a 2. megjegyzést: **alternatív port elérhető**)|  

###  <a name="BKMK_PortsExchangeConnectorHosted"></a> Exchange Server-összekötő -- &gt; Exchange Online  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Rendszerfelügyeleti webszolgáltatások HTTPS protokollon|--|5986|  

###  <a name="BKMK_PortsExchangeConnectorOnPrem"></a>Exchange Server-összekötő--> Helyi Exchange Server  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Rendszerfelügyeleti webszolgáltatások HTTP protokollon|--|5985|  

###  <a name="BKMK_PortsMacEnrollmentProxyPoint"></a>Mac számítógép--> beléptetési proxypont  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Secure Hypertext Transfer Protocol (HTTPS)|--|443|  

###  <a name="BKMK_PortsMP-DC"></a>Felügyeleti pont--> tartományvezérlő  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Lightweight Directory Access Protocol (LDAP)|--|389|  
|LDAP (SSL-kapcsolat [Secure Sockets Layer])|636|636|  
|Globális katalógus – LDAP|--|3268|  
|Globális katalógus – LDAP SSL|--|3269|  
|RPC végpontleképező|135|135|  
|RPC|--|DYNAMIC (Lásd a 6. megjegyzést: **Dinamikus portok**)|  

###  <a name="BKMK_PortsMP-Site"></a>Felügyeleti pont &lt; --> helykiszolgáló  
 (Lásd az 5. megjegyzést: **A helykiszolgáló és a helyrendszerek közötti kommunikáció**)  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|RPC végpontleképező|--|135|  
|RPC|--|DYNAMIC (Lásd a 6. megjegyzést: **Dinamikus portok**)|  
|Server Message Block (SMB)|--|445|  

###  <a name="BKMK_PortsMP-SQL"></a>Felügyeleti pont--> SQL Server  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|SQL TCP protokollon keresztül|--|1433 (lásd a 2. megjegyzést: **alternatív port elérhető**)|  

###  <a name="BKMK_PortsMobileDeviceClient-EnrollmentProxyPoint"></a>Mobileszköz--> beléptetési proxypont  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Secure Hypertext Transfer Protocol (HTTPS)|--|443|  

###  <a name="BKMK_PortsMobileDeviceClient-WindowsIntune"></a>Mobileszköz--> Microsoft Intune  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Secure Hypertext Transfer Protocol (HTTPS)|--|443|  

###  <a name="BKMK_PortsRSP-SQL"></a>Jelentéskészítési szolgáltatási pont--> SQL Server  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|SQL TCP protokollon keresztül|--|1433 (lásd a 2. megjegyzést: **alternatív port elérhető**)|  

###  <a name="BKMK_PortsIntuneConnector-WindowsIntune"></a>Szolgáltatáskapcsolódási pont--> Microsoft Intune  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Secure Hypertext Transfer Protocol (HTTPS)|--|443|
További információ: [internetelérési követelményei](/sccm/core/servers/deploy/configure/about-the-service-connection-point#bkmk_urls) a szolgáltatáskapcsolódási pont számára.

###  <a name="BKMK_PortsAppCatalogWebServicePoint_SiteServer"></a>Helykiszolgáló &lt; --> Alkalmazáskatalógus webszolgáltatási pontja  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Server Message Block (SMB)|--|445|  
|RPC végpontleképező|135|135|  
|RPC|--|DYNAMIC (Lásd a 6. megjegyzést: **Dinamikus portok**)|  

###  <a name="BKMK_PortsAppCatalogWebSitePoint_SiteServer"></a>Helykiszolgáló &lt; --> Alkalmazáskatalógus weboldal-elérési pontja  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Server Message Block (SMB)|--|445|  
|RPC végpontleképező|135|135|  
|RPC|--|DYNAMIC (Lásd a 6. megjegyzést: **Dinamikus portok**)|  

###  <a name="BKMK_PortsSite-AISP"></a>Helykiszolgáló &lt; --> Eszközintelligencia szinkronizációs pontja  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Server Message Block (SMB)|--|445|  
|RPC végpontleképező|135|135|  
|RPC|--|DYNAMIC (Lásd a 6. megjegyzést: **Dinamikus portok**)|  

###  <a name="BKMK_PortsSite-Client"></a>Helykiszolgáló--> ügyfél  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Hálózati ébresztés|9 (lásd a 2. megjegyzést: **alternatív port elérhető**)|--|  

###  <a name="BKMK_PortsSiteServer-CloudDP"></a>Helykiszolgáló--> felhőalapú terjesztési pont  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Secure Hypertext Transfer Protocol (HTTPS)|--|443|  

###  <a name="BKMK_PortsSite-DP"></a>Helykiszolgáló--> terjesztési pont  
 (Lásd az 5. megjegyzést: **A helykiszolgáló és a helyrendszerek közötti kommunikáció**)  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Server Message Block (SMB)|--|445|  
|RPC végpontleképező|135|135|  
|RPC|--|DYNAMIC (Lásd a 6. megjegyzést: **Dinamikus portok**)|  

###  <a name="BKMK_PortsSite-DC"></a>Helykiszolgáló--> tartományvezérlő  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Lightweight Directory Access Protocol (LDAP)|--|389|  
|LDAP (SSL-kapcsolat [Secure Sockets Layer])|636|636|  
|Globális katalógus – LDAP|--|3268|  
|Globális katalógus – LDAP SSL|--|3269|  
|RPC végpontleképező|135|135|  
|RPC|--|DYNAMIC (Lásd a 6. megjegyzést: **Dinamikus portok**)|  

###  <a name="BKMK_PortsCertificateRegistrationPoint_SiteServer"></a>Helykiszolgáló &lt; --> tanúsítványregisztrációs pont tanúsítvány  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Server Message Block (SMB)|--|445|  
|RPC végpontleképező|135|135|  
|RPC|--|DYNAMIC (Lásd a 6. megjegyzést: **Dinamikus portok**)|  

###  <a name="BKMK_PortsEndpointProtection_SiteServer"></a>Helykiszolgáló &lt; --> Endpoint Protection-pont  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Server Message Block (SMB)|--|445|  
|RPC végpontleképező|135|135|  
|RPC|--|DYNAMIC (Lásd a 6. megjegyzést: **Dinamikus portok**)|  

###  <a name="BKMK_EnrollmentPoint_SiteServer"></a>Helykiszolgáló &lt; --> beléptetési pont  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Server Message Block (SMB)|--|445|  
|RPC végpontleképező|135|135|  
|RPC|--|DYNAMIC (Lásd a 6. megjegyzést: **Dinamikus portok**)|  

###  <a name="BKMK_EnrollmentProxyPoint_SiteServer"></a>Helykiszolgáló &lt; --> beléptetési proxypont  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Server Message Block (SMB)|--|445|  
|RPC végpontleképező|135|135|  
|RPC|--|DYNAMIC (Lásd a 6. megjegyzést: **Dinamikus portok**)|  

###  <a name="BKMK_PortsSite-FSP"></a>Helykiszolgáló &lt; --> tartalék állapotkezelő pont  
 (Lásd az 5. megjegyzést: **A helykiszolgáló és a helyrendszerek közötti kommunikáció**)  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Server Message Block (SMB)|--|445|  
|RPC végpontleképező|135|135|  
|RPC|--|DYNAMIC (Lásd a 6. megjegyzést: **Dinamikus portok**)|  

###  <a name="BKMK_PortSite-Internet"></a>Helykiszolgáló--> Internet  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Hypertext Transfer Protocol (HTTP)|--|80 (lásd: 1. megjegyzést: **proxykiszolgáló portja**)|  

###  <a name="BKMK_PortsIssuingCA_SiteServer"></a>Helykiszolgáló &lt; --> kiállító hitelesítésszolgáltató (CA)  
 Ez a kommunikáció akkor használható, amikor tanúsítványprofilokat telepít a tanúsítványregisztrációs pont használatával. A kommunikáció nem használható a hierarchiában lévő összes helykiszolgálónál. Ehelyett azt csak szolgál a helykiszolgálón, a hierarchia tetején.  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|RPC végpontleképező|135|135|  
|RPC (DCOM)|--|DYNAMIC (Lásd a 6. megjegyzést: **Dinamikus portok**)|  

###  <a name="BKMK_PortsSite-RSP"></a>Helykiszolgáló &lt; --> jelentéskészítési szolgáltatási pont  
 (Lásd az 5. megjegyzést: **A helykiszolgáló és a helyrendszerek közötti kommunikáció**)  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Server Message Block (SMB)|--|445|  
|RPC végpontleképező|135|135|  
|RPC|--|DYNAMIC (Lásd a 6. megjegyzést: **Dinamikus portok**)|  

###  <a name="BKMK_PortsSite-Site"></a>Helykiszolgáló &lt; --> helykiszolgáló  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Server Message Block (SMB)|--|445|  

###  <a name="BKMK_PortsSite-SQL"></a>Helykiszolgáló--> SQL Server  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|SQL TCP protokollon keresztül|--|1433 (lásd a 2. megjegyzést: **alternatív port elérhető**)|  

 Olyan helyet, amely távoli SQL Server a Helyadatbázis futtatására a telepítés során kell megnyitnia a helykiszolgáló és az SQL Server között a következő portokat:  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Server Message Block (SMB)|--|445|  
|RPC végpontleképező|135|135|  
|RPC|--|DYNAMIC (Lásd a 6. megjegyzést: **Dinamikus portok**)|  

###  <a name="BKMK_PortsSite-Provider"></a>Helykiszolgáló--> SMS-szolgáltató  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Server Message Block (SMB)|--|445|  
|RPC végpontleképező|135|135|  
|RPC|--|DYNAMIC (Lásd a 6. megjegyzést: **Dinamikus portok**)|  

###  <a name="BKMK_PortsSite-SUP"></a>Helykiszolgáló &lt; --> szoftverfrissítési pont  
 (Lásd az 5. megjegyzést: **A helykiszolgáló és a helyrendszerek közötti kommunikáció**)  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Server Message Block (SMB)|--|445|  
|Hypertext Transfer Protocol (HTTP)|--|80 vagy 8530 (Lásd a 3. megjegyzést: **Windows Server Update Services**)|  
|Secure Hypertext Transfer Protocol (HTTPS)|--|443 vagy 8531 (Lásd a 3. megjegyzést: **Windows Server Update Services**)|  

###  <a name="BKMK_PortsSite-SMP"></a>Helykiszolgáló &lt; --> állapotáttelepítési pont  
 (Lásd az 5. megjegyzést: **A helykiszolgáló és a helyrendszerek közötti kommunikáció**)  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Server Message Block (SMB)|--|445|  
|RPC végpontleképező|135|135|  

###  <a name="BKMK_PortsProvider-SQL"></a> SMS-szolgáltató -- &gt; SQL Server  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|SQL TCP protokollon keresztül|--|1433 (lásd a 2. megjegyzést: **alternatív port elérhető**)|  

###  <a name="BKMK_PortsSUP-Internet"></a>Szoftverfrissítési pont--> Internet  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Hypertext Transfer Protocol (HTTP)|--|80 (lásd: 1. megjegyzést: **proxykiszolgáló portja**)|  

###  <a name="BKMK_PortsSUP-WSUS"></a>Szoftverfrissítési pont--> felsőbb rétegbeli WSUS-kiszolgáló  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Hypertext Transfer Protocol (HTTP)|--|80 vagy 8530 (Lásd a 3. megjegyzést: **Windows Server Update Services**)|  
|Secure Hypertext Transfer Protocol (HTTPS)|--|443 vagy 8531 (Lásd a 3. megjegyzést: **Windows Server Update Services**)|  

###  <a name="BKMK_PortsSQL-SQL"></a> SQL Server --&gt; SQL Server  
 A helyek közötti adatbázis-replikáció az SQL Server egy adott helyen és közvetlenül kommunikáljanak a szülő és gyermek hely az SQL Server szükséges.  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|SQL Server szolgáltatás|--|1433 (lásd a 2. megjegyzést: **alternatív port elérhető**)|  
|SQL Server Service Broker|--|4022 (lásd a 2. megjegyzést: **alternatív port elérhető**)|  

> [!TIP]  
>  Nem igényli a Configuration Manager az SQL Server Browser bővítményt, amely az 1434-es UDP-portot használja.  

###  <a name="BKMK_PortsStateMigrationPoint-to-SQL"></a>Állapotáttelepítési pont--> SQL Server  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|SQL TCP protokollon keresztül|--|1433 (lásd a 2. megjegyzést: **alternatív port elérhető**)|  



###  <a name="BKMY_PortNotes"></a> Megjegyzések a Configuration Manager ügyfelei és helyrendszerei által használt portokhoz  

1.  **Proxykiszolgáló portja**: Ez a port nem konfigurálható, de átirányítható egy konfigurált proxykiszolgálón.  

2.  **Alternatív port elérhető**: Alternatív port adható meg a Configuration Manager ezt az értéket. Egyéni port definiálása esetén helyettesítse be ezt az egyéni portot, amikor az IPsec-házirendek IP-szűrési adatait definiálja vagy a tűzfalakat konfigurálja.  

3.  **Windows Server Update Services (WSUS)**: A WSUS telepíthető portok: 80/443-as vagy a 8530-as/8531-es portot használja az ügyfél-kommunikációhoz. A Windows Server 2012 vagy Windows Server 2016 futtatásakor a WSUS a WSUS a 8530-as portot használja a HTTP és a 8531-es portot a HTTPS-hez alapértelmezés szerint van konfigurálva.  

     A telepítés után a port megváltoztatható. Nem kell ugyanazt a portszámot használni a teljes helyhierarchiában.  

    -   Ha a HTTP-port a 80-as, akkor a HTTPS-portnak a 443-asnak kell lennie.  

    -   Ha a HTTP-port bármi más, a HTTPS-portja kell 1-es vagy újabb verzióját, például 8530-as és 8531-es.   

    > [!NOTE]  
    >  A szoftverfrissítési pont a HTTPS protokoll használatára való konfigurálásakor a HTTP-portnak is nyitva kell lennie. A titkosítatlan adatok, például egyes frissítések licencfeltételei a HTTP-portot használják.  

4.  **Trivial FTP (TFTP) démon**: A Trivial FTP (TFTP) démon rendszerszolgáltatás nem igényel felhasználónevet vagy jelszót, és a Windows-telepítési szolgáltatások (WDS) beépített része. A Trivial FTP démon szolgáltatás biztosítja a következő RFC-k által definiált TFTP protokoll támogatását:  

    -   RFC 350: TFTP  

    -   RFC 2347: A beállítás bővítmény  

    -   RFC 2348: Blokkolás mérete lehetőség  

    -   RFC 2349: Időtúllépési időköz és átviteli méret beállításai  

     A TFTP egy fájlátviteli protokoll, amelyet a lemez nélküli rendszerindító környezetek támogatására hoztak létre. A TFTP démon a 69-es UDP-portot figyeli, de egy véletlenszerűen lefoglalt magas számú porton keresztül válaszol. Ezért a port engedélyezésekor lehetővé teszi a TFTP szolgáltatás fogadhatja a bejövő TFTP-kérelmeket, de nem engedélyezi a kiválasztott kiszolgáló válaszol a kérelmekre. A kijelölt kiszolgáló válaszolni a bejövő TFTP-kérelmeket, kivéve, ha a TFTP-kiszolgáló úgy van konfigurálva, hogy a 69-es porton válaszoljon nem engedélyezhető.  

5.  **A helykiszolgáló és helyrendszerek közötti kommunikáció**: Alapértelmezés szerint a helykiszolgáló és helyrendszerek közötti kommunikáció kétirányú. A helykiszolgáló kezdeményezi a kommunikációt a helyrendszer konfigurálásához, majd a legtöbb helyrendszer kapcsolódik a helykiszolgálóhoz, hogy elküldje az állapotadatait. A jelentéskészítési szolgáltatási pontok és a terjesztési pontok nem küldenek állapotadatokat. Ha **megkövetelése a helykiszolgálótól ehhez a helyrendszerhez kapcsolatok kezdeményezésének** a helyrendszer tulajdonságainál a helyrendszer telepítése után a helyrendszer nem fog kommunikációt kezdeményeznek a helykiszolgálón. Ehelyett a helykiszolgáló kezdeményezi a kommunikációt, és a helyrendszer-telepítési fiókot használja a hitelesítéshez a helyrendszer-kiszolgálóra.  

6.  **Dinamikus portok**: Dinamikus portok (más néven elmúló port) az operációs rendszer verziója által definiált portszámtartományt használnak. További információ az alapértelmezett porttartományokról: [A Windows rendszer szolgáltatásainak áttekintése és a hálózati portokra vonatkozó követelmények](http://go.microsoft.com/fwlink/p/?LinkId=317965).  

##  <a name="BKMK_AdditionalPorts"></a> További portlisták  
 A következő részekben a Configuration Manager által használt portokkal kapcsolatos további információk.  

###  <a name="BKMK_ClientShares"></a> Ügyfél és kiszolgáló közötti megosztások  
 Az ügyfelek mindig a Server Message Block (SMB) protokollt használják, amikor kapcsolódnak az UNC-megosztásokhoz. Példa:  

-   Kézi ügyféltelepítés a CCMSetup.exe **/source:** parancssori tulajdonság  

-   Endpoint Protection-ügyfelek, amelyek UNC elérési úton definíciós fájlok letöltésére

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Server Message Block (SMB)|--|445|  

###  <a name="BKMK_SQLPorts"></a> Kapcsolódás a Microsoft SQL Server rendszerhez  
 Az SQL Server adatbázismotorhoz való csatlakozáshoz és a helyek közötti replikációhoz használhatja az SQL Server alapértelmezett portját vagy megadhat egyéni portokat is:  

-   A helyek közötti kommunikáció a következőket használja:  

    -   SQL Server Service Broker, alapértelmezett beállítása a 4022-es TCP-port.  

    -   SQL Server szolgáltatás, amely alapértelmezés szerint a TCP 1433 portot.  

-   Az SQL Server adatbázismotor és a különböző Configuration Manager helyrendszerszerepkörök közötti helyen belüli kommunikáció alapértelmezés szerint a TCP 1433 portot.  

- A Configuration Manager használ a azonos portok és protokollok minden, ha a replika egy önálló SQL Server-példány volt a helyadatbázist futtató SQL rendelkezésre állási csoport replika folytatott kommunikációhoz.

Azure használatakor, és a Helyadatbázis egy belső vagy külső terheléselosztó mögött van, a következő tűzfalkivételeket konfigurálása minden egyes replikához, és terheléselosztási szabályok a következő portokat:
 - SQL TCP protokollon keresztül: TCP 1433
 - SQL Server Service Broker: 4022-ES TCP
 - Kiszolgálói üzenetblokk (SMB): TCP 445
 - RPC végpontleképező: TCP 135

> [!WARNING]  
>  A Configuration Manager nem támogatja a dinamikus portokat. Az SQL Server megnevezett példányai alapértelmezés szerint dinamikus portokat használnak az adatbázismotorhoz való csatlakozáshoz, ezért amikor megnevezett példányt használ, kézzel kell konfigurálnia azt a statikus portot, amelyet a helyen belüli kommunikációhoz kíván használni.  

 A következő helyrendszerszerepkörök közvetlenül kommunikálnak az SQL Server adatbázissal:  

-   Alkalmazáskatalógus webszolgáltatási pontja  

-   Tanúsítványregisztrációs pont szerepkör  

-   Beléptetési pont szerepkör  

-   Felügyeleti pont  

-   Helykiszolgáló  

-   Jelentéskészítési szolgáltatási pont  

-   SMS Provider  

-   SQL Server--> SQL Server  

Ha egy SQL Server egynél több helyet használ adatbázis-futtatáshoz, minden adatbázisnak külön SQL Server-példányt kell használnia, és minden példányt egyedi portkészlettel kell konfigurálni.  

Ha a tűzfal engedélyezve van az SQL Server-számítógépen, győződjön meg arról, hogy azt engedélyezésére van konfigurálva a portokat használja a telepítés során. Kiegészítő helyeken engedélyezi ezeket a portokat az SQL Server kommunikáló számítógépek közötti hálózati tűzfalak is konfigurálhat.  

Példa bemutatja, hogyan konfigurálhatja az SQL Server egy adott port használatára, lásd: [hogyan: A Server to Listen on a Specific TCP Port (SQL Server Configuration Manager) konfigurálása](http://go.microsoft.com/fwlink/p/?LinkID=226349) az SQL Server TechNet könyvtárban.  


### <a name="bkmk_discovery"></a> Felderítési és közzététele
A következő portokat kell használni a felderítési és a helyadatok közzétételére:
 - Lightweight Directory Access Protocol (LDAP): 389
 - LDAP (Secure Sockets Layer [SSL] kapcsolat): 636


 - Globális katalógus – LDAP: 3268
 - Globális katalógus – LDAP SSL: 3269


 - RPC végpontleképező: 135
 - RPC: Dinamikusan lefoglalt magas TCP-portok


 - TCP: 1024: 5000
 - TCP:  49152: 65535


###  <a name="BKMK_External"></a> A Configuration Manager által létrehozott külső kapcsolatok  
 Configuration Manager-ügyfelek vagy -helyrendszerek a következő külső kapcsolatokat létesíthetik:  

-   [Eszközintelligencia szinkronizálási pontja-- &gt; Microsoft](#BKMK_PortsAI)  

-   [Endpoint Protection-pont-- &gt; Internet](#BKMK_PortsEndpointProtection_Internet)  

-   [Ügyfél-- &gt; globális katalógus tartományvezérlője](#BKMK_PortsClient-GCDC)  

-   [A Configuration Manager konzol-- &gt; Internet](#BKMK_PortsConsole-Internet)  

-   [Felügyeleti pont-- &gt; tartományvezérlő](#BKMK_PortsMP-DC)  

-   [Helykiszolgáló-- &gt; tartományvezérlő](#BKMK_PortsSite-DC)  

-   [Helykiszolgáló &lt;  --  &gt; kibocsátó hitelesítésszolgáltató (CA)](#BKMK_PortsIssuingCA_SiteServer)  

-   [Szoftverfrissítési pont-- &gt; Internet](#BKMK_PortsSUP-Internet)  

-   [Szoftverfrissítési pont-- &gt; felsőbb rétegbeli WSUS-kiszolgáló](#BKMK_PortsSUP-WSUS)  

-   [Szolgáltatáskapcsolódási pont-- &gt; a Microsoft Intune](#BKMK_PortsIntuneConnector-WindowsIntune)  

###  <a name="BKMK_IBCMports"></a> Az internetes ügyfeleket támogató helyrendszerek telepítési követelményei  
 Felügyeleti pontok és terjesztési pontok, amelyek támogatják az internetalapú ügyfeleket, a szoftverfrissítési pont és a tartalék állapotkezelő pont a következő portokat használják telepítéshez és a javítás:  

-   Helykiszolgáló--> helyrendszer: 135-ös UDP- és TCP-portot használó RPC végpontleképező.  

-   Helykiszolgáló--> helyrendszer: Dinamikus RPC TCP-portok  

-   Helykiszolgáló &lt; --> helyrendszer: Kiszolgáló-üzenetblokkok (SMB) használatával a TCP 445-ös port.

Alkalmazások és csomagok terjesztési pontokra való telepítéséhez a következő RPC-portok szükségesek:  

-   Helykiszolgáló--> terjesztési pont: 135-ös UDP- és TCP-portot használó RPC végpontleképező

-   Helykiszolgáló--> terjesztési pont: Dinamikus RPC TCP-portok  

A helykiszolgálók és helyrendszerek közötti adatforgalom biztonságossá tételéhez használja az IPsec protokollt. Ha korlátoznia kell a használt dinamikus RPC-portokat, a Microsoft RPC konfigurációs eszközzel (rpccfg.exe) korlátozott számú portok konfigurálhatók ezekhez az RPC-csomagokhoz. További információ az RPC konfigurációs eszközről: [A távoli eljáráshívás (RPC) szolgáltatás konfigurálása adott portok használatára és ezen portok biztonságossá tétele az IPsec használatával](http://go.microsoft.com/fwlink/p/?LinkId=124096).  

> [!IMPORTANT]  
>  Ezek a helyrendszerek telepítése előtt győződjön meg arról, hogy a távoli beállításjegyzék szolgáltatás fut-e a helyrendszer-kiszolgálón, hogy a helyrendszer-telepítési fiók megadta, ha a helyrendszer egy másik Active Directory-erdő megbízhatósági kapcsolat nélkül.  

###  <a name="BKMK_PortsClientInstall"></a> A Configuration Manager-ügyfelek telepítése által használt portok  
Az, hogy ügyféltelepítéskor milyen portokat használ a rendszer, a központi telepítés módjától függ. Az egyes ügyfél-telepítési módszerek portok listáját lásd: **Configuration Manager-ügyfelek telepítése során használt portok** a a [Windows tűzfal és a System Center Configuration Manager-ügyfelek portbeállítások](../../../core/clients/deploy/windows-firewall-and-port-settings-for-clients.md) témakör. További információ a Windows tűzfalat az ügyfélen ügyféltelepítéshez és a telepítés utáni kommunikációhoz: [a Windows tűzfal és a System Center Configuration Manager-ügyfelek portbeállítások](../../../core/clients/deploy/windows-firewall-and-port-settings-for-clients.md).  

###  <a name="BKMK_MigrationPorts"></a> Áttelepítés által használt portok  
Az áttelepítést futtató helykiszolgáló számos portot használ az adatok gyűjtését a forráshely SQL Server-adatbázisok és a terjesztési pontok megosztása a forráshierarchia alkalmazható helyeihez való kapcsolódáshoz.  

 Ezeket a portokat kapcsolatos információkért tekintse meg a [az áttelepítéshez szükséges konfigurációk](../../../core/migration/prerequisites-for-migration.md#BKMK_Required_Configurations) szakasz a [előfeltételei a System Center Configuration Manager áttelepítési](../../../core/migration/prerequisites-for-migration.md) témakör.  

###  <a name="BKMK_ServerPorts"></a> A Windows Server által használt portok  
 Az alábbi táblázat néhány fontosabb port és azok funkciói találhatók a Windows Server által használt. Részletesebb információ a Windows Server szolgáltatásaival és hálózati portjaival kapcsolatos követelményekről: [A Windows Server rendszer szolgáltatásainak áttekintése és a hálózati portokra vonatkozó követelmények](http://go.microsoft.com/fwlink/p/?LinkID=123652).  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Tartománynévrendszer (DNS)|53|53|  
|Dynamic Host Configuration Protocol (DHCP)|67 és 68|--|  
|NetBIOS-névfeloldás|137|--|  
|NetBIOS datagramszolgáltatás|138|--|  
|NetBIOS munkamenet-szolgáltatás|--|139|  

