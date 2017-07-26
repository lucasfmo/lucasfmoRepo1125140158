---
title: "Operációsrendszer-lemezképek kezelése |} Microsoft Docs"
description: "A Configuration Managerben, ismerje meg a módszereket, amelyek segítségével a Windows-rendszerkép (WIM), fájljaiban tárolt operációsrendszer-lemezképek kezelése."
ms.custom: na
ms.date: 12/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fab13949-371c-4a4c-978e-471db1e54966
caps.latest.revision: 17
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 03722ff4f480cd26842e395fe1f7ec8359e2b33e
ms.openlocfilehash: 6953c3834ca303b949f22436010a87b3da9688dc
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="manage-operating-system-images-with-system-center-configuration-manager"></a>Operációsrenszer-lemezképek kezelése a System Center Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A Configuration Managerben az operációsrendszer-lemezképek tárolása WIM formátumú fájlokban történik, amelyek azoknak a referenciafájloknak és -mappáknak a tömörített gyűjteményét tartalmazzák, amelyekre szükség van az operációs rendszer sikeres telepítéséhez és konfigurációjához a számítógépen. Az operációs rendszerek minden központi telepítési forgatókönyve esetén ki kell választania egy operációsrendszer-lemezképet.   Használja az alapértelmezett operációsrendszer-lemezképet, vagy összeállíthatja az operációs rendszer lemezképét egy Ön által konfigurált referencia-számítógépről. A referencia-számítógép összeállításakor operációsrendszer-fájlokat, illesztőprogramokat, támogatófájlokat, szoftverfrissítéseket, eszközöket és más alkalmazásokat adhat hozzá az operációs rendszerhez, mielőtt rögzítené azt a képfájl létrehozásához. A következő szakasz mindegyik módszerről tartalmaz információt.  

 **Alapértelmezett kép**  

 Az alapértelmezett operációs rendszer lemezképe (install.wim) megtalálható a Windows operációs rendszer telepítési fájljai között. Ez a kép az alap operációs rendszer lemezképe, amely az illesztőprogramok szabványos készletét tartalmazza. Az alapértelmezett operációsrendszer-lemezkép használatakor az operációs rendszer telepítése után a feladatütemezési lépések használatával alkalmazásokat telepíthet, és más konfigurációkat hozhat létre.  Az alapértelmezett operációsrendszer-lemezkép az <*operációsrendszer-forrás elérési útja*>\Sources\install.wim helyen található.  

-   **Előnyök**  

    -   A lemezkép mérete kisebb, mint a rögzített lemezkép.  

    -   A feladatütemezési lépések használatával dinamikusabb az alkalmazások és konfigurációk telepítése. Megváltoztathatja például a telepítendő alkalmazásokat és a konfigurációkat a feladatütemezésben, és nem szükséges új lemezképet készíteni az operációs rendszerről.  

-   **Hátrányok**  

    -   Az operációs rendszer telepítése több időt vesz igénybe, mert az alkalmazások telepítésére és egyéb beállításokra csak az operációs rendszer telepítésének befejezése után kerül sor.  

 **A rögzített lemezkép**  

 Testre szabott operációsrendszer-lemezkép létrehozásához szüksége lesz egy, a kívánt operációs rendszerrel rendelkező referencia-számítógépre, és az alkalmazások telepítését és a beállítások konfigurálását is el kell végeznie. Ezután rögzítheti az operációs rendszer lemezképét a referencia-számítógépről a WIM-fájl létrehozásához. A referencia-számítógép rendszerének összeállítását elvégezheti manuálisan, vagy pedig feladatütemezés használatával automatizálhatja az összeállítási folyamat egyes lépéseit vagy egészét.   
A testre szabott operációsrendszer-lemezkép létrehozásának lépéseit, lásd: [operációsrendszer-lemezképek testreszabása](customize-operating-system-images.md).  

-   **Előnyök**  

    -   Ez a telepítési mód gyorsabb lehet, mint az alapértelmezett lemezkép használata. Az alkalmazásokat például előre lehet telepíteni a rögzített operációsrendszer-lemezképpel, és később nem szükséges azokat feladatütemezési lépések segítségével telepíteni.  

-   **Hátrányok**  

    -   Az operációs rendszer telepítése több időt vesz igénybe, mert az alkalmazások telepítésére és egyéb beállításokra csak az operációs rendszer telepítésének befejezése után kerül sor.  


