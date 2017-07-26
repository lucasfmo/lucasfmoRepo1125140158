---
title: "Operációs rendszer verziófrissítő csomagjainak kezelése |} Microsoft Docs"
description: "Ismerje meg, hogyan felügyelheti az operációs rendszer verziófrissítő csomagjai a System Center Configuration Managerben."
ms.custom: na
ms.date: 12/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b9b22655-b8c1-461f-8047-3a7e906f647a
caps.latest.revision: 12
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f44505c977b511223a083a960f871371c0ff133
ms.openlocfilehash: 5fef04f26b12bced073332fd1f7b4e7c7bd7d398
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="manage-operating-system-upgrade-packages-with-system-center-configuration-manager"></a>Operációs rendszer verziófrissítő csomagjainak kezelése a System Center Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A frissítési csomag a System Center Configuration Managerben a számítógépen meglévő operációs rendszer frissítéséhez használt Windows telepítési forrásfájlokat tartalmaz. Az alábbi szakaszok kezelése az operációs rendszer verziófrissítő csomagjai a Configuration Manager alkalmazásban.

##  <a name="BKMK_AddOSUpgradePkgs"></a> Operációsrendszer-frissítő csomagok hozzáadása a Configuration Managerhez  
 Az operációs rendszer verziófrissítő csomagjának használata előtt hozzá kell adnia a csomagot a Configuration Manager-hely. Az operációsrendszer-frissítő csomagot a következő eljárással adhatja hozzá egy helyhez.  

#### <a name="to-add-an-operating-system-upgrade-package"></a>Operációsrendszer-frissítő csomag hozzáadása  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Operációs rendszerek**pontot, majd kattintson az **Operációs rendszer verziófrissítő csomagjai**elemre.  

3.  Az Operációs rendszer verziófrissítő csomagjának felvétele varázsló elindításához kattintson a **Kezdőlap** **Létrehozás** csoportjában található **Operációs rendszer verziófrissítő csomagjának felvétele** elemre.  

4.  Az **Adatforrás** oldalon adja meg az operációsrendszer-frissítő csomag telepítési forrásfájljainak hálózati elérési útját. Adja meg az UNC használatával, hogy a telepítés forrásfájljainak a helye **\\\kiszolgáló\elérésiút** .  

    > [!NOTE]  
    >  A telepítési forrásfájlok között megtalálható a Setup.exe és egyéb, az operációs rendszer telepítéséhez használt fájlok és mappák.  

    > [!IMPORTANT]  
    >  A nemkívánatos módosítások megakadályozása érdekében korlátozza a telepítési forrásfájlokhoz való hozzáférést.  

5.  Az **Általános** lapon adja meg a következő adatokat, majd kattintson a **Tovább**gombra. Ez az információ azonosításra használható, amikor több operációs rendszeri telepítőcsomag van ugyanazon a helyen.  

    -   **Név**: Adja meg az operációs rendszer telepítőcsomagjának nevét.  

    -   **Verzió**: Adja meg az operációs rendszer telepítőcsomagjának verzióját.  

    -   **Megjegyzés**: Adja meg az operációs rendszer telepítőcsomagjának rövid leírását.  

6.  Fejezze be a varázslót.  

 Az operációs rendszeri telepítőcsomag már terjeszthető azokra a terjesztési pontokra, amelyekhez hozzáférnek a központi telepítési feladatütemezések.  

