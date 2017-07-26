---
title: "A Technical Preview-ban 1608 Configuration Manager lehetőségeit"
description: "További tudnivalók a Technical Preview elérhető szolgáltatások a System Center Configuration Manager, 1608 verziója."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 63e1df5e-637c-4b07-b7ec-95340f43a805
caps.latest.revision: 15
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5d08d1f9ccd995d544c3c21c4af52ede73343077
ms.openlocfilehash: c22e29da8036d69db917205f28a19a69281a64db
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1608-for-system-center-configuration-manager"></a>A rendszer 1608 Technical Preview képességei Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (Technical Preview-ban)*

Ez a cikk ismerteti az új szolgáltatásokat a Technical Preview a System Center Configuration Manager, a verzió 1608 elérhető. A verzió frissítése, és új képességeket adhat a Configuration Manager technical preview-helyeken telepítheti.      A technical preview ezen verziója a telepítés előtt tekintse át a bevezető témakört, [a System Center Configuration Manager Technical Preview](../../core/get-started/technical-preview.md), megismerkedhet a általános követelményei és korlátozásai technikai előzetes kiadásról, hogyan használja, és hogyan visszajelzést a technical Preview verzióinak szolgáltatásai közötti frissítéséhez.    


**Új funkciókat próbálhatja ki ebben a következők:**  




##  <a name="improvements-to-the-prepare-configmgr-client-for-capture-task-sequence-step"></a>A „ConfigMgr-ügyfél előkészítése a rögzítéshez” feladatütemezési lépés fejlesztései  
A ConfigMgr-ügyfél előkészítése a lépést most is teljesen eltávolítja a Configuration Manager-ügyfél csak a fontos információk eltávolítása helyett. Ha a feladatütemezés a rögzített operációsrendszer-lemezképet telepíti azt telepíti egy új Configuration Manager-ügyfél minden alkalommal.  


## <a name="improvements-to-software-center"></a>A szoftverközpont fejlesztései
* A Szoftverközpont **alkalmazások**, **frissítések**, és **operációs rendszerek** lapokon most láthatók, milyen szoftvert valaki nemrég felvette. A navigációs ablaktábla számok megjelenítése hány új szoftverfrissítési van az egyes lapokon.
* Felhasználók mostantól az alkalmazások jóváhagyás-igénylést, és nézze meg, a kérelmek előzményei szakaszt a a **alkalmazás részletei** nézet a Szoftverközpontban. A **kérelem** gombra **alkalmazás részletei** már nem irányítja át a webes alkalmazás katalógus.

## <a name="improvements-to-asset-intelligence"></a>Az Eszközintelligencia fejlesztései
A tulajdonságok a leltározott szoftverek, amely lehetővé teszi egy mezőt állítsa egyéb szoftverek szülő és gyermek kapcsolat jelentek meg. A leltározott szoftverek listában nézze meg a szülő szoftverek és a is elrejtése az összes alárendelt szoftver.

### <a name="configure-a-parent-to-child-relationship"></a>A szülő-gyermek kapcsolat konfigurálása
  1. A leltározott szoftverek csomópontjában fölérendelt szoftverfrissítési beállításához kattintson a jobb gombbal szoftver elem a **leltározott szoftverek** listában, és válassza a **tulajdonságok**.
  2. A megnyíló párbeszédpanelen válassza ki a szoftver, amelyet szeretne állítja be a kezdeti beállítás szülő szoftver.

### <a name="filter-the-software-display"></a>A szoftver megjelenítésének szűrése
Szülő gyermek kapcsolatok meghatározása után szűrheti a nézetek csak a szoftver, amely a szülő vagy, amely nincs definiálva kapcsolat megjelenítése. Ez elrejti egy másik leltározott szoftverek gyermeke beállított összes szoftver. Ehhez:
   1.    Keresősáv, válassza ki a **feltétel hozzáadása**
   2. Válassza ki **fölérendelt szoftverfrissítési** és módosítsa a feltételek értéket **üres**, és kattintson a **keresési**.

A megjelenített most csak a szülő szoftverelemek vagy szoftver, amelynek nincs definiált kapcsolatokat jeleníti meg. Szoftverek, amelyek csak egy másik cím gyermeke nem jeleníti meg.

## <a name="remote-control-keyboard-translation"></a>A távvezérlés billentyűzet fordítás
Korábban a Configuration Manager továbbítani a fő pozíciója a megjelenítő helyről a megosztó helyre. A problémás volt az eltérő a megjelenítő megosztó a billentyűzet konfigurációkat. Például az angol billentyűzet használatával egy megjelenítőt írja be az "A", de a megosztó francia billentyűzet gondoskodik a "Q". Azt, hogy a karakter, maga a megjelenítő billentyűzetről átkerülnek a megosztó, és a megjelenítő százalékát írja be a megosztó megérkezik módosítja az alapértelmezett viselkedés.

Ez a viselkedés is ki kell kapcsolni a megjelenítő Ha inkább írja be a megosztó billentyűzet elrendezés szerint. Változtathatja, a **Configuration Manager Távvezérlés**, válassza ki **művelet**, válassza **billentyűzet fordítási engedélyezése** kulcs pozíció átviteléhez.

> [!NOTE]
>
> Különleges kulcsok, például a ~! #@ $%, nem lesz megfelelően fordítva.

