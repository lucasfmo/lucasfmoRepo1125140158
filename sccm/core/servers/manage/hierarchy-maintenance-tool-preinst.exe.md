---
title: "Hierarchia-karbantartó eszközt |} Microsoft Docs"
description: "Megérteni a hierarchia-karbantartó eszközt mire alkalmas, és ezért előfordulhat, hogy használhatja. Parancssori beállítások hivatkozást tartalmaz."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cead6825-6113-4ba5-a381-ac3598dfee86
caps.latest.revision: 7
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 10b1010ccbf3889c58c55b87e70b354559243c90
ms.openlocfilehash: f3ddeaadfb1418aeeaacdca47768600c86b59083
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="hierarchy-maintenance-tool-preinstexe-for-system-center-configuration-manager"></a>A System Center Configuration Managerhez készült hierarchia-karbantartási eszköz (Preinst.exe)

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A hierarchia-karbantartási eszköz (Preinst.exe) átadja parancsok a a System Center Configuration Manager hierarchia Manager miközben fut a Hierarchiakezelő szolgáltatás. A hierarchia-karbantartási eszköz automatikusan települ a Configuration Manager-hely telepítésekor. A Preinst.exe megtalálhatja a \\ &lt; *Helykiszolgáló_neve*> \SMS_&lt;*Helykód*\bin\X64\00000409 megosztott mappában található a helykiszolgálón.  

 A hierarchia-karbantartási eszközt a következő helyzetekben használhatja:  

