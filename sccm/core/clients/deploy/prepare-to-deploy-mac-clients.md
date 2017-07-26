---
title: "Felkészülés az ügyfélszoftver központi telepítése Mac-számítógépekre |} Microsoft Docs"
description: "Konfigurációs feladatok Mac számítógépekhez a Configuration Manager-ügyfél központi telepítése előtt."
ms.custom: na
ms.date: 05/04/2017
ms.prod: configuration-manager
ms.reviewer: aaroncz
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2285a953-6a86-4ed5-97dd-cd57b02bc1ee
caps.latest.revision: 12
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: c6a6137fa978e1ea28aefea2aea4e29ba661efd6
ms.openlocfilehash: b3bb72f81812705b4654e268025074402e89a7cb
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---

# <a name="prepare-to-deploy-client-software-to-macs"></a>Felkészülés az ügyfélszoftver központi telepítése Mac-számítógépekre

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Győződjön meg arról, hogy készen áll az alábbi lépéseket követve [telepíthetők központilag Mac számítógépekre a Configuration Manager-ügyfél](/sccm/core/clients/deploy/deploy-clients-to-macs). 

## <a name="mac-prerequisites"></a>Mac-Előfeltételek

A Mac ügyfél-telepítési csomag nem rendelkezik a Configuration Manager adathordozóján. Töltse le a **ügyfelek egyéb operációs rendszerekhez** a a [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=525184).  

**Támogatott verziók:**  

-   **Mac OS X 10.6** (Hópárduc) 

-   **Mac OS X 10.7** (Lion) 

-   **Mac OS X 10.8** (Mountain Lion)

-   **Mac OS X 10.9** (Mavericks)

-   **Mac OS X 10.9** (Mavericks)  

-   **Mac OS X 10.10 rendszert** (Yosemite)  

-   **Mac OS X 10.11** (El Capitan)  

-   **Mac OS X 10.12** (macOS Sierra)  

## <a name="certificate-requirements"></a>Tanúsítványkövetelmények
Ügyfél telepítése és felügyelet Mac számítógépek a nyilvános kulcsokra épülő infrastruktúra (PKI) tanúsítványokat igényel. PKI-tanúsítványok kölcsönös hitelesítéssel és titkosított adattovábbítással a Mac számítógépek és a Configuration Manager-hely közötti kommunikáció védelméhez. A Configuration Manager kérelmezhet és telepíthet a felhasználói ügyféltanúsítványt a vállalati hitelesítésszolgáltató (CA) és a Configuration Manager beléptetési pont és a beléptetési proxy pont helyrendszer-szerepkörök Microsoft tanúsítványszolgáltatások használatával. Vagy is igényli és telepíti a számítógép-tanúsítvány egymástól függetlenül a Configuration Manager alkalmazásból, ha a tanúsítvány megfelel a követelményeknek, a Configuration Manager számára.   
  
A Configuration Manager Mac rendszerű ügyfelei mindig elvégzik a tanúsítvány-visszavonási ellenőrzést. Ez a funkció nem tiltható le.  
  
Ha a Mac ügyfelek nem tudják megerősíteni egy kiszolgálótanúsítvány tanúsítvány-visszavonási állapotát, mert nem találják a CRL-t, nem fogják tudni kapcsolódni a Configuration Manager helyrendszerei. Főként a kibocsátó hitelesítésszolgáltatóétól eltérő erdőben található Mac rendszerű ügyfelek esetén fontos ellenőrizni a CRL felépítését, hogy a Mac rendszerű ügyfelek megtalálják a CRL terjesztési pontját, és csatlakozni tudjanak hozzá a helyrendszer-kiszolgálókhoz való kapcsolódáshoz.  

Mielőtt a Configuration Manager-ügyfél a Mac számítógépen telepíti, döntse el, hogyan telepítheti az ügyféltanúsítványt:  

