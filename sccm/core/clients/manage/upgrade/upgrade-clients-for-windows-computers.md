---
title: "Ügyfelek frissítése |} Microsoft Docs"
description: "Frissítse az ügyfeleket a Windows rendszerű számítógépekre a System Center Configuration Managerben."
ms.custom: na
ms.date: 05/04/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6143fd47-48ec-4bca-b53b-5b9b9f067bc3
caps.latest.revision: 11
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 212628639300e9c361f7cee61b3df6b1cb6874ce
ms.openlocfilehash: 98b8c92e4dad3cef1ed3701b9c0f9111eb9941ea
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-upgrade-clients-for-windows-computers-in-system-center-configuration-manager"></a>A Windows rendszerű számítógépekhez készült ügyfelek frissítése a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Az ügyfél a Windows rendszerű számítógépeken használja a Configuration Manager ügyfél-telepítési módszert, vagy az automatikus ügyfélfrissítési funkcióival frissítheti. A következő ügyfél-telepítési módszerek alkalmazhatók a Windows rendszerű számítógépeken telepített ügyfélszoftverek frissítéséhez:  

-   Csoportházirend telepítése  

-   Bejelentkezési parancsprogramfájl telepítése  

-   Manuális telepítés  

-   Frissítéstelepítés  

 Ha szeretné frissíteni az ügyfelet egy ügyfél-telepítési módszert, használatával kapcsolatos további azokat a módszereket [ügyfélszoftverek központi telepítése Windows rendszerű számítógépekre a System Center Configuration Managerben](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md).

 1610 verziójától kezdve, kizárhatja az ügyfelek a frissítés alatt egy kizárási csoportban megadásával. További információkért lásd: [kihagyása a Windows rendszerű számítógépekhez készült frissítése ügyfelek](exclude-clients-windows.md).  


> [!TIP]  
>  Amennyiben a Configuration Manager egy előző verziójáról frissíti a kiszolgáló infrastruktúráját \(például Configuration Manager 2007-ről, vagy System Center 2012 Configuration Managerről\), a Configuration Manager-ügyfelek frissítése előtt ajánlott a kiszolgálófrissítések elvégzése, beleértve az összes aktuális ág frissítését is.   Az aktuális ág legújabb frissítése tartalmazza az ügyfél legújabb verzióját is, ezért az ügyfelek frissítését az összes használni kívánt Configuration Manager-frissítés telepítése után célszerű elvégezni.

