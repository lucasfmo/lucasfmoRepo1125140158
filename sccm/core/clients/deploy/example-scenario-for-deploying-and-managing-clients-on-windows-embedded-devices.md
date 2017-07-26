---
title: "Példa - Windows Embedded-ügyfelek központi telepítése |} Microsoft Docs"
description: "Tekintse meg a központi telepítésére és felügyeletére Windows Embedded-eszközökön a System Center Configuration Manager ügyfelek példát."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 10049c89-b37c-472b-b317-ce4f56cd4be7
caps.latest.revision: 8
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: c535bc62497b5ff0b60ca266c28630d890af3604
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="example-scenario-for-deploying-and-managing-system-center-configuration-manager-clients-on-windows-embedded-devices"></a>Példa központi telepítésére és felügyeletére Windows Embedded-eszközökön a System Center Configuration Manager ügyfelek

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ez a forgatókönyv bemutatja, hogyan kezelhetők az írási szűrő alkalmas Windows Embedded-eszközök konfigurációs Manager.If a beágyazott eszközei nem támogatják az írási szűrőket, úgy fognak működni, mint a Configuration Manager-ügyfelek, és ezeket az eljárásokat nem érvényesek.  

A coho Vineyard & Winery látogatóközpontot nyit, és szüksége van a számítógépeken, melyek Windows Embedded, interaktív bemutatók futtatásához. Az épület a az új látogatóközpont épülete nincs közel az informatikai részleg, a számítógépek távolról kell kezelni. Mellett az bemutatókat futtató szoftver ezeknek az eszközöknek a vállalati biztonsági házirendeknek ahhoz, hogy naprakész vírusvédelmi szoftvert kell futtatnia. A számítógépek futtatnia kell a hét, állásidő nélkül a látogatóközpont meg van nyitva.  

 A coho már futtatja a hálózatán lévő eszközök kezelése a Configuration Manager. A Configuration Manager az Endpoint Protection futtatásához, és a szoftverfrissítések és alkalmazások telepítéséhez van konfigurálva. Azonban mivel az informatikai csapat régebben nem kezelt Windows Embedded-eszközök előtt, Jane, a Configuration Manager rendszergazdája, egy kísérlet keretében két számítógépet a fogadó előterében vannak felügyel futnak.   

 Kezelése a Windows Embedded-eszközökre, amelyek az engedélyezett írási szűrőkkel, Jane a következő lépésekkel a Configuration Manager-ügyfél telepítését, az ügyfél védelméről az Endpoint Protection szolgáltatással és az interaktív bemutató szoftver telepítéséhez.  

1.  Jane olvasási hogyan használja a Windows Embedded-eszközök az írási szűrőket, és hogyan Configuration Manager könnyíti ezt meg automatikus letiltásával és újbóli engedélyezése az írási szűrők, tegye a szoftver telepítését.  

     További információkért lásd: [tervezése a System Center Configuration Manager Windows Embedded-eszközökre történő központi ügyféltelepítésre](../../../core/clients/deploy/plan/planning-for-client-deployment-to-windows-embedded-devices.md).  

2.  Mielőtt telepítené a Configuration Manager-ügyfelet, Jane létrehoz egy új lekérdezés alapú eszközgyűjteményt a Windows Embedded-eszközökön. Mivel a vállalat szokásos névadási formát használ számítógépeinek azonosítására, Jane egyedileg azonosíthatja a Windows Embedded-eszközöket a számítógép nevének első hat betűje alapján: **WEMDVC**. A következő WQL-lekérdezést használja a gyűjtemény létrehozásához: **select SMS_R_System.NetbiosName from SMS_R_System where SMS_R_System.NetbiosName like "WEMDVC%"**  

     Ez a gyűjtemény teszi lehetővé a Windows Embedded-eszközök felügyeletét különböző konfigurációs lehetőségekkel más eszközökről. Ezt a gyűjteményt fogja használni az újraindítások felügyeletére, az Endpoint Protection központi telepítésére az ügyfélbeállításokkal együtt, valamint az interaktív bemutató alkalmazás központi telepítésére.  

     Lásd: [gyűjtemények létrehozása a System Center Configuration Managerben](../../../core/clients/manage/collections/create-collections.md).  

