---
title: "A tartalomtár Lemezkarbantartó eszköz |} Microsoft Docs"
description: "A tartalomtár Lemezkarbantartó eszköz segítségével távolítsa el az árva-tartalom már nem a System Center Configuration Manager központi telepítés."
ms.custom: na
ms.date: 4/7/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 226cbbb2-9afa-4e2e-a472-be989c0f0e11
caps.latest.revision: 4
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 32f7fc4ef9c8e8d3c2ec8eeaf9a3174bad992ffb
ms.openlocfilehash: 76e6772bdd5cbd32d525e728f6ebc988b045da78
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="the-content-library-cleanup-tool-for-system-center-configuration-manager"></a>A tartalomtár Lemezkarbantartó eszköz a System Center Configuration Managerhez

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

 1702 verziójával kezdve a parancssori eszköz használható (**ContentLibraryCleanup.exe**), amely már nem a csomag vagy egy terjesztési pontról alkalmazás társított tartalom eltávolítása (elárvul tartalom). Az eszköz a tartalomtár Lemezkarbantartó eszköz neve, és a Configuration Manager korábbi termékek, amely a hasonló eszközök régebbi verzióit váltja fel.  

Az eszköz csak hatással van a tartalom a terjesztési ponton, meg kell adnia az eszköz futtatásakor. Az eszköz nem lehet eltávolítani a tartalmat a helykiszolgálón lévő tartalomtárba.

Található **ContentLibraryCleanup.exe** a *%CM_Installation_Path%\cd.latest\SMSSETUP\TOOLS\ContentLibraryCleanup a\* mappájában a helykiszolgálón, egy központi adminisztrációs hely vagy elsődleges helyen.

## <a name="requirements"></a>Követelmények  
 Az eszköz csak alapján futtathatók egyetlen terjesztési pont egyszerre.  
 - Közvetlenül a törölni kívánt terjesztési pontot futtató számítógépen, vagy egy másik kiszolgálóra távolról futtatható.
 - Az eszköz futtató felhasználói fióknak a Configuration Manager-hierarchia egy teljes körű rendszergazda egyenlő közvetlen szerepkör alapú felügyelet engedélyekkel kell rendelkeznie. Az eszköz nem működik, ha a fiók ezeket az engedélyeket kap, amely a teljes körű rendszergazdai jogosultságokkal rendelkezik a Windows biztonsági csoport tagjaként.

## <a name="modes-of-operation"></a>Működési módok
A következő két módban futtathatja az eszközt. Javasoljuk, hogy az eszközt futtatja *Lehetőségelemzések* módban az eszköz futtatása előtt áttekintheti az eredményeket *mód törlése*:
  1.    **Mi Ha mód**:   
      Ha nem adja meg a **/törlése** kapcsoló, az eszköz Lehetőségelemzések módban fut, és a tartalmat a terjesztési pontról törlendő azonosítja.
   - Ebben a módban, ha az eszköz nem törli adatokat.
   - A törlésre kerülő szolgáltatásfájlok tartalommal kapcsolatos információk az eszközök naplófájlba írása, és minden lehetséges törlés megerősítéséhez nem kéri.  
      </br>   

  2. **Mód törlése**:   
    Az eszköz futtatásakor a **/törlése** delete módban fut. az eszköz kapcsoló.

     - Ebben a módban történő futtatásakor az árva, amely a megadott terjesztési ponton található tartalom található tartalomtárból a terjesztési pont eszközbejegyzés törölhető.
     -     Minden egyes fájl törlése előtt meg kell erősítenie, hogy a fájlt törölni kell.  Kiválaszthatja, **Y** Igen, **N** nem, vagy **Igen az összes** kihagyja a további utasításokat, és törölje az összes árva tartalmat.  
     </br>

Ha az eszköz vagy módban fut, akkor automatikusan létrehoz egy naplófájlt, amely tartalmazza a módot, az eszköz fut, a nevét, valamint a terjesztési pont, a dátum és idő művelet néven. A naplófájl automatikusan megnyílik, az eszköz befejezése után.

Alapértelmezés szerint a naplófájl írni a felhasználói fiók, amely az eszköz fut a számítógépen, amelyen az eszköz fut az ideiglenes mappa. Használhatja a **/log** kapcsolót, hogy a naplófájl átirányíthatók más helyre, például egy hálózati megosztásra.


## <a name="run-the-tool"></a>Futtassa az eszközt
Az eszköz futtatásához:
1. Nyisson meg egy rendszergazdai parancssort egy mappába, amelyben **ContentLibraryCleanup.exe**.  
2. Ezután adja meg egy parancssort, amely tartalmazza a kötelező parancssori kapcsolók, és nem kötelező kapcsolók szeretne használni.

