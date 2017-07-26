---
title: "Hozzon létre egy feladatütemezést az operációs rendszer telepítéséhez |} Microsoft Docs"
description: "Feladatütemezések használatával a System Center Configuration Manager automatikusan telepíti az operációs rendszer lemezképét és egyéb olyan tartalmat, a célszámítógépen."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 217c8a0e-5112-420e-a325-2a6d75326290
caps.latest.revision: 13
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: 41aa6cf69a746f0ab67d804f1ee0c70db05d65ee
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="create-a-task-sequence-to-install-an-operating-system-in-system-center-configuration-manager"></a>Feladatütemezés létrehozása operációs rendszer telepítéséhez a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Feladatütemezések használatával a System Center Configuration Manager automatikusan telepíti az operációs rendszer lemezképének a célszámítógépen. Olyan feladatütemezést kell létrehoznia, amely hivatkozik a célszámítógép indításához használt rendszerindító lemezképre, a célszámítógépen telepíteni kívánt operációsrendszer-lemezképre, valamint a telepíteni kívánt esetleges egyéb tartalmakra, például más alkalmazásokra vagy szoftverfrissítésekre. Ezután telepítse központilag a feladatütemezést egy, a célszámítógépet tartalmazó gyűjteménybe.  

##  <a name="BKMK_InstallOS"></a> Feladatütemezés létrehozása egy operációs rendszer telepítéséhez  
 Az operációs rendszerek telepítése számos forgatókönyv szerint végezhető a környezetében. A legtöbb esetben létrehoz egy feladatütemezést, és bejelöli a **Meglévő lemezképcsomag telepítése** választógombot a Feladatütemezés létrehozása varázslóban az operációs rendszer, a szoftverfrissítések és alkalmazások telepítéséhez, valamint a felhasználói beállítások áttelepítéséhez. Mielőtt feladatütemezést hozna létre az operációs rendszer telepítéséhez, az alábbiakról kell gondoskodni:   

-   **Kötelező**  

    -   A [rendszerindító lemezkép](../get-started/manage-boot-images.md) a Configuration Manager konzol elérhetőnek kell lennie.  

    -   Egy [operációsrendszer-lemezkép](../get-started/manage-operating-system-images.md) a Configuration Manager konzol elérhetőnek kell lennie.  

-   **Kötelező (használat esetén)**  

    -   [Szoftverfrissítések](../../sum/get-started/synchronize-software-updates.md) szinkronizálni kell a Configuration Manager konzolon.  

    -   [Alkalmazások](../../apps/deploy-use/create-applications.md) fel kell venni a Configuration Manager konzolon.  

#### <a name="to-create-a-task-sequence-that-installs-an-operating-system"></a>Egy operációs rendszer telepítésére szolgáló feladatütemezés létrehozása  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Operációs rendszerek**pontot, majd kattintson a **Feladatütemezések**elemre.  

3.  A Feladatütemezés létrehozása varázsló elindításához kattintson a **Kezdőlap** **Létrehozás** csoportjában található **Feladatütemezés létrehozása** elemre.  

4.  Az **Új feladatütemezés létrehozása** lapon kattintson a **Meglévő lemezképcsomag telepítése**lehetőségre, majd a **Tovább**gombra.  

5.  A **Feladatütemezés adatai** lapon adja meg a következő beállításokat, majd kattintson a **Tovább**gombra.  

    -   **Feladatütemezés neve**: Adjon meg egy nevet, amely azonosítja a feladatütemezést.  

    -   **Leírás**: Adja meg a feladatütemezés által végrehajtandó feladat leírását.  

    -   **Rendszerindító lemezkép**: Adja meg a rendszerindító lemezképet, telepíti az operációs rendszert a célszámítógépen. A rendszerindító lemezkép a Windows PE egyik verzióját tartalmazza, amellyel telepíthető az operációs rendszer és a szükséges eszközillesztők. További információ: [rendszerindító lemezképek kezelése](../get-started/manage-boot-images.md).  

        > [!IMPORTANT]  
        >  A rendszerindító lemezkép architektúrájának kompatibilisnek kell lennie a célszámítógép hardverarchitektúrájával.  

