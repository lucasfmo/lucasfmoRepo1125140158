---
title: "Eszközintelligencia |} Microsoft Docs"
description: "Feladatokhoz közös Eszközintelligencia a System Center Configuration Managerben."
ms.custom: na
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e8159bd9-5c2b-4d25-82f9-78fcfd732ba9
caps.latest.revision: 6
caps.handback.revision: 0
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9c5d1e48b76392beaf54b5377c69b648537e86f8
ms.openlocfilehash: 17168e26f13340847928f6e3623115cd4b55997b
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-use-asset-intelligence-in-system-center-configuration-manager"></a>Az Eszközintelligencia szolgáltatás használata a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ebben a témakörben található információk nyújtanak segítséget a leggyakoribb Eszközintelligencia feladatok a System Center Configuration Manager-hierarchiában felügyelheti:  

##  <a name="BKMK_ViewInformation"></a> Az Eszközintelligencia adatainak megtekintése  
 Az Eszközintelligencia adatait az **Eszközintelligencia** kezdőlapján, illetve az eszközintelligencia-jelentésekben tekintheti meg.  

###  <a name="BKMK_AssetIntelligenceHomePage"></a> Az Eszközintelligencia kezdőlapja  
 Az **Eszközintelligencia** kezdőlapján található összegző irányítópulton az Eszközintelligencia-katalógus adatait találja. A kezdőlapon megtekintheti a katalógusszinkronizálásra, illetve a leltározott szoftverek állapotára vonatkozó adatokat. Az **Eszközintelligencia** kezdőlapja a következő szakaszokra oszlik:  

-   **Katalógus szinkronizálása**: Ismerteti, hogy az Eszközintelligencia engedélyezve van, az Eszközintelligencia-katalógus szinkronizálási pontja, a szinkronizálás ütemezését, e az ügyféllicenc-kimutatások importálása, állapot utolsó frissítésekor és az időt a következő ütemezett frissítés és az Eszközintelligencia szinkronizálási pontjához tartozó helyrendszer telepítése után történt módosítások számát az aktuális állapotát.  

    > [!NOTE]  
    >  Az **Eszközintelligencia** kezdőlapján csak akkor jelenik meg a katalógusszinkronizációs szakasz, ha telepítve lett egy, az Eszközintelligencia szinkronizálási pontjához tartozó helyrendszerszerepkör.  

-   **Leltározott Szoftverállapot**: A számát és százalékos arányát a leltározott szoftverek, szoftverkategóriák és szoftvercsaládok egy rendszergazda felhasználónak, a online azonosítása függőben van vagy azonosítatlan és nem függésben levő azonosított, a Microsoft által azonosított biztosít. A táblázat ezek számát, a diagram pedig a százalékos arányt tartalmazza.  

 Az alábbi útmutatást követve megtekintheti az Eszközintelligencia adatait az **Eszközintelligencia** kezdőlapján.  

##### <a name="to-view-asset-intelligence-information-on-the-asset-intelligence-home-page"></a>Az eszközintelligencia adatainak megtekintése az Eszközintelligencia kezdőlapján  

1.  Kattintson a Configuration Manager-konzolon az **Eszközök és megfelelőség**elemre.  

2.  Az **Eszközök és megfelelőség** munkaterületen kattintson az **Eszközintelligencia**lehetőségre. Ekkor megjelennek az Eszközintelligencia-jelentések.  

###  <a name="BKMK_AssetIntelligenceReports"></a> Eszközintelligencia-jelentések  
 Az Eszközintelligencia által összegyűjtött információkról több mint 60 Eszközintelligencia-jelentés készül. A jelentések nagy része konkrétabb jelentésekhez kapcsolódik, amelyekben általános adatokat kérdezhet le, és részletesebb információhoz juthat. Az Eszközintelligencia-jelentésekben találhatók a Configuration Manager konzolon a **figyelés** munkaterület alatt a **jelentéskészítési** csomópont. A jelentések a hardverekkel, licenckezeléssel és szoftverekkel kapcsolatos adatokat tartalmazzák. A Configuration Manager-jelentésekkel kapcsolatos további információkért lásd: [a System Center Configuration Manager jelentéskészítési](../../../../core/servers/manage/reporting.md).  

