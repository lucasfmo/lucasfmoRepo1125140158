---
title: "A Windows to Go és a System Center Configuration Manager központi telepítése |} Microsoft Docs"
description: "Ismerje meg, hogyan kell telepíteni a Windows To Go a System Center Configuration Manager egy külső meghajtóról indul el, a Windows To Go munkaterület létrehozása."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8eed50f5-80a4-422e-8aa6-a7ccb2171475
caps.latest.revision: 8
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 1a4a9da88caba55d9e340c7fb1f31f4e3b957f3e
ms.openlocfilehash: a8b1a42c43438553cfbb62328bed933378bb344c
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="deploy-windows-to-go-with-system-center-configuration-manager"></a>A Windows to Go és a System Center Configuration Manager központi telepítése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ez a témakör a Windows To Go a System Center Configuration Managerben kiépítésének lépéseit. A Windows To Go a Windows 8 rendszer vállalati felhasználásra szánt szolgáltatása, amellyel a Windows 7 és a Windows 8 minősítési követelményeinek megfelelő számítógépeken az operációs rendszertől függetlenül külső USB-meghajtóról indítható munkaterület hozható létre. A Windows To Go munkaterületek használhatják ugyanazt a lemezképet, amelyet a vállalat a munkaállomásaihoz és a laptopjaihoz használ, és ezekkel azonos módon felügyelhetők.  

 További információ a Windows To Go: [Windows To Go szolgáltatás áttekintése](http://go.microsoft.com/fwlink/p/?LinkId=263433).  

## <a name="provision-windows-to-go"></a>A Windows To Go kiépítése  
 A Windows To Go USB-kapcsolattal csatlakoztatható külső meghajtón tárolt operációs rendszer. A Windows To Go-meghajtó kiépítése többnyire az egyéb operációs rendszerekhez hasonló módon történik. Ugyanakkor a szolgáltatás felhasználó-központú és nagymértékben mobil jellegénél fogva ezen meghajtók kiépítésénél a szokásostól némileg eltérő megközelítést kell alkalmazni.  

 A Windows To Go általánosságban egy kétfázisú rendszernek tekinthető, amely lehetővé teszi a Windows To Go eszköz konfigurálását és a tartalom manuális előkészítését az operációs rendszer számára. Ez minimális hatással van a felhasználó és a felhasználó számítógépén érhet el. A számítógép manuális előkészítése után a kiépítési folyamat végrehajtásával biztosítható, hogy a számítógép készen álljon a használatra. A kiépítési folyamat az aktuális operációs rendszer központi telepítéséhez hasonló módon zajlik. A tartalom manuális előkészítésének és a Windows To Go kiépítésének általános munkafolyamata az alábbi lépésekből áll:  

1.  [A Windows To Go kiépítésének előfeltételei](#BKMK_Prereqs)  

2.  [Manuálisan előkészített adathordozó létrehozása](#BKMK_CreatePrestagedMedia)  

3.  [Windows To Go Creator lemezképkészítő csomag létrehozása](#BKMK_CreatePackage)  

4.  [Feladatütemezés módosítása, hogy engedélyezze a BitLockert a Windows To Go számára](#BKMK_UpdateTaskSequence)  

5.  [A Windows To Go-létrehozó csomag és a feladatütemezés központi telepítése](#BKMK_Deployments)  

6.  [A felhasználó futtathatja a Windows To Go-létrehozót](#BKMK_UserExperience)  

7.  [A Configuration Manager konfigurálja és előkészíti a Windows To Go-meghajtót](#BKMK_ConfigureStageDrive)  

8.  [A felhasználó bejelentkezik a Windows 8-ba](#BKMK_UserLogsIn)  

###  <a name="BKMK_Prereqs"></a> A Windows To Go kiépítésének előfeltételei  
 A Windows To Go kiépítése előtt végre kell hajtania a következő, a Configuration Manager alkalmazásban:  

-   **Rendszerindító lemezkép elküldése egy terjesztési pontra**  

     Az előkészített média létrehozása előtt el kell juttatnia a rendszerindító lemezképet egy terjesztési pontra.  

    > [!NOTE]  
    >  Rendszerindító lemezképek használatával az operációs rendszer telepítése a célszámítógépeken, a Configuration Manager környezetben. A Windows PE rendszernek egy olyan verzióját tartalmazzák, amely telepíti az operációs rendszert, valamint az esetleg szükséges további illesztőprogramokat is. A Configuration Manager két rendszerindító lemezképet biztosít: Egyik x64 támogatásához, x86 platformokat platformokon. Emellett saját rendszerindító lemezképeket is létrehozhat. További információkért lásd: [rendszerindító lemezképek kezelése](../get-started/manage-boot-images.md).  

-   **A Windows 8 operációsrendszer-kép elküldése egy terjesztési pontra**  

     Az előkészített média létrehozása előtt el kell juttatnia a Windows 8 operációsrendszer-képet egy terjesztési pontra.  

    > [!NOTE]  
    >  Az operációsrendszer-lemezképek .WIM formátumú fájlok, amelyek azoknak a referenciafájloknak és -mappáknak a tömörített gyűjteményét tartalmazzák, amelyekre szükség van az operációs rendszer sikeres telepítéséhez a számítógépen. További információkért lásd: [operációsrendszer-lemezképek kezelése](../get-started/manage-operating-system-images.md).  

-   **Feladatütemezés létrehozása a Windows 8 központi telepítéséhez**  

     Létre kell hoznia egy feladatütemezést a Windows 8 központi telepítéséhez, amelyre hivatkozhat a manuálisan előkészített adathordozó létrehozásakor. További információkért lásd: [feladatok automatizálásához a feladatütemezések kezeléséhez](manage-task-sequences-to-automate-tasks.md).  

###  <a name="BKMK_CreatePrestagedMedia"></a> Manuálisan előkészített adathordozó létrehozása  
 A manuálisan előkészített adathordozó tartalmazza a célszámítógép elindításához használt rendszerindító lemezképet és a célszámítógépre alkalmazható operációsrendszer-képet. A manuálisan előkészített médiával kiépített számítógép a rendszerindító lemezképpel indítható. A számítógép ezután futtathat egy meglévő, operációs rendszer központi telepítésére szolgáló feladatütemezést, amellyel egy teljes operációsrendszer-példányt telepíthet. Az operációs rendszert telepítő feladatütemezést az adathordozó nem tartalmazza.  

 Az előkészítési fázisban az operációsrendszer-kép és a rendszerindító lemezkép mellett további tartalmak, például alkalmazások és eszközillesztők is hozzáadhatók. Ez lerövidíti az operációs rendszer központi telepítését, és csökkenti a hálózati forgalmat, hiszen a szükséges tartalom már eleve megtalálható a meghajtón.  

 Manuálisan előkészített adathordozó létrehozásához kövesse az alábbi eljárást.  

#### <a name="to-create-prestaged-media"></a>Manuálisan előkészített adathordozó létrehozása  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Operációs rendszerek**pontot, majd kattintson a **Feladatütemezések**elemre.  

3.  A Feladatütemezési média létrehozása varázsló elindításához kattintson a **Kezdőlap** **Létrehozás** csoportjában található **Feladatütemezési média létrehozása** elemre.  

4.  A **Válassza ki az adathordozó típusát** lapon adja meg az alábbi adatokat, majd kattintson a **Tovább**gombra.  

    -   Válassza a **Manuálisan előkészített média**elemet.  

    -   Jelölje ki az **Operációs rendszer felügyelet nélküli központi telepítésének engedélyezése** beállítást a Windows To Go központi telepítésének felhasználói beavatkozás nélküli elindításához.  

        > [!IMPORTANT]  
        >  Ha ezt a beállítást az SMSTSPreferredAdvertID egyéni változóval együtt használja (lásd az eljárás későbbi részében), nincs szükség felhasználói beavatkozásra, a számítógép pedig automatikusan a Windows To Go központi telepítését indítja el, amikor Windows To Go-meghajtót észlel. Ugyanakkor ha az adathordozó konfigurációja jelszavas védelmet ír elő, a rendszer jelszót kér a felhasználótól. Ha az **Operációs rendszer felügyelet nélküli központi telepítésének engedélyezése** beállítást az SMSTSPreferredAdvertID változó nélkül használja, a feladatütemezés központi telepítésekor hiba történik.  

5.  A **Médiakezelés** lapon adja meg az alábbi adatokat, majd kattintson a **Tovább**gombra.  

    -   Válassza a **Dinamikus média** lehetőséget, ha engedélyezni szeretné, hogy a felügyeleti pontok átirányíthassák más felügyeleti pontokra a tartalmat az ügyfél helyének alapján a hely határain belül.  

    -   Válassza a **Helyalapú média** lehetőséget, ha azt szeretné, hogy a média csak a megadott felügyeleti pontra jusson el.  

6.  A **Média tulajdonságai**  lapon adja meg a következő adatokat, majd kattintson a **Tovább**gombra.  

    -   **Által létrehozott**: Adja meg, hogy ki hozta létre az adathordozót.  

    -   **Verzió**: Adja meg az adathordozó verziószámát.  

    -   **Megjegyzés**: Adja meg az adathordozó felhasználási területének egyedi leírását.  

    -   **Médiafájl**: Adja meg a és a kimeneti fájlok elérési útja. A varázsló erre a helyre írja ki a kimeneti fájlokat. Például:  **\\\servername\folder\outputfile.wim**  

7.  A **Biztonság** lapon adja meg az alábbi adatokat, majd kattintson a **Tovább**gombra.  

    -   Válassza ki **Ismeretlen számítógépek támogatásának engedélyezése** lehetővé teszi az adathordozó számára a Configuration Manager által nem felügyelt számítógépekre telepítse az operációs rendszer számára. Nincs rekord ezekhez a számítógépekhez a Configuration Manager adatbázisába. Az ismeretlen számítógépek a következők:  

        -   Egy számítógép, amelyen nincs telepítve a Configuration Manager-ügyfél  

        -   Olyan számítógép, amely nincs importálva a Configuration Managerbe  

        -   Olyan számítógép, amely nem észlelhető a Configuration Manager által  

    -   Jelölje be a **Média védelme jelszóval** négyzetet, és adjon meg egy erős jelszót az adathordozó jogosulatlan hozzáférés elleni védelméhez. Ha jelszót ad meg, a manuálisan előkészített adathordozó használatához a felhasználónak be kell írnia ezt a jelszót.  

        > [!IMPORTANT]  
        >  Javasoljuk, hogy mindig használjon jelszót a manuálisan előkészített adathordozó védelmére.  

        > [!NOTE]  
        >  Az előkészített adathordozó jelszavas védelme esetén a rendszer akkor is jelszót kér a felhasználótól, ha az adathordozót az **Operációs rendszer felügyelet nélküli központi telepítésének engedélyezése** beállítással konfigurálták.  

    -   A HTTP-kommunikációhoz válassza az **Önaláírt médiatanúsítvány létrehozása**beállítást, majd adja meg a tanúsítvány érvényességének kezdő és záró dátumát.  

    -   A HTTPS-kommunikációhoz válassza a **PKI tanúsítványának importálása**beállítást, majd adja meg az importálandó tanúsítványt és annak jelszavát.  

         További információ a rendszerindító lemezképekhez használt ügyféltanúsítványról: [PKI-tanúsítványkövetelmények](../../core/plan-design/network/pki-certificate-requirements.md).  

    -   **Felhasználó-eszköz kapcsolat**: Felhasználó-központú Felügyelet támogatásához a Configuration Manager alkalmazásban, határozza meg, hogyan rendelje hozzá a felhasználókat a célszámítógéphez az adathordozót. Hogyan támogatja az operációs rendszer központi telepítése a felhasználó-eszköz kapcsolat kapcsolatos további információkért lásd: [rendelje hozzá a felhasználókat a célszámítógéppel](../get-started/associate-users-with-a-destination-computer.md).  

        -   Válassza az **Automatikus jóváhagyással engedélyezze a felhasználó-eszköz kapcsolatot** lehetőséget, ha azt szeretné, hogy a média automatikusan rendelje hozzá a felhasználókat a célszámítógéphez. Ez a funkció az operációs rendszert telepítő feladatütemezés műveletein alapul. Ebben az esetben a feladatütemezés akkor hozza létre a kapcsolatot a megadott felhasználók és a célszámítógép között, amikor telepíti az operációs rendszert a célszámítógépre.  

        -   Válassza **A rendszergazda jóváhagyásától függően engedélyezze a felhasználó-eszköz kapcsolatot** lehetőséget, ha azt szeretné, hogy a média az engedély megadása után rendelje hozzá a felhasználókat a célszámítógéphez. Ez a funkció az operációs rendszert telepítő feladatütemezés hatókörén alapul. Ebben az esetben a feladatütemezés létrehozza a kapcsolatot a megadott felhasználók és a célszámítógép között, de az operációs rendszer telepítése előtt megvárja a rendszergazdai jóváhagyást.  

        -   Válassza a **Ne engedélyezze a felhasználó-eszköz kapcsolatot** lehetőséget, ha azt szeretné, hogy a média ne rendelje hozzá a felhasználókat a célszámítógéphez. Ebben az esetben a feladatütemezés nem rendeli hozzá a felhasználókat a célszámítógéphez, amikor telepíti az operációs rendszert.  

8.  A **Feladatütemezés** lapon adja meg az előző szakaszban létrehozott Windows 8-feladatütemezést.  

9. A **Rendszerindító lemezkép** lapon adja meg a következő adatokat, majd kattintson a **Tovább**gombra.  

    > [!IMPORTANT]  
    >  A terjesztett rendszerindító lemezkép architektúrájának meg kell felelnie a célszámítógép architektúrájának. Az x64 rendszerű célszámítógépek például elindíthatók és működtethetők x86 vagy x64 rendszerindító lemezképpel is. Az x86 rendszerű célszámítógépek elindításához és működtetéséhez azonban csak x86 rendszerindító lemezkép használható. EFI üzemmódban működő minősített Windows 8-as számítógépek esetén x64-alapú rendszerindító lemezképet kell használnia.  

    -   **Rendszerindító lemezkép**: Adja meg a rendszerindító lemezképet a célszámítógép indításához.  

    -   **Terjesztési pont**: Adja meg a terjesztési pontot, amelyen a rendszerindító lemezkép. A varázsló lekéri a rendszerindító lemezképet a terjesztési pontról, és a médiára írja azt.  

        > [!NOTE]  
        >  A rendszergazdának **Olvasás** hozzáférési jogosultsággal kell rendelkeznie a terjesztési ponton lévő rendszerindító lemezkép tartalmához. További információkért lásd: [tartalom eléréséhez fiókok kezelése](../../core/plan-design/hierarchy/manage-accounts-to-access-content.md).  

    -   Ha a varázsló **Médiakezelés** lapján a **Helyalapú média** beállítást választotta, adjon meg egy elsődleges helyhez tartozó felügyeleti pontot a **Felügyeleti pont** mezőben.  

    -   Ha a varázsló **Médiakezelés** lapján a **Dinamikus média** beállítást választotta, a **Társított felügyeleti pontok** mezőben adja meg a elsődleges helyhez tartozó felügyeleti pontokat, amelyeket használni szeretne, illetve a kívánt rangsort a kezdeti kommunikációhoz.  

10. A **Lemezképek** lapon adja meg az alábbi adatokat, majd kattintson a **Tovább**gombra.  

    -   **Lemezképcsomag**: Adja meg a Windows 8 operációs rendszer lemezképét tartalmazó csomagot.  

    -   **Lemezképindex**: Adja meg a lemezkép központi telepítéséhez, ha a csomag több operációs rendszeri lemezképet tartalmazza.  

    -   **Terjesztési pont**: Adja meg a terjesztési pontot, amelyen az operációs rendszer lemezképének csomagját. A varázsló lekéri az operációs rendszer lemezképét a terjesztési pontról, és az adathordozóra írja azt.  

        > [!NOTE]  
        >  A rendszergazdának **Olvasás** hozzáférési jogosultsággal kell rendelkeznie a terjesztési ponton lévő operációsrendszer-kép tartalmához. További információkért lásd: [tartalom eléréséhez fiókok kezelése](../../core/plan-design/hierarchy/manage-accounts-to-access-content.md).  

11. Az **Alkalmazás kijelölése** lapon jelölje ki az adathordozófájlba felvenni kívánt alkalmazástartalmat, majd kattintson a **Tovább**gombra.  

12. A **Csomag kiválasztása** lapon jelölje ki az adathordozófájlba felvenni további csomagtartalmat, majd kattintson a **Tovább**gombra.  

13. Az **Illesztőprogram-csomag kiválasztása** lapon jelölje ki az adathordozófájlba felvenni illesztőprogram-csomag tartalmát, majd kattintson a **Tovább**gombra.  

14. A **Terjesztési pontok** oldalon válasszon ki egy vagy több olyan terjesztési pontot, amelynél megtalálható a feladatütemezéshez szükséges tartalom, majd kattintson a **Tovább**gombra.  

15. A **Testreszabás** lapon adja meg a következő adatokat, majd kattintson a **Tovább**gombra.  

    -   **Változók**: Adja meg a feladatütemezés által az operációs rendszer telepítéséhez használt változókat. Windows To Go esetén a Windows To Go-példány automatikus kiválasztásához használja az SMSTSPreferredAdvertID változót a következő formátumban:  

         SMSTSPreferredAdvertID = {*DeploymentID*}, ahol a DeploymentID a Windows To Go-meghajtó kiépítési folyamatához használni kívánt feladatütemezés központi telepítési azonosítója.  

        > [!TIP]  
        >  Ha ezt a változót egy felügyelet nélküli futtatásra beállított feladatütemezéssel használja (lásd az eljárás korábbi részében), nincs szükség felhasználói beavatkozásra, a számítógép pedig automatikusan a Windows To Go központi telepítését indítja el, amikor Windows To Go-meghajtót észlel. Ugyanakkor ha az adathordozó konfigurációja jelszavas védelmet ír elő, a rendszer jelszót kér a felhasználótól.  

    -   **Indítás előtti parancsok**: Adja meg a feladatütemezés futtatása előtt futtatandó előindítási parancsokat. Az indítás előtti parancs olyan parancsfájl vagy végrehajtható fájl, amely a Windows PE környezetben képes interakciót folytatni a felhasználóval a feladatütemezés futtatása és az operációs rendszer telepítése előtt. Windows To Go központi telepítése esetén a következőket konfigurálja:  

        -   **OSDBitLockerPIN**: A Windows To Go esetén a BitLocker használatához jelszó szükséges. Egy indítás előtti parancs részeként állítsa be az **OSDBitLockerPIN** változót a Windows To Go-meghajtóhoz tartozó BitLocker-jelszó megadásához.  

            > [!WARNING]  
            >  Miután engedélyezte a BitLocker jelszavas védelmét, a felhasználónak minden alkalommal meg kell adnia a jelszót, amikor a számítógép a Windows To Go-meghajtóval indul el.  

        -   **SMSTSUDAUsers**: A célszámítógép elsődleges felhasználójának megadására szolgál. Ezzel a változóval gyűjtse össze a felhasználó nevét, amely azután a felhasználó és az eszköz társítására használható. További információkért lásd: [rendelje hozzá a felhasználókat a célszámítógéppel](../get-started/associate-users-with-a-destination-computer.md).  

            > [!TIP]  
            >  A felhasználónév lekéréséhez beviteli mezőt hozhat létre az indítás előtti parancs keretében, kérheti a felhasználótól a felhasználónév beírását, majd beállíthatja az értéket a változóhoz. Felveheti például a következő sorokat az indítás előtti parancsfájlba:  
            >   
            >  `UserID = inputbox("Enter Username" ,"Enter your username:","",400,0)`  
            >   
            >  `env("SMSTSUDAUsers") = UserID`  

         További információ az indítás előtti parancsként használandó parancsfájl létrehozásáról lásd: [indítás előtti parancsok feladatütemezési médiához](../understand/prestart-commands-for-task-sequence-media.md).  

16. Fejezze be a varázslót.  

    > [!NOTE]  
    >  A varázsló számára hosszabb időbe telhet létrehozni az előkészített adathordozófájlt.  

###  <a name="BKMK_CreatePackage"></a> Windows To Go Creator lemezképkészítő csomag létrehozása  
 A Windows To Go központi telepítése keretében létre kell hoznia egy csomagot az előkészített adathordozófájl telepítéséhez. A csomagnak tartalmaznia kell azt az eszközt, amely a Windows To Go-meghajtó konfigurálását végzi, és kibontja az előkészített adathordozót a meghajtóra. A Windows To Go Creator lemezképkészítő csomag létrehozásához kövesse az alábbi eljárást.  

#### <a name="to-create-the-windows-to-go-creator-package"></a>A Windows To Go Creator lemezképkészítő csomag létrehozása  

1.  A Windows To Go Creator lemezképkészítő csomagfájljait tartalmazó kiszolgálón hozzon létre egy forrásmappát a csomag forrásfájljai számára.  

    > [!NOTE]  
    >  A helykiszolgáló számítógépfiókjának **Olvasás** hozzáférési jogosultságokkal kell rendelkeznie a forrásmappához.  

2.  Másolja a [Create prestaged media](#BKMK_CreatePrestagedMedia) szakaszban létrehozott előkészített adathordozófájlt a csomag forrásmappájába.  

3.  Másolja a Windows To Go Creator eszközt (WTGCreator.exe) a csomag forrásmappájába. A creator eszköz elérhető bármely elsődleges helykiszolgálón a következő helyen: <*Configmgrtelepítésimappa*> \OSD\Tools\WTG\Creator.  

4.  Hozzon létre egy csomagot és programot a Csomag és program létrehozása varázslóval.  

5.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

6.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Alkalmazáskezelés**pontot, majd kattintson a **Csomagok**elemre.  

7.  A **Kezdőlap** **Létrehozás** csoportjában kattintson a **Csomag létrehozása**lehetőségre.  

8.  A **Csomag** lapon adja meg a csomag nevét és leírását. A csomagnak adja például a **Windows To Go** nevet, a csomag leírásaként pedig adja meg a következőt: **Package to configure a Windows To Go drive using System Center Configuration Manager** .  

9. Jelölje be az **Ez a csomag forrásfájlokat tartalmaz**négyzetet, adja meg az 1. lépésben a csomag számára létrehozott forrásmappa elérési útját, majd kattintson a **Tovább**gombra.  

10. A **Program típusa** lapon válassza a **Normál program**lehetőséget, majd kattintson a **Tovább**gombra.  

11. A **Normál program** lapon adja meg az alábbi beállításokat:  

    -   **Név**: Adja meg a program nevét. Például adja a programnak a **Creator** nevet.  

    -   **Parancssori**: Típus **WTGCreator.exe /wim:elokeszitettadathordozoneve.wim**, ahol az "elokeszitettadathordozoneve" létrehozott és a csomag forrásmappáját a Windows To Go Creator csomag másolja a manuálisan előkészített fájl neve.  

         Igény szerint a következő beállításokat is használhatja:  

        -   **enableBootRedirect**: parancssori kapcsoló a Windows To Go indítási beállításainak módosítására a rendszerindítás átirányításához. A kapcsoló használata esetén a számítógép az USB-meghajtóról fogja indítani a rendszert anélkül, hogy ehhez módosítani kellene a rendszerindítási sorrendet a számítógép firmverében, vagy a felhasználónak az indításkor választania kellene a rendszerindítási lehetőségek listájából. Ha a számítógép Windows To Go-meghajtót észlel, arról fog elindulni a rendszer.  

    -   **Futtatás**: Adja meg **normál** futtatni a programot, a rendszer és a program alapértelmezett értékei alapján.  

    -   **A program futtatható**: Adja meg a program futtatható-e csak amikor van bejelentkezett felhasználó.  

    -   **Futtatási mód**: Adja meg, hogy a program elindul-e a bejelentkezett felhasználó engedélyeivel vagy rendszergazdai engedélyekkel. A Windows To Go Creator futtatásához emelt szintű engedélyek szükségesek.  

    -   Jelölje be **A programtelepítés megtekintésének és módosításának engedélyezése a felhasználók számára**négyzetet, majd kattintson a **Tovább**gombra.  

12. A Követelmények lapon adja meg az alábbi beállításokat:  

    -   **Platform-követelmények**: Válassza ki a megfelelő Windows 8-platformokat a kiépítéshez.  

    -   **Becsült lemezterület**: Adja meg a Windows To Go Creator csomag forrásmappájának méretét.  

    -   **Maximálisan engedélyezett futási idő (perc)**: Adja meg a program az ügyfélszámítógépen futtassa várható maximális idejét. Az alapérték 120 perc.  

        > [!IMPORTANT]  
        >  Ha karbantartási időszakokat alkalmaz arra a gyűjteményre, amelyen a program fut, ütközést okozhat, ha a **Maximálisan engedélyezett futási idő** hosszabb az ütemezett karbantartási időszaknál. Ha a maximálisan engedélyezett futási idő értéke **Ismeretlen**, akkor a program elindul a karbantartási időszak alatt, de az időszak vége után is tovább fut, amíg be nem fejeződik vagy sikertelenség miatt le nem áll. Ha a maximálisan engedélyezett futási idő értéke egy meghatározott időszak (nem ismeretlenre van állítva), amely hosszabb minden rendelkezésre álló karbantartási időszaknál, akkor a program nem fog futni.  

        > [!NOTE]  
        >  Ha a változó értéke **ismeretlen**, a Configuration Manager állítja a maximálisan engedélyezett futási időt 12 órára (720 percre).  

        > [!NOTE]  
        >  Ha az túllépi a maximálisan engedélyezett futási időt (akár a felhasználó által vagy az alapértelmezett érték), a Configuration Manager leállítja a programot, ha **Futtatás rendszergazdai jogosultságokkal** van kiválasztva és **felhasználók megtekintése és a program telepítésébe való beavatkozást** nincs bejelölve a a **normál Program** lap.  

     Kattintson a **Tovább** gombra, és fejezze be a varázslót.  

###  <a name="BKMK_UpdateTaskSequence"></a> Feladatütemezés módosítása, hogy engedélyezze a BitLockert a Windows To Go számára  
 A Windows To Go a platformmegbízhatósági modul (TPM) nélkül engedélyezi a BitLocker titkosítást a rendszerindításra alkalmas külső meghajtón. Ezért egy külön eszközzel kell beállítani a BitLocker használatát a Windows To Go-meghajtón. A BitLocker engedélyezéséhez fel kell venni egy műveletet a feladatütemezésbe a **Windows és ConfigMgr beállítása** lépés után.  

> [!NOTE]  
>  A Windows To Go esetén a BitLocker használatához jelszó szükséges. A jelszót a [Create prestaged media](#BKMK_CreatePrestagedMedia) lépésben lehet beállítani, egy indítás előtti paranccsal, az OSDBitLockerPIN változó segítségével.  

 Az alábbi eljárás szerint módosíthatja a Windows 8 feladatütemezést, hogy engedélyezze a BitLockert a Windows To Go számára.  

#### <a name="to-update-the-windows-8-task-sequence-to-enable-bitlocker"></a>A Windows 8-feladatütemezés módosítása a BitLocker engedélyezése érdekében  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Alkalmazáskezelés**pontot, majd kattintson a **Csomagok**elemre.  

3.  A **Kezdőlap** **Létrehozás** csoportjában kattintson a **Csomag létrehozása**lehetőségre.  

4.  A **Csomag** lapon adja meg a csomag nevét és leírását. A csomagnak adja például a **BitLocker for Windows To Go** nevet, a csomag leírásaként pedig adja meg a következőt: **Package to update BitLocker for Windows To Go** .  

5.  Jelölje be az **Ez a csomag forrásfájlokat tartalmaz**beállítást, adja meg a Windows To Go-hoz szükséges BitLocker eszköz helyét, majd kattintson a **Tovább**gombra. A BitLocker eszköz érhető el semmilyen Configuration Manager elsődleges hely kiszolgálóján a következő helyen: <*Configmgrtelepítésimappa*> \OSD\Tools\WTG\BitLocker\  

6.  A **Program típusa** lapon jelölje be a **Ne hozzon létre programot**lehetőséget.  

7.  Kattintson a **Tovább** gombra, és fejezze be a varázslót.  

8.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

9. A **Szoftverkönyvtár** munkaterületen bontsa ki az **Operációs rendszerek**pontot, majd kattintson a **Feladatütemezések**elemre.  

10. Jelölje ki a Windows 8 feladatütemezést, amelyet a manuálisan előkészített média számára megadott.  

11. A **Kezdőlap** **Feladatütemezés** csoportjában kattintson a **Szerkesztés**elemre.  

12. Kattintson a **Windows és ConfigMgr beállítása** lépésre, a **Hozzáadás**gombra, az **Általános**lehetőségre, majd a **Parancssor futtatása**elemre. A Parancssor futtatása lépés megjelenik a Windows és ConfigMgr beállítása lépés után.  

13. A **Parancssor futtatása lépés** lépéshez tartozó **Tulajdonságok** lapon adja meg a következőket:  

    1.  **Név**: Adjon meg egy nevet a parancssor például **engedélyezi a BitLocker a Windows To Go**.  

    2.  **Parancssori**: i386\osdbitlocker_wtg.exe/enable/pwd: < *nincs &#124; AD*>  

         Paraméterek:  

        -   / pwd: < none &#124; AD > – adja meg a BitLocker-jelszó helyreállítási módját. Ez a paraméter kötelező, ha a parancssorban megadja az /Enable paramétert.  

             Válassza az **AD** értéket, hogy a BitLocker meghajtótitkosítás biztonsági másolatot készítsen a BitLocker által védett meghajtók helyreállítási információiról az Active Directory (AD) tartományi szolgáltatásokban. Ha biztonsági mentés készül a BitLocker által védett meghajtók helyreállítási jelszavairól, akkor a rendszergazda felhasználók helyre tudják állítani a zárolt meghajtókat. Így a jogosult felhasználók mindig hozzáférhetnek a vállalat titkosított adataihoz. Ha a **None**(Nincs) értéket választja, akkor a felhasználónak kell megőrizni a helyreállítási jelszót vagy helyreállítási kulcsot. Ha ez az információ elvész, vagy a felhasználó nem fejti vissza a meghajtót, mielőtt kilépne a szervezetből, akkor a rendszergazdák nem tudnak egyszerűen hozzáférni a meghajtóhoz.  

        -   / wait: < TRUE &#124; FALSE > – adja meg, hogy a feladatütemezés megvárja-e a titkosítás befejezését, mielőtt ő maga befejeződne.  

    3.  Jelölje be a **Csomag**lehetőséget, azután adja meg azt a csomagot, amelyet az eljárás elején hozott létre.  

    4.  A **Beállítások** lapon adja meg az alábbi feltételeket:  

        -   Feltétel = Feladatütemezési változó  

        -   Változó = _SMSTSWTG  

        -   Feltétel = Egyenlő  

        -   Érték = Igaz  

    > [!NOTE]  
    >  Ilyenkor nincs szükség a **BitLocker engedélyezése** lépésre, amely valószínűleg az új parancssori lépés után következik, mivel nem az engedélyezi a BitLockert a Windows To Go számára. Mindazonáltal megmaradhat ez a lépés a feladatütemezésben az olyan Windows 8 telepítésekhez, amelyek nem használnak Windows To Go-meghajtót.  

###  <a name="BKMK_Deployments"></a> A Windows To Go-létrehozó csomag és a feladatütemezés központi telepítése  
 A Windows To Go egy hibrid telepítési folyamat. Ezért van szükség a Windows To Go-létrehozó csomag és a Windows 8 feladatütemezés központi telepítésére. Az alábbi eljárás szerint végezheti el a központi telepítést.  

#### <a name="to-deploy-the-windows-to-go-creator-package"></a>A Windows To Go-létrehozó csomag központi telepítése  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Alkalmazáskezelés**pontot, majd kattintson a **Csomagok**elemre.  

3.  Jelölje ki a Windows To Go-csomagot, amelyet a [Windows To Go Creator lemezképkészítő csomag létrehozása](#BKMK_CreatePackage) lépésben állított össze.  

4.  A **Kezdőlap** **Telepítés** csoportjában kattintson a **Telepítés**elemre.  

5.  Az **Általános** lapon adja meg a következő beállításokat:  

    1.  **Szoftver**: Győződjön meg arról, hogy a Windows To Go-csomag van kiválasztva.  

    2.  **Gyűjtemény**: Kattintson a **Tallózás** kattintva kiválaszthatja azt a kívánt központi telepítése a Windows To Go-csomagot.  

    3.  **A gyűjteményhez társított alapértelmezett terjesztésipont-csoportok használata**: Válassza ezt a lehetőséget, ha a csomag tartalmát a gyűjtemény alapértelmezett terjesztésipont-csoport tárolni szeretné. Ha a kiválasztott gyűjteményhez nincs hozzárendelve alapértelmezett terjesztésipont-csoport, akkor ez a beállítás nem érhető el.  

6.  A **Tartalom** lapon kattintson a **Hozzáadás** gombra, és jelölje ki azokat a terjesztési pontokat vagy terjesztésipont-csoportokat, amelyekre terjeszteni szeretné a csomaghoz és a programhoz kapcsolódó tartalmat.  

7.  A **Központi telepítési beállítások** lapon a központi telepítési típusaként válassza az **Elérhető** értéket, majd kattintson a **Tovább**gombra.  

8.  Az **Ütemezés**lapon állítsa be, mikor kell telepíteni vagy elérhetővé tenni az ügyféleszközök számára az adott csomagot és programot.  

     Az ezen a lapon elérhető beállítások attól függően eltérőek, hogy a központi telepítés céljának beállítása **Elérhető** vagy **Kötelező**.  

9. Az **Ütemezés**lapon adja meg a következő beállításokat, majd kattintson a **Tovább**gombra.  

    1.  **A központi telepítés elérhetővé válásának ütemezése**: Adja meg azt a dátumot és időpontot, amikor a csomag és program érhető el a célszámítógépen futtatni. Ha az **UTC**beállítást választja, akkor a célszámítógépek ugyanakkor érhetik el a csomagot és a programot, nem pedig különböző időpontokban, a célszámítógépek helyi ideje szerint.  

    2.  **A központi telepítés lejáratának ütemezése**: Adja meg azt a dátumot és időpontot, amikor a csomag és program érvényessége lejár, a célszámítógépen. Ha az **UTC**beállítást választja, akkor a feladatütemezés ugyanakkor jár le a célszámítógépeken, nem pedig különböző időpontokban, a célszámítógépek helyi ideje szerint.  

10. A varázsló **Felhasználói élmény** lapján adja meg a következő adatokat:  

    -   **Szoftvertelepítés**: Lehetővé teszi, hogy a szoftver telepítése a beállított karbantartási időszakokon kívül történjen.  

    -   **Rendszer újraindítása (Ha a telepítés befejezéséhez szükséges)**: Lehetővé teszi, hogy az eszköz újraindítása, ha a Szoftvertelepítés miatt szükség van a beállított karbantartási időszakokon kívül.  

    -   **Embedded-eszközök**: Ha írási szűrőket használó Windows Embedded-eszközökre, amelyek telepít, megadhatja, hogy a csomagok és programok az ideiglenes rétegen történjen, és a véglegesítési később a változtatásokat, illetve hogy a változások véglegesítése a telepítési határidő lejártakor vagy karbantartási időszak alatt történjen. Ha a változtatásokat a telepítési határidő lejártakor vagy karbantartási időszakban véglegesíti, újraindításra van szükség, és a változtatások megmaradnak az eszközön.  

11. A **Terjesztési pontok** lapon adja meg a következő adatokat:  

    -   **Központi telepítési beállítások:** Adja meg **tartalom letöltése a terjesztési pontról és Futtatás helyben**.  

    -   **Engedélyezése az ügyfelek számára az azonos alhálózatban lévő más ügyfelekkel tartalmat osszanak**: A beállítással úgy csökkenthető a hálózat terhelése így az ügyfelek egyéb ügyfelekről, amelyek már letöltötték és gyorsítótárba helyezték a tartalmat a hálózaton. Ez a beállítás a Windows BranchCache szolgáltatást használja, és Windows Vista SP2 vagy újabb operációs rendszerű számítógépeken használható.  

    -   **Minden ügyfél számára a tartalék forráshely használatát a tartalomhoz**: Adja meg, hogy az ügyfelek tartalék forráshelyeként használják a nem előnyben részesített terjesztési pontok a tartalom esetén a tartalom nem érhető el egy előnyben részesített terjesztési ponton.  

12. Fejezze be a varázslót.  

#### <a name="to-deploy-the-windows-8-task-sequence"></a>A Windows 8 feladatütemezés központi telepítése  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Operációs rendszerek**pontot, majd kattintson a **Feladatütemezések**elemre.  

3.  Válassza ki [Prerequisites to provision Windows To Go](#BKMK_Prereqs) lépésben létrehozott Windows 8 feladatütemezést.  

4.  A **Kezdőlap** **Telepítés** csoportjában kattintson a **Telepítés**elemre.  

5.  Az **Általános** lapon adja meg a következő beállításokat:  

    1.  **Feladatütemezés**: Győződjön meg arról, hogy a Windows 8 feladatütemezés van kiválasztva.  

    2.  **Gyűjtemény**: Kattintson a **Tallózás** való válassza ki a gyűjteményt, amelyre a felhasználó telepíteni szeretne a Windows To Go minden eszközt magában foglal.  

        > [!IMPORTANT]  
        >  Ha a [Create prestaged media](#BKMK_CreatePrestagedMedia) lépésben elkészített adathordozó használja az SMSTSPreferredAdvertID változót, akkor a feladatütemezést telepítheti a **Minden rendszer** gyűjteményre, és megadhatja a **Csak Windows PE (rejtett)** beállítást a **Tartalom** lapon. Mivel a feladatütemezés rejtett, csak az adathordozó számára lesz elérhető.  

    3.  **A gyűjteményhez társított alapértelmezett terjesztésipont-csoportok használata**: Válassza ezt a lehetőséget, ha a csomag tartalmát a gyűjtemény alapértelmezett terjesztésipont-csoport tárolni szeretné. Ha a kiválasztott gyűjteményhez nincs hozzárendelve alapértelmezett terjesztésipont-csoport, akkor ez a beállítás nem érhető el.  

6.  A **Központi telepítési beállítások** lapon adja meg a következőket, majd kattintson a **Tovább**gombra.  

    -   **Cél**: Válassza ki **elérhető**. Ha egy felhasználó számára telepíti a feladatütemezést, akkor a felhasználó megkeresheti a feladatütemezést az alkalmazáskatalógusban, és szükség esetén kérheti. Ha egy eszköz számára telepíti a feladatütemezést, akkor a felhasználó megkeresheti a feladatütemezést a szoftverközpontban, és igény szerint telepítheti.  

    -   **Elérhetővé tétel a következők**: Adja meg, hogy a feladatütemezés a Configuration Manager ügyfelek, az adathordozók vagy a PXE számára elérhető.  

        > [!IMPORTANT]  
        >  Feladatütemezések automatizált központi telepítése esetén használja a **Csak média és PXE (rejtett)** beállítást. Ha bejelöli az **Operációs rendszer felügyelet nélküli központi telepítésének engedélyezése** lehetőséget, és beállítja az SMSTSPreferredAdvertID változót a manuálisan előkészített média számára, akkor a számítógép automatikusan a Windows To Go-telepítéssel végez rendszerindítást, ha észleli a Windows To Go-meghajtót. A manuálisan előkészített média beállításairól további információk találhatók a [Create prestaged media](#BKMK_CreatePrestagedMedia) című részben.  

7.  Az **Ütemezés** lapon adja meg a következő beállításokat, majd kattintson a **Tovább**gombra.  

    1.  **A központi telepítés elérhetővé válásának ütemezése**: Adja meg, a dátumot és időpontot, amikor a feladatütemezés a célszámítógépen futtatható. Ha az **UTC**beállítást választja, akkor a célszámítógépek ugyanakkor érhetik el a feladatütemezést, nem pedig különböző időpontokban, a célszámítógépek helyi ideje szerint.  

    2.  **A központi telepítés lejáratának ütemezése**: Adja meg a dátum és idő, amikor a feladatütemezés érvényessége lejár a célszámítógépen. Ha az **UTC**beállítást választja, akkor a feladatütemezés ugyanakkor jár le a célszámítógépeken, nem pedig különböző időpontokban, a célszámítógépek helyi ideje szerint.  

8.  A **Felhasználói élmény** lapon adja meg a következő adatokat:  

    -   **Feladatütemezés előrehaladásának megjelenítése**: Adja meg, hogy a Configuration Manager-ügyfél a feladatütemezés végrehajtását jeleníti meg.  

    -   **Szoftvertelepítés**: Adja meg, hogy a felhasználó számára az ütemezett időpont után telepítse a szoftvert a konfigurált karbantartási időszakon kívül.  

    -   **Rendszer újraindítása (Ha a telepítés befejezéséhez szükséges)**: Lehetővé teszi, hogy az eszköz újraindítása, ha a Szoftvertelepítés miatt szükség van a beállított karbantartási időszakokon kívül.  

    -   **Embedded-eszközök**: Ha írási szűrőket használó Windows Embedded-eszközökre, amelyek telepít, megadhatja, hogy a csomagok és programok az ideiglenes rétegen történjen, és a véglegesítési később a változtatásokat, illetve hogy a változások véglegesítése a telepítési határidő lejártakor vagy karbantartási időszak alatt történjen. Ha a változtatásokat a telepítési határidő lejártakor vagy karbantartási időszakban véglegesíti, újraindításra van szükség, és a változtatások megmaradnak az eszközön.  

    -   **Internetalapú ügyfelek**: Adja meg, hogy a feladatütemezés futhat egy Internet-alapú ügyfélen. Ez a beállítás nem használható olyan műveletek esetén, amelyek valamilyen szoftvert, például operációs rendszert telepítenek. Ezt a beállítást csak általános parancsfájlalapú feladatütemezésekhez használja, amelyek a szabványos operációs rendszerben végeznek műveleteket.  

9. A **Riasztások** lapon adja meg a feladatütemezés telepítésére vonatkozó riasztási beállításokat, majd kattintson a **Tovább**gombra.  

10. A **Terjesztési pontok** lapon adja meg a következő adatokat, majd kattintson a **Tovább**gombra.  

    -   **Telepítési lehetőségek**: Válassza ki **töltse le a tartalom helyileg, ha a futó feladatütemezés igényli**.  

    -   **Nincs helyi terjesztési pont nem érhető el, használjon távoli terjesztési pontot**: Adja meg, hogy használhatja-e az ügyfelek a feladatütemezés által igényelt tartalom letöltéséhez lassú és megbízhatatlan hálózatokon lévő terjesztési pontokra.  

    -   **Az ügyfelek számára a tartalom tartalék forráshelyének engedélyezése**:
        - *1610-es vagy korábbi*, kiválaszthatja, hogy a tartalék forráshely engedélyezése a tartalom jelölőnégyzetet forráshelyként, a terjesztési pontokat használják a forráshely tartalom Ha más terjesztési pontok nem érhetők el ezen határcsoportokon kívüli ügyfelek számára.
        - *Verziójától 1610*, már nem konfigurálható **tartalék forráshely engedélyezése a tartalom**.  Ehelyett konfigurálnia a határcsoportokat, amelyek meghatározzák, amikor egy ügyfél akkor kezdhető meg egy érvényes tartalomforrás helye további határcsoportjainak kereséséhez közötti kapcsolatokat. 

11. Fejezze be a varázslót.  

###  <a name="BKMK_UserExperience"></a> A felhasználó futtathatja a Windows To Go-létrehozót  
 Miután befejeződött a Windows To Go-csomag és a Windows 8 feladatütemezés telepítése, a Windows To Go-létrehozó elérhetővé válik a felhasználó számára. A felhasználó megnyithatja a szoftverkatalógust, vagy ha a Windows To Go-létrehozót eszközök számára telepítették, akkor a szoftverközpontot, és futtathatja a Windows To Go-létrehozó programot. Amikor a létrehozó csomag letöltése befejeződött, a tálcán megjelenik egy villogó ikon. Ha a felhasználó az ikonra kattint, megnyílik egy párbeszédpanel, amelyben ki lehet választani a Windows To Go-meghajtót (kivéve ha megadták a /drive parancssori beállítást). Ha a meghajtó nem fele meg a Windows To Go követelményeinek, vagy a meghajtón nincs elég szabad hely a lemezkép telepítéséhez, akkor a létrehozó program egy hibaüzenetet ad. A felhasználó ellenőrizheti a meghajtót és az alkalmazandó lemezképet a jóváhagyást kérő lapon. Mialatt a létrehozó konfigurálja és előkészíti a tartalmat a Windows To Go-meghajtóra, megjelenik a folyamatjelző párbeszédpanel. Az előkészítés végeztével megjelenik egy üzenet arról, hogy újra kell indítani a számítógépet a Windows To Go-meghajtóról.  

> [!NOTE]  
>  Ha a [Create a Windows To Go Creator package](#BKMK_CreatePackage) során nem engedélyezték a rendszerindítás átirányítását a létrehozó programhoz tartozó parancssorban, akkor előfordulhat, hogy a felhasználónak kell manuálisan újraindítania a számítógépet a Windows To Go-meghajtóról minden újraindítás alkalmával.  

###  <a name="BKMK_ConfigureStageDrive"></a> A Configuration Manager konfigurálja és előkészíti a Windows To Go-meghajtót  
 Miután a számítógép újraindult a Windows To Go-meghajtóról, a meghajtó betölti a Windows PE környezetet, és csatlakozik a felügyeleti ponthoz, hogy lekérje a házirendet, és befejezhesse az operációs rendszer központi telepítését. A Configuration Manager konfigurálja, és előkészíti a meghajtót. Miután a Configuration Manager előkészíti a meghajtót, a felhasználó újraindíthatja a számítógépet, hogy véglegesítse a telepítési folyamatot (például egy tartományhoz való csatlakozás vagy alkalmazások telepítése). Ez a folyamat minden manuálisan előkészített média esetében azonos.  

###  <a name="BKMK_UserLogsIn"></a> A felhasználó bejelentkezik a Windows 8-ba  
 A Configuration Manager a telepítési folyamat befejeződik, és a Windows 8 zárolási képernyő jelenik meg, miután a felhasználó bejelentkezhet az operációs rendszer.  