3.  Jane konfigurál egy karbantartási időszakot a gyűjtemény számára, hogy a bemutató alkalmazás telepítésénél és annak frissítésénél szükséges újraindítások ne a látogatóközpont nyitvatartási ideje alatt történjenek. A nyitvatartási idő hétfőtől vasárnapig 09:00 és 18:00 óra között lesz. A karbantartási időszakot minden napra 18:30 és 06:00 óra közé állítja be.  

4.  További információkért lásd: [a System Center Configuration Manager karbantartási időszakok használata](../../../core/clients/manage/collections/use-maintenance-windows.md).  

5.  Jane ezután beállítja az egyedi ügyfél-eszközbeállítást az Endpoint Protection-ügyfél telepítéséhez az **Igen** választásával a következő beállításoknál, majd központilag telepíti ezt az egyedi ügyfélbeállítást a Windows Embedded-eszközök gyűjteményére:  

    -   **Endpoint Protection ügyfél telepítése az ügyfélszámítógépeken**  

    -   **Az írási szűrőket tartalmazó Windows Embedded-eszközök esetén hajtsa végre az Endpoint Protection ügyféltelepítést (többszöri újraindítás szükséges)**  

    -   **Ügyféltelepítés engedélyezése az Endpoint Protection részére, és újraindítás a karbantartási ablakokon kívül**  

     Ha a Configuration Manager-ügyfél telepítve van, ezek a beállítások az Endpoint Protection ügyfél telepítése, és győződjön meg arról, hogy azt az a telepítés részeként megőrződjön az operációs rendszerben, hanem csak az átmeneti területre íródnak. A vállalat biztonsági házirendje megköveteli, hogy mindig telepítve legyen egy kártevőirtó szoftver, és Jane nem szeretné megkockáztatni, hogy a számítógépek akár az újraindítás rövid időszaka alatt is védelem nélkül maradjanak.  

    > [!NOTE]  
    >  Az Endpoint Protection-ügyfél telepítéséhez szükséges újraindítások egyszer fordulnak elő, az eszközök beállítási időszakában, a látogatóközpont működése előtt. A rendszeres központi telepítésével ellentétben az alkalmazások és a szoftver definíciófrissítéseit amikor legközelebb az Endpoint Protection ügyfél telepítve van az adott eszközön valószínűleg akkor fog megtörténni, amikor a vállalat Configuration Manager következő verziójára frissít.  

     További információkért lásd: [Endpoint Protection konfigurálása a System Center Configuration Managerben](../../../protect/deploy-use/configure-endpoint-protection.md).  

6.  A konfigurációs beállítások, az ügyfél most már a helyén Jane előkészíti a Configuration Manager-ügyfelek telepítése. Az ügyfelek telepítésének megkezdése előtt manuálisan kell letiltania az írási szűrőket a Windows Embedded-eszközökön. Elolvassa a számítógépekhez kapott OEM dokumentációt, és az utasításokat követve letiltja az írási szűrőket.  

     Jane átnevezi az eszközt, hogy a vállalat szokásos névadási formáját használja, majd manuálisan telepíti az ügyfelet CCMSetup futtatásával a következő paranccsal egy leképzett meghajtóról, amelyen az ügyfél forrásfájljai találhatók: **CCMSetup.exe /MP:mpserver.cohovineyardandwinery.com SMSSITECODE = CO1**  

     Ez a parancs telepíti az ügyfelet, hozzárendeli az ügyfelet a felügyeleti ponthoz, melynek teljes intranetes tartományneve **mpserver.cohovineyardandwinery.com**, és hozzárendeli az ügyfelet a **CO1**nevű elsődleges helyhez.  

     Jane tudja, hogy mindig hosszú időt vesz igénybe az ügyfelek telepítése, és állapotuk visszajelzése a helynek. Ezért vár az ügyfél sikeres telepítésének, helyhez való hozzárendelésének és az általa létrehozott Windows Embedded-eszközök gyűjteményében ügyfélként való megjelenésének ellenőrzésével.  

     Kiegészítő Visszajelzésként ő ellenőrzi a tulajdonságokat a Configuration Manager Vezérlőpult az eszközökön, és összehasonlítja azokat a hely által felügyelt szokásos Windows alapú számítógépekkel. Például az **Összetevők** lapon a **Hardverleltárügynök** beállítása **Engedélyezve**, és a **Műveletek** lapon 11 művelet áll rendelkezésre, melyek között van a **Központi alkalmazástelepítés kiértékelési ciklusa** és a **Felderítés adatgyűjtési ciklusa**is.  

     Miután meggyőződött arról, hogy az ügyfelek telepítése és hozzárendelése sikeres volt, megkapták az ügyfélházirendet a felügyeleti pontról, Jane az OEM utasításai alapján manuálisan engedélyezi az írási szűrőket.  

     További információkért lásd:  

    -   [Ügyfélszoftverek központi telepítése Windows rendszerű számítógépekre a System Center Configuration Managerben](../../../core/clients/deploy/deploy-clients-to-windows-computers.md)  

    -   [Az ügyfelek hozzárendelése egy helyet a System Center Configuration Managerben](../../../core/clients/deploy/assign-clients-to-a-site.md)  

