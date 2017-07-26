---
title: "Válassza ki a felderítési módszerek a Configuration Manager |} Microsoft Docs"
description: "Tekintse át a szempontok használandó módszerek és mely helyeken futtathatók."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 127ce713-d085-430f-ac7b-2701637fe126
caps.latest.revision: 9
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f72317cefab5ce8cad13b3120c3c93c856fa40b7
ms.openlocfilehash: 4b6be888be2ad6c1f5e7c0be33d9830bb870114e
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="select-discovery-methods-to-use-for-system-center-configuration-manager"></a>Select discovery methods to use for System Center Configuration Manager (A System Center Configuration Managerrel használandó felderítési módok kiválasztása)

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Sikeresen és hatékony használata a System Center Configuration Manager felderítési, amelyeket érdemes figyelembe venni használandó módszerek és mely helyeken futtatni azokat.  

 Mivel a felderítés igen nagy mennyiségű hálózati adatforgalmat generálhat, és a létrejövő felderítési adatrekordot (DDR) jelentős CPU-erőforrásokat használ feldolgozása során, használja a csak azokat a felderítési módszereket, amelyekre szüksége van céljai eléréséhez. Előfordulhat, hogy a csak egy-két felderítési módszer használatával indítsa el, és később engedélyez további módszereket is a mélyebb felderítéshez szabályozott módon. A jelen témakörben található információk segítségével kérdésekre vonatkozó döntések meghozatalában.  

 A más felderítési módszerekkel kapcsolatos információkért lásd: [kapcsolatos felderítési módszerek a System Center Configuration Manager](../../../../core/servers/deploy/configure/about-discovery-methods.md).  

## <a name="select-methods-to-discover-different-things"></a>A különböző dolgok felderítésére módszerek kijelölése  
 Lehetséges a Configuration Manager-ügyfélszámítógépek vagy felhasználói erőforrások felderítéséhez, engedélyeznie kell a megfelelő felderítési módszereket. Használhatja a felderítési módszerek különböző kombinációival különböző erőforrások találhatók meg, és ezeket az erőforrásokat kapcsolatos további információk felderítésére. A használt felderítési módszerek határozzák meg, milyen típusú erőforrásokat fog észlelni, és melyik Configuration Manager szolgáltatások és az ügynökök fogja használni a felderítési folyamat során. Akkor is, amely felderítené az erőforrások adatait típusának meghatározása.  

### <a name="discover-computers"></a>Számítógépek felderítése   
Ha szeretne olyan számítógépek felderítése, **Active Directory-Rendszerfelderítés** vagy **hálózatfelderítés**.  

 Ha szeretné felderíteni azokat az erőforrásokat, amely a Configuration Manager-ügyfél telepítése az ügyfélleküldéses telepítés használata előtt, például előfordulhat, hogy az Active Directory-Rendszerfelderítés futtatja. Ezzel a módszerrel, nem csupán az erőforrást deríti fel, de is alapvető információk még akkor is, kiegészítő információk felderítéséhez az Active Directory tartományi szolgáltatásokból. Ezek az információk hasznosak lehetnek, felépítése bonyolult lekérdezéseket vagy gyűjteményeket szeretne a hozzárendelés az ügyfél beállításai vagy központi tartalomterjesztés céljából.

Másik lehetőségként volt a hálózatfelderítést, és a beállítások segítségével az operációs rendszer (a későbbi ügyfélleküldéses telepítéshez szükséges) erőforrások felderítéséhez. A hálózatfelderítés a hálózati topológiáról, amelyek nem szerezhetők más felderítési módszerekkel kapcsolatos információkat biztosít. Ez a módszer, azonban biztosít semmilyen információt az Active Directory-környezetbe.

 Szerepel továbbá a hívott metódus **a Szívveréses felderítés**. Csak a Szívveréses felderítés használatával kényszerítheti a leküldéses ügyféltelepítés eltérő módszerrel telepített ügyfelek lehetőség. Azonban más felderítési módszerekkel szemben a Szívveréses felderítés nélküli számítógépek felderítésére, amelyeken nincs aktív Configuration Manager-ügyfél. Információ egy meglévő adatbázisrekord karbantartása, nem pedig a rekord alapinformációinak biztosítása kell szánt korlátozott számú ad vissza. A Szívveréses felderítés által kínált információk nem feltétlenül elégségesek összetettebb lekérdezések vagy gyűjtemények összeállításához.  

 Ha **Active Directory-Csoportfelderítés** a egy adott csoport tagságának felderítésére, is felderítheti, korlátozott rendszer vagy a számítógép adatait. Ez nem helyettesíti a számítógépek teljes felderítés, de alapvető információkat nyújtanak. Ez az információ nem elegendő az ügyfélleküldéses telepítés.  

