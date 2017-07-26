---
title: "Megfelelőségi beállítások figyelése |} Microsoft Docs"
description: "Segítségével egy vagy több eljárások ebben a témakörben az alapkonfiguráció megfelelőségi állapotát jeleníti meg."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 92c1ccca-a748-44cd-a52e-e41d34bf981d
caps.latest.revision: 6
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f9e939d871e95a3248d8e5d96cb73063a81fd5cf
ms.openlocfilehash: 75cd7e811262633d81d978265f21ec7ed3b61a58
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="monitor-compliance-settings-in-system-center-configuration-manager"></a>A System Center Configuration Manager megfelelőségi beállítások figyelése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Miután telepítette a System Center Configuration Manager referenciakonfigurációk eszközökre a hierarchiában, segítségével egy vagy több eljárások ebben a témakörben a referenciakonfiguráció megfelelőségi állapotának megjelenítése:

> [!NOTE]  
>  A megfelelőségi beállításokra vonatkozó jelentésekben az érvényesítési feltételek mezőiben (melyek megfelelője az ügyféloldali jelentésekben a **Korlátozások**elem) a mögöttes SML-kód jelenik meg. Ez megnehezíti a rendszergazdák, akik a konfigurációelem az érvényesítési feltételek rendszer a Configuration Manager konzolon hozták létre, ha azok nem rendelkeznek SML ismerete. Ebben az esetben használja a **figyelés** munkaterület a Configuration Manager konzolon a konfigurációs elem és a hozzá tartozó érvényesítési feltételek tulajdonságainak megtekintéséhez.  

##  <a name="view-compliance-results-in-the-configuration-manager-console"></a>Megfelelési eredmények megtekintése a Configuration Manager konzolon  
 Ezzel az eljárással a Configuration Manager konzolon a telepített alapkonfigurációk megfelelőségével kapcsolatos részletek megtekintéséhez.  

### <a name="view-compliance-results-in-the-configuration-manager-console"></a>Megfelelési eredmények megtekintése a Configuration Manager konzolon  

1.  Kattintson a Configuration Manager konzolon **figyelés** > **központi telepítések**.  

3.  Válassza ki a **Központi telepítések** listából az alapkonfigurációk azon központi telepítését, amelynek meg szeretné tekinteni a megfelelőségi információit.  

4.  Az alapkonfiguráció központi telepítésének megfelelőségével kapcsolatos összefoglaló információkat a főoldalon tudja ellenőrizni. Részletesebb adatok megtekintéséhez válassza ki az alapkonfigurációk központi telepítését, majd a **Kezdőlap** **Központi telepítés** csoportjában kattintson az **Állapot megtekintése** elemre a **Telepítés állapota** lap megnyitásához.  

     A **Telepítés állapota** lapon a következő fülek találhatók:  

    -   **Megfelelő**: Az érintett eszközök száma alapján alapkonfiguráció megfelelőségének megjelenítése. A megfelelő szabályra kattintva ideiglenes csomópontot hozhat létre az **Eszközök és megfelelőség** munkaterület **Felhasználók** vagy **Eszközök** csomópontja alatt, ahol megjelenik a szabálynak megfelelő összes felhasználó vagy eszköz. Az **Eszköz adatai** ablaktáblában jelennek meg az alapkonfigurációnak megfelelő felhasználók vagy eszközök. További információk megjelenítéséhez kattintson duplán a kívánt felhasználóra vagy az eszközre a listában.  

        > [!IMPORTANT]  
        >  Egy konfigurációs elem szabályt a rendszer nem értékeli ki, ha nem észlelhetők vagy nem alkalmazható az ügyféleszközre; azonban a szabály megfelelőként adja vissza.  

    -   **Hiba**: Megjeleníti a kijelölt alapkonfiguráció központi telepítését az érintett eszközök száma alapján kapcsolatos összes hiba. A megfelelő szabályra kattintva ideiglenes csomópontot hozhat létre az **Eszközök és megfelelőség** munkaterület **Felhasználók** vagy **Eszközök** csomópontja alatt, ahol megjelenik a szabállyal kapcsolatban hibát okozó összes felhasználó vagy eszköz. Amikor kijelöl egy felhasználót vagy eszközt, az **Eszköz adatai** ablaktáblán megjelennek azok a felhasználók vagy eszközök, akiket vagy amelyeket a kijelölt probléma érint. A problémával kapcsolatos további információk megjelenítéséhez kattintson duplán a kívánt felhasználóra vagy eszközre a listában.  

    -   **Nem megfelelő**: Az érintett eszközök száma alapján a referenciakonfigurációt nem megfelelő szabályok teljes listáját jeleníti meg. A megfelelő szabályra kattintva ideiglenes csomópontot hozhat létre az **Eszközök és megfelelőség** munkaterület **Felhasználók** vagy **Eszközök** csomópontja alatt, ahol megjelenik a szabálynak nem megfelelő összes felhasználó vagy eszköz. Amikor kijelöl egy felhasználót vagy eszközt, az **Eszköz adatai** ablaktáblán megjelennek azok a felhasználók vagy eszközök, akiket vagy amelyeket a kijelölt probléma érint. A problémával kapcsolatos további információk megjelenítéséhez kattintson duplán a kívánt felhasználóra vagy eszközre a listában.  

    -   **Ismeretlen**: Megjeleníti az összes felhasználó és eszköz nem jelentett megfelelőséget, a kijelölt alapkonfiguráció központi telepítés az aktuális ügyfélállapotával együtt az eszközök listáját.  