7.  Most, hogy a Configuration Manager-ügyfél telepítve van a Windows Embedded-eszközökön, Jane ellenőrzi, hogy tudja felügyelni azokat a ugyanúgy, mint a szokásos Windows-ügyfeleket. Például a Configuration Manager-konzolról távolról tudja felügyelni azokat használatával a távvezérlés, ügyfélházirendet kezdeményezhet számukra, és megtekintheti az ügyfél tulajdonságait és hardverleltárját.  

     Mivel ezek az eszközök egy Active Directory-tartományhoz csatlakozik, ő nem kell saját kezűleg jóváhagynia azokat megbízható ügyfelekként, és a Configuration Manager-konzolon ellenőrzi, hogy jóvá van hagyva.  

     További információkért lásd: [Ügyfélszoftverek kezelése a System Center Configuration Managerben](../../../core/clients/manage/manage-clients.md).  

8.  Az interaktív bemutató szoftver telepítéséhez Jane a **Szoftver központi telepítése varázsló** t futtatja, és konfigurálja a szükséges alkalmazást. A varázsló **Felhasználói élmény** oldalán az **Írási szűrő kezelése a Windows Embedded eszközökön** szakaszban elfogadja az alapértelmezett beállítást, ami **A változtatások véglegesítése a határidő lejártakor vagy karbantartási időszakban (újraindítást igényel)**.  

     Jane megtartja az írási szűrők alapértelmezett beállítását, hogy megtartsa az alkalmazást egy újraindítás után, így az mindig a látogatók rendelkezésére áll a számítógépeken. A napi karbantartási időszak egy biztonságos időtartamot biztosít, ami alatt megtörténhetnek a telepítéshez és a frissítésekhez kapcsolódó újraindítások.  

     Jane központilag telepíti az alkalmazást a Windows Embedded-eszközök gyűjteményére.  

     További információkért lásd: [Alkalmazások központi telepítése a System Center Configuration Managerrel](../../../apps/deploy-use/deploy-applications.md).  

