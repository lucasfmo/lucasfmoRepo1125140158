---
title: "Adatátviteli |} Microsoft Docs"
description: "Ismerje meg, hogyan helyezi át a Configuration Manager az adatok helyek között, és hogyan kezelheti az adatok átvitelét a hálózaton keresztül."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dc526e8d-fac3-4bb5-b206-03ad29b0ae11
caps.latest.revision: 12
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: bfe77a45b5f781611c343e06d1289add7abd2dfb
ms.openlocfilehash: bf0fdc8d4b4a72760b2cfb91231378a17df01594
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="data-transfers-between-sites-in-system-center-configuration-manager"></a>Adatátvitel a System Center Configuration Manager helyei között

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

System Center Configuration Manager használ a **fájl alapú replikációként** és **adatbázis-replikáció** különböző típusú adatok helyek közötti átviteléhez. További tudnivalók: hogyan helyezi át a Configuration Manager az adatok helyek között, és hogyan kezelheti az adatok átvitelét a hálózaton keresztül.  


## <a name="bkmk_fileroute"></a> File-based replication  
A Configuration Manager fájlalapú replikációt használ a fájlalapú adatok átviteléhez a hierarchiában lévő helyek között. Ezen adatok tartalmazzák az alkalmazások és csomagok, amelyet a gyermekhelyek terjesztési pontjaira szeretne telepíteni, és feldolgozatlan felderítési adatrekordok, amelyeket a szülőhelyekre és majd a feldolgozása.  

Helyek közötti fájlalapú kommunikáció a **Server Message Block** (SMB) protokoll a 445-ös TCP/IP-portot. Megadhat sávszélesség szabályozást és impulzusos módot a hálózaton keresztül továbbított adatmennyiséget, és az ütemezések segítségével szabályozhatja a hálózati adatküldés időpontját.  

### <a name="bkmk_routes"></a> Fájlreplikációs útvonalak  
A következő információk segítségére lehetnek beállítása és a fájlreplikációs útvonalak használata.  

#### <a name="file-replication-route"></a>Fájlreplikációs útvonal

Minden fájlreplikációs útvonal egy célhelyet, amelyre fájlalapú adatok vihetők át azonosít. Minden hely egy meghatározott célhelyre irányuló fájlreplikációs útvonalat támogat.  

A fájlreplikációs útvonalak a következő beállításokat módosíthatja:  

-  **Fájlreplikációs fiók**. Ezt a fiókot a célhely kapcsolódik, és írja az adatokat, hogy a hely **SMS_Site** megosztani. Az erre a megosztásra írt adatokat a fogadó hely dolgozza fel. Alapértelmezés szerint egy helyet a hierarchiában való felvételekor a Configuration Manager rendeli hozzá az új hely helykiszolgáló számítógépfiókjának, az adott hely fájlreplikációs fiókjaként. Ez a fiók kerül az adott hely **SMS_SiteToSiteConnection_&lt;Helykód\>**  egy helyi csoport a számítógépen, amely hozzáférést biztosít a SMS_Site megosztására. Ezt a fiókot átállíthatja Windows felhasználói fiókká. Ha módosítja a fiókot, ellenőrizze, hogy el hozzáadni az új fiókot a célhely **SMS_SiteToSiteConnection_&lt;Helykód\>**  csoport.  

    > [!NOTE]  
    >  A másodlagos helyek mindig a másodlagos hely kiszolgálójának számítógépfiókját használják **fájlreplikációs fiókként**.  

