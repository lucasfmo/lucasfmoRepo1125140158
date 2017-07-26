---
title: "Eszköz Eszközintelligencia bemutatása |} Microsoft Docs"
description: "Bevezetés az Eszközintelligencia a System Center Configuration Managerben."
ms.custom: na
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 0bdfdef5-390f-4099-8bde-de51d9a89175
caps.latest.revision: 7
caps.handback.revision: 0
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9c5d1e48b76392beaf54b5377c69b648537e86f8
ms.openlocfilehash: 879dc3f04f361af955afbc4db180d097073e8d41
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="introduction-to-asset-intelligence-in-system-center-configuration-manager"></a>A System Center Configuration Manager Eszközintelligencia szolgáltatásának bemutatása

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager Eszközintelligencia lehetővé teszi a készlet és a vállalaton belüli szoftverlicencek használatának kezelését az Eszközintelligencia-katalógus használatával. A Windows Management Instrumentation (WMI) számos hardverleltárosztálya bővíti a használt hardverekről és szoftvercímekről összegyűjtött információk körét. Ezek az információk több, mint 60 jelentésben szerepelnek könnyen használható formátumban. Számos jelentés konkrétabb jelentésekhez kapcsolódik, amelyek lehetővé teszik az általános adatok lekérdezését, illetve részletesebb információk megjelenítését is. Az Eszközintelligencia-katalógushoz egyéni információkat is hozzáadhat, például egyéni szoftverfrissítési kategóriákat, szoftvercsaládokat, szoftvercímkéket és hardverkövetelményeket. Emellett kapcsolódhat a System Center Online szolgáltatáshoz is   az Eszközintelligencia-katalógusnak a rendelkezésre álló legfrissebb információkkal való dinamikus frissítéséhez. A Microsoft ügyfelei egyeztethetik a vállalati szoftverlicencek használatát a megvásárolt szoftverlicencekkel a szoftverlicenc-információk importálása a Configuration Manager Helyadatbázis használják.  

##  <a name="BKMK_AssetIntelligenceCatalog"></a> Eszközintelligencia-katalógus  

 A Configuration Manager Eszközintelligencia-katalógus egy adatbázistáblákban a helyadatbázisban tárolt, amelyek több mint 300 000 szoftvercímre és -verzióra vonatkozó kategorizálási és azonosítási információkat tartalmaznak. Ezek adatbázistáblák adott szoftvercím hardverkövetelményeinek kezelésére is használhatók.  

 Az Eszközintelligencia-katalógus szoftverlicenc-információkat biztosít a használt szoftvercímekhez, a Microsofttól és a nem a Microsofttól származó szoftverek esetén egyaránt. Az Eszközintelligencia-katalógusban elérheti a szoftvercímekhez előre meghatározott hardverkövetelmények készletét, továbbá új felhasználó által definiált hardverkövetelmény-információkat is létrehozhat az egyéni követelmények teljesítése érdekében. Emellett testre szabhatja az Eszközintelligencia-katalógusban szereplő információkat, és a szoftvercímek adatait kategorizálás céljából feltöltheti a System Center Online szolgáltatásba.  

 Az Eszközintelligencia-katalógus az újonnan kiadott szoftvereket tartalmazó frissítései rendszeresen letölthetők a tömeges katalógusfrissítések végrehajtásához. Emellett a katalógust dinamikusan is frissítheti az Eszközintelligencia szinkronizálási pont helyrendszer-szerepkör használatával.  

###  <a name="BKMK_SoftwareCategories"></a> Szoftverkategóriák  
 Az Eszközintelligencia szoftverkategóriái használatával széles körben kategorizálhatók a leltározott szoftvercímek, emellett adott szoftvercsaládok magas szintű csoportosítására is szolgálnak. Szoftverkategóriát alkothatnak például az energiavállalatok, a kategórián belül pedig külön szoftvercsaládokat az olaj, a gáz vagy a vízenergia. Az Eszközintelligencia-katalógus több előre meghatározott szoftverkategóriával rendelkezik, és létrehozhatók felhasználó által definiált kategóriák a leltározott szoftverek további meghatározása céljából. Az előre meghatározott szoftverkategóriák érvényesítési állapota mindig **Ellenőrizve**értékű, míg az eszközintelligencia-katalógushoz hozzáadott egyéni szoftverkategória-adatok értéke **Felhasználó által definiált**. További információ a szoftverfrissítési kategóriák kezeléséről: [Eszközintelligencia konfigurálása a System Center Configuration Managerben](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md).  

