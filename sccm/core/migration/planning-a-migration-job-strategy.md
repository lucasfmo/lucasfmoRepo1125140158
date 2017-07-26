---
title: "Áttelepítési feladat megtervezése |} Microsoft Docs"
description: "Áttelepítési feladatok segítségével konfigurálhatja a System Center Configuration Manager-környezetbe áttelepíteni kívánt adatokat."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a70bfbd4-757a-4468-9312-1c3b373ef9fc
caps.latest.revision: 6
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: noindex
ms.translationtype: Machine Translation
ms.sourcegitcommit: cc0c1075af370b6190cbb269665d4a09e756ab4e
ms.openlocfilehash: 4c83540db763bea039a92633a1d1a808e60e27ad
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="plan-a-migration-job-strategy-in-system-center-configuration-manager"></a>A System Center Configuration Manager áttelepítési feladatok stratégiájának megtervezése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Áttelepítési feladatok segítségével konfigurálhatja a System Center Configuration Manager-környezetbe áttelepíteni kívánt adatokat. Az áttelepítési feladatok azonosítják az objektumok áttelepítését tervezi, és a célhierarchia legfelső szintű helyén futnak. Beállíthat egy vagy több áttelepítési feladatot. Ez lehetővé teszi az összes objektum egyszerre vagy adatok korlátozott részhalmazainak áttelepíteni.  

 Áttelepítési feladatokat hozhat létre, miután a Configuration Manager sikeresen összegyűjtötte az adatokat a forráshierarchia egy vagy több helyéről. Bármilyen sorrendben áttelepítheti az adatokat azon forráshelyekről, amelyekről vannak összegyűjtött adatok. A Configuration Manager 2007-forráshelyről, ahol az objektumot létrehozták helyről áttelepítheti az adatokat. Forráshelyek, amely futtatja a System Center 2012 Configuration Manager vagy újabb, az összes áttelepíthető adatok elérhető a forráshierarchia legfelső szintű helyén.  

 Mielőtt hierarchiák között telepítene át ügyfeleket, győződjön meg arról, hogy az ügyfelek által használt objektumok át lettek telepítve​​, és hogy ezek az objektumok elérhetőek a célhierarchiában. Például ha a Configuration Manager 2007 SP2 rendszerű forráshierarchiából telepít át, lehetséges, hogy olyan ügyfelet tartalmazó egyéni gyűjteménybe telepített tartalomhoz tartozó hirdetménnyel. Ebben a forgatókönyvben azt javasoljuk, hogy az áttelepítést a gyűjteményt, a hirdetés és a kapcsolódó tartalmat az ügyfél áttelepítése előtt. Ezek az adatok nem rendelhető hozzá az ügyfél a célhierarchiában, ha a tartalmat, a gyűjtemény és a hirdetmény nem települnek át az ügyfél az áttelepítése előtt. Ha az ügyfél nincs társítva a korábban futtatott hirdetményekhez és tartalmakhoz kapcsolódó adatokkal, az ügyfélnek a rendszer feleslegesen ajánlhatja fel telepítésre a tartalmat a célhierarchiában. Az ügyfél az adatokat követő áttelepítése esetén a rendszer társítja azt a hozzá tartozó tartalommal és hirdetménnyel, és nem ajánlja fel ezt a tartalmat az áttelepített hirdetményhez, kivéve ha az ismétlődik.  

 Bizonyos objektumok több, a forráshierarchiából a célhierarchiába történő adatáttelepítést igényelnek. Például történő sikeres áttelepítéséhez szoftverfrissítések az ügyfelek a célhierarchiára, meg kell egy aktív szoftverfrissítési pontot telepíteni, termékek katalógusának konfigurálása és a célhierarchiában a Windows Server Update Services (WSUS) a szoftverfrissítési pontot szinkronizálni.  

 A következő részekben leírtak alapján megtervezheti áttelepítési feladatait.  

