---
title: "Rendszerindító adathordozó - létrehozása a Configuration Manager |} Microsoft Docs"
description: "A Configuration Manager rendszerindító adathordozó megkönnyíti a Windows új verziójának telepítése, vagy cserélje le a számítógép és az átviteli beállítások."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ead79e64-1b63-4d0d-8bd5-addff8919820
caps.latest.revision: 11
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 89158debdf4c345a325feeb608db2215a88ed81b
ms.openlocfilehash: 9032698fa12bf453041ea06bf330d3b4687c2a97
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="create-bootable-media-with-system-center-configuration-manager"></a>Rendszerindító adathordozó létrehozása a System Center Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A Configuration Manager rendszerindító adathordozó a rendszerindító lemezképet, esetleg az indítás előtti parancsokat és kapcsolódó fájlokat és a Configuration Manager fájlokat tartalmazza. Az operációs rendszer központi telepítésekor az alábbi helyzetekben használhatja az előkészített adathordozókat:  

-   [A Windows új verziójának telepítése egy új (operációs rendszer nélküli) számítógépre](install-new-windows-version-new-computer-bare-metal.md)  

-   [Meglévő számítógép cseréje és a beállítások átvitele](replace-an-existing-computer-and-transfer-settings.md)  

##  <a name="BKMK_CreateBootableMedia"></a> Rendszerindító adathordozó létrehozása  
 A rendszerindító adathordozó elindításakor elindul a célszámítógép, csatlakozik a hálózatra, és lekéri onnan az adott feladatütemezést, az operációs rendszer lemezképét és a szükséges egyéb tartalmakat. Mivel a feladatütemezés nincs az adathordozón, a feladatütemezés és/vagy a tartalom megváltoztatható anélkül, hogy újabb adathordozót kellene létrehozni. A rendszerindító adathordozón a csomagok nem titkosítottak. Önnek kell gondoskodnia az olyan biztonsági eszközökről, mint az adathordozó jelszóval való védelme, hogy a csomag tartalma védve legyen a jogosulatlan felhasználóktól.  

 Mielőtt rendszerindító adathordozót hozna létre a Feladatütemezési média létrehozása varázsló segítségével, győződjön meg arról, hogy az alábbi feltételek teljesülnek:  

|Feladat|Leírás|  
|----------|-----------------|  
|Rendszerindító lemezkép|Az operációs rendszer központi telepítéséhez használt feladatütemezés rendszerindító lemezképével kapcsolatban fontolja meg az alábbiakat:<br /><br /> -A rendszerindító lemezkép architektúrájának meg kell felelnie a célszámítógép architektúrájának. Az x64 rendszerű célszámítógépek például elindíthatók és működtethetők x86 vagy x64 rendszerindító lemezképpel is. Az x86 rendszerű célszámítógépek elindításához és működtetéséhez azonban csak x86 rendszerindító lemezkép használható.<br />-Győződjön meg arról, hogy a rendszerindító lemezkép tartalmazza a hálózati és háttértár tároló-illesztőprogramoktól, amelyek a célszámítógép kiépítéséhez szükségesek.|  
|Feladatütemezés létrehozása operációs rendszer központi telepítéséhez|A rendszerindító adathordozó részeként meg kell adnia az operációs rendszer központi telepítéséhez használandó feladatütemezést. Új feladatütemezés létrehozásának lépéseit, lásd: [hozzon létre egy feladatütemezést az operációs rendszer telepítéséhez](../deploy-use/create-a-task-sequence-to-install-an-operating-system.md).|  
|A feladatütemezéshez társított összes tartalom terjesztése|A feladatütemezéshez szükséges minden tartalmat el kell helyeznie legalább egy terjesztési ponton. Ide tartozik a rendszerindító lemezkép és a hozzá tartozó egyéb fájlok. A varázsló a terjesztési pontról gyűjti az adatokat, amikor létrehozza a rendszerindító adathordozót. A terjesztési ponton található tartalomtárhoz **Olvasási** hozzáférési jogosultsággal kell rendelkeznie.  További információkért lásd: [tartalomtár](../../core/plan-design/hierarchy/the-content-library.md).|  
|A cserélhető USB-meghajtó előkészítése|Cserélhető USB-meghajtó esetén:<br /><br /> Cserélhető USB-meghajtó használata esetén a meghajtót csatlakoztatni kell a varázslót futtató számítógéphez, és a Windowsnak azt cserélhető eszközként kell észlelnie. A varázsló közvetlenül az USB-meghajtóra ír, amikor létrehozza az adathordozót. A különálló adathordozó FAT32 fájlrendszert használ. USB flash meghajtón nem hozhat létre olyan különálló adathordozót, amelynek tartalma között 4 GB méretűnél nagyobb fájl található.|  
|Kimeneti mappa létrehozása|CD-/DVD-készlet esetén:<br /><br /> Mielőtt elindítja a Feladatütemezési média létrehozása varázslót CD- vagy DVD-készletre írható média létrehozásához, létre kell hoznia egy mappát a varázsló által elkészített kimeneti fájlok tárolásához. A CD- vagy DVD-készletre írható médiát a varázsló közvetlenül ebbe a mappába helyezi .iso-fájlok formájában.|  

 Rendszerindító adathordozó létrehozásához a következő eljárást használhatja.  