> [!NOTE]  
>  Az Eszközintelligencia-katalógusban tárolt előre definiált szoftverkategória-információk csak olvashatók, nem lehet azokat megváltoztatni vagy törölni. Rendszergazda felhasználók hozzáadása, módosítása vagy törlése a felhasználó által definiált szoftverkategóriákhoz.  

###  <a name="BKMK_SoftwareFamilies"></a> Szoftvercsaládok  
 Az Eszközintelligencia szoftvercsaládjai használatával definiálhatók a szoftverkategóriákban található leltározott szoftvercímek. Az Eszközintelligencia-katalógus több előre meghatározott szoftvercsaláddal rendelkezik, és létrehozhatók felhasználó által definiált kategóriák a leltározott szoftverek további meghatározása céljából. Az előre meghatározott szoftvercsaládok érvényesítési állapota mindig **Ellenőrizve**értékű, míg az eszközintelligencia-katalógushoz hozzáadott egyéni szoftvercsaládadatok értéke **Felhasználó által definiált**. További információ a szoftvercsaládok kezeléséről: [Eszközintelligencia konfigurálása a System Center Configuration Managerben](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md).  

> [!NOTE]  
>  Az előre definiált szoftvercsaládok adatai csak olvashatók, és nem módosíthatók. Rendszergazda felhasználók hozzáadása, módosítása vagy törlése a felhasználó által definiált szoftvercsaládokhoz.  

###  <a name="BKMK_CustomLabels"></a> Szoftvercímkék  
 Az Eszközintelligencia egyéni szoftvercímkéi segítségével a szoftvercímek csoportosítására használható szűrőket hozhat létre, amiket az eszközintelligencia-jelentésekkel tekinthet meg. A szoftvercímkék segítségével valamilyen közös jellemzővel rendelkező szoftvercímek felhasználó által definiált csoportjai hozhatók létre. Így például létrehozhat egy Shareware nevű szoftvercímkét, társíthatja azt a leltározott shareware címekkel, és futtathat egy olyan jelentést, amely megjeleníti az összes olyan szoftvercímet, amelyhez a Shareware szoftvercímkét társították. A szoftvercímkék nem előre definiáltak. A szoftvercímkék érvényesítési állapota mindig **Felhasználó által definiált**. További információ a szoftvercímkék kezeléséről: [Eszközintelligencia konfigurálása a System Center Configuration Managerben](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md).  

###  <a name="BKMK_HardwareRequirements"></a> Hardverkövetelmények  
 A hardverkövetelményekre vonatkozó információkat használva még a szoftverek központi telepítése előtt ellenőrizheti, hogy számítógépe megfelel-e a szoftvercímek hardverkövetelményeinek. Az **Eszközintelligencia** csomópont alatti **Hardverkövetelmények** csomópontban az **Eszközök és megfelelőség** munkaterületen kezelheti a szoftvercímek hardverkövetelményeit. Számos előre meghatározott szoftverkövetelmény található az eszközintelligencia-katalógusban, továbbá új felhasználó által definiált hardverkövetelmény-információt is létrehozhat az egyéni követelmények teljesítése érdekében. Az előre meghatározott hardverkövetelmények érvényesítési állapota mindig **Ellenőrizve**értékű, míg az eszközintelligencia-katalógushoz hozzáadott felhasználó által definiált hardverkövetelmény-adatok értéke **Felhasználó által definiált**. További információ a hardverkövetelmények kezeléséről: [Eszközintelligencia konfigurálása a System Center Configuration Managerben](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md).  