-   [Áttelepítési feladatok típusai](#Types_of_Migration)  

-   [Az áttelepítési feladatok tervezésének általános szabályai](#About_Migration_Jobs)  

-   [Gyűjtemény áttelepítési feladatainak tervezése](#About_Collection_Migration)  

-   [Objektumok áttelepítési feladatainak tervezése](#About_Object_Migration)  

-   [Tervezése a korábban áttelepített objektumok áttelepítési feladatainak](#About_Object_Migrations)  

##  <a name="Types_of_Migration"></a>Áttelepítési feladatok típusai  
 A Configuration Manager a következő áttelepítési feladattípusokat támogatja. Mindegyik feladattípus úgy lett kialakítva, hogy segítséget nyújtson a feladatba felvehető objektumok definiálásában.  

 **Gyűjteményáttelepítés** (csak akkor támogatott, ha az áttelepítés a Configuration Manager 2007 SP2): Telepítse át a választott gyűjteményekhez kapcsolódó objektumok. A gyűjtemények áttelepítése alapértelmezés szerint a gyűjtemény tagjaihoz társított összes objektum tartozik. Egyes objektumpéldányok kizárhatók a gyűjteményáttelepítési feladatból.  

 **Objektumáttelepítés**: Kiválasztott objektumokat telepíti át. Csak az áttelepíteni kívánt adatokat jelölje ki.  

 **Előzőleg áttelepített objektum áttelepítése**: Telepítse át az objektumokat, amelyeket már korábban áttelepített, ha azok frissültek a forráshierarchiában található legutóbbi áttelepítésük óta.  

###  <a name="Objects_that_can_migrate"></a>Áttelepíthető objektumok  
 Egy adott típusú áttelepítési feladat nem minden objektumot tud áttelepíteni. A következő lista az egyes áttelepítési feladatokkal áttelepíthető objektumtípusokat tartalmazza.  

> [!NOTE]  
>  Gyűjtemények áttelepítési feladatai csak akkor, ha a Configuration Manager 2007 SP2 rendszerű forráshierarchiából telepít át objektumokat érhetők el.  

 **Feladattípusok segítségével az egyes objektumok áttelepítése**  

-   **Hirdetmények** (áttelepíthetők a támogatott Configuration Manager 2007-Forráshelyek érhető el)  

    -   Gyűjteményáttelepítés  


-   **Eszközintelligencia-katalógus**  

    -   Objektumáttelepítés  

    -   Előzőleg áttelepített objektum áttelepítése  

-   **Eszközintelligencia hardverkövetelményei**  

    -   Objektumáttelepítés  

    -   Előzőleg áttelepített objektum áttelepítése  

-   **Eszközintelligencia szoftverlista**  

    -   Objektumáttelepítés  

    -   Előzőleg áttelepített objektum áttelepítése  

-   **Határok**  

    -   Objektumáttelepítés  

    -   Előzőleg áttelepített objektum áttelepítése  

-   **Referenciakonfigurációk**  

    -   Gyűjteményáttelepítés  

    -   Objektumáttelepítés  

    -   Előzőleg áttelepített objektum áttelepítése  

-   **Konfigurációs elemek**  

    -   Gyűjteményáttelepítés  

    -   Objektumáttelepítés  

    -   Előzőleg áttelepített objektum áttelepítése  

-   **Karbantartási időszakok**  

    -   Gyűjteményáttelepítés  


-   **Operációs rendszer központi telepítő rendszerindító lemezképei**  

    -   Gyűjteményáttelepítés  

    -   Objektumáttelepítés  

    -   Előzőleg áttelepített objektum áttelepítése  

-   **Operációs rendszer központi telepítési illesztőprogram-csomagok**  

    -   Gyűjteményáttelepítés  

    -   Objektumáttelepítés  

    -   Előzőleg áttelepített objektum áttelepítése  

-   **Operációs rendszer központi telepítési illesztőprogramjai**  

    -   Gyűjteményáttelepítés  

    -   Objektumáttelepítés  

    -   Előzőleg áttelepített objektum áttelepítése  

-   **Operációs rendszer központi telepítési lemezképei**  

    -   Gyűjteményáttelepítés  

    -   Objektumáttelepítés  

    -   Előzőleg áttelepített objektum áttelepítése  

-   **Operációs rendszer központi telepítési csomagok**  

    -   Gyűjteményáttelepítés  

    -   Objektumáttelepítés  

    -   Előzőleg áttelepített objektum áttelepítése  

-   **Szoftverterjesztési csomagok**  

    -   Gyűjteményáttelepítés  

    -   Objektumáttelepítés  

    -   Előzőleg áttelepített objektum áttelepítése  

-   **Szoftverhasználat-mérési szabályok**  

    -   Objektumáttelepítés  

    -   Előzőleg áttelepített objektum áttelepítése  

-   **Szoftverfrissítési központi telepítési csomagok**  

    -   Gyűjteményáttelepítés  

    -   Objektumáttelepítés  

    -   Előzőleg áttelepített objektum áttelepítése  

-   **Szoftverfrissítési központi telepítési sablonok**  

    -   Gyűjteményáttelepítés  

    -   Objektumáttelepítés  

    -   Előzőleg áttelepített objektum áttelepítése  

-   **Szoftverfrissítési központi telepítések**  

    -   Gyűjteményáttelepítés  


-   **Szoftverfrissítési listák**  

    -   Objektumáttelepítés  

    -   Előzőleg áttelepített objektum áttelepítése  

-   **Feladatütemezések**  

    -   Gyűjteményáttelepítés  

    -   Objektumáttelepítés  

    -   Előzőleg áttelepített objektum áttelepítése  

-   **Virtuálisalkalmazás-csomagok**  

    -   Gyűjteményáttelepítés  

    -   Objektumáttelepítés  

    > [!IMPORTANT]  
    >  Habár az objektumok áttelepítésével a virtuális alkalmazáscsomagok áttelepítése is lehetséges, ezen csomagokat az **Előzőleg áttelepített objektum áttelepítése** áttelepítési feladattípus használatával nem telepítheti át, ehelyett törölnie kell az áttelepített virtuális alkalmazási csomagot a célhelyről, majd új áttelepítési feladatot kell létrehoznia a virtuális alkalmazás áttelepítéséhez.  

##  <a name="About_Migration_Jobs"></a>Az áttelepítési feladatok tervezésének általános szabályai  
 Az áttelepítési feladat létrehozása varázsló segítségével hozzon létre a célhierarchiába áttelepítendő objektumok áttelepítési feladatot. A létrehozandó áttelepítési feladat típusa meghatározza, hogy mely objektumok érhetők el az áttelepítéshez. Hozzon létre, és több áttelepítési feladatot használja az adatok áttelepítéséhez, ugyanazon forráshely vagy több forráshely. Adott típusú áttelepítési feladat használata nem gátolja meg, hogy egy más típusú áttelepítési feladatot is használjon.  

 Miután egy áttelepítési feladat sikeresen lefutott, az **Kész** állapottal jelenik meg, és nem futtatható újra, azonban az eredeti feladat által áttelepített bármely objektum áttelepítéséhez létrehozhat új áttelepítési feladatot, amelyben további objektumokat is szerepeltethet. További áttelepítési feladatok létrehozásakor az előzőleg áttelepített objektumok állapotának megjelenítése **áttelepítve**. Kiválaszthatja áttelepítésre újra őket, de csak az objektum frissült a forráshierarchiában, kijelölheti nincs szükség. Az **Áttelepítés után módosult objektumok** áttelepítési feladattípus használata esetén azonosíthatja azon objektumokat, amelyek frissültek eredeti áttelepítésük óta.  

 Az áttelepítési feladatokat futtatásuk előtt törölheti, Azonban áttelepítési feladat befejezése után azt a Configuration Manager-konzolon látható marad, és nem lehet törölni. Minden áttelepítési feladat befejeződött vagy még nem futott a Configuration Manager konzolban látható marad az áttelepítési folyamat befejeződését, és az áttelepítési adatok eltávolításáig.  

> [!NOTE]  
>  Áttelepítés használatával befejezése után a **áttelepítési adatok törlése** művelet, újrakonfigurálhatja ugyanazon hierarchiát az aktuális forráshierarchia előzőleg áttelepített objektumok ismételt láthatóvá tételéhez.  

 Jelölje ki az áttelepítési feladatot, és lehetőséget választja a Configuration Manager konzolján bármely áttelepítési feladat tartalmazott objektumokat megjelenítheti a **objektumok a feladatban** fülre.  

 A következő részek segítséget nyújtanak az összes áttelepítési feladat tervezéséhez.  

### <a name="data-selection"></a>Adatok kijelölése  
 Gyűjteményáttelepítési feladatok létrehozásakor ki kell jelölnie egy vagy több gyűjteményt. Miután kiválasztotta a gyűjteményeket, az áttelepítési feladat létrehozása varázsló megjeleníti a gyűjteményekhez társított objektumokat. Alapértelmezés szerint települnek át a kijelölt gyűjteményekhez társított összes objektumot, de az objektumokat, amelyeket nem szeretne áttelepíteni az adott feladattal jelölését. Ha olyan objektum, amely függő objektumok tartoznak, akkor törölje a jelet, ezek a függőségi viszonyban lévő objektumok is sincs bejelölve. Minden ellenőrizetlen objektumok egy kizárási listába kerülnek. és a rendszer eltávolítja azokat a jövőbeli áttelepítési feladatok esetén automatikusan kijelölt objektumok közül. Amennyiben szeretné automatikusan áttelepítésre kijelölni ezeket az objektumokat a jövőbeli áttelepítési feladatokhoz, kézzel kell eltávolítania azokat a kizárási listából.  

### <a name="site-ownership-for-migrated-content"></a>Az áttelepített tartalmat tulajdonló hely  
 Ha központi telepítésekhez telepít át tartalmakat, a tartalomobjektumot hozzá kell rendelnie a célhierarchia egy helyéhez. A hely ezután a tartalom tulajdonosa lesz a célhierarchiában. Habár a tartalom metaadatainak áttelepítését valójában a célhierarchia legfelső szintű helye végzi, a hozzárendelt hely fér hozzá a tartalom eredeti forrásfájljaihoz a hálózaton keresztül.  

 Az áttelepítésekor használt sávszélesség minimálisra csökkentése érdekében érdemes a tartalom tulajdonjogát a legközelebbi rendelkezésre álló helynek átadni. A tartalommal kapcsolatos információk megosztása globális jellegű a System Center Configuration Managerben, mert azok elérhetők lesznek minden helyen.  

 Tartalommal kapcsolatos információk minden hely számára a célhierarchiában történő megosztása adatbázis-replikáció. Azonban az elsődleges hely hozzárendelése és majd más elsődleges helyeken lévő terjesztési pontokra központilag telepített tartalmak átvitelére fájlalapú replikációval. Az átvitel során az adatok a központi adminisztrációs helyen keresztül jutnak el a további elsődleges helyekhez. Központosítja azokat a csomagokat, amelyeket terjeszteni több elsődleges helyhez áttelepítés előtt vagy közben rendel egy helyet a tartalom tulajdonosaként, csökkentheti adatátvitelek alacsony sávszélességű hálózatokon keresztül.  

### <a name="role-based-administration-security-scopes-for-migrated-data"></a>Az áttelepített adatokra vonatkozó szerepköralapú adminisztrációs biztonsági hatókörök  
 Amikor adatokat telepít át egy célhierarchiába, kell rendelnie egy vagy több szerepköralapú adminisztrációs biztonsági hatókörök az objektumokat, amelyek adatait áttelepíti. Ez biztosítja, hogy az áttelepítést követően csak a megfelelő rendszergazda felhasználók férhessenek hozzá ezen adatokhoz. A megadott biztonsági hatóköröket az áttelepítési feladat definiálja, és a rendszer az összes, az adott feladat által áttelepített objektumra alkalmazza azokat. Ha más biztonsági hatóköröket szeretne alkalmazni az objektumok különböző csoportjaira van szüksége, és szeretne hozzárendelni ezeket az áttelepítés során, át kell telepítenie az objektumok különböző csoportjaira eltérő áttelepítési feladatok használatával.  

 Áttelepítési feladat beállítása előtt tekintse át a szerepköralapú Adminisztráció működését a System Center Configuration Managerben. Szükség esetén állítsa be a vezérlőre, kik rendelkezzenek hozzáféréssel az áttelepített objektumokhoz a célhierarchiában áttelepíthető adatok egy vagy több biztonsági hatókört.  

 Biztonsági hatókörökkel és szerepköralapú felügyelettel kapcsolatban bővebben lásd: [szerepkör alapú felügyelet a System Center Configuration Manager – alapok](../../core/understand/fundamentals-of-role-based-administration.md).  

### <a name="review-migration-actions"></a>Áttelepítési műveletek áttekintése  
 Ha beállít egy áttelepítési feladat, az áttelepítési feladat létrehozása varázsló jeleníti meg, azokat, amelyek a sikeres áttelepítés biztosítása érdekében el kell végeznie, és azokat, amely a Configuration Manager a kijelölt adatok áttelepítése során. Tekintse át ezt az információt gondosan ellenőrizze a várt eredményt kapja.  

### <a name="schedule-migration-jobs"></a>Áttelepítési feladatok ütemezése  
 Az áttelepítési feladatok alapértelmezés szerint létrehozásukat követően azonnal elindulnak, Azonban ha az áttelepítési feladat fut, a feladat létrehozásakor, vagy a feladat tulajdonságainak szerkesztésével is megadhat. Ütemezheti az áttelepítési feladat futtatásához a következőképpen:  

-   Futtassa most az áttelepítési feladatot  

-   Feladat futtatása adott kezdési időpontban  

-   Ne futtassa az áttelepítési feladatot  

### <a name="specify-conflict-resolution-for-migrated-data"></a>Az áttelepített adatokra vonatkozó ütközésfeloldás megadása  
 Alapértelmezés szerint az áttelepítési feladatok nem írja felül a céladatbázis adatait csak az áttelepítési feladat adatbázist az előzőleg áttelepített adatok kihagyására vagy felülírására.  

##  <a name="About_Collection_Migration "></a>Gyűjtemény áttelepítési feladatainak tervezése  
 Gyűjtemények áttelepítési feladatai csak akkor, ha a Configuration Manager 2007 támogatott verzióját futtató forráshierarchia adatainak áttelepítésére érhetők el. Gyűjteménnyel való áttelepítéskor meg kell adni egy vagy több áttelepítendő gyűjteményt. Az egyes megadott műveleteknél az áttelepítési feladat automatikusan kiválasztja az áttelepítéshez kapcsolódó összes objektumot. Például felhasználó-gyűjtemény választásakor sor kerül a gyűjtemény tagjainak automatikus kiválogatására, és a gyűjteményhez társított központi telepítések áttelepíthetők. A tagokkal együtt történő áttelepítésre, nem kötelezően, kijelölhetők más központi telepítési objektumok is. Minden ilyen kijelölt elem felkerül az áttelepíthető objektumok listájára.  

 Gyűjtemény áttelepítésekor System Center Configuration Manager is áttelepíti a gyűjtemény beállításait, beleértve a karbantartási időszakok és a gyűjtemény változói, de azt nem lehet áttelepíteni a gyűjtemény beállításait az AMT kiépítéséhez.  

 Az alábbi szakaszokban található információk segítségével további információkhoz további beállításokat, amelyek használhatók a gyűjtemény alapú áttelepítési feladatokat.  

### <a name="exclude-objects-from-collection-migration-jobs"></a>Objektumok kizárása a gyűjtemény áttelepítési feladataiból  
 Egyes objektumok kizárhatók a gyűjtemény áttelepítési feladataiból. Ha egy adott objektumához kizárása a gyűjtemény áttelepítési feladataiból, hogy az objektum olyan globális kizárási listára, amely rendelkezik az összes objektum, amely az aktuális forráshierarchia valamelyik forráshelyén létrehozott áttelepítési feladatból kizárt kerül. A kizárási listán szereplő objektumok továbbra is elérhetők a jövőbeli áttelepítési feladatok, de nincsenek automatikusan egy új gyűjtemény alapú áttelepítési feladat létrehozásakor.  

 A kizárási listából szerkesztéssel eltávolíthatók a korábban kizárt objektumok. Ha új áttelepítési feladat létrehozásakor megad egy kapcsolódó gyűjteményt, a kizárási listából eltávolított objektum ismét automatikusan ki lesz választva.  

### <a name="unsupported-collections"></a>Nem támogatott gyűjtemények  
 A Configuration Manager telepíthet át az alapértelmezett felhasználói gyűjtemények, eszközgyűjtemények és a legtöbb egyéni gyűjtemény bármelyikét a Configuration Manager 2007 verziójú forráshierarchia. Azonban a Configuration Manager nem telepíthető át gyűjteményt, amelyikben felhasználók és eszközök szerepelnek.  

 A következő gyűjteményeket nem lehet áttelepíteni:  

-   Olyan gyűjtemény, amelyikhez a felhasználók és eszközök számára.  

-   A gyűjtemény egy másik erőforrástípust gyűjteményre hivatkozik. Például egy eszköz alapú gyűjteményt, amelyik tartalmaz algyűjteményt vagy felhasználó alapú gyűjteményre mutató hivatkozást. Ebben a példában csak a legfelső szintű gyűjtemény lesz telepítve.  

-   A gyűjtemény egy ismeretlen számítógépeket bevonó szabályt tartalmaz. A gyűjtemény áttelepítődik, de az ismeretlen számítógépeket bevonó szabály nem.  

### <a name="empty-collections"></a>Üres gyűjtemények  
 Az üres gyűjtemény olyan gyűjtemény, amelyikhez nincs társítva erőforrás. Üres gyűjtemény áttelepítésekor a Configuration Manager átalakítja a gyűjteményt egy szervezeti mappává, nem rendelkezik olyan felhasználók vagy eszközök. Ez a mappa az üres gyűjtemény nevével jön létre a **Felhasználógyűjtemények** vagy **Eszközgyűjtemények** csomópontja a **eszközök és megfelelőség** munkaterület a Configuration Manager konzolon.  

### <a name="linked-collections-and-subcollections"></a>Csatolt gyűjtemények és algyűjtemények  
 Gyűjtemények, amelyik másik gyűjteményhez van csatolva vagy algyűjteménnyel rendelkezik áttelepítésekor a Configuration Manager létrehoz egy mappát a **Felhasználógyűjtemények** vagy **Eszközgyűjtemények** csomópont kiegészítve a csatolt gyűjteményt vagy az algyűjteményt.  

### <a name="collection-dependencies-and-include-objects"></a>Gyűjtemény függőségei és belefoglalt objektumok  
 Amikor megad egy áttelepítési feladat létrehozása varázslóban áttelepítendő gyűjteményt, a függő gyűjtemények automatikusan kijelölt hogy bekerüljenek a feladatba. Ez a viselkedés garantálja, hogy az áttelepítés után rendelkezésre álljon minden szükséges erőforrás.  

 Példa: Az eszközök, Windows 7 rendszerű, és nevű gyűjtemény választja **Win_7**. Ez a gyűjtemény egy gyűjteményt, amely rendelkezik az ügyfél operációs rendszerek és nevű korlátozódik **minden_ügyfél**. A gyűjtemény **minden_ügyfél** automatikusan kijelöli az áttelepítéshez.  

### <a name="collection-limiting"></a>Gyűjteménykorlátozás  
 A System Center Configuration Managerrel, a gyűjtemények globális adatok, és kiértékelésük a hierarchia mindegyik helyén. Ezért meg kell tervezni, hogy a gyűjtemény hatóköre hogyan legyen korlátozva az áttelepítése után. Áttelepítéskor kiválaszthat egy gyűjteményt a forráshierarchiából, hogy azzal úgy korlátozza az áttelepítendő gyűjteményt, hogy az áttelepítésbe ne kerüljenek be a nem kívánt tagjai.  

 Például a Configuration Manager 2007 gyűjtemények kiértékelése az őket létrehozó helynél és az alárendelt helyekre. Lehet, hogy egy reklám a központi telepítésben csak egy alárendelt helyre került, és így a reklám hatóköri korlátja vonatkozhatna az alárendelt helyre. Szemben, a System Center Configuration Managerrel gyűjtemények kiértékelése az egyes helyeken és a társuló reklámok majd értékeli ki a rendszer minden egyes hely esetében. A gyűjteménykorlátozás lehetővé teszi a gyűjtemény tagjainak más gyűjteményen alapuló szűkítését, hogy elkerülhető legyen a gyűjtemény nem kívánt tagjainak a bekerülése.  

### <a name="site-code-replacement"></a>Helykódcsere  
 Olyan gyűjtemény, amelyikhez feltétel, amely azonosítja a Configuration Manager 2007 helyen áttelepítésekor a rendeltetési hierarchiában egy megadott hely kell megadnia. Ez garantálja, hogy az áttelepített gyűjtemény működőképes maradjon a rendeltetési hierarchiában, és a hatókörében ne növekedjen.  

### <a name="specify-behavior-for-migrated-advertisements"></a>Az áttelepített hirdetmények viselkedésének megadása  
 Alapértelmezés szerint a gyűjtemény alapú áttelepítési feladatok letiltása a rendeltetési hierarchiába áttelepülő hirdetményeket. Ebbe beletartozik minden olyan program, ami a hirdetménnyel társítva lett. Amely olyan gyűjtemény alapú áttelepítési feladatot hoz létre, ha megjelenik a **programok a Configuration Manager központi telepítésének engedélyezése a hirdetmény forráshierarchiából való áttelepítése után** beállítást a **beállítások** az áttelepítési feladat létrehozása varázsló. Ha ezt választja, a hirdetményhez kapcsolódó programok az áttelepítésük után engedélyezettek lesznek. Ajánlott eljárásként csak akkor válassza ezt a beállítást. Ehelyett engedélyezése a programokat, amikor ellenőrizheti, hogy az ügyfelek, akik szintén megkapják áttelepítésük után.  

> [!NOTE]  
>  Megjelenik a **programok a Configuration Manager központi telepítésének engedélyezése a hirdetmény forráshierarchiából való áttelepítése után** beállítás, csak ha hoz létre egy gyűjtemény alapú áttelepítési feladatot, és az áttelepítési feladat hirdetményeket tartalmaz.  

 A program áttelepítés utáni engedélyezéséhez törölje a jelet **tiltsa le a program a számítógépeken, ahol hirdetménnyel telepítették** a a **speciális** a program tulajdonságok lapon.  

##  <a name="About_Object_Migration"></a>Objektumok áttelepítési feladatainak tervezése  
 A gyűjtemények áttelepítésétől eltérően az áttelepíteni kívánt minden egyes objektumot és objektumpéldányt ki kell választani. Az egyéni objektumokat, például (hirdetmények a Configuration Manager 2007-hierarchiából) vagy egy kiadvány kiválaszthatja a System Center 2012 Configuration Manager vagy a System Center Configuration Manager hierarchiából felvétele egy adott áttelepítési feladat áttelepítendő objektumainak listájára. Az áttelepítési listába fel nem vett objektumokat az áttelepítési feladat nem telepíti át a rendeltetésként megadott helyre.  

 Objektum alapú áttelepítési feladat nem rendelkezik semmilyen további konfigurálás használhatókon az áttelepítési feladatok megtervezése.  

##  <a name="About_Object_Migrations"></a>Előzőleg áttelepített objektumok áttelepítési feladatainak tervezése  
 Ha a rendeltetési hierarchiába már áttelepített valamelyik objektum frissül a forráshierarchiában, az az objektum újra áttelepíthető egy **Áttelepítés után módosult objektumok** típusú feladattal. Például ha átnevezi vagy frissíti a forrásfájlokat egy csomagot a forráshierarchiában, a csomag változatszáma megnövekszik a forráshierarchiában. Miután megnövekedett a csomag verziószáma, ez a feladattípus kiválaszthatja áttelepítésre.  

 Ez a feladattípus hasonló az objektum-áttelepítési típushoz, azzal a különbséggel, hogy az áttelepítendő objektumok kiválasztásakor csak azon objektumok közül lehet választani, amelyek már frissültek az előző áttelepítési feladattal az áttelepítésük óta.   

 Ha bejelöli ezt a feladattípust, az Ütközésfeloldó viselkedés a a **beállítások** felülírja az előzőleg áttelepített objektumokat az áttelepítési feladat létrehozása varázsló van konfigurálva. Ez a beállítás nem módosítható.  

> [!NOTE]  
>  Ez az áttelepítési feladat felismeri a forráshierarchia által automatikusan frissített objektumokat és azokat, amelyiket rendszergazda frissített.  