6.  **A Windows telepítése** lapon adja meg a következő beállításokat, majd kattintson a **Tovább**gombra.  

    -   **Lemezképcsomag**: Adja meg a telepítendő operációs rendszer lemezképét tartalmazó csomagot. További információkért lásd: [operációsrendszer-lemezképek kezelése](../get-started/manage-operating-system-images.md).  

    -   **Kép**: Ha az operációs rendszer lemezképcsomagja több lemezképet tartalmaz, adja meg a telepítendő operációs rendszer lemezképét indexét.  

    -   **Particionálása és formázása az operációs rendszer telepítése a célszámítógépen**: Adja meg, hogy a feladatütemezésnek kell particionálni és formázni a célszámítógépet az operációs rendszer telepítése előtt.  

    -   **Termékkulcs**: Adja meg a telepítendő Windows operációs rendszer termékkulcsát. Kódolt mennyiségi licenckulcsot és normál termékkulcsot egyaránt megadhat. Nem kódolt termékkulcs használata esetén mindegyik 5 karakterből álló csoportot kötőjellel (-) kell egymástól elválasztani. Példa: *XXXXX-XXXXX-XXXXX-XXXXX-XXXXX*  

    -   **Kiszolgáló licencelési módja**: Adja meg, hogy a kiszolgálói licenc **Munkaállomásonként**, **kiszolgálónként**, vagy nincs megadva licenc. Ha a kiszolgálói licenc beállítása **Kiszolgálónként**, adja meg a kiszolgálói kapcsolatok maximális számát is.  

    -   Adja meg, hogyan legyen kezelve az operációs rendszer lemezképének telepítésekor használt rendszergazdai fiók.  

        -   **Helyi rendszergazdai fiók letiltása**: Adja meg, hogy a helyi rendszergazdai fiók le van tiltva az operációs rendszer lemezképének központi telepítésekor.  

        -   **Mindig azonos rendszergazdai jelszó használata**: Adja meg, hogy ugyanazt a jelszót a helyi rendszergazdai fiókhoz minden számítógépen van használni, amelyre az operációs rendszer lemezképét telepíti.  

7.  A **Hálózat beállítása** lapon adja meg a következő beállításokat, majd kattintson a **Tovább**gombra.  

    -   **Csatlakozás munkacsoporthoz**: Adja meg, hogy felvenni a célszámítógépet egy munkacsoporthoz.  

    -   **Csatlakozás tartományhoz**: Adja meg, hogy felvenni a célszámítógépet egy tartományba. A **Tartomány**mezőben adja meg a tartomány nevét.  

        > [!IMPORTANT]  
        >  A helyi erdőben a tartományok megkereséséhez lehetőség van a tallózásra, de távoli erdő esetén be kell írni a tartomány nevét.  

         Lehetőség van szervezeti egység (OU) megadására is. Ez egy nem kötelezően megadandó beállítás, amely annak a szervezeti egységnek az LDAP X.500 szerinti megkülönböztető nevét adja meg, amelyben létre kell hozni a számítógép fiókját, amennyiben az még nem létezik.  

    -   **Fiók**: Adja meg a felhasználónevet és a megadott tartományhoz való csatlakozáshoz engedéllyel rendelkező fiók jelszavát. Például: *tartomány\felhasználó* vagy *%változó%*.  

        > [!IMPORTANT]  
        >  Ha a tartománybeállítások vagy a munkacsoport-beállítások áttelepítését tervezi, meg kell adnia az érvényes tartományi hitelesítő adatokat.  

8.  Az a **Configuration Manager telepítése** adja meg azokat a célszámítógépen telepíteni, és kattintson a Configuration Manager ügyfélcsomag **következő**.  