> [!NOTE]  
>  Az Eszközintelligencia-jelentésekben feltüntetett, a telepített szoftvercímek mennyiségére és a licencekre vonatkozó adatok pontossága eltérhet a környezetben használt telepített szoftverek és a licencek tényleges mennyiségétől. Ennek oka, hogy a vállalati környezetben telepített szoftverekre vonatkozó szoftverlicencadatok leltározásakor összetett függőségekkel és korlátozásokkal kell számolni. Az Eszközintelligencia-jelentések önmagukban nem alkalmasak a megvásárolt szoftverlicencek megfelelőségének ellenőrzésére.  

 Az alábbi útmutatást követve az Eszközintelligencia-jelentések segítségével megtekintheti az Eszközintelligencia adatait.  

##### <a name="to-view-collected-asset-intelligence-information-by-using-asset-intelligence-reports"></a>Az Eszközintelligencia összegyűjtött adatainak megtekintése az Eszközintelligencia-jelentések segítségével  

1.  Kattintson a Configuration Manager konzolon **figyelés**.  

2.  A **Figyelés** munkaterületen bontsa ki a **Jelentéskészítés**csomópontot és a **Jelentések**elemet, majd kattintson az **Eszközintelligencia**lehetőségre. Ekkor megjelennek az Eszközintelligencia-jelentések.  

    > [!WARNING]  
    >  Ha a **Jelentések** csomóponton nem találhatók jelentésmappák, ellenőrizze, hogy konfigurálta-e a jelentéskészítést. További információkért lásd: [konfigurálása a System Center Configuration Manager jelentéskészítési](../../../../core/servers/manage/configuring-reporting.md).  

3.  Válassza ki a futtatni kívánt Eszközintelligencia-jelentést, majd a **Kezdőlap** lap **Jelentéscsoport** csoportjában kattintson a **Futtatás**elemre.  

##  <a name="BKMK_SynchronizeTheCatalog"></a> Eszközintelligencia-katalógus szinkronizálása  
 A szoftvercímek legutóbbi kategorizálásának lekéréséhez szinkronizálja a helyi Eszközintelligencia-katalógust a System Center Online szolgáltatással. Ha a System Center Online szolgáltatással manuálisan kéri a katalógus szinkronizálását, a szinkronizációs folyamat akár 15 percet (vagy még többet) is igénybe vehet. Configuration Manager-frissítések a **utolsó sikeres frissítés** beállítása a **Eszközintelligencia** kezdőlapján a szinkronizáció befejezésének aktuális idejét.  

> [!NOTE]  
>  Az eljárások megkezdése előtt telepíteni kell az Eszközintelligencia szinkronizációs pontja helyrendszerszerepkört. Az Eszközintelligencia szinkronizációs pontja telepítéséről további információkért lásd: [Eszközintelligencia konfigurálása a System Center Configuration Managerben](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md).  

 Az alábbi útmutatást követve hozza létre az Eszközintelligencia-katalógus szinkronizálási ütemezését.  

#### <a name="to-create-a-synchronization-schedule-for-the-asset-intelligence-catalog"></a>Eszközintelligencia-katalógus szinkronizálási ütemezésének létrehozása  

1.  Kattintson a Configuration Manager-konzolon az **Eszközök és megfelelőség**elemre.  

2.  Az **Eszközök és megfelelőség** munkaterületen kattintson az **Eszközintelligencia**lehetőségre.  

3.  A **Kezdőlap** lap **Létrehozás** csoportjában kattintson a **Szinkronizálás**elemre, majd a **Szinkronizálás ütemezése**lehetőségre.  

4.  Az **Eszközintelligencia-szinkronizációs pont ütemezése** párbeszédpanelen válassza az **Ütemezett szinkronizálás engedélyezése**lehetőséget, majd állítson be egy egyszerű vagy egyéni ütemezést.  