### <a name="discover-users"></a>Felhasználók felderítése   
Felhasználói információk felderítéséhez, használhatja **Active Directory-Felhasználófelderítés**. Active Directory-Rendszerfelderítés hasonló, ez a módszer deríti fel felhasználókat az Active Directoryból. Ez magában foglalja az alapszintű információk mellett kiterjesztett Active Directory adataival. Összetett lekérdezéseket és gyűjteményeket hasonló a számítógépek létrehozásához használhatja ezt az információt.  

### <a name="discover-group-information"></a>Csoportinformációk felderítése   
Amikor csoportokkal vagy csoporttagsággal kapcsolatos információk felderítésére, **Active Directory-Csoportfelderítés**. Ez a felderítési módszer hoz létre a biztonsági csoportok erőforrásrekordokat.  

 Ezt a módszert egy adott Active Directory-csoportot, illetve annak beágyazott csoportjai csoporton belüli csoport tagjainak azonosítása kereséséhez. Ezzel az eljárással emellett Active Directory-helyeken kereshet csoportokat, illetve rekurzív módon keresheti meg az adott hely összes gyermektárolóját az Active Directory Domain Servicesben.  

 Ez a felderítési módszer a terjesztési csoportok tagságát is kereshet. -Felhasználók és számítógépek csoportkapcsolatai feltérképezhetők.  

 Amikor felderít egy csoportot, a tagok korlátozott információkat is kap. Ez nem helyettesíti az Active Directory rendszer-felhasználói felderítési módszer alkalmazása, azonban. Jellemzően nem elegendők bonyolultabb lekérdezések vagy gyűjtemények létrehozása, vagy a leküldéses ügyféltelepítés alapjául szolgálnak.  

### <a name="discover-infrastructure"></a>Infrastruktúra felderítése   
Használhatja a hálózati infrastruktúra felderítésére két módszer **Active Directory-Erdőfelderítés** és **hálózatfelderítés**.  

 Használja az Active Directory-Erdőfelderítési funkciójával hajthat végre keresést az Active Directory-erdő alhálózatokat és Active Directory-helykonfigurációkkal kapcsolatos információkat. Ezeket a konfigurációkat felderítést követően automatikusan bevihetők a Configuration Managerbe határhelyként.  

 Ha azt szeretné, a hálózati topológia felderítését, használja a hálózatfelderítést. Más felderítési módszerek információk kapcsolódik az Active Directory tartományi szolgáltatásokban, és képes azonosítani az ügyfél aktuális hálózati helyét adja vissza, amíg nem biztosítanak infrastrukturális információkat az alhálózatok és a hálózat útválasztó-topológiája alapján.  

##  <a name="bkmk_shared"></a>Felderítési adatok van osztva a helyek között  
 Miután a Configuration Manager adatbázishoz felvette a felderítési adatokat, ezeket gyorsan megosztja az összes hely között a hierarchiában. Mert jellemzően nincs felderítése a hierarchiában több helyen ugyanazokat az információkat az előnye, fontolja meg az egyes felderítési módszereket, amelyekkel egy helyről futtassa, egyetlen példányát beállítását. Tanácsos ugyanazon módszer több példányát futtatni különböző helyeken helyett ehhez.  

 Azonban néhány környezetben hasznos lehet ugyanazt a felderítési módszert több helyen futtatni egy különálló konfigurációval és ütemezéssel rendelkező hozzárendelni. Például a hálózatfelderítés használatakor érdemes át tudja irányítani a helyi hálózati helyett WAN-KAPCSOLATON keresztüli összes hálózati hely felderítésének megkezdése felderítéséhez a helyekhez.

