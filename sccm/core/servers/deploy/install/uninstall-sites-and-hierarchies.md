---
title: "Távolítsa el a helyek |} Microsoft Docs"
description: "Útmutatóként ezen adatok segítségével távolítsa el a System Center Configuration Manager-hely."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d466edd2-97f0-44c1-a73e-d71abbdbf4a8
caps.latest.revision: 6
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: b4c4fc305adbb4acd5bb4941b856a6a4aa648d0f
ms.openlocfilehash: 6ad06753dc0e1d0958f7131afbf3ecb75eecb2e3
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="uninstall-sites-and-hierarchies-in-system-center-configuration-manager"></a>Helyek és hierarchiák eltávolítása a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A következő adatokat használja útmutatóként, ha el kell távolítania a System Center Configuration Manager-hely.  

A több helyet tartalmazó hierarchia leszerelésekor eltávolításának sorrendje fontos. A hierarchia alján található helyeket távolítsa el, és majd haladjon felfelé:  

1.  Az elsődleges helyekhez csatolt másodlagos helyeket távolítsa el.  
2.  Távolítsa el az elsődleges helyeken.
3.  Az összes elsődleges hely eltávolítása után eltávolíthatja a központi adminisztrációs helyet.  


##  <a name="BKMK_RemoveSecondarysite"></a> Másodlagos hely eltávolítása egy hierarchiából  
Nem helyezhet egy másodlagos helyre vagy ismételt hozzárendelése egy új szülő elsődleges hely másodlagos helyet. Eltávolítsa őket a hierarchiában, a másodlagos helyek törölni kell a közvetlen szülőhelyéről. A másodlagos hely törlése varázslóját a Configuration Manager konzol segítségével másodlagos hely eltávolításához. A másodlagos hely eltávolításakor választania kell, hogy törölje azt, vagy távolítsa el azt:  

-   **A másodlagos hely eltávolítása**. Ez a beállítás segítségével távolítsa el a hálózaton elérhető-e működő másodlagos helyet. Ez a beállítás eltávolítja a Configuration Manager a másodlagos helykiszolgálóról, és majd törli az összes információt a helyet és erőforrást a Configuration Manager-hely hierarchiában való. A Configuration Manager telepített SQL Server Expresst a másodlagos hely telepítésének részeként, ha a Configuration Manager fogja eltávolítani az SQL Expresst a másodlagos hely eltávolításakor. Ha az SQL Server Express telepítve volt, a másodlagos hely telepítése előtt, a Configuration Manager művelet nem távolítja el az SQL Server Express.  

-   **A másodlagos hely törlése**. Használja ezt a beállítást, ha az alábbiak egyike igaz:  

    -   A másodlagos hely telepítése nem sikerült  
    -   A másodlagos hely továbbra is megjelenik a Configuration Manager konzol eltávolítását követően

    Ez a beállítás törli az összes információt a helyet és erőforrást a Configuration Manager hierarchiából, de hagyja a másodlagos helykiszolgálón telepített Configuration Manager.  

    > [!NOTE]  
    >  Is használhatja a hierarchia-karbantartó eszközt és a **/delsite** másodlagos hely törléséhez a beállítást. Részletesebb információkért lásd: [A System Center Configuration Managerhez készült hierarchia-karbantartási eszköz (Preinst.exe)](../../../../core/servers/manage/hierarchy-maintenance-tool-preinst.exe.md).  

#### <a name="to-uninstall-or-delete-a-secondary-site"></a>Másodlagos hely eltávolítása vagy törlése  

1.  Ellenőrizze, hogy a telepítőt futtató rendszergazda felhasználó rendelkezik-e az alábbi biztonsági jogosultságokkal:  

    -   Rendszergazdai jogosultságok a másodlagos hely számítógépén  
    -   Helyi rendszergazdai jogosultságok a távoli Helyadatbázis-kiszolgáló az elsődleges helyhez, ha távoli  
    -   Infrastruktúra-rendszergazda vagy teljes körű rendszergazda biztonsági szerepkör az elsődleges szülőhelyen  
    -   Rendszergazdai jogosultságok a másodlagos hely helyadatbázisán  

