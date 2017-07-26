---

title: "Példaforgatókönyv telepítheti és figyelheti a biztonsági szoftverfrissítések |} Microsoft Docs"
description: "A példa bemutatja, hogyan szoftverfrissítések a Configuration Manager használatával telepítheti és figyelheti a biztonsági szoftverfrissítések havi kiadásokban Microsoft használja."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.technology:
- configmgr-sum
ms.service: 
ms.assetid: c32f757a-02da-43f2-b055-5cfd097d8c43
ms.translationtype: Machine Translation
ms.sourcegitcommit: e6cf8c799b5be2f7dbb6fadadddf702ec974ae45
ms.openlocfilehash: 0e6e2b3a9455bb6eda437eb1325aaaadb3d83420
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017



---
# <a name="example-scenario-for-using-system-center-configuration-manager-to-deploy-and-monitor-the-security-software-updates-released-monthly-by-microsoft"></a>Példaforgatókönyv a System Center Configuration Manager használatával történő üzembe helyezése és figyelése a Microsoft által havonta kiadott biztonsági szoftverfrissítések

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ez a témakör egy példán keresztül bemutatja hogyan használhatja szoftverfrissítéseket a System Center Configuration Managerben történő üzembe helyezése és figyelése a Microsoft havonta kiadott biztonsági szoftverfrissítések.  

 Ebben a forgatókönyvben a John a Configuration Manager rendszergazdája a Woodgrove bankban. Johnnak létre kell hozni a szoftverfrissítések telepítési stratégiáját a következő feltételek és követelmények szerint:  

-   Az aktuális szoftverfrissítések telepítése egy héttel azután történik, hogy a Microsoft közzétette a biztonsági szoftverfrissítéseket minden hónap második keddjén. Ezt az eseményt gyakran emlegetik úgy, hogy a Frissítő kedd.  

-   Megtörténik a szoftverfrissítések letöltése és előkészítése a terjesztési pontokon. Mielőtt John teljesen telepítené a termelő környezetbe a központi telepítéseket, az ügyfelek bizonyos részhalmazánál sor kerül a központi telepítés tesztelésére.  

-   Johnnak képesnek kell lenni a szoftverfrissítések megfelelőségének megfigyelésére havonta vagy évente.  

 Ez a forgatókönyv azt feltételezi, hogy már meg lett valósítva a szoftverfrissítési pont infrastruktúrája. Az alábbi információk segítségével tervezze meg, és a szoftverfrissítések konfigurálása a Configuration Managerben.  

|Folyamat|Hivatkozás|  
|-------------|---------------|  
|Tekintsük át a szoftverfrissítések főbb fogalmait.|[Szoftverfrissítések bemutatása](../understand/software-updates-introduction.md)|  
|A szoftverfrissítések megtervezése. Ez a tájékoztatás segíthet megtervezni a kapacitás kihasználását, a szoftverfrissítési pont infrastruktúrájának meghatározását, a szoftverfrissítési pont telepítését, a szinkronizálás beállításait és a szoftverfrissítések ügyfélgépi beállításait.|[Szoftverfrissítések tervezése](../plan-design/plan-for-software-updates.md)|  
|A szoftverfrissítések konfigurálása. Ez az információ segíti a hierarchiában a szoftverfrissítési pontok telepítését és konfigurálását, valamint segíti a szoftverfrissítések konfigurálását.<br /><br /> Ebben a forgatókönyvben John úgy konfigurálja, győződjön meg arról, hogy ő lekéri a legfrissebb biztonsági szoftverfrissítéseket a Microsoft minden hónap második szerdáján megtörténik a szoftverfrissítések szinkronizálásának ütemezését.|[Szoftverfrissítések szinkronizálása](../get-started/synchronize-software-updates.md)|  

 Ez a témakör következő részeiben ismerteti példa segítségével telepítheti és figyelheti a Configuration Manager biztonsági szoftverfrissítéseket a szervezetében.

##  <a name="BKMK_Step1"></a>1. lépés: Az éves megfelelőséghez egy szoftverfrissítési csoport létrehozása  
 John létrehoz egy szoftverfrissítési csoportot, amelyet az összes 2016-ben kiadott biztonsági szoftverfrissítések megfelelőségének figyeléséhez használhat. Elvégzi az alábbi táblázatban szereplő lépéseket.  

