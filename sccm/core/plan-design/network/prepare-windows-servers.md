---
title: "Windows Server rendszerű kiszolgálók előkészítése |} Microsoft Docs"
description: "Győződjön meg arról, hogy a számítógép megfelel-e az Előfeltételek a System Center Configuration Manager helykiszolgáló vagy helyrendszer-kiszolgáló használható."
ms.custom: na
ms.date: 2/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 2aca914f-641e-4bc8-98d4-bbf0a2a5276f
caps.latest.revision: 10
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dd102603356864add4084c6881c39bebcbd635f2
ms.openlocfilehash: 9b97dedb5d2be0bd2e47260033e6e4361467dc4e
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="prepare-windows-servers-to-support-system-center-configuration-manager"></a>Windows Server rendszerű kiszolgálók előkészítése a System Center Configuration Manager támogatására

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Használata előtt a Windows rendszerű számítógépeken egy helyrendszer-kiszolgálóként a System Center Configuration Manager, a számítógép meg kell felelnie egy helykiszolgáló vagy helyrendszer-kiszolgálóra való használat előfeltételeinek.  

-   Az Előfeltételek többek között általában egy vagy több Windows-szolgáltatások vagy szerepkörök, amelyek engedélyezve vannak a számítógépeken a Kiszolgálókezelő használatával.  

-   A metódus engedélyezéséhez a Windows-szolgáltatásokat és szerepeket eltér az operációs rendszerek között, mert tekintse meg az operációs rendszer használt beállításával kapcsolatos részletes információkat az operációs rendszer dokumentációjában.  

A cikkben szereplő információkat a Configuration Manager helyrendszerei támogatásához szükséges Windows konfigurációkat típusú áttekintése. Egyes helyrendszerszerepkörökkel konfigurációs információkért lásd: [hely és hely rendszerkövetelmények](/sccm/core/plan-design/configs/site-and-site-system-prerequisites).

##  <a name="BKMK_WinFeatures"></a>Windows-szolgáltatások és -szerepkörök  
 Windows-szolgáltatások és a számítógépen található szerepkörök beállításakor szükséges lehet, hogy a konfigurálás befejezéséhez a számítógép újraindítását. Emiatt tanácsos futtató számítógépeken adott helyrendszer-szerepkörök a Configuration Manager-hely vagy helyrendszer-kiszolgáló telepítése előtt azonosíthatja.
### <a name="features"></a>Jellemzők  
 A következő Windows-szolgáltatások szükségesek bizonyos helyrendszer-kiszolgálók, és létre kell hozni, az adott számítógépen a helyrendszerszerepkörök telepítése előtt.  

-   **.NET-keretrendszer**: Többek között  

    -   ASP.NET  
    -   HTTP-aktiválás  
    -   HTTP nélküli aktiválás  
    -   A Windows Communication Foundation (WCF) szolgáltatások  

    Különböző helyrendszerszerepkörökhöz szükséges a .NET-keretrendszer különböző verziói.  

    Mivel a .NET-keretrendszer 4.0-s és újabb verziók nem visszamenőlegesen kompatibilis 3.5-ös és korábbi verziók cserélni, amikor különböző felsorolt verziók szükséges, tervezi, hogy ugyanazon a számítógépen mindegyik verziót engedélyezi.  

-   **Háttérben futó intelligens átviteli szolgáltatás (BITS)**: Felügyeleti pontok BITS (és automatikusan kijelölt beállítások) felügyelt eszközökkel való kommunikáció támogatásához szükséges.  

-   **A BranchCache**: Terjesztési pontok is beállítható a BranchCache a BranchCache szolgáltatást használó ügyfelek támogatásához.  

-   **Az Adatdeduplikáció**: Terjesztési pontok az állítható, és igénybe vehesse az adatdeduplikáció.  

-   **Távoli különbözeti tömörítés (RDC)**: Minden olyan számítógépen, amelyen helykiszolgáló vagy terjesztési pontról a távoli asztali kapcsolat szükséges.   
    Az RDC generálja a csomagaláírásokat és végzi el az aláírás-összehasonlítást.  