5.  A változtatások mentéséhez kattintson az **OK** gombra.  

    > [!NOTE]  
    >  A szinkronizálás ütemezéséről, illetve a következő ütemezett szinkronizálásról az **Eszközök és megfelelőség** munkaterület hierarchiájának felső szintű helyén, az **Eszközintelligencia** csomópontban talál további információt.  

 Az alábbi útmutatást követve manuálisan szinkronizálhatja az Eszközintelligencia-katalógust.  

> [!WARNING]  
>  A System Center Online 12 óránként legfeljebb egy manuális szinkronizációs kérelmet fogad el.  

###  <a name="BKMK_ManuallySynchronizeCatalog"></a> Az Eszközintelligencia-katalógus manuális szinkronizálása  

1.  Kattintson a Configuration Manager-konzolon az **Eszközök és megfelelőség**elemre.  

2.  Az **Eszközök és megfelelőség** munkaterületen kattintson az **Eszközintelligencia**lehetőségre.  

3.  A **Kezdőlap** lap **Létrehozás** csoportjában kattintson a **Szinkronizálás**elemre, majd az **Eszközintelligencia-katalógus szinkronizálása**lehetőségre, végül kattintson az **OK**gombra.  

##  <a name="BKMK_CustomizeCatalog"></a> Az eszközintelligencia-katalógus testreszabása  
 A Eszközintelligencia-katalógus System Center Online-tól származó kategorizálási információinak tárolása a helyadatbázisban történik. Az adatok csak olvasási engedéllyel érhetők el, és sem módosítani, sem pedig törölni nem lehet őket. Az egyéni szoftverkategóriákat, szoftvercsaládokat, szoftvercímkéket és a hardverkövetelmény-katalógus adatait azonban szabadon létrehozhatja, módosíthatja és törölheti. Így a már létező vagy felhasználó által definiált szoftvercímadatok esetében egyéni kategorizálási adatokat használhat a System Center Online által biztosított információk helyett. Ha kategorizálási információkat módosít vagy vesz fel, a katalógus adatai felhasználó által definiált adatként szerepelnek majd. A felhasználó által definiált kategorizálási adatokat a rendszer más adatbázistáblákban tárolja, mint az ellenőrzött katalógusadatokat.  

###  <a name="BKMK_SoftwareCategories"></a> Szoftverkategóriák  
 Az Eszközintelligencia szoftverkategóriáinak használatával széles körben kategorizálhatók a leltározott szoftvercímek, emellett adott szoftvercsaládok magas szintű csoportosítására is használhatók. Szoftverkategóriát alkothatnak például az energiavállalatok, a kategórián belül pedig külön szoftvercsaládokat az olaj, a gáz vagy a vízenergia. Az Eszközintelligencia-katalógus több előre meghatározott szoftverkategóriával rendelkezik, emellett pedig lehetőség van felhasználó által definiált kategóriák létrehozására a leltározott szoftverek további meghatározása céljából. Az előre meghatározott szoftverkategóriák érvényesítési állapota mindig **Ellenőrizve**értékű, míg az Eszközintelligencia-katalógushoz hozzáadott egyéni szoftverkategória-adatok értéke **Felhasználó által definiált**.  

 Az alábbi útmutatást követve felhasználó által definiált szoftverkategóriát hozhat létre.  

##### <a name="to-create-a-user-defined-software-category"></a>Felhasználó által definiált szoftverkategória létrehozása  

1.  Kattintson a Configuration Manager-konzolon az **Eszközök és megfelelőség**elemre.  

2.  Az **Eszközök és megfelelőség** munkaterületen kattintson az **Eszközintelligencia**elemre, majd a **Katalógus**lehetőségre.  

3.  A **Kezdőlap** lap **Létrehozás** csoportjában kattintson a **Szoftverkategória létrehozása**elemre.  

4.  Az **Általános** lapon nevezze el az új szoftverkategóriát, majd igény szerint adja meg a leírását.  

    > [!NOTE]  
    >  Az újonnan létrehozott szoftverkategóriák érvényesítési állapota mindig **Felhasználó által definiált**értékű.  

     Kattintson a **Tovább**gombra.  

