---
title: "Különálló adathordozó létrehozása a System Center Configuration Managerrel |} Microsoft Docs"
description: "Különálló adathordozó használatával kapcsolat nélküli számítógépeken az operációs rendszer telepítése a Configuration Manager-hely vagy a hálózati."
ms.custom: na
ms.date: 03/24/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c6b9ccd2-78d9-4f0e-b25a-70d0866300ba
caps.latest.revision: 21
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: d4689545ce2be5c16a65b24489f30028a0f90f94
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="create-stand-alone-media-with-system-center-configuration-manager"></a>Különálló adathordozó létrehozása a System Center Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A Configuration Manager különálló adathordozó tartalmaz mindent, szükséges egy kapcsolat nélküli számítógépeken az operációs rendszer telepítése a Configuration Manager-hely vagy a hálózaton keresztül. Különálló adathordozó használata a következő operációsrendszer-telepítési helyzetekben:  

-   [A Windows új verziójára meglévő számítógép frissítése](refresh-an-existing-computer-with-a-new-version-of-windows.md)  

-   [A Windows új verziójának telepítése egy új (operációs rendszer nélküli) számítógépre](install-new-windows-version-new-computer-bare-metal.md)  

-   [A Windows frissítése a legújabb verzióra](upgrade-windows-to-the-latest-version.md)  

 A különálló adathordozó tartalmazza a feladatütemezést, amely automatizálja az operációs rendszer és minden egyéb szükséges tartalom, beleértve a rendszerindító lemezképet, az operációs rendszer lemezképét és az eszközillesztők telepítésének lépéseit. Mivel az operációs rendszer telepítéséhez szükséges adatok az önálló adathordozón tárolódnak, az önálló adathordozó lemezterület-igénye jelentősen nagyobb, mint a más típusú telepítőlemezeké. Amikor különálló adathordozót hoz létre egy központi adminisztrációs helyen, az ügyfél a hozzárendelt hely kódját az Active Directoryból fogja lekérni. A gyermekhelyeken létrehozott különálló adathordozók automatikusan az adott hely kódját rendelik az ügyfélhez.  

##  <a name="BKMK_CreateStandAloneMedia"></a>Különálló adathordozó létrehozása  
 Előtt a különálló adathordozó a feladatütemezési média létrehozása varázsló segítségével hoz létre, ügyeljen arra, hogy a következő feltételek teljesülnek:  

### <a name="create-a-task-sequence-to-deploy-an-operating-system"></a>Feladatütemezés létrehozása operációs rendszer központi telepítéséhez
A különálló adathordozó részeként meg kell adnia az operációs rendszer központi telepítéséhez használandó feladatütemezést. Új feladatütemezés létrehozásának lépéseit, lásd: [hozzon létre egy feladatütemezést az operációs rendszer telepítése a System Center Configuration Managerben](create-a-task-sequence-to-install-an-operating-system.md).

A következő műveletek nem támogatottak különálló adathordozók:
- Az Illesztőprogramok automatikus alkalmazása lépés használata a feladatütemezésben. Az eszközillesztők illesztőprogram-katalógusból való automatikus alkalmazása nem támogatott, de az Illesztőprogram-csomag alkalmazása lépésben elérhetővé tehet egy adott illesztőprogram-készletet a Windows telepítő számára.
- A csomagtartalom letöltése lépést a feladatütemezésben. A felügyeleti pont adatait nem áll rendelkezésre a különálló adathordozón, ezért a lépés sikertelen lesz a tartalom helyét enumerálása közben.
- A szoftverfrissítések telepítése.
- Szoftver telepítése az operációs rendszer telepítése előtt.
- Operációs rendszert központilag telepítő feladatütemezések.
- Felhasználók társítása a célszámítógéphez a felhasználó-eszköz kapcsolat támogatásához.
- Dinamikus csomag telepítése az Install Packages (Csomagok telepítése) feladattal.
- Dinamikus alkalmazás telepítése az Install Application (Alkalmazás telepítése) feladattal.