-   Amikor biztonságos kulcscserére van szükség, vannak olyan helyzetek, amikor manuálisan kell elvégezni a nyilvános kulcsok kezdeti cseréjét a helyek között. További információért lásd a jelen témakör [Nyilvános kulcsok manuális cseréje a helyek között](#BKMK_ManuallyExchangeKeys) című részét.  

-   Az olyan aktív feladatok eltávolításához, melyek már nem létező célhelyre vonatkoznak.  

-   Egy helykiszolgáló törléséhez a Configuration Manager konzolról, amikor nem tudja eltávolítani a helyet a telepítővel. Például fizikailag eltávolít egy Configuration Manager-hely nélkül először a telepítő futtatásával eltávolítaná a helyet, ha a hely adatai még létezni fognak a fölérendelt hely adatbázisában, és a fölérendelt hely továbbra is próbál az alárendelt hellyel való kommunikációhoz. A probléma megoldásához futtassa a hierarchia-karbantartó eszközt, és manuálisan törölnie az alárendelt helyet a fölérendelt hely adatbázisából.  

-   Egy hely összes Configuration Manager szolgáltatások leállítása anélkül, hogy egyesével kellene leállítania a szolgáltatásokat.  

-   Amikor helyreállít egy helyet, a CHILDKEYS kapcsoló használatával terjesztheti a nyilvános kulcsokat több alárendelt helyről a helyreállított helyre.  

A hierarchia-karbantartási eszköz futtatásához az aktuális felhasználónak rendszergazdai jogosultsággal kell rendelkeznie a helyi számítógépen. Kifejezetten a felhasználónak kell helyfelügyeleti jogosultsággal rendelkeznie; nem elegendő, hogy csak örökölje ezt a jogosultságot egy olyan csoport tagjaként, amelyiknek van ilyen jogosultsága.  

## <a name="hierarchy-maintenance-tool-command-line-options"></a>A hierarchia-karbantartó eszköz parancssori kapcsolói  
A hierarchia-karbantartó eszköz használatánál helyileg kell azt futtatnia a központi felügyeleti hely, az elsődleges hely vagy a másodlagos hely kiszolgálóján.  

A hierarchia-karbantartó eszköz futtatásakor a következő szintaxist kell használnia: preinst.exe /&lt;beállítás\>. A parancssori kapcsolók a következők:  

 **/ DELJOB &lt;* Helykód*> ** – ezt a beállítást használja egy helyen az összes feladat vagy parancs törlésére az aktuális helyről a megadott célhelyre.  

 **/ DELSITE &lt;* Eltávolítandó_alárendelt_helykód*> ** – segítségével ezt a beállítást egy fölérendelt helyen törölheti az alárendelt helyek adatait a fölérendelt hely adatbázisából. Általában akkor használják ezt a kapcsolót, amikor a helykiszolgáló számítógépet leszerelték, mielőtt eltávolították volna róla a helyet.  

> [!NOTE]  
>  A /DELSITE kapcsoló nem távolítja el a eltávolítandó_alárendelt_helykód paraméterrel megadott helyet a számítógépről. Ez a beállítás csak a helyadatokat a Configuration Manager adatbázisából.  

**/ DUMP &lt;* Helykód*> ** – használja ezt a beállítást, a helyi helykiszolgálón a helyvezérlő rendszerképeket írni a gyökérmappában található azon a meghajtó, amelyre a hely telepítve van. Kiírhatja egy adott hely helyvezérlő rendszerképét a mappába, vagy kiírhatja a hierarchia összes helyvezérlő fájlját.  

-   / DUMP &lt; *Helykód*> csak az adott hely helyvezérlő rendszerképét írja.  

-   A /DUMP kiírja az összes hely helyvezérlő fájljait.  

A képfájl a bináris megjelenítése a helyvezérlő fájlnak, mely a Configuration Manager-hely adatbázisában tárolódnak. A helyvezérlő fájl kiírt rendszerképe az alaplemezkép és a függőben lévő változásképek összege.  

A helyvezérlő fájl rendszerképének hierarchia-karbantartó eszközzel való kiírása, után a fájlnév pedig a formátum a következő lesz: sitectrl_&lt;*Helykód*> .ct0.  

**/ STOPSITE** -használja ezt a beállítást, a helyi helykiszolgálón a Configuration Manager Helyösszetevő-kezelő szolgáltatás, mely részlegesen alaphelyzetbe állítja a helyet egy leállítási ciklusának kezdeményezésére. A leállítási ciklus futásakor a helykiszolgálón és annak távoli hely egyes Configuration Manager szolgáltatások le van állítva. Ezek a szolgáltatások újratelepítésre vannak megjelölve. E leállítási ciklus eredményeképpen bizonyos jelszavak automatikusan megváltoznak a szolgáltatások újratelepítésekor.  

> [!NOTE]  
>  Ha meg szeretné tekinteni a leállítás, az újratelepítés és a helyösszetevő-kezelő jelszó-változtatásának rekordjait, akkor a parancssori kapcsoló használata előtt engedélyezze ennek az összetevőnek a naplózását.  

A leállítási ciklus az elindítása után automatikusan halad, és átugorja az összes nem válaszoló összetevőt és számítógépet. Ha azonban a helyösszetevő-kezelő szolgáltatás nem tud elérni egy távoli helyrendszert a leállítási ciklus során, akkor a helyösszetevő-kezelő szolgáltatás újraindításakor újratelepíti a távoli helyrendszerre telepített összetevőket. Újraindításakor a helyösszetevő-kezelő szolgáltatás ismételten megkísérli az összes olyan szolgáltatás újratelepítését, melyek újratelepítésre vannak megjelölve, amíg az sikeres nem lesz.  

A helyösszetevő-kezelő szolgáltatást Service Manager használatával indíthatja újra. Az újraindítás után minden érintett szolgáltatást eltávolít, újratelepít és újraindít. A /STOPSITE kapcsoló leállítási ciklus kezdeményezésére történő használata után nem kerülheti el az újratelepítési ciklusokat a helyösszetevő-kezelő szolgáltatás újraindítása után.  

**/KEYFORPARENT** – Ezzel a kapcsolóval terjesztheti egy hely nyilvános kulcsát egy fölérendelt helyre.  

A keyforparent beállítás fájlba helyezi a hely nyilvános kulcsának &lt; *Helykód*>. A program gyökerében CT4 programfájlok meghajtójának. Miután lefuttatta a preinst.exe ezzel a kapcsolóval, manuálisan másolja a &lt; *Helykód*>. CT4 fájlt a fölérendelt hely...\Inboxes\hman.box mappájába (nem a hman.box\pubkey mappájába).  

**/KEYFORCHILD** – Ezzel a kapcsolóval terjesztheti a hely nyilvános kulcsát egy alárendelt helyre.  

A keyforchild a lehetőségnél a hely nyilvános kulcsát a fájl &lt; *Helykód*>. A program gyökerében CT5 programfájlok meghajtójának. Miután lefuttatta a preinst.exe ezzel a kapcsolóval, manuálisan másolja a &lt; *Helykód*>. CT5 fájlt az alárendelt hely...\Inboxes\hman.box mappájába (nem a hman.box\pubkey mappájába).  

**/CHILDKEYS** – Ezt a kapcsolót a helyreállított hely alárendelt helyein alkalmazhatja. Ezzel a kapcsolóval terjesztheti a több alárendelt helyről származó nyilvános kulcsokat a helyreállított helyre.  

A childkeys a lehetőségnél a kulcsot a helyről, ha futtatja a kapcsolót, és az összes alárendelt helyének nyilvános kulcsát a fájl &lt; *Helykód*>. CT6.  

Miután lefuttatta a preinst.exe ezzel a kapcsolóval, manuálisan másolja a &lt; *Helykód*>. CT6 fájlt a helyreállított hely...\Inboxes\hman.box mappájába (nem a hman.box\pubkey mappájába).  

**/PARENTKEYS** – Ezt a kapcsolót a helyreállított hely fölérendelt helyén alkalmazhatja. Ezzel a kapcsolóval terjesztheti az összes fölérendelt helyről származó nyilvános kulcsokat a helyreállított helyre.  

A parentkeys a lehetőségnél a kulcsot a helyről, ha futtatja a kapcsolót, és, hogy a hely valamennyi fölérendelt a kulcsok helyének fájlba &lt;Helykód\>. CT7.  

Miután lefuttatta a preinst.exe ezzel a kapcsolóval, manuálisan másolja a &lt; *Helykód*>. CT7 fájlt a helyreállított hely...\Inboxes\hman.box mappájába (nem a hman.box\pubkey mappájába).  

##  <a name="BKMK_ManuallyExchangeKeys"></a>A helyek közötti nyilvános kulcsok manuális cseréje  
Alapértelmezés szerint a **biztonságos kulcscsere kötelező** engedélyezve van a Configuration Manager-helyek. Amikor biztonságos kulcscserére van szükség, két olyan helyzet van, amikor manuálisan kell elvégezni a kulcsok kezdeti cseréjét a helyek között.  

-   Ha az Active Directory-séma nem lett kibővítve a Configuration Manager  

-   Configuration Manager-helyek nem teszik közzé a helyadatokat az Active Directory  

A hierarchia-karbantartó eszközzel exportálhatja a nyilvános kulcsokat minden helyhez. Az exportálás után manuálisan kell kicserélnie a kulcsokat a helyek között.  

> [!NOTE]  
>  A nyilvános kulcsok manuális cseréje után áttekintheti a **hman.log** naplófájlt, amely rögzíti a helykonfigurációk változásait és a helyadatok közzétételét az Active Directory tartományi szolgáltatások felé a fölérendelt helykiszolgálón, hogy ellenőrizze, feldolgozta-e az elsődleges hely az új nyilvános kulcsot.  

#### <a name="to-manually-transfer-the-child-site-public-key-to-the-parent-site"></a>Az alárendelt hely nyilvános kulcsának manuális átvitele a fölérendelt helyre  

1.  Az alárendelt helyre bejelentkezve nyisson meg egy parancssort, és navigáljon a **Preinst.exe** fájlhoz.  

2.  Írja be az alárendelt hely nyilvános kulcsának exportálásához a következőket: **Preinst / keyforparent**  

3.  A keyforparent lehetőségnél az alárendelt hely nyilvános kulcsát a  **&lt;Helykód\>. CT4** fájl a rendszermeghajtó gyökérmappájában található.  

4.  Helyezze át a  **&lt;Helykód\>. CT4** fájlt a fölérendelt hely ** &lt;telepítési könyvtár\>\inboxes\hman.box** mappa.  

#### <a name="to-manually-transfer-the-parent-site-public-key-to-the-child-site"></a>A fölérendelt hely nyilvános kulcsának manuális átvitele az alárendelt helyre  

1.  A fölérendelt helyre bejelentkezve nyisson meg egy parancssort, és navigáljon a **Preinst.exe** fájlhoz.  

2.  Írja be a fölérendelt hely nyilvános kulcsának exportálásához a következőket: **Preinst / keyforchild**.  

3.  A keyforchild a lehetőségnél a fölérendelt hely nyilvános kulcsát a  **&lt;Helykód\>. CT5** fájl a rendszermeghajtó gyökérmappájában található.  

4.  Helyezze át a  **&lt;Helykód\>. CT5** fájlt a ** &lt;telepítési könyvtár\>\inboxes\hman.box** az alárendelt hely könyvtárába.  

