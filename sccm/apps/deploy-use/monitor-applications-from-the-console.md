---
title: "A System Center Configuration Manager konzol alkalmazások figyelése |} Microsoft Docs"
description: "A szoftverekhez, beleértve a figyelés munkaterületen a Configuration Manager segítségével a frissítések, a megfelelőségi beállítások és alkalmazások telepítésének figyelése."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 784c295c-b8b8-4202-ab9f-665908d49d6d
caps.latest.revision: 5
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: fd7ea34b605d70f2ba9bd40384eb566ec3a87430
ms.openlocfilehash: 42d21d10489bffe32b875384f8801686239a0ba4
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="monitor-applications-from-the-system-center-configuration-manager-console"></a>Alkalmazások figyelése a System Center Configuration Manager konzolról

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


A System Center Configuration Managerben, figyelheti minden szoftver, beleértve a szoftverfrissítések, a megfelelőségi beállítások, alkalmazások, feladatütemezések, és a csomagok és programok központi telepítése. A központi telepítések figyelhetők a **figyelés** munkaterületen, a Configuration Manager konzolon és jelentések használatával.  

 A Configuration Manager támogatják a különböző alkalmazások állapot szerinti figyelést, amely lehetővé teszi, hogy a felhasználók és eszközök utolsó központi telepítési állapota követését. Ezek az állapotüzenetek adatokat jelenítenek meg az egyes eszközökről. Például ha egy alkalmazás egy felhasználógyűjtemény számára lett telepítve, megtekintheti a megfelelőségi állapotát a központi telepítés és a központi telepítés célja a Configuration Manager konzolon.  

## <a name="learn-about-compliance-states-in-system-center-configuration-manager"></a>További tudnivalók a System Center Configuration Manager megfelelőségi állapotai
 Egy alkalmazástelepítési állapotnak az egyik következő megfelelőségi állapota lehet:  

-   **Sikeres** – Az alkalmazás központi telepítése sikerült vagy már telepítve volt.  

-   **Folyamatban** – Az alkalmazás központi telepítése folyamatban van.  

-   **Ismeretlen** – Nem sikerült meghatározni az alkalmazás központi telepítésének állapotát. Ez az állapot nem tartozhat olyan telepítéshez, amelynek az oka **Elérhető**. Ez az állapot jellemzően akkor jelenik meg, ha az állapotüzenetek az ügyfélgéptől még nem érkeztek meg.  

-   **Nem teljesített követelmények** – Az alkalmazás nem lett telepítve, mert nem felelt meg valamelyik függőségnek vagy követelményi szabálynak, illetve az az operációs rendszer nem használható, amelyikre telepíteni kellett.  

-   **Hiba** – Az alkalmazás hiba miatt nem lett telepítve.  

A megfelelőségi állapot, beleértve a megfelelőségi állapot és a felhasználók és eszközök számát alkategóriáit ebbe a kategóriába tartozó további információk is megtekinthetők. Például a **Hiba** megfelelőségi állapot a következő alkategóriákkal rendelkezik:  

-   Hiba a követelmények kiértékelésekor  

-   Tartalom vonatkozású hibák  

-   Telepítési hibák  

 Ha egy alkalmazástelepítésre több megfelelőségi állapot vonatkozik, látható az az összegzett állapot, amelyik a legkisebb mértékű megfelelőséget jelzi. Példa:  

    -   Ha felhasználó jelentkezik be két eszköz és az alkalmazás sikeresen telepítve van egy eszközön, de nem tudja telepíteni a második eszköz, az adott felhasználó az alkalmazás összevont telepítési állapotát jeleníti meg, mint **hiba**.  

    -   Ha egy alkalmazás az összes felhasználóra, jelentkezzen be a számítógépre van telepítve, az adott számítógépre több telepítési eredményt kapja. Ha az egyik telepítés sikertelen, a számítógép összevont telepítési állapotát a **Hiba**jelzi.  

