---
title: "Médiarögzítésű adathordozó - létrehozása a Configuration Manager |} Microsoft Docs"
description: "A feladatütemezési média létrehozása varázsló segítségével médiarögzítésű adathordozó létrehozása a Configuration Managerben az operációs rendszer lemezképét a referencia-számítógépről rögzíteni."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 10eb8958-3848-49d7-95c0-16119b624580
caps.latest.revision: 11
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 89158debdf4c345a325feeb608db2215a88ed81b
ms.openlocfilehash: 5acf800ff5aebd849e294393337755145a60cca5
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="create-capture-media-with-system-center-configuration-manager"></a>Médiarögzítésű adathordozó létrehozása a System Center Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Médiarögzítésű adathordozó a Configuration Manager lehetővé teszi az operációs rendszer lemezképét a referencia-számítógépről rögzíteni. A médiarögzítési funkció a következő helyzetben használható:  

-   [Hozzon létre egy feladatütemezést az operációs rendszer rögzítéséhez](create-a-task-sequence-to-capture-an-operating-system.md)  

##  <a name="BKMK_CreateCaptureMedia"></a> Médiarögzítésű adathordozó létrehozása  
 A médiarögzítésű adathordozó segítségével operációs rendszer lemezképét rögzítheti egy referencia-számítógépről. Ez az adathordozó tartalmazza a referencia-számítógép rendszerindító lemezképét és az operációs rendszer lemezképét rögzítő feladatütemezést.

Médiarögzítésű adathordozó a Feladatütemezési média létrehozása varázslóval hozható létre. A varázsló futtatása előtt ellenőrizze, hogy teljesült-e az összes következő feltétel:  

|Feladat|Leírás|  
|----------|-----------------|  
|Rendszerindító lemezkép|Az operációs rendszer központi telepítésére szolgáló feladatütemezésben használt rendszerindító lemezképpel kapcsolatban fontolja meg az alábbiakat:<br /><br /> -A rendszerindító lemezkép architektúrájának meg kell felelnie a célszámítógép architektúrájának. Az x64 rendszerű célszámítógépek például elindíthatók és működtethetők x86 vagy x64 rendszerindító lemezképpel is. Az x86 rendszerű célszámítógépek elindításához és működtetéséhez azonban csak x86 rendszerindító lemezkép használható.<br />-Győződjön meg arról, hogy a rendszerindító lemezkép tartalmazza a hálózati és háttértár tároló-illesztőprogramoktól, amelyek a célszámítógép kiépítéséhez szükségesek.|  
|A feladatütemezéshez társított összes tartalom terjesztése|A feladatütemezéshez szükséges összes tartalmat helyezze el legalább egy terjesztési ponton. Ide tartozik a rendszerindító lemezkép, az operációs rendszer lemezképe és az egyéb kapcsolódó fájlok. A varázsló a terjesztési pontról gyűjti az adatokat, amikor létrehozza a különálló adathordozót. A terjesztési ponton található tartalomtárhoz **Olvasási** hozzáférési jogosultsággal kell rendelkeznie.  További információkért lásd: [tartalomterjesztés](../../core/servers/deploy/configure/deploy-and-manage-content.md#bkmk_distribute).|  
|A cserélhető USB-meghajtó előkészítése|Cserélhető USB-meghajtó esetén:<br /><br /> Cserélhető USB-meghajtó használata esetén a meghajtót csatlakoztatni kell a varázslót futtató számítógéphez, és a Windowsnak azt cserélhető eszközként kell észlelnie. A varázsló közvetlenül az USB-meghajtóra ír, amikor létrehozza az adathordozót.|  
|Kimeneti mappa létrehozása|CD-/DVD-készlet esetén:<br /><br /> Mielőtt elindítja a Feladatütemezési média létrehozása varázslót CD- vagy DVD-készletre írható média létrehozásához, létre kell hoznia egy mappát a varázsló által elkészített kimeneti fájlok tárolásához. A CD- vagy DVD-készletre írható médiát a varázsló közvetlenül ebbe a mappába helyezi .iso-fájlok formájában.|  

 Médiarögzítésű adathordozó létrehozásához a következő eljárást használhatja.  

#### <a name="to-create-capture-media"></a>Médiarögzítésű adathordozó létrehozása  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Operációs rendszerek**pontot, majd kattintson a **Feladatütemezések**elemre.  

3.  A Feladatütemezési média létrehozása varázsló elindításához kattintson a **Kezdőlap** **Létrehozás** csoportjában található **Feladatütemezési média létrehozása** elemre.  

4.  A **Válassza ki az adathordozó típusát** oldalon jelölje ki a **Média rögzítése**elemet, majd kattintson a **Tovább**gombra.  

5.  A **Hordozó típusa** lapon adja meg, hogy az adathordozót flash meghajtón vagy CD-/DVD-készleten hozza-e létre, majd kattintson az alábbiak konfigurálásához:  

    -   Ha az **USB flash meghajtó**lehetőséget választja, adja meg a meghajtót, amelyen a tartalmat tárolni kívánja.  

    -   A **CD/DVD-készlet**választásakor adja meg az adathordozó kapacitását, valamint a kimeneti fájlok nevét és elérési útvonalát. A varázsló erre a helyre írja ki a kimeneti fájlokat. Például:  **\\\servername\folder\outputfile.iso**  

         Ha az adathordozó kapacitása túl kicsi a teljes tartalom tárolásához, a rendszer több fájlt hoz létre, és több CD-n vagy DVD-n kell tárolnia a tartalmat. Ha több adathordozó szükséges, a Configuration Manager fűz sorszámot a létrehozott kimeneti fájlok nevéhez. Emellett, ha az operációs rendszer mellett alkalmazást is telepít, és az alkalmazás nem fér el egyetlen adathordozón, a Configuration Manager az alkalmazás több adathordozón tárolja. A különálló adathordozó futtatásakor a Configuration Manager bekéri a felhasználótól a következő tartalmazó adathordozót az alkalmazást.  

        > [!IMPORTANT]  
        >  Meglévő .iso lemezkép kijelölése esetén a Feladatütemezési média varázsló törli a lemezképet a meghajtóról vagy megosztásról, amint a varázsló következő oldalára lép. A meglévő lemezkép akkor is törlődik, ha később megszakítja a varázsló működését.  

     Kattintson a **Tovább**gombra.  

6.  A **Rendszerindító lemezkép** lapon adja meg a következő adatokat, majd kattintson a **Tovább**gombra.  

    > [!IMPORTANT]  
    >  A megadott rendszerindító lemezkép architektúrájának meg kell felelnie a referencia-számítógép architektúrájának. Az x64 rendszerű referencia-számítógépek például elindíthatók és működtethetők x86 vagy x64 rendszerindító lemezképpel is. Az x86 rendszerű referencia-számítógépek elindításához és működtetéséhez azonban csak x86 rendszerindító lemezkép használható.  

    -   A **Rendszerindító lemezkép** mezőben adja meg a rendszerindító lemezképet a referencia-számítógép indításához.  

    -   A **Terjesztési pont** mezőben adja meg azt a terjesztési pontot, ahol a rendszerindító lemezkép található. A varázsló lekéri a rendszerindító lemezképet a terjesztési pontról, és a médiára írja azt.  

        > [!NOTE]  
        >  A terjesztési ponton található tartalomtárhoz Olvasási hozzáférési jogosultsággal kell rendelkeznie.  

7.  Fejezze be a varázslót.  

