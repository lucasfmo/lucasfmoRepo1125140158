---
title: "Manuálisan előkészített adathordozó létrehozása a System Center Configuration Managerrel |} Microsoft Docs"
description: "Manuálisan előkészített adathordozó létrehozása a System Center Configuration Manager egyszerűsítése érdekében a Windows központi telepítési, több forgatókönyv szerint."
ms.custom: na
ms.date: 04/11/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ff6e7267-302a-4563-815e-cdc0d1a4b60f
caps.latest.revision: 12
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: ae9488a34c6b1e04397c4875de4b3bc607f7116c
ms.openlocfilehash: 33abf3853d912d423e427db4d35fb4a16167164e
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="create-prestaged-media-with-system-center-configuration-manager"></a>Manuálisan előkészített adathordozó létrehozása a System Center Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A manuálisan előkészített adathordozó a System Center Configuration Manager egy Windows Imaging Format (WIM) fájl, amelyiket a gyártó, illetve a Configuration Manager környezethez nem csatlakoztatott vállalati előkészítő központ egy operációs rendszer nélküli számítógépen telepítve.  
A manuálisan előkészített adathordozó tartalmazza a célszámítógép elindításához használt rendszerindító lemezképet és a célszámítógépre alkalmazható operációsrendszer-képet. Megadhatja a manuálisan előkészített adathordozó részét képező alkalmazásokat, csomagokat és illesztőprogram-csomagokat is. Az operációs rendszert telepítő feladatütemezést az adathordozó nem tartalmazza. A manuálisan előkészített adathordozót az új számítógép merevlemezére teszik mielőtt a számítógépet elküldenék a végfelhasználónak. Az operációs rendszer központi telepítésekor az alábbi helyzetekben használhatja az előkészített adathordozókat:  

-   [Lemezkép létrehozása OEM gyára vagy helyi raktár számára](../../osd/deploy-use/create-an-image-for-an-oem-in-factory-or-a-local-depot.md)  

-   [A Windows új verziójának telepítése egy új (operációs rendszer nélküli) számítógépre](install-new-windows-version-new-computer-bare-metal.md)  

-   [A Windows to Go központi telepítése](deploy-windows-to-go.md)  

 A számítógép a manuálisan előkészített adathordozó alkalmazása utáni első indításakor a Windows PE környezetben indul el, és csatlakozik egy felügyeleti ponthoz, hogy megkeresse a feladatütemezést, amely befejezi az operációs rendszer telepítési folyamatát. Megadhatja a manuálisan előkészített adathordozó részét képező alkalmazásokat, csomagokat és illesztőprogram-csomagokat. Olyan feladatütemezés telepítésekor, amelyik manuálisan előkészített adathordozót használ, a varázsló először a feladatütemezés gyorsítótárában keresi az érvényes tartalmat, és ha az nem található vagy megváltozott, letölti a tartalmat a terjesztési pontról.  

##  <a name="BKMK_CreatePrestagedMedia"></a> Manuálisan előkészített adathordozó létrehozása  
 Mielőtt manuálisan előkészített adathordozót hozna létre a Feladatütemezési média létrehozása varázsló segítségével, győződjön meg róla, hogy az alábbi feltételek teljesülnek-e:  