> [!NOTE]  
>  A Configuration Manager-konzolon megjelenő hardverkövetelményeket az Eszközintelligencia-katalógusból olvassa be, és nem a System Center 2012 Configuration Manager ügyfelek leltározott szoftvercímre vonatkozó alapulnak. A hardverkövetelményekre vonatkozó adatok nem frissülnek a System Center Online szinkronizálási folyamatának részeként. Felhasználó által definiált hardverkövetelményeket hozhat létre olyan leltározott szoftverekhez, amelyek nem rendelkeznek társított hardverkövetelményekkel.  

 Alapértelmezés szerint minden felsorolt hardverkövetelmény megjeleníti az alábbi adatokat:  

-   **Szoftvercím**: Megadja a hardverkövetelmény társított szoftvercímet.  

-   **Minimális CPU (MHz)**: Adja meg a minimális processzorsebesség, megahertzben (MHz), a szoftver futtatásához szükséges.  

-   **Minimális RAM (KB)**: Adja meg a minimális memória kilobájt (KB), a szoftver futtatásához szükséges.  

-   **Minimális lemezterület (KB)**: Adja meg a minimális szabad merevlemez-terület, a szoftver futtatásához szükséges.  

-   **Minimális lemezméret (KB)**: Meghatározza a minimum merevlemez méretét, a szoftver futtatásához szükséges.  

-   **Érvényesítési állapot**: Megadja a hardverkövetelmény ellenőrzési állapotát.  

 Az Eszközintelligencia-katalógusban tárolt előre definiált hardverkövetelmények írásvédettek és nem törölhetők.  A rendszergazda felhasználók hozzáadhatnak, módosíthatnak vagy törölhetnek az eszközintelligencia-katalógusban nem tárolt szoftverekre vonatkozó, felhasználó által definiált hardverkövetelményeket.  

##  <a name="BKMK_InventoriedSoftwareTitles"></a> Leltározott szoftvercímek  
 A leltárba vett szoftvercímek adatai megtekinthetők a **Leltározott szoftver** csomópont alatti **Eszközintelligencia** csomópontban, az **Eszközök és megfelelőség** munkaterületen . A Hardverleltározási Ügyfélügynök a leltárba vett szoftverek információt gyűjt a Configuration Manager-ügyfelek az Eszközintelligencia-katalógusban tárolt szoftvercímek alapján.  

> [!WARNING]  
>  A hardverleltározási ügyfélügynök az Eszközintelligencia engedélyezett hardverleltár-jelentési osztályai alapján gyűjti a leltárt. További információ a jelentéskészítés engedélyezéséhez osztályok, lásd: [Eszközintelligencia konfigurálása a System Center Configuration Managerben](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md).  

 Alapértelmezés szerint a következő adatok jelennek meg az összes leltározott szoftvercímnél:  

-   **Név**: Adja meg a leltározott szoftvercím neve.  

-   **Szállítói**: Adja meg a leltározott szoftvercímet kifejlesztő gyártó neve.  

-   **Verzió**: Adja meg a leltározott szoftvercím termékverziója.  

-   **Kategória**: Adja meg a leltározott szoftvercímhez aktuálisan hozzárendelt szoftverkategória.  

-   **Termékcsalád**: Adja meg a leltározott szoftvercímhez aktuálisan hozzárendelt szoftvercsalád.  

-   **Label** [**1**, **2**, and **3**]: Megadja a szoftvercímhez társított egyéni címkék. A leltározott szoftvercímekhez legfeljebb három egyéni címke lehet társítva.  

-   **Count**: A Configuration Manager-ügyfelek, amelyeknek a a szoftvercím számát adja meg.  

-   **Állapot**: Adja meg a leltározott szoftvercím érvényesítési állapota.  

> [!NOTE]  
>  A leltárba vett szoftverekre vonatkozó kategorizálási információkat (a termék nevét, a szállítót, szoftverkategóriát és a szoftvercsaládot) csak a hierarchia legfelső szintű helyén  módosíthatja. Az előre meghatározott kategorizálási adatok módosítását követően a szoftver érvényesítési állapota **Ellenőrizve** értékről **Felhasználó által definiált**értékűre vált.  