5.  Az **Összefoglalás** lapon tekintse át a beállításokat, majd kattintson a **Tovább**gombra.  

6.  A varázslóból való kilépéshez a **Befejezés** lapon kattintson a **Bezárás** gombra.  

###  <a name="BKMK_SoftwareFamilies"></a> Szoftvercsaládok  
 Az Eszközintelligencia szoftvercsaládjai használatával alaposabban meghatározhatók a szoftverkategóriákban található leltározott szoftvercímek. Szoftverkategóriát alkothatnak például az energiavállalatok, a kategórián belül pedig külön szoftvercsaládokat az olaj, a gáz vagy a vízenergia. Az Eszközintelligencia-katalógus több előre meghatározott szoftvercsaláddal rendelkezik, emellett pedig lehetőség van a felhasználó által definiált családok létrehozására a leltározott szoftverek meghatározása céljából. Az előre meghatározott szoftvercsaládok érvényesítési állapota mindig **Ellenőrizve**értékű, míg az Eszközintelligencia-katalógushoz hozzáadott egyéni szoftvercsaládadatok értéke **Felhasználó által definiált**.  

 Az alábbi útmutatást követve létrehozhat felhasználó által definiált szoftvercsaládot.  

##### <a name="to-create-a-user-defined-software-family"></a>Felhasználó által definiált szoftvercsalád létrehozása  

1.  Kattintson a Configuration Manager-konzolon az **Eszközök és megfelelőség**elemre.  

2.  Az **Eszközök és megfelelőség** munkaterületen kattintson az **Eszközintelligencia**elemre, majd a **Katalógus**lehetőségre.  

3.  A **Kezdőlap** lap **Létrehozás** csoportjában kattintson a **Szoftvercsalád létrehozása**elemre.  

4.  Az **Általános** lapon nevezze el az új szoftvercsaládot, majd igény szerint adja meg a leírását.  

    > [!NOTE]  
    >  Az újonnan létrehozott szoftvercsaládok érvényesítési állapota mindig **Felhasználó által definiált**értékű.  

5.  Az **Összefoglalás** lapon tekintse át a beállításokat, majd kattintson a **Tovább**gombra.  

6.  A varázslóból való kilépéshez a **Befejezés** lapon kattintson a **Bezárás** gombra.  

###  <a name="BKMK_SoftwareLabels"></a> Szoftvercímkék  
 Az Eszközintelligencia egyéni szoftvercímkéi segítségével a szoftvercímek csoportosítására használható szűrőket hozhat létre, amelyeket Eszközintelligencia-jelentésekkel tekinthet meg. Ha például létrehoz egy „shareware” nevű szoftvercímkét, amelyet több alkalmazáshoz is hozzárendel, akkor a megfelelő jelentés lefuttatása után minden „shareware” szoftvercímkével ellátott cím megjelenik a találati listában. Az Eszközintelligencia-katalógushoz hozzáadott egyéni szoftvercímkék érvényesítési állapota **Felhasználó által definiált** értékű.  

 Az alábbi útmutatást követve létrehozhat felhasználó által definiált egyéni címkét.  

##### <a name="to-create-a-user-defined-software-label"></a>Felhasználó által definiált egyéni címke létrehozása  

1.  Kattintson a Configuration Manager-konzolon az **Eszközök és megfelelőség**elemre.  

2.  Az **Eszközök és megfelelőség** munkaterületen kattintson az **Eszközintelligencia**elemre, majd a **Katalógus**lehetőségre.  

3.  A **Kezdőlap** lap **Létrehozás** csoportjában kattintson a **Szoftvercímke létrehozása**elemre.  

4.  Az **Általános** lapon nevezze el az új szoftvercsaládot, majd igény szerint adja meg a leírását.  

    > [!NOTE]  
    >  Az újonnan létrehozott egyéni szoftvercímkék érvényesítési állapota mindig **Felhasználó által definiált**értékű.  

5.  Az **Összefoglalás** lapon tekintse át a beállításokat, majd kattintson a **Tovább**gombra.  