5.  A **Telepítés állapota** lapon tekinthetők meg a telepített alapkonfiguráció megfelelőségével kapcsolatos részletes információk. A **Központi telepítések** csomópont alatt létrejön egy ideiglenes csomópont, amellyel később gyorsan előkeresheti ezt az információt.  

##  <a name="view-compliance-results-by-using-reports"></a>Megfelelési eredmények megtekintése jelentések segítségével  
 A Configuration Manager megfelelőségi beállításainak számos olyan beépített jelentéseket, amelyek lehetővé teszik, hogy a konfigurációs elemek, a konfigurációs alapterv és a telepítésekre vonatkozó információk figyelését. Ezek a jelentések a **Megfelelőség és beállítások kezelése**jelentési kategóriába tartoznak.  

> [!IMPORTANT]  
>  Ha a megfelelőségi beállítások jelentéseiben az**%**Eszközszűrő **és a Felhasználószűrő paraméterek szerepelnek, helyettesítő karaktert (** ) kell használnia.  

 Jelentéskészítés a Configuration Manager konfigurálásával kapcsolatos további információkért lásd: [jelentéskészítés a System Center Configuration Managerben](../../core/servers/manage/reporting.md)  

##  <a name="view-compliance-results-on-a-configuration-manager-windows-client-computer"></a>Megfelelési eredmények megtekintése a Configuration Manager Windows rendszerű ügyfélszámítógépek

> [!NOTE]  
>  Információk nem megtekintése a Configuration Manager Windows-ügyfélen, ha egy tartományi Vendég fiókkal van bejelentkezve.    

1.  Az ügyfélszámítógép Vezérlőpultján lépjen a **Configuration Manager** elemre, majd a tulajdonságainak megnyitásához kattintson rá duplán.  

2.  Kattintson a **Konfigurációk** fülre, és tekintse meg a telepített alapkonfigurációk listáját.  

3.  Tekintse meg az egyes alapkonfigurációk **Megfelelőségi állapotát** :  

    > [!IMPORTANT]  
    >  Az ügyfél 15 percig gyorsítótárazza a kiértékelési eredményeket. Ha egy 15 perces időszakon belül újraértékelést kezdeményez, a rendszer új kiértékelés helyett ebből a gyorsítótárból adja vissza a megfelelőségi eredményeket. Így ha olyan módosítást hajt végre az ügyfélen, amely hatással lehet a megfelelőség értékelésének eredményére, az újraértékelés kezdeményezése előtt várja meg, amíg letelik a 15 perc.  

    -   **Megfelelő**: Az ügyfélszámítógép megfelel a kiértékelt alapkonfigurációnak van.  

    -   **Nem megfelelő**: Az ügyfélszámítógép a kiértékelt alapkonfigurációnak való megfelelés kívül esik.  

    -   **Ismeretlen**: Az ügyfélszámítógép még nem értékelte ki az alapkonfigurációt. Ha a megfelelőség értékelésének ütemezésén kívül szeretné elindítani a kiértékelést, válassza ki az értékelni kívánt alapkonfigurációkat, majd kattintson a **Kiértékelés**lehetőségre.  

        > [!NOTE]  
        >  Ha helyi rendszergazdai hitelesítő adatokkal rendelkezik az ügyfélszámítógépen, megtekintheti az egyes értékelt alapkonfigurációkra vonatkozó információkat annak meghatározásához, hogy mely konfigurációelem jelentett nem megfelelő állapotot. Ehhez jelölje ki az alapkonfigurációt, majd kattintson a **Jelentés megtekintése**lehetőségre.  

4.  Kattintson az **OK** gombra.  

##  <a name="create-collections-based-on-configuration-baseline-compliance"></a>Alapkonfiguráció megfelelősége alapuló gyűjtemények létrehozása  
 A következő eljárással hozhat létre a Configuration Manager gyűjteményt a meghatározott megfelelőségű eszközök alapján. A következő megfelelőségi állapotok alapján hozhat létre gyűjteményeket:  

-   **Megfelelő:**  

-   **Hiba:**  

-   **Non-compliant**  

-   **Ismeretlen**  

1.  Kattintson a Configuration Manager konzolon **eszközök és megfelelőség** > **megfelelőségi beállítások** > **Referenciakonfigurációk**.  

3.  Az **Alapkonfigurációk** listában jelölje ki az alapkonfigurációt, mely alapján gyűjteményt szeretne létrehozni.  

4.  A **Központi telepítés** lap **Telepítési csoport**szakaszában kattintson az **Új gyűjtemény létrehozása** lehetőségre, majd a legördülő listából válassza ki a megfelelőségi szintet, amely alapján létre szeretné hozni a gyűjteményt.  

5.  Ekkor a **Felhasználói gyűjtemény létrehozása varázsló** vagy az **Eszközgyűjtemény létrehozása varázsló** nyílik meg, attól függően, hogy a konfigurációelem felhasználók vagy eszközök számára van-e telepítve. A varázsló automatikusan ki van töltve a megfelelő értékekkel a gyűjtemény létrehozásához, de az értékeket szerkesztheti is.  

6.  A varázsló befejezése után a gyűjtemény megjelenik a **Felhasználógyűjtemények** vagy az **Eszközgyűjtemények** csomópontban az **Eszközök és megfelelőség** munkaterületen.  

