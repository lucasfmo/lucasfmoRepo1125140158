---
title: "Eszköz- és felhasználói erőforrások felderítéséhez |} Microsoft Docs"
description: "Olvassa el a felderítési áttekintést folyamat és a felderítési adatrekordokat."
ms.custom: na
ms.date: 2/8/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 30844519-ce14-456f-bfb8-4318b578e9f6
caps.latest.revision: 20
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 7b6674f331c82cc7899b8661cf38b9d3022cf21b
ms.openlocfilehash: 647826e9d340d3ef97abab0dba51041a3727dedc
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="run-discovery-for-system-center-configuration-manager"></a>A felderítés futtatása a System Center Configuration Managerből

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Segítségével egy vagy több felderítési módszerek a System Center Configuration Managerben található felügyelhető eszköz- és felhasználói erőforrásokat. Felderítési segítségével is a környezetben található hálózati infrastruktúrák azonosítására. Számos különböző módszer segítségével különböző dolgok felderítésére, és minden metódus rendelkezik saját konfigurációk és korlátozások érvényesek.  

## <a name="overview-of-discovery"></a>A felderítés áttekintése  
 Felderítés az a folyamat, amely szerint a Configuration Manager értesül a felügyelhető dolgokról. A rendelkezésre álló felderítési módszerek a következők:  

-   Active Directory-erdőfelderítés  

-   Active Directory-csoportfelderítés  

-   Active Directory-rendszerfelderítés  

-   Active Directory-felhasználófelderítés  

-   Szívveréses felderítés  

-   Hálózatfelderítés  

-   Kiszolgálófelderítés  

> [!TIP]  
>  Az egyéni felderítési módszerekről az [About discovery methods for System Center Configuration Manager](../../../../core/servers/deploy/configure/about-discovery-methods.md) (Tudnivalók a System Center Configuration Manager felderítési módjairól) című témakörben talál további információkat.  
>   
>  A használandó módszerek kiválasztásával, és a hierarchia megfelelő helyeinek segítségért lásd: [válassza ki a megfelelő felderítési módszerek a System Center Configuration Manager](../../../../core/servers/deploy/configure/select-discovery-methods-to-use.md).  

 A legtöbb felderítési módszereket használja, a módszert egy helyen, és állítsa be az keresési meghatározott hálózatban vagy Active Directory-helyekhez. Futtatott felderítés lekérdezi eszközöket és felhasználókat, melyekkel kezelhető a Configuration Manager a megadott helyen. Amikor egy felderítési módszer sikeresen megtalál erőforrásra vonatkozó adatokat, ezt az információt egy felderítési adatrekordot (DDR) nevű fájlba helyezi el. A fájl majd egy elsődleges vagy központi adminisztrációs hely dolgoz fel. A DDR feldolgozásakor a rendszer létrehoz egy új rekordot a helyadatbázisban az újonnan felderített erőforrásokhoz, vagy frissíti a meglévő rekordokat az új információval.  

 A felderítés nagy mennyiségű hálózati adatforgalmat generálhat, és az általuk előállított adatrekordok jelentősen igénybe veszik a CPU erőforrásait feldolgozása során. Ezért tervez használni, csak azokat a felderítési módszereket, amelyekre szüksége van céljai eléréséhez. Elég lehet akár mindössze egy-két felderítési módszer alkalmazása is, amelyek mellett később szabályozott módon bármikor aktiválhat további módszereket is a mélyebb felderítéshez.  

 Után a felderítési adatokat ad hozzá a Helyadatbázis, a információ majd replikálja, függetlenül attól, hol történt annak felderítése vagy feldolgozása a hierarchia mindegyik helyén. Ezért amíg beállíthat különböző ütemezéseket és beállításokat a felderítési módszerek különböző helyeken, előfordulhat, hogy futtatni egy meghatározott felderítési módszert csak egyetlen helyen. Ez csökkenti a felhasznált hálózati sávszélesség az ismétlődések, és a feldolgozás, a redundáns felderítési adatok több különböző helyére.  

 Felderítési adatok segítségével egyéni gyűjtemények és lekérdezések, amelyek logikailag csoportosítják az erőforrásokat a felügyeleti feladatokhoz. Példa:  

-   Ügyféltelepítések kérdez le, vagy frissíteni.  

-   Tartalom központi telepítése a felhasználók vagy eszközök számára.  

-   Ügyfélbeállítások és kapcsolódó konfigurációk telepítése.

##  <a name="BKMK_DDRs"></a>Tudnivalók az adatfelderítési rekordokról  
 Adatfelderítési rekordok által létrehozott olyan fájlok egy felderítési módszer. Kezelheti a Configuration Managerben, például számítógépek, felhasználók, és bizonyos esetekben hálózati infrastruktúrára erőforrásra vonatkozó adatokat tartalmaznak. Ezek feldolgozása az elsődleges helyeken vagy a központi felügyeleti helyeken történik. Miután az adatfelderítési Rekordban lévő erőforrás-információkat is meg kell adni az adatbázisba, a DDR törlődik, és globális adatokként a hierarchia összes helyére replikálja az adatokat.  

 Az adatfelderítési rekordok feldolgozását végző hely a rekordokban lévő adatoktól függ:  

-   Adatfelderítési rekordok az újonnan felderített erőforrásokhoz, amelyek nem az adatbázis feldolgozásának a hierarchia legfelső szintű helyén. A legfelső szintű hely új erőforrásrekordot hoz létre az adatbázisban, és hozzárendeli egy egyedi azonosítót. Az adatfelderítési rekordok átvitele fájl alapú replikációként amíg el nem érik a legfelső szintű helyen.  

-   A korábban felderített objektumokhoz tartozó adatfelderítési rekordokat az elsődleges helyek dolgozzák fel. Az alárendelt elsődleges helyek nem továbbítanak adatfelderítési rekordokat a központi felügyeleti helyre, ha az adatfelderítési rekord az adatbázisban már szereplő erőforrásra vonatkozó adatokat tartalmaz.  

-   A másodlagos helyek nem dolgozza fel adatfelderítési rekordokat, és ezeket mindig fájl alapú replikációként a fölérendelt elsődleges helyre.  

A DDR-fájlokat a .ddr kiterjesztés azonosítja, és méretük jellemzően 1 KB körüli.  

## <a name="get-started-with-discovery"></a>A felderítés első lépései:  
 Mielőtt a Configuration Manager konzol segítségével discovery beállítása, tisztában kell lennie a különbségek a módszereket, mit tehet, és az egyes módszerek korlátozásait.  

A következő témakörök, amelyek segítséget a felderítési módszerek sikeres használatát alaprendszert hozhat létre:  

-   [Felderítési módszerek a System Center Configuration Manager](../../../../core/servers/deploy/configure/about-discovery-methods.md)  

-   [Válassza ki a megfelelő felderítési módszerek a System Center Configuration Managerhez](../../../../core/servers/deploy/configure/select-discovery-methods-to-use.md)  

Majd, Miután megismerte a használni kívánt módszereket, tekintse át az egyes módszerek beállítása [felderítési módszerek konfigurálása a System Center Configuration Manager](../../../../core/servers/deploy/configure/configure-discovery-methods.md).  

