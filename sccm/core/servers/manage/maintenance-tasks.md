---
title: "Karbantartási feladatok |} Microsoft Docs"
description: "Ismerje meg, milyen karbantartási feladatok elvégzésére a Configuration Manager-helyek és hierarchiák, és mikor kell azokat elvégezni őket."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 625bb787-6d16-47a0-8b0f-b129cd909ca3
caps.latest.revision: 7
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3b56e84cbe9785e280fb02ede6644a8ed2769586
ms.openlocfilehash: 90b6e4434abc5573a364c769bd835e08e5dff16d
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="maintenance-tasks-for-system-center-configuration-manager"></a>A System Center Configuration Manager karbantartási feladatai

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager-helyek és -hierarchiákat kell rendszeres tartani és figyelni kell a hatékony és folyamatos működés érdekében. Rendszeres karbantartásnak, hogy a hardverek, szoftverek és a Configuration Manager-adatbázis továbbra is megfelelően és hatékonyan működik. Optimális teljesítmény nagymértékben csökkenti a meghibásodás kockázatát.  

 Riasztások beállítása és az Állapotrendszer használatával figyelheti az állapotát a Configuration Manager [riasztások és az állapotrendszer használata a System Center Configuration Manager](../../../core/servers/manage/use-alerts-and-the-status-system.md).  

