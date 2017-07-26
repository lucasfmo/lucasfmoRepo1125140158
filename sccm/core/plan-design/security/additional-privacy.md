---
title: "A System Center Configuration Manager adatvédelmi nyilatkozata – további információk |} Microsoft Docs"
description: "További tudnivalók arról, hogy a Microsoft hogyan gyűjti és a System Center Configuration Manager telepítési adatait használja."
ms.custom: na
ms.date: 12/30/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1fcc921f-085f-4b0b-9c53-1e0707211076
caps.latest.revision: 5
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
translation.priority.ht:
- cs-cz
- de-de
- en-gb
- es-es
- fr-fr
- hu-hu
- it-it
- ja-jp
- ko-kr
- nl-nl
- pl-pl
- pt-br
- pt-pt
- ru-ru
- sv-se
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 47d473b3884c3cd2ff7516629a7c32d4e52ac39b
ms.openlocfilehash: ef7b3656f9b4a31e07227aa4e864448d0dd1fcdc
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="additional-information-about-privacy-for-system-center-configuration-manager"></a>A System Center Configuration Manager adatvédelmi vonatkozó további információért

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


## <a name="updates-and-servicing"></a>Frissítések és karbantartás
A System Center Configuration Manager bevezet egy új frissítési modell, amely segít a Configuration Manager telepítési naprakész lesz a legújabb frissítésekkel és szolgáltatásokkal. Telepítésekor ez a funkció hozzáadása egy új helyrendszerszerepkör, amely a szolgáltatáskapcsolódási pont helyrendszer-kiszolgálóra, amely úgy dönt, hogy egy rendszergazda hívják. Az összegyűjtött információk és felhasználásukról kapcsolatos részletekért lásd: a használati adatok című részben.


## <a name="usage-data"></a>Használati adatok
A System Center Configuration Manager diagnosztikai és használati adatokat saját magáról, amely a telepítési élmény, minőségét és a jövőbeli kiadások biztonságának javításához használja a Microsoft gyűjti.
Diagnosztikai és használati adatok minden System Center Configuration Manager-hierarchiában engedélyezve van. SQL Server-lekérdezéseket, amelyek hetente futnak az egyes elsődleges helyeken és a központi adminisztrációs helyen áll. Amikor a hierarchia központi adminisztrációs helyet használ, a rendszer erre a helyre replikálja az elsődleges helyekről származó adatokat. A hierarchia legfelső szintű helyen a szolgáltatáskapcsolódási pont keresésekor küldi el ezeket az információkat a frissítéseket. Ha a szolgáltatáskapcsolódási pont kapcsolat nélküli módban van, a rendszer a szolgáltatáskapcsolódási eszközzel küldi át az adatokat.

A Configuration Manager gyűjti az adatokat csak a hely SQL server adatbázisa, és közvetlenül az ügyfelektől vagy helykiszolgálóktól nem gyűjt adatokat.

Rendszergazdák módosíthatják a nyissa meg az összegyűjtött adatok szintjét a **használati adatok** szakasz a Configuration Manager konzol.

