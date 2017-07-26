---
title: "Forráshierarchia stratégiájának forrás |} Microsoft Docs"
description: "Egy forráshierarchiát, és az adatok gyűjtését a forráshelyről, a System Center Configuration Manager áttelepítési feladat konfigurálása előtt."
ms.custom: na
ms.date: 1/3/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4800a800-66c8-4c35-aebe-e413a23790c1
caps.latest.revision: 6
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: cb5f7bf52a53935ca61b0e1b66822919b17d33e2
ms.openlocfilehash: 0619de32f859f512ee1c9f5a9c83ef8d04a256ca
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="plan-a-source-hierarchy-strategy-in-system-center-configuration-manager"></a>A System Center Configuration Managerben forráshierarchia stratégiájának tervezése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Áttelepítési feladat beállítása a System Center Configuration Manager környezetben, mielőtt egy forráshierarchiát, és adatokat gyűjt a legalább egy forráshelyről ebben a hierarchiában. A következő szakaszok segítségével tervezheti meg a forráshierarchiák, Forráshelyek konfigurálását, és a meghatározására, hogyan Configuration Manager információt gyűjt a forráshelyeket a forráshierarchiában. 

##  <a name="BKMK_Source_Hierarchies"></a> Forráshierarchiák  
A forráshierarchia a Configuration Manager-hierarchia, amely az áttelepíteni kívánt adatokat tartalmaz. Állítsa be az áttelepítést, és a forráshierarchia megadása, meg kell adnia a forráshierarchia legfelső szintű helyén. Ez a hely más néven forráshely. Hogy áttelepítheti az adatokat a forráshierarchiában további helyeket más néven forráshely.  

-   Áttelepítési feladat beállítása a Configuration Manager 2007 verziójú forráshierarchia adatainak áttelepítésére, konfigurálja úgy, hogy egy vagy több konkrét forráshely a forráshierarchia adatainak áttelepítésére.  

-   Ha a System Center 2012 Configuration Manager futtató forráshierarchia adatainak áttelepítésére áttelepítési feladat beállítása, vagy később, akkor csak kell megadnia a legfelső szintű helyen.  

Egyszerre csak egy forráshierarchia állíthat be.  

-   Ha állít be egy új forráshierarchiához, adott hierarchia automatikusan lesz az aktuális forráshierarchia cseréje a korábbi forráshierarchiát.  

-   Ha beállít egy forráshierarchiát, meg kell adnia a forráshierarchia legfelső szintű helyén, a Configuration Manager az SMS-szolgáltató és a forráshely helyadatbázisához való kapcsolódáshoz használandó hitelesítő adatok megadása.  

-   A Configuration Manager ezen hitelesítő adatok használatával futtatja az adatgyűjtést az objektumok és terjesztési pontok információ lekérése a forráshelyről.  

-   Az adatgyűjtési folyamat részeként megtörténik a forráshierarchiában található gyermekhelyek azonosítása.  

-   Ha a forráshierarchia egy Configuration Manager 2007 hierarchia, állíthat be ezeket a további helyeket forráshelyként az egyes forráshelyeknél külön hitelesítő adatokkal.  

Bár egymás után több forráshierarchiák állíthat be, az áttelepítés lehet aktív csak egy forráshierarchiára vonatkozóan egyszerre.  

-   Ha az aktuális forráshierarchia az áttelepítés befejezése előtt beállítása további forráshierarchiát, a Configuration Manager megszakítja az aktív áttelepítési feladatokat, és elhalasztja az ütemezett áttelepítési feladatokat az aktuális forráshierarchiára vonatkozóan.  

-   Az újonnan konfigurált forráshierarchiából válik az aktuális forráshierarchia, és az eredeti forráshierarchia pedig inaktívvá.  

-   Majd állíthatja be kapcsolat hitelesítő adatait, a további Forráshelyek kiválasztásához és az áttelepítési feladatok az új forráshierarchiára vonatkozóan.  

Ha inaktív forráshierarchia visszaállításakor, és korábban nem használt **áttelepítési adatok törlése**, megtekintheti a korábban konfigurált áttelepítési feladatokat adott forráshierarchiára vonatkozóan. Az adott hierarchiából azonban csak azt követően tudja folytatni az áttelepítést, hogy újrakonfigurálta a hierarchia megfelelő forráshelyeinek eléréséhez szükséges hitelesítő adatokat, majd átütemezte a be nem fejeződött áttelepítési feladatokat.  

> [!CAUTION]  
>  Ha egyetlen forráshierarchiából telepít át adatokat, minden további forráshierarchiának egy egyedi helykódsorozatot kell tartalmaznia.  