9. Az Endpoint Protection definíciófrissítésének konfigurálásához Jane a szoftverfrissítéseket használja, és futtatja az Automatikus központi telepítési szabály létrehozása varázslót. Kiválasztja a **Definíciófrissítések** sablont a varázsló előfeltöltésére az Endpoint Protection alkalmazásnak megfelelő beállításokkal.  

     Ezek a beállítások a következőket tartalmazzák a varázsló **Felhasználói élmény** oldalán:  

    -   **Viselkedés a határidőhöz**: A **Szoftvertelepítés** jelölőnégyzet nincs bejelölve.  

    -   **Írási szűrő kezelése a Windows Embedded-eszközök**: A **változtatások véglegesítése a határidő lejártakor vagy karbantartási időszakban (újraindítást igényel)** jelölőnégyzet nincs bejelölve.  

     Jane megtartja ezeket az alapértelmezés szerinti beállításokat. Ez a két beállítás ezzel a konfigurációval együtt lehetővé teszi az Endpoint Protection bármely szoftverfrissítési leírásának telepítését az átmeneti területre a nap folyamán, és a telepítéshez és véglegesítéshez nem kell megvárni a karbantartási időszakot. Ez a konfiguráció felel meg a legjobban a számítógépek vállalati biztonsági házirendjének a naprakész kártevőirtó-védelem futtatásával.  

    > [!NOTE]  
    >  Az alkalmazásokhoz tartozó szoftvertelepítésekkel ellentétben az Endpoint Protection szoftverfrissítési leírásai nagyon gyakran, akár naponta többször is változnak. Ezek gyakran kis fájlok. Az ilyen típusú biztonsággal kapcsolatos központi telepítéseknél gyakran hasznos lehet mindig az átmeneti területre telepíteni, és nem várakozni a karbantartási időszakra. A Configuration Manager-ügyfél gyorsan újratelepíti a szoftver definíciófrissítéseit, ha az eszköz újraindul, mert ez a művelet egy értékelési ellenőrzést igényel, és nem várja meg a következő ütemezett értékelést.  

     Jane kiválasztja a Windows Embedded-eszközök gyűjteményét az automatikus központi telepítési szabályhoz.  

     További információk a következő helyen találhatók:  
                  3. lépés: A Configuration Manager szoftverfrissítéseinek beállítása a definíciófrissítések ügyfélszámítógépekre a [az Endpoint Protection konfigurálása a System Center Configuration Managerben](../../../protect/deploy-use/configure-endpoint-protection.md)  

10. Jane úgy dönt, hogy beállít egy karbantartási feladatot, amely rendszeresen véglegesíti az összes változást az átmeneti területen. Ez a feladat a szoftverfrissítési leírások központi telepítését támogatja, hogy csökkenjen az összegyűlt frissítések száma, melyeket mindig újra kell telepíteni az eszköz újraindulása esetén. Tapasztalatai szerint ez segíti a kártevőirtó programok hatékonyabb működését.  

    > [!NOTE]  
    >  Ezek a szoftverfrissítési leírások automatikusan véglegesítődnének a lemezképbe, ha a beágyazott eszközök egy másik felügyeleti feladatot futtatnának a változások véglegesítésére. Például az interaktív bemutató szoftver új verziójának telepítése is véglegesítené a változásokat a szoftverfrissítési leírásokban. A havonta szokásos szoftverfrissítések telepítése a karbantartási időszak alatt is véglegesítené a változásokat a szoftverfrissítési leírásokban. Ebben a helyzetben azonban, amelyben nem futnak a szokásos szoftverfrissítések, és az interaktív bemutató szoftver sem frissül nagyon gyakran, a szoftver definíciófrissítései esetleg csak hónapok múlva rögzülnének automatikusan a lemezképbe.  

     Jane először létrehoz egy egyéni feladatütemezést, melyben nincs más beállítás, csak a neve. Utána futtatja a Feladatütemezés létrehozása varázslót:  

    1.  Az **Új feladatütemezés létrehozása** lapon kiválasztja az **Új egyéni feladatütemezés létrehozása**elemet, majd rákattint a **Tovább**gombra.  

    2.  A **Feladatütemezés adatai** lapon a feladatütemezés nevének beírja a **Maintenance task to commit changes on embedded devices** szöveget, majd rákattint a **Tovább**gombra.  

    3.  Az **Összegzés** lapon a **Tovább**gombot választva befejezi a varázsló használatát.  

     Jane ezután központilag telepíti ezt az egyéni feladatütemezést a Windows Embedded-eszközök gyűjteményére, majd konfigurálja az ütemezést, hogy minden hónapban lefusson. A központi telepítés beállításainak részeként bejelöli **A változtatások véglegesítése a határidő lejártakor vagy karbantartási időszakban (újraindítást igényel)** melletti jelölőnégyzetet, hogy a módosítások újraindítás után is megmaradjanak. Ennek a központi telepítésnek a konfigurálásához kiválasztja az éppen elkészített egyéni feladatütemezést, majd a **Kezdőlap** lapon a **Központi telepítés** csoportban rákattint a **Telepítás** elemre a Szofver központi telepítése varázsló elindításához:  

    1.  Az **Általános** lapon kiválasztja a Windows Embedded-eszközök gyűjteményét, majd rákattint a **Tovább**gombra.  

    2.  A **Központi telepítési beállítások** oldalon bejelöli a **Cél** elemnél a **Kötelező**értéket, majd rákattint a **Tovább**gombra.  

    3.  Az **Ütemezés** oldalon rákattint az **Új** lehetőségre egy heti ütemezés megadásához a karbantartási időszakban, majd rákattint a **Tovább**gombra.  

    4.  További módosítások nélkül befejezi a varázslót.  

     További információk a következő helyen találhatók:  
                  [A System Center Configuration Managerben feladatok automatizálásához a feladatütemezések kezeléséhez](../../../osd/deploy-use/manage-task-sequences-to-automate-tasks.md).  