Ha az operációs rendszerek központi telepítéséhez használt feladatütemezés tartalmazza a [csomagtelepítés](../../osd/understand/task-sequence-steps.md#BKMK_InstallPackage) lépés és hozza létre a különálló adathordozót egy központi adminisztrációs helyen, hiba történhet. A központi felügyeleti hely nem rendelkezik azon ügyfélkonfigurálási házirendekkel, amelyek a feladatütemezés végrehajtása közben a szoftverterjesztési ügynök engedélyezéséhez szükségesek. A CreateTSMedia.log fájlban a következő hiba jelenhet meg:<br /><br /> "WMI-metódus SMS_TaskSequencePackage.GetClientConfigPolicies sikertelen (0x80041001)"<br /><br /> A különálló adathordozót egy **csomag telepítése** lépés, kell létrehoznia a különálló adathordozót azon az elsődleges helyen, amelynek engedélyezett szoftverterjesztési ügynöke, vagy adja hozzá egy [parancssor futtatása](../understand/task-sequence-steps.md#BKMK_RunCommandLine) lépés után a [Windows és ConfigMgr beállítása](../understand/task-sequence-steps.md#BKMK_SetupWindowsandConfigMgr) lépés és első **csomag telepítése** lépést a feladatütemezéshez. A **Parancssor futtatása** lépés a WMIC parancsot futtatja, hogy engedélyezze a szoftverterjesztési ügynököt, mielőtt az első Telepítőcsomag lépés futna. A feladatütemezés **Parancssor futtatása** lépésében a következő használható:<br /><br />
```
WMIC /namespace:\\\root\ccm\policy\machine\requestedconfig path ccm_SoftwareDistributionClientConfig CREATE ComponentName="Enable SWDist", Enabled="true", LockSettings="TRUE", PolicySource="local", PolicyVersion="1.0", SiteSettingsKey="1" /NOINTERACTIVE
```

### <a name="distribute-all-content-associated-with-the-task-sequence"></a>A feladatütemezéshez társított összes tartalom terjesztése
A feladatütemezéshez szükséges minden tartalmat el kell helyeznie legalább egy terjesztési ponton. Ide tartozik a rendszerindító lemezkép, az operációs rendszer lemezképe és az egyéb kapcsolódó fájlok. A varázsló a terjesztési pontról gyűjti az adatokat, amikor létrehozza a különálló adathordozót. A terjesztési ponton található tartalomtárhoz **Olvasási** hozzáférési jogosultsággal kell rendelkeznie.  További információk: [Egy feladatütemezés által hivatkozott tartalom terjesztése](manage-task-sequences-to-automate-tasks.md#BKMK_DistributeTS).

### <a name="prepare-the-removable-usb-drive"></a>A cserélhető USB-meghajtó előkészítése
*A cserélhető USB-meghajtó:*

Cserélhető USB-meghajtó használata esetén a meghajtót csatlakoztatni kell a varázslót futtató számítógéphez, és a Windowsnak azt cserélhető eszközként kell észlelnie. A varázsló közvetlenül az USB-meghajtóra ír, amikor létrehozza az adathordozót. A különálló adathordozó FAT32 fájlrendszert használ. USB flash meghajtón nem hozhat létre olyan különálló adathordozót, amelynek tartalma között 4 GB méretűnél nagyobb fájl található.

### <a name="create-an-output-folder"></a>Kimeneti mappa létrehozása
*A CD/DVD-készlet:*

Mielőtt elindítja a Feladatütemezési média létrehozása varázslót CD- vagy DVD-készletre írható média létrehozásához, létre kell hoznia egy mappát a varázsló által elkészített kimeneti fájlok tárolásához. A CD- vagy DVD-készletre írható médiát a varázsló közvetlenül ebbe a mappába helyezi .iso-fájlok formájában.


 A következő eljárással hozhat létre önálló adathordozót cserélhető USB-meghajtó vagy CD/DVD-készleten.  

## <a name="to-create-stand-alone-media"></a>Különálló adathordozó létrehozása  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Operációs rendszerek**pontot, majd kattintson a **Feladatütemezések**elemre.  

3.  A Feladatütemezési média létrehozása varázsló elindításához kattintson a **Kezdőlap** **Létrehozás** csoportjában található **Feladatütemezési média létrehozása** elemre.  

4.  A **Válassza ki az adathordozó típusát** oldalon adja meg az alábbi beállításokat, majd kattintson a **Tovább**gombra.  

    -   Válassza ki **különálló adathordozó**.  

    -   Ha az operációs rendszer felhasználói beavatkozást nem igénylő központi telepítését kívánja lehetővé tenni, jelölje be az **Operációs rendszer felügyelet nélküli központi telepítésének engedélyezése**beállítást. Ebben az esetben a telepítés nem kéri be a felhasználótól a hálózati konfigurációs adatokat és a választható feladatütemezéseket. Ugyanakkor ha az adathordozó konfigurációja jelszavas védelmet ír elő, a rendszer mindenképpen kéri a jelszót a felhasználótól.  

5.  A **Hordozó típusa** lapon adja meg, hogy az adathordozót flash meghajtón vagy CD-/DVD-készleten hozza-e létre, majd kattintson az alábbiak konfigurálásához:  

    > [!IMPORTANT]  
    >  A különálló adathordozó FAT32 fájlrendszert használ. USB flash meghajtón nem hozhat létre olyan különálló adathordozót, amelynek tartalma között 4 GB méretűnél nagyobb fájl található.  

    -   Ha az **USB flash meghajtó**lehetőséget választja, adja meg a meghajtót, amelyen a tartalmat tárolni kívánja.  

    -   A **CD/DVD-készlet**választásakor adja meg az adathordozó kapacitását, valamint a kimeneti fájlok nevét és elérési útvonalát. A varázsló erre a helyre írja ki a kimeneti fájlokat. Például:  **\\\servername\folder\outputfile.iso**  

         Ha az adathordozó kapacitása túl kicsi a teljes tartalom tárolásához, a rendszer több fájlt hoz létre, és több CD-n vagy DVD-n kell tárolnia a tartalmat. Ha több adathordozó szükséges, a Configuration Manager fűz sorszámot a létrehozott kimeneti fájlok nevéhez. Emellett, ha az operációs rendszer mellett alkalmazást is telepít, és az alkalmazás nem fér el egyetlen adathordozón, a Configuration Manager az alkalmazás több adathordozón tárolja. A különálló adathordozó futtatásakor a Configuration Manager bekéri a felhasználótól a következő tartalmazó adathordozót az alkalmazást.   

         > [!IMPORTANT]  
         >  Meglévő .iso lemezkép kijelölése esetén a Feladatütemezési média varázsló törli a lemezképet a meghajtóról vagy megosztásról, amint a varázsló következő oldalára lép. A meglévő lemezkép akkor is törlődik, ha később megszakítja a varázsló működését.  

     Kattintson a **Tovább** gombra.  

6.  Az a **biztonsági** lapon, a következő beállítások közül választhat, majd **következő**:
    - **Adathordozó jelszavas védelme**: Adjon meg egy erős jelszót az adathordozó védelmének elősegítésére. Ha jelszót ad meg, a jelszót az adathordozó használatához szükséges.  

        > [!IMPORTANT]  
        >  A különálló adathordozón csak a feladatütemezési lépést, és ezek változói vannak titkosítva. Az adathordozó egyéb tartalma nincs titkosítva, ezért ne adjon meg bizalmas adatokat a feladatütemezés parancsfájljaiban. Tárolásához és valósítja meg az összes bizalmas információk a feladatütemezési változók használatával.  

    - **Adja meg a különálló adathordozó érvényességéhez időintervallumát** (1702 verziójával kezdve): Nem kötelező érvényességének kezdő és záró dátumának beállítása az adathordozón. Ezek a beállítások alapesetben le vannak tiltva. A dátum a számítógép rendszerideje összehasonlítja a különálló adathordozó futtatása előtt. Amikor a rendszer pontos ideje a kezdési időpontnál korábbi vagy későbbi, mint a lejárati idő, a különálló adathordozó nem indult el. Ezek a beállítások is elérhetők a New-CMStandaloneMedia PowerShell-parancsmag használatával.
7.  Az a **különálló CD/DVD** lapon adja meg az operációs rendszert központilag telepítő feladatütemezést, és kattintson a **következő**. Válasszon **társított alkalmazások függőségeinek észlelése és hozzáadása az adathordozóhoz** tartalom hozzáadása az alkalmazásfüggőségek önálló adathordozót.
    > [!TIP]
    > Várt alkalmazásfüggőségek nem látható, ha kijelölésének megszüntetése, és ezután jelölje ki újra a **társított alkalmazások függőségeinek észlelése és hozzáadása az adathordozóhoz** beállítás a listájának frissítése.

    A varázsló lehetővé teszi, hogy csak adott rendszerindító lemezképhez társított feladatütemezés kiválasztását.  

8. Az a **alkalmazás kijelölése** lap (rendelkezésre álló 1702 verziójától kezdve), adja meg a médiafájl részeként, és kattintson az alkalmazástartalmat **következő**.
9. Az a **csomag kiválasztása** lap (rendelkezésre álló 1702 verziójától kezdve), adja meg a médiafájl részeként, és kattintson a csomag tartalmát **következő**.
10. Az a **illesztőprogram-csomag kiválasztása** lap (rendelkezésre álló 1702 verziójától kezdve), adja meg a médiafájl részeként, és kattintson az illesztőprogram-csomag tartalmát **következő**.
11.  Az a **terjesztési pontok** lapon adja meg a feladatütemezés által igényelt tartalmat tartalmazó terjesztési pontokat, és kattintson a **következő**.  

     A Configuration Manager terjesztési pontokat, amelyeken megtalálható a tartalom csak jeleníti meg. A folytatáshoz terjessze a feladatütemezéshez társított összes tartalmat (többek között a rendszerindító lemezképet és az operációs rendszer lemezképét) legalább egy terjesztési pontra. A tartalom terjesztése, vagy indítsa újra a varázslót, vagy távolítsa el a terjesztési pontokat, akkor már ezen a lapon kiválasztott nyissa meg az előző lapra, és majd vissza a **terjesztési pontok** oldalt, hogy frissüljön a terjesztési pontok listájában. A tartalmak terjesztésével kapcsolatos további információkért lásd: [Egy feladatütemezés által hivatkozott tartalom terjesztése](manage-task-sequences-to-automate-tasks.md#BKMK_DistributeTS). További információ a terjesztési pontok és a tartalomkezelésről: [tartalom és tartalomkezelési infrastruktúra kezelése a System Center Configuration Manager](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

    > [!NOTE]  
    >  Rendelkeznie kell **olvasási** hozzáférési jogosultsággal a terjesztési pontokon található tartalomtárhoz.  

12. A **Testreszabás** lapon adja meg a következő adatokat, majd kattintson a **Tovább**gombra.  

    -   Adja meg a feladatütemezés által az operációs rendszer telepítéséhez használt változókat.  

    -   Adja meg a feladatütemezés előtt futtatni kívánt indítás előtti parancsok. Az indítás előtti parancsok olyan parancsfájlok vagy végrehajtható fájlok, amelyek a Windows PE környezetben képesek interakciót folytatni a felhasználóval a feladatsor futtatása és az operációs rendszer telepítése előtt. Az adathordozóhoz használható indítás előtti parancsokkal kapcsolatos további információkért lásd: [indítás előtti parancsok feladatütemezési médiához a System Center Configuration Managerben](../understand/prestart-commands-for-task-sequence-media.md).  

         Bejelölheti **indítás előtti parancshoz szükséges fájlokat** foglalja magában a szükséges fájlok az indítás előtti parancshoz.  

        > [!TIP]  
        >  Feladatütemezési média létrehozásakor a a feladatütemezés írja a Csomagazonosítót és az előindítási parancssort, beleértve a feladatütemezési változók, a Configuration Manager konzolt futtató számítógépen a CreateTSMedia.log naplófájlba értékét. Ebben a naplófájlban ellenőrizheti a feladatütemezési változók értékét.  

13. Fejezze be a varázslót.  

 A különálló adathordozó-fájlok (.iso) a célmappában jönnek létre. Ha a **Különálló CD/DVD** lehetőséget választotta, ekkor átmásolhatja a kimeneti fájlokat egy CD- vagy DVD-készletre.  

##  <a name="BKMK_StandAloneMediaTSExample"></a>Példa feladatütemezés különálló adathordozóról  
 A következő táblázattal útmutatóként létrehozásakor a feladatütemezés különálló adathordozóról operációs rendszer központi telepítéséhez. A táblázat segítséget nyújt a feladatütemezési lépések általános sorrendjének meghatározásához és a lépések logikai csoportokba rendezéséhez és szerkezetének kialakításához. Az Ön által létrehozott feladatütemezés ettől a példától változhat, és több vagy kevesebb feladatütemezési lépések és csoportok tartalmazhatnak.  

> [!NOTE]  
>  A feladatütemezési média varázsló minden esetben különálló adathordozó létrehozásához kell használnia.  

|Feladatütemezési csoport vagy lépés|Leírás|  
|---------------------------------|-----------------|  
|Fájlok és beállítások rögzítése – **(új feladatütemezési csoport)**|Feladatütemezési csoport létrehozása. A feladatütemezési csoportok a jobb rendezés és hibaellenőrzés érdekében összefogják a hasonló feladatütemezési lépéseket.|  
|Windows-beállítások rögzítése|Ezzel a feladatütemezési lépéssel jelölheti ki azokat a beállításokat a Microsoft Windowsban, amelyek rögzítve lesznek a célszámítógép meglévő operációs rendszeréből a rendszerképből való újratelepítés előtt. Rögzítheti a számítógép nevét, a felhasználói és szervezeti információkat, valamint az időzóna beállításait.|  
|Hálózati beállítások rögzítése|Ezzel a feladatütemezési lépéssel rögzítheti a hálózati beállításokat arról a számítógépről, amely megkapja a feladatütemezést. A hálózati adapter beállításai mellett rögzítheti a számítógép tartományi vagy munkacsoportbeli tagságát is.|  
|Felhasználói fájlok és beállítások rögzítése – **(új feladatütemezési alcsoport)**|Feladatütemezési csoport létrehozása a feladatütemezési csoporton belül. Ez az alcsoport tartalmazza a célszámítógép meglévő operációs rendszeréből a rendszerképből való újratelepítés előtt a felhasználói állapotadatok rögzítéséhez szükséges lépéseket. Az elsőként hozzáadott csoporthoz hasonlóan ez az alcsoport a jobb rendezés és hibaellenőrzés érdekében összefogja a hasonló feladatütemezési lépéseket.|  
|Helyi állapot helyének beállítása|Ezzel a feladatütemezési lépéssel határozhat meg helyi helyet a védett elérési út kijelölésére szolgáló feladatütemezési változó használatával. A felhasználói állapot egy védett könyvtárban tárolódik a merevlemezen.|  
|Felhasználói állapot rögzítése|Ezzel a feladatütemezési lépéssel rögzítheti azokat a felhasználói fájlokat és beállításokat, amelyeket szeretne átemelni az új operációs rendszerbe.|  
|Operációs rendszer telepítése – **(új feladatütemezési csoport)**|Új feladatütemezési alcsoport létrehozása. Ez az alcsoport az operációs rendszer telepítéséhez szükséges lépéseket tartalmazza.|  
|Újraindítás Windows PE környezetben vagy merevlemezen|Ezzel a feladatütemezési lépéssel határozhat meg újraindítási beállításokat arra a számítógépre vonatkozóan, amely a feladatütemezést megkapja. Ez a lépés üzenetben tájékoztatja a felhasználót a számítógép újraindításáról, hogy a telepítés folytatódhasson.<br /><br /> Ez a lépés a csak olvasható **_SMSTSInWinPE** feladatütemezési változót használja. Ha a kapcsolódó érték **hamis** , a feladatütemezési lépés folytatódik.|  
|Operációs rendszer alkalmazása|Ezzel a feladatütemezési lépéssel telepítheti az operációsrendszer-képet a célszámítógépen. Ez a lépés törli az adott köteten (a Configuration Manager-specifikus vezérlési fájlok) kivételével az összes fájlt, és majd alkalmazza a megfelelő soros lemezköteten WIM-fájlban található összes kötetlemezképet telepíti. Egy **sysprep** válaszfájl konfigurálásával emellett megadhatja, hogy melyik lemezpartíciót szeretné használni a telepítéshez.|  
|Windows-beállítások alkalmazása|Ezzel a feladatütemezési lépéssel konfigurálhatja a Windows-beállítások konfigurációs adatait a célszámítógéphez. Az alkalmazható Windows-beállítások lehetnek a felhasználói és szervezeti adatokkal, a termék- vagy licenckulcsokkal, az időzónával és a helyi rendszergazdai jelszóval kapcsolatos adatok.|  
|Hálózati beállítások alkalmazása|Ezzel a feladatütemezési lépéssel adhatja meg a célszámítógép hálózati vagy munkacsoport-konfigurációs adatait. Megadhatja azt is, hogy a számítógép DHCP-kiszolgált használ-e, vagy statikusan is hozzárendelheti az IP-címmel kapcsolatos információkat.|  
|Illesztőprogram-csomag alkalmazása|Ez a feladatütemezési lépés lehetővé teszi, hogy egy adott illesztőprogram-csomagban minden eszközillesztőt elérhetővé tegyen a Windows telepítő számára. A különálló adathordozónak az összes szükséges illesztőprogramot tartalmaznia kell.|  
|Operációs rendszer beállítása – **(új feladatütemezési csoport)**|Új feladatütemezési alcsoport létrehozása. Ez az alcsoport tartalmazza a Configuration Manager-ügyfél telepítéséhez szükséges lépéseket.|  
|Windows és ConfigMgr beállítása|Ez a feladatütemezési lépés használatával a Configuration Manager ügyfélszoftver telepítéséhez. A Configuration Manager telepíti, és regisztrálja a Configuration Manager-ügyfél GUID Azonosítóját. A szükséges telepítési paramétereket a **Telepítés tulajdonságai** ablakban rendelheti hozzá.|  
|Felhasználói fájlok és beállítások visszaállítása – **(új feladatütemezési csoport)**|Új feladatütemezési alcsoport létrehozása. Ez az alcsoport a felhasználói állapot visszaállításához szükséges lépéseket tartalmazza.|  
|Felhasználói állapot visszaállítása|Ezzel a feladatütemezési lépéssel kezdeményezheti, hogy a Felhasználóáttelepítő (USMT) visszaállítsa a Felhasználói állapot rögzítése művelettel rögzített felhasználói állapotot és beállításokat a célszámítógépen.|  