|Feladat|Leírás|  
|----------|-----------------|  
|Rendszerindító lemezkép|Az operációs rendszer központi telepítéséhez használt feladatütemezés rendszerindító lemezképével kapcsolatban fontolja meg az alábbiakat:<br /><br /> -A rendszerindító lemezkép architektúrájának meg kell felelnie a célszámítógép architektúrájának. Az x64 rendszerű célszámítógépek például elindíthatók és működtethetők x86 vagy x64 rendszerindító lemezképpel is. Az x86 rendszerű célszámítógépek elindításához és működtetéséhez azonban csak x86 rendszerindító lemezkép használható.<br />-Győződjön meg arról, hogy a rendszerindító lemezkép tartalmazza a hálózati és háttértár tároló-illesztőprogramoktól, amelyek a célszámítógép kiépítéséhez szükségesek.|  
|Feladatütemezés létrehozása operációs rendszer központi telepítéséhez|A manuálisan előkészített adathordozó részeként meg kell adnia az operációs rendszer központi telepítéséhez használandó feladatütemezést.<br /><br /> -Az új feladatütemezés létrehozásának lépéseit, lásd: [hozzon létre egy feladatütemezést az operációs rendszer telepítéséhez](../../osd/deploy-use/create-a-task-sequence-to-install-an-operating-system.md).<br />-A feladatok importálásával kapcsolatos további információkért lásd: [feladatok automatizálásához a feladatütemezések kezeléséhez](../../osd/deploy-use/manage-task-sequences-to-automate-tasks.md).|  
|A feladatütemezéshez társított összes tartalom terjesztése|A feladatütemezéshez szükséges összes tartalmat helyezze el legalább egy terjesztési ponton. Ide tartozik a rendszerindító lemezkép, az operációs rendszer lemezképe és az egyéb kapcsolódó fájlok. A varázsló a terjesztési pontról gyűjti az adatokat, amikor létrehozza a különálló adathordozót. A terjesztési ponton található tartalomtárhoz **Olvasási** hozzáférési jogosultsággal kell rendelkeznie.  További információkért lásd: [tartalomtár](../../core/plan-design/hierarchy/the-content-library.md).|  
|Merevlemez a célszámítógépen|A célszámítógép merevlemezét formázni kell, mielőtt a manuálisan előkészített adathordozó tartalma a számítógép merevlemezére kerülne. Ha a merevlemez nincs formázva az adathordozó alkalmazásakor, az operációs rendszer központi telepítését végrehajtó feladatütemezés működése sikertelen lesz, amikor megkísérli elindítani a célszámítógépet.|  

> [!NOTE]  
>  A feladatütemezési média létrehozása varázsló a következő feladatütemezési változó állapotát állítja be az adathordozón: **_SMSTSMediaType = OEMMedia**. Ezt az állapotot használhatja a feladatütemezésben.  

 Manuálisan előkészített adathordozó létrehozásához a következő eljárást használhatja.  

#### <a name="to-create-prestaged-media"></a>Manuálisan előkészített adathordozó létrehozása  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Operációs rendszerek**pontot, majd kattintson a **Feladatütemezések**elemre.  

3.  A Feladatütemezési média létrehozása varázsló elindításához kattintson a **Kezdőlap** **Létrehozás** csoportjában található **Feladatütemezési média létrehozása** elemre.  

4.  A **Válassza ki az adathordozó típusát** lapon adja meg az alábbi adatokat, majd kattintson a **Tovább**gombra.  

    -   Válassza a **Manuálisan előkészített média**elemet.  

    -   Ha az operációs rendszer felhasználói beavatkozást nem igénylő központi telepítését kívánja lehetővé tenni, jelölje be az **Operációs rendszer felügyelet nélküli központi telepítésének engedélyezése**beállítást. Ebben az esetben a telepítés nem kéri be a felhasználótól a hálózati konfigurációs adatokat és a választható feladatütemezéseket. Ugyanakkor ha az adathordozó konfigurációja jelszavas védelmet ír elő, a rendszer mindenképpen kéri a jelszót a felhasználótól.  

5.  A **Médiakezelés** lapon adja meg az alábbi adatokat, majd kattintson a **Tovább**gombra.  

    -   Válassza a **Dinamikus média** lehetőséget, ha engedélyezni szeretné, hogy a felügyeleti pontok átirányíthassák más felügyeleti pontokra a tartalmat az ügyfél helyének alapján a hely határain belül.  

    -   Válassza a **Helyalapú média** lehetőséget, ha azt szeretné, hogy a média csak a megadott felügyeleti pontra jusson el.  

6.  A **Média tulajdonságai**  lapon adja meg a következő adatokat, majd kattintson a **Tovább**gombra.  

    -   **Által létrehozott**: Adja meg, hogy ki hozta létre az adathordozót.  

    -   **Verzió**: Adja meg az adathordozó verziószámát.  

    -   **Megjegyzés**: Adja meg az adathordozó felhasználási területének egyedi leírását.  

    -   **Médiafájl**: Adja meg a és a kimeneti fájlok elérési útja. A varázsló erre a helyre írja ki a kimeneti fájlokat. Például:  **\\\servername\folder\outputfile.wim**  