A csomag- és programtelepítések telepítési állapota nem vonható össze.  

 Az alkategóriák használata segíti az alkalmazás központi telepítése során a fontos problémák gyors felismerését. Azokról az eszközökről, amelyek a megfelelőségi állapot bizonyos alkategóriájába kerülnek, további tájékoztatás is látható.  

 Alkalmazások kezelése a Configuration Manager számos olyan beépített jelentéseket, amelyek lehetővé teszik az alkalmazások és a telepítésekre vonatkozó információk figyelését. Ezek a jelentések a **Szoftverterjesztés – Alkalmazásfigyelés**jelentési kategóriába tartoznak.  

 Jelentéskészítés a Configuration Managerben konfigurálásával kapcsolatos további információkért lásd: [a System Center Configuration Manager jelentéskészítési](../../core/servers/manage/reporting.md).  

## <a name="monitor-the-state-of-an-application-in-the-configuration-manager-console"></a>A Configuration Manager konzolon alkalmazás állapotának figyelése  

1.  Kattintson a Configuration Manager konzol **figyelés** > **központi telepítések**.  

3.  Részleteinek átnézéséhez, az egyes megfelelőségi állapotok és az eszközök ebben az állapotban, jelölje ki a telepítést, majd a a **Home** lap a **telepítési** csoportjában válassza **állapotának megtekintése** megnyitásához a **központi telepítési állapot** ablaktáblán. Ezen az ablaktáblán az eszközök a megfelelőségi állapotukkal együtt jelennek meg. Válassza ki a bármely eszközre kattintva részletesebb információkat a központi telepítési állapota az adott eszközre.  

    > [!NOTE]  
    >  A **Telepítés állapota** ablaktáblán legfeljebb 20 000 elem jelenhet meg. Ha szeretne további elemeket, a Configuration Manager-jelentések segítségével alkalmazás állapotadatainak megtekintéséhez.  
    >   
    >  A telepítési típusok állapota összevonva jelenik meg a **Telepítés állapota** ablaktáblán. A telepítési típusok részletesebb megtekintéséhez használja az **Az alkalmazás infrastruktúrájára vonatkozó hibák** jelentést a **Szoftverterjesztés – Alkalmazásfigyelés**jelentési kategóriában.  

4.  Egy alkalmazás telepítésére vonatkozó általános állapotadatok átnézéséhez, jelölje ki a telepítést, és válassza a **összegzés** lapra a **kiválasztott központi telepítés** ablak.  

5.  Az alkalmazás telepítési típusára vonatkozó adatok átnézéséhez, jelölje ki a telepítést, és válassza a **központi telepítési típusok** lapra a **kiválasztott központi telepítés** ablak.  

A megjelenő adatokat a **központi telepítési állapot** ablaktábla kiválasztása után **állapotának megtekintése** a Configuration Manager adatbázisából jövő adatokat jelzi. A megjelenő adatokat a **összegzés** lapon és a **központi telepítési típusok** lapon látható tájékoztatás összegzett adatokat.

Ha a megjelenített adatok a **összegzése** lapon és a **központi telepítési típusok** lapon látható adatok nem egyeznek a **központi telepítésének állapotát** ablaktáblán válassza ki **összefoglaló futtatása** hogy frissítse ezen lapok adatait. Az alkalmazástelepítések összegzési időköze a következőképpen konfigurálható:  

1. Kattintson a Configuration Manager konzol **felügyeleti** > **Helykonfiguráció** > **helyek**.

2. Az a **helyek** listára, válassza ki a helyet, amely az összegzési időközt konfigurálni szeretné, majd a a **Home** lap a **beállítások** csoportjában válassza **állapot-összefoglalók**.

3. Az a **állapot-összefoglalók** párbeszédpanelen válassza ki **alkalmazás-KözpontiTelepítés összegző**, és válassza a **szerkesztése**.  

4. Az a **alkalmazás-központi telepítés összegző tulajdonságai** párbeszédpanelen konfigurálja a kívánt összegzési időközt, és válassza a **OK**.  