-  **Ütemezés**. Beállíthatja, hogy az ütemezés az egyes fájlreplikációs útvonalak korlátozhatja az adatok típusát és idő, amikor vihetők át az adatokat a célhelyre.  
-  **Sebességhatárok**. Megadhatja az egyes fájlreplikációs útvonalak a hely által a célhelyre történő adatátvitelhez használt hálózati sávszélesség szabályozásához sebességhatárok:  

    -  A célhelyre küldött adatblokkok méretének megadásához használja az **Impulzusos mód** beállítást. Egyes adatblokkok küldése közötti késleltetés is megadható. Használja ezt a beállítást, ha az adott hely nagyon alacsony sávszélességű hálózati kapcsolaton keresztül kell adatokat küldenie. Beállíthatja például úgy a korlátozást, hogy öt másodpercenként 1 kB adatot küldjön, de soha ne küldjön 1 kB-ot három másodperc alatt, függetlenül a kapcsolat sebességétől vagy aktuális kihasználtságától.
    -  Használja **A megadott maximális átviteli sebességre korlátozva óránként** beállítást, amennyiben azt szeretné, hogy a hely csak az idő megadott százalékában küldjön adatokat egy célhelyre. Ezt a beállítást használja, ha a Configuration Manager határozza meg a hálózaton elérhető sávszélességet, hanem osztja az adatküldés időtartamát az. Adatküldést követően olyan, rövid ideig tartó, amely idő, amikor a rendszer nem küld adatokat Időblokkok következnek. Például, ha a maximális sebesség értéke **50 %**, a Configuration Manager adott ideig adatokat küld egy meghatározott, majd egy nem történik adatküldés ugyanannyi ideig szünetelteti. Nem felügyelt adatok tényleges mérete mennyisége vagy az adatblokk méretét. Ehelyett csak az adatküldés idejének kezelésére kerül sor.  

        > [!CAUTION]  
        > Egy hely alapértelmezés szerint három **párhuzamos küldést** képes használni a célhelyre történő adatátvitelhez. Amikor sebességhatárt ad meg egy fájlreplikációs útvonalhoz, a **párhuzamos küldés** az adott helyre történő adatküldés esetén egyre korlátozódik. Ez akkor is igaz, ha a **Rendelkezésre álló sávszélesség korlátozása (%)** beállítást **100%**-ra állítja. Például ha az alapértelmezett beállításokat használja a küldőhöz, ez csökkenti az átviteli sebességet a célhelyre az alapértelmezett teljesítmény egyharmad.  

-  Fájlalapú tartalom átviteléhez egy fájlreplikációs útvonalat konfigurálhat két másodlagos hely között.  

Egy fájlreplikációs útvonalhoz, kezelhetik a **felügyeleti** munkaterületet, bontsa ki a **Hierarchiakonfiguráció** csomópont, és válassza **fájlreplikáció**.  

#### <a name="sender"></a>Feladó

Minden hely egy küldővel rendelkezik. A küldő kezeli a hálózati kapcsolatot egy hely és egy célhely között, és egyidejűleg több hellyel képes kapcsolatot létrehozni. A helyhez való kapcsolódáshoz a küldő a helyre vezető fájlreplikációs útvonalat használja, ennek segítségével azonosítja a fiókot, amelyet a hálózati kapcsolat létrehozásához kell használnia. A küldő ezt a fiókot is használja az adatok írása az adott hely SMS_Site megosztására.  

A küldő alapértelmezés szerint több **párhuzamos küldést**használva írja az adatokat a célhelyre. Ezeket általában szálnak nevezik. Minden egyes párhuzamos küldés (vagy szál) egy eltérő fájlalapú objektumot képes a célhelyre másolni. Alapértelmezés szerint, amikor a küldő megkezdi egy objektum küldését, folyamatosan írja az adott objektum adatblokkjait, amíg a teljes objektumot el nem küldte. Miután az adott objektumhoz tartozó összes adatot elküldte, egy új objektum küldése kezdődhet meg az adott szálon.  

A küldőhöz a következő beállításokat módosíthatja:  

-  **Maximális párhuzamos küldés**. Alapértelmezés szerint minden hely használja öt párhuzamos küldések számát, amelyek közül hármat akkor használ, amikor adatokat küld valamelyik célhelyre. Az értéknek a növelésével emelheti a közti adatátvitel sebességét, helyek, mert a Configuration Manager a egyszerre több fájlt továbbítson is. Ugyanakkor az érték növelésével a helyek közti hálózati sávszélesség iránti igény is növekszik.  