> [!NOTE]
> Ha azt tervezi, a hely hozzárendelésének ügyfelei számára a frissítés során, megadhatja az új hely a SMSSITECODE client.msi-tulajdonsággal. Ha a SMSSITECODE automatikus használja, meg kell adnia SITEREASSIGN = igaz értékre automatikus hozzárendelései megtörténik a frissítés során. További információkért lásd: [SMSSITECODE](../../deploy/about-client-installation-properties.md#smssitecode).

## <a name="use-automatic-client-upgrade"></a>Az automatikus ügyfélfrissítés használata  
 Beállíthatja, hogy automatikusan frissítse az ügyfélszoftvert a Configuration Manager ügyfélszoftver legújabb verzióját, ha a Configuration Manager azonosítja, hogy a Configuration Manager hierarchiájában hozzárendelt ügyfél verziója korábbi, mint a hierarchiában használt verzió a Configuration Manager. Ez az eset tartalmazza az ügyfél frissítését a legújabb verzióra, amikor a rendszer megkísérli hozzárendelni a Configuration Manager-hely.  

 Az ügyfelek a következő esetekben frissíthetők automatikusan:  

-   Az ügyfél verziója korábbi, mint a hierarchiában használt verzió.  

-   A központi adminisztrációs helyen található ügyfélen van telepített nyelvi csomag, a meglévő ügyfélen pedig nincs.  

-   Az ügyfél egyik előfeltételének verziója különbözik az ügyfélen telepített verziótól.  

-   Egy vagy több ügyfél-telepítési fájl verziója eltérő.  

> [!NOTE]  
>  A jelentés futtatása **száma a Configuration Manager ügyfelek ügyfél-verziónkénti** a jelentés mappában **hely – ügyfél-információ** a hierarchiában a Configuration Manager-ügyfél különböző verzióit azonosításához.  

 A Configuration Manager létrehoz egy frissítési csomagot, amely automatikusan elküld a hierarchiában lévő összes terjesztési pont alapértelmezés szerint. Ha módosítja a központi adminisztrációs helyen lévő ügyfélcsomagot, például felvesz egy nyelvi csomagot, a Configuration Manager automatikusan frissíti a csomagot, majd elküldi a hierarchiában lévő összes terjesztési pontra. Ha engedélyezve van az ügyfélfrissítés, mindegyik ügyfél automatikusan telepíteni fogja a nyelvi csomagot.  

> [!NOTE]  
>  A Configuration Manager nem küld automatikusan az ügyfél frissítése csomagot a Configuration Manager felhő alapú terjesztési pontokra.  

 Azt javasoljuk, hogy engedélyezze az automatikus ügyfélfrissítéseket a hierarchiát. Ez akkor is megtartja az ügyfelek frissítése, minimális adminisztratív terhelés mellett.  

 A következő művelet végrehajtásával konfigurálhatja az automatikus ügyfélfrissítést. Az automatikus ügyfélfrissítést központi adminisztrációs helyen kell konfigurálni, és ez a konfiguráció a hierarchiában lévő összes ügyfélre érvényes.  

### <a name="to-configure-automatic-client-upgrades"></a>Automatikus ügyfélfrissítések konfigurálása  

1.  A Configuration Manager konzolon kattintson az **Adminisztráció**elemre.  

2.  Az **Adminisztráció** munkaterületen bontsa ki a **Helykonfiguráció**csomópontot, majd kattintson a **Helyek**lehetőségre.  

3.  A **Kezdőlap** **Helyek** csoportjában kattintson a **Hierarchiabeállítások**elemre.  

4.  A **Hierarchiabeállítások tulajdonságai** párbeszédpanel **Ügyfélfrissítés** lapján ellenőrizze az üzemi ügyfél verzióját és dátumát, és győződjön meg róla, hogy ezt a verziót kívánja használni a Windows rendszerű számítógépek frissítéséhez.  Ha nem a várt ügyfélverzió jelenik meg, előfordulhat, hogy üzemivé kell előléptetnie az üzem előtti ügyfelet. További információkért lásd: [ügyfélfrissítések tesztelése egy üzem előtti gyűjteményben a System Center Configuration Managerben az](../../../../core/clients/manage/upgrade/test-client-upgrades.md).  

5.  Kattintson **A hierarchiában lévő összes ügyfél frissítése üzemi ügyfél használatával lehetőségre** , majd az **OK** gombra a megerősítő párbeszédpanelen.  

6.  Ha a kiszolgálókra nem szeretné alkalmazni az ügyfélfrissítéseket, kattintson a **Kiszolgálók frissítésének mellőzése**elemre.  

7.  Adja meg, hogy a számítógépeknek hány napon belül kell telepíteniük az ügyfelet, miután megkapják az ügyfélházirendet. Az ügyfél a megadott számú napon belül véletlenszerű időközzel lesz frissítve. Ez megakadályozza azt, hogy egyszerre kezdődjön el nagy mennyiségű ügyfélszámítógép frissítése.

    > [!NOTE]
    > Frissítheti az ügyfelet a számítógépen futnia kell. Ha a számítógép nem fut, ha a frissítés fogadásához ütemezve van, a frissítés nem történik meg. Ehelyett a számítógép újraindítása után egy másik frissítés időpontra van ütemezve egy véletlenszerű számú napon belül engedélyezett. Ha ez történik, hány nap frissítése után, a frissítés ütemezi a véletlenszerű egyszerre a számítógép újraindítása után 24 órán belül megtörténik.
    >     
    > Ez a viselkedés miatt számítógépek, amelyek rendszeresen állítsa le a munkanapok végén hosszabb időt vehet igénybe egy frissítéséhez, ha a véletlenszerűen ütemezett frissítési idő a időn belül nem várt.

7. Verziójától 1610, ha a frissítés alatt, az ügyfelek kizárni kívánt kattintson **kizárási megadott frissítésből ügyfelek** , és adja meg a gyűjtemény kizárása.

8.  Kattintson az **Ügyfél telepítési csomagjának automatikus terjesztése azokra a terjesztési pontokra, amelyek engedélyezve vannak az előzetesen beállított tartalomhoz**lehetőségre, ha szeretné átmásolni az ügyféltelepítési csomagot azokra a terjesztési pontokra, amelyeken engedélyezve van az előkészített tartalom.  

9. Kattintson az **OK** gombra a beállítások mentéséhez és a **Hierarchiabeállítások tulajdonságai** párbeszédpanel bezárásához. Az ügyfelek akkor kapják meg ezeket a beállításokat, amikor letöltik következő alkalommal a házirendet.

>[!NOTE]
>Ügyfélfrissítések fogadják el semmilyen Configuration Manager karbantartási időszakok konfigurálása.

