---
title: "IOS és Mac OS X rendszerű eszközök Intune-nal felügyelt konfigurációelemek létrehozása |} Microsoft Docs"
description: "A System Center Configuration Manager iOS és Mac OS X-konfigurációs elem használatával az iOS és Mac OS X rendszerű eszközök beállításait."
ms.custom: na
ms.date: 03/28/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 613a48ac-c55d-4c4a-94ea-d3747a1b10cb
caps.latest.revision: 15
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 6e2cb628217598480973d4f728a9e0a7cd5873e7
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-create-configuration-items-for-ios-and-mac-os-x-devices-managed-with-intune"></a>Az Intune-nal felügyelt iOS és Mac OS X rendszerű eszközök konfigurációelemek létrehozása
A System Center Configuration Manager használata **iOS és Mac OS X** konfigurációelemet használva felügyelheti az iOS és Mac OS X rendszerű eszközökhöz a Microsoft Intune vagy a helyszínen felügyelt regisztrált a Configuration Manager által beállításait.  
  
### <a name="to-create-an-ios-and-mac-os-x-configuration-item"></a>iOS és Mac OS X típusú konfigurációelem létrehozása  
  
1.  Kattintson a Configuration Manager konzolon **eszközök és megfelelőség**.  
  
2.  Az **Eszközök és megfelelőség** munkaterületen bontsa ki a **Megfelelőségi beállítások**csomópontot, majd kattintson a **Konfigurációelemek**lehetőségre.  
  
3.  A **Kezdőlap** lap **Létrehozás** csoportjában kattintson a **Konfigurációelem létrehozása**elemre.  
  
4.  A **Konfigurációelem létrehozása varázsló** **Általános** lapján adja meg a konfigurációelem nevét, és nem kötelezően leírást is megadhat hozzá.  
  
5.  A **Határozza meg a létrehozandó konfigurációelem típusát** csoportban válassza az **iOS és Mac OS X** elemet.  
  
6.  Kattintson a **kategóriák** Ha létrehozni és hozzárendelni kategóriákat szeretne kereséséhez és szűréséhez konfigurációs elemek a Configuration Manager konzolon.  
  
7.  A varázsló **Támogatott platformok** lapján jelölje ki azokat az iOS- és Mac OS X-platformokat, amelyek kiértékelik majd a konfigurációelemet.  
  
