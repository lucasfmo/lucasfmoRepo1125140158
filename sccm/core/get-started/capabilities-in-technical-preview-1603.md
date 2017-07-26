---
title: "A Technical Preview 1603-as Configuration Manager lehetőségeit"
description: "További tudnivalók a Technical Preview elérhető szolgáltatások a System Center Configuration Manager, 1603-as verzióra."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5f861b72-9f14-4d17-a512-4a79b660abe6
caps.latest.revision: 8
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: noindex,nofollow
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: dee2b4ce042bb4a434bb019e17a6b16e2807945c
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1603-for-system-center-configuration-manager"></a>A Technical Preview 1603-as rendszer képességei Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (Technical Preview-ban)*

Ez a cikk ismerteti az új szolgáltatásokat, amelyek elérhetők a Technical Preview a System Center Configuration Manager, 1603-as verzióra. A verzió frissítése, és új képességeket adhat a Configuration Manager technical preview-helyeken telepítheti. Alternatív megoldásként a System Center Technical Preview 5 használatakor jelen verziójában telepíti a System Center Configuration Manager Technical Preview alapszintű verziójára. A technical preview ezen verziója a telepítés előtt tekintse át a bevezető témakört, [a System Center Configuration Manager Technical Preview](../../core/get-started/technical-preview.md), megismerkedhet a általános követelményei és korlátozásai technikai előzetes kiadásról, hogyan használja, és hogyan visszajelzést a technical Preview verzióinak szolgáltatásai közötti frissítéséhez.  

 **A Technical Preview kiadással kapcsolatos ismert problémák:**  

-   Ebben a kiadásban a korábban kiadott funkciókhoz frissítéseket tartalmaz, de nem esetleges új szolgáltatásokat. Ezért a frissítési varázsló szolgáltatások lapja üres lesz, ha korábban már frissített a 1602-es és engedélyezve van az összes funkcióját 1602-es.  

-   A helykiszolgáló frissítései a Technical Preview 1603-as, miután az ügyfél nem képes használni a távvezérlési szolgáltatásokat, amíg szintén frissítik őket a 1603-as verzióra.  

 **Új funkciókat próbálhatja ki ebben a következők:**  

##  <a name="BKMK_SC1603"></a>A szoftverközpont fejlesztései  

### <a name="new-tiled-view-for-apps"></a>Alkalmazások új, csempe típusú megjelenítése  
 A végfelhasználók mostantól választhat listás és csempés megjelenítése az alkalmazások listáját a **alkalmazások** szoftverközpont fülre.  

### <a name="select-multiple-updates-in-software-center"></a>Több frissítés kijelölése a Szoftverközpontban  
 Az a **frissítések** lapon szoftverközpont, most több frissítést, vagy válasszon **összes frissítése** megkezdéséhez egyszerre több frissítés telepítését.  

##  <a name="BKMK_RC1603"></a>Távvezérlési funkció fejlesztései  

### <a name="limit-shared-clipboard-access-in-a-remote-control-session"></a>A megosztott vágólap hozzáférésének korlátozása a távvezérlési munkamenetben  
 Most engedélyezheti az új távoli eszközök ügyfélbeállítás **adatkérés a felhasználónak a megosztott vágólapon történő fájlátvitelhez** a távvezérlési munkamenetet a megosztott vágólap korlátozhatják.  

 Ha engedélyezve van, a végfelhasználó egy távoli munkamenetet megosztó kell engedélyeket a néző a munkamenet nézőjének fájlokat a munkamenetből a helyi számítógépre a megosztott vágólapon keresztül előtt.  

 Ezzel hozzáad egy védelmi réteget biztosít a felhasználó korábban, ha a megjelenítő teljes vezérlést kapott a végfelhasználó számítógép, azok lenne a megosztott vágólap használatával fájlátvitel a munkamenetből a helyi számítógépre, de a felhasználó teljes mértékben transzparens módon.  