6.  A varázslóból való kilépéshez a **Befejezés** lapon kattintson a **Bezárás** gombra.  

###  <a name="BKMK_HardwareRequirements"></a> Hardverkövetelmények  
 A hardverkövetelmények adatai segítségével még a szoftverek központi telepítése előtt ellenőrizheti, hogy számítógépe megfelel-e az adott szoftver hardverkövetelményeinek. Számos előre meghatározott szoftverkövetelmény található az Eszközintelligencia-katalógusban, továbbá új, felhasználó által definiált hardverkövetelmény-információt is létrehozhat az egyéni követelmények teljesítése érdekében. Az előre meghatározott hardverkövetelmények érvényesítési állapota mindig **Ellenőrizve**értékű, míg az Eszközintelligencia-katalógushoz hozzáadott, felhasználó által definiált hardverkövetelmény-adatok értéke **Felhasználó által definiált**.  

> [!IMPORTANT]  
>  A Configuration Manager-konzolon megjelenő hardverkövetelményeket a helyi számítógépen az Eszközintelligencia-katalógusból olvassa be, és nem a System Center 2012 Configuration Manager ügyfelek leltározott szoftvercímre vonatkozó alapulnak. A hardverkövetelményekre vonatkozó adatok nem frissülnek a System Center Online szinkronizálási folyamatának részeként. Felhasználó által definiált hardverkövetelményeket hozhat létre olyan leltározott szoftverekhez, amelyek nem rendelkeznek társított hardverkövetelményekkel.  

 Az alábbi útmutatást követve felhasználó által definiált hardverkövetelményt hozhat létre.  

##### <a name="to-create-a-user-defined-hardware-requirements"></a>Felhasználó által definiált hardverkövetelmény létrehozása  

1.  Kattintson a Configuration Manager-konzolon az **Eszközök és megfelelőség**elemre.  

2.  Az **Eszközök és megfelelőség** munkaterületen kattintson az **Eszközintelligencia**elemre, majd a **Hardverkövetelmények**lehetőségre.  

3.  A **Kezdőlap** lap **Létrehozás** csoportjában kattintson a **Hardverkövetelmények létrehozása**elemre.  

4.  Az **Általános** lapon adja meg az alábbi adatokat:  

    1.  **Szoftvercím**: Megadja a hardverkövetelményhez, amelyre a hardverkövetelmények vonatkoznak. Nem adhat meg olyan szoftvercímet, amely már szerepel az Eszközintelligencia-katalógusban.  

    2.  **Érvényesítési állapot**: Ismerteti az érvényesítési állapota **felhasználó által definiált** a hardverkövetelmények. Ez a beállítás nem módosítható.  

    3.  **Minimális CPU (MHz)**: Adja meg a minimális processzorsebesség, megahertzben (MHz), a szoftver futtatásához szükséges.  

    4.  **Minimális RAM (KB)**: Adja meg a minimális memória kilobájt (KB), a szoftver futtatásához szükséges.  

    5.  **Minimális lemezterület (KB)**: Adja meg a minimális szabad lemezterület, a szoftver futtatásához szükséges.  

    6.  **Minimális lemezméret (KB)**: Meghatározza a minimum merevlemez méretét, a szoftver futtatásához szükséges.  

     Kattintson a **Tovább** gombra.  

5.  Az **Összefoglalás** lapon tekintse át a beállításokat, majd kattintson a **Tovább**gombra.  

6.  A varázslóból való kilépéshez a **Befejezés** lapon kattintson a **Bezárás** gombra.  

###  <a name="BKMK_ModifyCategorization"></a> A leltározott szoftver kategorizálási adatainak módosítása  
 Az Eszközintelligencia-katalógus előre meghatározott szoftverei olyan speciális kategorizálási adatokkal lettek konfigurálva, mint a terméknév, a gyártó, a szoftverkategória vagy a szoftvercsalád. Ha az előre meghatározott kategorizálási adatok nem felelnek meg az Ön elvárásainak, a szoftver tulajdonságai között módosíthatja az információkat. Az előre meghatározott kategorizálási adatok módosításakor a szoftver érvényesítési állapota **Ellenőrizve** értékről **Felhasználó által definiált**értékűre vált.  