##  <a name="AssetIntelligenceSycnronizationPoint"></a> Eszközintelligencia szinkronizációs pontja  
 Az Eszközintelligencia szinkronizációs pontja, a Configuration Manager helyrendszer-szerepkör (a 443-as TCP-port használatával) a System Center online-hoz való kapcsolódáshoz használt dinamikus Eszközintelligencia-katalógus adatait kezeléséhez frissíti. Ez a helyszerepkör csak a hierarchia legfelső szintű helyén telepíthető. Összes Eszközintelligencia-katalógus testreszabása a legfelső szintű helyhez kapcsolódó Configuration Manager konzol használatával kell konfigurálnia. Bár az összes frissítést a legfelső szintű helyen kell konfigurálni, az eszközintelligencia-katalógus adatai a hierarchia más helyeire is replikálódnak. Az Eszközintelligencia szinkronizációs pontja helyszerepkör a katalógus igény szerinti szinkronizálását a System Center Online szolgáltatással, valamint az automatikus katalógusszinkronizálás ütemezését is lehetővé teszi. Új eszközintelligencia-katalógusbeli adatok letöltése mellett az Eszközintelligencia szinkronizációs pontja feltölthet egyéni szoftvercím-adatokat is a System Center Online szolgáltatásba kategorizálás céljából. A Microsoft a System Center Online szolgáltatásba kategorizálásra feltöltött szoftvercímeket nyilvános információként kezeli. Ezért győződjön meg arról, hogy saját egyéni szoftvercímei nem tartalmaznak bizalmas vagy szellemi tulajdont képező adatokat.  

> [!NOTE]  
>  Egy olyan kategorizálatlan szoftvercím elküldése után, amelyre legalább négy kategorizálási kérelem érkezett, a System Center Online kutatói azonosítják és kategorizálják a szoftvercímet, majd az információt elérhetővé teszik az online szolgáltatást használó ügyfelek számára. A kategorizáláskor azok a szoftvercímek élveznek előnyt, amelyekre a legtöbb kategorizálási kérelem érkezett. Az üzletági és az egyéni szoftveralkalmazások általában nem kategorizálhatók, ezért ezeket a szoftvercímeket nem érdemes elküldeni a Microsoftnak.  

> [!NOTE]  
>  Az Eszközintelligencia szinkronizációs pontja helyrendszerszerepkör szükséges a System Center Online szolgáltatáshoz való kapcsolódáshoz. Az Eszközintelligencia szinkronizációs pontja telepítéséről további információkért lásd: [Eszközintelligencia konfigurálása a System Center Configuration Managerben](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md).  

##  <a name="BKMK_AssetIntelligenceHomePage"></a> Az Eszközintelligencia kezdőlapja  
 A **Eszközintelligencia** csomópontja a **eszközök és megfelelőség** munkaterület a Configuration Manager eszközintelligencia kezdőlapján. Az eszközintelligencia-katalógus adatait az **Eszközintelligencia** kezdőlapján található összegző irányítópult-nézetben találja.  

> [!NOTE]  
>  Az **Eszközintelligencia** kezdőlapja nem frissíti automatikusan az adatokat megtekintés közben.  

 Az **Eszközintelligencia** kezdőlapja a következő szakaszokra oszlik:  

-   **Katalógus szinkronizálása**: Információkat biztosít, hogy az Eszközintelligencia engedélyezve van és az Eszközintelligencia szinkronizálási pontjának aktuális állapotát. Emellett itt láthatja a szinkronizálás ütemezését, azt, hogy megtörtént-e az ügyféllicenc-kimutatások importálása, valamint a legutóbbi és a legközelebbi állapotfrissítés időpontját, továbbá az Eszközintelligencia szinkronizációs pontjához tartozó helyrendszer telepítését követő módosítások számát.  

    > [!NOTE]  
    >  Az **Eszközintelligencia** kezdőlapján csak akkor jelenik meg a katalógusszinkronizációs szakasz, ha telepítve lett egy Eszközintelligencia szinkronizációs pontjához tartozó helyrendszerszerepkör.  