További információt a forráshierarchia konfigurálásáról lásd: [forráshierarchiák és Forráshelyek System Center Configuration Manager áttelepítéshez](../../core/migration/configuring-source-hierarchies-and-source-sites-for-migration.md)  

##  <a name="BKMK_Source_Sites"></a> Forráshelyek  
 A forráshelyek azok a helyek a forráshierarchiában, amelyek az áttelepíteni kívánt adatokkal rendelkeznek. A forráshierarchia legfelső szintű helye mindig az első forráshely. Amikor az áttelepítés egy új forráshierarchia első forráshelyéről adatokat gyűjt, az adott hierarchiában található további helyekről is felderít információkat.  

 A kezdeti forráshelyre vonatkozó adatgyűjtés befejezése utáni műveletek a forráshierarchia termékverziójától függőek.  

### <a name="source-sites-that-run-configuration-manager-2007-sp2"></a>Configuration Manager 2007 SP2-t futtató forráshelyek  
 Miután az adatgyűjtés a Configuration Manager 2007 SP2-hierarchia kezdeti forráshelyéről, nem rendelkeznek beállítása további forráshelyeket, az áttelepítési feladatok létrehozása előtt. Azonban mielőtt adatokat telepítene át további helyeket, be kell állítania a további helyeket forráshelyként, és a System Center Configuration Manager kell sikeres adatgyűjtést ezekről a helyekről.  

 Az adatok gyűjtését a további helyeket, külön-külön beállíthatja a helyekhez forráshelyként. Ehhez adja meg a hitelesítő adatokat a System Center Configuration Manager az SMS-szolgáltató és a Helyadatbázis az egyes Forráshelyek való kapcsolódáshoz. Miután beállította a forráshelyre vonatkozóan a hitelesítő adatokat, az adatgyűjtési folyamat az adott hely kezdődik.  

 A Configuration Manager 2007 SP2-forráshierarchiában további forráshelyeket beállításakor be kell állítania Forráshelyek felülről lefelé, ami azt jelenti, hogy beállította az alsó szintű helyeket utolsó. Konfigurálhatja forráshelyeket a hierarchia valamelyik ágában bármikor, de be kell állítania egy helyet, mint amit a forráshely bármelyik gyermekhelyét forráshelyként beállítása előtt.  

> [!NOTE]  
>  A Configuration Manager 2007 SP2-hierarchia csak elsődleges helyek áttelepítése támogatott.  

### <a name="source-sites-that-run-system-center-2012-configuration-manager-or-later"></a>A System Center 2012 Configuration Manager futtató Forráshelyek vagy újabb verzió  
 Miután az adatgyűjtés a System Center 2012 Configuration Manager vagy újabb hierarchia kezdeti forráshelyéről, nem rendelkeznek a forráshierarchiában további forráshelyeket beállításához. Ennek az az oka eltérően a Configuration Manager 2007, a Configuration Manager ezen verziói olyan megosztott adatbázist használnak, és a megosztott adatbázis lehetővé teszi az azonosítását, majd a kezdeti forráshelyről az összes rendelkezésre álló objektumok áttelepítését.  

 Ha a hozzáférési fiókok beállítása az adatok gyűjtéséhez, előfordulhat, hogy kell biztosítania a **forráshely SMS-szolgáltató fiókja** a forráshierarchiában több számítógéphez való hozzáférés. Erre akkor lehet szükség, ha a forráshely az SMS-szolgáltató több példányát támogatja, és mindegyik példány külön számítógépen fut. Amikor megkezdődik az adatgyűjtés, a célhierarchia legfelső szintű helye kapcsolatba lép a forráshierarchia legfelső szintű helyével, hogy azonosítsa az adott helyhez tartozó SMS-szolgáltatót. Csak az SMS-szolgáltató első példányát azonosítja a folyamat. Ha az adatgyűjtési folyamatnak nem sikerül elérnie az SMS-szolgáltatót az azonosított helyen, a folyamat leáll, és nem próbál kapcsolódni az adott helyen az SMS-szolgáltató példányát futtató további számítógépekhez.  