2.  A Configuration Manager konzolon válassza **felügyeleti**.  
3.  Az a **felügyeleti** munkaterületet, bontsa ki a **Helykonfiguráció**, majd válassza ki **helyek**.  
4.  Válassza ki, hogy el szeretné távolítani a másodlagos hely kiszolgálóján.  
5.  Az a **Home** lap a **hely** csoportban válassza **törlése**.  
6.  Az **Általános** lapon válassza ki, hogy eltávolítani vagy törölni szeretné a másodlagos helyet, majd kattintson a **Tovább**gombra.  
7.  Az a **összegzés** lapon ellenőrizze a beállításokat, és válassza ki **következő**.  
8.  Az a **befejezési** lapon jelölje be **Bezárás** a varázslóból való kilépéshez.  

##  <a name="BKMK_UninstallPrimary"></a> Elsődleges hely eltávolítása  
A Configuration Manager telepítő társított másodlagos hellyel nem rendelkező elsődleges hely eltávolításához futtathatja. Elsődleges hely eltávolítása előtt a következőkre kell figyelnie:  

-   Ha a Configuration Manager-ügyfelek a helyen konfigurált határokon belül találhatók, és az elsődleges hely a Configuration Manager-hierarchia részét képezi, fontolja meg, a határokat egy másik elsődleges helyhez a hierarchiában az elsődleges hely eltávolítása előtt.  
-   Ha az elsődleges helykiszolgáló már nem áll rendelkezésre, a helykiszolgáló helyadatbázisból való törléséhez a hierarchia-karbantartó eszközt kell használnia a központi adminisztrációs helyen. Részletesebb információkért lásd: [A System Center Configuration Managerhez készült hierarchia-karbantartási eszköz (Preinst.exe)](../../../../core/servers/manage/hierarchy-maintenance-tool-preinst.exe.md).  

Egy elsődleges helyet az alábbi eljárás segítségével távolíthat el.  

#### <a name="to-uninstall-a-primary-site"></a>Elsődleges hely eltávolítása  

1.  Ellenőrizze, hogy a telepítőt futtató rendszergazda felhasználó rendelkezik-e az alábbi biztonsági jogosultságokkal:  

    -   Helyi rendszergazdai jogosultságok a központi felügyeleti hely kiszolgálóján  
    -   Helyi rendszergazdai jogosultságok a központi adminisztrációs hely, ha távoli a távoli Helyadatbázis-kiszolgáló
    -   Rendszergazdai jogosultságok a helyadatbázist a központi adminisztrációs hely  
    -   Helyi rendszergazdai jogosultságok az elsődleges hely számítógépén  
    -   Helyi rendszergazdai jogosultságok a távoli Helyadatbázis-kiszolgáló az elsődleges helyhez, ha távoli  
    -   A központi adminisztrációs hely infrastruktúra-rendszergazda vagy teljes körű rendszergazda biztonsági szerepkörrel társított felhasználó nevét  

2.  Indítsa el az elsődleges helykiszolgálón a Configuration Manager telepítő az alábbi módszerek egyikének használatával:  

    -   A **Start**, jelölje be **a Configuration Manager telepítő**.  
    -   Nyissa meg a Setup.exe fájlt &lt; *Configmgrtelepítésiadathordozó*> \SMSSETUP\BIN\X64.  
    -   Nyissa meg a Setup.exe fájlt &lt; *Configmgrtelepítésiútvonal*> \BIN\X64.  

3.  Az a **előkészületek** lapon jelölje be **következő**.  
4.  A a **bevezetés** lapon jelölje be **Configuration Manager-hely eltávolítása**, majd válassza ki **következő**.  
5.  Az a **a Configuration Manager-hely eltávolítása**, adja meg, hogy-e távolítani a helyadatbázist az elsődleges helykiszolgálón, és hogy a Configuration Manager konzol eltávolítja-e. Alapértelmezés szerint a telepítő mindkettőt eltávolítja.  

    > [!IMPORTANT]  
    >  Abban az esetben, ha az elsődleges helyhez másodlagos helyet is társítottak, először a másodlagos helyet kell eltávolítania, mielőtt az elsődleges helyet eltávolíthatná.  

6.  Válassza ki **Igen** a Configuration Manager elsődleges helye eltávolításának megerősítését.  

##  <a name="BKMK_UninstallPrimaryDistViews"></a> Elosztott nézetekkel konfigurált elsődleges hely eltávolítása  
 El szeretné távolítani a gyermek elsődleges helyek rendelkezik elosztott nézetek, a központi adminisztrációs helyre mutató replikációs hivatkozásán engedélyezve van, ki kell kapcsolnia az elosztott nézeteket a hierarchiában. Az alábbi információk segítségével kikapcsolása elosztott nézeteket egy elsődleges hely eltávolítása előtt.  