Ha több példányát futtatni különböző helyeken ugyanazon felderítési módszerek konfigurálja, alaposan tervezze minden hely konfigurációját. El szeretné kerülni, nehogy két vagy több hely ugyanazokat az erőforrásokat a hálózatról vagy az Active Directory felderítését. Ez további hálózati sávszélességet, és hozzon létre duplikált DDR.

A következő táblázat ismerteti, hogy mely helyeken állíthat be az egyes felderítési módszereket.  

|A felderítési módszer|Támogatott helyek|  
|----------------------|-------------------------|  
|Active Directory-erdőfelderítés|Központi adminisztrációs hely<br /><br /> Elsődleges hely|  
|Active Directory-csoportfelderítés|Elsődleges hely|  
|Active Directory-rendszerfelderítés|Elsődleges hely|  
|Active Directory-felhasználófelderítés|Elsődleges hely|  
|A Szívveréses felderítés<sup>1</sup>|Elsődleges hely|  
|Hálózatfelderítés|Elsődleges hely<br /><br /> Másodlagos hely|  

 <sup>1</sup> a másodlagos helyek nem konfigurálhatnak Szívveréses felderítést, de Szívveréses adatfelderítési Rekordokat fogadhatnak ügyfél.  

 Amikor másodlagos helyek hálózatfelderítést, vagy Szívveréses adatfelderítési, azok átvitele az adatfelderítési Rekordokat fájl alapú replikációként a fölérendelt elsődleges helyre. Ennek oka az, csak az elsődleges helyek és a központi adminisztrációs helyek DDR tud feldolgozni. Adatfelderítési rekordok feldolgozásával kapcsolatos további információkért lásd: [tudnivalók az adatfelderítési rekordokról](../../../../core/servers/deploy/configure/run-discovery.md#BKMK_DDRs).  

## <a name="considerations-for-different-discovery-methods"></a>Más felderítési módszerek szempontjai  
 Mivel minden egyes hely kiszolgáló- és hálózati környezet különböző, célszerű korlátozni a felderítés kezdeti konfigurációi. Szorosan figyelheti egyes Helykiszolgálók képesek-e feldolgozni a létrehozott felderítési adatok.  

Ha egy **Active Directory** rendszerek, felhasználók vagy csoportok egyik felderítési módszere:  

-   Futtassa a felderítést, amely a tartományvezérlők gyors hálózati kapcsolattal rendelkezik egy helyen.  

-   Fontolja meg az Active Directory replikációs topológiájára, hogy felderítési férhetnek hozzá a legújabb információkat.  

-   Fontolja meg a felderítési konfiguráció hatókörét, és korlátozza a felderítés csak az Active Directory-helyek és-csoportokat, amelyek fel kell derítenie.  

Ha **hálózatfelderítés**:  

-   Korlátozott kezdeti konfigurációt használatával a hálózati topográfia megállapításához.  

-   A hálózati topográfia azonosítása után állítsa be a hálózatfelderítés az adott helyeken, amelyek központiak a részletesebben felderíteni kívánt hálózati területek fusson.  

Mivel **a Szívveréses felderítés** nem fut egy megadott hely nem kell figyelembe venni a felderítés futtatási helyének meghatározása az általános tervezésnél.  

##  <a name="bkmk_best"></a>Ajánlott eljárások a felderítéshez  
A felderítés a legjobb eredmény érdekében a következőket javasoljuk:

 - **Futtassa az Active Directory-Csoportfelderítés előtt futtassa az Active Directory-Rendszerfelderítést és az Active Directory-Felhasználófelderítés.**  

 Ha az Active Directory-Csoportfelderítés korábban felderítetlen felhasználó vagy számítógép csoport tagjaként, megkísérli felderíteni a felhasználóra vagy számítógépre vonatkozó alapvető adatokat. Mivel az Active Directory-Csoportfelderítés nincs optimalizálva az ilyen típusú feladatra, ez a folyamat okozhat végre. Emellett az Active Directory-Csoportfelderítés csak az alapvető adatokat a felhasználók és számítógépek felderítésére szolgál, és nem hoz létre egy teljes felhasználói vagy számítógép-felderítési adatrekordot azonosítja. Active Directory-Rendszerfelderítést és az Active Directory-Felhasználófelderítés futtatásakor az egyes objektumtípusoknál további Active Directory-attribútumok érhetők el. Ennek eredményeképpen az Active Directory-Csoportfelderítés sokkal hatékonyabban.  

- **Active Directory-Csoportfelderítés beállításakor csak adja meg a csoportokat, amelyek a Configuration Managerrel együtt használni.**  

 A által használt erőforrások Active Directory-Csoportfelderítés, hogy szabályozni adja meg, csak azokat a csoportokat, amelyek a Configuration Managerrel együtt használni. Ennek oka az, az Active Directory-Csoportfelderítés rekurzív módon keres a felhasználók, számítógépek és beágyazott csoportok számára felderített egyes csoportokban. Az egyes beágyazott csoportok keresése bontsa ki az Active Directory-Csoportfelderítés hatókörét, és csökkentheti a teljesítményt. Emellett a változásfelderítés az Active Directory-Csoportfelderítés beállításakor a felderítési módszer módosítások minden egyes csoportnál figyeli. Ez tovább csökkenti a teljesítményt, ha a metódus szükségtelen csoportokban kell keresnie.  

- **Felderítési módszerek közötti teljes felderítés és a változásfelderítés gyakoribb időtartama hosszabb időköz beállítása.**  

 Mivel a változásfelderítés a teljes felderítési ciklus-nál kevesebb erőforrást használ, és képes azonosítani az új vagy megváltozott erőforrásokat az Active Directoryban, csökkentheti a gyakoriságát, a teljes felderítési ciklusok hetente (vagy kevesebb). Változásfelderítés az Active Directory-Rendszerfelderítés, Active Directory-Felhasználófelderítés és Active Directory-Csoportfelderítés szinte valamennyi változását az Active Directory-objektumok azonosítja, és karbantarthatja erőforrások pontos felderítési adatokat.  

- **Futtassa az Active Directory felderítési módszerei egy elsődleges helyen, amelynek hálózati helye a legközelebb az Active Directory tartományvezérlőjéhez van.**  

 Az Active Directory-felderítés, annak érdemes futtatni egy elsődleges hely felderítése a teljesítmény javítása érdekében, amely a tartományvezérlők gyors hálózati kapcsolattal rendelkezik. Ha több helyen futtatja az Active Directory ugyanazon felderítési módszer, beállítása egyes felderítési módszerek átfedés elkerülése érdekében. Eltérően a Configuration Manager verziói túli felderítési adatok meg vannak osztva helyek között. Ezért nincs szükség ugyanazokat az adatokat több helyen felderíteni. További információkért lásd: [felderítési adatok meg vannak osztva a helyek közötti](../../../../core/servers/deploy/configure/select-discovery-methods-to-use.md#bkmk_shared).  

- **Active Directory-Erdőfelderítést csak egy helyről futtassa, ha azt tervezi, hogy automatikusan határokat hozzon létre a felderítési adatokat.**  

 Ha az Active Directory-Erdőfelderítés a hierarchia egynél több helyen futtatja, célszerű csak akkor engedélyezze a határok automatikus létrehozásának egyetlen helyen beállítások. Ennek oka az, amikor az Active Directory-Erdőfelderítés az egyes helyeken fut, és határokat hoz létre, a Configuration Manager egyetlen objektumba nem tudja egyesíteni ezeket a határokat. Amikor az Active Directory-Erdőfelderítés több helyen hozzon létre automatikusan határokat konfigurál, az eredmény lehet ismétlődő határ objektumokat kaphat a Configuration Manager konzolon.  

