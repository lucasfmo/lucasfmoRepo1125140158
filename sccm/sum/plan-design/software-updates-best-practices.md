---

title: "Ajánlott eljárások a szoftverfrissítések |} Microsoft Docs"
description: "Használja az alábbi gyakorlati tanácsok a System Center Configuration Manager szoftverfrissítések."
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
ms.assetid: 6d20389a-9de2-4a64-bced-9fc4fa519174
ms.translationtype: Machine Translation
ms.sourcegitcommit: d94acac84f052a01de9d9c9f65f237c0006c45b8
ms.openlocfilehash: 5df20f3703442de1be6220ca2770e182e330c036
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017



---
# <a name="best-practices-for-software-updates-in-system-center-configuration-manager"></a>Bevált gyakorlatok a System Center Configuration Manager szoftverfrissítéseihez

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ez a témakör a System Center Configuration Manager szoftverfrissítések gyakorlati tanácsokat tartalmaz. A gyakorlati tanácsok a kezdeti telepítés és a folyamatos működés szerinti bontásban szerepelnek.  

## <a name="installation-best-practices"></a>Gyakorlati tanácsok a telepítéshez  
 Használja az alábbi gyakorlati tanácsokra a Configuration Manager szoftverfrissítések telepítésekor.  

### <a name="use-a-shared-wsus-database-for-software-update-points"></a>Megosztott WSUS-adatbázis használata a szoftverfrissítési pontokhoz  
 Ha több szoftverfrissítési pontot telepít egy elsődleges helyre, akkor ugyanazt a WSUS-adatbázist kell használni minden olyan pont esetében, amelyek ugyanabban az Active Directory-erdőben vannak. Az azonos adatbázis használatával jelentős mértékben enyhíthető az ügyfél és a hálózat teljesítményére gyakorolt hatás, amely olyankor léphet fel, amikor az ügyfelek új szoftverfrissítési pont használatára váltanak. Amikor egy ügyfél olyan új szoftverfrissítési pont használatára vált át, amely a korábbi szoftverfrissítési ponttal azonos adatbázist használ, különbözeti vizsgálatra ebben az esetben is sor kerül, de ez a vizsgálat sokkal kisebb méretű, mint ha a WSUS-kiszolgálóhoz saját adatbázis tartozna.  

> [!IMPORTANT]  
>  Meg kell osztania a helyi WSUS-tartalommappákat is, ha megosztott WSUS-adatbázist használ a szoftverfrissítési pontokhoz.  

 További információ a szoftverfrissítési pontok váltásáról: a [szoftverfrissítési pontok váltásáról](../../sum/plan-design/plan-for-software-updates.md#BKMK_SUPSwitching) szakasz a [tervezése a System Center Configuration Manager szoftverfrissítések](../../sum/plan-design/plan-for-software-updates.md) témakör.  

### <a name="when-configuration-manager-and-wsus-use-the-same-sql-server-configure-one-of-these-to-use-a-named-instance-and-the-other-to-use-the-default-instance-of-sql-server"></a>Ha a Configuration Manager és a WSUS szolgáltatás ugyanazt az SQL Server rendszert használja, egyiküket konfigurálja elnevezett példány használatára, a másikat az SQL Server alapértelmezett példányának használatára.  
 Ha a Configuration Manager és a WSUS adatbázisa ugyanazt az SQL Server használja, és ossza meg ugyanazt az SQL Server-példányt, nem lehet egyszerűen megállapítani az erőforrások felhasználásának megoszlását a két alkalmazás között. A Configuration Manager és a WSUS másik SQL Server-példányt használja, esetén az egyes alkalmazások esetleg fellépő erőforrás-használati problémák diagnosztizálására és egyszerűbb.  

### <a name="specify-the-store-updates-locally-setting-for-the-wsus-installation"></a>A „Frissítések helyi tárolása” beállítás megadása a WSUS-telepítéshez  
 Ha a WSUS telepítése, válassza ki a **frissítések helyi tárolása** beállítást. Ha meg van adva ez a beállítás, a szoftverfrissítésekhez tartozó licencfeltételek letöltődnek a szinkronizálási folyamat során, és azokat a WSUS-kiszolgáló helyi merevlemeze tárolja. Ha a beállítás nincs megadva, előfordulhat, hogy az ügyfélszámítógépek nem ellenőrzik az olyan szoftverfrissítések megfelelőségét, amelyekhez licencfeltételek tartoznak. A szoftverfrissítési pont telepítésekor a WSUS-szinkronizálás kezelője alapértelmezés szerint 60 percenként ellenőrzi, hogy ez a beállítás engedélyezve van-e.  

## <a name="operational-best-practices"></a>Gyakorlati tanácsok az üzemeltetéshez  
 Támaszkodjon az alábbi gyakorlati tanácsokra a szoftverfrissítések használatánál:  

### <a name="limit-software-updates-to-1000-in-a-single-software-update-deployment"></a>Egyetlen szoftverfrissítési célú központi telepítésben legfeljebb 1000 szoftverfrissítés alkalmazása  
 A szoftverfrissítések száma az egyes központi telepítésekben ne haladja meg az 1000-et. Automatikus központi telepítési szabály létrehozása esetén ellenőrizze, hogy a megadott kritérium nem eredményez-e 1000-nél több szoftverfrissítést. Amikor kézzel telepíti a frissítéseket, ne válasszon 1000-nél több telepítendő frissítést.  

### <a name="create-a-new-software-update-group-each-time-an-automatic-deployment-rule-runs-for-patch-tuesday-and-for-general-deployment"></a>Egy új szoftverfrissítési csoport létrehozása minden alkalommal, amikor egy automatikus központi telepítési szabály futtatása a "Frissítő kedd" vagy általános központi telepítés  
 A szoftverfrissítési telepítéshez legfeljebb 1000 szoftverfrissítés tartozhat. Automatikus központi telepítési szabály létrehozásakor megadhatja, hogy meglévő frissítési csoport használ, vagy a szabály futásakor minden alkalommal új frissítési csoportot hoz létre. Amikor olyan automatikus központi telepítési szabályhoz határozza meg a feltételeket, amely több szoftverfrissítést eredményez, és a szabály ismétlődő módon fut, adja meg, hogy a szabály minden futásakor új szoftverfrissítési csoport jöjjön létre. Ez megakadályozza, hogy a központi telepítés túllépje a telepítésenkénti 1000 szoftverfrissítést jelentő korlátozását.  

### <a name="use-an-existing-software-update-group-for-automatic-deployment-rules-for-endpoint-protection-definition-updates"></a>Meglévő szoftverfrissítési csoport használata az Endpoint Protection-definíciófrissítésekre vonatkozó automatikus központi telepítési szabályokhoz  
 Mindig használjon meglévő szoftverfrissítési csoportot, ha az Endpoint Protection-definíciófrissítéseket gyakran telepíti automatikus központi telepítési szabály használatával Különben az idő múlásával akár több száz szoftverfrissítési csoport is létrejöhet. A definíciófrissítések közzétevői általában úgy állítják be a definíciófrissítéseket, hogy az érvényességük lejárjon, ha már négy újabb frissítés van helyettük. Így az automatikus központi telepítési szabállyal létrehozott szoftverfrissítési csoport soha nem fog négynél több – egy aktív és három felülírt – definíciófrissítést tartalmazni a közzétevőre vonatkozóan.  

## <a name="see-also"></a>Lásd még:  
 [A System Center Configuration Manager szoftverfrissítések tervezése](../../sum/plan-design/plan-for-software-updates.md)