### <a name="to-create-bootable-media"></a>Rendszerindító adathordozó létrehozása  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Operációs rendszerek**pontot, majd kattintson a **Feladatütemezések**elemre.  

3.  A Feladatütemezési média létrehozása varázsló elindításához kattintson a **Kezdőlap** **Létrehozás** csoportjában található **Feladatütemezési média létrehozása** elemre.  

4.  A **Válassza ki az adathordozó típusát** oldalon adja meg az alábbi beállításokat, majd kattintson a **Tovább**gombra.  

    -   Jelölje ki a **Rendszerindító adathordozó**elemet.  

    -   Ha az operációs rendszer felhasználói beavatkozást nem igénylő központi telepítését kívánja csak lehetővé tenni, jelölje be az **Operációs rendszer felügyelet nélküli központi telepítésének engedélyezése**beállítást.  

        > [!IMPORTANT]  
        >  Ebben az esetben a telepítés nem kéri be a felhasználótól a hálózati konfigurációs adatokat és a választható feladatütemezéseket. Ugyanakkor ha az adathordozó konfigurációja jelszavas védelmet ír elő, a rendszer mindenképpen kéri a jelszót a felhasználótól.  

5.  A **Médiakezelés** oldalon adja meg a következő beállítások valamelyikét, majd kattintson a **Tovább**gombra.  

    -   Válassza a **Dinamikus média** lehetőséget, ha engedélyezni szeretné, hogy a felügyeleti pontok átirányíthassák más felügyeleti pontokra a tartalmat az ügyfél helyének alapján a hely határain belül.  

    -   Válassza a **Helyalapú média** lehetőséget, ha azt szeretné, hogy a média csak a megadott felügyeleti pontra jusson el.  

6.  A **Hordozó típusa** lapon adja meg, hogy az adathordozót flash meghajtón vagy CD-/DVD-készleten hozza-e létre, majd kattintson az alábbiak konfigurálásához:  

    > [!IMPORTANT]  
    >  A különálló adathordozó FAT32 fájlrendszert használ. USB flash meghajtón nem hozhat létre olyan különálló adathordozót, amelynek tartalma között 4 GB méretűnél nagyobb fájl található.  

    -   Ha az **USB flash meghajtó**lehetőséget választja, adja meg a meghajtót, amelyen a tartalmat tárolni kívánja.  

    -   A **CD/DVD-készlet**választásakor adja meg az adathordozó kapacitását, valamint a kimeneti fájlok nevét és elérési útvonalát. A varázsló erre a helyre írja ki a kimeneti fájlokat. Például:  **\\\servername\folder\outputfile.iso**  

         Ha az adathordozó kapacitása túl kicsi a teljes tartalom tárolásához, a rendszer több fájlt hoz létre, és több CD-n vagy DVD-n kell tárolnia a tartalmat. Ha több adathordozó szükséges, a Configuration Manager fűz sorszámot a létrehozott kimeneti fájlok nevéhez. Emellett, ha az operációs rendszer mellett alkalmazást is telepít, és az alkalmazás nem fér el egyetlen adathordozón, a Configuration Manager az alkalmazás több adathordozón tárolja. A különálló adathordozó futtatásakor a Configuration Manager bekéri a felhasználótól a következő tartalmazó adathordozót az alkalmazást.  

        > [!IMPORTANT]  
        >  Meglévő .iso lemezkép kijelölése esetén a Feladatütemezési média varázsló törli a lemezképet a meghajtóról vagy megosztásról, amint a varázsló következő oldalára lép. A meglévő lemezkép akkor is törlődik, ha később megszakítja a varázsló működését.  

     Kattintson a **Tovább**gombra.  

