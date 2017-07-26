---
title: "Szoftverfrissítések előfeltételei |} Microsoft Docs"
description: "További tudnivalók a System Center Configuration Manager szoftverfrissítéseinek előfeltételei."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: fdf05118-162a-411e-b72e-386b9dc9a5e1
ms.translationtype: Machine Translation
ms.sourcegitcommit: 238ef5814c0c1b832c28d63c9f3879e21a6c439b
ms.openlocfilehash: 179f076f228daa5adf612275a822cd379b0ce1e3
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---

# <a name="prerequisites-for-software-updates-in-system-center-configuration-manager"></a>A System Center Configuration Manager szoftverfrissítéseinek előfeltételei

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ez a témakör a System Center Configuration Manager szoftverfrissítéseinek előfeltételeit ismerteti. Ezekhez a külső és a belső függőségek külön táblázatban vannak felsorolva.  

## <a name="software-update-dependencies-external-to-configuration-manager"></a>Software Update Manager alkalmazáson kívüli függőségek konfiguráció  
 Az alábbi szakaszok tartalmazzák a szoftverfrissítésekre vonatkozó külső függőségeket.  

### <a name="internet-information-services-iis"></a>Internet Information Services (IIS)  
 Internet Information Services (IIS) ahhoz, hogy futtatható a szoftverfrissítési pont, a felügyeleti pont és a terjesztési pont helyrendszer-kiszolgálóján kell lennie. További információkért lásd: [helyrendszerszerepkörök előfeltételei](../../core/plan-design/configs/site-and-site-system-prerequisites.md).  

### <a name="windows-server-update-services-wsus"></a>Windows Server Update Services (WSUS)  
 A WSUS szolgáltatás szükséges a szoftverfrissítések szinkronizálásához és az ügyfeleken a szoftverfrissítések megfelelőségi vizsgálatának végrehajtásához. A WSUS-kiszolgálót még az előtt telepíteni kell, hogy létrehozná a szoftverfrissítési pont helyrendszerszerepkörét. A szoftverfrissítési pont a WSUS alábbi verzióit támogatja:  

-   WSUS 4 (a Windows Server 2012 és Windows Server 2012 R2 szerepköre)  

-   A WSUS 3.2 (a Windows Server 2008 R2 szerepköre)  

 Ha egy helyen több szoftverfrissítési pont van, győződjön meg arról, hogy az összes futtatnak WSUS ugyanazt a verzióját.  