További információkért tekintse meg a vonatkozó használati adatok szintjei és beállításai a "További információ" cikkek a [diagnosztikai és használati adatokat a System Center Configuration Manager](http://go.microsoft.com/fwlink/?LinkID=626566) cikk.


## <a name="customer-experience-improvement-program"></a>Felhasználói élmény fokozása program
A felhasználói élmény fokozása Program (CEIP) alapvető információt gyűjt a Configuration Manager konzolról az Ön hardverkonfigurációjáról, és hogyan használja szoftvereinket és szolgáltatásainkat trendek és használati minták azonosításához. Felhasználói élmény fokozása program adatokat is gyűjti, a típusával és számával előforduló hibákat, szoftverek és hardverek teljesítményére, és a szolgáltatások sebességére vonatkozik. Nem gyűjtünk a nevét, címét, vagy egyéb kapcsolattartási adatait. Az ügyfélszámítógépekről nem gyűjtünk a CEIP programban felhasználható adatokat.

Ezt az információt arra használjuk fel, hogy a Microsoft szoftvereinek és szolgáltatásainak a minőségét, megbízhatóságát és teljesítményét javítsuk.

Az adatok, amelyek a gyűjtött, feldolgozott vagy továbbított CEIP kapcsolatban bővebben lásd: a [CEIP adatvédelmi nyilatkozatában](http://go.microsoft.com/fwlink/?LinkID=525211).

## <a name="operations-management-suite-connector"></a>Az Operations Management Suite-összekötő
A Microsoft Operations Management Suite-összekötő szinkronizálásának adatok, például gyűjtemények, a System Center Configuration Manager a Microsoft Operations Management Suite. A Microsoft Azure-előfizetése Azonosítóját és a titkos kulcs tárolódnak a Configuration Manager adatbázisa a szolgáltatás rendszergazda általi konfigurálása során. Az Azure Active Directory ügyfélkulcs és a Microsoft Operations Management Suite-munkaterület megosztott kulcsot is a helyszíni System Center Configuration Manager adatbázisban tárolódnak. System Center Configuration Manager és a Microsoft Operations Management Suite közötti kommunikáció minden esetben HTTPS PROTOKOLLT használja. Nincsenek további információt a gyűjtemények kívül véletlenszerű telemetriai adatokat a Microsoftnak valósul meg. A Microsoft Operations Management Suite összegyűjtő információkkal kapcsolatos részletekért lásd: [naplózni a analytics biztonsági](http://go.microsoft.com/fwlink/?LinkId=823545).

## <a name="asset-intelligence"></a>Eszközintelligencia
Az eszközintelligencia szolgáltatás lehetővé teszi, hogy az IT-rendszergazdák meghatározását, nyomon követheti és konfigurációs szabványoknak való megfelelés proaktív kezelését. A fizikai és a virtuális alkalmazások telepítésére és használatára egyaránt kiterjedő mérések és jelentések segítséget nyújtanak ahhoz, hogy a szervezet megalapozott döntéseket hozhasson a szoftverek licencelésével kapcsolatban, és folyamatosan teljesítse a licencszerződések feltételeit. Használati adatok összegyűjtése a Configuration Manager-ügyfelek, után rendszergazdák segítségével különböző szolgáltatások meg az adatokat, például gyűjtemények, lekérdezések és jelentéskészítő.

Minden egyes szinkronizáció során letölti egy ismert szoftverek katalógusát a Microsoft. Microsoft információinak elküldéséről a szervezetek számára, tovább vizsgált és a katalógushoz hozzáadott belül felderített Kategorizálatlan szoftvercímek a informatikai rendszergazdák választhatják. A felöltés előtt egy párbeszédpanelen megjelenik az ellenőrizhetők a feltöltésre váró adatok. A már feltöltött adatok nem hívhatók vissza. Az Eszközintelligencia szolgáltatás nem küld információt a Microsoftnak a felhasználókról, a számítógépekről és a licenchasználatról.

Szoftverek feltöltése, után a Microsoft kutatói azonosítása, kategorizálását, és végezze el ezt az információt elérhetővé más ügyfelek számára a szolgáltatás és a katalógus más felhasználói. Minden feltöltött szoftver nyilvános lesz. Az alkalmazás és a kategorizálásához kapcsolódó információ bekerül a katalógusban, és letölthetővé a katalógus más felhasználói számára. Az Eszközintelligencia szolgáltatás adatgyűjtésének konfigurálását megelőzően, illetve mielőtt eldöntené, hogy szeretne-e információkat küldeni a Microsoftnak, vegye figyelembe a szervezet adatvédelmi követelményeit.

Az eszközintelligencia szolgáltatás alapértelmezés szerint nincs engedélyezve a System Center Configuration Managerben. A kategorizálatlan szoftverek feltöltése soha nem automatikusan történik, és a rendszer kialakítása nem teszi lehetővé e feladat automatizálását. Az egyes szoftverek feltöltésének kiválasztását és jóváhagyását manuális módszerrel kell elvégezni.

## <a name="endpoint-protection"></a>Endpoint Protection
A Microsoft felhőalapú védelmi szolgáltatás volt korábbi nevén Microsoft Active Protection Service vagy térképek.
A vonatkozó termék azokat a System Center Endpoint Protection és az Endpoint Protection szolgáltatást a System Center Configuration Manager (System Center Endpoint Protection és a Windows 10 rendszerhez készült Windows Defender kezelése). Ez a funkció nincs megvalósítva a System Center Endpoint Protection for Linux és a System Center Endpoint Protection for Mac csomagokkal.

A Microsoft Felhőszolgáltatásához védelmi kártevőirtó közösségi egy önkéntes globális online Közösség, amely tartalmazza a System Center Endpoint Protection felhasználóit. Ha igénybe veszi a Microsoft felhőalapú védelmi szolgáltatás, System Center Endpoint Protection automatikusan küld információkat a Microsoft. A Microsoft az információk meghatározásához szoftvert kell a lehetséges fenyegetések miatt vizsgálni, továbbá a System Center Endpoint Protection hatékonyságának javítása érdekében. A Közösség elősegíti az új kártevőszoftver-fertőzések terjedésének megállítását. Ha egy Microsoft Felhőszolgáltatásra védelmi jelentés kártevőket vagy esetlegesen nemkívánatos szoftvereket, amelyek az Endpoint Protection-ügyfél eltávolítása esetleg kapcsolatos adatokat tartalmaz, a Microsoft Felhőszolgáltatás-védelmi letölti a legfrissebb aláírást. Microsoft Felhőszolgáltatás-védelmet "vakriasztásokat" is tájékozódhat (ahol egy eredetileg kártevőként azonosított elemről kiderül, hogy nem kell lennie) és hárítsa el őket.

A Microsoft Cloud Protection Service Közösség jelentései lehetséges kártevő fájlok, például a fájlneveket, titkosítási kivonatot, szállító, méretet és dátumbélyegzőket információkat tartalmaznak. Ezenkívül a Microsoft felhőalapú védelmi szolgáltatás teljes URL-címeket a fájl eredetét jelezze gyűjthet. URL-időnként előfordulhat a személyes adatok, például a feltételek vagy űrlapokon megadott adatok. Jelentések kiterjedhetnek lejegyezte, ha az Endpoint Protection értesítést nemkívánatos szoftverrel kapcsolatos műveleteket. A Microsoft felhőalapú védelmi szolgáltatás jelentései tartalmazzák ezt az információt a Microsoft fel tudja mérni milyen hatékonyan Endpoint Protection észleli és eltávolítása kártevőket és vélhetően nemkívánatos szoftver és annak megpróbálja azonosítani az új kártevő szoftverek.

Ha egy alapszintű vagy speciális tagság csatlakozhat Microsoft Felhőszolgáltatás-védelem. Az alapszintű tag jelentései a fentiekben ismertetett információkkal rendelkezik. A kiemelt jelentések összetettebbek, és a, hogy az Endpoint Protection által észlelt szoftverrel kapcsolatban további részletekre terjedhetnek tag, például a szoftverek helyét, az ilyen fájlneveket, hogyan működik a szoftver, és milyen hatással vannak a számítógépre. A jelentések és más Endpoint Protection felhasználóktól, aki részt vesz a Microsoft Felhőszolgáltatás védelmi súgó Microsoft kutatóinak gyorsabban felismerjék az új fenyegetéseket. A kártevőleírások létrehozása olyan programok, amelyek az elemzési kritériumnak megfelelnek, és a frissített leírások érhetik el a Microsoft Update szolgáltatáson keresztül minden felhasználó.

Észleléséhez és javításához bizonyos típusú kártevőszoftver-fertőzések érdekében a termék rendszeresen információkat küld a Microsoft Felhőszolgáltatás-védelmet a számítógép biztonsági állapotát. Ezen információk közé tartozik a számítógép biztonsági beállításait és az illesztőprogramok leíró naplófájlok és más szoftverek rendszerindítás közben a számítógép indításakor kapcsolatos információkat.
Egy szám, amely egyedileg azonosítja a számítógépen is lett van küldve. Is a Microsoft felhőalapú védelmi szolgáltatás gyűjthet az IP-címek, amelyek a lehetséges kártevő fájlok csatlakoznak.

A Microsoft Cloud Protection Service Közösség jelentései Microsoft szoftvereinek és szolgáltatásainak javítását szolgálják. A jelentések is felhasználható statisztikai, egyéb tesztelési, illetve elemzési célokra és meghatározások létrehozásához. Csak a Microsoft alkalmazottai, alvállalkozói, partnerek és szállítók, akiknek az üzleti szeretné használni, a jelentések érhetik el azokat.

A Microsoft felhőalapú védelmi szolgáltatás szándékosan nem gyűjt személyes adatokat. Az Microsoft Felhőszolgáltatás védelmi gyűjt személyes adatokat, a Microsoft az információkat nem használja az Ön azonosítására vagy kapcsolatfelvételre.

Összegyűjtött adatok kapcsolatos további részletek találhatók a termék dokumentációját a [a System Center Configuration Managerben az Endpoint Protection](http://go.microsoft.com/fwlink/?LinkId=823547).

## <a name="site-hierarchy--geographical-view-with-bing-maps"></a>A Helyhierarchia – földrajzi nézet a Bing Maps szolgáltatással
A Helyhierarchia - a földrajzi nézet lehetővé teszi a maps megtekintése a Configuration Manager fizikai kiszolgálói topológiájának biztosító Microsoft Bing Maps. A funkció engedélyezéséhez, Ön által biztosított helyére vonatkozó információkat kerül a kiszolgálóról a Bing Maps webszolgáltatásnak.

A Microsoft a Microsoft Bing Maps és a Microsoft egyéb webhelyeinek és szolgáltatásainak üzemeltetésére és fejlesztésére használja fel ezeket az információkat. További információkért lásd: a [Microsoft adatvédelmi nyilatkozatát](http://go.microsoft.com/fwlink/?LinkId=823548).
Igény szerint mellőzheti is a Helyhierarchia földrajzi nézetének használatát. A Helyhierarchia-Diagram nézet megmutatja, hogy a hierarchiában, és nem használja a Bing Maps szolgáltatás.

## <a name="microsoft-intune-subscription"></a>A Microsoft Intune-előfizetés
Az ügyfelek, akik vásárolt a Microsoft Intune-előfizetést a Configuration Manager segítségével kezelik mobileszközeiket, amely kapcsolódik a Microsoft Intune-nal. [Microsoft Online Services adatvédelmi nyilatkozatát](http://go.microsoft.com/fwlink/?LinkId=262214) vonatkozik a Microsoft online services, köztük a Microsoft Intune. Ha az ügyfél is egy Microsoft Intune-előfizetést, a [Microsoft Online Services adatvédelmi nyilatkozatát](http://go.microsoft.com/fwlink/?LinkId=262214) a jelen adatvédelmi nyilatkozat mellett olvassa el.

A Microsoft Intune folytatott kommunikáció minden esetben HTTPS PROTOKOLLT használja. Konfigurálja a Microsoft Intune-előfizetést, és töltse le a tanúsítvány-aláírási kérelem (CSR) iOS-támogatás konfigurálásához szükséges, hogy egy rendszergazda jelentkezzen be a Microsoft Intune egy szervezeti fiókkal és jelszóval. Ezek a hitelesítő adatok nem kerülnek a Configuration Manager. A Microsoft Intune-nal folytatott minden egyéb kommunikáció hitelesítése PKI-tanúsítványok, amelyek a Microsoft Intune automatikusan létrehozza.

A Microsoft Intune szolgáltatáshoz kapcsolódó eszközök kezeléséhez, bizonyos információk küldött és fogadott a Microsoft Intune-ból. Ezen információk közé tartozik az egyszerű felhasználónév (UPN) az összes olyan felhasználó, a szolgáltatás és az eszköz Hardverleltár-információk a Microsoft Intune által kezelt eszközök rendelt. Metaadatok, mint például az alkalmazás neve, kiadója és verziószáma, a Manage.Microsoft.com terjesztési pontokhoz társított tartalmakhoz kapcsolódó küld a Microsoft Intune. A Manage.Microsoft.com terjesztési pontokhoz társított tényleges bináris tartalmat titkosított előtt fel lesz töltve az Intune-hoz.

A rendszer alapértelmezés szerint nem konfigurálja ezt a szolgáltatást. Rendszergazdák átkerül a Manage.Microsoft.com terjesztési pontokra és a felhasználókat, akik a szolgáltatáshoz rendelt tartalom szabályozzák. A szolgáltatás bármikor eltávolítható.

