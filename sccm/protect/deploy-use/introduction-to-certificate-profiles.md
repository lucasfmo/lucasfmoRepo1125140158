---
title: "Tanúsítványprofilok ismertetése |} Microsoft Docs"
description: "Ismerje meg, hogyan működnek a tanúsítványprofilok a System Center Configuration Manager Active Directory tanúsítványszolgáltatás a."
ms.custom: na
ms.date: 03/30/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 41dcc259-f147-4420-bff2-b65bdf8cff77
caps.latest.revision: 7
author: arob98
ms.author: angrobe
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: aa8924a013ebdbee888cab33001fddbe7ad2d67e
ms.openlocfilehash: 1864f814152233d3c67bd83a96623e4a6e051569
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---

# <a name="introduction-to-certificate-profiles-in-system-center-configuration-manager"></a>Tanúsítványprofilok ismertetése a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


Tanúsítványprofilok működik az Active Directory tanúsítványszolgáltatások és a felügyelt eszközöknek tanúsítványhitelesítést biztosítsanak kiépítése a hálózati eszközök tanúsítványigénylési szolgáltatása szerepkör, úgy, hogy a felhasználók zökkenőmentesen a vállalati erőforrások eléréséhez. Létrehozhat és telepíthet például olyan tanúsítványprofilokat, amelyek ellátják a felhasználókat a szükséges tanúsítványokkal, hogy kezdeményezzenek VPN és vezetéknélküli kapcsolatokat. 

A tanúsítványprofilok automatikusan konfigurálják a felhasználók készülékét, tehát a vállalat olyan erőforrásai, mint a Wi-Fi hálózatok és a VPN kiszolgálók elérhetők anélkül, hogy manuálisan kellene tanúsítványt telepíteni, vagy más eljárást kellene használni. A tanúsítványprofilok a vállalati erőforrások biztonságának fenntartásában is segítenek, mivel használható több olyan beállítás is, amelyiket a vállalati nyilvános kulcsú infrastruktúra (PKI) támogatja. Megkövetelheti például a kiszolgálói hitelesítés használatát minden Wi-Fi és VPN kapcsolathoz, mivel a felügyelt eszközöket ellátta a szükséges tanúsítványokkal.   

A tanúsítványprofilok a következő felügyeleti képességeket biztosítják:  

-   Tanúsítványigénylés és -megújítás egy vállalati hitelesítésszolgáltató (CA) iOS, Windows 8.1, Windows RT 8.1, Windows 10 asztali és mobil és Android rendszerű eszközökhöz. Ezek a tanúsítványok használható a Wi-Fi és VPN-kapcsolatok.  

-   Megbízható legfelső szintű hitelesítésszolgáltatói tanúsítványok és köztes hitelesítésszolgáltatói tanúsítványok központi telepítése a megbízható eszközök láncolatának konfigurálására, hogy VPN és Wi-Fi kapcsolatokat lehessen létesíteni, ha kiszolgálói hitelesítésre van szükség.  

-   A telepített tanúsítványok figyelése, és jelentések készítése  

**Példa:** Minden alkalmazott csatlakozhat a vállalat különböző helyszínein a Wi-Fi elérési pontokhoz való kell lennie. A Wi-Fi való csatlakozáshoz szükséges tanúsítványok központi telepítéséhez, és a tanúsítvány ahhoz, hogy zökkenőmentes felhasználói kapcsolat hivatkozó Wi-Fi profilok központi telepítése.  

**Példa:** A nyilvános kulcsokra épülő infrastruktúra rendelkezik, és szeretne áttérni a tanúsítványszolgáltatás egy olyan rugalmasabb, biztonságosabb módjára, amely lehetővé teszi, hogy felhasználók elérjék a vállalati erőforrásokhoz a személyes eszközeikről biztonság csökkenése nélkül. Tanúsítványprofilok konfigurálása olyan beállításokkal és protokollokkal, amelyek támogatják az adott eszközplatform számára. A készülékek ezt követően automatikusan lekérhetik ezeket a tanúsítványokat egy internetes elérésű beléptetési kiszolgálótól. Ezt követően konfigurálja a VPN-profilokat a tanúsítványok használatára, hogy az eszköz a vállalati erőforrások eléréséhez.  

## <a name="types-of-certificate-profiles"></a>Tanúsítványprofilok típusai  
 Háromféle típusú tanúsítványprofil van:  

-   **Megbízható Hitelesítésszolgáltatói tanúsítvány** -segítségével telepíthet egy megbízható legfelső szintű hitelesítésszolgáltató vagy köztes szintű Hitelesítésszolgáltatót megbízható tanúsítványlánc kialakításához, amikor az eszköznek kiszolgálót kell hitelesíteni.  