-  **Ismétlés beállításai**. Alapértelmezés szerint minden hely újrapróbálja csatlakozási probléma esetén kétszer, egy perc késleltetéssel a csatlakozási kísérletek között. Módosíthatja a csatlakozási kísérleteinek száma a helyet, és a próbálkozások közti várakozási idő.  

Kezelhetik a helyhez, a küldő a **felügyeleti** munkaterületet, bontsa ki a **Helykonfiguráció** csomópontban jelölje ki a **helyek** csomópont, és válassza **tulajdonságok** a kezelni kívánt helyhez. Válassza ki a **küldő** lapon a küldő beállításainak módosításához.  

## <a name="bkmk_dbrep"></a> Database replication  
A Configuration Manager adatbázis-replikáció az SQL Server, adatátvitelt, és a hely adatbázisában a hierarchia más helyeinek adatbázisaiban tárolt adatokkal végrehajtott változtatásokat. Vegye figyelembe a következő adatbázis-replikációval kapcsolatos:

-  Az összes hely ugyanazokat az információkat osztozik.  
-  Amikor helyet telepít egy hierarchiában, az adatbázis-replikáció automatikusan jön létre az új hely és a kijelölt szülőhely között.  
-  Ha a hely telepítése befejeződik, adatbázis-replikáció automatikusan elindul.  

Amikor új helyet ad hozzá a hierarchia, Configuration Manager létrehoz egy általános adatbázist az új helyen. Ezután a szülőhely pillanatképet hoz létre a vonatkozó adatok az adatbázisában, és majd átviszi a pillanatkép az új hely fájl alapú replikációként. Az új hely majd használja az SQL Server tömeges másolási Program (BCP) betölti az információt a Configuration Manager-adatbázis helyi példányába. A pillanatkép betöltése után minden hely adatbázis-replikációt végez a másik hellyel.  

Az adatok helyek közti replikálásához, a Configuration Manager használ a saját adatbázis-replikációs szolgáltatás. Az adatbázis-replikációs szolgáltatás az SQL Server változáskövetési funkciójával figyeli a helyi adatbázis módosításait, és azután replikál a többi hely felé az SQL Server Service Broker (SSB) használatával. Ez a folyamat alapértelmezés szerint a 4022-es TCP/IP-portot használja.  

A Configuration Manager replikációs csoportokba adatbázis-replikáció útján replikált adatokat. Vegye figyelembe a következő replikációs csoportok:

-  Minden replikációs csoportnak külön, rögzített replikációs ütemezése van, amely meghatározza, hogy a rendszer milyen gyakran replikálja a csoportban levő adatok módosításait a többi hely felé.  

     Például egy a szerepköralapú adminisztrációs beállítások módosításait gyorsan replikálja más helyekre, annak érdekében, hogy érvénybe lépjenek a lehető leghamarabb. Eközben alacsonyabb prioritású konfigurációs változás, például egy új másodlagos hely telepítési kérését nem replikálja olyan sürgősen. Egy új hely iránti kérés elér a célként megadott elsődleges helyre több percet is igénybe vehet.  

-   Az adatbázis-replikáció a következő beállításokat módosíthatja:  

    -  **Adatbázis-replikációs hivatkozások**. Ha adott a forgalom halad át a hálózati vezérlő.  
    -  **Elosztott nézetek**. Módosítsa a beállításokat, amellyel kérelmeit, amelyeket a kijelölt helyadatok esetében egy központi adminisztrációs helyen is vonatkozóan közvetlenül elérje a gyermek elsődleges helyek adatbázis-replikációs hivatkozások esetében.  
    -  **Ütemezések**. Adja meg a replikációs hivatkozás használatakor, valamint a helyadatok különböző típusainak replikációja mikor történjen.  
    -  **Összegzési**. Adatok összegzési, amely áthalad a replikációs hivatkozásokat tartalmazó hálózati forgalommal kapcsolatos beállításainak módosítása. Összegzési alapértelmezés szerint 15 percenként történik, és az adatbázis-replikációs jelentésekben használatos.  
    -  **Adatbázis-replikáció küszöbértékei**. Adja meg, amikor hivatkozások rendszer csökkentett teljesítményűnek vagy sikertelen volt. Is konfigurálhatja, amikor a Configuration Manager riasztást küld állapotú csökkentett teljesítményű vagy sikertelen replikációs hivatkozások.  