##  <a name="BKMK_AddOSImages"></a>A Configuration Manager operációsrendszer-lemezképek hozzáadása  
 Az operációsrendszer-lemezkép használata előtt hozzá kell adnia a kép Configuration Manager-hely. Operációs rendszer lemezképét a következő eljárással adhatja hozzá egy helyhez.  

#### <a name="to-add-an-operating-system-image-to-a-site"></a>Operációs rendszer lemezképének hozzáadása egy helyhez  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Operációs rendszerek** pontot, majd kattintson az **Operációsrendszer-lemezképek** elemre.  

3.  Az Operációsrendszer-lemezkép hozzáadása varázsló elindításához kattintson a **Kezdőlap** **Létrehozás** csoportjában található **Operációsrendszer-lemezkép hozzáadása** varázsló elemre.  

4.  Az **Adatforrás** oldalon adja meg az operációs rendszeri lemezkép hálózati elérési útját. Írja be például a következőt: **\\\server\path\OS.WIM**.  

5.  Az **Általános** lapon adja meg a következő adatokat, majd kattintson a **Tovább** gombra. Ez az információ azonosításra használható, amikor több operációs rendszeri lemezkép van ugyanazon a helyen.  

    -   **Név**: Adja meg a lemezkép nevét. Alapértelmezés szerint a program a WIM-fájlból veszi a lemezkép nevét.  

    -   **Verzió**: Adja meg a lemezkép verziószámát.  

    -   **Megjegyzés**: Adja meg a lemezkép rövid leírását.  

6.  Fejezze be a varázslót.  

 Most már terjesztheti az operációs rendszer lemezképét a terjesztési pontokra.  