-   **Egyszerű tanúsítványigénylési protokoll (SCEP)** -lehetővé teszi, hogy egy eszköz vagy felhasználó tanúsítványt igényelni a SCEP protokoll és a hálózati eszközök tanúsítványigénylési szolgáltatása a Windows Server 2012 R2-t futtató kiszolgálón.
-   **Személyes információcsere (.pfx)** -lehetővé teszi, hogy egy eszköz vagy felhasználó (más néven a PKCS #12) .pfx tanúsítvány kérése.

    > [!NOTE]  
    >  Létre kell hoznia egy tanúsítványprofilt a típusú **megbízható Hitelesítésszolgáltatói tanúsítvány** létrehozása előtt egy **egyszerű tanúsítványigénylési protokoll (SCEP)** tanúsítványprofilt.  

## <a name="requirements-and-supported-platforms"></a>Követelmények és támogatott platformok  
 Az SCEP protokollt használó tanúsítványprofilok központi telepítéséhez telepítenie kell a tanúsítványregisztrációs pont helyrendszer-kiszolgálót a központi adminisztrációs hely vagy elsődleges hely. Házirendmodul telepítése az ndes számára, a Configuration Manager házirend moduljának olyan kiszolgálóra, amely a Windows Server 2012 R2 fut, az Active Directory tanúsítványszolgáltatások szerepkör, és egy működő hálózati eszközök Tanúsítványigénylési, amely elérhető a tanúsítványt igénylő eszközök is. A Microsoft Intune által beléptetett eszközök esetén ehhez a hálózati eszközök Tanúsítványigénylési az internetről, például egy szegélyhálózatban (más néven DMZ) alhálózatban elérhetőnek kell lennie.  

 További információ a hogyan a hálózati eszközök tanúsítványigénylési szolgáltatása támogatja a házirendmodult úgy, hogy a Configuration Manager tanúsítványok központi telepítésére: [házirendmodul használata a hálózati eszközök tanúsítványigénylési szolgáltatása](http://go.microsoft.com/fwlink/p/?LinkId=328657).  

 A Configuration Manager támogatja a tanúsítványok különböző tanúsítványtárakba, attól függően, hogy a követelmények, az eszköz típusát és az operációs rendszer telepítését. A következő eszközök és operációs rendszerek támogatottak:  

-   Windows RT 8.1  

-   Windows 8.1  

-   Windows Phone 8.1  

-   Windows 10 asztali és mobil verziója  

-   iOS  

-   Android  

> [!IMPORTANT]  
>  Android, iOS, Windows Phone és beléptetett Windows 8.1 vagy újabb rendszerű eszközök profilokat telepíteni, ezeket az eszközöket lehet [Microsoft Intune-ban regisztrált](https://technet.microsoft.com/en-us/library/dn646962.aspx).   

A rendszer a jellemző forgatókönyv a System Center Configuration Manager telepíti a megbízható legfelső szintű Hitelesítésszolgáltatói tanúsítványokat telepítenek a Wi-Fi és VPN-kiszolgálót, ha a kapcsolat EAP-TLS, EAP-TTLS, és PEAP hitelesítési protokollt, és az IKEv2, L2TP/IPsec és egyesítő Cisco IPsec VPN protokollt használja.  

Meg kell győződni arról, hogy a vállalat gyökér szintű tanúsítványa már telepítve van az eszközön, amikor az tanúsítványokat kérne le az SCEP tanúsítványprofil használatával.  

Az SCEP tanúsítványprofilban megadhatók különböző beállítások a különböző környezetek vagy kapcsolódási igények szerint testre szabott tanúsítványok lekéréséhez. A **Tanúsítványprofil létrehozása varázsló** két lapot tartalmaz az igénylési paraméterek részére. Az első, az **SCEP-igénylés**tartalmazza az igénylési kérelmek beállításait, és azt, hogy a tanúsítvány hova legyen telepítve. A második, a **Tanúsítvány tulajdonságai**magát a lekért tanúsítványt ismerteti.  

## <a name="deploying-certificate-profiles"></a>Tanúsítványprofilok központi telepítése  
 A tanúsítványprofil központi telepítésekor a profil tanúsítványfájljai telepítve lesznek az ügyféleszközökre. Telepítve lesznek az SCEP esetleges paraméterei is, és az SCEP kérelmei az ügyféleszközön lesznek feldolgozva. Tanúsítványprofilok központi telepítése a felhasználói és eszközcsoportokra, és adja meg az egyes tanúsítványok tárolási célhelye. Az alkalmazhatósági szabályok határozzák meg, hogy a tanúsítványok telepíthetők-e az eszközre. A tanúsítványprofilok felhasználógyűjtemények van telepítve, amikor a felhasználó-eszköz kapcsolat határozza meg, mely a felhasználók eszközein lesznek telepítve a tanúsítványok. Ha felhasználói tanúsítványokat tartalmazó tanúsítványprofilok vannak telepítve eszközök gyűjteményére alapértelmezés szerint a tanúsítványok települ az egyes a felhasználók elsődleges eszközére. Ez a viselkedés telepíteni tudja a tanúsítványt, a felhasználók eszközökhöz módosíthatja a **SCEP-igénylés** oldalán a **Tanúsítványprofil létrehozása varázsló**. A felhasználói tanúsítványok viszont nem lesznek telepítve olyan eszközre, amelyik munkacsoporti számítógép.  

## <a name="monitoring-certificate-profiles"></a>Tanúsítványprofilok figyelése  

Tanúsítványprofil-telepítéseket megfelelőségi eredményeit, illetve a jelentések megtekintésével figyelheti. Ezek a módszerek ismertetett [tanúsítványprofilok figyelése](/sccm/protect/deploy-use/monitor-certificate-profiles).


## <a name="automatic-revocation-of-certificates"></a>Tanúsítványok automatikus visszahívása  
 A System Center Configuration Manager automatikusan visszavonja a felhasználói és számítógépi tanúsítványokat, amelyek tanúsítványprofilok használatával a következő körülmények között lettek telepítve:  

-   Az eszközt kivonják a System Center Configuration Manager felügyelet alól.  

-   Az eszköz ki lett törölve szelektíven.  

-   Az eszköz le lesz tiltva, a System Center Configuration Manager hierarchiából.  

 A tanúsítvány visszahívásához a helykiszolgáló visszahívási parancsot küld a tanúsítványt kibocsátó tanúsítványszolgáltatónak. A visszahívás oka **A tevékenység megszűnt**.  
