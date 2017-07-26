---
title: "A Technical Preview-ban 1704 Configuration Manager lehetőségeit"
description: "További tudnivalók a Technical Preview elérhető szolgáltatások a System Center Configuration Manager, 1704 verzió."
ms.custom: na
ms.date: 4/21/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e318e705-20f2-417d-8cde-7dfe661b2fa7
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: ae008c91a7387ba76f2bfac13f8feb489a0cc558
ms.openlocfilehash: d7caee47ca74064630e09c1bdb94187af256d4b4
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1704-for-system-center-configuration-manager"></a>A rendszer 1704 Technical Preview képességei Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (Technical Preview-ban)*

Ez a cikk ismerteti az új szolgáltatásokat, amelyek a Technical Preview a System Center Configuration Manager, 1704 verzió érhető el. A verzió frissítése, és új képességeket adhat a Configuration Manager technical preview-helyeken telepítheti. A technical preview ezen verziója a telepítés előtt tekintse át a bevezető témakört, [a System Center Configuration Manager Technical Preview](../../core/get-started/technical-preview.md), megismerkedhet a általános követelményei és korlátozásai technikai előzetes kiadásról, hogyan használja, és hogyan technical Preview funkciókkal kapcsolatos visszajelzés küldése közötti frissíteni.    


**Új funkciókat próbálhatja ki ebben a következők:**  

## <a name="configure-android-apps-with-app-configuration-policies"></a>Android-alkalmazások konfigurálása alkalmazás-konfigurációs házirendek
Segítségével a System Center Configuration Manager (a Configuration Manager) alkalmazás-konfigurációs házirendek terjesztése a beállításokat, amelyekre szükség lehet, amikor egy felhasználó egy alkalmazást futtat az Android munkahelyi eszközök. Android alkalmazás-konfigurációs szabályzatok csak munkahelyi az Android rendszerű eszközök elérhetők, és jóváhagyott alkalmazásokra vonatkozik a munkahelyi store a Play áruházból.

### <a name="try-it-out"></a>Próbálja ki                 

Kattintson a Configuration Manager konzol **szoftverkönyvtár** > **Alkalmazáskezelés** > **alkalmazáskonfigurációs szabályzatok** válassza **alkalmazáskonfigurációs szabályzat létrehozása**. Az a **általános** oldalon a varázsló, akkor most **válassza ki a konfigurációs házirend típusát**. A konfigurációs szabályzat által megcélzott platformot határoz meg: **Konfigurációs házirend az Androidos munkahelyi alkalmazások**. Megadhat majd **adja meg a név-érték párok** vagy **keresse meg a tulajdonságlista JSON-fájl**. Az új konfigurációs házirend látható a **szoftverkönyvtár** munkaterületen, a a **alkalmazáskonfigurációs szabályzatok** csomópont. Az alkalmazás-konfigurációs házirend társítása egy Android munkahelyi alkalmazás központi telepítését, az alkalmazás központi telepítése a szokásos módon az eljárás használatával a [telepíthet központilag alkalmazásokat](/sccm/apps/deploy-use/deploy-applications) témakör.

## <a name="hardware-inventory-collects-secure-boot-information"></a>A biztonságos rendszerindítás adatokat gyűjt a Hardverleltár
Hardverleltár most gyűjt adatokat a biztonságos rendszerindítás engedélyezve van-e az ügyfeleken. Ezeket az információkat tárolja a **SMS_Firmware** osztály (bevezetett, a verzió 1702), és engedélyezve van a hardveres szoftverleltár alapértelmezés szerint. Hardverleltár kapcsolatos további információkért lásd: [konfigurálása a Hardverleltár](/sccm/core/clients/manage/inventory/configure-hardware-inventory).

## <a name="add-child-task-sequences-to-a-task-sequence"></a>Feladatütemezések gyermek hozzáadása egy feladatütemezéshez
Ebben a verzióban adhat hozzá egy új feladatütemezési lépést, amely egy másik feladatütemezést, amely a feladatütemezések közötti szülő-gyermek kapcsolat létrehozása. Ez lehetővé teszi, hogy további moduláris feladatütemezések újra használhatja.  

Gyermek feladatütemezés ad hozzá egy feladatütemezés vegye figyelembe a következőket:

