---
title: "Előfeltételek hely |} Microsoft Docs"
description: "Útmutató a Windows-számítógép konfigurálása a System Center Configuration Manager helyrendszer-kiszolgálóként."
ms.custom: na
ms.date: 1/17/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1392797b-76cb-46b4-a3e4-8f349ccaa078
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 42549b98dd7f418cc3f4543198aaeb90ea8a3efd
ms.openlocfilehash: 0b1d2d619d6cdaf36cc22ef461ea1505b5cacc41
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="site-and-site-system-prerequisites-for-system-center-configuration-manager"></a>Hely és hely rendszer Előfeltételek a System Center Configuration Managerhez

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


 Windows-alapú számítógépek számára szükséges specifikus konfigurációk támogatása a System Center Configuration Manager helyrendszer-kiszolgálóként.  


 Az összes olyan terméket például a Windows Server Update Services (WSUS) a szoftverfrissítési pontot, kell a termék dokumentációjában talál további Előfeltételek azonosításához és, hogy a termék használatára vonatkozó korlátozások. Ide tartoznak a csak konfigurációkat közvetlenül a Configuration Managerrel történő használathoz.   

> [!NOTE]  
>  2016. január, a támogatási lejárt, a .NET-keretrendszer 4.0-s, 4.5-ös és 4.5.1-es verzióját. További információ: [A Microsoft .NET keretrendszer támogatási életciklusra vonatkozó szabályzata – GYIK](https://support.microsoft.com/gp/framework_faq?WT.mc_id=azurebg_email_Trans_943_NET452_Update) a support.microsoft.com címen.  

## <a name="bkmk_generalprerewq"></a>Általános helyrendszer-kiszolgáló követelményei és korlátozásai
**Minden helyrendszer-kiszolgálókat a következők vonatkoznak:**

-   Minden helyrendszer egy 64 bites operációs rendszert kell használnia. Az egyetlen kivételt a rendszer a terjesztési pont helyrendszer-szerepkör, amely egyes 32 bites operációs rendszerek telepítése.  

-   Beléptetésihely-rendszerek nem támogatottak az operációs rendszerek Server Core telepítéseken. Kivétel ez alól az, hogy a Server Core-telepítések támogatottak-e a terjesztési pont helyrendszerszerepkörhöz, PXE és csoportos küldés támogatása nélkül.  

-   Helyrendszer-kiszolgáló telepítése után nem támogatott módosítása:  

    -   A helyrendszer számítógépén a tartomány tartománynév (más néven a **tartomány átnevezése**).  

    -   A számítógép tartományi tagságát.  

    -   A számítógép nevét.  

  Meg kell változtatnia ezek egyikét sem, ha kell, először a helyrendszer-szerepkör eltávolítása a számítógépről, és telepítse újra a szerepkört, a módosítás befejezése után. Ha ez érinti a helykiszolgáló számítógépén, akkor a hely eltávolítása és majd telepítse újra a helyet, a módosítás befejezése után.  

-   Helyrendszerszerepkörök nem támogatottak a Windows Server-fürt példányokon. Az egyetlen kivételt a rendszer a Helyadatbázis-kiszolgálón.  

-   Indítási típus módosítása vagy a "Bejelentkezés" beállításait a Configuration Manager szolgáltatás nem támogatott. Ha ezt teszi, hogy megakadályozhatja, hogy fontos szolgáltatások nem fognak megfelelően futni.  

##  <a name="bkmk_2012Prereq"></a>Windows Server 2012 és annál újabb operációs rendszereken előfeltételei  
###  <a name="bkmk_2012sspreq"></a>Helykiszolgáló: központi adminisztrációs helyen és elsődleges helyen  
  **Windows kiszolgálói szerepkörök és szolgáltatások:**  

-   .NET-keretrendszer 3.5 SP1 (vagy újabb)  

-   .NET-keretrendszer 4.5.2  

-   Távoli különbözeti tömörítés  

**Windows ADK:**  

-   Ahhoz, hogy telepíteni vagy frissíteni, a központi adminisztrációs hely vagy elsődleges hely, telepítenie kell a Windows Assessment and Deployment Kit (ADK), amely a Configuration Manager verziója most telepítése vagy frissítése szükséges verziója.  

    -   A Configuration Manager 1511-es verziója szükséges a Windows 10 RTM (10.0.10240) a Windows ADK-verziót.  

-   További információ erről a követelményről: [operációs rendszer központi telepítésének infrastrukturális követelményei](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment).  

**Visual C++ terjeszthető csomag:**  

-   Configuration Manager telepíti a Microsoft Visual C++ 2013 újraterjeszthető csomagot minden helykiszolgálót telepítő számítógépre.  

-   A központi adminisztrációs helyek és az elsődleges helyeken szükséges a vonatkozó újraterjeszthető fájl x86 és x64 verziója.  

###  <a name="bkmk_2012secpreq"></a>Helykiszolgáló: másodlagos helyen  
**Windows kiszolgálói szerepkörök és szolgáltatások:**  

-   .NET-keretrendszer 3.5 SP1 (vagy újabb)  

-   .NET-keretrendszer 4.5.2  

-   Távoli különbözeti tömörítés  

**Visual C++ terjeszthető csomag:**  

-   Configuration Manager telepíti a Microsoft Visual C++ 2013 újraterjeszthető csomagot minden helykiszolgálót telepítő számítógépre.  

-   A másodlagos helyek csak a x64 verziója.  

**Alapértelmezett helyrendszerszerepkörök:**  

-   Alapértelmezés szerint egy másodlagos helyet telepít egy **felügyeleti pont** és egy **terjesztési pont**.  

-   Győződjön meg arról, hogy a másodlagos helykiszolgáló megfelel-e ezen helyrendszerszerepkörök előfeltételeit.  

###  <a name="bkmk_2012dbpreq"></a>Adatbázis-kiszolgáló  
**Távoli beállításszolgáltatás:**  

-   A Configuration Manager-hely telepítésekor engedélyeznie kell a távoli beállításjegyzék szolgáltatás a számítógépen, amely a helyadatbázist fogja tartalmazni.  

**SQL Server:**  

-   A központi adminisztrációs hely vagy elsődleges hely telepítése előtt telepítenie kell a helyadatbázist tároló SQL Server támogatott verziója.  

-   A másodlagos hely telepítése előtt telepítheti az SQL Server támogatott verzióját.  

-   Ha úgy dönt, hogy, hogy a Configuration Manager telepíti az SQL Server Expresst a másodlagos hely telepítésének részeként, győződjön meg arról, hogy a számítógép megfelel-e az SQL Server Express futtatására vonatkozó követelményeknek.  

###  <a name="bkmk_2012smsprovpreq"></a>SMS-szolgáltató kiszolgáló  
**Windows ADK:**  

-   A számítógépen, ahová az SMS-szolgáltató példányát telepíti, amelyhez a Configuration Manager verziója most telepítése vagy frissítése a Windows ADK szükséges verziójának kell rendelkeznie.  

    -   A Configuration Manager 1511-es verziója szükséges a Windows 10 RTM (10.0.10240) a Windows ADK-verziót.  

-   További információ erről a követelményről: [operációs rendszer központi telepítésének infrastrukturális követelményei](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment).  

###  <a name="bkmk_2012acwspreq"></a>Az Alkalmazáskatalógus weboldal-elérési pontja  
**Windows kiszolgálói szerepkörök és szolgáltatások:**  

-   .NET-keretrendszer 3.5 SP1 (vagy újabb)  

-   .NET-keretrendszer 4.5.2-es:  

    -   ASP.NET 4.5  

**IIS-konfiguráció:**  

-   Általános HTTP-szolgáltatások:  

    -   Alapértelmezett dokumentum  

    -   Statikus tartalom  

-   Alkalmazásfejlesztés:  

    -   ASP.NET 3.5 (és automatikusan kijelölt beállítások)  

    -   ASP.NET 4.5 (és automatikusan kijelölt beállítások)  

    -   .NET-bővíthetőség 3.5  

    -   .NET-bővíthetőség 4.5  

-   Biztonsági:  

    -   Windows-hitelesítés  

-   Kompatibilitás az IIS 6 kezelésével:  

    -   Kompatibilitás az IIS 6 metabázisával  

###  <a name="bkmk_2012ACwsitepreq"></a>Az Alkalmazáskatalógus webszolgáltatási pontja  
**Windows kiszolgálói szerepkörök és szolgáltatások:**  

-   .NET-keretrendszer 3.5 SP1 (vagy újabb)  

-   .NET-keretrendszer 4.5.2-es:  

    -   ASP.NET 4.5:  

        -   HTTP-aktiválás (és automatikusan kijelölt beállítások)  

**IIS-konfiguráció:**  

-   Általános HTTP-szolgáltatások:  

    -   Alapértelmezett dokumentum  

-   Kompatibilitás az IIS 6 kezelésével:  

    -   Kompatibilitás az IIS 6 metabázisával  

-   Alkalmazásfejlesztés:  

    -   ASP.NET 3.5 (és automatikusan kijelölt beállítások)  

    -   .NET-bővíthetőség 3.5  

    -   ASP.NET 4.5 (és automatikusan kijelölt beállítások)  

    -   .NET-bővíthetőség 4.5  

**A számítógép memóriája:**  

-   A számítógép, amelyen a helyrendszerszerepkör rendelkeznie kell legalább 5 %-a számítógép elérhető memóriájából ahhoz, hogy a helyrendszer-szerepkör a kérelmek feldolgozását.  

-   Ha a helyrendszerszerepkör közösen elhelyezve egy másik, ugyanilyen igényű helyrendszerszerepkörrel helyrendszer-szerepkör, az a számítógép memóriakövetelménye nem növelhető, de marad a minimum 5 %-os.  

###  <a name="bkmk_2012AIpreq"></a>Eszközintelligencia szinkronizációs pontja  
**Windows kiszolgálói szerepkörök és szolgáltatások:**  

-   .NET-keretrendszer 4.5.2  

###  <a name="bkmk_2012crppreq"></a>Tanúsítványregisztrációs pont  
**Windows kiszolgálói szerepkörök és szolgáltatások:**  

-   .NET-keretrendszer 4.5.2-es:  

    -   HTTP-aktiválás  

**IIS-konfiguráció:**  

-   Alkalmazásfejlesztés:  

    -   ASP.NET 3.5 (és automatikusan kijelölt beállítások)  

    -   ASP.NET 4.5 (és automatikusan kijelölt beállítások)  

-   Kompatibilitás az IIS 6 kezelésével:  

    -   Kompatibilitás az IIS 6 metabázisával  

    -   IIS 6 WMI kompatibilitási mód  

###  <a name="bkmk_2012dppreq"></a>Terjesztési pont  
**Windows kiszolgálói szerepkörök és szolgáltatások:**  

-   Távoli különbözeti tömörítés  

**IIS-konfiguráció:**  

-   Alkalmazásfejlesztés:  

    -   ISAPI-bővítmények  

-   Biztonsági:  

    -   Windows-hitelesítés  

-   Kompatibilitás az IIS 6 kezelésével:  

    -   Kompatibilitás az IIS 6 metabázisával  

    -   IIS 6 WMI kompatibilitási mód  

**PowerShell:**  

-   A Windows Server 2012 vagy újabb, a PowerShell 3.0 vagy 4.0 szükség van a terjesztési pont telepítése előtt.  

**Visual C++ terjeszthető csomag:**  

-   Configuration Manager telepíti a Microsoft Visual C++ 2013 újraterjeszthető csomagot egy terjesztési pontot üzemeltető minden számítógépen.  

-   A telepített verzió attól függ, hogy a számítógép-platform (x86 vagy x64).  

**A Microsoft Azure:**  

-   A Microsoft Azure-ban egy felhőalapú szolgáltatás használatával futtatni egy terjesztési pontot.  

**PXE vagy csoportos küldést támogató:**  

-   Telepítse és konfigurálja a Windows-telepítési szolgáltatások (WDS) Windows kiszolgálói szerepkör.  

    > [!NOTE]  
    >  A WDS automatikusan telepítve és konfigurálva PXE vagy csoportos küldést támogató Windows Server 2012 vagy újabb verziót futtató kiszolgálóra a terjesztési pont konfigurálásakor.  

> [!NOTE]  
> A terjesztési pont helyrendszer-szerepkör nem igényel a háttérben futó intelligens átviteli szolgáltatás (BITS). BITS konfigurálva van a terjesztési pont számítógépén, ha a BITS a terjesztési pont számítógépén nem használják a tartalmak letöltésének megkönnyítésére BITS szolgáltatást használó ügyfeleknek.  

###  <a name="bkmk_2012EPPpreq"></a>Endpoint Protection-pont  
**Windows kiszolgálói szerepkörök és szolgáltatások:**  

-   .NET-keretrendszer 3.5 SP1 (vagy újabb)  

###  <a name="bkmk_2012Enrollpreq"></a>A beléptetési pont  
**Windows kiszolgálói szerepkörök és szolgáltatások:**  

-   .NET-keretrendszer 3.5-ös (vagy újabb)  

-   .NET-keretrendszer 4.5.2-es:  

     E helyrendszerszerepkör telepítésekor a Configuration Manager automatikusan telepíti a .NET-keretrendszer 4.5.2-es verzióját. A telepítés újraindítás függőben állapotba állíthatja a kiszolgálót. Ha újraindítás függőben a .NET-keretrendszer .NET-alkalmazások sikertelen lehet, amíg a kiszolgáló újraindul, és a telepítés befejeződése után.  

    -   HTTP-aktiválás (és automatikusan kijelölt beállítások)  

    -   ASP.NET 4.5  


**IIS-konfiguráció:**  

-   Általános HTTP-szolgáltatások:  

    -   Alapértelmezett dokumentum  

-   Alkalmazásfejlesztés:  

    -   ASP.NET 3.5 (és automatikusan kijelölt beállítások)  

    -   .NET-bővíthetőség 3.5  

    -   ASP.NET 4.5 (és automatikusan kijelölt beállítások)  

    -   .NET-bővíthetőség 4.5  

-   Kompatibilitás az IIS 6 kezelésével:  

    -   Kompatibilitás az IIS 6 metabázisával  

**A számítógép memóriája:**  

-   A számítógép, amelyen a helyrendszerszerepkör rendelkeznie kell legalább 5 %-a számítógép elérhető memóriájából ahhoz, hogy a helyrendszer-szerepkör a kérelmek feldolgozását.  

-   Ha a helyrendszerszerepkör közösen elhelyezve egy másik, ugyanilyen igényű helyrendszerszerepkörrel helyrendszer-szerepkör, az a számítógép memóriakövetelménye nem növelhető, de marad a minimum 5 %-os.  

###  <a name="bkmk_2012EnrollProxpreq"></a>Beléptetési proxypont  
**Windows kiszolgálói szerepkörök és szolgáltatások:**  

-   .NET-keretrendszer 3.5-ös (vagy újabb)  

-   .NET-keretrendszer 4.5.2  

     E helyrendszerszerepkör telepítésekor a Configuration Manager automatikusan telepíti a .NET-keretrendszer 4.5.2-es verzióját. A telepítés újraindítás függőben állapotba állíthatja a kiszolgálót. Ha újraindítás függőben a .NET-keretrendszer .NET-alkalmazások sikertelen lehet, amíg a kiszolgáló újraindul, és a telepítés befejezése után.  

**IIS-konfiguráció:**  

-   Általános HTTP-szolgáltatások:  

    -   Alapértelmezett dokumentum  

    -   Statikus tartalom  

-   Alkalmazásfejlesztés:  

    -   ASP.NET 3.5 (és automatikusan kijelölt beállítások)  

    -   ASP.NET 4.5 (és automatikusan kijelölt beállítások)  

    -   .NET-bővíthetőség 3.5  

    -   .NET-bővíthetőség 4.5  

-   Biztonsági:  

    -   Windows-hitelesítés  

-   Kompatibilitás az IIS 6 kezelésével:  

    -   Kompatibilitás az IIS 6 metabázisával  

**A számítógép memóriája:**  

-   A számítógép, amelyen a helyrendszerszerepkör rendelkeznie kell legalább 5 %-a számítógép elérhető memóriájából ahhoz, hogy a helyrendszer-szerepkör a kérelmek feldolgozását.  

-   Ha a helyrendszerszerepkör közösen elhelyezve egy másik, ugyanilyen igényű helyrendszerszerepkörrel helyrendszer-szerepkör, az a számítógép memóriakövetelménye nem növelhető, de marad a minimum 5 %-os.  

###  <a name="bkmk_2012FSPpreq"></a>Tartalék állapotkezelő pont  
Az alapértelmezett IIS-konfiguráció szükség az alábbi kiegészítésekkel:  

-   Kompatibilitás az IIS 6 kezelésével:  

    -   Kompatibilitás az IIS 6 metabázisával  

###  <a name="bkmk_2012MPpreq"></a>Felügyeleti pont  
**Windows kiszolgálói szerepkörök és szolgáltatások:**  

-   .NET-keretrendszer 4.5.2  

-   BITS Server Extensions (és automatikusan kijelölt beállítások) vagy a háttérben futó intelligens átviteli szolgáltatás (BITS) (és automatikusan kijelölt beállítások)  

**IIS-konfiguráció:**  

-   Alkalmazásfejlesztés:  

    -   ISAPI-bővítmények  

-   Biztonsági:  

    -   Windows-hitelesítés  

-   Kompatibilitás az IIS 6 kezelésével:  

    -   Kompatibilitás az IIS 6 metabázisával  

    -   IIS 6 WMI kompatibilitási mód  

###  <a name="bkmk_2012RSpoint"></a>Jelentéskészítési szolgáltatási pont  
**Windows kiszolgálói szerepkörök és szolgáltatások:**  

-   .NET-keretrendszer 4.5.2  

**SQL Server Reporting Services:**  

-   Telepítésekor, és állítsa be az SQL Server Reporting Services támogatásához, mielőtt telepíti a jelentéskészítési szolgáltatási pont az SQL Server legalább egy példányát.  

-   A használt SQL Server Reporting Services példány lehet a helyadatbázishoz használt példánnyal.  

-   Ezenkívül a használt példány megosztható más System Center-termékekkel, mindaddig, amíg a többi System Center-terméknél nincs korlátozva az SQL Server példány megosztása.  

###  <a name="bkmk_SCPpreq"></a>Szolgáltatáskapcsolódási pont  
**Windows kiszolgálói szerepkörök és szolgáltatások:**  

-   .NET-keretrendszer 4.5.2  

     E helyrendszerszerepkör telepítésekor a Configuration Manager automatikusan telepíti a .NET-keretrendszer 4.5.2-es verzióját. A telepítés újraindítás függőben állapotba állíthatja a kiszolgálót. Ha újraindítás függőben a .NET-keretrendszer .NET-alkalmazások sikertelen lehet, amíg a kiszolgáló újraindul, és a telepítés befejeződése után.  

**Visual C++ terjeszthető csomag:**  

-   Configuration Manager telepíti a Microsoft Visual C++ 2013 újraterjeszthető csomagot egy terjesztési pontot üzemeltető minden számítógépen.  

-   A helyrendszer-szerepkör a x64 szükséges verziója.  

###  <a name="bkmk_2012SUPpreq"></a>Szoftverfrissítési pont  
**Windows kiszolgálói szerepkörök és szolgáltatások:**  

-   .NET-keretrendszer 3.5 SP1 (vagy újabb)  

-   .NET-keretrendszer 4.5.2  

Az alapértelmezett IIS-konfigurációt megadása kötelező.

**A Windows Server Update Services:**  

-   Telepítenie kell a Windows kiszolgálói szerepkör a Windows Server Update Services egy számítógépen a szoftverfrissítési pont telepítése előtt.  

-   További információk: [Szoftverfrissítések tervezése a System Center Configuration Managerben](../../../sum/plan-design/plan-for-software-updates.md).  

### <a name="state-migration-point"></a>állapotáttelepítési pont  
Az alapértelmezett IIS-konfigurációt megadása kötelező.  

##  <a name="bkmk_2008"></a>Windows Server 2008 R2 és Windows Server 2008 előfeltételei  
Windows Server 2008 és Windows Server 2008 R2 most meghosszabbított támogatás és nem alapvető technikai támogatással keretében támogatjuk a [Microsoft terméktámogatási ciklusait](https://support.microsoft.com/lifecycle). A Configuration Manager helyrendszer-kiszolgálóként a fenti operációs rendszerek jövőbeli támogatásával kapcsolatos további információkért lásd: [eltávolítva és elavult funkciók a System Center Configuration Manager](../../../core/plan-design/changes/removed-and-deprecated-features.md).  

**Minden .NET-keretrendszer követelményei a következők vonatkoznak:**  

-   Telepítse a .NET-keretrendszer a helyrendszerszerepkörök telepítése előtt. Például tekintse meg a [Microsoft .NET-keretrendszer 4 (önálló telepítő)](http://go.microsoft.com/fwlink/p/?LinkId=193048). A .NET-keretrendszer 4 Ügyfélprofilja nem elegendő ehhez a követelményhez.  

**Az alábbiak érvényesek az összes Windows Communication Foundation (WCF) kapcsolatos aktiválási követelményekre vonatkoznak:**  

-   WCF aktiválását konfigurálhatja a helyrendszer-kiszolgálón a .NET Framework Windows szolgáltatás részeként. Például a Windows Server 2008 R2, futtassa a **szolgáltatások hozzáadása varázsló** további szolgáltatások telepítése a kiszolgálón. A a **szolgáltatások kiválasztása** ablaktáblában bontsa ki a **NET Framework 3.5.1 szolgáltatások**, bontsa ki a **WCF-aktiválás**, és ezután jelölje be mind a **HTTP-aktiválás** és **HTTP nélküli aktiválás** ezen funkciók engedélyezéséhez.  

###  <a name="bkmk_2008sspreq"></a>Helykiszolgáló: központi adminisztrációs helyen és elsődleges helyen  
**.NET-keretrendszer:**  

-   .NET-keretrendszer 3.5 SP1 (vagy újabb)  

-   .NET-keretrendszer 4.5.2  

**Windows-szolgáltatás:**  

-   Távoli különbözeti tömörítés  

**Windows ADK:**  

-   Ahhoz, hogy telepíteni vagy frissíteni, a központi adminisztrációs hely vagy elsődleges hely, telepítenie kell, amely a Configuration Manager verziója most telepítése vagy frissítése a szükséges Windows ADK-verziót.  

    -   A Configuration Manager 1511-es verziója szükséges a Windows 10 RTM (10.0.10240) a Windows ADK-verziót.  

-   További információ erről a követelményről: [operációs rendszer központi telepítésének infrastrukturális követelményei](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment).  

**Visual C++ terjeszthető csomag:**  

-   Configuration Manager telepíti a Microsoft Visual C++ 2013 újraterjeszthető csomagot minden helykiszolgálót telepítő számítógépre.  

-   A központi adminisztrációs helyek és az elsődleges helyeken szükséges a vonatkozó újraterjeszthető fájl x86 és x64 verziója.  

###  <a name="bkmk_2008secpreq"></a>Helykiszolgáló: másodlagos helyen  
**.NET-keretrendszer:**  

-   .NET-keretrendszer 3.5 SP1 (vagy újabb)  

-   .NET-keretrendszer 4.5.2  

**Visual C++ terjeszthető csomag:**  

-   Configuration Manager telepíti a Microsoft Visual C++ 2013 újraterjeszthető csomagot minden helykiszolgálót telepítő számítógépre.  

-   A másodlagos helyek csak a x64 verziója.  

**Alapértelmezett helyrendszerszerepkörök:**  

-   Alapértelmezés szerint egy másodlagos helyet telepít egy **felügyeleti pont** és egy **terjesztési pont**.  

-   Győződjön meg arról, hogy a másodlagos helykiszolgáló megfelel-e ezen helyrendszerszerepkörök előfeltételeit.  

###  <a name="bkmk_2008dbpreq"></a>Adatbázis-kiszolgáló  
**Távoli beállításszolgáltatás:**  

-   A Configuration Manager-hely telepítésekor engedélyeznie kell a távoli beállításjegyzék szolgáltatás a számítógépen, amely a helyadatbázist fogja tartalmazni.  

**SQL Server:**  

-   A központi adminisztrációs hely vagy elsődleges hely telepítése előtt telepítenie kell a helyadatbázist tároló SQL Server támogatott verziója.  

-   A másodlagos hely telepítése előtt telepítheti az SQL Server támogatott verzióját.  

-   Ha úgy dönt, hogy, hogy a Configuration Manager telepíti az SQL Server Expresst a másodlagos hely telepítésének részeként, győződjön meg arról, hogy a számítógép megfelel-e az SQL Server Express futtatására vonatkozó követelményeknek.  

###  <a name="bkmk_2008smsprovpreq"></a>SMS-szolgáltató kiszolgáló  
**Windows ADK:**  

-   A számítógépen, ahová az SMS-szolgáltató példányát telepíti, amelyhez a Configuration Manager verziója most telepítése vagy frissítése a Windows ADK szükséges verziójának kell rendelkeznie.  

    -   A Configuration Manager 1511-es verziója szükséges a Windows 10 RTM (10.0.10240) a Windows ADK-verziót.  

-   További információ erről a követelményről: [operációs rendszer központi telepítésének infrastrukturális követelményei](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment).  

###  <a name="bkmk_2008acwspreq"></a>Az Alkalmazáskatalógus weboldal-elérési pontja  
**.NET-keretrendszer:**  

-   .NET-keretrendszer 4.5.2  

**IIS-konfiguráció:**

Az alapértelmezett IIS-konfiguráció szükség az alábbi kiegészítésekkel:  

-   Általános HTTP-szolgáltatások:  

    -   Statikus tartalom  

    -   Alapértelmezett dokumentum  

-   Alkalmazásfejlesztés:  

    -   ASP.NET (és automatikusan kijelölt beállítások)  

         Egyes esetekben, amikor IIS telepítve, vagy a .NET-keretrendszer 4.5.2-es verziójának telepítése után konfigurálni például explicit módon engedélyeznie kell az ASP.NET 4.5-ös verzióját. Például egy 64 bites számítógépen, amelyen a .NET-keretrendszer 4.0.30319-es, a következő parancsot: **%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -i-engedélyezése**  

-   Biztonsági:  

    -   Windows-hitelesítés  

-   Kompatibilitás az IIS 6 kezelésével:  

    -   Kompatibilitás az IIS 6 metabázisával  

###  <a name="bkmk_2008ACwsitepreq"></a>Az Alkalmazáskatalógus webszolgáltatási pontja  
**.NET-keretrendszer:**  

-   .NET-keretrendszer 3.5 SP1 (vagy újabb)  

-   .NET-keretrendszer 4.5.2  

**A Windows Communication Foundation (WCF) aktiválása:**  

-   HTTP-aktiválás  

-   HTTP nélküli aktiválás  

**IIS-konfiguráció:**

Az alapértelmezett IIS-konfiguráció szükség az alábbi kiegészítésekkel:  

-   Alkalmazásfejlesztés:  

    -   ASP.NET (és automatikusan kijelölt beállítások)  

         Egyes esetekben, amikor IIS telepítve, vagy a .NET-keretrendszer 4.5.2-es verziójának telepítése után konfigurálni például explicit módon engedélyeznie kell az ASP.NET 4.5-ös verzióját. Például egy 64 bites számítógépen, amelyen a .NET-keretrendszer 4.0.30319-es, a következő parancsot: **%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -i-engedélyezése**  

-   Kompatibilitás az IIS 6 kezelésével:  

    -   Kompatibilitás az IIS 6 metabázisával  

**A számítógép memóriája:**  

-   A számítógép, amelyen a helyrendszerszerepkör rendelkeznie kell legalább 5 %-a számítógép elérhető memóriájából ahhoz, hogy a helyrendszer-szerepkör a kérelmek feldolgozását.  

-   Ha a helyrendszerszerepkör közösen elhelyezve egy másik, ugyanilyen igényű helyrendszerszerepkörrel helyrendszer-szerepkör, az a számítógép memóriakövetelménye nem növelhető, de marad a minimum 5 %-os.  

###  <a name="bkmk_2008AIpreq"></a>Eszközintelligencia szinkronizációs pontja  
**.NET-keretrendszer:**  

-   .NET-keretrendszer 4.5.2  

###  <a name="bkmk_2008crppreq"></a>Tanúsítványregisztrációs pont  
**.NET-keretrendszer:**  

-   .NET-keretrendszer 4.5.2  

-   HTTP-aktiválás  

**IIS-konfiguráció:**

Az alapértelmezett IIS-konfiguráció szükség az alábbi kiegészítésekkel:  

-   Kompatibilitás az IIS 6 kezelésével:  

    -   Kompatibilitás az IIS 6 metabázisával  

    -   IIS 6 WMI kompatibilitási mód  

###  <a name="bkmk_2008dppreq"></a>Terjesztési pont  
**IIS-konfiguráció:**

Az alapértelmezett IIS-konfigurációt vagy egy egyéni konfigurációt is használhat. Egyéni IIS-konfigurációt használni, engedélyeznie kell az IIS a következő beállításokat:  

-   Alkalmazásfejlesztés:  

    -   ISAPI-bővítmények  

-   Biztonsági:  

    -   Windows-hitelesítés  

-   Kompatibilitás az IIS 6 kezelésével:  

    -   Kompatibilitás az IIS 6 metabázisával  

    -   IIS 6 WMI kompatibilitási mód  

Egyéni IIS-konfiguráció használatakor eltávolíthatja a nem szükséges, például a következő beállításokat:  

-   Általános HTTP-szolgáltatások:  

    -   HTTP-átirányítás  

-   Az IIS-kezelés parancsfájljai és eszközei  

**Windows-szolgáltatás:**  

-   Távoli különbözeti tömörítés  

**Visual C++ terjeszthető csomag:**  

-   Configuration Manager telepíti a Microsoft Visual C++ 2013 újraterjeszthető csomagot egy terjesztési pontot üzemeltető minden számítógépen.  

-   A telepített verzió attól függ, hogy a számítógép-platform (x86 vagy x64).  

**A Microsoft Azure:**  

-   Az Azure-ban egy felhőalapú szolgáltatás használatával futtatni egy terjesztési pontot.  

**PXE vagy csoportos küldést támogató:**  

-   Telepítse és konfigurálja a Windows-telepítési szolgáltatások (WDS) Windows kiszolgálói szerepkör.  

    > [!NOTE]  
    >  A WDS automatikusan telepítve és konfigurálva PXE vagy csoportos küldést támogató Windows Server 2012 vagy újabb verziót futtató kiszolgálóra a terjesztési pont konfigurálásakor.  

> [!NOTE]  
> A terjesztési pont helyrendszer-szerepkör nem igényel a háttérben futó intelligens átviteli szolgáltatás (BITS). BITS konfigurálva van a terjesztési pont számítógépén, ha a BITS a terjesztési pont számítógépén nem használják a tartalmak letöltésének megkönnyítésére BITS szolgáltatást használó ügyfeleknek.  


###  <a name="bkmk_2008EPPpreq"></a>Endpoint Protection-pont  
**.NET-keretrendszer:**  

-   .NET-keretrendszer 3.5 SP1 (vagy újabb)  

###  <a name="bkmk_2008Enrollpreq"></a>A beléptetési pont  
**.NET-keretrendszer:**  

-   .NET-keretrendszer 4.5.2  

     A helyrendszer-szerepkör telepítésekor, ha a kiszolgáló még nincs telepítve a .NET-keretrendszer támogatott verziója, a Configuration Manager automatikusan telepíti a .NET-keretrendszer 4.5.2-es verzióját. A telepítés újraindítás függőben állapotba állíthatja a kiszolgálót. Ha újraindítás függőben a .NET-keretrendszer .NET-alkalmazások sikertelen lehet, amíg a kiszolgáló újraindul, és a telepítés befejeződése után.  

**A Windows Communication Foundation (WCF) aktiválása:**  

-   HTTP-aktiválás  

-   HTTP nélküli aktiválás  

**IIS-konfiguráció:**

Az alapértelmezett IIS-konfiguráció szükség az alábbi kiegészítésekkel:  

-   Alkalmazásfejlesztés:  

    -   ASP.NET (és automatikusan kijelölt beállítások)  

         Egyes esetekben, amikor IIS telepítve, vagy a .NET-keretrendszer 4.5.2-es verziójának telepítése után konfigurálni például explicit módon engedélyeznie kell az ASP.NET 4.5-ös verzióját. Például egy 64 bites számítógépen, amelyen a .NET-keretrendszer 4.0.30319-es, a következő parancsot: **%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -i-engedélyezése**  

**A számítógép memóriája:**  

-   A számítógép, amelyen a helyrendszerszerepkör rendelkeznie kell legalább 5 %-a számítógép elérhető memóriájából ahhoz, hogy a helyrendszer-szerepkör a kérelmek feldolgozását.  

-   Ha a helyrendszerszerepkör közösen elhelyezve egy másik, ugyanilyen igényű helyrendszerszerepkörrel helyrendszer-szerepkör, az a számítógép memóriakövetelménye nem növelhető, de marad a minimum 5 %-os.  

###  <a name="bkmk_2008EnrollProxpreq"></a>Beléptetési proxypont  
**.NET-keretrendszer:**  

-   .NET-keretrendszer 4.5.2  

     A helyrendszer-szerepkör telepítésekor, ha a kiszolgáló még nincs telepítve a .NET-keretrendszer támogatott verziója, a Configuration Manager automatikusan telepíti a .NET-keretrendszer 4.5.2-es verzióját. A telepítés újraindítás függőben állapotba állíthatja a kiszolgálót. Ha újraindítás függőben a .NET-keretrendszer .NET-alkalmazások sikertelen lehet, amíg a kiszolgáló újraindul, és a telepítés befejeződése után.  

**A Windows Communication Foundation (WCF) aktiválása:**  

-   HTTP-aktiválás  

-   HTTP nélküli aktiválás  

**IIS-konfiguráció:**

Az alapértelmezett IIS-konfiguráció szükség az alábbi kiegészítésekkel:  

-   Alkalmazásfejlesztés:  

    -   ASP.NET (és automatikusan kijelölt beállítások)  

         Egyes esetekben, amikor IIS telepítve, vagy a .NET-keretrendszer 4.5.2-es verziójának telepítése után konfigurálni például explicit módon engedélyeznie kell az ASP.NET 4.5-ös verzióját. Például egy 64 bites számítógépen, amelyen a .NET-keretrendszer 4.0.30319-es, a következő parancsot: **%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -i-engedélyezése**  

**A számítógép memóriája:**  

-   A számítógép, amelyen a helyrendszerszerepkör rendelkeznie kell legalább 5 %-a számítógép elérhető memóriájából ahhoz, hogy a helyrendszer-szerepkör a kérelmek feldolgozását.  

-   Ha a helyrendszerszerepkör közösen elhelyezve egy másik, ugyanilyen igényű helyrendszerszerepkörrel helyrendszer-szerepkör, az a számítógép memóriakövetelménye nem növelhető, de marad a minimum 5 %-os.  

###  <a name="bkmk_2008FSPpreq"></a>Tartalék állapotkezelő pont  
**IIS-konfiguráció:**

Az alapértelmezett IIS-konfiguráció szükség az alábbi kiegészítésekkel:  

-   Kompatibilitás az IIS 6 kezelésével:  

    -   Kompatibilitás az IIS 6 metabázisával  

###  <a name="bkmk_2008MPpreq"></a>Felügyeleti pont  
**.NET-keretrendszer:**  

-   .NET-keretrendszer 4.5.2  

**IIS-konfiguráció:**

Az alapértelmezett IIS-konfigurációt vagy egy egyéni konfigurációt is használhat. Minden olyan felügyeleti pont engedélyezése a mobileszközök támogatásához a további IIS-konfigurációt igényli az ASP.NET (és automatikusan kijelölt beállításokkal).

Egyes esetekben, amikor IIS telepítve, vagy a .NET-keretrendszer 4.5.2-es verziójának telepítése után konfigurálni például explicit módon engedélyeznie kell az ASP.NET 4.5-ös verzióját. Például egy 64 bites számítógépen, amelyen a .NET-keretrendszer 4.0.30319-es, a következő parancsot: **%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -i-engedélyezése**  


Egyéni IIS-konfigurációt használni, engedélyeznie kell az IIS a következő beállításokat:  

-   Alkalmazásfejlesztés:  

    -   ISAPI-bővítmények  

-   Biztonsági:  

    -   Windows-hitelesítés  

-   Kompatibilitás az IIS 6 kezelésével:  

    -   Kompatibilitás az IIS 6 metabázisával  

    -   IIS 6 WMI kompatibilitási mód  


Egyéni IIS-konfiguráció használatakor eltávolíthatja a nem szükséges, például a következő beállításokat:  

-   Általános HTTP-szolgáltatások:  

    -   HTTP-átirányítás  

-   Az IIS-kezelés parancsfájljai és eszközei  

**Windows-szolgáltatás:**  

-   BITS Server Extensions (és automatikusan kijelölt beállítások), vagy a háttérben futó intelligens átviteli szolgáltatás (BITS) (és automatikusan kijelölt beállítások)  

###  <a name="bkmk_2008RSpoint"></a>Jelentéskészítési szolgáltatási pont  
**.NET-keretrendszer:**  

-   .NET-keretrendszer 4.5.2  

**SQL Server Reporting Services:**  

-   Telepítésekor, és állítsa be az SQL Server Reporting Services támogatásához, mielőtt telepíti a jelentéskészítési szolgáltatási pont az SQL Server legalább egy példányát.  

-   A használt SQL Server Reporting Services példány lehet a helyadatbázishoz használt példánnyal.  

-   Ezenkívül a használt példány megosztható más System Center-termékekkel, mindaddig, amíg a többi System Center-terméknél nincs korlátozva az SQL Server példány megosztása.  

###  <a name="bkmk_2008SCPpreq"></a>Szolgáltatáskapcsolódási pont  
**.NET-keretrendszer:**  

-   .NET-keretrendszer 4.5.2  

     A helyrendszer-szerepkör telepítésekor, ha a kiszolgáló még nincs telepítve a .NET-keretrendszer támogatott verziója, a Configuration Manager automatikusan telepíti a .NET-keretrendszer 4.5.2-es verzióját. A telepítés újraindítás függőben állapotba állíthatja a kiszolgálót. Ha újraindítás függőben a .NET-keretrendszer .NET-alkalmazások sikertelen lehet, amíg a kiszolgáló újraindul, és a telepítés befejeződése után.  

**Visual C++ terjeszthető csomag:**  

-   Configuration Manager telepíti a Microsoft Visual C++ 2013 újraterjeszthető csomagot egy terjesztési pontot üzemeltető minden számítógépen.  

-   A helyrendszer-szerepkör a x64 szükséges verziója.  

###  <a name="bkmk_2008SUPpreq"></a>Szoftverfrissítési pont  
**.NET-keretrendszer:**  

-   .NET-keretrendszer 3.5 SP1 (vagy újabb)  

-   .NET-keretrendszer 4.5.2  

**IIS-konfiguráció:**

Az alapértelmezett IIS-konfigurációt megadása kötelező.  

**A Windows Server Update Services:**  

-   Telepítenie kell a Windows Server-szerepkör a Windows Server Update Services egy számítógépen a szoftverfrissítési pont telepítése előtt.  

-   További információk: [Szoftverfrissítések tervezése a System Center Configuration Managerben](../../../sum/plan-design/plan-for-software-updates.md).

###  <a name="bkmk_2008SMPpreq"></a>Állapotáttelepítési pont  
**IIS-konfiguráció:**

Az alapértelmezett IIS-konfigurációt megadása kötelező.  