|Folyamat|Hivatkozás|  
|-------------|---------------|  
|Az a **minden szoftverfrissítés** a Configuration Manager konzolon, a John csomópont hozzáadása a 2015-ben csak biztonsági szoftverfrissítések lettek közzétéve vagy módosítva megjelenítendő feltételek, a következő feltételeknek:<br /><br /><ul><li>**Feltételek**: Közzététel vagy módosítás dátuma</li><li>**Feltétel**: Nagyobb vagy egyenlő, mint a megadott dátum<br />**Érték**: 1/1/2015</li><li>**Feltételek**: Frissítési besorolás<br />**Érték**: Biztonsági frissítések</li><li>**Feltételek**: Lejárt <br />**Érték**: Nem</li></ul>|Nem áll rendelkezésre további információ|
|John a szűrt szoftverfrissítéseket új szoftverfrissítési csoportba veszi fel a következő követelményekkel:<br /><br /><ul><li>**Név**: Megfelelőségi csoport - Microsoft biztonsági frissítések, 2015</li><li>**Leírás**: Szoftverfrissítések|[Szoftverfrissítések felvétele frissítési csoportba](add-software-updates-to-an-update-group.md)|  

##  <a name="BKMK_Step2"></a>2. lépés: Az automatikus központi telepítési szabály létrehozása az aktuális hónaphoz  
 John létrehoz egy automatikus telepítési szabályt a Microsoft által az aktuális hónapban közzétett biztonsági szoftverfrissítéseihez. Elvégzi az alábbi táblázatban szereplő lépéseket.  

|Folyamat|Hivatkozás|  
|-------------|---------------|  
|John létrehoz egy automatikus telepítési szabályt a következő követelményekkel:<br /><br /><ol><li>Az **Általános** lapon John konfigurálja a következőket:<br /> <ul><li>Itt adhatja meg **havi biztonsági frissítések** nevét.</li><li>Kiválasztja a vizsgálat a kis létszámú gyűjteményt.</li><li>Kiválasztja **hozzon létre egy új szoftverfrissítési csoport**.</li><li>Ellenőrzi, hogy **központi telepítés engedélyezése a szabály futtatása után** nincs kiválasztva.</li></ul></li><li>A **Központi telepítési beállítások** lapon John az alapértelmezett beállításokat választja.</li><li>Az a **szoftverfrissítések** lapon John konfigurálja következő tulajdonságszűrőket és keresési feltételek:<br /><ul><li>Közzététel vagy módosítás dátuma **Elmúlt 1 hónap**.</li><li>Frissítés besorolása **Biztonsági frissítések**.</li></ul></li><li>Az a **értékelési** lapon John lehetővé teszi, hogy a szabály az ütemezés szerint fusson a **második Csütörtökére** , minden **hónap**. John is ellenőrzi, hogy a szinkronizálási ütemezés futtatásra van beállítva a **második szerdáján** , minden **hónap**.</li><li>John a Központi telepítési ütemezés, a Felhasználói élmény, a Riasztások és a Letöltési beállítások oldalon is az alapértelmezett beállítást használja.</li><li>Az a **központi telepítési csomag** lapján John megadja egy új központi telepítési csomagot.</li><li>John az alapértelmezett beállítást használja a Letöltési hely és a Nyelv kiválasztása oldalon.</li></ol>|[Szoftverfrissítések automatikus központi telepítése](automatically-deploy-software-updates.md)|  

##  <a name="BKMK_Step3"></a>3. lépés: Győződjön meg arról, hogy szoftverfrissítések telepítésre készek  
 Minden hónap második csütörtökén John meggyőződik róla, hogy a szoftverfrissítések telepítésre készek. Elvégzi a következő lépéssel.  