> [!IMPORTANT]  
>  A kategorizálási adatok csak a felső szintű helyen módosíthatók.  

 Az alábbi útmutatást követve módosíthatja a leltározott szoftverek kategorizálási adatait.  

##### <a name="to-modify-the-categorizations-for-software-titles"></a>A szoftvercímek kategorizálásának módosítása  

1.  Kattintson a Configuration Manager-konzolon az **Eszközök és megfelelőség**elemre.  

2.  Az **Eszközök és megfelelőség** munkaterületen kattintson az **Eszközintelligencia**elemre, majd a **Leltározott szoftver**lehetőségre.  

3.  Jelöljön ki egy vagy több szoftvercímet, amelynek módosítani szeretné a kategorizálását.  

4.  A **Kezdőlap** **Tulajdonságok** csoportjában kattintson a **Tulajdonságok**elemre.  

5.  Az **Általános** lapon az alábbi kategorizálási adatokat módosíthatja:  

    -   **Terméknév**: Adja meg a leltározott szoftvercím neve.  

    -   **Szállítói**: Adja meg a leltározott szoftvercímet kifejlesztő gyártó neve.  

    -   **Kategória**: Adja meg a leltározott szoftvercímhez aktuálisan hozzárendelt szoftverkategória.  

    -   **Termékcsalád**: Adja meg a leltározott szoftvercímhez aktuálisan hozzárendelt szoftvercsalád.  

6.  A változtatások mentéséhez kattintson az **OK** gombra.  

 Az alábbi útmutatást követve visszaállíthatja a szoftver eredeti kategorizálási adatait.  

### <a name="revert-categorization-information-to-original-settings-for-software"></a>A szoftver kategorizálási adatainak visszaállítása az eredeti állapotba  
 A Configuration Manager kategorizálási információ a System Center Online az adatbázisban tárolja. Ezek az adatok nem törölhetők. A kategorizálási adatok módosítása után visszaállíthatja őket a System Center Online által szolgáltatott eredeti állapotba. Azon leltározott szoftverek eredeti beállításai is visszaállíthatók, amelyek nem szerepelnek az Eszközintelligencia-katalógusban.  

 Az alábbi útmutatást követve visszaállíthatja a kategorizálási adatok eredeti beállításait.  

##### <a name="to-revert-categorization-information-to-original-settings"></a>A kategorizálási adatok eredeti beállításainak visszaállítása  

1.  Kattintson a Configuration Manager-konzolon az **Eszközök és megfelelőség**elemre.  

2.  Az **Eszközök és megfelelőség** munkaterületen kattintson az **Eszközintelligencia**elemre, majd a **Leltározott szoftver**lehetőségre.  

3.  Jelöljön ki egy vagy több szoftvercímet, amelyet vissza szeretne állítani az eredeti beállítások szerint. Csak a **Felhasználó által definiált** állapotú szoftverek beállításai állíthatók vissza.  

    > [!TIP]  
    >  Az **Állapot** oszlopra kattintva érvényesítési állapotuk szerint rendezheti a szoftvereket. Az érvényesítési állapot szerinti rendezésnek köszönhetően egyszerűen kiválaszthatja azokat a szoftvereket, amelyek beállításait vissza szeretné állítani.  

4.  A **Kezdőlap** lap **Termék** csoportjában kattintson a **Visszaállítás**elemre.  

5.  A szoftver eredeti kategorizálási adatainak visszaállításához kattintson az **Igen** gombra.  

6.  Miután az Eszközintelligencia-katalógusban visszaállította a szoftver eredeti kategorizálási adatait, az érvényesítési állapot **Felhasználó által definiált** értékűről **Ellenőrizve**értékűre vált. Ha egy olyan szoftver beállításait állítja vissza, amely nem szerepel a katalógusban, az érvényesítési állapot **Felhasználó által definiált** értékűről **Kategorizálatlan**értékűre vált.  