9. Az **Állapotáttelepítés** lapon adja meg a következő adatokat, majd kattintson a **Tovább**gombra.  

    -   **Felhasználói beállítások rögzítése**: Adja meg, hogy a feladatütemezés rögzíti a felhasználói állapotot. A felhasználói állapot rögzítéséhez és visszaállításához kapcsolatos további információkért lásd: [felhasználói állapot kezelése](../get-started/manage-user-state.md).  

    -   **Hálózati beállítások rögzítése**: Adja meg, hogy a feladatütemezés rögzíti a célszámítógép hálózati beállításait. A hálózati adapter beállításai mellett rögzítheti a tartományi vagy a munkacsoportbeli tagságot is.  

    -   **Microsoft Windows beállítások rögzítése**:  Adja meg, hogy a feladatütemezés rögzíti a célszámítógép Windows-beállításait az operációs rendszer lemezképének telepítése előtt. Rögzítheti a számítógép nevét, a regisztrált felhasználó és szervezet nevét, valamint az időzóna beállításait.  

10. A **Frissítésekkel együtt** lapon adja meg, hogy milyen szoftverfrissítéseket szeretne telepíteni: a szükséges szoftverfrissítéseket, minden szoftverfrissítést, vagy egyet sem; azután kattintson a **Tovább**gombra. Ha a szoftverfrissítések telepítését választja, a Configuration Manager csak azokat a frissítéseket, amelyek telepíti a gyűjteményeket, amelyek a célszámítógép a tagja legyen.  

11. Az **Alkalmazások telepítése** oldalon adja meg a célszámítógépen telepítendő alkalmazásokat, majd kattintson a **Tovább**gombra. Ha több alkalmazást ad meg, lehetősége van a folytatáshoz a feladatsorrendet is megadni, amennyiben egy adott alkalmazást nem sikerült telepíteni.  