7.  A **Biztonság** lapon adja meg a következő beállításokat, majd kattintson a **Tovább**gombra.  

    -   Válassza ki a **Ismeretlen számítógépek támogatásának engedélyezése** melletti jelölőnégyzetet, hogy lehetővé teszi az adathordozó olyan operációs rendszerek központi telepítéséhez a Configuration Manager által nem kezelt számítógépekre. Nincs rekord ezekhez a számítógépekhez a Configuration Manager adatbázisába.  

         Az ismeretlen számítógépek a következők:  

        -   Egy számítógép, amelyen nincs telepítve a Configuration Manager-ügyfél  

        -   Olyan számítógép, amely nincs importálva a Configuration Managerbe  

        -   Olyan számítógép, amely nem észlelhető a Configuration Manager által  

    -   Jelölje be a **Média védelme jelszóval** négyzetet, és adjon meg egy erős jelszót az adathordozó jogosulatlan hozzáférés elleni védelmének elősegítésére. Ha jelszót ad meg, a rendszerindító adathordozó használatához a felhasználónak be kell írnia ezt a jelszót.  

        > [!IMPORTANT]  
        >  Ajánlott biztonsági eljárásként a rendszerindító adathordozóhoz mindig használjon jelszavas védelmet.  

    -   A HTTP-kommunikációhoz válassza az **Önaláírt médiatanúsítvány létrehozása**beállítást, majd adja meg a tanúsítvány érvényességének kezdő és záró dátumát.  

    -   A HTTPS-kommunikációhoz válassza a **PKI tanúsítványának importálása**beállítást, majd adja meg az importálandó tanúsítványt és annak jelszavát.  

         További információ a rendszerindító lemezképekhez használt ügyféltanúsítványról: [PKI-tanúsítványkövetelmények](../../core/plan-design/network/pki-certificate-requirements.md).  

    -   **Felhasználó-eszköz kapcsolat**: Felhasználó-központú Felügyelet támogatásához a Configuration Manager alkalmazásban, határozza meg, hogyan rendelje hozzá a felhasználókat a célszámítógéphez az adathordozót. Hogyan támogatja az operációs rendszer központi telepítése a felhasználó-eszköz kapcsolat kapcsolatos további információkért lásd: [rendelje hozzá a felhasználókat a célszámítógéppel](../get-started/associate-users-with-a-destination-computer.md).  

        -   Válassza az **Automatikus jóváhagyással engedélyezze a felhasználó-eszköz kapcsolatot** lehetőséget, ha azt szeretné, hogy a média automatikusan rendelje hozzá a felhasználókat a célszámítógéphez. Ez a funkció az operációs rendszert telepítő feladatütemezés műveletein alapul. Ebben az esetben a feladatütemezés akkor hozza létre a kapcsolatot a megadott felhasználók és a célszámítógép között, amikor telepíti az operációs rendszert a célszámítógépre.  

        -   Válassza **A rendszergazda jóváhagyásától függően engedélyezze a felhasználó-eszköz kapcsolatot** lehetőséget, ha azt szeretné, hogy a média az engedély megadása után rendelje hozzá a felhasználókat a célszámítógéphez. Ez a funkció az operációs rendszert telepítő feladatütemezés hatókörén alapul.  Ebben az esetben a feladatütemezés létrehozza a kapcsolatot a megadott felhasználók és a célszámítógép között, de az operációs rendszer telepítése előtt megvárja a rendszergazdai jóváhagyást.  

        -   Válassza a **Ne engedélyezze a felhasználó-eszköz kapcsolatot** lehetőséget, ha azt szeretné, hogy a média ne rendelje hozzá a felhasználókat a célszámítógéphez. Ebben az esetben a feladatütemezés nem rendeli hozzá a felhasználókat a célszámítógéphez, amikor telepíti az operációs rendszert.  