-   **Leltározott Szoftverállapot**: A számát és százalékos arányát a leltározott szoftverek, szoftverkategóriák és szoftvercsaládok Microsoft, a rendszergazda, online azonosítása függőben van vagy azonosítatlan és nem függésben levő azonosított által azonosított biztosít. A táblázat ezek számát, a diagram pedig a százalékos arányt tartalmazza.  

##  <a name="BKMK_AssetIntelligenceReports"></a> Eszközintelligencia-jelentések  
 Az Eszközintelligencia-jelentésekben találhatók a Configuration Manager konzolon a **figyelés** munkaterületen, az Eszközintelligencia mappában található a **jelentéskészítési** csomópont. A jelentések a hardverekkel, licenckezeléssel és szoftverekkel kapcsolatos adatokat tartalmazzák. A Configuration Manager-jelentésekkel kapcsolatos további információkért lásd: [a System Center Configuration Manager jelentéskészítési](../../../../core/servers/manage/reporting.md).  

> [!NOTE]  
>  Az eszközintelligencia-jelentésekben megjelenített telepített szoftvercímek és licencinformációk eltérhetnek a ténylegesen telepített szoftvercímek számától, illetve az adott környezetben használt licencek tényleges számától. Ezt a különbséget a vállalati környezetben telepített szoftvercímek licencinformációinak leltározásával kapcsolatos összetett függőségek és korlátozások okozzák. Az eszközintelligencia-jelentések önmagukban nem alkalmasak a megvásárolt szoftverlicencek megfelelőségének ellenőrzésére.  

###  <a name="BKMK_HardwareReports"></a> Az Eszközintelligencia hardverjelentései  
 Az Eszközintelligencia hardverjelentései a szervezetnél található hardvereszközökre vonatkozó információkkal szolgálnak. A hardverleltár-információk (például a sebesség, a memória, a perifériák és így tovább) felhasználásával az Eszközintelligencia hardverjelentései képesek adatokat megjeleníteni az USB-eszközökről, a frissítendő hardverekről, sőt azon számítógépekről is, amelyek még nem állnak készen egy adott a szoftverfrissítésre.  

> [!NOTE]  
>  Az Eszközintelligencia hardverjelentéseinek bizonyos felhasználói adatait a rendszer biztonsági eseménynaplójából gyűjti a program. A jelentések pontossága érdekében a számítógépnek egy új felhasználóhoz való hozzárendelése esetén javasolt törölni ezt a naplót.  

###  <a name="BKMK_LicenseManagementReports"></a> Az Eszközintelligencia licenckezelési jelentései  
 Az Eszközintelligencia licenckezelési jelentései a licenchasználatra vonatkozó információkkal szolgálnak. A licencjelentés felsorolja a telepített Microsoft-alkalmazásokat a Microsoft Licenckimutatással (MLS) kompatibilis formátumban. Ez kényelmes módot nyújt a megvásárolt licenceknek a használt licencekkel való egyeztetésére . Más licenckezelési jelentések azon számítógépekkel kapcsolatos információkkal szolgálnak, amelyek a Kulcskezelő szolgáltatást (KMS) futtató kiszolgálóként működnek az operációsrendszer-aktiválási statisztikákhoz.  