12. Fejezze be a varázslót.  

 Most már telepítheti a feladatütemezést a számítógépek egy gyűjteményébe.  További információk: [Feladatütemezés telepítése](manage-task-sequences-to-automate-tasks.md#BKMK_DeployTS).  

##  <a name="BKMK_InstallExistingOSImageTSExample"></a> Példa meglévő operációs rendszeri lemezképet telepítő feladatütemezésre  
 Az alábbi táblázat olyan feladatütemezés létrehozásához szolgálhat útmutatásként, amely meglévő operációsrendszer-kép segítségével telepít operációs rendszert. A táblázat segítséget nyújt a feladatütemezési lépések általános sorrendjének meghatározásához és a lépések logikai csoportokba rendezéséhez és szerkezetének kialakításához. Az Ön által létrehozott feladatütemezés eltérhet ettől a példától, és több vagy kevesebb feladatütemezési lépést tartalmazhat.  

> [!IMPORTANT]  
>  Ezt a feladatütemezést mindig a Feladatütemezés létrehozása varázslóval hozza létre.  

 Ha a Feladatütemezés létrehozása varázsló segítségével hozza létre ezt az új feladatütemezést, néhány feladatütemezési lépés neve eltér attól, mint ha manuálisan adta volna hozzá ezeket a lépéseket egy meglévő feladatütemezéshez. Az alábbi táblázatban láthatók az elnevezési eltérések:  

|Feladatütemezés létrehozása varázsló feladatütemezési lépésének neve|Feladatütemezés-szerkesztő egyenértékű lépésének neve|  
|---------------------------------------------------------|-----------------------------------------------|  
|Felhasználói állapot tárolására vonatkozó kérelem|Állapot tárolásának igénylése|  
|Felhasználói fájlok és beállítások rögzítése|Felhasználói állapot rögzítése|  
|Felhasználói állapot tárolásának felszabadítása|Állapot tárolásának felszabadítása|  
|Újraindítás Windows PE környezetben|Újraindítás Windows PE környezetben vagy merevlemezen|  
|0 lemez particionálása|Lemez formázása és particionálása|  
|Felhasználói fájlok és beállítások visszaállítása|Felhasználói állapot visszaállítása|  

|Feladatütemezési csoport vagy lépés|Leírás|  
|---------------------------------|-----------------|  
|Fájlok és beállítások rögzítése – **(új feladatütemezési csoport)**|Feladatütemezési csoport létrehozása. A feladatütemezési csoportok a jobb rendezés és hibaellenőrzés érdekében összefogják a hasonló feladatütemezési lépéseket.<br /><br /> Ez a csoport tartalmazza a referencia-számítógépen futó operációs rendszer fájljainak és beállításainak rögzítéséhez szükséges lépéseket.|  
|Windows-beállítások rögzítése|Ezzel a feladatütemezési lépéssel jelölheti ki a referencia-számítógépről rögzítendő feladatütemezési lépéseket. Rögzítheti a számítógép nevét, a felhasználói és szervezeti információkat, valamint az időzóna beállításait.|  
|Hálózati beállítások rögzítése|Ezzel a feladatütemezési lépéssel rögzítheti a hálózati beállításokat a referencia-számítógépről. A hálózati adapter beállításai mellett rögzítheti a referencia-számítógép tartományi vagy munkacsoportbeli tagságát is.|  
|Felhasználói fájlok és beállítások rögzítése – **(új feladatütemezési alcsoport)**|Feladatütemezési csoport létrehozása a feladatütemezési csoporton belül. Ez az alcsoport a felhasználói állapotadatok rögzítéséhez szükséges lépéseket tartalmazza. Az elsőként hozzáadott csoporthoz hasonlóan ez az alcsoport a jobb rendezés és hibaellenőrzés érdekében összefogja a hasonló feladatütemezési lépéseket.|  
|Felhasználói állapot tárolására vonatkozó kérelem|Ezzel a feladatütemezési lépéssel igényelhet hozzáférést olyan állapotáttelepítési ponthoz, amely a felhasználói állapot adatait tárolja. Ez a feladatütemezési lépés a felhasználói állapot adatainak rögzítésére vagy visszaállítására állítható be.|  
|Felhasználói fájlok és beállítások rögzítése|Ez a feladatütemezési lépés használatával a felhasználói állapotot és beállításokat, amelyek megkapják a lépéshez tartozó feladatütemezés a referencia-számítógépről rögzíteni a felhasználói állapot áttelepítési eszköz (USMT) használatával. Rögzítheti az alapértelmezett beállításokat, vagy megadhatja, hogy mely beállításokat szeretné rögzíteni.|  
|Felhasználói állapot tárolásának felszabadítása|Ezzel a feladatütemezési lépéssel értesítheti az állapotáttelepítési pontot a rögzítési vagy visszaállítási művelet befejezéséről.|  
|Operációs rendszer telepítése – **(új feladatütemezési csoport)**|Új feladatütemezési alcsoport létrehozása. Ez az alcsoport telepítése és konfigurálása a Windows PE környezet szükséges lépéseket tartalmazza.|  
|Újraindítás Windows PE környezetben|Ezzel a feladatütemezési lépéssel határozhat meg újraindítási beállításokat arra a célszámítógépre vonatkozóan, amely a feladatütemezést megkapja. Ez a lépés üzenetben tájékoztatja a felhasználót a számítógép újraindításáról, hogy a telepítés folytatódhasson.<br /><br /> Ez a lépés a csak olvasható **_SMSTSInWinPE** feladatütemezési változót használja. Ha a kapcsolódó érték **hamis** , a feladatütemezési lépés folytatódik.|  
|0 lemez particionálása|Ezzel a feladatütemezési lépéssel adhatja meg a célszámítógépen a merevlemez formázásához szükséges műveleteket. Az alapértelmezett lemezszám a **0**.<br /><br /> Ez a lépés a csak olvasható **_SMSTSClientCache** feladatütemezési változót használja. Ez a lépés akkor fog futni, ha a Configuration Manager-ügyfél gyorsítótára nem létezik.|  
|Operációs rendszer alkalmazása|Ezzel a feladatütemezési lépéssel telepítheti az operációsrendszer-képet a célszámítógépen. Ez a lépés az adott köteten (a Configuration Manager-specifikus vezérlési fájlok) kivételével minden fájl törlése után a WIM-fájlban a megfelelő soros lemezköteten a cél számítógépen található összes kötetlemezképet vonatkozik. Egy **sysprep** válaszfájl konfigurálásával emellett megadhatja, hogy mely lemezpartíciót szeretné használni a telepítéshez.|  
|Windows-beállítások alkalmazása|Ezzel a feladatütemezési lépéssel konfigurálhatja a Windows-beállítások konfigurációs adatait a célszámítógéphez. Az alkalmazható Windows-beállítások lehetnek a felhasználói és szervezeti adatokkal, a termék- vagy licenckulcsokkal, az időzónával és a helyi rendszergazdai jelszóval kapcsolatos adatok.|  
|Hálózati beállítások alkalmazása|Ezzel a feladatütemezési lépéssel adhatja meg a célszámítógép hálózati vagy munkacsoport-konfigurációs adatait. Megadhatja azt is, hogy a számítógép DHCP-kiszolgált használ-e, vagy statikusan is hozzárendelheti az IP-címmel kapcsolatos információkat.|  
|Eszközillesztők alkalmazása|Ezzel a feladatütemezési lépéssel telepítheti az illesztőprogramokat az operációs rendszer telepítésének részeként. **Az összes kategóriából származó illesztőprogram figyelembevétele** választógombot bejelölve engedélyezheti, hogy a Windows telepítő minden meglévő illesztőprogram-kategóriában keressen, **Az illesztőprogramok figyelembevételének korlátozása a kiválasztott kategóriákra**választógombot bejelölve pedig korlátozhatja, hogy a Windows telepítő mely illesztőprogram-kategóriákban keressen.<br /><br /> Ez a lépés a csak olvasható **_SMSTSMediaType** feladatütemezési változót használja. Ez a feladatütemezési lépés csak akkor fut, ha a változó értéke nem **FullMedia**.|  
|Illesztőprogram-csomag alkalmazása|Ez a feladatütemezési lépés lehetővé teszi, hogy egy adott illesztőprogram-csomagban minden eszközillesztőt elérhetővé tegyen a Windows telepítő számára.|  
|Operációs rendszer beállítása – **(új feladatütemezési csoport)**|Új feladatütemezési alcsoport létrehozása. Ez az alcsoport a telepített operációs rendszer beállításához szükséges lépéseket tartalmazza.|  
|Windows és ConfigMgr beállítása|Ez a feladatütemezési lépés használatával a Configuration Manager ügyfélszoftver telepítéséhez. A Configuration Manager telepíti, és regisztrálja a Configuration Manager-ügyfél GUID Azonosítóját. A szükséges telepítési paramétereket a **Telepítés tulajdonságai** ablakban rendelheti hozzá.|  
|Frissítések telepítése|Ezzel a feladatütemezési lépéssel adja meg, hogy a szoftverfrissítések hogyan legyenek telepítve a célszámítógépen. A rendszer ezen feladatütemezési lépés futtatásáig nem értékeli ki, hogy a célszámítógépen alkalmazhatóak-e szoftverfrissítések. Ezen a ponton a célszámítógépen a szoftverfrissítések bármely más Configuration Manager által felügyelt-ügyfélhez hasonlóan értékeli ki.<br /><br /> Ez a lépés a csak olvasható **_SMSTSMediaType** feladatütemezési változót használja. Ez a feladatütemezési lépés csak akkor fut, ha a változó értéke nem **FullMedia**.|  
|Felhasználói fájlok és beállítások visszaállítása – **(új feladatütemezési alcsoport)**|Új feladatütemezési alcsoport létrehozása. Ez az alcsoport a felhasználói fájlok és beállítások visszaállításához szükséges lépéseket tartalmazza.|  
|Felhasználói állapot tárolására vonatkozó kérelem|Ezzel a feladatütemezési lépéssel igényelhet hozzáférést olyan állapotáttelepítési ponthoz, amely a felhasználói állapot adatait tárolja.|  
|Felhasználói fájlok és beállítások visszaállítása|Ez a feladatütemezési lépés segítségével kezdeményezheti a felhasználói állapot áttelepítési Felhasználóáttelepítő (USMT) visszaállítani a felhasználói állapotot és beállításokat a célszámítógépre.|  
|Felhasználói állapot tárolásának felszabadítása|Ezzel a feladatütemezési lépéssel értesítheti az állapotáttelepítési pontot arról, hogy a felhasználói állapotadatokra már nincs szükség.|  