##  <a name="BKMK_DistributeBootImages"></a> Operációsrendszer-lemezképek terjesztése terjesztési pontra  
 Az operációsrendszer-lemezképek terjesztése ugyanúgy történik a terjesztési pontokra, mint más tartalmaké. A legtöbb esetben az operációs rendszer központi telepítésének megkezdése előtt legalább egy terjesztési pontra szükséges eljuttatni az operációs rendszer lemezképét. Operációsrendszer-lemezkép terjesztésére vonatkozó lépésekért lásd: [Tartalom terjesztése](../../core/servers/deploy/configure/deploy-and-manage-content.md#a-namebkmkdistributea-distribute-content).  

##  <a name="BKMK_OSUpgradePkgApplyUpdates"></a> Szoftverfrissítések alkalmazása operációs rendszer verziófrissítő csomagjára  
 A Configuration Manager 1602-es verziójával kezdve alkalmazhat új szoftverfrissítéseket az operációs rendszer lemezképét az operációs rendszer verziófrissítő csomagjának a. Rendelkeznie kell egy frissítési csomagot a szoftverfrissítések alkalmazása előtt a szoftver infrastruktúrával frissíti, sikeresen szinkronizálnia a szoftverfrissítéseket, és letölti a szoftverfrissítéseket a helykiszolgáló tartalomtárába. További információkért lásd: [szoftverfrissítések központi telepítése](../../sum/deploy-use/deploy-software-updates.md).  

 A megfelelő szoftverfrissítéseket meghatározott ütemezés szerint alkalmazhatja a verziófrissítő csomagokra. A megadott ütemezés szerint meg a Configuration Manager végrehajtja a szoftverfrissítéseket, választhat, hogy az operációs rendszer verziófrissítő csomagjának, és igény szerint terjesztheti a frissített verziófrissítő csomagot a terjesztési pontokra. Az operációs rendszer verziófrissítő csomagjára vonatkozó információ, beleértve az importálás idején már végrehajtott szoftverfrissítéseket is, a helyadatbázisban tárolódik. A verziófrissítő csomag eredeti létrehozása óta alkalmazott szoftverfrissítéseket a rendszer szintén a helyadatbázisban tárolja. Amikor elindítja a varázslót, amellyel szoftverfrissítéseket alkalmazhat az operációs rendszer verziófrissítő csomagjára, a varázsló lekér egy listát azokról az alkalmazható szoftverfrissítésekről, amelyek még nem lettek alkalmazva a választott frissítőcsomagra. A Configuration Manager a szoftverfrissítések a helykiszolgálón lévő tartalomtárba másolja, és végrehajtja a szoftverfrissítéseket az operációs rendszer verziófrissítő csomagjának.  

 Az operációs rendszer verziófrissítő csomagjára a következő módon alkalmazhat szoftverfrissítéseket.  

#### <a name="to-apply-software-updates-to-an-operating-system-upgrade-package"></a>Szoftverfrissítések alkalmazása operációs rendszer verziófrissítő csomagjára  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Operációs rendszerek**pontot, majd kattintson az **Operációs rendszer verziófrissítő csomagjai**elemre.  

3.  Jelölje ki azt a verziófrissítő csomagot, amelyikre szoftverfrissítéseket kíván alkalmazni.  

4.  A varázsló elindításához a **Kezdőlap** **Operációs rendszer verziófrissítő csomagjai** csoportjában kattintson a **Frissítések ütemezése** elemre.  

5.  A **Frissítések kiválasztása** oldalon jelölje ki az operációs rendszer lemezképén végrehajtani kívánt szoftverfrissítéseket, majd kattintson a **Tovább**gombra.  

6.  Az **Ütemezés beállítása** lapon adja meg a következő beállításokat, majd kattintson a **Tovább**gombra.  

    1.  **Ütemezés**: Adja meg a ütemezését, amikor a szoftverfrissítések alkalmazása az operációs rendszer lemezképén.  

    2.  **Folytatás hiba**:  Szoftverfrissítések alkalmazása a lemezképen, még akkor is, ha a hiba továbbra is ezt a beállítást.  

    3.  **Terjessze a lemezképet terjesztési pontokra**: Ezt a beállítást követően szeretné frissíteni az operációs rendszer lemezképét a terjesztési pontokon a szoftverfrissítések alkalmazása.  

7.  Az **Összefoglalás** lapon ellenőrizze az adatokat, majd kattintson a **Tovább**gombra.  

8.  A **Befejezés** lapon ellenőrizze, hogy a szoftverfrissítések alkalmazása sikeresen megtörtént-e az operációs rendszer lemezképén.  

