---
title: "Tervezze meg a helyszíni MDM |} Microsoft Docs"
description: "Tervezze meg a helyszíni mobileszköz-kezelés a System Center Configuration Manager rendszerű mobileszközök kezelésére."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 02979fb8-ea7e-4ec6-b7e0-ecbfda73e52d
caps.latest.revision: 9
caps.handback.revision: 0
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 507bad02c6e028f09a8b0c8a566ac55f7c3942a5
ms.openlocfilehash: 544c3bea0c7df96887ee1717f061c39c64b82d01
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="plan-for-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>A System Center Configuration Manager helyszíni mobileszköz-kezelésének tervezése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Vegye figyelembe az alábbi követelményeket kezelni a Configuration Manager infrastruktúra előkészítése előtt\-helyszíni mobileszköz-kezelés.

##  <a name="bkmk_devices"></a>Támogatott eszközök  
 A helyszíni mobileszköz-kezelés lehetővé teszi az eszköz operációs rendszerének beépített felügyeleti funkciói segítségével mobil eszközök kezelését.  A felügyeleti funkció az Open Mobile Alliance (OMA) Device Management (DM) szabványán alapul, és számos eszközplatform használja az eszközök felügyeletének lehetővé tételére.  Ezek nevezzük **modern eszközök** (a dokumentációjában és a Configuration Manager konzol felhasználói felületén) megkülönböztetendő más azokat kezelheti a Configuration Manager-ügyfél igénylő eszközök.  

 > [!NOTE]  
>  Az aktuális ág a Configuration Manager helyszíni mobileszköz-kezelés a következő operációs rendszereket futtató eszközök beléptetési támogatja:  
>   
> -  Windows 10 Enterprise  
> -   Windows 10 Pro  
> -   A Windows 10 Team \(kezdve a Configuration Manager 1602-es verzió\)  
> -   Windows 10 mobil verzió  
> -   Windows 10 Mobile Enterprise
> -   Windows 10 IoT Enterprise   

##  <a name="bkmk_intune"></a>A Microsoft Intune-előfizetés használata  
 Használatának\-helyszíni mobileszköz-kezelés, szüksége lesz egy Microsoft Intune-előfizetést. Az előfizetés csak az eszközök licenckezelésének nyomon követéséhez szükséges, és a program nem használja azt az eszközök felügyeletére vagy az eszközökre vonatkozó felügyeleti információk tárolására. Az összes felügyeleti tevékenység kezelése vállalati környezetben a helyi Configuration Manager infrastruktúrájának használatával.  

 > [!NOTE]  
 > A Configuration Manager támogatja 1610 verziójától kezdve a mobileszközök kezelését a Microsoft Intune és a helyi Configuration Manager infrastruktúrájának használatával egyszerre.   

 Ha a helyen vannak internetkapcsolattal rendelkező eszközök, az Intune szolgáltatás segítségével ellenőrizze, hogy az eszközfelügyeleti pont a házirend-frissítési eszközök értesítésére. Ez az Intune használata szigorúan csak az internetes kitettségű eszközök értesítésére szolgál. Internetkapcsolat nélküli eszközök (és az Intune által nem érhető el) a konfigurált lekérdezési időközt jelentkeznek be a felügyeleti funkciók helyrendszerszerepkörök támaszkodnak.  

> [!TIP]  
>  Azt javasoljuk, hogy az Intune beállítása előtt a szükséges helyrendszerszerepköröket a helyrendszerszerepkör működőképességéhez szükséges idő minimalizálásához.  

 Az Intune-előfizetés beállítása információkért lásd: [Microsoft Intune-előfizetés beállítása helyszíni mobileszközök kezeléséhez a System Center Configuration Managerben](../../mdm/get-started/set-up-intune-subscription-on-premises-mdm.md).  

##  <a name="bkmk_roles"></a>Szükséges helyrendszerszerepkörök  
 A\-helyszíni mobileszköz-kezelés az egyes a következő helyrendszerszerepkörök közül legalább egy szükséges:  

-   **Beléptetési proxypont** a beléptetési kérelmek támogatásához.  

-   **Beléptetési pont** eszközök beléptetésére.  

-   **Eszközfelügyeleti pont** házirendkézbesítésre. A helyrendszerszerepkör a felügyeleti pont szerepkör egy, a mobileszköz-kezelés lehetővé tételére konfigurált változata.  

-   **Terjesztési pont** a tartalomkézbesítésre.  