##  <a name="BKMK_RequestCatalogUpdate"></a> Katalógusfrissítés igénylése kategorizálatlan szoftvercímek számára  
 A kategorizálatlan szoftvercímadatokat elküldheti a System Center Online-hoz, hogy a szolgáltatás kivizsgálhassa és kategorizálhassa azokat. Ha elküld egy adott kategorizálatlan szoftvercímet, és arra legalább négy kategorizálási kérelem érkezett, a Microsoft kutatói azonosítják és kategorizálják a szoftvercímet, majd az információt elérhetővé teszik a System Center Online szolgáltatást használó ügyfelek számára. A Microsoftnál azok a szoftvercímek élveznek elsőbbséget, amelyekre a legtöbb kategorizálási kérelem érkezett. Az üzletági és az egyéni szoftveralkalmazások általában nem kategorizálhatók, ezért ezeket a szoftvercímeket nem érdemes elküldeni a Microsoftnak.  

 Ha szoftvercímadatot küld kategorizálásra a System Center Online-hoz, a következő feltételek lépnek érvénybe:  

-   A Microsoft csak az alapvető szoftvercímadatokat továbbítja a System Center Online-nak, a kategorizálandó adatok pedig elküldés előtt ellenőrizhetők.  

-   A szoftverlicencadatokat a rendszer soha nem továbbítja.  

-   A feltöltött szoftvercímek a System Center Online katalógus részeként nyilvánosan elérhetővé és letölthetővé válnak.  

-   A szoftvercímek forrását nem a System Center Online katalógusa tárolja. A bizalmas vagy jogvédett adatokat tartalmazó alkalmazáscímeket azonban nem szabad kategorizálás céljából elküldeni a System Center Online-nak.  

> [!NOTE]  
>  Az Eszközintelligencia szolgáltatás adatvédelmi tudnivalók kapcsolatos további információkért lásd: [biztonsága és adatvédelme a System Center Configuration Manager Eszközintelligencia](../../../../core/clients/manage/asset-intelligence/security-and-privacy-for-asset-intelligence.md).  

 Az alábbi útmutatást követve kérheti a System Center Online-tól az Eszközintelligencia-katalógus szoftvercímeinek kategorizálását.  

#### <a name="to-request-a-catalog-update-for-uncategorized-software-titles"></a>Katalógusfrissítés igénylése kategorizálatlan szoftvercímek számára  

1.  Kattintson a Configuration Manager-konzolon az **Eszközök és megfelelőség**elemre.  

2.  Az **Eszközök és megfelelőség** munkaterületen kattintson az **Eszközintelligencia**elemre, majd a **Leltározott szoftver**lehetőségre.  

3.  Jelöljön ki egy vagy több terméknevet, amelyet el szeretne küldeni kategorizálásra a System Center Online-hoz. A szolgáltatás részére csak a kategorizálatlan szoftvercímeket küldheti el. Ha egy leltározott szoftvercímet egy rendszergazda már kategorizált, ezért az állapota „Felhasználó által definiált” értékű, kattintson a jobb gombbal a szoftvercímre, majd a **Visszaállítás** elemre. Így a szoftvercím állapota **Kategorizálatlan** értékűre vált, így el lehet küldeni kategorizálásra a System Center Online-hoz.  

    > [!NOTE]  
    >  A Configuration Manager kategorizálandó egyszerre legfeljebb 100 szoftvercímet tud feldolgozni. Ha több mint 100 szoftvercímet választott ki, csak az első 100 kerül feldolgozásra. A fennmaradó szoftvercímeket 100-nál kevesebb elemet tartalmazó csoportokban tudja kijelölni kategorizálásra.  

    > [!TIP]  
    >  Az **Állapot** oszlopra kattintva érvényesítési állapotuk szerint rendezheti a szoftvereket. Így megtekintheti a kategorizálatlan termékneveket, és gyorsan kiválaszthatja azokat, amelyeket kategorizáltatni szeretne.  