|Folyamat|Hivatkozás|  
|-------------|---------------|  
|John meggyőződik róla, hogy a szoftverfrissítések szinkronizálása sikeresen befejeződött.|[Szoftverfrissítések szinkronizálási állapota](monitor-software-updates.md#BKMK_SUSyncStatus)|  

##  <a name="BKMK_Step4"></a>4. lépés: A szoftverfrissítési csoport telepítése  
 Miután John meggyőződik róla, hogy a szoftverfrissítések telepítésre készek, telepíti a szoftverfrissítéseket. Elvégzi az alábbi táblázatban szereplő lépéseket.  

|Folyamat|Hivatkozás|  
|-------------|---------------|  
|John az új szoftverfrissítési csoport részére létrehoz két próbatelepítést. Mindegyik központi telepítésnél figyelembe veszi a következő környezeteket:<br /><br /> **Próbatelepítés munkaállomásra**: A következőt a munkaállomás próbatelepítéséhez John veszi figyelembe:<br /><br /><ul><li>Adja meg a telepítési gyűjteményt, amelyben az a munkaállomások a telepítés ellenőrzése.</li><li>Konfigurálja a központi telepítési beállításokat, amelyek a környezetéből lévő munkaállomásokra vonatkoznak.</li></ul><br />**Próbatelepítés kiszolgálóra**: A következőt a kiszolgáló próbatelepítéséhez John veszi figyelembe:<br /><br /><ul><li>Adja meg a telepítési gyűjteményt, amelyben a kiszolgálók a telepítés ellenőrzése.</li><li>Konfigurálja a központi telepítési beállításokat, amelyek a kiszolgáló-ügyfelek a környezetében.</li></ul>|[Szoftverfrissítések központi telepítése](deploy-software-updates.md)|  
|John meggyőződik róla, hogy a próbatelepítések sikeresek voltak.|[A szoftverfrissítések központi telepítési állapota](monitor-software-updates.md#BKMK_SUDeployStatus)|  
|John a két központi telepítést frissíti azzal az új gyűjteménnyel, amelyik tartalmazza a termelésben résztvevő munkaállomásokat és kiszolgálókat.|Nem áll rendelkezésre további információ|  

##  <a name="BKMK_Step5"></a>5. lépés: A telepített szoftverfrissítések megfelelőségének figyelése  
 John figyeli a szoftverfrissítések telepítéseinek megfelelőségét. Elvégzi az alábbi táblázatban szereplő lépést.  

|Folyamat|Hivatkozás|  
|-------------|---------------|  
|John figyeli a szoftverfrissítések telepítési állapotát a Configuration Manager konzolon, és megnézi a szoftverfrissítések központi telepítési jelentéseit a konzolról elérhető.|[Szoftverfrissítések figyelése a System Center Configuration Managerben](../../sum/deploy-use/monitor-software-updates.md)|  

##  <a name="BKMK_Step6"></a>6. lépés: Havi szoftverfrissítések hozzáadása az éves frissítési csoporthoz  
 John a havi szoftverfrissítések csoportból hozzáadja a szoftverfrissítéseket az éves szoftverfrissítések csoportjához. Elvégzi az alábbi táblázatban szereplő lépést.  

|Folyamat|Hivatkozás|  
|-------------|---------------|  
|John kiválasztja a szoftverfrissítéseket a havi szoftverfrissítések csoportjából, és hozzáadja azokat ahhoz a szoftverfrissítési csoporthoz, amelyiket az éves megfelelőséghez hozott létre. Nyomon követi a szoftverfrissítés megfelelőségét, és különböző jelentéseket hoz létre a vezetőség részére.|[Szoftverfrissítések felvétele egy telepített frissítési csoportba](add-software-updates-to-an-update-group.md)|  

John sikeresen befejezte a biztonsági szoftverfrissítések havi központi telepítését. Folytatja a szoftverfrissítések megfelelőségének figyelését, és jelentéseket készít, hogy biztos legyen benne, hogy a környezetében az ügyfélgépek megfelelősége elfogadható szinten van.  

##  <a name="BKMK_MonthlyProcess"></a>Szoftverfrissítések központi telepítése ismétlődő havi folyamata  
 Az első olyan hónap után, amikor John telepítette a szoftverfrissítéseket, a következőkben a harmadiktól a hatodik lépésig végzi a Microsoft biztonsági szoftverfrissítéseinek havi telepítését.  