7.  A **Biztonság** lapon adja meg az alábbi adatokat, majd kattintson a **Tovább**gombra.  

    -   Válassza ki a **Ismeretlen számítógépek támogatásának engedélyezése** melletti jelölőnégyzetet, hogy lehetővé teszi az adathordozó olyan operációs rendszerek központi telepítéséhez a Configuration Manager által nem kezelt számítógépekre. Nincs rekord ezekhez a számítógépekhez a Configuration Manager adatbázisába.  További információkért lásd: [Ismeretlen számítógépek központi telepítésének előkészítéséhez](../get-started/prepare-for-unknown-computer-deployments.md).  

    -   Jelölje be a **Média védelme jelszóval** négyzetet, és adjon meg egy erős jelszót az adathordozó jogosulatlan hozzáférés elleni védelmének elősegítésére. Ha jelszót ad meg, a manuálisan előkészített adathordozó használatához a felhasználónak be kell írnia ezt a jelszót.  

        > [!IMPORTANT]  
        >  Javasoljuk, hogy mindig használjon jelszót a manuálisan előkészített adathordozó védelmére.  

    -   A HTTP-kommunikációhoz válassza az **Önaláírt médiatanúsítvány létrehozása**beállítást, majd adja meg a tanúsítvány érvényességének kezdő és záró dátumát.  

    -   A HTTPS-kommunikációhoz válassza a **PKI tanúsítványának importálása**beállítást, majd adja meg az importálandó tanúsítványt és annak jelszavát.  

         További információ a rendszerindító lemezképekhez használt ügyféltanúsítványról: [PKI-tanúsítványkövetelmények](../../core/plan-design/network/pki-certificate-requirements.md).  

    -   **Felhasználó-eszköz kapcsolat**: Felhasználó-központú Felügyelet támogatásához a Configuration Manager alkalmazásban, határozza meg, hogyan rendelje hozzá a felhasználókat a célszámítógéphez az adathordozót. Hogyan támogatja az operációs rendszer központi telepítése a felhasználó-eszköz kapcsolat kapcsolatos további információkért lásd: [rendelje hozzá a felhasználókat a célszámítógéppel](../get-started/associate-users-with-a-destination-computer.md).  

        -   Válassza az **Automatikus jóváhagyással engedélyezze a felhasználó-eszköz kapcsolatot** lehetőséget, ha azt szeretné, hogy a média automatikusan rendelje hozzá a felhasználókat a célszámítógéphez. Ez a funkció az operációs rendszert telepítő feladatütemezés műveletein alapul. Ebben az esetben a feladatütemezés akkor hozza létre a kapcsolatot a megadott felhasználók és a célszámítógép között, amikor telepíti az operációs rendszert a célszámítógépre.  

        -   Válassza **A rendszergazda jóváhagyásától függően engedélyezze a felhasználó-eszköz kapcsolatot** lehetőséget, ha azt szeretné, hogy a média az engedély megadása után rendelje hozzá a felhasználókat a célszámítógéphez. Ez a funkció az operációs rendszert telepítő feladatütemezés hatókörén alapul. Ebben az esetben a feladatütemezés létrehozza a kapcsolatot a megadott felhasználók és a célszámítógép között, de az operációs rendszer telepítése előtt megvárja a rendszergazdai jóváhagyást.  

        -   Válassza a **Ne engedélyezze a felhasználó-eszköz kapcsolatot** lehetőséget, ha azt szeretné, hogy a média ne rendelje hozzá a felhasználókat a célszámítógéphez. Ebben az esetben a feladatütemezés nem rendeli hozzá a felhasználókat a célszámítógéphez, amikor telepíti az operációs rendszert.  

8.  A **Feladatütemezés** lapon adja meg a célszámítógépen futtatni kívánt feladatütemezést. A feladatütemezés által hivatkozott tartalom az **Ez a feladatütemezés a következő tartalomra hivatkozik**ablaktáblában jelenik meg. Ellenőrizze a tartalmat, majd kattintson a **Tovább**gombra.  