A Configuration Manager osztályozza a, vagyis az adatbázis-replikáció útján replikált adatokat **globális adatok** vagy **helyadatok**. Az adatbázis-replikáció során az adatbázis-replikációs hivatkozáson keresztül történik a globális és a helyadatok módosításainak továbbítása. Globális adatok a szülő és gyermek hely replikálhatja. Helyadatok csak a szülőhely felé replikálja. Egy harmadik adattípus, helyi adatok nem replikálja más helyekre. Helyi adatok információt, amely a többi helynek nincs szükség. Vegye figyelembe a következő adattípusokkal kapcsolatban:  

-  **Globális adatok**. A másodlagos helyek ezeknek a globális adatok, globális proxyadatokként csak egy részhalmazát kapják meg a globális adatok a rendszergazdák által létrehozott objektumok, amelyek a hierarchia összes helyére replikálódnak hivatkozik. Globális adatok tartalmazzák a szoftverek központi telepítései, a szoftverfrissítések, a gyűjteménymeghatározások és a szerepköralapú adminisztrációs biztonsági hatókörök. A rendszergazdák a központi adminisztrációs helyen és az elsődleges helyeken hozhatnak létre globális adatokat.  
-  **Helyadatok**. Helyadatok azok az operatív információk, hogy a Configuration Manager elsődleges hely és az ügyfelek, az elsődleges helyekhez jelentés létrehozása. A helyadatok replikálódnak a központi felügyeleti hely részére, de más elsődleges helyek részére nem. Helyadatok közé tartoznak a Hardverleltár-adatait, az állapotüzeneteket, a riasztások és a lekérdezés alapú gyűjtemények eredményei. Helyadatok csak akkor megtekinthető, a központi adminisztrációs helyen és az elsődleges hely, ahonnan az adatok származnak. A helyadatot csak azon az elsődleges helyen lehet módosítani, ahol létrehozták.  

     Minden a helyadatok replikálódnak a központi adminisztrációs helyhez. A központi adminisztrációs hely felügyelet és a jelentéskészítést az egész helyhierarchiára az hajt végre.  

A következő részek a beállításokat, módosíthatja az adatbázis-replikáció kezelésére.  

### <a name="bkmk_Dblinks"></a> Adatbázis-replikációs hivatkozások  
Amikor új helyet telepít egy hierarchiában, a Configuration Manager automatikusan létrehoz egy adatbázis-replikációs hivatkozás a szülőhely és az új hely között. Létrejön egy hivatkozás, akkor a két hely kapcsolódni.  

Minden adatbázis-replikációs hivatkozás a replikációs hivatkozáson keresztül az adatok átvitelét szabályozásához beállításait módosíthatja. Minden replikációs hivatkozásnak külön beállításai vannak. Az adatbázis-replikációs hivatkozások esetében a következő vezérlők használhatók:  

-  Replikációleállítási a kijelölt hely adatainak a központi adminisztrációs hely egy elsődleges helyről, a központi adminisztrációs hely közvetlenül az elsődleges hely adatbázisából hozzáférnének ehhez ezen adatokhoz.  
-  Ütemezheti a kijelölt helyadatok átvitele a gyermek elsődleges helyek a központi adminisztrációs hely.
-  Megadhatja azokat a beállításokat, amelyek meghatározzák, ha egy adatbázis-replikációs hivatkozás csökkentett teljesítményű állapotba került, vagy sikertelen volt.
-  Adja meg, mikor kell riasztást kiadni egy sikertelen replikációs hivatkozás.
-  Adja meg, hogy milyen gyakran összegezze a Configuration Manager a replikációs hivatkozást használó replikációs forgalommal kapcsolatos adatokat. Ezek az adatok a jelentésekhez kellenek.