##  <a name="BKMK_RamDiskTFTP"></a> A RamDisk TFTP blokkméretének és ablakméretének testreszabása PXE-képes terjesztési pontokon  
 A Technical Preview 1603-as testreszabhatja a RamDisk TFTP blokkméretét és ablakméretét a PXE-képes terjesztési pontokon. Ha testreszabta a hálózatot, akkor a rendszerindító lemezkép letöltése időtúllépési hiba miatt sikertelen lehet, ha a blokk vagy az ablak mérete túl nagy. A RamDisk TFTP blokkméretének és ablakméretének testreszabásával lehetővé válik a TFTP-forgalom optimalizálása, amikor PXE-t használ a konkrét hálózati követelmények teljesítésére.   
A leghatékonyabb konfiguráció meghatározásához tesztelje a testreszabott beállításokat a környezetében.  

-   **TFTP-blokkméret**: A blokkméret a kiszolgáló által (a tárgyalt RFC 2347 szabványnak megfelelően) a fájlt letöltő ügyfélre küldött adatcsomagok mérete. A nagyobb blokkméret lehetővé teszi a kiszolgáló számára, hogy kevesebb csomagot küldjön, így kevesebbet kell várakozni a kiszolgáló és az ügyfél közötti üzenetváltás miatti késésekre. A nagyobb blokkméret ugyanakkor töredezett csomagokat eredményezhet, amit a PXE-ügyfelek implementációjának többsége nem támogat.  

-   **TFTP-ablakméret**: TFTP egy visszaigazolási (ACK) csomagot igényel minden adatblokk küldött. A kiszolgáló egészen addig nem küldi el a következő blokkot a sorozatból, amíg meg nem kapja az előző blokk ACK-csomagját. A TFTP-ablak a Központi Windows-telepítési szolgáltatások egyik funkciója, amellyel meghatározható, hogy hány adatblokk tölt ki egy ablakot. A kiszolgáló közvetlenül egymás után küldi az adatblokkokat egészen addig, amíg az ablak megtelik, majd az ügyfél ACK-csomagot küld. Az ablak méretének növelésével csökkenthető az ügyfél és a kiszolgáló közötti üzenetváltás miatti várakozások száma, ezzel együtt pedig a rendszerindító lemezkép letöltésének teljes időtartama is.  

### <a name="try-it-out"></a>Próbálja ki!  
 Próbálja a következő feladatok végezhetők, majd ez a témakör tetejénél található visszajelzési információk használva tudassa velünk, milyen eredménnyel járt:  

-   Képes vagyok egyéni a RamDisk TFTP-ablakméretet beállítani a PXE-képes terjesztési ponton.  

-   Képes vagyok egyéni a RamDisk TFTP-blokkméretet beállítani a PXE-képes terjesztési ponton.  

### <a name="to-modify-the-ramdisk-tftp-window-size"></a>A RamDisk TFTP-ablakméret módosítása  

-   Egyéni RamDisk TFTP-blokkméret beállításához vegye fel a következő beállításkulcsot a PXE-képes terjesztési pontokon:  

     **Hely**: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SMS\DP  
    Név: RamDiskTFTPWindowSize  

     **Típus**: REG_DWORD  

     **Érték**: &lt;egyéni ablakméret\>  

 Az alapértelmezett érték 1 (azaz 1 adatblokk tölti ki az ablakot).  

### <a name="to-modify-the-ramdisk-tftp-block-size"></a>A RamDisk TFTP-blokkméret módosítása  

-   Egyéni RamDisk TFTP-blokkméret beállításához vegye fel a következő beállításkulcsot a PXE-képes terjesztési pontokon:  

     **Hely**: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SMS\DP  
    Név: RamDiskTFTPBlockSize  

     **Típus**: REG_DWORD  

     **Érték**: &lt;egyéni blokkméret\>  

 Az alapértelmezett érték 4096 (4k).  