**Ismert problémák** az eszköz futtatásakor a következő hiba előfordulhat, hogy adható vissza, ha a csomag vagy központi telepítés sikertelen volt, vagy folyamatban van:
-  *System.InvalidOperationException: A tartalomtár nem törlődnek azonnal mert csomag <packageID> nincs megfelelően telepítve.*

**Megkerülő megoldás:** Nincs. Az eszköz nem megbízható árva fájlok azonosítása, amikor a tartalom központi telepítése sikertelen volt, vagy folyamatban van. Ezért az eszköz nem lehetővé teszi a karbantartás tartalomhoz, hogy a probléma megoldásáig.

### <a name="command-line-switches"></a>Parancssori kapcsolók  
A következő parancssori kapcsolókat is használható bármilyen sorrendben.   

|Kapcsoló|Részletek|
|---------|-------|
|**/ delete**  |**Nem kötelező** </br> A kapcsoló használata, ha törli a tartalmat a terjesztési pontról. Mielőtt tartalom törlését kéri. </br></br> A kapcsoló nem használható, ha az eszköz naplózza az eredményeket kapcsolatban, hogy mely tartalmak törlése akkor történik meg, de nem törli a tartalmat a terjesztési pontról. </br></br> Például: ***ContentLibraryCleanup.exe /dp server1.contoso.com/DELETE*** |
| **/q**       |**Nem kötelező** </br> Erre a kapcsolóra az eszköz, amely minden használata (például a megjelenő utasításokat tartalom törlése), és automatikusan nem nyissa meg a naplófájlt csendes módban fut. </br></br> Például: ***ContentLibraryCleanup.exe /q /dp server1.contoso.com*** |
| **/dp &lt;terjesztési pont teljes Tartományneve >**  | **Kötelező** </br> Adja meg a törölni kívánt terjesztési pont teljes tartománynevét (FQDN). </br></br> Például:  ***ContentLibraryCleanup.exe /dp server1.contoso.com***|
| **/PS &lt;elsődleges hely teljesen minősített Tartományneve >**       | **Nem kötelező** karbantartásakor tartalmat a terjesztési pontról egy elsődleges helyen.</br>**Szükséges** karbantartásakor tartalmat a terjesztési pontról egy másodlagos helyen. </br></br>Az eszköz csatlakozik a szülő elsődleges hely SMS-szolgáltató lekérdezéseinek futtatásához. A lekérdezések lehetővé teszik az eszköz határozza meg, hogy mely tartalmak kell lennie a terjesztési ponton, hogy azonosíthassa a tartalom árván maradt, és el kell távolítani. A kapcsolat a fölérendelt elsődleges helyre kell megállapítani a terjesztési pont másodlagos helyen, mert a szükséges adatokat nem érhetők el közvetlenül a másodlagos helyről.</br></br> Adja meg az FQDN az elsődleges hely, amely a terjesztési pont tartozik, vagy a szülő elsődleges szülő, ha a terjesztési pont másodlagos helyen. </br></br> Például: ***ContentLibraryCleanup.exe /dp server1.contoso.com /ps siteserver1.contoso.com*** |
| **/sc &lt;elsődleges hely kódja >**  | **Nem kötelező** karbantartásakor tartalmat a terjesztési pontról egy elsődleges helyen.</br>**Szükséges** karbantartásakor tartalmat a terjesztési pontról egy másodlagos helyen. </br></br> Adja meg a helykódot az elsődleges hely, amely a terjesztési pont tartozik, vagy a szülő elsődleges hely, amikor a terjesztési pont másodlagos helyen.</br></br> Például: ***ContentLibraryCleanup.exe /dp server1.contoso.com /sc ABC*** |
| **/ log<log file directory>**       |**Nem kötelező** </br> Adja meg a helyet, ahol az eszköz ír a naplófájlba írást. Ez akkor lehet egy helyi meghajtó, vagy egy hálózati megosztás.</br></br> Ez a kapcsoló nem használható, ha a naplófájl kerül a felhasználó a számítógépen, amelyen az eszköz fut az ideiglenes mappa.</br></br> Helyi meghajtó példát: ***ContentLibraryCleanup.exe /dp server1.contoso.com log C:\Users\Administrator\Desktop*** </br></br>Példa a hálózati megosztáshoz: ***ContentLibraryCleanup.exe /dp server1.contoso.com/log \\ &lt;megosztás >\&lt; mappa >***|