### <a name="roles"></a>Szerepkörök  
 A következő Windows-szerepkörök szükségesek bizonyos funkciók, például a szoftverfrissítések és az operációs rendszer központi telepítésének támogatásához, az IIS pedig a leggyakoribb helyrendszer-szerepkörök használatához.  

 -   **Hálózati eszközök tanúsítványigénylési szolgáltatása** (az Active Directory tanúsítványszolgáltatás):  A Windows-szerepkör előfeltétele a Configuration Manager-Tanúsítványprofilok használatához.  

 -   **Webkiszolgáló (IIS)**: Beleértve a következőket:  
    -   Általános HTTP-szolgáltatások >  
        -   HTTP-átirányítás  
    -   Alkalmazásfejlesztés >  
        -   .NET-bővíthetőség  
        -   ASP.NET  
        -   ISAPI-bővítmények  
        -   ISAPI-szűrők  
    -   Felügyeleti eszközök >  
        -   Kompatibilitás az IIS 6 kezelésével  
        -   Kompatibilitás az IIS 6 metabázisával  
        -   Kompatibilitás az IIS 6 Windows Management Instrumentation (WMI)  
    -   Biztonság >  
        -   Kérelmek szűrése  
        -   Windows-hitelesítés  

 A következő helyrendszerszerepkörök a felsorolt IIS-konfigurációk közül legalább egyet használja:  
    -   Alkalmazáskatalógus webszolgáltatási pontja  
    -   Alkalmazáskatalógus weboldal-elérési pontja  
    -   Terjesztési pont  
    -   Beléptetési pont  
    -   Beléptetési proxypont  
    -   Tartalék állapotkezelő pont  
    -   Felügyeleti pont  
    -   Szoftverfrissítési pont  
    -   Állapotáttelepítési pont     

    Az IIS szolgáltatás minimálisan szükséges verziója a helykiszolgáló operációs rendszeréhez biztosított verzió.  

    Ezek az IIS-konfigurációk mellett, előfordulhat, hogy be kell állítania [IIS-kérelemszűrés a terjesztési pontok](#BKMK_IISFiltering).  

-   **Windows-telepítési szolgáltatások**: Ez a szerepkör az operációs rendszer központi telepítéséhez használatos.  
-   **A Windows Server Update Services**: Ez a szerepkör a szoftverfrissítések eljuttathatók esetén szükséges.  

##  <a name="BKMK_IISFiltering"></a>Az IIS-kérelemszűrés a terjesztési pontok  
 Alapértelmezés szerint az IIS használja a kérelmek szűrésének blokkolására néhány fájlnév-kiterjesztést és mappahelyet kizár a HTTP vagy HTTPS használatával végzett kommunikációból. A terjesztési ponton ezzel megakadályozhatja az ügyfelek, amelyek a letiltott kiterjesztéseket vagy mappahelyeket csomagokat töltsenek le.  

 Ha a csomag forrásfájljai az IIS-ben a Kérelemszűrési konfiguráció által blokkolt kiterjesztéseket, be kell állítania a kérelmek szűrésének arra. Ezt a terjesztési pontok számítógépein futó IIS-kezelő [kérelemszűrési szolgáltatásának módosításával](https://technet.microsoft.com/library/hh831621.aspx) teheti meg.  

 Emellett a következő fájlnév-kiterjesztések által a Configuration Manager használt csomagokhoz és alkalmazásokhoz. Győződjön meg arról, hogy a Kérelemszűrési konfigurációk ne blokkolják ezeket a fájlkiterjesztéseket:  

-   .PCK  
-   .PKG  
-   .STA  
-   .TAR  

A központi szoftvertelepítéssel állhatnak nevű mappa például forrásfájlokat **bin** rendelkező fájlt, vagy a **.mdb** fájlnév-kiterjesztésű.  

-   Alapértelmezés szerint nem engedélyezi az ilyen elemek hozzáférését a kérelmek szűrésének IIS-ben (**bin** rejtett szegmensként le van tiltva és **.mdb** le van tiltva, a fájlnév-kiterjesztésűeket).  

-   Ha az IIS alapértelmezett konfigurációját használja egy terjesztési ponton, a BITS szolgáltatást használó ügyfelek nem fogják tudni letölteni a terjesztési pontról a szoftvertelepítési tartalmat, és azt fogják jelezni, hogy a tartalomra várakoznak.  

-   Ahhoz, hogy az ügyfelek letölthessék a tartalmat, mindegyik vonatkozó terjesztési ponton szerkesztése **kérelemszűrés** az IIS-kezelőben a kívánt fájlkiterjesztéseket és mappákat, a csomagok és a központilag telepített alkalmazások eléréséhez.  

> [!IMPORTANT]  
>  A kérelemszűrő módosítása növelheti a számítógép támadási felületét.  
>   
>  -   A kiszolgáló szintjén végrehajtott módosítások a kiszolgáló összes webhelyére érvényesek lesznek.  
> -   Az egyes webhelyek elvégzett módosítások csak az adott webhelyre vonatkoznak.  
>   
>  A biztonsági szempontból ajánlott a Configuration Manager egy dedikált webkiszolgálón. Ha más alkalmazásokat a webkiszolgálón kell futtatnia, egyéni webhely használatára a Configuration Manager számára. További információkért lásd: [Helyrendszer-kiszolgálók webhelyei a System Center Configuration Manager alkalmazásban](../../../core/plan-design/network/websites-for-site-system-servers.md).  

## <a name="http-verbs"></a>HTTP-műveletek
**Felügyeleti pontok:** Győződjön meg arról, hogy az ügyfelek sikeresen kommunikálhatnak a felügyeleti pontot, a felügyeleti pont kiszolgálón ellenőrizze a következő HTTP-műveletek engedélyezett:  
 - GET
 - POST
 - CCM_POST
 - HEAD
 - PROPFIND

**Terjesztési pontok:** Terjesztési pontok azt igénylik, hogy engedélyezett-e a következő HTTP-műveleteket, mint:
 - GET
 - HEAD
 - PROPFIND

Kérelmek szűrése konfigurálásával kapcsolatos további információkért lásd: [konfigurálja a kérelmek szűrésének IIS-ben](https://technet.microsoft.com/library/hh831621.aspx#Verbs) könyvtárát vagy hasonló dokumentáció, és a Windows Server, a felügyeleti pontot üzemeltető verziójára vonatkozik.