> [!IMPORTANT]  
>  Az Eszközintelligencia számos licenckezelési jelentése a mennyiségi licencelés felügyeletének egyik módját jelentő KMS működésére vonatkozó információkat jelenít meg. Ha még nincs megvalósítva egy KMS-kiszolgáló, előfordulhat, hogy egyes jelentések nem adnak vissza adatot. A KMS-szel kapcsolatos további tudnivalókért keressen a KMS kulcsszóra a [Microsoft TechNeten](http://go.microsoft.com/fwlink/?linkid=3225).  

###  <a name="BKMK_SoftwareReports"></a> Az Eszközintelligencia szoftverjelentései  
 Az Eszközintelligencia szoftverekről szóló jelentései a szervezetben lévő számítógépeken telepített szoftvercsaládokról, kategóriákról és adott szoftvercímekről nyújtanak információt. A szoftverjelentések tájékoztatnak a böngésző segítő objektumairól, az automatikusan elinduló szoftverekről és így tovább. Ezen jelentések révén azonosíthatók a reklámprogramok, kémprogramok és egyéb kártevők, illetve a felesleges szoftverek is a gördülékenyebb szoftverbeszerzés és -támogatás érdekében.  

###  <a name="BKMK_SoftwareIdTagReports"></a> Az Eszközintelligencia szoftverazonosító címkével ellátott szoftverekre vonatkozó jelentései  
 Az Eszközintelligencia szoftverazonosító címkével ellátott szoftverekre vonatkozó jelentései az ISO/IEC 19770-2 szabványnak megfelelő szoftverazonosító címkeadatokat tartalmazó szoftverekkel kapcsolatos információkkal szolgálnak. A szoftverazonosító címkék a telepített szoftverek azonosítására használható mérvadó információkat tartalmaznak. Ha engedélyezte az SMS_SoftwareTag Hardverleltár-jelentési osztályát, a Configuration Manager gyűjti a szoftverazonosító címkeadatokat tartalmazó szoftverekkel kapcsolatos információkat. Az alábbi jelentések a szoftverekre vonatkozó információkat nyújtanak:  

-   **14A szoftver - engedélyezett szoftverazonosító címkével engedélyezett ellátott szoftverek keresése**: Ez a jelentés egy engedélyezett szoftverazonosító címkével rendelkező telepített szoftverek számát tartalmazza.  

-   **14B szoftver - meghatározott szoftverazonosító címkével rendelkező számítógépek ellátott szoftverekkel**: Ez a jelentés felsorolja az összes olyan számítógépet, egy meghatározott engedélyezett szoftverazonosító címkével ellátott szoftverekkel.  

-   **Telepített szoftverek 14C - szoftver szoftverazonosító címkével ellátott szoftver egy adott számítógép**: Ez a jelentés egy meghatározott engedélyezett szoftverazonosító címkével egy adott számítógépen telepített összes szoftvert tartalmazza.  

###  <a name="BKMK_ReportingLImitations"></a> Az Eszközintelligencia jelentéskészítési korlátozásai  
 Az Eszközintelligencia jelentései nagy mennyiségű adatot szolgáltatnak a telepített szoftvercímekről, illetve a megvásárolt és használt szoftverlicencekről. Azonban nem ajánlott azokat kizárólagos információforrásként használni a megvásárolt szoftverek licenceinek ellenőrzéséhez.  

####  <a name="BKMK_ExampleDependencies"></a> Példák függőségekre  
 Az eszközintelligencia-jelentések a  telepített szoftvercímekre és licencinformációkra vonatkozó adatainak pontossága eltérhet a tényleges használt mennyiségtől. Ezt a különbséget a vállalati környezetben használatban lévő szoftvercímek licencinformációinak leltározásával kapcsolatos összetett függőségek okozzák. Az alábbi példák bemutatják a vállalatnál telepített szoftvereknek az eszközintelligencia-jelentések segítségével való leltározásával kapcsolatos függőségeket, amelyek befolyásolhatják a  eszközintelligencia-jelentések-jelentések pontosságát:  

 **Az ügyfélhardver leltárározásával kapcsolatos függőségek**  
 Telepített Eszközintelligencia szoftverjelentései Hardverleltár engedélyezése az Eszközintelligencia-jelentések kiterjesztése a Configuration Manager-ügyfelek összegyűjtött adatokon alapulnak. A Hardverleltár-jelentési függőség, mert a Eszközintelligencia-jelentések csak a Configuration Manager ügyfelek, amelyek sikeresen befejezték a hardverleltározási folyamatokat a szükséges Eszközintelligencia WMI jelentéskészítési osztályok az adatokat tükrözik. Emellett a Configuration Manager ügyfél Hardverleltár folyamatait a rendszergazda által megadott ütemezés szerint hajtsa végre, mert előfordulhat némi késleltetés az adatok jelentésében, amely hatással van az Eszközintelligencia-jelentések pontosságát. Például előfordulhat, hogy egy leltározott licencelt szoftvercímet eltávolítottak, miután az ügyfél sikeresen befejezte a hardverleltározási ciklust. Azonban a szoftvercím van jelenik meg az Eszközintelligencia-jelentések csak az ügyfél következő ütemezett Hardverleltár-jelentési ciklus.  

 **Szoftvercsomagolási függőségek**  
 Eszközintelligencia-jelentések a telepített szoftverek cím összegyűjtött adatokon szabványos Configuration Manager ügyfél Hardverleltár folyamatait használatával alapulnak, mert néhány cím szoftveradatokat nem gyűjtik be megfelelően. Például a szabványos telepítési folyamatoknak nem megfelelő vagy a telepítés előtt módosított szoftvertelepítések pontatlan eszközintelligencia-jelentésekhez vezethetnek.  

####  <a name="BKMK_LegalLimitations"></a> Jogi korlátozások  
 Az eszközintelligencia-jelentésekben megjelenő információkra számos korlátozás vonatkozik, és azok nem értelmezhetők jogi, számviteli vagy más szakmai útmutatásként. Az eszközintelligencia-jelentések által biztosított információk kizárólag tájékoztatásul szolgálnak, és nem használhatók egyedüli információforrásként a szoftverlicenc-használat megfelelőségének megállapításához.  

 A következő példákban szereplő korlátozások a vállalatnál telepített szoftvereknek és a licenchasználatnak az Eszközintelligencia használatával történő leltározásával kapcsolatosak, és befolyásolhatják az eszközintelligencia-jelentések pontosságát:  

 **A Microsoft licenchasználati mennyiségi korlátozásai**  
 -   A beszerzett Microsoft-szoftverlicencek mennyisége a rendszergazdák által szolgáltatott információkon alapul, és azokat figyelmesen meg kell vizsgálni, hogy a megfelelő számú szoftverlicenc legyen megadva.  

-   A Microsoft szoftverlicencek jelentett mennyisége csak a mennyiségi licencelési programokon keresztül beszerzett Microsoft szoftverlicencekkel kapcsolatos információt tartalmazza, és nem tükrözi a kiskereskedelmi, OEM- vagy más szoftverlicenc-értékesítési csatornákon keresztül beszerzett szoftverlicencekre vonatkozó információkat.  

-   Előfordulhat, hogy a jelentésben szereplő Microsoft szoftverlicencek mennyisége a szoftver viszonteladói jelentéskészítési követelményei és ütemezése miatt nem tartalmazza az elmúlt 45 napban beszerzett szoftverlicenceket.  

-   Előfordulhat, hogy a Microsoft szoftverlicencek mennyisége nem tartalmazza a vállalati fúzió vagy felvásárlás miatt átvitt szoftverlicenceket.  

-   A Microsoft mennyiségi licencelési (MVLS) szerződés által tartalmazott nem szabványos feltételek és kikötések befolyásolhatják a szoftverlicencek jelentett számát, ezért előfordulhat, hogy a Microsoft képviselőjével közösen meg kell vizsgálni azt.  

 **A telepített szoftvercímek mennyiségi korlátozásai**  
 Configuration Manager-ügyfelek a Hardverleltár-jelentési ciklusainak az Eszközintelligencia-jelentések a telepített szoftverek mennyiségének pontos kimutatásához sikeresen be kell. Emellett előfordulhat, hogy egy sikeres hardverleltározási jelentéskészítési ciklust követően a licencelt szoftvercímek telepítése és eltávolítása között késleltetés lép fel, amely nem szerepel azon eszközintelligencia-jelentésekben, amelyeket az ügyfél által jelentett soron következő ütemezett hardverleltár előtt futtattak.  

 **Licencegyeztetési korlátozások**  
 A megvásárolt szoftverlicencek mennyisége a telepített szoftverek mennyiségének egyeztetés számítja ki a rendszergazda által megadott licencmennyiséget összehasonlítása és mennyiségét telepített szoftvercímek begyűjti a Configuration Manager ügyfél hardverleltározásai a rendszergazda által beállított ütemezés szerint. Ez az összehasonlítás nem tükrözi a Microsoft a licencelési állapotra vonatkozó végleges következtetését. A tényleges licencelési állapot az adott szoftvercímtől és a licencfeltételek által biztosított használati jogoktól függ.  

##  <a name="BKMK_ValidationStates"></a> Az Eszközintelligencia érvényesítési állapotai  
 Az Eszközintelligencia érvényesítési állapotai az eszközintelligencia-katalógus adatainak forrás- és aktuális érvényesítési állapotát jelzik. A következő táblázat az Eszközintelligencia lehetséges érvényesítési állapotait és az azokat okozó rendszergazdai műveleteket tartalmazza.  

|**Állapot**|**Meghatározás**|**Rendszergazdai művelet**|**Megjegyzés**|  
|---------------|--------------------|------------------------------|-----------------|  
|**Ellenőrizve**|A katalóguselemet a System Center Online kutatói definiálták.|Nincs.|A legjobb állapot.|  
|**Felhasználó által definiált**|A katalóguselemet nem a System Center Online kutatói definiálták.|A helyi katalógus adatainak testreszabása.|Ez az állapot az eszközintelligencia-jelentésekben jelenik meg.|  
|**Függőben**|A katalóguselem nem a System Center Online kutatói által definiált, de az elem el lett küldve a System Center Online-hoz kategorizálásra.|A System Center Online-tól kért kategorizálás.|A katalóguselem ebben az állapotban marad, amíg a System Center Online kutatói nem kategorizálják, és meg nem történt az eszközintelligencia-katalógus szinkronizálása.|  
|**Frissíthető**|Az egymás utáni katalógusszinkronizálás során a System Center Online másképp definiált egy felhasználó által definiált elemet.|A helyi eszközintelligencia-katalógus testreszabása az elem felhasználó által definiáltként való kategorizálásához.|Az Ütközés feloldása műveletet használva eldöntheti, hogy az új kategorizálási információt vagy a korábbi, felhasználó által definiált értéket szeretné-e használni. Ütközések megoldásával kapcsolatos további információkért lásd: [az Eszközintelligencia a System Center Configuration Managerben műveletei](../../../../core/clients/manage/asset-intelligence/operations-for-asset-intelligence.md).|  
|**Kategorizálatlan**|A katalóguselem nincs definiálva a System Center Online kutatói által, az elem nem lett elküldve a System Center Online-nak kategorizálásra, és a rendszergazda nem rendelt hozzá felhasználó által definiált kategorizálási értéket.|Nincs.|Kérjem kategorizálást, vagy testre is szabhatja helyi katalógus adatait.<br /><br /> Kategorizálás kérésével kapcsolatos további információkért lásd: [az Eszközintelligencia a System Center Configuration Managerben műveletei](../../../../core/clients/manage/asset-intelligence/operations-for-asset-intelligence.md).<br /><br /> A szoftvercím kategóriájának kapcsolatos további információkért lásd: [az Eszközintelligencia a System Center Configuration Managerben műveletei](../../../../core/clients/manage/asset-intelligence/operations-for-asset-intelligence.md).|  

> [!NOTE]  
>  A System Center Online-hoz kategorizálási célból elküldött katalóguselemek érvényesítési állapota a központi adminisztrációs helyen **Függőben** értékűként van feltüntetve, azonban az elsődleges gyermekhelyeken továbbra is **Kategorizálatlan** értékűként.  

> [!NOTE]  
>  Miután kategorizálási ütközés fel lett oldva, az elem nincs érvényesítve, kivéve, ha újabb adatkategorizálási frissítések az elemre vonatkozó új információt vezetnek be.  

 Ha érvényesítési állapota állnak lehet egy állapotból a másikra, tekintse meg a [érvényesítési állapotváltásainak példái a System Center Configuration Manager eszközintelligencia](../../../../core/clients/manage/asset-intelligence/example-validation-state-transitions-for-asset-intelligence.md).  