- A szülő és gyermek feladatütemezések hatékonyan van egyesítve, csupán egyetlen szabályzatot állít, az ügyfél futtatja.
- Egy alárendelt feladatütemezést, amely egy másik feladatütemezés szülő hozzáadása nem támogatott.
- A környezet nem globális. Például ha a változó a szülő feladatütemezés által beállított, és a gyermek feladatütemezés majd módosíthatja, a változó marad megváltozott áthelyezése előre. Hasonlóképpen a gyermek feladatütemezést hoz létre egy új változót, ha a változó érhető el a szülő feladatütemezés fennmaradó lépéseit.
- Egyetlen feladat feladatütemezési művelet állapotüzeneteket küldeni / normál.
- A feladatütemezések bejegyzést írni az smsts.log naplófájl helye, a napló új bejegyzéseit, amelyek egyértelműen, amikor egy gyermek feladatütemezés kezdődik.
- A Technical Preview a Configuration Manager, a verzió 1704, ha a gyermek feladatütemezések bármely csomagra hivatkozik, és futtatja a szülő feladatütemezés a Szoftverközpontból, az ügyfél nem találja a csomag tartalmát a gyermek feladatütemezés futtatásakor. Ebben a forgatókönyvben kell futtatnia a feladatütemezés media (rendszerindító adathordozó, PXE, stb.).  

    Ha a gyermek feladatütemezés hasonló lépéseket **parancssor futtatása** (minden csomag-hivatkozás nélkül), **formátum**, **BitLocker**stb, akkor a feladatütemezés a szoftverközpontból sikeresen fog futni.

### <a name="to-add-a-child-task-sequence-to-a-task-sequence"></a>Gyermek feladatütemezés hozzáadása egy feladatütemezéshez
1. Kattintson a feladatütemezés-szerkesztő, **Hozzáadás**, jelölje be **általános**, és kattintson a **feladatütemezés futtatása**.
2. Kattintson a **Tallózás** jelölje be a gyermek feladatütemezés.  

## <a name="reload-boot-images-with-current-windows-pe-version"></a>Töltse be újra a rendszerindító lemezképek Windows PE aktuális verziójával
Amikor futtatja **terjesztési pontok frissítése** a kijelölt rendszerindító lemezkép, most választhat töltse be újra a rendszerindító lemezkép Windows PE (a Windows ADK telepítési könyvtárból) legújabb verzióját. A **általános** a varázsló tájékoztatást ad azokról a Windows ADK-verzió van telepítve a helykiszolgálón, a Windows ADK-verzión, amelyből a rendszerindító lemezkép Windows PE lett megadva, és a Configuration Manager-ügyfél verziója. Ezek az információk segítségével határozza meg, hogy töltse be újra a rendszerindító lemezkép segítségével. Emellett egy olyan új oszlop (**ügyfélverzió**) rendszerindító lemezképeket megtekintésekor hozzá lett adva a **rendszerindító lemezképek** csomópont, hogy a Configuration Manager-ügyfél melyik verzióját minden rendszerindító lemezképet használja.

### <a name="to-reload-a-boot-image-with-the-current-windows-pe-version"></a>Töltse be újra az aktuális verzióval Windows PE rendszerindító lemezkép

1. Nyissa meg a Configuration Manager konzol **szoftverkönyvtár** > **operációs rendszerek** > **rendszerindító lemezképek**.
2. Válasszon rendszerindító lemezképet, és kattintson a **terjesztési pontok frissítése**.
3. Az a **általános** lapján jelöljön ki **Újrabetöltés rendszerindító lemezkép Windows PE a telepített Windows ADK a jelenlegi verziója**.

## <a name="improvements-to-operating-system-deployment"></a>Operációs rendszer központi telepítésének fejlesztései
A következő fejlesztéseket operációs rendszerek központi telepítése, amely a felhasználó hang visszajelzést eredményét hajtottunk.

- [Új **operációsrendszer-verzió** az operációs rendszeri lemezképek részére oszlop](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/17558407-add-a-column-to-the-operating-system-images-node-f): Jelentek meg egy olyan új oszlop neve **operációsrendszer-verzió** megjelenítéséhez a lemezkép operációs rendszerének verziója, az adatainak megtekintésekor az **operációsrendszer-lemezképek** és **operációs rendszer verziófrissítő csomagjai** csomópontok. Csak az első indexének verzióját a. WIM jelenik meg. Lépjen a **részletek** operációsrendszer-verziók a más indexek áttekintheti a lemezkép lapon.

- [Az Smsts.log hatékonyabb naplózás](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/16791919-stop-filling-smsts-log-with-useless): Ez verziójától kezdve folyamatban, már nem az smsts.log naplófájl helye CCM_CIVersionInfo.PolicyID információk írása bejegyzések. Korábbi verziói lehetnek nagy mennyiségű bejegyzések az információ, ami szigorú további információt a naplófájlban találja.