8.  A **Rendszerindító lemezkép** oldalon adja meg a következő beállításokat, majd kattintson a **Tovább**gombra.  

    > [!IMPORTANT]  
    >  A terjesztett rendszerindító lemezkép architektúrájának meg kell felelnie a célszámítógép architektúrájának. Az x64 rendszerű célszámítógépek például elindíthatók és működtethetők x86 vagy x64 rendszerindító lemezképpel is. Az x86 rendszerű célszámítógépek elindításához és működtetéséhez azonban csak x86 rendszerindító lemezkép használható.  

    -   A **Rendszerindító lemezkép** mezőben adja meg a rendszerindító lemezképet a célszámítógép indításához.  

    -   A **Terjesztési pont** mezőben adja meg azt a terjesztési pontot, ahol a rendszerindító lemezkép található. A varázsló lekéri a rendszerindító lemezképet a terjesztési pontról, és a médiára írja azt.  

        > [!NOTE]  
        >  A terjesztési ponton található tartalomtárhoz **Olvasási** hozzáférési jogosultsággal kell rendelkeznie.  

    -   Ha helyalapú rendszerindító adathordozót hoz létre a varázsló **Médiakezelés** lapján, a **Felügyeleti pont** mezőben adjon meg egy elsődleges helyről származó felügyeleti pontot.  

    -   Ha dinamikus rendszerindító adathordozót hoz létre a varázsló **Médiakezelés** lapján, a **Társított felügyeleti pontok**mezőben adja meg az elsődleges hely használni kívánt felügyeleti pontjait, valamint a prioritási sorrendet a kezdeti kommunikációhoz.  

9. A **Testreszabás** oldalon adja meg a következő beállításokat, majd kattintson a **Tovább**gombra.  

    -   Adja meg a feladatütemezés által az operációs rendszer telepítéséhez használt változókat.  

    -   Adja meg a feladatütemezés futtatása előtt futtatandó előindítási parancsokat. Az indítás előtti parancsok olyan parancsfájlok vagy végrehajtható fájlok, amelyek a Windows PE környezetben képesek interakciót folytatni a felhasználóval a feladatsor futtatása és az operációs rendszer telepítése előtt. További információkért lásd: [indítás előtti parancsok feladatütemezési médiához](../understand/prestart-commands-for-task-sequence-media.md).  

        > [!TIP]  
        >  Feladatütemezési média létrehozásakor a a feladatütemezés írja a Csomagazonosítót és az előindítási parancssort, beleértve a feladatütemezési változók, a Configuration Manager konzolt futtató számítógépen a CreateTSMedia.log naplófájlba értékét. Ebben a naplófájlban ellenőrizheti a feladatütemezési változók értékét.  

         Választható módon jelölje be a **Tartalmazza az indítás előtti parancshoz szükséges fájlokat** négyzetet az indítás előtti parancshoz szükséges fájlok bevételéhez.  

10. Fejezze be a varázslót.  

## <a name="create-bootable-media-on-a-usb-drive-from-a-network-share"></a>Egy hálózati megosztáson USB-meghajtóval rendszerindító adathordozó létrehozása
Ebben a szakaszban található információk segítséget nyújt egy USB flash meghajtón rendszerindító adathordozó létrehozása, ha a flash meghajtó nem csatlakozik a Configuration Manager konzolt futtató számítógép. A rendszerindító adathordozó létrehozásához az USB-meghajtón, feladatütemezési rendszerindítási adathordozó létrehozása, csatlakoztassa az ISO-fájlt, és a fájlok átviteléhez az ISO-fájlt az USB-meghajtóra.

1. [A feladatütemezési rendszerindítási adathordozó létrehozása](#to-create-task-boobable-media). Az a **médiatípus** lapon jelölje be **CD/DVD-készlet**. A varázsló ír a kimeneti fájlokat a megadott helyre. Például:  **\\\servername\folder\outputfile.iso**.  
2. A cserélhető USB-meghajtó előkészítése. A meghajtó és kell lennie, üres, rendszerindításra alkalmas.
3. Csatlakoztathatja az ISO-fájlt a megosztásnak a helyét, és a fájlok átviteléhez az ISO-fájlt az USB-meghajtót.

## <a name="next-steps"></a>További lépések  
[A Windows központi telepítése a hálózaton keresztül rendszerindító adathordozó használatával](use-bootable-media-to-deploy-windows-over-the-network.md)  