-   Használja a Configuration Manager beléptetést a [CMEnroll eszköz](/sccm/core/clients/deploy/deploy-clients-to-macs#install-the-client-and-then-enroll-the-client-certificate-on-the-mac). A beléptetési folyamat nem támogatja az automatikus tanúsítványmegújítást, ezért a Mac számítógépeket a telepített tanúsítvány lejárta előtt újra be kell léptetni.  

-   [A tanúsítvány lekérését és telepítését módszer, amely független a Configuration Manager](/sccm/core/clients/deploy/deploy-clients-to-macs#use-a-certificate-request-and-installation-method-that-is-independent-from-configuration-manager).  

A Mac ügyféltanúsítvány-igényéről és a Mac számítógépek támogatásához szükséges más PKI-tanúsítványok kapcsolatos további információkért lásd: [PKI-tanúsítványkövetelmények a System Center Configuration Manager](../../../core/plan-design/network/pki-certificate-requirements.md).  

Mac-ügyfél automatikusan rendelt a Configuration Manager-hely, amely felügyeli őket. A Mac rendszerű ügyfelek csak internetes ügyfelekként települnek, akkor is, ha a kommunikáció az intranetre korlátozódik. Ez az ügyfél-konfiguráció azt jelenti, hogy ezek az ügyfelek a hozzájuk társított helyek helyrendszerszerepköreivel (a felügyeleti és terjesztési pontokkal) kommunikálnak, ha beállítja, hogy a helyrendszerszerepkörök engedélyezzék az interneten keresztüli ügyfélkapcsolatokat. A Mac számítógépek a hozzárendelt helyen kívüli helyrendszerszerepkörökkel nem kommunikálnak.  

> [!IMPORTANT]  
>  A Configuration Manager Mac-ügyfél nem használható a használatára konfigurált felügyeleti ponthoz kapcsolódni egy [adatbázis-replika](../../../core/servers/deploy/configure/database-replicas-for-management-points.md).  


## <a name="deploy-a-web-server-certificate-to-site-system-servers"></a>Helyrendszer-kiszolgálók egy webkiszolgáló-tanúsítvány telepítése  
Ezek a helyrendszerek nincs meg, ha a helyrendszerszerepköröket futtató számítógépekre történő központi telepítése egy webkiszolgáló-tanúsítvány:  

-   Felügyeleti pont  

-   Terjesztési pont  

-   Beléptetési pont  

-   Beléptetési proxypont  

A webkiszolgáló-tanúsítványnak tartalmaznia kell az internetes teljesen minősített tartománynevet (FQDN), amely a helyrendszer tulajdonságai között van megadva. A kiszolgáló nem rendelkezik az internetről a Mac számítógépek támogatásához elérhetőnek kell lennie. Ha nem igényel internetalapú ügyfélfelügyeletet, megadhatja az intranetes teljes tartománynév értékét az internetes helyett.  

Adja meg a helyrendszer internetes teljes tartománynév értékét a webkiszolgáló-tanúsítvány a felügyeleti pont, a terjesztési pont és a beléptetési proxypontot. 

Központi telepítésre példát hoz létre, és telepíti a webkiszolgáló-tanúsítványt, tekintse meg a [a webkiszolgáló-tanúsítvány telepítése a Helyrendszerekhez, hogy futtassa IIS](../../plan-design/network/example-deployment-of-pki-certificates.md#BKMK_webserver2008_cm2012).  


## <a name="deploy-a-client-authentication-certificate-to-site-system-servers"></a>Ügyfél-hitelesítési tanúsítvány központi telepítése a helyrendszer-kiszolgálókon  
 Ezek a helyrendszerek nincs meg, ha egy ügyfél-hitelesítési tanúsítvány telepítendő helyrendszerszerepköröket futtató számítógépekre:  

-   Felügyeleti pont  

-   Terjesztési pont  

 Központi telepítésre példát, amely létrehoz és telepít egy ügyféltanúsítványt a felügyeleti pontokhoz, tekintse meg a [a tanúsítvány a Windows ügyfélszámítógépek telepítése](../../plan-design/network/example-deployment-of-pki-certificates.md#BKMK_client2008_cm2012)  

 Központi telepítésre példát, amely létrehoz és telepít egy ügyféltanúsítványt a terjesztési pontok, tekintse meg a [a terjesztési pontok az ügyféltanúsítvány központi telepítése](../../plan-design/network/example-deployment-of-pki-certificates.md#BKMK_clientdistributionpoint2008_cm2012).  

>[!IMPORTANT]
>  Az ügyfél eszközökre telepíteni kívánt macOS Sierra fut, a tulajdonos nevét a felügyeleti pont tanúsítványának kell megfelelően kell konfigurálni, például a a felügyeletipont-kiszolgáló teljes Tartományneve.

## <a name="prepare-the-client-certificate-template-for-macs"></a>Az ügyfél-sablon előkészítése Mac számítógépekhez  

 A tanúsítványsablonnak rendelkeznie kell **Olvasás** és **Beléptetés** engedéllyel ahhoz a felhasználói fiókhoz, amely be fogja léptetni a tanúsítványt a Mac számítógépen.  

 Lásd: [az ügyféltanúsítvány központi telepítése Mac számítógépekhez](../../plan-design/network/example-deployment-of-pki-certificates.md#BKMK_MacClient_SP1).  

## <a name="configure-the-management-point-and-distribution-point"></a>A felügyeleti pont és terjesztési pont konfigurálása  
 Konfigurálja a felügyeleti pontokon a következő beállításokat:  

-   HTTPS  

-   Lehetővé tegyék az ügyfélkapcsolatokat az internetről. Ez a konfigurációs érték szükséges a Mac számítógépek felügyeletéhez. Ez azonban nem jelenti azt, hogy a helyrendszer-kiszolgálóknak elérhetőknek kell lenniük az internetről.  

-   A felügyeleti pont használatának engedélyezése a mobileszközök és a Mac számítógépek számára  

 Bár a terjesztési pontok nem szükségesek az ügyfél telepítéséhez, úgy kell konfigurálni a terjesztési pontokat, hogy lehetővé tegyék az ügyfélkapcsolatokat az internetről, ha szeretne szoftvert telepíteni ezekre a számítógépekre, az ügyfél telepítése után.  

 
### <a name="to-configure-management-points-and-distribution-points-to-support-macs"></a>Felügyeleti pontok és terjesztési pontok Mac számítógépek támogatásához konfigurálása  

Mielőtt hozzákezd, győződjön meg arról, hogy a felügyeleti pontot és a terjesztési pontot futtató helyrendszer-kiszolgáló internetes teljes tartománynévvel van konfigurálva. Ha ezek a kiszolgálók Internet alapú ügyfélfelügyelet nem támogatja, megadhatja az intranetes teljes Tartománynevet az internetes teljes tartománynév értékét. 

A helyrendszer-szerepkörök egy elsődleges helyen kell lennie.  


1.  Kattintson a Configuration Manager konzol **felügyeleti** > **Helykonfiguráció** > **kiszolgálók és Helyrendszerszerepkörök**, és kattintson a jobb oldali helyrendszer-szerepkörökkel rendelkező kiszolgálónak.  

3.  A részleteket tartalmazó ablaktáblán kattintson a jobb gombbal **felügyeleti pont**, válassza a **szerepkör tulajdonságai**, és a a **felügyeleti pont tulajdonságai** párbeszédpanelen adja meg ezeket a beállításokat:  

    1.  Válasszon **HTTPS**.  

    2.  Válasszon **kapcsolatok engedélyezése csak az internetes ügyfelek** vagy **intranetes és internetes kapcsolatok engedélyezése**. Ezek a beállítások egy internetes vagy intranetes teljes Tartománynevet igényelnek.  

    3.  Válasszon **engedélyezése mobileszközök és Mac számítógépek számára a felügyeleti pont használatának**.  

4.  A részleteket tartalmazó ablaktáblán kattintson a jobb gombbal **terjesztési pont**, válassza a **szerepkör tulajdonságai**, és a a **terjesztési pont tulajdonságai** párbeszédpanelen adja meg ezeket a beállításokat:  

    -   Válasszon **HTTPS**.  

    -   Válasszon **kapcsolatok engedélyezése csak az internetes ügyfelek** vagy **intranetes és internetes kapcsolatok engedélyezése**. Ezek a beállítások egy internetes vagy intranetes teljes Tartománynevet igényelnek.  

    -   Válasszon **tanúsítvány importálása**, és keresse meg az exportált ügyfél terjesztési pontjának tanúsítványfájlját, majd adja meg a jelszót.  

5.  Az összes felügyeleti pontok és terjesztési pontok az elsődleges helyek, az Mac-eket használja, akkor ismételje meg a 2 – 4.  

## <a name="configure-the-enrollment-proxy-point-and-the-enrollment-point"></a>A beléptetési proxypont és a beléptetési pont konfigurálása  
 Mindkét helyrendszerszerepkört ugyanarra a helyre kell telepíteni, de nem szükséges ugyanarra a helyrendszer-kiszolgálóra vagy ugyanabba az Active Directory-erdőbe telepíteni.  

 További információ a helyrendszerszerepkörök elhelyezéséről és szempontokat lásd: [helyrendszer-szerepkörök](../../../core/plan-design/hierarchy/plan-for-site-system-servers-and-site-system-roles.md#bkmk_planroles) a [helyrendszer-kiszolgálók és helyrendszerszerepkörök tervezése a System Center Configuration Manager](../../../core/plan-design/hierarchy/plan-for-site-system-servers-and-site-system-roles.md).  

 Ezekkel az eljárásokkal konfigurálhatók a helyrendszerszerepkörök a Mac számítógépek támogatásához.   

-   [Új helyrendszer-kiszolgáló](#new-site-system-server)  

-   [Meglévő helyrendszer-kiszolgáló](#existing-site-system-server)  

###  <a name="new-site-system-server"></a>Új helyrendszer-kiszolgáló  

1.  Kattintson a Configuration Manager konzol **felügyeleti** >  **Helykonfiguráció** > **kiszolgálók és Helyrendszerszerepkörök**  

3.  Az a **Home** lap a **létrehozása** csoportjában válassza **helyrendszer-kiszolgáló létrehozása**.  

4.  Az a **általános** csoportjában adja meg a helyrendszer általános beállításait.  Győződjön meg arról, hogy az internetes teljes tartománynév adjon meg egy értéket. Ha a kiszolgáló nem lesz elérhető az internetről, használja az intranetes teljes Tartománynevet.  

5.  Az a **Rendszerszerepkör kiválasztása** lapon jelölje be **beléptetési proxypont** és **beléptetési pont** az elérhető szerepkörök listájából.  

6.  Az a **beléptetési Proxypont** lapon tekintse át a beállításokat, és végezze el a szükséges módosításokat.  

7.  Az a **beléptetési pont beállításai** lapon tekintse át a beállításokat, és végezze el a szükséges módosításokat. Ezután fejezze be a varázslót.  

### <a name="existing-site-system-server"></a>Meglévő helyrendszer-kiszolgáló  

1.  Kattintson a Configuration Manager konzol **felügyeleti** >  **Helykonfiguráció** > **kiszolgálók és Helyrendszerszerepkörök**, és válassza ki a kiszolgálót, amely a Mac számítógépek támogatásához használni szeretne.  

3.  Az a **Home** lap a **létrehozása** csoportjában válassza **helyrendszer-szerepkörök hozzáadása**.  

4.  Az **Általános** lapon adja meg a helyrendszer általános beállításait, majd kattintson a **Tovább**gombra. Győződjön meg arról, hogy az internetes teljes tartománynév adjon meg egy értéket. Ha a kiszolgáló nem lesz elérhető az internetről, használja az intranetes teljes Tartománynevet.   

5.  Az a **Rendszerszerepkör kiválasztása** lapon, válassza ki **beléptetési proxypont** és **beléptetési pont** az elérhető szerepkörök listájából.  

6.  Az a **beléptetési Proxypont** lapon tekintse át a beállításokat, és végezze el a szükséges módosításokat.  

7.  Az a **beléptetési pont beállításai** lapon tekintse át a beállításokat, és végezze el a szükséges módosításokat. Ezután fejezze be a varázslót.  

## <a name="install-the-reporting-services-point"></a>A jelentéskészítési szolgáltatási pont telepítése  
 [Telepítse a jelentéskészítési szolgáltatási pontot](../../../core/servers/manage/configuring-reporting.md) Ha szeretne jelentéseket futtatni Mac számítógépekhez.  

### <a name="next-steps"></a>További lépések

[A Configuration Manager-ügyfél központi telepítése Mac számítógépekre](/sccm/core/clients/deploy/deploy-clients-to-macs).  