-   [Karbantartási feladatok](#bkmk_MTs)  

##  <a name="bkmk_MTs"></a>Karbantartási feladatok  
 Rendszeres karbantartása fontos, hogy a helyes működése érdekében. Karbantartási naplózhatja karbantartás feljegyezheti, karbantartási és a feladatokkal kapcsolatos karbantartási kapcsolatos megjegyzések hagyva.  

### <a name="when-to-do-common-maintenance-tasks"></a>Ha általános karbantartási feladatok  
 A hely karbantartása, fontolja meg karbantartási napi vagy heti. Egyes feladatok különböző ütemezése lehet szükség. Gyakori karbantartás többek között beépített karbantartási feladatokból és a más feladatokat, például fiókkarbantartásból állhat fenntartani a vállalati szabályzatoknak való megfelelőségét.  

 A következő adatokat használja útmutatóként különböző karbantartási feladatokat hajthatnak végre, hogy mikor tervezéséhez nyújtanak segítséget. Használja ezt a listát kiindulási pontként, és adja hozzá az alkalmazáshoz szükséges feladatok.  

**Napi feladatok**   
Az alábbiakban karbantartási feladatokat, amelyeket érdemes figyelembe venni a napi ütemezés szerint:  

-   Ellenőrizze, hogy naponta ütemezett található előre megadott karbantartási feladatok futnak-e.  

-   Ellenőrizze a Configuration Manager-adatbázis állapotát.  

-   Ellenőrizze a helyrendszer állapotát.  

-   Ellenőrizze a Configuration Manager hely rendszer Beérkezett fájlok számát.  

-   Ellenőrizze a helyrendszerek állapotát.  

-   Ellenőrizze a helyrendszereken az operációs rendszerek eseménynaplóit.  

-   Ellenőrizze az SQL Server hibanaplóját a Helyadatbázis számítógépén.  

-   Ellenőrizze a rendszerteljesítményt.  

-   Ellenőrizze a Configuration Manager riasztásokat.  

**Heti feladatok**   
Karbantartási feladatokat, amelyeket érdemes figyelembe venni heti ütemezésnél a következők:  

-   Ellenőrizze, hogy hetente ütemezett található előre megadott karbantartási feladatok futnak-e.  

-   Törölje a szükségtelenné vált fájlokat a helyrendszerekről.  

-   Készítsen és terjesszen végfelhasználói jelentéseket, ha szükséges.  

-   Készítsen biztonsági másolatot az alkalmazás, a biztonsági és a rendszer eseménynaplóit, és törölje őket.  

-   Ellenőrizze a Helyadatbázis méretét, és ellenőrizze, hogy nincs elég szabad lemezterület a Helyadatbázis-kiszolgálón úgy, hogy az adatbázis növekedéséhez.  

-   Hajtsa végre az SQL Server-adatbázis karbantartást a helyadatbázison az SQL Server karbantartási tervnek megfelelően.  

-   Ellenőrizze az elérhető lemezterületet minden helyrendszeren.  

-   Futtassa a Lemeztöredezettség-mentesítő eszközöket minden helyrendszeren.  

**Rendszeres feladatok**   
Egyes, amelyekhez nem szükséges napi vagy heti karbantartási feladatok számára fontos általános állapota. Ezeket a feladatokat is győződjön meg arról, hogy a biztonsági, valamint a vész-helyreállítási tervek naprakészek legyenek. Karbantartási feladatokat, mint a napi vagy heti feladat bizonyos időközönként érdemes a következők:  

-   Változás-fiókkal és jelszóval, ha szükséges, a biztonsági tervnek megfelelően.  

-   Tekintse át a karbantartási terv, ellenőrizze, hogy ütemezett karbantartási feladatok ütemezése megfelelő és hatékony konfigurált beállításoktól függ.  

-   Tekintse át a Configuration Manager-hierarchia kialakítását a szükséges módosításokat.  

-   Ellenőrizze a hálózat teljesítményében győződjön meg arról, hogy nem történt módosítás, amelyek befolyásolják a hely működését.  

-   Ellenőrizze, hogy a hely működését befolyásoló Active Directory-beállítások nem változtak. Ellenőrizze például, hogy az Active Directory-helyekhez hozzárendelt, és a Configuration Manager-helyhez határként használt alhálózat nem lettek módosítva.  

-   Tekintse át a vész-helyreállítási terv végre a szükséges módosításokat.  

-   Hajtsa végre egy helyhelyreállítást a vész-helyreállítási terv teszt laboratóriumi biztonsági másolatot készíteni a helykiszolgáló biztonsági mentése karbantartási feladat által létrehozott legfrissebb biztonsági másolat használatával.

-   Ellenőrizze a hardver hibákat vagy e elérhető hardverfrissítések.  

-   Ellenőrizze a hely általános állapotát.  

###  <a name="BKMK_UseMTs"></a>A Helyadatbázis működési állapotának karbantartása  
 Amely ütemezett, és állítsa be a feladatokat hajthatnak végre, a Configuration Manager-hely és a hierarchia, amíg a helyösszetevők folyamatosan adatok hozzáadása a Configuration Manager adatbázisába. Az adatmennyiség növekedésével elutasítása adatbázis teljesítménye és szabad tárhelye az adatbázisban. Helykarbantartási feladatok állíthat be, amely már nem szükséges azokat az elavult adatokat távolítja el.  

 A Configuration Manager rendszerben is használhatja a Configuration Manager-adatbázis karbantartásában előre megadott karbantartási feladatok. Nem minden karbantartási feladatok alapértelmezés szerint minden helyen érhetők el. Több feladatot engedélyezve vannak, amíg nem, de mindegyiken ütemezés szerint állíthatja be.  

 Legtöbb karbantartási feladat bizonyos időközönként eltávolítja az elavult adatokat a Configuration Manager-adatbázisból. Az adatbázis méretének csökkentése a szükségtelen adatok eltávolításával javítja az teljesítményét és integritását, az adatbázis, amely növeli a hatékonyságot, a hely és hierarchia. Egyéb feladatok, például **indexek újraépítése**, segít fenntartani az adatbázis hatékony működését. Egyéb feladatok, például a **helykiszolgáló biztonsági mentése** hiba esetén segít előkészíteni az adatok helyreállítását.  

> [!IMPORTANT]  
>  Ha adatok törlésére szolgáló feladat ütemezését tervezi, vegye figyelembe az adatok használatát a hierarchiát. Ha adatok törlésére szolgáló feladat futtat egy adott helyen, a Configuration Manager-adatbázis eltávolítja a az adatokat, és ez a változás a hierarchia összes helyére replikálja. Ez a törlés hatással lehet más feladatok, amelyek a szóban forgó adatokat használják. Például a központi adminisztrációs helyen beállíthat felderítési nem ügyfélszámítógépek azonosítása érdekében havonta egyszer futtatásához. Szeretné telepíteni a Configuration Manager-ügyfelet ezekre a számítógépekre, a két héten belül. Azonban a hierarchia egyik helyén, hogy egy rendszergazda állítja be a elavult eszközfelderítési adatok törlése feladat hétnaponta lefusson. Az eredménye, hogy hét nappal később nem ügyfélszámítógépeket, akkor azok törlődnek az a Configuration Manager adatbázisába. Vissza a központi adminisztrációs helyen előkészíti a leküldéses telepítése a Configuration Manager-ügyfelet ezekre a számítógépekre új 10 napon. Mivel azonban az elavult eszközfelderítési adatok törlése feladat mostanában lefutott, és a törölt adatokat, amelyek hétnapos vagy annál régebbi, a mostanában felderített számítógépek már nem érhetők el az adatbázisban.  

Miután telepítette a Configuration Manager-hely, tekintse át az elérhető karbantartási feladatokat, és engedélyezze azokat, amelyek a rendszer működéséhez szükségesek. Tekintse át a minden feladat alapértelmezés szerinti ütemezését, és ha szükséges, az ütemezés beállítása a karbantartási feladatok jobban megfeleljenek az adott hierarchiának és környezetnek finomhangolását. Bár a legtöbb környezetben kell felelnek meg az alapértelmezett ütemezés minden feladat, a webhelyek és az adatbázis teljesítményének figyeléséhez, és feladatokat a központi telepítés hatékonyság növelése finomhangolhatja várt. Tervezze meg rendszeresen tekintse át a hely és az adatbázis teljesítményét, és konfigurálja újra a karbantartási feladatokat és azok ütemezését a rendszer hatékony működésének fenntartása érdekében.  

#### <a name="set-up-maintenance-tasks"></a>Karbantartási feladatok beállítása  
 Minden egyes Configuration Manager-hely támogatja a karbantartási feladatokat, amelyek segítenek a Helyadatbázis működési hatékonyság fenntartásához. Alapértelmezés szerint több karbantartási feladat minden helyen engedélyezve vannak, és mindegyik feladat támogatja a független ütemezéseket. Karbantartási feladatok be vannak állítva külön-külön az egyes helyeknél és, hogy a hely adatbázisára vonatkoznak. Azonban bizonyos feladatokat, például **elavult eszközfelderítési adatok törlése**, hatással vannak a hierarchiában található összes helyen rendelkezésre álló információkat.  

 Csak a karbantartási feladatokat, beállíthat egy helyen jelennek meg a Configuration Manager konzolon. Karbantartási feladatok helytípus szerinti teljes listáját lásd: [hivatkozás tartozó karbantartási feladatokat a System Center Configuration Manager](../../../core/servers/manage/reference-for-maintenance-tasks.md).  

 Az alábbi eljárás segítségével állítsa be a karbantartási feladatok általános beállításait.  

###### <a name="to-set-up-maintenance-tasks-for-configuration-manager"></a>A Configuration Manager karbantartási feladatainak beállítása  

1.  Nyissa meg a Configuration Manager konzol **felügyeleti** > **Helykonfiguráció** >**helyek**.  

2.  Válassza ki a helyet, amelynek a beállítani kívánt karbantartási feladatot.  

3.  Az a **Home** lap a **beállítások** csoportjában válassza **Helykarbantartás**, és válassza ki a beállítani kívánt karbantartási feladatot.  

    > [!TIP]  
    >  Csak a kiválasztott helyen rendelkezésre álló feladatok jelennek meg.  

4.  A feladat beállításához válasszon **szerkesztése**, ellenőrizze a **feladat engedélyezése** jelölőnégyzet be van jelölve, és állítsa be annak ütemezését, hogy a feladat futtatásakor. Ha a feladat törli az elavult adatokat is, állítsa be a feladat futtatásakor az adatbázisból törlendő adatok korát. Válasszon **OK** kattintva zárja be a feladat **tulajdonságok**.  

    > [!NOTE]  
    >  A **elavult állapotüzenetek törlése**, Állapotszűrő szabályok beállítása során a törlendő adatok korát beállítása.  

5.  Engedélyezheti vagy letilthatja a feladatot anélkül, hogy a feladat tulajdonságainak szerkesztésével, válassza ki a **engedélyezése** vagy **letiltása** gombra. A gomb címkéje a feladat aktuális konfigurációjától függően változik.  

6.  Ha elkészült, a karbantartási feladatok konfigurálását, válassza ki a **OK** az eljárás befejezéséhez.