##  <a name="BKMK_DistributeBootImages"></a>A terjesztési pontokra operációsrendszer-lemezképek terjesztése  
 Az operációsrendszer-lemezképek terjesztése ugyanúgy történik a terjesztési pontokra, mint más tartalmaké. A legtöbb esetben az operációs rendszer központi telepítésének megkezdése előtt legalább egy terjesztési pontra szükséges eljuttatni az operációs rendszer lemezképét. Operációsrendszer-lemezkép terjesztésére vonatkozó lépésekért lásd: [Tartalom terjesztése](../../core/servers/deploy/configure/deploy-and-manage-content.md#a-namebkmkdistributea-distribute-content).  

##  <a name="BKMK_OSImagesApplyUpdates"></a>Szoftverfrissítések alkalmazása operációs rendszeri lemezképre  
 Időnként megjelennek olyan szoftverfrissítések, amelyek alkalmazhatók az operációs rendszeri lemezképen lévő operációs rendszerre. Szoftverfrissítések lemezképre alkalmazása előtt rendelkeznie kell a szoftverfrissítéseket, az infrastruktúra helyezze, rendelkezik sikeresen kell szinkronizálnia a szoftverfrissítéseket, és letölti a telepített frissítések a tartalomtár a helykiszolgálón. További információkért lásd: [szoftverfrissítések központi telepítése](../../sum/deploy-use/deploy-software-updates.md).  

 Ezeket az alkalmazható szoftverfrissítéseket a lemezképre vonatkozóan megadott ütemterv szerint lehet végrehajtani. A megadott ütemezés szerint meg a Configuration Manager végrehajtja a szoftverfrissítéseket, kiválasztott az operációs rendszer lemezképét, és igény szerint terjesztheti a frissített lemezképet a terjesztési pontokra. Az operációs rendszer lemezképére vonatkozó információ, beleértve az importálás idején már végrehajtott szoftverfrissítéseket is, a helyadatbázisban tárolódik. A szoftverfrissítések azért hajthatók végre a lemezképen, mert kezdetben bekerültek és tárolódnak a helyadatbázisban. Az operációs rendszeri lemezkép szoftverfrissítését végző varázsló elindításakor lekéri azon alkalmazható szoftverfrissítések listáját, amelyek még nem lettek végrehajtva a kijelölt lemezképre. A Configuration Manager a szoftverfrissítések a helykiszolgálón lévő tartalomtárba másolja, és végrehajtja a szoftverfrissítéseket az operációs rendszer lemezképét.  

 A következő eljárás használható a szoftverfrissítések operációs rendszeri lemezképre történő végrehajtásához.  

#### <a name="to-apply-software-updates-to-an-operating-system-image"></a>Szoftverfrissítések alkalmazása operációs rendszeri lemezképre  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Operációs rendszerek** pontot, majd kattintson az **Operációsrendszer-lemezképek** elemre.  

3.  Jelölje ki azt az operációs rendszeri lemezképet, amelyikre végrehajtja a szoftverfrissítéseket.  

4.  A varázsló elindításához kattintson a **Kezdőlap** **Operációs rendszer lemezképe** csoportjában a **Frissítések ütemezése** elemre.  

5.  A **Frissítések kiválasztása** oldalon jelölje ki az operációs rendszer lemezképén végrehajtani kívánt szoftverfrissítéseket, majd kattintson a **Tovább** gombra.  

6.  Az **Ütemezés beállítása** lapon adja meg a következő beállításokat, majd kattintson a **Tovább**gombra.  

    1.  **Ütemezés**: Adja meg a ütemezését, amikor a szoftverfrissítések alkalmazása az operációs rendszer lemezképén.  

    2.  **Folytatás hiba**:  Szoftverfrissítések alkalmazása a lemezképen, még akkor is, ha a hiba továbbra is ezt a beállítást.  

    3.  **Terjessze a lemezképet terjesztési pontokra**: Ezt a beállítást követően szeretné frissíteni az operációs rendszer lemezképét a terjesztési pontokon a szoftverfrissítések alkalmazása.  

7.  Az **Összefoglalás** lapon ellenőrizze az adatokat, majd kattintson a **Tovább**gombra.  

8.  A **Befejezés** lapon ellenőrizze, hogy a szoftverfrissítések alkalmazása sikeresen megtörtént-e az operációs rendszer lemezképén.  

##  <a name="BKMK_OSImageMulticast"></a>Az operációs rendszer lemezképének előkészítése csoportos központi telepítést  
 Több számítógép számára csoportos küldéssel történő telepítéssel engedélyezheti az operációsrendszer-lemezkép egyidejű letöltését. A lemezképet a terjesztési pont csoportosan küldi az ügyfeleknek ahelyett, hogy a lemezkép egy példányát minden egyes ügyfélnek külön kapcsolaton keresztül küldené el. Ha úgy dönt, a [Windows központi telepítése a hálózaton keresztül használjon csoportos](../deploy-use/use-multicast-to-deploy-windows-over-the-network.md) operációs rendszer központi telepítésének módja, az operációs rendszer lemezképének csomagját, az operációs rendszer lemezképét csoportos küldésre képes terjesztési pontra történő terjesztése előtt a csoportos küldés támogatásához kell konfigurálnia. A következő eljárással adhatja meg a csoportos küldés beállításait operációs rendszer lemezképének meglévő csomagjában.  

#### <a name="to-modify-an-operating-system-image-package-to-use-multicast"></a>Operációs rendszer lemezképcsomagjának módosítása csoportos küldés használatára  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Operációs rendszerek** pontot, majd kattintson az **Operációsrendszer-lemezképek** elemre.  

3.  Válassza ki azt az operációsrendszer-lemezképet, amelyet a csoportos küldésre engedélyezett terjesztési pontra továbbítani kíván.  

4.  A **Kezdőlap** **Tulajdonságok** csoportjában kattintson a **Tulajdonságok** elemre.  

5.  Válassza a **Terjesztési beállítások** lapot, és konfigurálja a következő beállításokat:  

    -   **Ez a csomag (csak WinPE esetén) csoportos küldésének engedélyezése**: Akkor válassza ezt a beállítást egy időben települ központilag operációsrendszer-lemezképek, hogy a Configuration Manager.  

    -   **Csoportosan küldött csomagok titkosítása**: Adja meg, hogy a lemezkép titkosítva legyen-e, a terjesztési pontra való továbbítás előtt. Akkor adja meg ezt a beállítást, ha a csomagban bizalmas adatok szerepelnek. Ha a lemezkép nincs titkosítva, a csomag tartalma a hálózaton nem titkosított szöveg formájában lesz látható, és esetleg illetéktelen felhasználó olvashatja.  

    -   **Csomag átvitele csak csoportos küldésen keresztül**: Adja meg, hogy a terjesztési pont csak csoportos küldési munkamenetben a lemezkép telepítéséhez.  

         Ha megadja a **Csomag átvitele csak csoportos küldésen keresztül** beállítást, akkor a **Tartalom helyi letöltése, ha a futó feladatütemezés igényli** beállítást is meg kell adni az operációs rendszer lemezképének központi telepítési beállításaként. A lemezképre vonatkozóan a központi telepítési beállításokat megadhatja az operációsrendszer-lemezkép továbbításakor, vagy később, a telepítés tulajdonságainak szerkesztésével. A központi telepítés beállításai a telepítési objektum **Tulajdonságok** lapjának **Terjesztési pontok** lapfülén találhatóak.  

6.  Kattintson az **OK** gombra.  