#### <a name="to-uninstall-a-primary-site-that-is-configured-with-distributed-views"></a>Elosztott nézetekkel konfigurált elsődleges hely eltávolítása  

1.  El szeretné távolítani valamelyik elsődleges helyet, ki kell kapcsolnia az elosztott nézeteket a hierarchiában, a központi adminisztrációs helyen és az elsődleges hely közötti hivatkozásokon.  
2.  Összes hivatkozáson lévő elosztott nézetek letiltása után győződjön meg arról, hogy az elsődleges helyről származó adatok befejezze a újrainicializálását a központi adminisztrációs helyen. A Configuration Manager konzol, az adatok inicializálása a figyelheti a **figyelés** munkaterületen megtekinti a hivatkozást a a **adatbázis-replikáció** csomópont.  
3.  Miután az adatok újrainicializálása sikeresen megtörtént a központi adminisztrációs helyen, eltávolíthatja az elsődleges helyet. Az elsődleges hely eltávolításáról [elsődleges hely eltávolítása](#BKMK_UninstallPrimary).  
4.  Ha az elsődleges hely teljesen eltávolítva, újrakonfigurálhatja az elosztott nézeteket az elsődleges helyekre mutató hivatkozásokat tartalmaz.  

    > [!IMPORTANT]  
    >  Ha az elsődleges hely eltávolítása előtt kikapcsolják az elosztott nézeteket az egyes helyeken, vagy mielőtt az elsődleges helyről származó adatok újrainicializálása sikeresen megtörténne a központi adminisztrációs hely, elsődleges helyek és a központi adminisztrációs hely közötti replikáció sikertelen lehet. Ebben a forgatókönyvben ki kell kapcsolnia az elosztott nézeteket minden hivatkozásra a helyet tartalmazó hierarchiákban, és ezt követően követően az adatok újrainicializálása sikeresen megtörtént a központi adminisztrációs hellyel rendelkező, újrakonfigurálhatja az elosztott nézetek.  

##  <a name="BKMK_UninstallCAS"></a> A központi adminisztrációs hely eltávolítása  
 A Configuration Manager telepítő elsődleges gyermekhellyel nem rendelkező központi adminisztrációs hely eltávolításához futtathatja. Egy központi adminisztrációs helyet az alábbi eljárás segítségével távolíthat el.  

#### <a name="to-uninstall-a-central-administration-site"></a>Központi adminisztrációs hely eltávolítása  

1.  Ellenőrizze, hogy a telepítőt futtató rendszergazda rendelkezik-e az alábbi biztonsági jogosultságokkal:  

    -   Helyi rendszergazdai jogosultságok a központi felügyeleti hely kiszolgálóján  
    -   A Helyadatbázis-kiszolgáló a központi adminisztrációs hely, ha a Helyadatbázis-kiszolgáló nincs telepítve a helykiszolgálón helyi rendszergazdai jogosultságok 

2.  Az alábbi módszerek egyikének használatával indítsa el a Configuration Manager telepítőjét a központi felügyeleti hely kiszolgálóján:  

    -   Kattintson a **Start**gombra, majd a **Configuration Manager telepítő**elemre.  
    -   Nyissa meg a Setup.exe fájlt &lt; *Configmgrtelepítésiadathordozó*> \SMSSETUP\BIN\X64.  
    -   Nyissa meg a Setup.exe fájlt &lt; *Configmgrtelepítésiútvonal*> \BIN\X64.  

3.  Az a **előkészületek** lapon jelölje be **következő**.  
4.  A a **bevezetés** lapon jelölje be **Configuration Manager-hely eltávolítása**, majd válassza ki **következő**.  
5.  Az a **a Configuration Manager-hely eltávolítása**, adja meg, hogy-e távolítani a helyadatbázist a központi adminisztrációs hely kiszolgálójához való, valamint a Configuration Manager konzol eltávolítása. Alapértelmezés szerint a telepítő mindkettőt eltávolítja.  

    > [!IMPORTANT]  
    >  Abban az esetben, ha a központi adminisztrációs helyhez elsődleges helyet is társítottak, először az elsődleges helyet kell eltávolítania, mielőtt a központi adminisztrációs helyet eltávolíthatná.  

6.  Válassza ki **Igen** a Configuration Manager központi adminisztrációs hely az eltávolítás megerősítéséhez.  