11. A számítógépek automatikus futtatásához Jane ír egy parancsfájlt az eszközöknek a következő beállításokkal való konfigurálásához:  

    -   Automatikus bejelentkezés a vendég fiók használatával, melyhez nem tartozik jelszó.  

    -   Telepítéskor automatikusan futtassa az interaktív bemutató szoftvert.  

     Jane csomagok és programok segítségével végzi ennek a parancsfájlnak a központi telepítését a Windows Embedded-eszközök gyűjteményébe. A Szoftver központi telepítése varázsló futtatásakor ismét bejelöli **A változtatások véglegesítése a határidő lejártakor vagy karbantartási időszakban (újraindítást igényel)** melletti jelölőnégyzetet, hogy a módosítások újraindítás után is megmaradjanak.  

     További információ: [Csomagok és programok a System Center Configuration Managerben](../../../apps/deploy-use/packages-and-programs.md).  

12. Másnap reggel Jane ellenőrzi a Windows Embedded-eszközöket. Meggyőződik a következőkről:  

    -   A számítógép automatikusan bejelentkezett a vendég fiók használatával.  

    -   Az interaktív bemutató szoftver elindult.  

    -   Az Endpoint Protection-ügyfél telepítve van, és a legfrissebb szoftverfrissítési leírásokkal rendelkezik.  

    -   Hogy az eszköz újraindult a karbantartási időszakban.  

     További információkért lásd:  

    -   [A System Center Configuration Managerben az Endpoint Protection figyelése](../../../protect/deploy-use/monitor-endpoint-protection.md)  

    -   [Alkalmazások figyelése a System Center Configuration Managerrel](/sccm/apps/deploy-use/monitor-applications-from-the-console)  

13. Jane ellenőrzi a számítógépeket, és beszámol a sikeres feladatvégzésről a felettesének. Így 20 számítógépet rendelnek a látogatói központba.  

     A Configuration Manager-ügyfél, amelyhez letiltása, majd engedélyezi az írási szűrőket, kézi telepítésének elkerülése érdekében Jane gondoskodik róla, hogy a rendelés tartalmaz egy testre szabott lemezképet, amely már tartalmazza a Configuration Manager-ügyfél telepítését és helyhozzárendelését. Az eszközök emellett a vállalati névadási formának megfelelő neveket kapnak.  

     A számítógépeket egy héttel a megnyitása előtt szállítják ki a látogatói központba. Ezen idő alatt a számítógépek hálózathoz csatlakoznak, minden eszközfelügyelet automatikusan történik, és nincs szükség helyi rendszergazdára. Jane meggyőződik róla, hogy a számítógépek a várt módon működnek:  

    -   A számítógépeken lévő ügyfélszoftverek elvégezték a helyhozzárendelést, és letöltötték a megbízható legfelső szintű kulcsot az Active Directory tartományi szolgáltatásokból.  

    -   A számítógépeken lévő ügyfélszoftverek automatikusan hozzáadódtak a Windows Embedded-eszközök gyűjteményéhez, és a beállításuk is megtörtént a karbantartási időszakban.  

    -   Az Endpoint Protection-ügyfél telepítve van, és rendelkezik a kártevőirtó védelemhez tartozó legfrissebb szoftverfrissítési leírásokkal.  

    -   Az interaktív bemutató szoftver telepítve van és automatikusan elindul, és készen áll a felhasználásra.  

14. Az itt bemutatott kezdeti beállítás után minden, a frissítéshez szükséges újraindításra kizárólag a látogatói központ bezárása után kerül sor.  