##  <a name="BKMK_Data_Gathering"></a> Adatgyűjtés  
 Közvetlenül a forráshierarchia megadása, állítsa be a hitelesítő adatokat a forráshierarchiában található mindegyik további forráshelyhez vagy megosztotta egy forráshely terjesztési pontjait, a Configuration Manager elindul az adatok gyűjtését a forráshelyről.  

 Az adatgyűjtési folyamat aztán egyszerű ütemezés alapján ismétlődik, hogy szinkronban maradjanak az adatok a forráshelyen található adatokon végbemenő változásokkal. A folyamat alapértelmezés szerint négy óránként ismétlődik. Ez a ciklus ütemezése szerkesztésével módosíthatja a **tulajdonságok** a forráshely. A kezdeti adatgyűjtési folyamata a Configuration Manager adatbázisa található összes objektumot át kell néznie, és egy befejezése hosszabb időt is igénybe vehet. A későbbi adatgyűjtési folyamatok csak az adatok változásait azonosítják, így végrehajtásuk kevesebb ideig tart.  

 Az adatgyűjtéshez a célhierarchia legfelső szintű helye kapcsolódik a forráshely SMS-szolgáltatójához és helyadatbázisához, hogy beolvassa az objektumok és terjesztési pontok listáját. Az ilyen kapcsolatok a forráshely hozzáférési fiókjait használják. Az adatgyűjtéshez szükséges konfigurálási kapcsolatos információkért lásd: [előfeltételei a System Center Configuration Manager áttelepítési](../../core/migration/prerequisites-for-migration.md).  

 Indítsa el, és állítsa le az adatgyűjtési folyamat használatával **adatok összegyűjtése most** és **adatgyűjtés leállítása** a Configuration Manager konzolon.  

 Miután **adatgyűjtés leállítása** egy forráshelynél bármilyen okból újra kell konfigurálnia a hitelesítő adatokat a hely ezt követően gyűjthet adatokat erről a helyről újra. Konfigurálja újra a forráshelyet, amíg a Configuration Manager nem tudja azonosítani, új objektumokat vagy a korábban áttelepített objektumokat a webhelyen változásait.  

> [!NOTE]  
>  Mielőtt egy önálló elsődleges hely központi adminisztrációs hellyel rendelkező hierarchiává bővít, le kell állítania minden az adatgyűjtés. Újrakonfigurálhatja az adatgyűjtést a helybővítés befejezése után.  

### <a name="gather-data-now"></a>konzoljának  
 Ha a kezdeti adatgyűjtési folyamat egy helyre vonatkozóan befejeződött, a folyamat ismétli magát, hogy azonosítsa a legutóbbi adatgyűjtési ciklus óta megváltozott objektumokat. Használhatja a **adatok összegyűjtése most** műveletet a Configuration Manager konzolon, azonnal el tudja indítani a folyamatot, és alaphelyzetbe állítja a következő ciklus kezdési idejét.  

 Miután egy forráshelyre vonatkozóan sikeresen befejeződött egy adatgyűjtési folyamat, megoszthatja a forráshely terjesztési pontjait, és konfigurálhatja az áttelepítési feladatokat, amelyek elvégzik a helyről az adatok áttelepítését. Az adatgyűjtés áttelepítés ismétlődő folyamat, és azt továbbra is fennáll, amíg meg nem változtatják a forráshierarchiát, vagy használjon **adatgyűjtés leállítása** az adatgyűjtési folyamat az adott hely befejezéséhez.  

### <a name="stop-gathering-data"></a>és  
 Használhat **adatgyűjtés leállítása** az adatgyűjtési folyamat egy forráshelyre vonatkozóan, ha már nem szeretné azonosítsa az adott hely új vagy megváltozott objektumait, ha a Configuration Manager befejezéséhez. Ez a művelet is megakadályozza, hogy a Configuration Manager kínál a célhierarchiában lévő ügyfelek a forrás megosztott terjesztési pontjait tartalomhelyként áttelepített tartalomhoz.  

 Állítsa le az adatgyűjtést a forráshelyekről, futtatnia kell **adatgyűjtés leállítása** a az alsó szintű Forráshelyek, majd ismételje meg a műveletet minden szülőhelyen. A forráshierarchia legfelső szintű helyén kell utoljára leállítania az adatgyűjtést. Előbb az összes gyermekhelyen kell leállítania az adatgyűjtést, csak ezután hajthatja végre ezt a műveletet a szülőhelyen. Az adatgyűjtést rendszerint csak akkor kell leállítania, amikor készen áll az áttelepítési folyamat befejezésére.  

 Miután leállította az adatgyűjtést a forráshelyen, korábban összegyűjtött adatok objektumok és gyűjtemények az adott hely használhatóak maradnak arra használja, ha beállította az új áttelepítési feladatoknál. Azonban nem látja az új objektumokat vagy gyűjteményeket, sem látnak meglévő objektumokon végrehajtott módosítások. Ha újra konfigurálja a forráshelyet, és ismét megkezdi az adatgyűjtést, látni fogja a korábban áttelepített objektumok adatait és állapotát.  