4.  A **Kezdőlap** lap **Termék** csoportjában kattintson az **Igénykatalógus frissítése**elemre.  

5.  Tekintse át a System Center Online kategorizálási kérelmekről szóló adatvédelmi üzenetét. A **Részletek** elemre kattintva tekintheti meg a System Center Online-hoz elküldendő adatokat.  

6.  Jelölje be az **Elolvastam és megértettem ezt az üzenetet**jelölőnégyzetet, majd az **OK** gombra kattintva küldje el a kategorizálásra kiválasztott szoftvercímeket.  

7.  Ellenőrizze, hogy a System Center Online-hoz kategorizálásra elküldött leltározott szoftverterméknevek állapota **Kategorizálatlan** értékűről **Függőben**értékűre változott-e.  

    > [!NOTE]  
    >  A System Center Online-hoz kategorizálási célból elküldött szoftverek érvényesítési állapota a központi adminisztrációs helyen **Függőben** értékűként, az elsődleges gyermekhelyeken azonban még **Kategorizálatlan** értékűként van feltüntetve.  

##  <a name="BKMK_ResolveSoftwareDetails"></a> Szoftveradatok ütközésének feloldása  
 Ha a System Center Online-tól kapott, újonnan frissített szoftverkategorizálási részletek ütköznek a már létező szoftveradatokkal, megadhatja, hogy hogyan szeretné feloldani az ütközést. Ütközés esetén az érintett szoftver állapota **Frissíthető**értékűre módosul. A szoftveradatok ütközésének feloldását követően a szoftverkategorizálási adatokat (a megadott beállításoknak megfelelően) az Eszközintelligencia-katalógus tárolja. A szoftveradatok ütközése soha nem érinti kétszer ugyanazt a szoftverkategorizálási értéket, hacsak a System Center Online-beli érték nem módosul az ütközés feloldását követően.  

 A szoftveradatok ütközésének feloldásához kövesse az alábbi eljárást.  

#### <a name="to-resolve-a-software-details-conflict"></a>Szoftveradatok ütközésének feloldása  

1.  Kattintson a Configuration Manager-konzolon az **Eszközök és megfelelőség**elemre.  

2.  Az **Eszközök és megfelelőség** munkaterületen kattintson az **Eszközintelligencia**elemre, majd a **Leltározott szoftver**lehetőségre.  

3.  Tekintse át a **Frissíthető** állapotú szoftvercímekre vonatkozó **Állapot** oszlopot.  

4.  Jelölje ki az ütközés által érintett szoftvercímet, majd a **Kezdőlap** lap **Termék** csoportjában kattintson az **Ütközés feloldása**elemre.  

5.  Tekintse át az alábbi információkat:  

    -   **Az értékek helyi**: Megadja a már meglévő szoftverkategorizálási adatokat az Eszközintelligencia-katalógus ütköző újabb System Center Online szoftverkategorizálási adatokat.  

    -   **Letöltött érték**: Adja meg az új System Center Online szereplő szoftverkategorizálási adatokkal ütköző az Eszközintelligencia katalógusban szoftverkategorizálási adatokat.  

6.  A szoftveradatok ütközésének feloldásához válassza az alábbi beállítások egyikét:  

    -   **Ne módosítsa a helyileg szerkesztett katalógus információinak értékét**: Oldja fel a szoftveradatok ütközése soha megtartják a meglévő Eszközintelligencia-katalógus szoftver kategorizálási adatait. Ha ezt a beállítást választja, a szoftvercím állapota **Frissíthető** értékűről **Felhasználó által definiált**értékűre módosul.  

    -   **A helyileg szerkesztett katalógusadatok értékeinek felülírása a System Center Online letöltött érték**: Oldja fel a szoftveradatok ütközése soha által felülírja a meglévő Eszközintelligencia-katalógus szoftver kategorizálási adatait a System Center Online-tól kapott új információkkal. Ha ezt a beállítást választja, a szoftvercím állapota **Frissíthető** értékűről **Ellenőrizve**értékűre módosul.  

     Az ütközés feloldásának mentéséhez kattintson az **OK** gombra.  