-   **Szolgáltatáskapcsolódási pont** történő kapcsolódáshoz a tűzfalon kívüli eszközök értesítésére az Intune-ban.  

 Ezen helyrendszerszerepkörök telepíthetők egyetlen helyrendszer-kiszolgálóra, illetve a szervezet igényeitől függően különböző kiszolgálókon elkülönítve futtathatók. Minden helyrendszer-kiszolgáló, a használt\-helyszíni mobileszköz-kezelés megbízható eszközökkel való kommunikáció HTTPS-végpontként kell konfigurálni. További információk: [Szükséges megbízható kommunikáció](#bkmk_trustedComs).  

 Helyrendszerszerepkörök megtervezésével kapcsolatos további információk: [Helyrendszer-kiszolgálók és helyrendszerszerepkörök megtervezése a System Center Configuration Managerhez](../../core/plan-design/hierarchy/plan-for-site-system-servers-and-site-system-roles.md).  

 További információ a szükséges helyrendszerszerepkörök hozzáadásáról: [Helyrendszerszerepkörök telepítése a helyszíni mobileszköz-felügyelethez a System Center Configuration Managerben](../../mdm/get-started/install-site-system-roles-for-on-premises-mdm.md).  

##  <a name="bkmk_trustedComs"></a>Szükséges megbízható kommunikáció  
 A\-helyszíni mobileszköz-kezelés szükséges helyrendszerszerepkörök engedélyezni kell a HTTPS-kommunikációhoz. Igényeitől függően használhatja a vállalati hitelesítésszolgáltatót (CA) a kiszolgálók és eszközök közötti megbízható kapcsolatok létrehozásához, vagy pedig egy nyilvánosan elérhető hitelesítésszolgáltatót megbízható hatóságként.  Mindkét esetben szüksége lesz egy webkiszolgáló-tanúsítvány konfigurálására az IIS-kiszolgálóval a szükséges helyrendszerszerepköröket tartalmazó helyrendszer-kiszolgálókon, valamint a hitelesítésszolgáltató által azon eszközökre telepített főtanúsítványra, amelyeket csatlakoztatni kell ezekhez a kiszolgálókhoz.  

 A vállalati hitelesítésszolgáltató megbízható kommunikációra való használatakor végezze el a következő teendőket:  

-   A webkiszolgáló-tanúsítvány sablonjának létrehozása és kiállítása a hitelesítésszolgáltatónál.  

-   Webkiszolgáló-tanúsítvány igénylése minden szükséges helyrendszerszerepkört futtató helyrendszer-kiszolgálóhoz.  

-   Az IIS szolgáltatás konfigurálása a helyrendszer-kiszolgálón a kért webkiszolgáló-tanúsítvány használatára.  

 A vállalati Active Directory tartományhoz csatlakozó eszközök esetében a vállalati hitelesítésszolgáltató főtanúsítványa már rendelkezésre áll az eszközön a megbízható kapcsolatokhoz. Ez azt jelenti, hogy a tartományhoz csatlakozó eszközök (például asztali számítógépek) automatikusan megbízhatók lesznek a helyrendszer-kiszolgálókkal való HTTPS-kapcsolatok esetében. Azonban a nem tartományhoz csatlakoztatott (általában mobil) eszközökre nincs telepítve a szükséges főtanúsítvány. Az eszközök szükséges ahhoz, hogy sikeresen kommunikálni a helyrendszer-kiszolgálók támogatása manuálisan kell telepíteni a főtanúsítványt\-helyszíni mobileszköz-kezelés.  

 Az egyes eszközök általi használathoz exportálnia kell a kiállító hitelesítésszolgáltató főtanúsítványát. A főtanúsítvány-fájl beszerzéséhez exportálhatja azt a hitelesítésszolgáltató használatával, vagy egy egyszerűbb módszerként használhatja a hitelesítésszolgáltató által kibocsátott webkiszolgáló-tanúsítványt a főtanúsítvány kibontására, majd létrehozhatja a főtanúsítvány-fájlt.   Ezt követően a főtanúsítványt kézbesíteni kell az eszközre.  Néhány példa kézbesítési módszerekre  

-   Fájlrendszer  

-   E-mail melléklet  

-   Memóriakártya  

-   Megosztott eszköz  

-   Felhőalapú tároló (például a OneDrive)  

-   Kis hatótávolságú kommunikáció (NFC) kapcsolat  

-   Vonalkódolvasó  

-   Kezdőélmény (OOBE) telepítési csomag  

 További információk: [A megbízható kommunikációhoz szükséges tanúsítványok beállítása a helyszíni mobileszközök kezeléséhez a System Center Configuration Managerben](../../mdm/get-started/set-up-certificates-on-premises-mdm.md).  

##  <a name="bkmk_enrollment"></a>Regisztrációs megfontolások  
 Az eszköz regisztrálásának engedélyezése\-helyszíni mobileszköz-kezelés, felhasználókhoz kell rendelni a regisztrálására vonatkozó engedéllyel, és az eszközeik megbízható kommunikációra a szükséges helyrendszerszerepköröket üzemeltető helyrendszer-kiszolgálók képesnek kell lennie.  

 Felhasználói regisztrálási jogosultság megadása egy regisztrációs profilt, a Configuration Manager-ügyfél beállításai beállításának lépésein is elvégezhető. A regisztrációs profil az ügyfél alapértelmezett beállításait használva leküldhető az összes felderített felhasználónak vagy beállíthatja a regisztrációs profilt az egyéni ügyfélbeállításokban, és leküldheti a beállításokat egy vagy több felhasználói gyűjteménynek.  

 Miután megadta a felhasználói regisztrálási jogosultságot, a felhasználók regisztrálhatják saját eszközeiket. A regisztráláshoz a felhasználó eszközének rendelkeznie kell a helyrendszerszerepköröket üzemeltető helyrendszer-kiszolgálókon használt webkiszolgáló-tanúsítványt kiállító hitelesítésszolgáltató főtanúsítványával.  

 A felhasználó által kezdeményezett regisztráció alternatívájaként beállíthat egy csoportos regisztrációs  csomagot, amely lehetővé teszi az eszköz felhasználói beavatkozás nélküli regisztrálását. Ezt a csomagot el lehet juttatni az eszközre az első használatra való kiosztás előtt, vagy azután, hogy az eszköz végighaladt a OOBE folyamaton.  

 A regisztráció beállításával kapcsolatos további információkért lásd:  

-   [A helyszíni mobileszköz-kezelés a System Center Configuration Managerben az eszközregisztráció beállítása](../../mdm/get-started/set-up-device-enrollment-on-premises-mdm.md)  

-   [Eszközök regisztrálása a helyszíni mobileszköz-kezelés a System Center Configuration Managerben](../../mdm/deploy-use/enroll-devices-on-premises-mdm.md)  