Adatbázis-replikációs hivatkozások, a Configuration Manager konzolon konfigurálhatja a a **adatbázis-replikáció** csomópont, a hivatkozás tulajdonságait szerkesztheti. Ebben a csomópontban jelenik meg, mindkét típusú lista a **figyelés** munkaterület és a **felügyeleti** munkaterületen, a a **Hierarchiakonfiguráció** csomópont. A replikációs hivatkozás a megfelelő szülő vagy gyermekhelyen is szerkeszthető.  

> [!TIP]  
> Az adatbázis-replikációs hivatkozások az **Adatbázis-replikáció** csomópontból szerkeszthetők a fenti két munkaterület bármelyikén. Azonban ha használja a **adatbázis-replikáció** csomópontja a **figyelés** munkaterületen, akkor is is megtekintheti az adatbázis-replikáció állapotát, és elérheti a Replication Link Analyzer eszköz segítségével megvizsgálhatja az adatbázis-replikációval kapcsolatos problémákat.  

További információ a replikációs hivatkozások beállításáról: [Helyadatbázisok replikációjának vezérlői](#BKMK_DBRepControls). További információ a replikálás figyeléséről: [adatbázis replikációs hivatkozások és a replikációs állapot figyelése](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md#BKMK_MonitorRepLinksAndStatuss) a a [figyelő hierarchia és replikációs infrastruktúra a System Center Configuration Managerben](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md) témakör.  

Olvassa el az alábbi szakaszok az adatbázis-replikációs hivatkozások tervezéséhez nyújtanak segítséget.  

### <a name="bkmk_distviews"></a> Elosztott nézetek  
Elosztott nézetek választott a webhely adatelérési kérelmeit, amelyeket a központi adminisztrációs helyen vonatkozóan közvetlenül egy gyermek elsődleges hely adatbázisából. A közvetlen hozzáférés feleslegessé adatainak történő replikálásához, hogy az elsődleges helyről a központi adminisztrációs helyhez. Minden replikációs hivatkozás nem függ egymástól, mert az csak a replikációs hivatkozások esetében az Ön által az elosztott nézetek is használhatja. Nem használhat elosztott nézeteket egy elsődleges és másodlagos hely között.  

Az elosztott nézetek előnyei a következők:  

-  Csökkentik a CPU-terhelést a központi adminisztrációs helyen és elsődleges helyek adatbázis-változások feldolgozása
-  Kevesebb adatot kell továbbítani a hálózaton a központi adminisztrációs hely
-  A központi adminisztrációs hely adatbázisát futtató SQL server teljesítményének növelése
-  Kevesebb lemezterületet használ a központi adminisztrációs hely adatbázisa

Fontolja meg az elosztott nézeteket használni, ha az elsődleges hely közel vannak a központi adminisztrációs helyhez a hálózaton, és a két hely mindig, és folyamatos kapcsolatban állnak. Ennek az az oka az elosztott nézetek replikálni a kijelölt adatokat az egyes helyek SQL Server kiszolgálói közti közvetlen kapcsolatokon keresztül a helyek között. A közvetlen kapcsolat minden alkalommal, amikor ezek az adatok kérik a központi adminisztrációs helyen. Általában előfordulhat, hogy engedélyezi az elosztott nézetek adatok kérések futtatásakor jelentéseket vagy lekérdezéseket készítenek, az erőforrás-kezelőben, és csak a gyűjtemény azon gyűjtemények értékelése esetén, amelyek a helyadatok alapuló szabályokat tartalmaznak adatainak megtekintésekor.  

Alapértelmezés szerint az elosztott nézetek ki az összes replikációs hivatkozás meg vannak kapcsolva. Ha bekapcsolja az elosztott nézeteket egy replikációs hivatkozásra, kiválasztja azokat a helyadatokat, amelyek nem replikálja a központi adminisztrációs helyen adott hivatkozáson keresztül. A központi adminisztrációs hely közvetlenül a hivatkozáshoz elsődleges gyermekhely adatbázisából éri el ezeket az adatokat. Az alábbi típusú helyadatokra lehet beállítani az elosztott nézeteket:  

-  az ügyfelek hardverleltáradatai
-  az ügyfelek szoftverleltár- és mérési adatai
-  az ügyfelek, az elsődleges hely és az összes másodlagos hely állapotüzenetei

Működés közben az elosztott nézetek nem láthatók azon rendszergazda felhasználó számára, akik megtekinti az adatokat, a Configuration Manager konzolon vagy a jelentésekben. Amikor egy kérelem adatokat, az elosztott nézetek számára engedélyezve van, a a közvetlenül a központi adminisztrációs hely adatbázisát futtató SQL server hozzáfér az SQL server, és lekéri az információkat az alárendelt elsődleges hely. Például a használata a Configuration Manager konzol a központi adminisztrációs hely Hardverleltár-adatokat kér két helytől, és csak az egyik hely esetében van engedélyezve a hardverleltárra az elosztott nézet. Az ahhoz a helyhez tartozó ügyfelek leltáradatait, amely nincs beállítva az elosztott nézetek számára, a központi adminisztrációs hely adatbázisából kéri le a rendszer. Az elosztott nézetek konfigurált helyhez tartozó ügyfelek leltáradatait érhető el az alárendelt elsődleges hely adatbázisából. Ez az információ a Configuration Manager konzolon vagy a jelentésekben jelenik meg a forrás azonosítása nélkül.  

Mindaddig, amíg egy replikációs hivatkozás esetében van valamilyen adatra az elosztott nézetek számára engedélyezve van, az elsődleges gyermekhely nem replikálja az adatokat a központi adminisztrációs hely. Amint kikapcsolják az elosztott nézeteket valamelyik adattípusra vonatkozóan, az elsődleges gyermekhely folytatja a replikálást az adatok a központi adminisztrációs hely felé a rendes adatreplikáció részeként. Azonban mielőtt ezeket az adatokat a központi adminisztrációs helyen érhető el, ezek az adatok replikációs csoportok újra kell inicializálni az elsődleges hely és a központi adminisztrációs hely között. Hasonlóképpen Miután eltávolít egy elsődleges helyet, amelyen engedélyezve van az elosztott nézetek, a központi adminisztrációs hely kell végeznie az adatok újrainicializálása, amelyekre engedélyezve voltak az elosztott nézeteket a központi adminisztrációs helyen lévő adatok eléréséhez.  

> [!IMPORTANT]  
> Ha a webhely-hierarchia bármelyik replikációs hivatkozása elosztott nézeteket használ, ki kell kapcsolnia az összes replikációs hivatkozás esetében az elosztott nézetek és el szeretné távolítani valamelyik elsődleges helyet. További információ: [Elosztott nézetekkel konfigurált elsődleges hely eltávolítása](../../../core/servers/deploy/install/uninstall-sites-and-hierarchies.md#BKMK_UninstallPrimaryDistViews).  

#### <a name="prerequisites-and-limitations-for-distributed-views"></a>Elosztott nézetekre vonatkozó Előfeltételek és korlátozások  

-  Az elosztott nézetek csak a központi adminisztrációs hely és elsődleges hely közti replikációs hivatkozások is használhatja.
- A központi adminisztrációs hely az SQL Server rendszer Enterprise verzióján kell használnia. Az elsődleges hely nem rendelkezik az ennek a követelménynek.
-  A központi adminisztrációs helyen csak egy példányban lehet telepítve SMS szolgáltató, és annak a példánynak a helyadatbázis-kiszolgálón kell lennie. Ez azért szükséges, hogy az SQL server, a központi adminisztrációs helyen elérhessék az SQL server, a gyermek elsődleges hely szükséges a Kerberos-hitelesítés támogatásához. Az elsődleges gyermekhelyen levő SMS szolgáltatóra vonatkozóan nincs korlátozás.
-  A központi adminisztrációs helyen csak egy SQL Server jelentéskészítési szolgáltatási pont lehet telepítve, és annak a helyadatbázis-kiszolgálón kell lennie. Ez elengedhetetlen ahhoz, hogy az SQL server, a központi adminisztrációs helyen, a gyermek elsődleges hely SQL-kiszolgáló eléréséhez szükséges a Kerberos-hitelesítés támogatásához.
-  A helyadatbázis nem futhat egy SQL Server fürtön.
-  A Helyadatbázis nem futhat egy SQL Server Always On rendelkezésre állási csoporthoz.
-  A központi adminisztrációs hely adatbázis-kiszolgáló számítógépfiókjának olvasási engedélyekkel kell rendelkeznie a helyadatbázist az elsődleges hely.

> [!IMPORTANT]  
>  Az elosztott nézetek és az adatreplikálási ütemezés amikor adatokat képes replikálni, amely az adatbázis-replikációs hivatkozások egymást kölcsönösen kizáró beállítások láthatók.  

### <a name="BKMK_schedules"></a> Helyadat-átvitel ütemezése az adatbázis-replikációs hivatkozások esetében  
A gyermek típusú elsődleges hely adatainak a központi adminisztrációs helyre történő replikálásához használt hálózati sávszélesség szabályozásához beütemezheti, hogy mikor használandók a replikációs hivatkozások, és megadhatja, hogy mikor történjen meg a különböző típusú helyadatok replikálása. Azt is szabályozhatja, hogy az elsődleges hely mikor replikálja az állapotüzeneteket, a leltáradatokat és a mérési adatokat. A másodlagos helyekről létrehozott adatbázis-replikációs hivatkozások nem támogatják az ütemezést a helyadatoknál. A globális adatok átvitele nem ütemezhető.  

Az adatbázis-replikációs hivatkozás ütemezésének konfigurálásakor korlátozhatja a kiválasztott helyadatok átvitelét az elsődleges helyről a központi adminisztrációs helyre, és különböző időpontokat állíthat be a különböző típusú helyadatok replikálásához.  

> [!IMPORTANT]  
> Egy adatbázis-replikációs hivatkozásban nem használhatók egyszerre az elosztott nézetek és az adatreplikálási ütemezés beállításai.  

### <a name="BKMK_SummarizeDBReplication"></a> Az adatbázis-replikációs forgalom összegzése  
Minden hely rendszeres időközönként összegzi annak a hely adatbázis-replikációs hivatkozások áthaladó hálózati forgalommal kapcsolatos adatokat. Az összegzett adatok az adatbázis-replikációs jelentésekben használt. A replikációs hivatkozáshoz tartozó mindkét hely összegzi a replikációs hivatkozáson áthaladó hálózati forgalmat. Az adatok összegzését a helyadatbázist futtató SQL Server rendszer hajtja végre. Miután az adatok összegzési, az adatokat más helyekre replikált globális adatként.  

Alapértelmezés szerint az összegzés 15 percenként történik. Adatbázis-replikációs hivatkozás tulajdonságai a hálózati forgalom összegzésének gyakoriságát módosításához szerkessze a **összegzési időköz**. Az összegzés gyakorisága hatással van az adatbázis-replikációra vonatkozó jelentésekben megjelenített információkat. Kiválaszthatja az időköz 5 perc és 60 perc között. Ha növeli az összegzés gyakorisága, megnöveli a replikációs hivatkozáshoz minden helyen az SQL server feldolgozási terhelését.  

### <a name="BKMK_DBRepThresholds"></a>Adatbázis-replikáció küszöbértékei  
Az adatbázis-replikáció küszöbértékei határozzák meg, hogy mikor jelentendő csökkentett teljesítményűnek vagy sikertelennek az adatbázis-replikációs hivatkozások állapota. Alapértelmezés szerint egy hivatkozást csökkentett teljesítményű állapotra van beállítva, amikor valamelyik replikációs csoport nem tudja végrehajtani a replikációt 12 egymást követő kísérlet alatt. A hivatkozás csökkentett sikertelen állapotát, amikor valamelyik replikációs csoport tudja végrehajtani a replikációt 24 egymást követő kísérlet alatt.  

Amikor a Configuration Manager jelzi a csökkentett teljesítményű vagy sikertelen replikációs hivatkozásokat finomhangolása egyéni értékeket adhat meg. Beállítása, amikor a Configuration Manager jelzi, hogy az adatbázis-replikációs hivatkozások esetében az egyes állapotokhoz segíthetnek pontosabban az adatbázis-replikációs hivatkozások között adatbázis-replikáció állapotának figyelésére.  

Mivel egy vagy néhány replikációs csoport a replikáció, míg a többi replikációs csoport sikeresen replikálásához továbbra is sikertelen, tervezze meg replikációs hivatkozás replikációs állapotának ellenőrzését, amikor első alkalommal jelzi a csökkentett állapotúként. Ha meghatározott replikációs csoportok esetében ismétlődő késések fordulnak elő, de ez a késés nem jelent problémát, vagy ha a helyek közötti hálózati kapcsolat kis sávszélességű, próbálja meg módosítani a hivatkozás csökkentett teljesítményű vagy sikertelen állapotához tartozó újrapróbálkozási értéket. Csökkentett teljesítményű vagy sikertelen volt a kapcsolat beállítása előtt növeli az újbóli próbálkozások számát, ha kiküszöbölheti az ismert problémákkal kapcsolatos téves figyelmeztetéseket, és pontosabban nyomon követheti a hivatkozás állapotát.  

Is érdemes lehet tudni, hogy milyen gyakran az adott csoportok replikációjára minden replikációs csoport replikációs szinkronizálási időközét. Megtekintéséhez a **szinkronizálás időköze** a replikációs csoportot, a a **figyelés** munkaterületen, a a **adatbázis-replikáció** csomópontban jelölje ki a **replikálás részletei** a replikációs hivatkozás lapon.  

További információ az adatbázis-replikáció figyeléséről, valamint a replikációs állapot figyelése: [adatbázis replikációs hivatkozások és a replikációs állapot figyelése](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md#BKMK_MonitorRepLinksAndStatuss) a a [figyelő hierarchia és replikációs infrastruktúra a System Center Configuration Managerben](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md) témakör.  

További információ az adatbázis-replikálás küszöbértékeiről: [Helyadatbázisok replikációjának vezérlői](#BKMK_DBRepControls).  

## <a name="BKMK_DBRepControls"></a> Helyadatbázis-replikációs beállítások  
Módosíthatja a beállításokat az egyes adatbázisok adatbázis-replikációhoz használt hálózati sávszélesség szabályozásához. A beállítások csak a hely adatbázisába, amelyben a beállítások érvényesek. A beállítások mindig használata, amikor a hely bármilyen adatokat replikál egy másik helyre történő adatbázis-replikáció útján.  

Amely módosíthatja az egyes adatbázisok replikációs beállítások a következők:  

-  Módosítsa a SSB-portot.  
-  Állítsa a idő eltelte után a replikációs hibák elindítani a helyet, hogy újrainicializálja a Helyadatbázis példányát.  
-  Állítson be egy helyadatbázist az adatbázis-replikáció során replikált adatok tömörítésére. A rendszer csak a helyek közötti adatátvitelhez tömöríti az adatokat, a helyadatbázisban való tároláshoz egyik helyen sem.  

A Helyadatbázis, a Configuration Manager konzolon a replikációs vezérlők beállításainak módosítása a **adatbázis-replikáció** csomópont, a Helyadatbázis tulajdonságainak szerkesztésével. Ez a csomópont a **Felügyelet** munkaterület **Hierarchiakonfiguráció** csomópontjában található, és a **Figyelés**munkaterületen is megjelenik. A Helyadatbázis tulajdonságainak szerkesztéséhez jelölje ki a helyek közötti replikációs hivatkozást, és nyissa meg bármelyik **szülő adatbázis tulajdonságai** vagy **gyermek adatbázis tulajdonságai**.  

> [!TIP]  
> Az adatbázis-replikáció beállításait bármelyik munkaterület **Adatbázis replikálása** csomópontjában konfigurálhatja. Azonban ha használja a **adatbázis-replikáció** csomópontja a **figyelés** munkaterületen, akkor is megtekintheti a replikációs hivatkozás adatbázis-replikáció állapotát, és a Replication Link Analyzer eszköz segítségével megvizsgálhatja a replikációval kapcsolatos problémákat.  