8.  A varázsló **Eszközbeállítások** lapján jelölje ki a konfigurálni kívánt beállításcsoportot. Tekintse meg jelen témakör [Útmutató az iOS- és Mac OS X-eszközökhöz készült konfigurációelemek beállításaihoz](#BKMK_Setref) című szakaszát, majd kattintson a **Tovább** gombra.  
  
    > [!TIP]  
    >  Ha nem találja a kívánt beállítást, jelölje be a **További olyan beállítások konfigurálása, amelyek nem találhatók meg az alapértelmezett beállítási csoportokban jelölőnégyzetet**.  
  
9. Minden egyes lapon adja meg a szükséges beállításokat, illetve azt, hogy szeretné-e őket kijavítani, ha nem felelnek meg az eszközök követelményeinek (ha ez a lehetőség támogatott).  
  
10. A beállításcsoportokban azt is megadhatja, hogy a nem megfelelőnek ítélt konfigurációelemek esetén a rendszer milyen súlyossági szintről küldjön Önnek értesítést:  
  
    -   **Nincs** – a megfelelőségi szabálynak eleget nem tevő eszközök nem kerül a hiba súlyossága a Configuration Manager-jelentések.  
  
    -   **Információ** – a megfelelőségi szabálynak eleget nem tevő eszközök adják meg a hiba súlyosságát a **információk** Configuration Manager jelentések.  
  
    -   **Figyelmeztetés** – a megfelelőségi szabálynak eleget nem tevő eszközök adják meg a hiba súlyosságát a **figyelmeztetés** Configuration Manager jelentések.  
  
    -   **Kritikus** – a megfelelőségi szabálynak eleget nem tevő eszközök adják meg a hiba súlyosságát a **kritikus** a Configuration Manager jelentésekben.  
  
    -   **Kritikus eseménnyel** – a megfelelőségi szabálynak eleget nem tevő eszközök adják meg a hiba súlyosságát a **kritikus** a Configuration Manager jelentésekben. Ezt a súlyossági szintet az alkalmazás eseménynaplója is rögzíti Windows-eseményként.  
  
11. A varázsló **Platform alkalmazhatósága** lapján áttekintheti azokat a beállításokat, amelyek nem kompatibilisek a korábban kiválasztott támogatott platformokkal. Visszaléphet, hogy eltávolítsa ezeket a beállításokat, vagy folytathatja a műveletet.  
  
    > [!TIP]  
    >  A nem támogatott beállítások megfelelőségét a rendszer nem ellenőrzi.  
  
12. Fejezze be a varázslót.  
  
 Az új konfigurációelemet az **Eszközök és megfelelőség** munkaterület **Konfigurációelemek** csomópontjában tekintheti meg.  
  
##  <a name="ios-and-mac-os-x-configuration-item-settings-reference"></a>Útmutató az iOS és Mac OS X típusú konfigurációelemek beállításaihoz  
  
###  <a name="password"></a>Jelszó  
  
|Beállítás neve|Részletek|  
|------------------|-------------|  
|**Jelszó igénylése mobileszközökön**|Jelszó kérése a támogatott eszközökön.|  
|**Jelszó minimális hossza (karakter)**|A jelszó minimális hossza.|  
|**Jelszó lejárati ideje napokban**|Azon napok száma, amely után a jelszót kötelező megváltoztatni.|  
|**Megjegyzett jelszavak száma**|Megakadályozza a korábban használt jelszavak használatát.|  
|**Sikertelen bejelentkezési próbálkozások száma az eszköz törlése előtt**|A megadott számú sikertelen bejelentkezési kísérlet után törli az eszközt.<br /><br /> (Csak iOS)|  
|**Jelszó bonyolultsága**|Kiválasztja, hogy megadhat-e PIN-kódot (pl. „1234”), vagy erős jelszót kell megadnia.| 
|**Egyszerű jelszavak engedélyezése**|Engedélyezze az egyszerű jelszavak, például **0000** és **1234**.|
|**Zárolás feloldása ujjlenyomattal**|Az eszköz zárolásának feloldásához ujjlenyomat használatának engedélyezése.|
|**PIN-kód módosítása** (csak felügyelt)|Engedélyezi az eszköz jelszavának hozzáadott, módosítani vagy eltávolítani.|
  
###  <a name="device"></a>Eszköz  
 Ezek a beállítások az iOS- és a Mac OS X-eszközökre egyaránt érvényesek.  
  
|Beállítás neve|Részletek|  
|------------------|-------------|  
|**Game centerbeli barátok hozzáadása**|Barátok hozzáadásának engedélyezése a Game Center alkalmazásban.|
|**Hangtárcsázás**|A hangtárcsázási funkció engedélyezése az eszközön.|  
|**Beszédfelismerési asszisztens**|A hangvezérelt alkalmazások (pl. Siri) használatának engedélyezése.|  
|**Beszédfelismerési asszisztens zárolt állapotban**|A hangvezérelt alkalmazások használatának engedélyezése, ha az eszköz zárolva van.|  
|**Képernyőfelvétel**|Képernyőképek készítésének engedélyezése az eszköz kijelzőjéről.|  
|**Videobeszélgetési ügyfél**|A videocsevegésre alkalmas alkalmazások (pl. FaceTime) használatának engedélyezése.|  
|**Több résztvevős játék**|Engedélyezi, hogy az interneten keresztül más játékosokkal együtt játsszon.|  
|**Személyespénztárca-szoftver zárolt állapotban**|A személyespénztárca-szoftverek (pl. Passbook) használatának engedélyezése.|  
|**Diagnosztikai adatok beküldése**|Engedélyezi az alkalmazások naplófájljainak elküldését.|  
|**Műveletközpont értesítéseinek**|A felhasználó hozzáférhessen az értesítések nézetéhez az eszköz zárolásának feloldása nélkül.|
|**Apple zene** (csak felügyelt)|Az Apple zene alkalmazás használatának engedélyezése.|
|**Podcastok** (csak felügyelt)|A podcastok alkalmazás használatának engedélyezése.|
|**Üzenetek alkalmazás** (csak felügyelt)|A szöveges üzenetek küldéséhez az üzenetek alkalmazás használatának engedélyezése.|
|**Módosítás tapéta** (csak felügyelt)|Lehetővé teszi a felhasználó számára az eszköz tapéta módosítását.|
|**Word definition keresési** (csak felügyelt)|Az iOS funkciója, amely lehetővé teszi, hogy jelöljön ki egy szót, és keressen meg definition engedélyezése.|
|**Körkörös észlelését párosított Apple órák**|Ha engedélyezve van, az Apple Watch nem jeleníti meg értesítések nem használt alatt.|
|**A Siri Profanitás szűrő** (csak felügyelt)|Megakadályozza, hogy a Siri Diktálás vagy profán nyelvi beszélünk.|
|**Eszköz neve módosítása** (csak felügyelt)|Engedélyezi a felhasználó az eszköz nevének módosításához.|
|**Diagnosztika küldésének beállításainak módosítása** (csak felügyelt)|Engedélyezi vagy letiltja az Apple-nek diagnosztikai adatokat küldjön az eszközt.|
|**Game centerbeli** (csak felügyelt)|A Game Center alkalmazás használatának engedélyezése.|
|**iTunes rádió** (csak felügyelt)|Az iTunes rádió alkalmazás használatának engedélyezése.|
|**Apple hírek** (csak felügyelt)|Az Apple hírek alkalmazás használatának engedélyezése.|
|**Apple Watch párosítás** (csak felügyelt)|Engedélyezi, hogy az eszköz egy Apple Watch párosítani.|
|**Automatikus javítási** (csak felügyelt)|Lehetővé teszi, hogy az eszköz automatikusan javítsa ki a hibás szó.|
|**Bluetooth-módosítás** (csak felügyelt)|Lehetővé teszi, hogy a felhasználó számára az eszköz Bluetooth-beállítások módosítását.|
|**Alkalmazás mobiladatátvitel-használati beállításai vált** (csak felügyelt)|Engedélyezi a felhasználó számára meghatározzák melyik alkalmazások bonyolíthatnak le mobilhálózati adatforgalmat.|
|**Azok a billentyűparancsok** (csak felügyelt)|Billentyűparancsok használatának engedélyezése.|
|**A prediktív billentyűzetek** (csak felügyelt)|Előfordulhat, hogy szeretné, hogy a felhasználó szavak javasolja prediktív billentyűzetek használatának engedélyezése.|
|**Azok a helyesírás-ellenőrzési** (csak felügyelt)|Lehetővé teszi, hogy az eszköz helyesírás-ellenőrző.|
|**Értesítési beállításainak módosítása** (csak felügyelt)|Lehetővé teszi a felhasználó számára az eszköz az értesítési beállításainak módosítását.|
|**A Spotlight kereső internetes eredmények visszaadásának** (csak felügyelt)|Lehetővé teszik a Spotlight kereső csatlakozzon az internethez, hogy további találatokat adjon vissza.|
|**Használja az internetről lekérdezés felhasználó által létrehozott tartalom Siri** (csak felügyelt)|Engedélyezése Siri kérdések megválaszolása webhelyek elérésére.|

  
###  <a name="store"></a>Áruház  
 Ezek a beállítások csak iOS-eszközökre vonatkoznak.  
  
|Beállítás neve|Részletek|  
|------------------|-------------|  
|**Alkalmazás-áruház**|Hozzáférés engedélyezése az alkalmazásáruházhoz az eszközön.|  
|**Adjon meg egy jelszót az alkalmazásáruházhoz való hozzáféréshez**|A felhasználóknak meg kell adniuk egy jelszót az alkalmazásáruházhoz való hozzáféréshez.|  
|**Alkalmazáson belüli vásárlások**|Az alkalmazásokon belüli vásárlás engedélyezése a felhasználók számára.|
|**Apple Configuratort és iTunes csak alkalmazások telepítése** (csak felügyelt)|Engedélyezheti vagy letilthatja az App Store áruházból származó eszköz adniuk a kezőképernyőjükhöz. Felhasználók továbbra is használhatja iTunes vagy az Apple Configurator eszközzel telepítéséhez és alkalmazások frissítése.|
|**Az iBooks áruház elérésének** (csak felügyelt)|Engedélyezi a felhasználó számára az iBook áruházban könyveket böngésszen és vásároljon.|
|**Automatikus app letöltések** (csak felügyelt)|Ez az eszköz automatikusan letölti egyéb eszközein futó vásárolt alkalmazások engedélyezése Ez a beállítás nincs hatással az alkalmazások frissítése.|

  
###  <a name="browser"></a>Böngésző  
 Ezek a beállítások csak iOS-eszközökre vonatkoznak.  
  
|Beállítás neve|Részletek|  
|------------------|-------------|  
|**Alapértelmezett böngésző**|A felhasználók módosíthatják az alapértelmezett böngészőt.|  
|**Automatikus kitöltés**|A felhasználók módosíthatják a böngésző automatikus kiegészítési funkciójának beállításait.|  
|**Active scripting**|A böngésző futtathat parancsfájlokat (pl. Active X-parancsfájlok).|  
|**Előugróablak-blokkoló**|A böngésző előugróablak-blokkolójának engedélyezése vagy letiltása.|  
|**Cookie-k**|A cookie-k mentésének engedélyezése az eszközön.|  
|**Hamis figyelmeztetés**|A potenciálisan rosszindulatú webhelyekről szóló figyelmeztetések engedélyezése vagy letiltása.|  
  
###  <a name="content-rating"></a>Tartalom minősítése  
 Ezek a beállítások csak iOS-eszközökre vonatkoznak.  
  
|Beállítás neve|Részletek|  
|------------------|-------------|  
|**Durva tartalom a médiaáruházban**|Megadja, hogy engedélyezni szeretné-e a hozzáférést a felnőtt tartalmakhoz az alkalmazásáruházban.|  
|**Minősítési régió**|Megadja azt az országot, amely esetében alkalmazni szeretné a minősítési korlátozásokat.|  
|**Film minősítése**|Megadja a filmes tartalmak engedélyezni kívánt maximális minősítését.|  
|**Televízió-műsor minősítése**|Megadja a tv-műsoros tartalmak engedélyezni kívánt maximális minősítését.|  
|**Alkalmazás minősítése**|Megadja az alkalmazástartalmak engedélyezni kívánt maximális minősítését.| 
|**Az iBook áruházban "Erotika" ellátott lévő tartalmak** (csak felügyelt)|A felhasználó számára "az erotikus tartalom" kategóriába könyvek letöltésének engedélyezése.| 
  
> [!NOTE]  
>  A választható minősítések a kiválasztott **Minősítési régiótól** függően változhatnak.  
  
###  <a name="cloud"></a>Felhő  
 Ezek a beállítások csak iOS-eszközökre vonatkoznak.  
  
|Beállítás neve|Részletek|  
|------------------|-------------|  
|**Felhőbeli biztonsági mentését**|A felhőszolgáltatásokra (pl. iCloud) végzett biztonsági mentés engedélyezése.|  
|**Biztonsági másolat titkosításának engedélyezése**|A felhőszolgáltatásokra végzett biztonsági mentés titkosításának engedélyezése.|  
|**Dokumentumszinkronizálás**|Dokumentumok egy felhőszolgáltatásra történő szinkronizálásának engedélyezése.|  
|**Fényképszinkronizálás**|Fényképek egy felhőszolgáltatásra történő szinkronizálásának engedélyezése.| 
|**icloud szolgáltatásba fényképe oszlopot könyvtár**|Ha beállítása **nem**, letilthatja az icloud tárhelyére végzett mentésének fénykép könyvtár, amely lehetővé teszi, hogy a felhasználók a felhőben tárolt fotóit és videóit. Bármely fényképek, az eszközre az icloud szolgáltatásba fényképe oszlopot könyvtár nem teljesen le az eszközről törlődnek, amennyiben az értéke **nem**.|
|**Fénykép megosztása icloudba szinkronizálásának engedélyezése**|Beállítása **nem** letiltása az icloud tárhelyére végzett fénykép megosztása az eszközön.|
|**Tevékenységek más eszközön való folytatáshoz handoff számára**|A felhasználó továbbra is, amely egy másik iOS-eszköz vagy a Mac OS X rendszerű gépen elkezdett munkát.|
|**Icloudba történő szinkronizálásának engedélyezése felügyelt alkalmazásokból való szinkronizálja az adatokat**|Lehetővé teszi az alkalmazások adatokat szinkronizáljanak a felhasználó iCloud-fiókjával kezelése az Intune-nal.|

  
###  <a name="security"></a>Biztonság  
 Ezek a beállítások csak iOS-eszközökre vonatkoznak.  
  
|Beállítás neve|Részletek|  
|------------------|-------------|  
|**Fényképezőgép**|Engedélyezi az eszköz kamerájának használatát.| 
|**Új vállalati alkalmazás szerzők megbízhatóság**|Lehetővé teszi, hogy a felhasználó kiválaszthatja a nem az alkalmazás-áruházból letöltött alkalmazások megbízhatónak.| 
  
###  <a name="roaming"></a>Barangolás  
 Ezek a beállítások csak iOS-eszközökre vonatkoznak.  
  
|Beállítás neve|Részletek|  
|------------------|-------------|  
|**Hangroaming**|Hanghívások engedélyezése barangolás közben.|  
|**Automatikus szinkronizálás barangolás közben**|Az eszköz automatikus szinkronizálásának engedélyezése barangolás közben.|  
|**Adatroaming**|Hálózatok közötti barangolás engedélyezése adatok elérése közben.|  
  
###  <a name="system-security"></a>Rendszerbiztonság  
 Ezek a beállítások csak iOS-eszközökre vonatkoznak.  
  
|Beállítás neve|Részletek|  
|------------------|-------------|  
|**Nem megbízható TLS tanúsítványokat elfogadó felhasználó**|Ha **Engedélyezve** van, lehetővé teszi a felhasználó számára, hogy elfogadja ezeket a tanúsítványokat. Ha **Tiltva** van, automatikusan elutasítja a nem megbízható tanúsítványokat.|
|**(Csak felügyelt módban). az aktiválási zár engedélyezése**|Ezzel a beállítással engedélyezheti az iOS aktiválási zárat a **felügyelt** iOS-eszközökön. További információk az Aktiválási zárról: [iOS aktiválási zár a System Center Configuration Managerrel](../../mdm/deploy-use/manage-ios-activation-lock.md).
|**Zárolási képernyő vezérlőközpontja**|Itt adható meg, hogy a Vezérlőközpont alkalmazás elérhető legyen-e, amikor az eszköz zárolva van.|  
|**A zárolási képernyő értesítési nézete**|Itt adható meg, hogy megtekinthetők-e az értesítések, amikor az eszköz zárolva van.|  
|**Zárolási képernyő mai nézete**|Itt adható meg, hogy látható legyen-e a Ma nézet, amikor az eszköz zárolva van.|  
|**Módosítsa a fiókbeállításokat** (csak felügyelt)|Lehetővé teszi a felhasználó megváltoztassa a fiók beállításait, például e-mail-konfigurációkat.|
|**A barátok alkalmazás beállításai módosításokat** (csak felügyelt)|Lehetővé teszi a felhasználó megváltoztassa a barátok alkalmazás beállításait.|
|**Az egy iOS-eszközzel párosítható eszközök szabályozásának való használatát a gazdapárosítási** (csak felügyelt)|Engedélyezése a gazdapárosítási funkcióval a rendszergazda szabályozhatja, hogy mely az iOS-eszközök párosítható eszközök.|
|**Összes tartalom és beállítás törlésére** (csak felügyelt)|Engedélyezi a felhasználó törölje az összes tartalmat és beállítást az eszközön beállítás használatához.|
|**Állítson be korlátozásokat, eszközön** (csak felügyelt)|Engedélyezi a felhasználó eszközkorlátozásokat (szülői felügyeletet) konfigurálása az eszközön.|
|**Konfigurációs profilok és tanúsítványok telepítésének** (csak felügyelt)|A konfigurációs profilok és tanúsítványok telepítésének engedélyezése.|
|**Kérelmek kimenő AirPlay jelszavát**|Párosítási jelszó kérése, amikor a felhasználó az airplay segítségével tartalmat kíván közvetíteni egyéb Apple-eszközökre.|
  
###  <a name="data-protection"></a>Adatvédelem  
 Ezek a beállítások csak iOS-eszközökre vonatkoznak.  
  
|Beállítás neve|Részletek|  
|------------------|-------------|  
|**Nem felügyelt egyéb alkalmazásokban felügyelt alkalmazások dokumentumainak megnyitása**|A Configuration Manager alkalmazáskezelési házirendjei által felügyelt alkalmazásokból való használatra.|  
|**Egyéb, felügyelt alkalmazásokban nem felügyelt alkalmazások dokumentumainak megnyitása**|A Configuration Manager alkalmazáskezelési házirendjei által felügyelt alkalmazásokból való használatra.| 
|**AirDrop tekinti egy nem felügyelt cél** (csak felügyelt)|Leállítja a felügyelt alkalmazások adatokat küldhetnének. Airdrop.|
|**AirDrop** (csak felügyelt)|Az AirDrop funkció közeli eszközökkel való használatának engedélyezése.|
  
###  <a name="compliant-and-noncompliant-apps-ios"></a>Megfelelő és nem megfelelő alkalmazások (iOS)  
 Egy listában megadhatja a vállalatban megfelelőnek vagy nem megfelelőnek ítélt iOS-alkalmazásokat. Ezután jelentések használatával megjeleníthetők azok az eszközök, amelyekre nem megfelelő alkalmazásokat telepítettek, valamint az a felhasználó, aki a telepítést végezte.  
  
 Egyazon konfigurációelemben nem adhatók meg egyszerre megfelelő és nem megfelelő alkalmazások is.  
  
#### <a name="to-specify-the-compliant-or-noncompliant-apps-list"></a>A megfelelő vagy a nem megfelelő alkalmazások listájának megadása  
  
1.  A **Megfelelő és nem megfelelő alkalmazások (iOS)** lapon adja meg a következő információkat:  
  
    -   **Szabályzatnak nem megfelelő alkalmazások listája** – Ezzel a beállítással meghatározhatja azoknak az alkalmazásoknak a listáját, amelyeket a rendszer nem megfelelőként jelez, ha a felhasználók telepítik őket.  
  
    -   **Szabályzatnak megfelelő alkalmazások listája** – Ha ezt a beállítást választja, összeállíthatja azon alkalmazások listáját, amelyeket telepíthetnek a felhasználók. A listán nem szereplő alkalmazások telepítéséről jelentés készül.  
  
    -   **Hozzáadás** – Hozzáadhat egy alkalmazást a kijelölt listához. Meg kell adnia egy szabadon választott nevet, valamint tetszés szerint megadhatja az alkalmazás kiadóját, valamint az alkalmazás alkalmazás-áruházbeli URL-címét.  
  
         Az URL-cím megadásához keresse meg a használni kívánt alkalmazást az iTunes App Store-ban.  
  
         Nyissa meg az alkalmazás lapját, és másolja az URL-címet a vágólapra. Most ezt a címet felhasználhatja URL-címként a kompatibilis vagy a nem kompatibilis alkalmazások listájában.  
  
         **Példa:** Keressen rá az áruházban a **Microsoft Word iPad** alkalmazást. Ebben az esetben a következő URL-t használja: **https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8**.  
  
    -   **Szerkesztés** – Segítségével szerkesztheti a kijelölt alkalmazás nevét, kiadóját és URL-címét.  
  
    -   **Eltávolítás** – Törölheti a kijelölt alkalmazást a listából.  
  
    -   **Importálás** – Importálhatja azokat az alkalmazásokat, amelyeket egy vesszővel tagolt fájlban megadott. Használja a fájlban megadott formátumot, alkalmazásnevet, kiadót és URL-címet.  
  
2.  Amikor elkészült, kattintson a **Tovább** gombra.  
  
 A megfelelő és nem megfelelő alkalmazások figyeléséhez a következő jelentések egyikét használhatja:  
  
-   **Egy adott felhasználó nem kompatibilis alkalmazásainak és eszközeinek listája:** Azon felhasználók adatait jeleníti meg, akik a beállított szabályzatnak meg nem felelő alkalmazásokat telepítettek. A jelentés azokat az eszközöket is tartalmazza, amelyeken telepítették az alkalmazásokat.  
  
-   **Nem kompatibilis alkalmazásokkal rendelkező felhasználók összegzése:** Azon felhasználókról jelenít meg adatokat, akiknek az eszközein a beállított szabályzatnak meg nem felelő alkalmazások vannak telepítve.  
  
 A jelentések használatára vonatkozó információért lásd: [Jelentéskészítés a System Center Configuration Managerben](../../core/servers/manage/reporting.md).  
  
###  <a name="compliant-and-noncompliant-apps-mac-os-x"></a>Megfelelő és nem megfelelő alkalmazások (Mac OS X)  
 Egy listában megadhatja a vállalatban megfelelőnek vagy nem megfelelőnek ítélt Mac OS X-alkalmazásokat. Ezután jelentések használatával megjeleníthetők azok az eszközök, amelyeken nem megfelelő alkalmazásokat telepítettek, valamint az a felhasználó, aki a telepítést végezte.  
  
 Egyazon konfigurációelemben nem adhatók meg egyszerre megfelelő és nem megfelelő alkalmazások is.  
  
#### <a name="to-specify-the-compliant-or-noncompliant-apps-list"></a>A megfelelő vagy a nem megfelelő alkalmazások listájának megadása  
  
1.  A **Megfelelő és nem megfelelő alkalmazások (Mac OS X)** lapon adja meg a következő információkat:  
  
    -   **Szabályzatnak nem megfelelő alkalmazások listája** – Ezzel a beállítással meghatározhatja azoknak az alkalmazásoknak a listáját, amelyeket a rendszer nem megfelelőként jelez, ha a felhasználók telepítik őket.  
  
    -   **Szabályzatnak megfelelő alkalmazások listája** – Ha ezt a beállítást választja, összeállíthatja azon alkalmazások listáját, amelyeket telepíthetnek a felhasználók. A listán nem szereplő alkalmazások telepítéséről jelentés készül.  
  
    -   **Hozzáadás** – Hozzáadhat egy alkalmazást a kijelölt listához. Meg kell adnia egy szabadon választott nevet, valamint tetszés szerint megadhatja az alkalmazás kiadóját, valamint az alkalmazás csomagazonosítóját.  
  
        > [!TIP]  
        >  Az alkalmazás csomagazonosítóját az alábbi lépéseket követve keresheti meg a telepített alkalmazást futtató Mac számítógépen:  
        >   
        >  1.  Nyissa meg az alkalmazás telepítési mappáját (például **/Applications**)  
        > 2.  Jelölje ki az *<alkalmazásnév\>***.app** csomagot, és válassza a **Show Package Contents** (Csomag tartalmának megjelenítése) lehetőséget.  
        > 3.  Nyissa meg az **Info.plist** fájlt  
        > 4.  Ellenőrizze a **CFBundleIdentifier** kulcshoz hozzárendelt értéket  
        >   
        >  A csomagazonosító formátuma: **com.contoso.alkalmazásnév**  
  
    -   **Szerkesztés** – A kiválasztott alkalmazás nevének, kiadójának és csomagazonosítójának szerkesztése.  
  
    -   **Eltávolítás** – Törölheti a kijelölt alkalmazást a listából.  
  
    -   **Importálás** – Importálhatja azokat az alkalmazásokat, amelyeket egy vesszővel tagolt fájlban megadott. Használja a fájlban megadott formátumot, alkalmazásnevet, kiadót és alkalmazáscsomag-azonosítót.  
  
2.  Amikor elkészült, kattintson a **Tovább** gombra.  
  
 A megfelelő és nem megfelelő alkalmazások figyeléséhez a következő jelentések egyikét használhatja:  
  
-   **Egy adott felhasználó nem kompatibilis alkalmazásainak és eszközeinek listája:** Azon felhasználók adatait jeleníti meg, akik a beállított szabályzatnak meg nem felelő alkalmazásokat telepítettek. A jelentés azokat az eszközöket is tartalmazza, amelyeken telepítették az alkalmazásokat.  
  
-   **Nem kompatibilis alkalmazásokkal rendelkező felhasználók összegzése:** Azon felhasználókról jelenít meg adatokat, akiknek az eszközein a beállított szabályzatnak meg nem felelő alkalmazások vannak telepítve.  
  
 A jelentések használatára vonatkozó információért lásd: [Jelentéskészítés a System Center Configuration Managerben](../../core/servers/manage/reporting.md).  
  
### <a name="ios-and-mac-os-x-custom-profile-settings"></a>Egyéni iOS- és Mac OS X-profil beállításai  
 Az **iOS- és Max OS X-eszközökhöz készült egyéni profilokkal** érvénybe léptetheti az iOS- és Mac OS X-eszközökön az [Apple Configuratorral](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) létrehozott beállításokat. Ezzel az eszközzel számos olyan beállítást készíthet, amelyek ezen eszközök működését vezérlik, és egy konfigurációs profilba exportálhatja őket. Ezt a konfigurációs profilt később egyéni iOS- és Mac OS X-profilokba importálhatja, és a beállításokat érvénybe léptetheti munkahelye felhasználói és eszközei esetében.  
  
> [!NOTE]  
>  Ellenőrizze, hogy az Apple Configuratorból exportált beállítások kompatibilisek-e azon eszközök iOS- vagy Mac OS X-verziójával, amelyeken az egyéni profilt telepíti. Az inkompatibilis beállítások megoldásával kapcsolatos információért keresse a Konfigurációs profilokkal kapcsolatos referenciát és a Mobileszköz-kezelési protokollal kapcsolatos referenciát az [Apple Developer](https://developer.apple.com/) webhelyen.  
  
#### <a name="to-create-an-ios-and-mac-os-x-custom-profile"></a>Egyéni iOS- és Mac OS X-profil létrehozása  
  
1.  A **Konfigurációelem létrehozása varázsló** **Egyéni iOS- és Mac OS X-profil beállításainak konfigurálása** lapján adja meg a következő információkat:  
  
    -   **Egyéni konfigurációs profil neve (megjelenik a felhasználóknak)** -adja meg a szabályzat nevét, amely megjelenik az eszközön, és a Configuration Manager-jelentések.  
  
    -   **Importálás** – Válasszon egy fájlt az Apple Configuratorból exportáltak közül.  
  
    -   **Konfigurációs profil adatai** – Megjeleníti az importált fájlt.  
  
    -   **Nem megfelelő beállítások szervizelése** -  
  
         Itt adhatja meg, hogy ki szeretné-e javítani a nem megfelelő konfigurációs beállításokat (ha ez támogatott).  
  
    -   **Meg nem felelőség súlyossága jelentésekhez** – Itt adhatja meg, hogy milyen súlyossági szintről készüljön jelentés, ha ez a megfelelőségi szabályzat nem megfelelőnek minősül. A választható súlyossági szintek az alábbiak:  
  
        > [!NOTE]  
        >  Ha egy Mac OS X-eszköz készenléti állapotban van, a házirendek és profilok nem kézbesíthetők, és nem naplózhatók. Ennek eredményeképpen a Configuration Manager konzol ideiglenesen megjelenítheti a házirend-beállítások állapotüzenet hibás, amíg az eszköz fel nem ébred a készenléti üzemmódból.  
  
        -   **Nincs** a megfelelőségi szabálynak eleget nem tevő eszközök nem kerül a hiba súlyossága a Configuration Manager-jelentések.  
  
        -   **Információ** a megfelelőségi szabálynak eleget nem tevő eszközök adják meg a hiba súlyosságát a **információk** a Configuration Manager jelentésekben.  
  
        -   **Figyelmeztetés** a megfelelőségi szabálynak eleget nem tevő eszközök adják meg a hiba súlyosságát a **figyelmeztetés** Configuration Manager jelentések.  
  
        -   **Kritikus** a megfelelőségi szabálynak eleget nem tevő eszközök adják meg a hiba súlyosságát a **kritikus** a Configuration Manager jelentésekben.  
  
        -   **Kritikus eseménnyel** a megfelelőségi szabálynak eleget nem tevő eszközök adják meg a hiba súlyosságát a **kritikus** a Configuration Manager jelentésekben. Ezt a súlyossági szintet az alkalmazás eseménynaplója is rögzíti Windows-eseményként.  
  
#### <a name="how-to-create-a-configuration-profile-file"></a>Konfigurációs profilfájl létrehozása  
 Az egyéni házirend által használt konfigurációs profilfájlt kétféleképpen hozhatja létre:  
  
-   A fájl Apple Configurator eszközből történő exportálásával (**.mobileconfig** kiterjesztéssel).  
  
-   A fájlt Ön is létrehozhatja, ha az [Apple konfigurációs profilok készítésére szolgáló útmutatójának](https://developer.apple.com/library/ios/featuredarticles/iPhoneConfigurationProfileRef/Introduction/Introduction.html) megfelelő sémáját használja.  
  
###  <a name="kiosk-mode-ios"></a>Teljes képernyős mód (iOS)  
 A teljes képernyős mód lehetővé teszi az eszközök zárolását, hogy csak bizonyos szolgáltatások működjenek rajtuk. Megadhatja például, hogy az eszköz csak egy meghatározott felügyelt alkalmazás futtatását engedélyezze, vagy letilthatja a hangerő-szabályozó gombok használatát az eszközön. Ezek a beállítások egy eszköz demonstrációs modelljéhez, illetve egy olyan eszközhöz használhatók, amely csak egyetlen funkció végrehajtására van kijelölve (például egy pénztári eszköz).  
  
#### <a name="to-configure-kiosk-mode-for-ios-devices"></a>Teljes képernyős mód konfigurálása iOS-eszközökhöz  
  
1.  A **Konfigurációelem létrehozása varázsló** **Teljes képernyős mód beállításainak konfigurálása iOS eszközökhöz** lapján adja meg a következő információkat:  
  
    -   **Alkalmazás kiválasztása** – Az eszköz Kioszk módjában futtatható alkalmazás kiválasztása. Az itt megadotton kívül más alkalmazás nem futtatható az eszközön. A következő lehetőségek közül választhat:  
  
        -   **Felügyelt alkalmazás:** Kattintson a Tallózás gombra, és válasszon egy felügyelt alkalmazást.  
  
        -   **Áruházbeli alkalmazás:** Adja meg egy Áruházbeli alkalmazás URL-címét, és az **Azonosító lekérése** gombra kattintva töltse ki az **Alkalmazásazonosító** mezőt.  
  
         Az alkalmazás URL-címének megkeresése:  
  
        -   Egy keresőmotor segítségével keresse meg az iTunes alkalmazás-áruházban használni kívánt alkalmazást, és nyissa meg az alkalmazás lapját.  
  
        -   Másolja a lap URL-címét a vágólapra. Ezt a címet adja majd meg a Kioszk módban futtatni kívánt alkalmazás URL-címeként.  
  
        -   **Példa:** Keresse meg **Microsoft Word iPad**. Ebben az esetben a következő URL-t használja: **https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8**.  
  
    -   **Érintés** – Engedélyezheti vagy letilthatja az érintőképernyőt az eszközön.  
  
    -   **Képernyő elforgatása** – Engedélyezheti vagy letilthatja a képernyő tájolásának módosítását az eszköz elforgatásakor.  
  
    -   **Hangerőgombok** – Engedélyezheti vagy letilthatja a hangerőszabályzó gombok használatát az eszközön.  
  
    -   **Csengés kapcsolója** – Engedélyezheti vagy letilthatja a csengető- (némító-) kapcsolót az eszközön.  
  
    -   **Képernyőalvás és -ébresztés gomb:** – Engedélyezheti vagy letilthatja a képernyő ébresztőgombját az eszközön.  
  
    -   **Automatikus zárolás** – Engedélyezheti vagy letilthatja az eszköz automatikus zárolását.  
  
    -   **Monó hang** – Engedélyezheti vagy letilthatja a **Monó hang** kisegítő beállítást.  
  
    -   **Hangalámondás** – Engedélyezheti vagy letilthatja a **Hangalámondás** kisegítő beállítást, amely hangosan felolvassa az eszköz képernyőjén megjelenő szöveget.  
  
    -   **Narrátor beállításai** – Engedélyezheti vagy letilthatja a narrátor beállításait (például hogy milyen gyorsan történjen a képernyőn látható szöveg felolvasása).  
  
    -   **Nagyítás** – Engedélyezheti vagy letilthatja a **Nagyítás** kisegítő beállítást, amellyel érintéssel nagyíthatja az eszköz képernyőjén megjelenő tartalmat.  
  
    -   **Nagyítás beállításai** – Engedélyezheti vagy letilthatja a nagyítási funkció módosítását.  
  
    -   **Színek invertálása** – Engedélyezheti vagy letilthatja a **Színek invertálása** kisegítő beállítást, amellyel módosíthatja a képernyőt a látásukban korlátozott felhasználók számára.  
  
    -   **Színek invertálásának beállításai** – Engedélyezheti vagy letilthatja a színinvertálási funkció módosítását.  
  
    -   **Érintéssegítés** – Engedélyezheti vagy letilthatja az **Érintéssegítés** kisegítő beállítást, amely segít a nehézségekkel küszködő felhasználóknak a képernyőn elvégezhető kézmozdulatok végrehajtásában.  
  
    -   **Érintéssegítés beállításai** – Engedélyezheti vagy letilthatja az Érintéssegítés funkció módosítását.  
  
    -   **Beszédválasztás** – Engedélyezheti vagy letilthatja a **Beszédválasztás** kisegítő beállítást, amellyel felolvastatható az Ön által kijelölt szöveg.  
  
    -   **Nem megfelelő beállítások szervizelése** – Itt adhatja meg, hogy ki szeretné-e javítani a nem megfelelő konfigurációs beállításokat (ha ez támogatott).  
  
    -   **Meg nem felelőség súlyossága jelentésekhez** – Itt adhatja meg, hogy milyen súlyossági szintről készüljön jelentés, ha ez a megfelelőségi szabályzat nem megfelelőnek minősül. A használható súlyossági szintek a következők:  
  
        -   **Nincs** a megfelelőségi szabálynak eleget nem tevő eszközök nem kerül a hiba súlyossága a Configuration Manager-jelentések.  
  
        -   **Információ** a megfelelőségi szabálynak eleget nem tevő eszközök adják meg a hiba súlyosságát a **információk** a Configuration Manager jelentésekben.  
  
        -   **Figyelmeztetés** a megfelelőségi szabálynak eleget nem tevő eszközök adják meg a hiba súlyosságát a **figyelmeztetés** Configuration Manager jelentések.  
  
        -   **Kritikus** a megfelelőségi szabálynak eleget nem tevő eszközök adják meg a hiba súlyosságát a **kritikus** a Configuration Manager jelentésekben.  
  
        -   **Kritikus eseménnyel** a megfelelőségi szabálynak eleget nem tevő eszközök adják meg a hiba súlyosságát a **kritikus** a Configuration Manager jelentésekben. Ezt a súlyossági szintet az alkalmazás eseménynaplója is rögzíti Windows-eseményként.  
  
## <a name="see-also"></a>Lásd még:  
 [A System Center Configuration Manager ügyfélalkalmazás nélkül felügyelt eszközök konfigurációelemei](../../compliance/deploy-use/configuration-items-for-devices-managed-without-the-client.md)