9. A **Rendszerindító lemezkép** lapon adja meg a következő adatokat, majd kattintson a **Tovább**gombra.  

    > [!IMPORTANT]  
    >  A terjesztett rendszerindító lemezkép architektúrájának meg kell felelnie a célszámítógép architektúrájának. Az x64 rendszerű célszámítógépek például elindíthatók és működtethetők x86 vagy x64 rendszerindító lemezképpel is. Az x86 rendszerű célszámítógépek elindításához és működtetéséhez azonban csak x86 rendszerindító lemezkép használható.  

    -   A **Rendszerindító lemezkép** mezőben adja meg a rendszerindító lemezképet a célszámítógép indításához. További információkért lásd: [rendszerindító lemezképek kezelése](../get-started/manage-boot-images.md).  

    -   A **Terjesztési pont** mezőben adja meg azt a terjesztési pontot, ahol a rendszerindító lemezkép található. A varázsló lekéri a rendszerindító lemezképet a terjesztési pontról, és a médiára írja azt.  

        > [!NOTE]  
        >  A terjesztési ponton található tartalomtárhoz **Olvasási** hozzáférési jogosultsággal kell rendelkeznie. További információkért lásd: [tartalomtár](../../core/plan-design/hierarchy/the-content-library.md).  

    -   Ha a varázsló **Médiakezelés** lapján a **Helyalapú média** beállítást választotta, adjon meg egy elsődleges helyhez tartozó felügyeleti pontot a **Felügyeleti pont** mezőben.  

    -   Ha a varázsló **Médiakezelés** lapján a **Dinamikus média** beállítást választotta, a **Társított felügyeleti pontok** mezőben adja meg a elsődleges helyhez tartozó felügyeleti pontokat, amelyeket használni szeretne, illetve a kívánt rangsort a kezdeti kommunikációhoz.  

10. A **Lemezképek** lapon adja meg az alábbi adatokat, majd kattintson a **Tovább**gombra.  

    -   A **Lemezképcsomag** mezőben adja meg az operációs rendszer lemezképét. További információkért lásd: [operációsrendszer-lemezképek kezelése](../get-started/manage-operating-system-images.md).  

    -   Ha a csomag több operációs rendszeri lemezképet tartalmazza, a **Lemezképindex** mezőben adja meg a központilag telepíteni kívánt lemezképet.  

    -   A **Terjesztési pont** mezőben adja meg azt a terjesztési pontot, amelyen az operációs rendszer lemezképcsomagja található. A varázsló lekéri az operációs rendszer lemezképét a terjesztési pontról, és az adathordozóra írja azt.  

11. A **Testreszabás** lapon adja meg a következő adatokat, majd kattintson a **Tovább**gombra.  

    -   Adja meg a feladatütemezés által az operációs rendszer telepítéséhez használt változókat.  

    -   Adja meg a feladatütemezés futtatása előtt futtatandó előindítási parancsokat. Az indítás előtti parancsok olyan parancsfájlok vagy végrehajtható fájlok, amelyek a Windows PE környezetben képesek interakciót folytatni a felhasználóval a feladatsor futtatása és az operációs rendszer telepítése előtt. Az adathordozóhoz használható indítás előtti parancsokkal kapcsolatos további információkért tekintse meg a [indítás előtti parancsok feladatütemezési médiához](../understand/prestart-commands-for-task-sequence-media.md).  

        > [!TIP]  
        >  Feladatütemezési média létrehozásakor a a feladatütemezés írja a Csomagazonosítót és az előindítási parancssort, beleértve a feladatütemezési változók, a Configuration Manager konzolt futtató számítógépen a CreateTSMedia.log naplófájlba értékét. Ebben a naplófájlban ellenőrizheti a feladatütemezési változók értékét.  

12. Fejezze be a varázslót.  

## <a name="next-steps"></a>További lépések
[A vállalati operációs rendszerek központi telepítésének forgatókönyvei](scenarios-to-deploy-enterprise-operating-systems.md)