> [!WARNING]  
>  A **frissítések** kell csak szoftverfrissítések annál újabb verziók támogatják a WSUS 4.0-s verzióját. Mielőtt szinkronizálná az új besorolást, és kiértékelné a Windows 10-es karbantartási tervben szereplő, Windows 10 operációs rendszert futtató számítógépeket, mindenképpen telepítse a WSUS számára készült [3095113-as gyorsjavítást](https://support.microsoft.com/kb/3095113) a szoftverfrissítési pontokon és helykiszolgálókon. A gyorsjavítás lehetővé teszi, hogy a Windows Server 2012 vagy Windows Server 2012 R2 rendszerű kiszolgálók szinkronizálják és terjesszék a Windows 10-hez készült funkciófrissítéseket. További információkért lásd: [kezelése a Windows mint szolgáltatás](../../osd/deploy-use/manage-windows-as-a-service.md).  
>   
>  Ha a **Verziófrissítések** https://supportszoftverfrissítéseinek előfeltételeit ismerteti.microsoftszoftverfrissítéseinek előfeltételeit ismerteti.com/kb/3095113 [3095113-as gyorsjavítást](https://support.microsoft.com/kb/3095113)besorolással, látogasson el a [Recover from synchronizing the Verziófrissítések category before you install KB 3095113](#BKMK_RecoverUpgrades)szoftverfrissítéseinek előfeltételeit ismerteti.  

### <a name="wsus-administration-console"></a>WSUS felügyeleti konzol  
 A WSUS felügyeleti konzoljának szükséges a Configuration Manager helykiszolgálón, amikor a szoftverfrissítési pont távoli helyrendszer-kiszolgáló és WSUS nincs telepítve a helykiszolgálón.  

> [!IMPORTANT]  
>  A WSUS-verzió a helykiszolgálón a szoftverfrissítési pontokon futó WSUS-verziójának egyeznie kell.  

> [!IMPORTANT]  
>  Ne használjon a WSUS felügyeleti konzolját a WSUS beállításainak konfigurálására. A Configuration Manager kapcsolódik a WSUS szolgáltatáshoz a szoftverfrissítési ponton futó, és konfigurálja a megfelelő beállításokat.  

### <a name="windows-update-agent-wua"></a>Windows Update Agent (WUA)  
 A WUA ügyfélszoftver szükséges az ügyfeleken, hogy azok kapcsolódni tudjanak a WSUS-kiszolgálóhoz, és be tudják olvasni a megfelelőség szempontjából vizsgálandó szoftverfrissítések listáját.  

 A Configuration Manager telepítésekor letöltődik a WUA legújabb verziója. Ezt követően a Configuration Manager-ügyfél telepítésekor, a WUA frissítése, ha szükséges. A telepítés sikertelensége esetén azonban más módszert kell használnia a WUA ügyfélszoftver frissítésére.  

## <a name="software-update-dependencies-internal-to-configuration-manager"></a>A Configuration Manageren belüli szoftverfrissítés-függőségeket  
 Az alábbi szakaszok tartalmazzák a belső függőségek, a szoftverfrissítések a Configuration Manager alkalmazásban.  

### <a name="management-points"></a>Felügyeleti pontok  
 Felügyeleti pontok információt továbbítanak az ügyfélszámítógépek és a Configuration Manager-hely között. Ezek szükségesek a szoftverfrissítésekhez.  

### <a name="software-update-point"></a>Szoftverfrissítési pont  
 A WSUS-kiszolgálón kell tudni telepíteni a Configuration Manager szoftverfrissítéseinek telepítenie kell egy szoftverfrissítési pontot. További információkért lásd: [telepítse és konfigurálja a szoftverfrissítési pontot](../get-started/install-a-software-update-point.md).

### <a name="distribution-points"></a>Terjesztési pontok  
 Terjesztési pontok szükségesek a szoftverfrissítésekhez a tartalmat tároló. Terjesztési pontok telepítéséről és a tartalomkezelésről kapcsolatos további információkért lásd: [tartalom és tartalomkezelési infrastruktúra kezelése](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

### <a name="client-settings-for-software-updates"></a>A szoftverfrissítésekhez tartozó ügyfélbeállítások  
 A szoftverfrissítések alapértelmezés szerint engedélyezettek az ügyfeleknél. Vannak azonban olyan egyéb beállítások, amelyekkel szabályozhatja, hogyan és mikor ügyfelek számára a szoftverrel megfelelőségének az értékelését frissíti, és szabályozhatja, hogy a szoftverfrissítések hogyan legyenek telepítve.  

 További információkért tekintse át a következőket:  

-   [A szoftverfrissítések ügyfélbeállítások](../get-started/manage-settings-for-software-updates.md#a-namebkmkclientsettingsa-client-settings-for-software-updates).  

-   [Szoftverfrissítések ügyfélbeállításainak](../../core/clients/deploy/about-client-settings.md#software-updates) témakör.  

### <a name="reporting-services-point"></a>Jelentéskészítési szolgáltatási pont  
 A jelentéskészítési szolgáltatási pont helyrendszerszerepkörével lehet megjeleníteni a szoftverfrissítésekre vonatkozó jelentéseket. Ez a szerepkör nem kötelező, de ajánlott a használata. További információ jelentéskészítési szolgáltatási pont, lásd: [konfigurálása reporting](../../core/servers/manage/configuring-reporting.md) .  

##  <a name="BKMK_RecoverUpgrades"></a> Helyreállítás azt követően, hogy még a KB 3095113 telepítése előtt szinkronizálta a Verziófrissítések kategóriát  
 Telepítse a WSUS számára készült [3095113-as gyorsjavítást](https://support.microsoft.com/kb/3095113) a szoftverfrissítési pontokon és a helykiszolgálókon, mielőtt szinkronizálná a **Verziófrissítések** besorolást. Ha a gyorsjavítás nincs telepítve a **Verziófrissítések** besorolás engedélyezésekor, a WSUS akkor is látni fogja a Windows 10 1511-es buildjéhez tartozó verziófrissítést, ha nem képes a hozzá tartozó csomagok megfelelő letöltésére és telepítésére. Ha a [3095113-as gyorsjavítást](https://support.microsoft.com/kb/3095113)előzetes telepítése nélkül szinkronizálná a verziófrissítést, használhatatlan adatokat töltene fel a WSUS-adatbázisba (SUSDB), amelyeket a verziófrissítések megfelelő telepítése érdekében el kell távolítani.  A következő eljárással probléma megoldásához.  

#### <a name="to-recover-from-synchronizing-the-upgrades-classification-before-you-install-kb-3095113"></a>Helyreállítás a verziófrissítések besorolású KB 3095113 telepítése előtt  

1.  Törölje a verziófrissítések besorolású szoftverfrissítéseket. Az alábbi mintaparancsfájl hasonló PowerShell-parancsfájlt használhatja:  

    ```  
    $Server = Get-WSUSServer  
    $Config = $Server.GetConfiguration()  
    $Update10563 = “df4e45a3-946d-4467-b3fd-8621174bb666”  
    $UpdateGUID = New-Object Guid($Update10563)  
    $Server.DeleteUpdate($UpdateGUID)  
    ```  

    > [!IMPORTANT]  
    >  Előtt futtatnia kell a parancsfájl az összes szoftverfrissítési pontján a Configuration Manager-hierarchiában, nyissa meg a következő lépéssel.  

     A Verziófrissítések besorolású szoftverfrissítések tömeges törléséhez módosítsa úgy a PowerShell-parancsprogramot, hogy az több GUID-ot olvasson be egy .txt-fájlból.  

2.  Törölje a jelet a **frissítések** besorolás a szoftverfrissítési pont összetevő tulajdonságai párbeszédpanelen (további információkért lásd: [besorolások és termékek konfigurálása](../get-started/configure-classifications-and-products.md)), majd indítsa el a szoftverfrissítések szinkronizálása (további információkért lásd: [szinkronizálhatók a szoftverfrissítések](../get-started/synchronize-software-updates.md).  

3.  Telepítse a WSUS számára készült [3095113-as gyorsjavítást](https://support.microsoft.com/kb/3095113) a szoftverfrissítési pontokon és helykiszolgálókon.  

4.  Válassza ki a **frissítések** besorolás a szoftverfrissítési pont összetevő tulajdonságai párbeszédpanelen (további információkért lásd: [besorolások és termékek konfigurálása](../get-started/configure-classifications-and-products.md)), majd indítsa el a szoftverfrissítések szinkronizálása (további információkért lásd: [szinkronizálhatók a szoftverfrissítések](../get-started/synchronize-software-updates.md).  

## <a name="next-steps"></a>További lépések
[Készítse elő a szoftverfrissítések kezelése](../get-started/prepare-for-software-updates-management.md)

