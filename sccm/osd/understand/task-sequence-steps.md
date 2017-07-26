---
title: "Feladatütemezési lépéseket - Configuration Manager |} Microsoft Docs"
description: "Ismerje meg a feladatütemezési lépések, amelyeket a Configuration Manager feladatütemezésbe."
ms.custom: na
ms.date: 03/26/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7c888a6f-8e37-4be5-8edb-832b218f266d
caps.latest.revision: 26
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 071d758f1015d16217a54fe26df5f8f948c818a3
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="task-sequence-steps-in-system-center-configuration-manager"></a>Feladatütemezési lépések a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Az alábbi feladatütemezési lépések felveheti a Configuration Manager feladatütemezésbe. További információk a feladatütemezések szerkesztésével kapcsolatban: [Feladatütemezés szerkesztése](../deploy-use/manage-task-sequences-to-automate-tasks.md#BKMK_ModifyTaskSequence).  


##  <a name="BKMK_ApplyDataImage"></a>Adatok kép feladatütemezési lépés alkalmazása  
 Az **Adatlemezképfájl alkalmazása** feladatütemezési lépéssel a megadott célpartícióra másolhatja az adatlemezképfájlt.  

 Ez a lépés csak Windows PE környezetben futtatható. Normál operációs rendszereken nem futtatható. A művelet feladatütemezési változóival kapcsolatos további információkért lásd: [feladat feladatütemezési művelet változói](task-sequence-action-variables.md).  

### <a name="details"></a>Részletek  
 A lépés **Tulajdonságok** lapján az ebben a szakaszban bemutatott beállításokat konfigurálhatja.  

 Ezenkívül a **Beállítások** lapon a következő műveleteket hajthatja végre:  

-   A lépés letiltása.  

-   Annak megadása, hogy a feladatütemezés folytatódjon-e, ha a lépés futtatása során hiba lép fel.  

-   Feltételek megadása, melyeknek teljesülnie kell a lépés futtatásához.  

 **Név**  
 Egy rövid, felhasználó által definiált név, mely leírja az ebben a lépésben végrehajtott műveletet.  

 **Leírás**  
 Részletesebb információk az ebben a lépésben végrehajtott műveletről.  

 **Lemezképcsomag**  
 A **Tallózás** gombra kattintva adja meg az ebben a feladatütemezésben használni kívánt **lemezképcsomagot**. A **Válasszon csomagot** párbeszédpanelen jelölje ki a telepíteni kívánt csomagot. A meglévő lemezképcsomagok társított tulajdonságadatai a **Válasszon csomagot** párbeszédpanel alján jelennek meg. A kiválasztott **lemezképcsomagból** telepíteni kívánt **lemezképet** a legördülő listából választhatja ki.  

> [!NOTE]  
>  Ez a feladatütemezési művelet adatfájlként kezeli a lemezképet, és nem végez el semmilyen ahhoz szükséges beállítást, hogy a lemezképet operációs rendszerként el lehessen indítani.  

 **Cél**  
 Egy meglévő formázott partíciót és merevlemezt, egy adott logikai meghajtó betűjelét, vagy egy, a a logikai meghajtó betűjelét tartalmazó feladatütemezési változó nevét adja meg.  

-   **Következő elérhető partíció** -, amely még nem lett korábban művelet céljaként megadva egy operációs rendszer alkalmazása vagy Adatlemezképfájl a feladatütemezés következő olyan partíció használata.  

-   **Adott lemez és partíció** – Itt adhatja meg a **lemez** (0-tól induló) számának és a **partíció** (1-től induló) számának.  

-   **Adott logikaimeghajtó-betűjel** -adja meg a **meghajtóbetűjelet** a Windows PE által a partícióhoz rendelt. Fontos megjegyezni, hogy ez a meghajtóbetűjel eltérhet attól a meghajtóbetűjeltől, amelyet az újonnan telepített operációs rendszer fog hozzárendelni.  

-   **Változóként tárolt logikaimeghajtó-betűjel** -adja meg a Windows PE által a partícióhoz rendelt meghajtóbetűjelet tartalmazó feladatütemezési változó. Ezt a változót általában a **Lemez formázása és particionálása** feladatütemezési művelet **Partíció tulajdonságai** párbeszédpanelének Speciális részében állítják be.  

 **Törölje a partíción lévő összes tartalmat kép alkalmazása előtt**  
 Azt határozza meg, hogy a lemezkép telepítése előtt a célpartíción lévő összes fájl törlődjön. Ha nem törli a partíció tartalmát, ezzel a lépéssel további tartalmat alkalmazhat egy korábban már célként megadott partíción.  

##  <a name="BKMK_ApplyDriverPackage"></a>Illesztőprogram-csomag alkalmazása  
 Az **Illesztőprogram-csomag alkalmazása** feladatütemezési lépéssel az illesztőprogram-csomagban lévő összes illesztőprogramot letöltheti, és telepítheti a Windows operációs rendszerben.

 Az **Illesztőprogram-csomag alkalmazása** feladatütemezési lépés az adott illesztőprogram-csomagban lévő összes eszközillesztőt elérhetővé teszi a Windows számára. Ez a lépés a feladatütemezés **Operációs rendszer alkalmazása** és **Windows és ConfigMgr beállítása** lépése közé beillesztve elérhetővé teszi az illesztőprogram-csomagban lévő eszközillesztőket a Windows számára. Az**Illesztőprogram-csomag alkalmazása** lépést általában az**Illesztőprogramok automatikus alkalmazása** feladatütemezési lépés után célszerű elhelyezni. Az **Illesztőprogram-csomag alkalmazása** feladatütemezési lépés különálló adathordozóról történő telepítések esetén is használható.  

 Győződjön meg arról, hogy a hasonló eszközillesztők egy illesztőprogram-csomagba kerüljenek, és terjessze azokat a megfelelő terjesztési pontokra. Miután továbbítja a Configuration Manager-ügyfél számítógépeinek elvégezheti a telepítést. Például egy gyártó összes eszközillesztőjét elhelyezheti egy illesztőprogram-csomagban, majd terjesztheti a csomagot a terjesztési pontokra, ahol a kapcsolódó számítógépek hozzájuk férhetnek.

 Ez a lépés használható különálló adathordozókhoz, illetve olyan rendszergazdák számára, akik illesztőprogramok egy adott készletét szeretnék telepíteni, beleértve olyan eszközök illesztőprogramjait, melyek nem lennének megtalálhatóak egy Plug and Play vizsgálattal (például hálózati nyomtatók).  

 Ez a feladatütemezési lépés csak Windows PE környezetben futtatható. Normál operációs rendszereken nem futtatható. A művelet feladatütemezési változóival kapcsolatban [Az Illesztőprogram-csomag alkalmazása feladatütemezési művelet változói](task-sequence-action-variables.md#BKMK_ApplyDriverPackage) című témakörben találhatók további információk.  

### <a name="details"></a>Részletek  
 A lépés **Tulajdonságok** lapján az ebben a szakaszban bemutatott beállításokat konfigurálhatja.  

 Ezenkívül a **Beállítások** lapon a következő műveleteket hajthatja végre:  

-   A lépés letiltása.  

-   Annak megadása, hogy a feladatütemezés folytatódjon-e, ha a lépés futtatása során hiba lép fel.  

-   Feltételek megadása, melyeknek teljesülnie kell a lépés futtatásához.  

 **Név**  
 Egy rövid, felhasználó által definiált név, mely leírja az ebben a lépésben végrehajtott műveletet.  

 **Leírás**  
 Részletesebb információk az ebben a lépésben végrehajtott műveletről.  

 **Illesztőprogram-csomag**  
 A **Tallózás** gombra kattintva, majd a **Válasszon csomagot** párbeszédpanel megnyitásával megadhatja a szükséges eszközillesztőket tartalmazó illesztőprogram-csomagot. Adjon meg egy már létező csomagot, melyet elérhetővé kíván tenni. A csomaghoz kapcsolódó tulajdonságok a párbeszédpanel alján jelennek meg.  

 **Válassza ki a háttértár-illesztőprogramot, amely a korábbi Windows Vista operációs rendszer telepítése előtt telepíteni kell**  
 Adja meg a Windows Vista előtti operációs rendszerek telepítéseihez szükséges háttértár-illesztőprogramokat, ha vannak ilyenek.  

 **Illesztőprogram**  
 Válassza ki a háttértár-illesztőprogram fájlját, amelyet a Windows Vista előtti operációs rendszerek központi telepítésein a beállítás előtt kell telepíteni. A legördülő lista a megadott csomag alapján lesz feltöltve.  

 **Modell**  
 Adja meg a rendszerindításhoz szükséges eszközt, mely a Windows Vista előtti operációs rendszerek központi telepítéseihez szükséges.  

 **Felügyelet nélküli aláírás nélküli illesztőprogramok, ahol ez engedélyezett Windows verziója**  
 Ezzel a beállítással engedélyezheti az aláírás nélküli illesztőprogramok telepítését a referencia-számítógépen.  

##  <a name="BKMK_ApplyNetworkSettings"></a>Hálózati beállítások alkalmazása  
 A **Hálózati beállítások alkalmazása** feladatütemezési lépéssel adhatja meg a célszámítógép hálózati vagy munkacsoport-konfigurációs adatait. A megadott értékek a megfelelő válaszfájlformátumban lesznek tárolva ahhoz, hogy a Windows telepítő felhasználhassa azokat a **Windows és ConfigMgr beállítása** feladatütemezési lépés futtatásakor.  

 Ez a feladatütemezési lépés normál operációs rendszeren és Windows PE környezetben is futtatható. A művelet feladatütemezési változóival kapcsolatban [A Hálózati beállítások alkalmazása feladatütemezési művelet változói](task-sequence-action-variables.md#BKMK_ApplyNetworkSettings) című témakörben találhatók további információk.  

### <a name="details"></a>Részletek  
 A lépés **Tulajdonságok** lapján az ebben a szakaszban bemutatott beállításokat konfigurálhatja.  

 Ezenkívül a **Beállítások** lapon a következő műveleteket hajthatja végre:  

-   A lépés letiltása.  

-   Annak megadása, hogy a feladatütemezés folytatódjon-e, ha a lépés futtatása során hiba lép fel.  

-   Feltételek megadása, melyeknek teljesülnie kell a lépés futtatásához.  

 **Név**  
 Egy rövid, felhasználó által definiált név, mely leírja az ebben a lépésben végrehajtott műveletet.  

 **Leírás**  
 Részletesebb információk az ebben a lépésben végrehajtott műveletről.  

 **Csatlakozás munkacsoporthoz**  
 Ezzel a beállítással csatlakoztathatja a célszámítógépet a megadott munkacsoporthoz. A **Munkacsoport** sorban adja meg a munkacsoport nevét. Ezt az értéket a **Hálózati beállítások rögzítése** feladatütemezési lépésben rögzített érték felülbírálhatja.  

 **Csatlakozás tartományhoz**  
 Ezzel a beállítással csatlakoztathatja a célszámítógépet a megadott tartományhoz. Adja meg, vagy tallózással keresse meg a tartományt (például *fabricam.com*). Adja meg, vagy tallózással keresse meg egy szervezeti egység LDAP-elérésiútját (például LDAP//OU=számítógépek, DC=Fabricam.com, C=com).  

 **Fiók**  
 A **Beállítás** elemre kattintva adjon meg egy olyan fiókot, amely jogosult arra, hogy csatlakoztassa a számítógépet a tartományhoz. Az a **Windows felhasználói fiók** párbeszédpanelen adhatja meg a felhasználónevet a következő formátumban: **Tartomány\felhasználó** .  

 **Adapter beállításai**  
 Adja meg a hálózati beállításokat a számítógép minden hálózati adapteréhez. Az **Új** lehetőségre kattintva megnyithatja a **Hálózati beállítások** párbeszédpanelt, majd megadhatja a hálózati beállításokat. Ha egy korábbi **Hálózati beállítások rögzítése** feladatütemezési lépés rögzítette a hálózati beállításokat, ezek lesznek alkalmazva a hálózati adapterre, nem pedig az ebben a lépésben megadottak. Ha korábban nem lettek rögzítve hálózati beállítások, a **Hálózati beállítások alkalmazása** lépésben megadott beállítások lesznek alkalmazva a hálózati adapterekre, a Windows eszközfelsorolási sorrendjében.  

##  <a name="BKMK_ApplyOperatingSystemImage"></a>Operációs rendszer lemezképének alkalmazása  
 Az **Operációs rendszer lemezképének alkalmazása** feladatütemezési lépéssel telepíthető operációs rendszer a célszámítógépen. Ez a feladatütemezési lépés attól függően hajtja végre műveletek egy csoportját, hogy az operációs rendszer lemezképét, vagy az operációs rendszer telepítőcsomagját használja-e az operációs rendszer telepítéséhez.  

 Az **Operációs rendszer lemezképének alkalmazása** lépés az alábbi műveleteket hajtja végre az operációs rendszer lemezképének használatakor.  

1.  Törli a célkötet által megadott mappában lévő fájlok kivételével minden tartalom a &#95; SMSTSUserStatePath feladatütemezési változót.  

2.  Kibontja a megadott .wim fájl tartalmát a megadott célpartícióra.  

3.  Előkészíti a válaszfájlt:  

    1.  Létrehoz egy új alapértelmezett Windows-telepítési válaszfájlt (a sysprep.inf vagy az unattend.xml fájlt) a telepítés alatt álló operációs rendszerhez.  

    2.  Ezzel összefésül minden, a felhasználó által megadott válaszfájlban esetlegesen meglévő értéket.  

4.  Átmásolja a Windows rendszertöltőket az aktív partícióra.  

5.  Beállítja a boot.ini fájlt vagy a rendszerindítási konfigurációs adatbázist (BCD), hogy hivatkozza az újonnan telepített operációs rendszert.  

 Az **Operációs rendszer lemezképének alkalmazása** lépés az alábbi műveleteket hajtja végre operációs rendszer telepítőcsomagjának használatakor.  

1.  Törli a célkötet által megadott mappában lévő fájlok kivételével minden tartalom a &#95; SMSTSUserStatePath feladatütemezési változót.  

2.  Előkészíti a válaszfájlt:  

    1.  Létrehoz egy friss válaszfájlt a Configuration Manager által létrehozott alapértékekkel.  

    2.  Ezzel összefésül minden, a felhasználó által megadott válaszfájlban esetlegesen meglévő értéket.  

> [!NOTE]  
>  A Windows tényleges telepítését a **Windows és ConfigMgr beállítása** feladatütemezési lépés indítja el. Miután az **Operációs rendszer alkalmazása** feladatütemezési lépés lefutott, az OSDTargetSystemDrive feladatütemezési változó értéke az operációs rendszer fájljait tartalmazó partíció meghajtóbetűjelére lesz beállítva.  

 Ez a feladatütemezési lépés csak Windows PE környezetben futtatható. Normál operációs rendszereken nem futtatható. A művelet feladatütemezési változóival kapcsolatban [Az Operációs rendszer lemezképének alkalmazása feladatütemezési művelet változói](task-sequence-action-variables.md#BKMK_ApplyOperatingSystem) című témakörben találhatók további információk.  

### <a name="details"></a>Részletek  
 A lépés **Tulajdonságok** lapján az ebben a szakaszban bemutatott beállításokat konfigurálhatja.  

 Ezenkívül a **Beállítások** lapon a következő műveleteket hajthatja végre:  

-   A lépés letiltása.  

-   **Tartalom elérése közvetlenül a terjesztési pontról**:  

     Ezzel a beállítással adhatja meg, hogy a feladatütemezés közvetlenül a terjesztési pontról érje-e el az operációs rendszer lemezképét. Ez a beállítás használható például operációs rendszerek korlátozott tárolókapacitású beágyazott eszközökre való központi telepítéséhez. Ha ez a beállítás meg van adva, konfigurálnia kell a csomagmegosztási beállításokat is a csomag tulajdonságainak **Adatelérés** lapján.  

    > [!NOTE]  
    >  Ez a beállítás a **Szoftver központi telepítése varázsló** **Terjesztési pontok** lapján beállított telepítési beállítást nem a feladatütemezés teljes tartalmára, hanem csak a feladatütemezési lépésben megadott operációsrendszer-képre vonatkozóan írja felül.  

-   Annak megadása, hogy a feladatütemezés folytatódjon-e, ha a lépés futtatása során hiba lép fel.  

-   Feltételek megadása, melyeknek teljesülnie kell a lépés futtatásához.  

 **Név**  
 Egy rövid, felhasználó által definiált név, mely leírja az ebben a lépésben végrehajtott műveletet.  

 **Leírás**  
 Részletesebb információk az ebben a lépésben végrehajtott műveletről.  

 **Operációs rendszer alkalmazása egy rögzített lemezképből**  
 Egy korábban rögzített operációsrendszer-képet telepít. A **Tallózás** lehetőségre kattintva nyissa meg a **Válasszon csomagot** párbeszédpanelt, majd válassza ki a telepíteni kívánt meglévő lemezképcsomagot. Ha több lemezkép van hozzárendelve a megadott **lemezképcsomaghoz**, a legördülő listából válassza ki, hogy melyik társított lemezképet kívánja használni ehhez a telepítéshez. A lemezképre kattintva megtekintheti az egyes meglévő lemezképek alapvető adatait.  

 **Operációs rendszer lemezképének alkalmazása eredeti telepítési forrásból**  
 Egy eredeti telepítési forrás használatával telepít egy operációs rendszert. A **Tallózás** lehetőségre kattintva nyissa meg az **Operációs rendszer telepítőcsomagjának kiválasztása** párbeszédpanelt, majd válassza ki a telepíteni kívánt meglévő operációsrendszer-telepítőcsomagot. A lemezképforrásra kattintva megtekintheti az egyes meglévő lemezképforrások alapvető adatait. A lemezképforrásokhoz kapcsolódó tulajdonságok az eredménypanelen jelennek meg, a párbeszédpanel alján. Ha a megadott csomaghoz több kiadás is hozzá van rendelve, a legördülő listából választhatja ki, hogy melyik hozzárendelt **Kiadást** kívánja használni.  

 **Egyéni telepítés használni egy felügyelet nélküli telepítési vagy sysprep válaszfájlt**  
 Ezzel a beállítással egy Windows-telepítési válaszfájlt (**unattend.xml**, **unattend.txt** vagy **sysprep.inf** fájlt) adhat meg az operációs rendszer verziójától és a telepítési módszertől függően. A megadott fájl tartalmazhat bármilyen, a Windows-válaszfájlok által támogatott szabványos konfigurációs beállítást. Például ennek segítségével megadhatja az Internet Explorer alapértelmezett kezdőlapját. Meg kell adnia a csomagot, amely tartalmazza a válaszfájlt, illetve a csomagban lévő fájlhoz tartozó elérési utat.  

> [!NOTE]  
>  A megadott Windows-telepítési válaszfájl tartalmazhat beágyazott feladatütemezési változókat %*változónév*% alakban, ahol a változónév a változó neve. A %*változónév*% karakterlánc helyére a **Windows és ConfigMgr beállítása** feladatütemezési művelet tényleges változóértékei kerülnek. Fontos azonban megjegyezni, hogy az ilyen beágyazott feladatütemezési változók nem használhatók az unattend.xml válaszfájlok csak numerikus mezőiben.  

 Ha nem ad meg Windows-telepítési válaszfájlt, a feladatütemezési művelet automatikusan létrehoz egy válaszfájlt.  

 **Cél**  
 Egy meglévő formázott partíciót és merevlemezt, egy adott logikai meghajtó betűjelét, vagy egy, a a logikai meghajtó betűjelét tartalmazó feladatütemezési változó nevét adja meg.  

-   **Következő elérhető partíció** -, amely még nem lett korábban művelet céljaként megadva egy operációs rendszer alkalmazása vagy Adatlemezképfájl a feladatütemezés következő olyan partíció használata.  

-   **Adott lemez és partíció** – Itt adhatja meg a **lemez** (0-tól induló) számának és a **partíció** (1-től induló) számának.  

-   **Adott logikaimeghajtó-betűjel** -adja meg a **meghajtóbetűjelet** a Windows PE által a partícióhoz rendelt. Fontos megjegyezni, hogy ez a meghajtóbetűjel eltérhet attól a meghajtóbetűjeltől, amelyet az újonnan telepített operációs rendszer fog hozzárendelni.  

-   **Változóként tárolt logikaimeghajtó-betűjel** -adja meg a Windows PE által a partícióhoz rendelt meghajtóbetűjelet tartalmazó feladatütemezési változó. Ezt a változót általában a **Lemez formázása és particionálása** feladatütemezési művelet **Partíció tulajdonságai** párbeszédpanelének Speciális részében állítják be.  

##  <a name="BKMK_ApplyWindowsSettings"></a>Windows beállítások alkalmazása  
 A **Windows beállítások alkalmazása** feladatütemezési lépéssel konfigurálhatja a Windows beállításait a célszámítógépen. A megadott értékek a megfelelő válaszfájlformátumban lesznek tárolva ahhoz, hogy a Windows telepítő felhasználhassa azokat a **Windows és ConfigMgr beállítása** feladatütemezési lépés futtatásakor.  

 Ez a feladatütemezési lépés csak Windows PE környezetben futtatható. Normál operációs rendszereken nem futtatható. A művelet feladatütemezési változóival kapcsolatban [A Windows-beállítások alkalmazása feladatütemezési művelet változói](task-sequence-action-variables.md#BKMK_ApplyWindowsSettings) című témakörben találhatók további információk.  

### <a name="details"></a>Részletek  
 A lépés **Tulajdonságok** lapján az ebben a szakaszban bemutatott beállításokat konfigurálhatja.  

 Ezenkívül a **Beállítások** lapon a következő műveleteket hajthatja végre:  

-   A lépés letiltása.  

-   Annak megadása, hogy a feladatütemezés folytatódjon-e, ha a lépés futtatása során hiba lép fel.  

-   Feltételek megadása, melyeknek teljesülnie kell a lépés futtatásához.  

 **Név**  
 Egy rövid, felhasználó által definiált név, mely leírja az ebben a lépésben végrehajtott műveletet.  

 **Leírás**  
 Részletesebb információk az ebben a lépésben végrehajtott műveletről.  

 **Felhasználónév**  
 Adja meg a célszámítógéphez társított regisztrált felhasználónevet. Ezt az értéket a **Windows beállítások rögzítése** feladatütemezési műveletben rögzített érték felülbírálhatja.  

 **Szervezet neve**  
 Adja meg a célszámítógéphez társított regisztrált szervezetnevet. Ezt az értéket a **Windows beállítások rögzítése** feladatütemezési műveletben rögzített érték felülbírálhatja.  

 **Termékkulcs**  
 Adja meg a célszámítógépen végzett Windows-telepítéshez használt termékkulcsot.  

 **Kiszolgálólicencelés**  
 Adja meg a kiszolgáló licencelési módját. **Kiszolgálónkénti** vagy **felhasználónkénti** licencelési módot választhat. Ha a kiszolgálónkénti licencelési módot választja, a licencszerződésben engedélyezett maximális kapcsolatszámot is meg kell adnia. Válassza a **Ne adja meg** lehetőséget, ha a célszámítógép nem kiszolgáló, vagy nem szeretné megadni a licencelési módot.  

 **A kapcsolatok maximális száma**  
 A licencszerződésében megadottaknak megfelelően adja meg az ezen a számítógépen elérhető kapcsolatok maximális számát.  

 **Véletlenszerűen generálja a helyi rendszergazda jelszavát, és tiltsa le a fiókot az összes támogatott platformon (ajánlott)**  
 Ezzel a lehetőséggel véletlenszerű helyi rendszergazdai jelszót állíthat elő. Ekkor létrejön egy helyi rendszergazdai jelszó, és a fiók le lesz tiltva a támogatott platformokon.  

 **Engedélyezze a fiókot, és adja meg a helyi rendszergazda jelszavát**  
 Ezzel a lehetőséggel engedélyezheti a helyi rendszergazdai fiókot és létrehozhatja a helyi rendszergazda jelszavát. Adja meg a jelszót a **Jelszó** sorban, majd erősítse meg a jelszót a **Jelszó megerősítése** sorban.  

 **Időzóna**  
 Adja meg a célszámítógépen beállítandó időzónát. Ezt az értéket a **Windows beállítások rögzítése** feladatütemezési lépésben rögzített érték felülbírálhatja.  

##  <a name="BKMK_AutoApplyDrivers"></a>Illesztőprogramok automatikus alkalmazása  
 Az **Illesztőprogramok automatikus alkalmazása** feladatütemezési lépéssel egyeztetheti és telepítheti az illesztőprogramokat az operációs rendszer központi telepítésének részeként.  

 Az **Illesztőprogramok automatikus alkalmazása** feladatütemezési lépés a következő műveleteket hajtja végre:  

1.  Megvizsgálja a hardvert, és megkeresi az összes, a rendszerben megtalálható eszköz Plug and Play azonosítóját.  

2.  Elküldi az eszközök és Plug and Play azonosítóik listáját a felügyeleti pontra. A felügyeleti pont minden eszközhöz visszaküldi az illesztőprogram-katalógusban található kompatibilis illesztőprogramok listáját. A felügyeleti pont az összes illesztőprogramot figyelembe veszi attól függetlenül, hogy melyik illesztőprogram-csomagban találhatók. A rendszer csak a megadott illesztőprogram-kategóriával címkézett és a letiltottként nem megjelölt illesztőprogramokat veszi figyelembe.  

3.  Minden eszközhöz az ügyfél választja ki a legjobb olyan illesztőprogramot, mely megfelelő a telepített operációs rendszerhez, és egy elérhető terjesztési ponton található.  

4.  A kijelölt illesztőprogram vagy illesztőprogramok egy terjesztési pontról töltődnek le, és elő vannak készítve a cél operációs rendszeren.  

    1.  Lemezképalapú telepítés esetén az illesztőprogramok bekerülnek az operációs rendszer illesztőprogramtárába.  

    2.  Telepítő-alapú telepítések esetén a Windows telepítőben be lesz állítva, hogy hol találhatóak az illesztőprogramok.  

5.  Amikor lefut a **Windows és ConfigMgr beállítása** feladatütemezési lépés, és először elindul a Windows rendszer, megtalálja a művelet által előkészített illesztőprogramokat.  

> [!IMPORTANT]
>  A **illesztőprogramok automatikus alkalmazása** feladatütemezési lépés nem használható különálló adathordozók, mert a Windows telepítőnek nem lesz kapcsolata a Configuration Manager-hely.

Ez a feladatütemezési lépés csak Windows PE környezetben futtatható. Normál operációs rendszereken nem futtatható. A művelet feladatütemezési változóival kapcsolatban [Az Illesztőprogramok automatikus alkalmazása feladatütemezési művelet változói](task-sequence-action-variables.md#BKMK_AutoApplyDrivers) című témakörben találhatók további információk.  

### <a name="details"></a>Részletek  
 A lépés **Tulajdonságok** lapján az ebben a szakaszban bemutatott beállításokat konfigurálhatja.  

 Ezenkívül a **Beállítások** lapon a következő műveleteket hajthatja végre:  

-   A lépés letiltása.  

-   Annak megadása, hogy a feladatütemezés folytatódjon-e, ha a lépés futtatása során hiba lép fel.  

-   Feltételek megadása, melyeknek teljesülnie kell a lépés futtatásához.  

 **Név**  
 Egy rövid, felhasználó által definiált név, mely leírja az ebben a lépésben végrehajtott műveletet.  

 **Leírás**  
 Részletesebb információk az ebben a lépésben végrehajtott műveletről.  

 **Csak a legjobban illeszkedő kompatibilis illesztőprogramok telepítése**  
 Azt adja meg, hogy a feladatütemezési lépés minden észlelt hardvereszközhöz csak a leginkább kompatibilis illesztőprogramot telepítse.  

 **Összes kompatibilis illesztőprogram telepítése**  
 Azt adja meg, hogy a feladatütemezési lépés minden észlelt hardvereszközhöz telepítse az összes kompatibilis illesztőprogramot, és lehetővé teszi, hogy a legjobb illesztőprogramot a Windows telepítő válassza ki. Ez a lehetőség több hálózati sávszélességet és lemezterületet igényel, mert több illesztőprogram letöltésével jár, de eredményezheti egy jobb illesztőprogram kiválasztását.  

 **Az összes kategóriából származó illesztőprogram figyelembevétele**  
 Azt adja meg, hogy a feladatütemezési művelet minden elérhető illesztőprogram-kategóriában keresse a megfelelő eszközillesztőket.  

 **A kiválasztott kategóriákra illesztőprogramok figyelembevételének korlátozása**  
 Azt adja meg, hogy a feladatütemezési művelet a megadott illesztőprogram-kategóriákban keresse a megfelelő eszközillesztőket.  

 **Felügyelet nélküli aláírás nélküli illesztőprogramok a Windows, ahol ez engedélyezett verziói**  
 Lehetővé teszi, hogy a feladatütemezési művelet aláírás nélküli Windows-eszközillesztőket telepítsen.  

> [!IMPORTANT]  
>  Ez a beállítás nem vonatkozik azokra az operációs rendszerekre, melyekben nem konfigurálható az illesztőprogramok aláírási házirendje.  

##  <a name="BKMK_CaptureNetworkSettings"></a>Hálózati beállítások rögzítése  
 A **Hálózati beállítások rögzítése** feladatütemezési lépéssel rögzítheti a feladatütemezést futtató számítógép Microsoft hálózati beállításait. A beállítások feladatütemezési változókba lesznek mentve, amelyek felülírják a **Hálózati beállítások alkalmazása** feladatütemezési lépésben konfigurált alapértelmezett beállításokat.  

 Ez a feladatütemezési lépés csak normál operációs rendszereken futtatható. Windows PE környezetben nem futtatható. A művelet feladatütemezési változóival kapcsolatban [A Hálózati beállítások rögzítése feladatütemezési művelet változói](task-sequence-action-variables.md#BKMK_CaptureNetworkSettings) című témakörben találhatók további információk.  

### <a name="details"></a>Részletek  
 A lépés **Tulajdonságok** lapján az ebben a szakaszban bemutatott beállításokat konfigurálhatja.  

 Ezenkívül a **Beállítások** lapon a következő műveleteket hajthatja végre:  

-   A lépés letiltása.  

-   Annak megadása, hogy a feladatütemezés folytatódjon-e, ha a lépés futtatása során hiba lép fel.  

-   Feltételek megadása, melyeknek teljesülnie kell a lépés futtatásához.  

 **Név**  
 Egy rövid, felhasználó által definiált nevet ad meg, mely leírja az ebben a lépésben végrehajtott műveletet.  

 **Leírás**  
 Részletesebb információkat biztosít az ebben a lépésben végrehajtott műveletről.  

 **Tartomány- és munkacsoporttagság áttelepítése**  
 A célszámítógép tartomány- és munkacsoporttagsági adatait rögzíti.  

 **Hálózati adapter konfigurációjának áttelepítése**  
 A célszámítógép hálózati adapterének konfigurációját rögzíti. A rögzített adatok között szerepelnek a globális hálózati beállítások, az adapterek száma és az egyes hálózati adapterekhez tartozó beállítások is. A beállítások tartalmazzák a DNS, a WINS, az IP-címek és a portszűrők beállításait is.  

##  <a name="BKMK_CaptureOperatingSystemImage"></a>Operációs rendszer lemezképének rögzítése  
 Az **Operációs rendszer lemezképének rögzítése** feladatütemezési lépéssel egy vagy több lemezképet rögzíthet a referencia-számítógépről, majd azokat egy WIM-fájlban tárolhatja a megadott hálózati megosztáson. Az operációs rendszer Lemezképcsomagjának hozzáadása varázslóval majd importálására használható. WIM-fájlt a Configuration Managerbe a úgy, hogy az informatikai használható operációs rendszerek lemezképalapú központi telepítése.  

 A referencia-számítógép minden kötete (meghajtója) különálló lemezképként lesz rögzítve a .wim fájlban. Ha a hivatkozott számítógépen több kötet van, az eredményül kapott WIM-fájl minden kötethez egy különálló lemezképet fog tartalmazni. Csak az NTFS vagy FAT32 fájlrendszerrel formázott kötetek lesznek rögzítve. Az egyéb formátumú, illetve az USB-kötetek figyelmen kívül lesznek hagyva.  

 A referencia-számítógépen telepített operációs rendszer, amely a Configuration Manager által támogatott, és kell előkészíteni a SysPrep eszköz használatával Windows-verziónak kell lennie. A telepített operációs rendszer kötetének és a rendszerindító kötetnek meg kell egyeznie.  

 Egy olyan Windows-fiókot is meg kell adni, mely rendelkezik írási engedéllyel a kiválasztott hálózati megosztáson.  

 Ez a feladatütemezési lépés csak Windows PE környezetben futtatható. Normál operációs rendszereken nem futtatható. A művelet feladatütemezési változóival kapcsolatban [Az Operációs rendszer lemezképének rögzítése feladatütemezési művelet változói](task-sequence-action-variables.md#BKMK_CaptureOperatingSystemImage) című témakörben találhatók további információk.  

### <a name="details"></a>Részletek  
 A lépés **Tulajdonságok** lapján az ebben a szakaszban bemutatott beállításokat konfigurálhatja.  

 Ezenkívül a **Beállítások** lapon a következő műveleteket hajthatja végre:  

-   A lépés letiltása.  

-   Annak megadása, hogy a feladatütemezés folytatódjon-e, ha a lépés futtatása során hiba lép fel.  

-   Feltételek megadása, melyeknek teljesülnie kell a lépés futtatásához.  

 **Név**  
 Egy rövid, felhasználó által definiált név, mely leírja az ebben a lépésben végrehajtott műveletet.  

 **Leírás**  
 Részletesebb információk az ebben a lépésben végrehajtott műveletről.  

 **Cél**  
 A fájl fájlrendszerbeli elérési útja a helyre, amely a Configuration Manager használ, amikor a rögzített operációsrendszer-lemezképet tárolja.  

 **Leírás**  
 A .WIM fájlban tárolt rögzített operációsrendszer-lemezképhez felhasználó által definiált leírás, melyet nem kötelező megadni.  

 **Verzió**  
 A rögzített operációsrendszer-lemezképhez hozzárendelendő, felhasználó által definiált verziószám, melyet nem kötelező megadni. Ez az érték betűk és számok tetszőleges kombinációja lehet, és a.WIM fájl tárolja.  

 **Hozta létre**  
 Az operációs rendszer lemezképét létrehozó felhasználó neve, melyet a WIM-fájl tárol, és nem kötelező megadni.  

 **Operációs rendszer lemezképének rögzítése fiók**  
 Meg kell adnia a Windows-fiókot, amely rendelkezik jogosultságokkal a megadott hálózati megosztáson. A **Beállítás** gombra kattintva adhatja meg a Windows-fiók nevét.  

##  <a name="BKMK_CaptureUserState"></a>Felhasználói állapot rögzítése  
 A **Felhasználói állapot rögzítése** feladatütemezési lépés lehetővé teszi, hogy a Felhasználóáttelepítő (USMT) eszközzel rögzítse a felhasználó állapotát és a beállításokat a feladatütemezést futtató számítógépen. Ez a feladatütemezési lépés a **Felhasználói állapot visszaállítása** feladatütemezési lépéssel együtt használható. Az USMT 3.0.1-es és újabb, ez a beállítás mindig titkosítja az USMT által létrehozott és a Configuration Manager által kezelt titkosítási kulcs használatával.  

 További információ a felhasználói állapot operációs rendszerek központi telepítése közbeni kezeléséről: [felhasználói állapot kezelése](../get-started/manage-user-state.md).  

 Használhatja a **felhasználói állapot rögzítése** feladatütemezési lépést együtt a **állapot tárolásának igénylése** és **állapot tárolásának felszabadítása** feladatütemezési lépést, ha az állapotbeállításokat mentse, vagy szeretné visszaállítani a beállításokat egy állapotáttelepítési pontot a Configuration Manager-hely.  

 A **Felhasználói állapot rögzítése** feladatütemezési lépés az USMT eszköz leggyakrabban használt beállításait csak részlegesen teszi elérhetővé. Az OSDMigrateAdditionalCaptureOptions feladatütemezési változóval további parancssori kapcsolókat is megadhat.  

 Ez a feladatütemezési lépés csak Windows PE környezetben futtatható. Normál operációs rendszereken nem futtatható. A művelet feladatütemezési változóival kapcsolatban [A Felhasználói állapot rögzítése feladatütemezési művelet változói](task-sequence-action-variables.md#BKMK_CaptureUserState) című témakörben találhatók további információk.  

### <a name="details"></a>Részletek  
 A lépés **Tulajdonságok** lapján az ebben a szakaszban bemutatott beállításokat konfigurálhatja.  

 Ezenkívül a **Beállítások** lapon a következő műveleteket hajthatja végre:  

-   A lépés letiltása.  

-   Annak megadása, hogy a feladatütemezés folytatódjon-e, ha a lépés futtatása során hiba lép fel.  

-   Feltételek megadása, melyeknek teljesülnie kell a lépés futtatásához.  

 **Név**  
 Egy rövid, felhasználó által definiált név, mely leírja az ebben a lépésben végrehajtott műveletet.  

 **Leírás**  
 Részletesebb információk az ebben a lépésben végrehajtott műveletről.  

 **Felhasználói állapot áttelepítését szolgáló eszközcsoma**  
 Adja meg a Configuration Manager-csomagot, amely a kívánt Ez a feladatütemezési lépés a felhasználói állapotot és beállításokat rögzítésekor használandó USMT-verziót tartalmazza. Ez a csomag nem igényel programot. A feladatütemezési lépés futtatásakor a feladatütemezés az USMT eszköz a csomagban lévő verziói közül a megadottat fogja használni. Annak az operációs rendszernek az architektúrája alapján, melynek az állapotát rögzíti, olyan csomagot adjon meg, mely az USMT eszköz 32 bites vagy x64 verzióját tartalmazza.  

 **Összes felhasználói profil rögzítése a szokásos beállításokkal**  
 Ezzel a beállítással minden felhasználói profiladatot áttelepíthet. A beállítás alapértelmezés szerint engedélyezett.  

 Ha ezt a beállítást, de nem engedélyezi a felhasználói állapot visszaállítása feladatütemezési lépésben a helyi számítógép-felhasználói profilok visszaállítása beállítást, a feladatütemezés sikertelen lesz, mert a Configuration Manager jelszavak hozzárendelése nélkül nem tudja áttelepíteni az új fiókokat. Továbbá, ha az **Új feladatütemezés létrehozása** varázslóval létrehoz egy feladatütemezést egy **Meglévő lemezképcsomag telepítéséhez**, a létrejövő feladatütemezés alapértelmezés szerint „Az összes felhasználói profil rögzítése a szokásos beállítások használatával” beállítást használja, de nem alkalmazza a helyi számítógép-felhasználói profilok (azaz nem tartományi fiókok) visszaállítására szolgáló beállítást.  

 Engedélyezze a **Helyi számítógép-felhasználói profilok visszaállítása** beállítást, és adja meg a jelszót az áttelepítendő fiókhoz. Manuálisan létrehozott feladatütemezéseknél ez a beállítás a Felhasználói állapot visszaállítása lépésben található. Az **Új feladatütemezés létrehozása** varázslóval létrehozott feladatütemezésekben ez a beállítás a varázsló **Felhasználói fájlok és beállítások visszaállítása** lapján található.  

 Ez nem érvényes, ha nincsenek helyi felhasználói fiókok.  

 **Felhasználói profilok rögzítésének testre szabása**  
 Ezzel a beállítással adhat meg egyéni profilfájl-áttelepítést. A **Fájlok** gombra kattintva válassza ki azokat a konfigurációs fájlokat, amelyeket az USMT eszköznek használnia kell ehhez a lépéshez. Meg kell adnia egy egyéni .xml fájlt, amely arra vonatkozó szabályokat tartalmaz, hogy mely felhasználói állapotfájlokat kell áttelepíteni.  

 **Kattintson ide a konfigurációs fájlok kiválasztásához:**  
 Ezzel a lehetőséggel jelölheti ki a konfigurációs fájlokat az USMT-csomagban, melyeket használni kíván a felhasználói profilok rögzítéséhez. Kattintson a **Fájlok** gombra a **Konfigurációs fájlok** párbeszédpanel megnyitásához. Konfigurációs fájl megadásához írja be a fájl nevét a **Fájlnév** sorba, majd kattintson a **Hozzáadás** gombra.  

 **Részletes naplózás engedélyezése**  
 Ha bejelöli ezt a beállítást, részletesebb naplófájl-információk jönnek létre. Állapotok rögzítésekor a Scanstate.log napló jön létre és tárolódik a feladatütemezés naplómappájában, melynek az alapértelmezett mappája a \windows\system32\ccm\logs.  

 **Titkosított fájlrendszert használó fájlok mellőzése**  
 Akkor engedélyezze ezt a beállítást, ha ki szeretné hagyni a titkosított fájlrendszerrel (EFS) titkosított fájlok rögzítését, beleértve a profilfájlokat is. Az operációs rendszertől és az USMT eszköz verziójától függően előfordulhat, hogy a titkosított fájlok nem lesznek olvashatók visszaállítás után. További információt az USMT eszköz dokumentációjában talál.  

 **Másolás fájlrendszerelérés használatával a fájlrendszer elérése**  
 Ha engedélyezi ezt a lehetőséget, megadhatja a következő beállítások bármelyikét:  

-   **Továbbra is, ha egyes fájlok nem rögzíthetők**: Ezzel a beállítással az áttelepítési folyamat folytatódik, még akkor is, ha egyes fájlok nem rögzíthetők. Ha letiltja ezt a beállítást, és egy fájl nem rögzíthető, a feladatütemezési lépés sikertelen lesz. A beállítás alapértelmezés szerint engedélyezett.  

-   **Helyi rögzítés fájlok másolása helyett hivatkozásokat használva**: A fájlok rögzítése rögzített NTFS-hivatkozásokkal használandó beállítás engedélyezése.  

     További információk az adatok rögzített hivatkozásokkal történő áttelepítésével kapcsolatban: [Hard-Link Migration Store](http://go.microsoft.com/fwlink/p/?LinkId=240222) (Rögzített hivatkozásos áttelepítési tár)  

-   **Üzemmódban végezze a rögzítést (csak Windows PE)**: Engedélyezi ezt a beállítást, a teljes operációs rendszer helyett Windows PE környezetben a felhasználói állapot rögzítése érdekében.  

 **Rögzítés a VSS Volume Copy Shadow szolgáltatások () használatával**  
 Ez a beállítás akkor is lehetővé teszi a fájlok rögzítését, ha azokat egy másik alkalmazás szerkesztésre zárolta.  

##  <a name="BKMK_CaptureWindowsSettings"></a>Windows beállítások rögzítése  
 A **Windows-beállítások rögzítése** feladatütemezési lépéssel rögzítheti a feladatütemezést futtató számítógép Windows-beállításait. A beállítások feladatütemezési változókba lesznek mentve, melyek felülírják a **Windows beállítások alkalmazása** feladatütemezési lépésben konfigurált alapértelmezett beállításokat.  

 Ez a feladatütemezési lépés Windows PE környezetben és normál operációs rendszeren is futtatható. A művelet feladatütemezési változóival kapcsolatban [A Windows-beállítások rögzítése feladatütemezési művelet változói](task-sequence-action-variables.md#BKMK_CaptureWindowsSettings) című témakörben találhatók további információk.  

### <a name="details"></a>Részletek  
 A lépés **Tulajdonságok** lapján az ebben a szakaszban bemutatott beállításokat konfigurálhatja.  

 Ezenkívül a **Beállítások** lapon a következő műveleteket hajthatja végre:  

-   A lépés letiltása.  

-   Annak megadása, hogy a feladatütemezés folytatódjon-e, ha a lépés futtatása során hiba lép fel.  

-   Feltételek megadása, melyeknek teljesülnie kell a lépés futtatásához.  

 **Név**  
 Egy rövid, felhasználó által definiált név, mely leírja az ebben a lépésben végrehajtott műveletet.  

 **Leírás**  
 Részletesebb információk az ebben a lépésben végrehajtott műveletről.  

 **Számítógépnév áttelepítése**  
 Ezzel a lehetőséggel rögzítheti a számítógép NetBIOS-számítógépnevét.  

 **Regisztrált felhasználó és szervezet nevét áttelepítése**  
 Ezzel a lehetőséggel rögzítheti a regisztrált felhasználó- és a szervezetneveket a számítógépről.  

 **Időzóna áttelepítése**  
 Ezzel a lehetőséggel rögzítheti a számítógép időzóna-beállítását.  

##  <a name="BKMK_CheckReadiness"></a>Készültség ellenőrzése  
 A **Felkészültség ellenőrzése** feladatütemezési lépéssel ellenőrizheti, hogy a célszámítógép megfelel-e a megadott központi telepítési előfeltételeknek.  

### <a name="details"></a>Részletek  
 A lépés **Tulajdonságok** lapján az ebben a szakaszban bemutatott beállításokat konfigurálhatja.  

 Ezenkívül a **Beállítások** lapon a következő műveleteket hajthatja végre:  

-   A lépés letiltása.  

-   Annak megadása, hogy a feladatütemezés folytatódjon-e, ha a lépés futtatása során hiba lép fel. Ehhez a lépéshez ne jelölje be ezt a beállítást, mert ekkor a lépés csak a készenléti ellenőrzéseket naplózza, és nem állítja le a feladatütemezést, ha egy ellenőrzés nem sikerül.  

-   Feltételek megadása, melyeknek teljesülnie kell a lépés futtatásához.  

 **Név**  
 Egy rövid, felhasználó által definiált név, mely leírja az ebben a lépésben végrehajtott műveletet.  

 **Leírás**  
 Részletesebb információk az ebben a lépésben végrehajtott műveletről.  

 **Minimális memória (MB)**  
 Ezzel a beállítással ellenőrizheti, hogy a rendszerben található memória mennyisége (MB-ban) eléri-e vagy meghaladja-e a megadott mennyiséget. Alapértelmezés szerint ez a beállítás be van jelölve.  

 **Minimális processzorsebesség (MHz)**  
 Ezzel a beállítást ellenőrizheti, hogy a célszámítógép processzorának sebessége (MHz-ben) eléri-e vagy meghaladja-e a megadott mennyiséget. Alapértelmezés szerint ez a beállítás be van jelölve.  

 **Ellenőrizze a minimális szabad lemezterület (MB)**  
 Ezzel a beállítással ellenőrizheti, hogy a célszámítógépen rendelkezésre álló szabad tárterület (MB-ban) eléri-e vagy meghaladja-e a megadott mennyiséget.  

 **Győződjön meg arról, frissíteni kell az aktuális operációs rendszer**  
 Ezzel a beállítással ellenőrizheti, hogy a célszámítógépen telepített operációs rendszer megfelel-e a megadott követelménynek. A beállítás alapértelmezett értéke az **ÜGYFÉL**.  

##  <a name="BKMK_ConnectToNetworkFolder"></a>Csatlakozás hálózati mappához  
 A **Csatlakozás hálózati mappához** feladatütemezési művelettel kapcsolatot létesíthet egy megosztott hálózati mappával.  

 Ez a feladatütemezési lépés normál operációs rendszeren és Windows PE környezetben is futtatható. A művelet feladatütemezési változóival kapcsolatban [A Hálózati beállítások rögzítése feladatütemezési művelet változói](task-sequence-action-variables.md#BKMK_ConnecttoNetworkFolder) című témakörben találhatók további információk.  

### <a name="details"></a>Részletek  
 A lépés **Tulajdonságok** lapján az ebben a szakaszban bemutatott beállításokat konfigurálhatja.  

 Ezenkívül a **Beállítások** lapon a következő műveleteket hajthatja végre:  

-   A lépés letiltása.  

-   Annak megadása, hogy a feladatütemezés folytatódjon-e, ha a lépés futtatása során hiba lép fel.  

-   Feltételek megadása, melyeknek teljesülnie kell a lépés futtatásához.  

##  <a name="BKMK_ConvertDisktoDynamic"></a>Lemez konvertálása dinamikus lemezzé  
 A **Lemez konvertálása dinamikus lemezzé** feladatütemezési lépéssel egy fizikai lemezt alaplemez típusúról dinamikus lemez típusúra konvertálhat.  

 Ez a feladatütemezési lépés normál operációs rendszeren és Windows PE környezetben is futtatható. A művelet feladatütemezési változóival kapcsolatban [A Lemez konvertálása dinamikus lemezzé feladatütemezés műveleti változói](task-sequence-action-variables.md#BKMK_ConvertDisk) című témakörben találhatók további információk.  

### <a name="details"></a>Részletek  
 A lépés **Tulajdonságok** lapján az ebben a szakaszban bemutatott beállításokat konfigurálhatja.  

 Ezenkívül a **Beállítások** lapon a következő műveleteket hajthatja végre:  

-   A lépés letiltása.  

-   Annak megadása, hogy a feladatütemezés folytatódjon-e, ha a lépés futtatása során hiba lép fel.  

-   Feltételek megadása, melyeknek teljesülnie kell a lépés futtatásához.  

 **Név**  
 Egy rövid, felhasználó által definiált név, mely leírja az ebben a lépésben végrehajtott műveletet.  

 **Leírás**  
 Részletesebb információk az ebben a lépésben végrehajtott műveletről.  

 **Lemezszám**  
 A konvertálni kívánt lemez fizikai lemezszáma.  

##  <a name="BKMK_DisableBitLocker"></a>A BitLocker letiltása  
 A **BitLocker inaktívvá tétele** feladatütemezési lépéssel inaktívvá teheti a BitLocker-titkosítást az operációs rendszer jelenlegi meghajtóján vagy egy adott meghajtón. Ez a művelet nem titkosított szövegként láthatóvá teszi a merevlemez kulcsvédőit, de a meghajtó tartalmát nem fejti vissza. Ennek következtében a művelet szinte azonnal elkészül.  

> [!NOTE]  
>  A BitLocker meghajtótitkosítás lemezkötetek tartalmához biztosít alacsony szintű titkosítást.  

 Ha több meghajtó van titkosítva, akkor a BitLockert minden adatmeghajtón inaktívvá kell tenni, mielőtt inaktívvá tenné az operációs rendszer meghajtóján.  

 Ez a feladatütemezési lépés csak normál operációs rendszereken futtatható. Windows PE környezetben nem futtatható.  

### <a name="details"></a>Részletek  
 A lépés **Tulajdonságok** lapján az ebben a szakaszban bemutatott beállításokat konfigurálhatja.  

 Ezenkívül a **Beállítások** lapon a következő műveleteket hajthatja végre:  

-   A lépés letiltása.  

-   Annak megadása, hogy a feladatütemezés folytatódjon-e, ha a lépés futtatása során hiba lép fel.  

-   Feltételek megadása, melyeknek teljesülnie kell a lépés futtatásához.  

 **Név**  
 Egy rövid, felhasználó által definiált nevet ad meg, mely leírja az ebben a lépésben végrehajtott műveletet.  

 **Leírás**  
 Részletesebb információkat biztosít az ebben a lépésben végrehajtott műveletről.  

 **Operációs rendszer jelenlegi meghajtója**  
 Inaktívvá teszi a BitLockert az operációs rendszer jelenlegi meghajtóján.  

 **Adott meghajtó**  
 Inaktívvá teszi a BitLockert egy adott meghajtón. A legördülő lista használatával adhatja meg a meghajtót, amelyen inaktívvá kívánja tenni a BitLockert.  

##  <a name="BKMK_DownloadPackageContent"></a>Csomag tartalmának letöltése  
 A **Csomag tartalmának letöltése** feladatütemezési lépéssel töltheti le a következő csomagtípusok bármelyikét:  

-   Operációsrendszer-lemezképek  

-   Operációs rendszer verziófrissítő csomagjai  

-   Illesztőprogram-csomagok  

-   Csomagok  

 Ez a lépés az alábbi esetekben használható jól operációsrendszer-frissítési feladatütemezésekben:  

-   Egyetlen, az x86- és x64-alapú platformokkal is együttműködő frissítési feladatütemezés használata. Ezt úgy teheti meg, hogy a **Verziófrissítés előkészítése** csoportban két **Csomag tartalmának letöltése** lépést ad meg olyan feltételekkel, amelyek észlelik az ügyfél architektúráját, és csak az operációs rendszer megfelelő verziófrissítési csomagját töltik le. Az egyes **Csomag tartalmának letöltése** lépéseket konfigurálja ugyanazon változó használatára, és használja az **Operációs rendszer verziófrissítésének elvégzése** lépés adathordozó-útvonalának változóját.  

-   A megfelelő illesztőprogam-csomag dinamikus letöltéséhez használjon két **Csomag tartalmának letöltése** lépést olyan feltételekkel, amelyek észlelik az egyes illesztőprogram-csomagokhoz tartozó megfelelő hardvertípust. Az egyes **Csomag tartalmának letöltése** lépéseket konfigurálja ugyanazon változó használatára, és használja a változót az **Előkészített tartalom** értékként az **Operációs rendszer verziófrissítésének elvégzése** lépés illesztőprogramokra vonatkozó szakaszában.  

Ez a feladatütemezési lépés normál operációs rendszeren és Windows PE környezetben is futtatható. Kívánja, mentheti a csomagot a Configuration Manager-ügyfél gyorsítótárában WinPE környezetben azonban nem támogatott.

### <a name="details"></a>Részletek  
 A lépés **Tulajdonságok** lapján az ebben a szakaszban bemutatott beállításokat konfigurálhatja.  

 Ezenkívül a **Beállítások** lapon a következő műveleteket hajthatja végre:  

-   A lépés letiltása.  

-   Annak megadása, hogy a feladatütemezés folytatódjon-e, ha a lépés futtatása során hiba lép fel.  

-   Feltételek megadása, melyeknek teljesülnie kell a lépés futtatásához.  

 **Név**  
 Egy rövid, felhasználó által definiált nevet ad meg, mely leírja az ebben a lépésben végrehajtott műveletet.  

 **Leírás**  
 Részletesebb információkat biztosít az ebben a lépésben végrehajtott műveletről.  

 **Csomag kiválasztása** ikon  
 Kattintson az ikonra a letölteni kívánt csomag kiválasztásához. A csomag kiválasztása után ismét az ikonra kattintva kiválaszthat egy további csomagot.  

 **Helyezze be a következő helyen**  
 A következő helyek egyikére mentheti el a csomagot:  

-   **Feladatütemezési munkakönyvtár**  

-   **A Configuration Manager-ügyfél gyorsítótára**: Ez a beállítás használatával tárolhatja a tartalmakat az ügyfél gyorsítótárában. Így az ügyfél társ-gyorsítótárazási forrásként működhet más társ-gyorsítótárazási ügyfelek számára. További információkért lásd: [készítse elő a Windows PE társ-gyorsítótárazás WAN-hálózati forgalom csökkentése érdekében](../get-started/prepare-windows-pe-peer-cache-to-reduce-wan-traffic.md).  

-   **Egyéni elérési út**  

 **Elérési út mentése változóként**  
 Az elérési utat elmentheti változóként, melyet felhasználhat más feladatütemezési lépésekben. A Configuration Manager egy numerikus utótagot ad hozzá a változó nevét. Ha % változót adja meg például*tartalom*% egyéni változóként, akkor a legfelső szintű tároló a hivatkozott tartalom (amely több csomag is lehet). Tekintse meg a változó, ha szeretne hozzáadni egy numerikus utótagot a változót. Például az első csomag meg fog hivatkozni %*tartalom01*% változó. Amikor egy későbbi lépésben, például az operációs rendszer verziófrissítésének elvégzése, a változó % szeretné használni*tartalom02*% vagy %*mycontent03*%, ahol a szám, amelyben a csomag az lépésben felsorolt sorrendben felel meg.  

 **Ha egy csomag letöltése sikertelen, a listában szereplő további csomagok letöltésének folytatása**  
 Azt határozza meg, hogy ha egy csomag letöltése sikertelen, a rendszer lépjen a listában szereplő következő csomagra, és kezdje meg annak letöltését.  

##  <a name="BKMK_EnableBitLocker"></a>A BitLocker engedélyezése  
 A **BitLocker engedélyezése** feladatütemezési lépéssel engedélyezheti a BitLocker-titkosítást a merevlemez legalább két partícióján. Az első aktív partíció tartalmazza a Windows rendszerindítási kódját. Egy másik partíció tartalmazza az operációs rendszert. A rendszerindítási partíciónak titkosítatlannak kell maradnia.  

 Windows PE környezetben a **Kiépítés előtti BitLocker** feladatütemezési lépéssel engedélyezheti a BitLockert a kívánt meghajtón. További információkat a [Kiépítés előtti BitLocker](#BKMK_PreProvisionBitLocker) című témakörben olvashat.  

> [!NOTE]  
>  A BitLocker meghajtótitkosítás lemezkötetek tartalmához biztosít alacsony szintű titkosítást.  

 A **BitLocker engedélyezése** lépés csak normál operációs rendszerekben futtatható, Windows PE környezetben nem futtatható. A művelet feladatütemezési változóival kapcsolatban [A BitLocker engedélyezése feladatütemezési művelet változói](task-sequence-action-variables.md#BKMK_EnableBitLocker) című témakörben találhatók további információk.  

 Ha a **Csak TPM**, a **TPM és indítókulcs USB-n** vagy a **TPM és PIN-kód** lehetőséget adja meg, a platformmegbízhatósági modulnak (TPM) a következő állapotban kell lennie ahhoz, hogy futtatni lehessen a **BitLocker engedélyezése** lépést:  

-   Engedélyezve  

-   Aktiválva  

-   Tulajdonjog engedélyezve  

 A feladatütemezési lépés el tudja végezni a TPM esetlegesen fennmaradó inicializálási lépéseit, mert a hátralévő lépésekhez nem szükséges fizikai jelenlét vagy újraindítás. A **BitLocker engedélyezése** feladatütemezési lépés által szükség esetén transzparens módon végrehajtható fennmaradó TPM-inicializálási lépések a következők:  

-   Ellenőrzőkulcspár létrehozása  

-   Tulajdonosazonosító-érték létrehozása és letétbe helyezése az Active Directoryban, amit az érték támogatásához ki kellett volna terjeszteni  

-   Saját tulajdonba vétel  

-   A tároló-gyökérkulcs létrehozása, vagy alaphelyzetbe állítása, ha már létezik, de nem kompatibilis  

 Ha azt szeretné, hogy a **BitLocker engedélyezése** lépés várja meg, amíg a meghajtótitkosítási folyamat befejeződik, mielőtt megkezdődne a feladatütemezés következő lépése, jelölje be a **Várakozás** jelölőnégyzetet. Ha nem jelöli be a **Várakozás** jelölőnégyzetet, a meghajtótitkosítási folyamat a háttérben fog futni, a feladatütemezés végrehajtása pedig azonnal folytatódik a következő lépéssel.  

 A BitLockerrel egy számítógéprendszer több meghajtója is titkosítható (operációsrendszer- és adatmeghajtók is). Egy adatmeghajtó titkosításához az operációs rendszernek már titkosítva kell lennie, és a titkosítási folyamatnak már késznek kell lennie, mert az adatmeghajtók kulcsvédői az operációs rendszer meghajtóján vannak tárolva. Emiatt ha ugyanabban a folyamatban titkosítja az operációs rendszer meghajtóját és az adatmeghajtót, a várakozási lehetőséget be kell jelölni a BitLocker az operációs rendszer meghajtóján való használatát engedélyező lépésnél.  

 Ha a merevlemez már titkosítva van, de a BitLocker inaktívvá van téve, akkor a BitLocker újraengedélyezi a kulcsvédőt vagy kulcsvédőket, és szinte azonnal elkészül. Ebben az esetben nem szükséges a merevlemez újbóli titkosítása.  

 A művelet feladatütemezési változóival kapcsolatban [A BitLocker engedélyezése feladatütemezési művelet változói](task-sequence-action-variables.md#BKMK_EnableBitLocker) című témakörben találhatók további információk.  

### <a name="details"></a>Részletek  
 A lépés **Tulajdonságok** lapján az ebben a szakaszban bemutatott beállításokat konfigurálhatja.  

 Ezenkívül a **Beállítások** lapon a következő műveleteket hajthatja végre:  

-   A lépés letiltása.  

-   Annak megadása, hogy a feladatütemezés folytatódjon-e, ha a lépés futtatása során hiba lép fel.  

-   Feltételek megadása, melyeknek teljesülnie kell a lépés futtatásához.  

 **Név**  
 Egy leíró nevet ad meg a feladatütemezési lépéshez.  

 **Leírás**  
 Lehetővé teszi a feladatütemezési lépés ismertetésének megadását.  

 **Válassza ki a titkosítandó meghajtót**  
 A titkosítandó meghajtót adja meg. Az operációs rendszer jelenlegi meghajtójának titkosításához válassza **Az operációs rendszer jelenlegi meghajtója** lehetőséget, majd konfigurálja a következő beállítások egyikét a kulcskezeléshez:  

-   **Csak TPM**: Ezt a beállítást csak platformmegbízhatósági modul (TPM) használata.  

-   **Indítókulcs csak USB-n**: Válassza ki az ezzel a beállítással egy USB flash meghajtón tárolt indítókulcsot használhat. Ha ezt a beállítást jelöli be, a BitLocker zárolja a normál rendszerindítási folyamatot, mindaddig, amíg nem csatlakoztatnak egy, a BitLocker indítókulcsot tartalmazó USB-eszközt a számítógéphez.  

-   **TPM és indítókulcs USB-n**: Ezt a beállítást használja a TPM-et és egy USB flash meghajtón tárolt indítókulcsot. Ha ezt a beállítást jelöli be, a BitLocker zárolja a normál rendszerindítási folyamatot, mindaddig, amíg nem csatlakoztatnak egy, a BitLocker indítókulcsot tartalmazó USB-eszközt a számítógéphez.  

-   **TPM és PIN-kód**:  Ezt a beállítást használja a TPM-et és egy személyes azonosítószámot (PIN). Ha ezt a beállítást jelöli be, a BitLocker zárolja a normál rendszerindítási folyamatát, mindaddig, amíg a felhasználó meg nem adja a PIN-kódot.  

 Egy adott, operációs rendszert nem tartalmazó adatmeghajtó titkosításához válassza az**Adott meghajtó** lehetőséget, majd válassza ki a meghajtót a listából.  

 **A helyreállítási kulcs helyének kiválasztása**  
 A helyreállítási jelszó létrehozási helyének megadásához válassza **Az Active Directoryban** lehetőséget, így letétbe helyezheti a jelszót az Active Directoryban. Ha ezt a beállítást választja, ki kell terjesztenie az Active Directoryt a helyre, hogy a BitLocker vonatkozó helyreállítási adatai is mentve legyenek. Ha úgy dönt, hogy egyáltalán nem hoz létre jelszót, válassza a **Ne hozzon létre helyreállítási kulcsot** lehetőséget. A jelszó létrehozása azonban ajánlott eljárás.  

 **Várjon, amíg a BitLocker a meghajtótitkosítási folyamat folyamatos feladatütemezés végrehajtása előtt az összes meghajtón befejezte**  
 Ezzel a lehetőséggel biztosíthatja, hogy a BitLocker meghajtótitkosítás befejeződjön a feladatütemezés következő lépésének futtatása előtt. Ha bejelöli ezt a beállítást, a felhasználó nem fog tudni bejelentkezni a számítógépre, amíg a rendszer nem titkosította a teljes lemezkötetet.  

 Egy nagy méretű merevlemez titkosításakor a titkosítási folyamat akár óráig is eltarthat. Ha nem jelöli be ezt a lehetőséget, a feladatütemezés azonnal tovább tud majd haladni.  

##  <a name="BKMK_FormatandPartitionDisk"></a>Lemez formázása és particionálása  
 A **Lemez formázása és particionálása** feladatütemezési lépéssel formázhatja és particionálhatja a célszámítógép kívánt lemezét.  

> [!IMPORTANT]  
>  Minden beállítás, melyet ebben a feladatütemezési lépésben ad meg, az egyetlen megadott lemezre vonatkozik. Ha a célszámítógép egy másik lemezét is szeretné formázni és particionálni, hozzá kell adnia egy további **Lemez formázása és particionálása** feladatütemezési lépést a feladatütemezéshez.  

 Ez a feladatütemezési lépés csak Windows PE környezetben futtatható. Normál operációs rendszereken nem futtatható. A művelet feladatütemezési változóival kapcsolatban [A Lemez formázása és particionálása feladatütemezési művelet változói](task-sequence-action-variables.md#BKMK_FormatPartitionDisk) című témakörben találhatók további információk.  

### <a name="details"></a>Részletek  
 A lépés **Tulajdonságok** lapján az ebben a szakaszban bemutatott beállításokat konfigurálhatja.  

 Ezenkívül a **Beállítások** lapon a következő műveleteket hajthatja végre:  

-   A lépés letiltása.  

-   Annak megadása, hogy a feladatütemezés folytatódjon-e, ha a lépés futtatása során hiba lép fel.  

-   Feltételek megadása, melyeknek teljesülnie kell a lépés futtatásához.  

 **Név**  
 Egy rövid, felhasználó által definiált név, mely leírja az ebben a lépésben végrehajtott műveletet.  

 **Leírás**  
 Részletesebb információk az ebben a lépésben végrehajtott műveletről.  

 **Lemezszám**  
 A formázni kívánt lemez fizikai lemezszáma. A szám a Windows eszközfelsorolási sorrendjén alapul.  

 **Lemeztípus**  
 A formázni kívánt lemez típusa. A legördülő listából két lehetőséget választhat ki:  

-   Normál (MBR) – fő rendszerindító rekord.  

-   GPT – GUID partíciós tábla  

> [!NOTE]  
>  Ha a lemez típusát a **Normál (MBR)** értékről **GPT**-re módosítja, és a partícióelrendezésben kiterjesztett partíció található, az összes kiterjesztett és logikai partíció el lesz távolítva az elrendezésből. A lemez típusának módosítása előtt a program kérni fogja, hogy erősítse meg ezt a műveletet.  

 **Kötet**  
 A létrejövő partícióval vagy kötettel kapcsolatos konkrét információk, beleértve a következőket:  

-   Név  

-   Fennmaradó szabad lemezterület  

 Új partíció létrehozásához az **Új** gombra kattintva megnyithatja a **Partíció tulajdonságai** párbeszédpanelt. Megadhatja a partíció típusát és méretét, illetve azt, hogy ez lesz-e a rendszerindító partíció. Meglévő partíció módosításához kattintson a módosítani kívánt partícióra, majd a Tulajdonságok gombra. Merevlemez-partíciók beállításával kapcsolatos további információkért tekintse meg a következők egyikét:  

-   [UEFI/GPT-alapú merevlemez-partíciók konfigurálása](http://go.microsoft.com/fwlink/?LinkID=272104)  

-   [BIOS/MBR-alapú merevlemez-partíciók konfigurálása](http://go.microsoft.com/fwlink/?LinkId=272105)  

 Egy partíció törléséhez válassza ki a törölni kívánt partíciót, majd kattintson a **Törlés** gombra.  

##  <a name="BKMK_InstallApplication"></a>Alkalmazás telepítése  
 Az **Alkalmazás telepítése** feladatütemezési lépéssel telepíthet alkalmazásokat a feladatütemezés részeként. Ezzel a lépéssel olyan alkalmazásokat telepíthet, melyeket a feladatütemezési lépés ad meg, vagy olyan alkalmazásokat, melyek feladatütemezési változók egy dinamikus listájában vannak megadva. Ezen lépés futtatásakor az alkalmazás telepítése azonnal megkezdődik, anélkül, hogy kivárná a házirend-lekérdezési időközt.  

 A telepített alkalmazásoknak meg kell felelnie a következő feltételeknek:  

-   Az alkalmazásnak a Windows Installer vagy a parancsfájl telepítő központi telepítési típusának kell lennie. A Windows-alkalmazáscsomag (.appx fájl) típusú központi telepítések nem támogatottak.  

-   A helyi rendszerfiókban, és nem a felhasználói fiókban kell futnia.  

-   Nem működhet együtt az asztallal. A programnak csendesen vagy felügyelet nélküli módban kell futnia.  

-   Nem kezdeményezhet önállóan újraindítást. Az alkalmazásnak a normál újraindítási kóddal, a 3010-es kilépési kóddal kell újraindítást igényelnie. Ez biztosítja, hogy a feladatütemezési lépés megfelelően fogja kezelni az újraindítást. Ha az alkalmazás valóban egy 3010-es kilépési kóddal tér vissza, a mögöttes feladatütemező motor végrehajtja az újraindítást. Az újraindítás után a feladatütemezés végrehajtása automatikusan folytatódik.  

 Az **Alkalmazás telepítése** lépés futtatásakor az alkalmazás ellenőrzi, hogy a követelményszabályok és az észlelési módszer alkalmazhatók-e az alkalmazás központi telepítési típusaira. Az alkalmazás ezen ellenőrzés eredménye alapján az alkalmazható központi telepítési típust telepíti. Ha egy központi telepítési típus függőségeket tartalmaz, a program kiértékeli a függő központi telepítési típust, és az Alkalmazás telepítése lépés részeként telepíti. Az alkalmazásfüggőségek nem támogatottak különálló adathordozók esetén.  

> [!NOTE]  
>  Egy másik alkalmazást felülíró alkalmazás telepítése esetén a feladatütemezési lépés sikertelen lesz, ha nem állnak rendelkezésre a felülírt alkalmazás tartalomfájljai. Tegyük fel például, hogy a Microsoft Visio 2010 telepítve van egy ügyfélen vagy egy rögzített lemezképen. Amikor az Alkalmazás telepítése feladatütemezési lépés futtatásával telepíteni szeretné a Microsoft Visio 2013-at, a Microsoft Visio 2010 (a felülírt alkalmazás) tartalomfájljainak elérhetőnek kell lennie egy terjesztési ponton, különben a feladatütemezés végrehajtása sikertelen lesz. Az olyan ügyfeleken vagy rögzített lemezképeken, melyeken nincs telepítve a Microsoft Visio, a Microsoft Visio 2010 tartalomfájljainak keresése nélkül megtörténik a Microsoft Visio 2013 telepítése.  

> [!NOTE]
> Használhatja a SMSTSMPListRequestTimeoutEnabled és SMSTSMPListRequestTimeout beépített változók engedélyezze és adja meg, hány ezredmásodperc feladatütemezés várakozzon, mielőtt újból megkísérli az alkalmazás vagy a szoftver telepítését frissítése után nem sikerült beolvasnia a felügyeleti pontok listáját a helymeghatározási szolgáltatásoktól. További információkért lásd: [feladat feladatütemezési beépített varliables](task-sequence-built-in-variables.md).

 Ez a feladatütemezési lépés csak normál operációs rendszereken futtatható. Windows PE környezetben nem futtatható.  

### <a name="details"></a>Részletek  
 A lépés **Tulajdonságok** lapján konfigurálhatja az ebben a részben ismertetett beállításokat.  

 Ezenkívül a **Beállítások** lapon a következő műveleteket hajthatja végre:  

-   A lépés letiltása.  

-   Ezzel a beállítással újra megpróbálhatja ezt a lépést, ha a számítógép váratlanul újraindul. Azt is megadhatja, hogy a rendszer hányszor próbálkozzon újra az újraindítás után.  

-   Annak megadása, hogy a feladatütemezés folytatódjon-e, ha a lépés futtatása során hiba lép fel.  

-   Feltételek megadása, melyeknek teljesülnie kell a lépés futtatásához.  

 **Név**  
 Egy rövid, felhasználó által definiált név, mely leírja az ebben a lépésben végrehajtott műveletet.  

 **Leírás**  
 Részletesebb információk az ebben a lépésben végrehajtott műveletről.  

 **A következő alkalmazások telepítése**  
 Ez a beállítás azokat az alkalmazásokat adja meg, melyek a megadott sorrendben telepítve lesznek.  

 A Configuration Manager kiszűr minden esetleges letiltott alkalmazást vagy olyan alkalmazást, a következő beállításokkal. Ezek az alkalmazások nem fognak megjelenni a **Válassza ki a telepítendő alkalmazást** párbeszédpanelen.  

-   Csak amikor van bejelentkezett felhasználó  

-   Futtatás felhasználói jogosultságokkal  

 **Alkalmazások telepítése a dinamikus változók listájának megfelelően**  
 Ez a beállítás feladatütemezési változók egy gyűjteményhez vagy egy számítógéphez meghatározott készletének alapnevét adja meg. Ezek a változók határozzák meg a gyűjteményen vagy a számítógépen telepítendő alkalmazásokat. Minden változónév egy közös alapnévből és egy 01-től induló numerikus utótagból áll. Az egyes változók értéke csak az alkalmazás neve lehet, semmi más.  

 A dinamikus változólistával telepítendő alkalmazások esetén a következő beállítást engedélyezni kell a a **általános** lapon, ha az alkalmazás **tulajdonságok** párbeszédpanel: **Ez az alkalmazás az alkalmazás telepítése feladatütemezési művelet ahelyett manuális telepítésének engedélyezése**  

> [!NOTE]  
>  Különálló adathordozós telepítések esetében nem lehet alkalmazásokat telepíteni dinamikus változólistával.  

 Egyetlen alkalmazás egy AA01 nevű feladatütemezési változóval való telepítéséhez például a következő változót kell megadni:  

|Változó neve|Változó értéke|  
|-------------------|--------------------|  
|AA01|Microsoft Office|  

 Két alkalmazás telepítéséhez a következő változókat lehet megadni:  

|Változó neve|Változó értéke|  
|-------------------|--------------------|  
|AA01|Microsoft Lync|  
|AA02|Microsoft Office|  

 Az alábbi feltételek vannak hatással arra, hogy mi lesz telepítve:  

-   Ha a változó értéke tartalmaz bármilyen más adatot az alkalmazás nevén kívül. Ez az alkalmazás nem lesz telepítve, és folytatódik a feladatütemezés végrehajtása.  

-   Ha nem található a megadott alapnévvel és a „01” utótaggal rendelkező változó, egy alkalmazás sem lesz telepítve. Ha bejelöli **Folytatás hiba** a feladatütemezési lépés beállítások lapján, a feladatütemezés végrehajtása folytatódik, amikor egy alkalmazás telepítése sikertelen. Ha a beállítás nincs bejelölve, a feladatütemezés végrehajtása sikertelen lesz, és nem telepíti a hátralevő alkalmazásokat.  

 **Ha egy alkalmazás sikertelen, folytassa a listában szereplő többi alkalmazás telepítését**  
 Ez a beállítás azt határozza meg, hogy folytatódjon a lépés végrehajtása, ha egy adott alkalmazás telepítése sikertelen. Ha ez a beállítás be van jelölve, a feladatütemezés végrehajtása attól függetlenül folytatódik, hogy bármely telepítés hibát ad-e vissza. Ha ez nincs bejelölve, és egy telepítés sikertelen, a feladatütemezési lépés azonnal befejeződik.  

##  <a name="BKMK_InstallDeploymentTools"></a>Központi telepítés eszközeinek telepítése  
 Használja a **központi telepítés eszközeinek telepítése** feladatütemezési lépés a Sysprep központi telepítési eszközöket tartalmazó Configuration Manager telepítéséhez.  

### <a name="details"></a>Részletek  
 A lépés **Tulajdonságok** lapján az ebben a szakaszban bemutatott beállításokat konfigurálhatja.  

 Ezenkívül a **Beállítások** lapon a következő műveleteket hajthatja végre:  

-   A lépés letiltása.  

-   Annak megadása, hogy a feladatütemezés folytatódjon-e, ha a lépés futtatása során hiba lép fel.  

-   Feltételek megadása, melyeknek teljesülnie kell a lépés futtatásához.  

 **Név**  
 Egy rövid, felhasználó által definiált név, mely leírja az ebben a lépésben végrehajtott műveletet.  

 **Leírás**  
 Részletesebb információk az ebben a lépésben végrehajtott műveletről.  

 **Sysprep csomag**  
 Ezzel a beállítással a következő operációs rendszerek a Sysprep központi telepítési eszközöket tartalmazó Configuration Manager-csomagot:  

-   Windows XP SP3  

-   Windows XP X64 SP2  

-   Windows Server 2003 SP2  

##  <a name="BKMK_InstallPackage"></a>Csomag telepítése

 A **Csomag telepítése** feladatütemezési lépéssel telepíthet szoftvereket a feladatütemezés részeként. Ezen lépés futtatásakor a telepítés azonnal megkezdődik, anélkül, hogy kivárná a házirend-lekérdezési időközt.  

 A telepített szoftvernek meg kell felelnie a következő feltételeknek:  

-   A helyi rendszerfiókban, és nem a felhasználói fiókban kell futnia.  

-   Nem működhet együtt az asztallal. A programnak csendesen vagy felügyelet nélküli módban kell futnia.  

-   Nem kezdeményezhet önállóan újraindítást. A szoftvernek a normál újraindítási kóddal, a 3010-es kilépési kóddal kell újraindítást igényelnie. Ez biztosítja, hogy a feladatütemezési lépés megfelelően fogja kezelni az újraindítást. Ha a szoftver valóban egy 3010-es kilépési kóddal tér vissza, a mögöttes feladatütemező motor végrehajtja az újraindítást. Az újraindítás után a feladatütemezés végrehajtása automatikusan folytatódik.  

 Operációs rendszerek központi telepítésekor nem támogatottak azok a programok, melyek az **Először egy másik program futtatása** beállítást használják egy függő program telepítéséhez. Ha a szoftver esetében engedélyezve van az **Először egy másik program futtatása** beállítás, és a függő program már futott korábban a célszámítógépen, a függő program futni fog, és a feladatütemezés végrehajtása folytatódik. Ha azonban a függő program még nem futott korábban a célszámítógépen, a feladatütemezési lépés sikertelen lesz.  

> [!NOTE]  
>  A központi felügyeleti hely nem rendelkezik azon ügyfélkonfigurálási házirendekkel, amelyek a feladatütemezés végrehajtása közben a szoftverterjesztési ügynök engedélyezéséhez szükségesek. Amikor a központi felügyeleti helyen feladatütemezés részére hoz létre önálló adathordozót, és a feladatütemezés tartalmazza a **Telepítőcsomag** lépést, megjelenhet a következő hiba a CreateTsMedia.log fájlban:  
>   
>  `"WMI method SMS_TaskSequencePackage.GetClientConfigPolicies failed (0x80041001)"`  
>   
>  Az olyan önálló adathordozónál, amelyik tartalmazza a Telepítőcsomag lépést, az önálló adathordozót azon az elsődleges helyen kell létrehozni, amelyiknek van engedélyezett szoftverterjesztési ügynöke, illetve fel kell venni a **Parancssor futtatása** lépést a **Windows és a ConfigMgr telepítése** lépés után és az első **Csomag telepítése** lépés előtt. A **Parancssor futtatása** lépés a WMIC parancsot futtatja, hogy engedélyezze a szoftverterjesztési ügynököt, mielőtt az első Csomag telepítése lépés futna. A feladatütemezés **Parancssor futtatása** lépésében a következő használható:  
>   
>  **Parancssori**: **WMIC/Namespace:\\\root\ccm\policy\machine\requestedconfig elérési ccm_SoftwareDistributionClientConfig most letölthető a KomponensNév létrehozása = "SWDist engedélyezése", engedélyezve = "true", LockSettings = "TRUE", PolicySource = "local", az PolicyVersion = "1.0" SiteSettingsKey = "1" / NOINTERACTIVE**  
>   
>  Különálló adathordozó létrehozásával kapcsolatos további információkért lásd: [különálló adathordozó létrehozása](../deploy-use/create-stand-alone-media.md).  

 Ez a feladatütemezési lépés csak normál operációs rendszereken futtatható. Windows PE környezetben nem futtatható.  

### <a name="details"></a>Részletek  
 A lépés **Tulajdonságok** lapján az ebben a szakaszban bemutatott beállításokat konfigurálhatja.  

 Ezenkívül a **Beállítások** lapon a következő műveleteket hajthatja végre:  

-   A lépés letiltása.  

-   Annak megadása, hogy a feladatütemezés folytatódjon-e, ha a lépés futtatása során hiba lép fel.  

-   Feltételek megadása, melyeknek teljesülnie kell a lépés futtatásához.  

 **Név**  
 Egy rövid, felhasználó által definiált név, mely leírja az ebben a lépésben végrehajtott műveletet.  

 **Leírás**  
 Részletesebb információk az ebben a lépésben végrehajtott műveletről.  

 **Egyetlen szoftvercsomag telepítése**  
 Ezzel a beállítással egy Configuration Manager szoftvercsomag. A lépés megvárja, amíg a telepítés befejeződött.  

 **Szoftvercsomagok telepítése a dinamikus változók listájának megfelelően**  
 Ez a beállítás feladatütemezési változók egy gyűjteményhez vagy egy számítógéphez meghatározott készletének alapnevét adja meg. Ezek a változók határozzák meg a gyűjteményen vagy a számítógépen telepítendő csomagokat. Minden változónév egy közös alapnévből és egy 001-től induló numerikus utótagból áll. Az egyes változók értékének egy csomagazonosítót és vesszővel elválasztva a szoftver nevét kell tartalmaznia.  

 A dinamikus változólistával telepítendő szoftverek esetén a következő beállítást engedélyezni kell a a **speciális** lapon a csomag **tulajdonságok** párbeszédpanel: **A csomag telepítése feladatütemezés központi telepítés helyett telepítésének program engedélyezése**  

> [!NOTE]  
>  Különálló adathordozós telepítések esetében nem lehet szoftvercsomagokat telepíteni dinamikus változólistával.  

 Egyetlen szoftvercsomag egy AA001 nevű feladatütemezési változóval való telepítéséhez például a következő változót kell megadni:  

|Változó neve|Változó értéke|  
|-------------------|--------------------|  
|AA001|CEN00054:Install|  

 Három szoftvercsomag telepítéséhez a következő változókat lehet megadni:  

|Változó neve|Változó értéke|  
|-------------------|--------------------|  
|AA001|CEN00054:Install|  
|AA002|CEN00107:Install Silent|  
|AA003|CEN00031:Install|  

 Az alábbi feltételek vannak hatással arra, hogy mi lesz telepítve:  

-   Ha a változó értéke nem a megfelelő formátumban van megadva, vagy nem ad meg érvényes alkalmazásazonosítót és nevet, a szoftver telepítése sikertelen lesz.  

-   Ha a csomagazonosító kisbetűket tartalmaz, az adott szoftver telepítése sikertelen lesz.  

-   Ha nem található a megadott alapnévvel és a „001” utótaggal rendelkező változó, egy csomag sem lesz telepítve, és a folyamatütemezés végrehajtása folytatódik.  

 **Ha egy szoftvercsomag telepítése nem sikerül, folytassa a listában szereplő többi csomag telepítését**  
 Ez a beállítás azt határozza meg, hogy folytatódjon a lépés végrehajtása, ha egy adott szoftvercsomag telepítése sikertelen. Ha ez a beállítás be van jelölve, a feladatütemezés végrehajtása attól függetlenül folytatódik, hogy bármely telepítés hibát ad-e vissza. Ha ez nincs bejelölve, és egy telepítés sikertelen, a feladatütemezési lépés azonnal befejeződik.  

##  <a name="BKMK_InstallSoftwareUpdates"></a>Telepítse a szoftverfrissítéseket  
 A **Szoftverfrissítések telepítése** feladatütemezési lépéssel szoftverfrissítéseket telepíthet a célszámítógépen. A rendszer ezen feladatütemezési lépés futtatásáig nem értékeli ki, hogy a célszámítógépen alkalmazhatóak-e szoftverfrissítések. Ekkor a célszámítógépen értékeli ki a szoftverfrissítések, mint bármely más Configuration Manager által felügyelt ügyfél. Konkrétan ez a lépés csak azokat a szoftverfrissítéseket telepíti, melyek olyan gyűjteményeket céloznak, amelyeknek a számítógép jelenleg tagja.  
>  [!IMPORTANT]
>Erősen ajánlott, hogy telepítse a legújabb verzióját a Windows Update Agent a sok jobb teljesítmény, a szoftverfrissítések telepítése feladatütemezési lépés használata esetén.
>* Windows 7 esetén a [3161647-es számú Tudásbázis-cikkből](https://support.microsoft.com/kb/3161647) tájékozódhat.
>* Windows 8 esetén a [3163023-as számú Tudásbázis-cikkből](https://support.microsoft.com/kb/3163023) tájékozódhat.

 Ez a feladatütemezési lépés csak normál operációs rendszereken futtatható. Windows PE környezetben nem futtatható. A feladatütemezési művelet feladatütemezési változóival kapcsolatban [A Szoftverfrissítések telepítése feladatütemezési művelet változói](task-sequence-action-variables.md#BKMK_InstallSoftwareUpdates) témakörben találhatók további információk.

 > [!NOTE]
 > Használhatja a SMSTSMPListRequestTimeoutEnabled és SMSTSMPListRequestTimeout beépített változók engedélyezze és adja meg, hány ezredmásodperc feladatütemezés várakozzon, mielőtt újból megkísérli az alkalmazás vagy a szoftver telepítését frissítése után nem sikerült beolvasnia a felügyeleti pontok listáját a helymeghatározási szolgáltatásoktól. További információkért lásd: [beépített feladatütemezési változókat](task-sequence-built-in-variables.md).

> [!NOTE]
>A Beállítások lapon konfigurálhatja ezen feladatütemezés újbóli megpróbálását, ha a számítógép váratlanul újraindul. Ez előfordulhat például az olyan szoftverfrissítések telepítésekor, amelyek automatikusan újraindítják a rendszert. A Configuration Manager 1602-es verziótól kezdve beállíthatja az SMSTSWaitForSecondReboot változó adja meg, hogy mennyi ideig (másodpercben) a feladatütemezés leálljon-e a számítógép újraindítását, ha a szoftverfrissítések telepítése. További információkért lásd: [beépített feladatütemezési változókat](task-sequence-built-in-variables.md).

### <a name="details"></a>Részletek  
 A lépés **Tulajdonságok** lapján az ebben a szakaszban bemutatott beállításokat konfigurálhatja.  

 Ezenkívül a **Beállítások** lapon a következő műveleteket hajthatja végre:  

-   A lépés letiltása.  

-   Ezzel a beállítással újra megpróbálhatja ezt a lépést, ha a számítógép váratlanul újraindul. Azt is megadhatja, hogy a rendszer hányszor próbálkozzon újra az újraindítás után.  

-   Annak megadása, hogy a feladatütemezés folytatódjon-e, ha a lépés futtatása során hiba lép fel.  

-   Feltételek megadása, melyeknek teljesülnie kell a lépés futtatásához.  

 **Név**  
 Egy rövid, felhasználó által definiált név, mely leírja az ebben a lépésben végrehajtott műveletet.  

 **Leírás**  
 Részletesebb információk az ebben a lépésben végrehajtott műveletről.  

 **A telepítéshez szükséges – csak a kötelező szoftverfrissítések**  
 Válassza ezt a beállítást, a Configuration Managerben a célszámítógépeken, amelyek megkapják a feladatütemezést kötelezőként megjelölt összes szoftverfrissítést telepíteni. A kötelező szoftverfrissítések a rendszergazda által meghatározott telepítési határidővel rendelkeznek.  

 **Elérhető telepítés – minden szoftverfrissítés**  
 Ezt a beállítást az összes elérhető szoftverfrissítést a Configuration Manager-gyűjteményhez, amelyek megkapják a feladatütemezést telepítse. Az összes elérhető szoftverfrissítés telepítve lesz a célszámítógépeken.  

 **A gyorsítótárazott vizsgálati eredmények szoftverfrissítések kiértékelése**  
A Configuration Manager 1606-os verziójától kezdve el lehet indítani a szoftverfrissítések teljes keresését, nem kell a gyorsítótárazott keresési eredményeket használni. A feladatütemezés alapértelmezés szerint a gyorsítótárazott eredményeket használja,. A jelölőnégyzet jelének törlésével arra utasíthatja az ügyfelet, hogy csatlakozzon a szoftverfrissítési ponthoz, és töltse le és dolgozza fel a legújabb szoftverfrissítési katalógust. Például akkor tanácsos ezt a lehetőséget választani, ha feladatütemezéssel [rögzíti és állítja össze egy operációs rendszer lemezképét](../deploy-use/create-a-task-sequence-to-capture-an-operating-system.md); ez esetben tudható, hogy sok szoftverfrissítésre lesz szükség, különösen soknak közülük függőségei vannak (ilyen esetben látható a felületen, hogy X-et előbb kell telepíteni, mint Y-t). Ha letiltja ezt a beállítást, és a feladatütemezés központi telepítése egy nagy mennyiségű ügyfelet, azok összes kapcsolódik a szoftverfrissítési pont egyszerre. Ez teljesítményproblémákat okozhat a katalógus feldolgozása és letöltése közben. A legtöbb esetre az alapértelmezett beállítások használatát javasoljuk.

A Configuration Manager 1606-os verziójában megjelent az új SMSTSSoftwareUpdateScanTimeout feladatütemezési változó. Ezzel szabályozható a szoftverfrissítések keresésének időkorlátja a Szoftverfrissítések telepítése feladatütemezési lépés közben. Az alapértelmezett érték 30 perc. További információkért lásd: [beépített feladatütemezési változókat](task-sequence-built-in-variables.md).


##  <a name="BKMK_JoinDomainorWorkgroup"></a>Csatlakozás tartományhoz vagy munkacsoporthoz  
 A **Csatlakozás tartományhoz vagy munkacsoporthoz** feladatütemezési lépéssel hozzáadhatja a célszámítógépet egy munkacsoporthoz vagy tartományhoz.  

 Ez a feladatütemezési lépés csak normál operációs rendszereken futtatható. Windows PE környezetben nem futtatható. A feladatütemezési művelet feladatütemezési változóival kapcsolatban [A Csatlakozás tartományhoz vagy munkacsoporthoz feladatütemezési művelet változói](task-sequence-action-variables.md#BKMK_JoinDomainWorkgroup) című témakörben találhatók további információk.  

### <a name="details"></a>Részletek  
 A lépés **Tulajdonságok** lapján az ebben a szakaszban bemutatott beállításokat konfigurálhatja.  

 Ezenkívül a **Beállítások** lapon a következő műveleteket hajthatja végre:  

-   A lépés letiltása.  

-   Annak megadása, hogy a feladatütemezés folytatódjon-e, ha a lépés futtatása során hiba lép fel.  

-   Feltételek megadása, melyeknek teljesülnie kell a lépés futtatásához.  

 **Név**  
 Egy rövid, felhasználó által definiált név, mely leírja az ebben a lépésben végrehajtott műveletet.  

 **Leírás**  
 Részletesebb információk az ebben a lépésben végrehajtott műveletről.  

 **Csatlakozás munkacsoporthoz**  
 Ezzel a beállítással csatlakoztathatja a célszámítógépet a megadott munkacsoporthoz. Ha a számítógép jelenleg egy tartomány tagja, ezen beállítás bejelölése hatására a számítógép újra fog indulni.  

 **Csatlakozás tartományhoz**  
 Ezzel a beállítással csatlakoztathatja a célszámítógépet a megadott tartományhoz.  

 Megadhat vagy tallózással megkereshet egy szervezeti egységet (OU) a megadott tartományban, melyhez a számítógépet csatlakoztatni szeretné. Ha a számítógép jelenleg egy másik tartomány vagy munkacsoport tagja, ennek hatására a számítógép újra fog indulni. Ha a számítógép már tagja egy másik szervezeti egységnek, az Active Directory Domain Services nem engedélyezi a szervezeti egység módosítását, és a rendszer ezt a beállítást figyelmen kívül hagyja.  

 **Adja meg a fiókot, amelyiknek engedélye van a tartományhoz való csatlakozáshoz**  
 A **Beállítás** gombra kattintva megadhat egy olyan fiókot és jelszót, amely jogosult a tartományhoz való csatlakozásra. A fiókot a következő formátumban kell megadni:  

 *Tartomány\fiók*  

## <a name="BKMK_PrepareConfigMgrClientforCapture"></a>ConfigMgr-ügyfél előkészítése a rögzítéshez  
Használja a **ConfigMgr-ügyfél előkészítése a rögzítéshez** lépés a Configuration Manager-ügyfél eltávolításához, vagy az ügyfél konfigurálása a referencia-számítógép előkészítése a rögzítéshez a lemezkép-készítési folyamat részeként.

A Configuration Manager verziója 1610 kezdődően a ConfigMgr-ügyfél előkészítése lépés teljesen eltávolítja a Configuration Manager-ügyfél, helyett csak a fontos információk eltávolítása. Ha a feladatütemezés a rögzített operációsrendszer-lemezképet telepíti azt telepíti egy új Configuration Manager-ügyfél minden alkalommal.  

A Configuration Manager verziója 1610, mielőtt ezt a lépést a következő feladatokat hajtja végre:  

-   Az ügyfél-konfigurációs tulajdonságokra vonatkozó szakasz eltávolítása a Windows-könyvtárban lévő smscfg.ini fájlból. E tulajdonságok közé tartozik többek között a Configuration Manager GUID és egyéb ügyfél-azonosítók ügyfél-specifikus adatait.  

-   Törli az összes SMS vagy a Configuration Manager számítógép-tanúsítvánnyal.  

-   A Configuration Manager-ügyfél gyorsítótárának törlése.  

-   A hozzárendelt helyváltozó a Configuration Manager-ügyfél.  

-   Az összes helyi Configuration Manager-házirend törlése.  

-   A megbízható legfelső szintű kulcsának eltávolítása a Configuration Manager-ügyfél.  

 Ez a feladatütemezési lépés csak normál operációs rendszereken futtatható. Windows PE környezetben nem futtatható.  

### <a name="details"></a>Részletek  
 A lépés **Tulajdonságok** lapján az ebben a szakaszban bemutatott beállításokat konfigurálhatja.  

 Ezenkívül a **Beállítások** lapon a következő műveleteket hajthatja végre:  

-   A lépés letiltása.  

-   Annak megadása, hogy a feladatütemezés folytatódjon-e, ha a lépés futtatása során hiba lép fel.  

-   Feltételek megadása, melyeknek teljesülnie kell a lépés futtatásához.  

 **Név**  
 Egy rövid, felhasználó által definiált név, mely leírja az ebben a lépésben végrehajtott műveletet.  

 **Leírás**  
 Részletesebb információk az ebben a lépésben végrehajtott műveletről.  

##  <a name="BKMK_PrepareWindowsforCapture"></a>Windows előkészítése a rögzítéshez  
 A **Windows előkészítése a rögzítéshez** feladatütemezési lépéssel megadhatja azokat a Sysprep-beállításokat, amelyeket az operációsrendszer-lemezképeknek a referencia-számítógépen történő rögzítése során kíván használni. Ez a feladatütemezési művelet futtatja a Sysprep eszközt, majd a feladatütemezéshez megadott Windows PE rendszerindító lemezképpel indítja újra a számítógépet. Ez a művelet akkor végezhető el sikeresen, ha a referencia-számítógép nincs tartományhoz csatlakoztatva.  

 Ez a feladatütemezési lépés csak normál operációs rendszereken futtatható. Windows PE környezetben nem futtatható. A feladatütemezési művelet feladatütemezési változóival kapcsolatban [A Windows előkészítése a rögzítéshez feladatütemezési művelet változói](task-sequence-action-variables.md#BKMK_PrepareWindowsCapture) témakörben találhatók további információk.  

### <a name="details"></a>Részletek  
 A lépés **Tulajdonságok** lapján az ebben a szakaszban bemutatott beállításokat konfigurálhatja.  

 Ezenkívül a **Beállítások** lapon a következő műveleteket hajthatja végre:  

-   A lépés letiltása.  

-   Annak megadása, hogy a feladatütemezés folytatódjon-e, ha a lépés futtatása során hiba lép fel.  

-   Feltételek megadása, melyeknek teljesülnie kell a lépés futtatásához.  

 **Név**  
 Egy rövid, felhasználó által definiált név, mely leírja az ebben a lépésben végrehajtott műveletet.  

 **Leírás**  
 Részletesebb információk az ebben a lépésben végrehajtott műveletről.  

 **Háttértár-illesztőprogramok listá automatikus létrehozása**  
 Ezzel a lehetőséggel azt állíthatja be, hogy a Sysprep eszköz automatikusan készítse el a referencia-számítógép háttértár-illesztőprogramjainak listáját. Ez a beállítás engedélyezi a sysprep.inf fájl Háttértár-illesztőprogramok listájának létrehozása beállítását a referencia-számítógépen. A beállítással kapcsolatban a Sysprep dokumentációjában találhatóak további információk.  

 **Ne állítsa vissza az aktiválási jelzőt**  
 Ez a beállítás megakadályozza, hogy a Sysprep eszköz alaphelyzetbe állítása a termékaktiválási jelzőt.  

##  <a name="BKMK_PreProvisionBitLocker"></a>Kiépítés előtti BitLocker  
 Windows PE környezetben a **Kiépítés előtti BitLocker** feladatütemezési lépéssel engedélyezheti a BitLockert a kívánt meghajtón. A merevlemezen csak a használatban lévő terület titkosított, így a titkosítás sokkal gyorsabb. A kulcskezelési beállításokat a [BitLocker engedélyezése](#BKMK_EnableBitLocker) feladatütemezési lépés futtatásával kell alkalmazni az operációs rendszer telepítése után. Ez a lépés csak Windows PE környezetben futtatható. Normál operációs rendszereken nem futtatható.  

> [!IMPORTANT]  
>  A BitLocker kiépítés előtti alkalmazásához legalább Windows 7 operációs rendszert kell telepíteni, a számítógépnek támogatnia kell a platformmegbízhatósági modult, és a modulnak engedélyezve kell lennie.  

### <a name="details"></a>Részletek  
 A lépés **Tulajdonságok** lapján az ebben a szakaszban bemutatott beállításokat konfigurálhatja.  

 Ezenkívül a **Beállítások** lapon a következő műveleteket hajthatja végre:  

-   A lépés letiltása.  

-   Annak megadása, hogy a feladatütemezés folytatódjon-e, ha a lépés futtatása során hiba lép fel.  

-   Feltételek megadása, melyeknek teljesülnie kell a lépés futtatásához.  

 **Név**  
 Egy rövid, felhasználó által definiált nevet ad meg, mely leírja az ebben a lépésben végrehajtott műveletet.  

 **Leírás**  
 Részletesebb információkat biztosít az ebben a lépésben végrehajtott műveletről.  

 **BitLocker alkalmazása meghatározott meghajtón**  
 Adja meg a meghajtót, amelyen engedélyezni kívánja a BitLockert. A meghajtón csak a felhasznált terület lesz titkosítva.  

 **Kihagyhatja ezt a lépést TPM Modullal nem rendelkező vagy letiltott TPM van számítógépek**  
 Ezzel a lehetőséggel kihagyhatja a meghajtótitkosítást, ha a számítógép hardvere nem támogatja a TPM modult, vagy nincs engedélyezve a TPM modul. Ezt a lehetőséget használhatja például akkor, ha egy virtuális gépre telepít egy operációs rendszert.  

##  <a name="BKMK_ReleaseStateStore"></a>Állapot tárolásának felszabadítása  
 Az **Állapot tárolásának felszabadítása** feladatütemezési lépéssel értesítheti az állapotáttelepítési pontot a rögzítési vagy visszaállítási művelet befejezéséről. Ez a lépés az **Állapot tárolásának igénylése**, a **Felhasználói állapot rögzítése** és a **Felhasználói állapot visszaállítása** feladatütemezési lépéssel együtt használható a felhasználói állapotadatoknak az állapotáttelepítési ponttal és Felhasználóáttelepítővel (USMT) való áttelepítéséhez.  

 További információ a felhasználói állapot operációs rendszerek központi telepítése közbeni kezeléséről: [felhasználói állapot kezelése](../get-started/manage-user-state.md).  

 Ha a felhasználói állapot az **Állapot tárolásának igénylése** feladatütemezési lépésben való rögzítéséhez hozzáférést igényelt egy állapotáttelepítési ponthoz, ez a lépés értesíti az állapotáttelepítési pontot arról, hogy a rögzítési folyamat befejeződött, és hogy a felhasználói állapotadatok elérhetők a visszaállításhoz. Az állapotáttelepítési pont úgy állítja be a hozzáférési engedélyeket a rögzített állapothoz, hogy csak a visszaállítást végző számítógép számára legyen elérhető (csak olvashatóként).  

 Ha a felhasználói állapot az **Állapot tárolásának igénylése** feladatütemezési lépésben való rögzítéséhez hozzáférést igényelt egy állapotáttelepítési ponthoz, ez a feladatütemezési lépés értesíti az állapotáttelepítési pontot arról, hogy a visszaállítási folyamat befejeződött. Ezen a ponton aktiválódnak az állapotáttelepítési ponthoz konfigurált megőrzési beállítások.  

> [!IMPORTANT]  
>  Célszerű megadni a **Folytatás hiba esetén** beállítást az **Állapot tárolásának igénylése** és az **Állapot tárolásának felszabadítása** lépés közötti összes feladatütemezési lépés esetében (ha vannak ilyenek), annak érdekében, hogy az **Állapot tárolásának igénylése** feladatütemezési műveletek megfelelője az **Állapot tárolásának felszabadítása** feladatütemezési műveletek között is elérhető legyen.  

 Ez a feladatütemezési lépés csak normál operációs rendszereken futtatható. Windows PE környezetben nem futtatható. A feladatütemezési művelet feladatütemezési változóival kapcsolatban [Az Állapot tárolásának felszabadítása ütemezési művelet változói](task-sequence-action-variables.md#BKMK_ReleaseStateStore) témakörben találhatók további információk.  

### <a name="details"></a>Részletek  
 A lépés **Tulajdonságok** lapján az ebben a szakaszban bemutatott beállításokat konfigurálhatja.  

 Ezenkívül a **Beállítások** lapon a következő műveleteket hajthatja végre:  

-   A lépés letiltása.  

-   Annak megadása, hogy a feladatütemezés folytatódjon-e, ha a lépés futtatása során hiba lép fel.  

-   Feltételek megadása, melyeknek teljesülnie kell a lépés futtatásához.  

 **Név**  
 Egy rövid, felhasználó által definiált név, mely leírja az ebben a lépésben végrehajtott műveletet.  

 **Leírás**  
 Részletesebb információk az ebben a lépésben végrehajtott műveletről.  

##  <a name="BKMK_RequestStateStore"></a>Állapot tárolásának igénylése  
 Az **Állapot tárolásának igénylése** feladatütemezési lépéssel igényelhet hozzáférést egy állapotáttelepítési ponthoz az állapotnak egy számítógépről való rögzítésekor, vagy az állapotnak egy számítógépre történő visszaállításakor.  

 További információ a felhasználói állapot operációs rendszerek központi telepítése közbeni kezeléséről: [felhasználói állapot kezelése](../get-started/manage-user-state.md).  

 Az **Állapot tárolásának igénylése** feladatütemezési lépést együtt használva az **Állapot tárolásának felszabadítása**, a **Felhasználói állapot rögzítése** és a **Felhasználói állapot visszaállítása** feladatütemezési lépéssel felhasználói állapotadatokat telepíthet át egy állapotáttelepítési pont és a Felhasználóáttelepítő (USMT) használatával.  

> [!NOTE]  
>  Ha most hozott létre egy új állapotáttelepítési pont (SMP) helyszerepkört, akár egy óráig is eltarthat, amíg elérhető lesz a felhasználói állapot tárolásához. Az állapotáttelepítési pont elérhetőségének elősegítésére, az állapotáttelepítési pont bármely tulajdonságának beállításával kiválthatja a helyvezérlő fájl frissítését.  

 Ez a feladatütemezési lépés normál operációs rendszeren és Windows PE környezetben is futtatható a kapcsolat nélküli Felhasználóáttelepítővel. A feladatütemezési művelet feladatütemezési változóival kapcsolatban [Az Állapot tárolásának igénylése feladatütemezési művelet változói](task-sequence-action-variables.md#BKMK_RequestState) című témakör nyújt további tájékoztatást.  

### <a name="details"></a>Részletek  
 A lépés **Tulajdonságok** lapján az ebben a szakaszban bemutatott beállításokat konfigurálhatja.  

 Ezenkívül a **Beállítások** lapon a következő műveleteket hajthatja végre:  

-   A lépés letiltása.  

-   Annak megadása, hogy a feladatütemezés folytatódjon-e, ha a lépés futtatása során hiba lép fel.  

-   Feltételek megadása, melyeknek teljesülnie kell a lépés futtatásához.  

 **Név**  
 Egy rövid, felhasználó által definiált név, mely leírja az ebben a lépésben végrehajtott műveletet.  

 **Leírás**  
 Részletesebb információk az ebben a lépésben végrehajtott műveletről.  

 **Állapot rögzítése a számítógépről**  
 Keres egy olyan állapotáttelepítési pontot, mely megfelel az állapotáttelepítési pontok beállításaiban konfigurált minimális követelményeknek (ügyfelek maximális száma és minimális szabad lemezterület), de azt nem garantálja, hogy az állapot áttelepítésének időpontjában elegendő lemezterület áll rendelkezésre. Ezzel a lehetőséggel hozzáférést igényelhet az állapotáttelepítési ponthoz abból a célból, hogy rögzítse a felhasználói állapotot és a beállításokat egy számítógépről.  

 Ha a Configuration Manager-hely több állapotáttelepítési pont is engedélyezve van, ez a feladatütemezési lépés megkeresi kérdez le, a webhely-felügyeleti pont állapotáttelepítési pontok listáját, és ezután kiértékelve talál, amely megfelel a minimális követelményeknek lemezterülettel rendelkező állapotáttelepítési pontot.  

 **Állapot visszaállítása másik számítógépről**  
 Ezzel a lehetőséggel hozzáférést igényelhet egy állapotáttelepítési ponthoz abból a célból, hogy korábban rögzített felhasználói állapotot és beállításokat állítson vissza egy célszámítógépen.  

 Ha a Configuration Manager-hely több állapotáttelepítési pont is van, ez a feladatütemezési lépés megkeresi az állapotáttelepítési ponthoz, amelyen megtalálható a célszámítógép tárolt számítógép állapotát.  

 **Az újrapróbálkozások számát**  
 A feladatütemezési lépés ennyiszer próbál meg megtalálni egy megfelelő állapotáttelepítési pontot, mielőtt hibát jelentene.  

 **Újrapróbálkozási késleltetés (másodpercben)**  
 Az az idő másodpercben megadva, ameddig a feladatütemezési lépés vár az újrapróbálkozások között.  

 **Ha a számítógépfiók nem tud csatlakozni az állapottárolóhoz, használja a hálózatelérési fiókot.**  
 Meghatározza, hogy a Configuration Manager hálózati hozzáférési fiók hitelesítő adatait fogja-e csatlakozni az állapotáttelepítési ponthoz, ha a Configuration Manager-ügyfél nem tud hozzáférni az állapotáttelepítési pont állapottárolójához számítógépfiókját. Ez a beállítás kevésbé biztonságos, mert más számítógépek is hozzáférhetnek az állapottárolóhoz a hálózatelérési fiókkal, de szükséges lehet, ha a célszámítógép nincs tartományhoz csatlakoztatva.  

##  <a name="BKMK_RestartComputer"></a>Indítsa újra a számítógépet  
 A **Számítógép újraindítása** feladatütemezési lépéssel újraindíthatja a feladatütemezést futtató számítógépet. Az újraindítás után a számítógép automatikusan folytatja a végrehajtást a feladatütemezés következő lépésével.  

 Ez a feladatütemezési lépés normál operációs rendszeren és Windows PE környezetben is futtatható. A feladatütemezési művelet feladatütemezési változóival kapcsolatos további információkért lásd: [indítsa újra a számítógépet a feladatütemezési műveletek változói](task-sequence-action-variables.md#BKMK_RestartComputer).  

### <a name="details"></a>Részletek  
 A lépés **Tulajdonságok** lapján az ebben a szakaszban bemutatott beállításokat konfigurálhatja.  

 Ezenkívül a **Beállítások** lapon a következő műveleteket hajthatja végre:  

-   A lépés letiltása.  

-   Annak megadása, hogy a feladatütemezés folytatódjon-e, ha a lépés futtatása során hiba lép fel.  

-   Feltételek megadása, melyeknek teljesülnie kell a lépés futtatásához.  

 **Név**  
 Egy rövid, felhasználó által definiált név, mely leírja az ebben a lépésben végrehajtott műveletet.  

 **Leírás**  
 Részletesebb információk az ebben a lépésben végrehajtott műveletről.  

 **A feladatütemezéshez hozzárendelt rendszerindító lemezkép**  
 Jelölje be ezt a lehetőséget a célszámítógéphez, ha a feladatütemezéshez hozzárendelt rendszerindító lemezképfájlt szeretné használni. A rendszerindító lemezképfájllal további, Windows PE környezetben futó feladatütemezési lépések lesznek futtatva.  

 **A jelenleg telepített alapértelmezett operációs rendszer**  
 Ha bejelöli ezt a lehetőséget, a célszámítógép újraindításkor a telepített operációs rendszert fogja elindítani.  

 **Értesítse a felhasználót az újraindítás előtt**  
 Ha bejelöli ezt a lehetőséget, a felhasználó számára megjelenik egy értesítés, hogy a célszámítógép újra fog indulni. A beállítás alapértelmezés szerint engedélyezett.  

 **Értesítési üzenet**  
 Adjon meg egy értesítési üzenetet, mely a célszámítógép újraindítása előtt jelenik meg a felhasználó számára.  

 **Üzenet megjelenítésének időkorlátja**  
 Adja meg a célszámítógép újraindítása előtt a felhasználónak biztosított időtartamot másodpercben. Az alapértelmezett időtartam hatvan (60) másodperc.  

##  <a name="BKMK_RestoreUserState"></a>Felhasználói állapot visszaállítása  
 A **Felhasználói állapot visszaállítása** feladatütemezési lépéssel kezdeményezheti, hogy a Felhasználóáttelepítő (USMT) visszaállítsa a felhasználói állapotot és a beállításokat a célszámítógépen. Ez a feladatütemezési lépés a **Felhasználói állapot rögzítése** feladatütemezési lépéssel együtt használható.  

 További információ a felhasználói állapot operációs rendszerek központi telepítése közbeni kezeléséről: [felhasználói állapot kezelése](../get-started/manage-user-state.md).  

 Használhatja a **felhasználói állapot visszaállítása** feladatütemezési lépést együtt a **állapot tárolásának igénylése** és **állapot tárolásának felszabadítása** feladatütemezési lépést, ha az állapotbeállításokat mentse, vagy szeretné visszaállítani a beállításokat egy állapotáttelepítési pontot a Configuration Manager-hely. Az USMT 3.0-s és újabb verzióiban ez a beállítás mindig visszafejti az USMT által létrehozott és a Configuration Manager által kezelt titkosítási kulcs használatával.  

 A **Felhasználói állapot visszaállítása** feladatütemezési lépés az USMT eszköz leggyakrabban használt beállításait csak részlegesen teszi elérhetővé. Az OSDMigrateAdditionalCaptureOptions feladatütemezési változóval további parancssori kapcsolókat is megadhat.  

> [!IMPORTANT]  
>  Ha nem operációsrendszer-telepítési célra használja a **Felhasználói állapot visszaállítása** feladatütemezési lépést, közvetlenül a [Felhasználói állapot visszaállítása](#BKMK_RestartComputer) feladatütemezési lépés után adja meg a **Számítógép újraindítása** feladatütemezési lépést.  

 Ez a feladatütemezési lépés csak normál operációs rendszereken futtatható. Windows PE környezetben nem futtatható. A feladatütemezési művelet feladatütemezési változóival kapcsolatban [A Felhasználói állapot visszaállítása feladatütemezési művelet változói](task-sequence-action-variables.md#BKMK_RestoreUserState) című témakör nyújt további tájékoztatást.  

### <a name="details"></a>Részletek  
 A lépés **Tulajdonságok** lapján az ebben a szakaszban bemutatott beállításokat konfigurálhatja.  

 Ezenkívül a **Beállítások** lapon a következő műveleteket hajthatja végre:  

-   A lépés letiltása.  

-   Annak megadása, hogy a feladatütemezés folytatódjon-e, ha a lépés futtatása során hiba lép fel.  

-   Feltételek megadása, melyeknek teljesülnie kell a lépés futtatásához.  

 **Név**  
 Egy rövid, felhasználó által definiált nevet ad meg, mely leírja az ebben a lépésben végrehajtott műveletet.  

 **Leírás**  
 Részletesebb információkat biztosít az ebben a lépésben végrehajtott műveletről.  

 **Felhasználói állapot áttelepítését szolgáló eszközcsoma**  
 Adja meg a Configuration Manager-csomagot, amely a felhasználói állapotot és a beállítások visszaállításához használni ehhez a lépéshez USMT verzióját tartalmazza. Ez a csomag nem igényel programot. A feladatütemezési lépés futtatásakor a feladatütemezés az USMT eszköz a csomagban lévő verziói közül a megadottat fogja használni. Annak az operációs rendszernek az architektúrája alapján, melynek az állapotát visszaállítja, olyan csomagot adjon meg, mely az USMT eszköz 32 bites vagy x64 verzióját tartalmazza.  

 **Összes rögzített felhasználói profil visszaállítása a szokásos beállításokkal**  
 A rögzített felhasználói profilokat a szokásos beállításokkal állítja vissza. A **Felhasználói profil rögzítésének testreszabása** lehetőséggel testre szabhatja, hogy mely beállítások legyenek visszaállítva.  

 **Felhasználói profilok visszaállításának testreszabása**  
 Lehetővé teszi annak testre szabását, hogy mely fájlokat szeretné visszaállítani a célszámítógépen. A **Fájlok** lehetőségre kattintva megadhatja, hogy az USMT-csomag mely konfigurációs fájljait szeretné használni a felhasználói profilok visszaállításához. Konfigurációs fájl hozzáadásához adja meg a fájl nevét a **Fájlnév** mezőben, majd kattintson a **Hozzáadás** gombra. A Fájlok panelen jelennek meg a konfigurációs fájlok, melyeket a művelet használni fog. A megadott .xml fájl határozza meg, hogy a rendszer mely felhasználói fájlokat fogja visszaállítani.  

 **Helyi számítógép-felhasználói profilok visszaállítása**  
 A helyi számítógép-felhasználói (azaz a nem tartományi felhasználói) profilokat állítja vissza. A visszaállított helyi felhasználói fiókokhoz új jelszót kell majd megadnia, mert a helyi felhasználói fiókok eredeti jelszavait nem lehet áttelepíteni. A **Jelszó** mezőben adja meg az új jelszót, majd erősítse meg a jelszót a **Jelszó megerősítése** mezőben.  

 **Továbbra is, ha egyes fájlok nem állíthatók vissza.**  
 A felhasználói állapot visszaállításának folytatása akkor is, ha néhány fájlt nem lehet visszaállítani. A beállítás alapértelmezés szerint engedélyezett. Ha letiltja ezt a lehetőséget, és a fájlok visszaállítása során hibák lépnek fel, a feladatütemezési lépés azonnal véget ér egy hibával, és nem lesz minden fájl visszaállítva.  

 **Részletes naplózás engedélyezése**  
 Ha bejelöli ezt a beállítást, részletesebb naplófájl-információk jönnek létre. Állapotok visszaállításakor a Loadstate.log napló jön létre és tárolódik a feladatütemezés naplómappájában, melynek az alapértelmezett mappája a \windows\system32\ccm\logs.  

##  <a name="BKMK_RunCommandLine"></a>Parancssor futtatása  
 A **Parancssor futtatása** feladatütemezési lépéssel egy megadott parancssort futtathat.  

 Ez a lépés normál operációs rendszeren és Windows PE környezetben is futtatható. A feladatütemezési művelet feladatütemezési változóival kapcsolatban [A Parancssor futtatása feladatütemezési művelet változói](task-sequence-action-variables.md#BKMK_RunCommand) című témakörben találhatók további információk.  

### <a name="details"></a>Részletek  
 A lépés **Tulajdonságok** lapján az ebben a szakaszban bemutatott beállításokat konfigurálhatja.  

 Ezenkívül a **Beállítások** lapon a következő műveleteket hajthatja végre:  

-   A lépés letiltása.  

-   Annak megadása, hogy a feladatütemezés folytatódjon-e, ha a lépés futtatása során hiba lép fel.  

-   Feltételek megadása, melyeknek teljesülnie kell a lépés futtatásához.  

 **Név**  
 Egy rövid, felhasználó által definiált nevet ad meg, mely leírja a futtatott parancssort.  

 **Leírás**  
 Részletesebb információkat biztosít az ebben a lépésben futtatott parancssorról.  

 **Parancssor**  
 A futtatott parancssort adja meg. A mező kitöltése kötelező. Többek között a következőket fájlnév-kiterjesztések az ajánlott eljárás, például a .vbs és az .exe. Adjon meg minden szükséges beállításfájlt, parancssori paramétert vagy kapcsolót.  

 Ha a fájl neve nincs megadva fájlnévkiterjesztés, a Configuration Manager próbálkozás .com, .exe, és. bat. Ha a fájlnév kiterjesztése, amely nem egy végrehajtható fájl, a Configuration Manager társítást próbál alkalmazni egy helyi. Például ha a parancssor az Olvassel.gif, a Configuration Manager elindítja a célszámítógépen a .gif fájlok megnyitásához megadott alkalmazást.  

 Példák:  

 **Setup.exe /a**  

 **cmd.exe /c copy Jan98.dat c:\sales\Jan98.dat**  

> [!NOTE]  
>  Parancssori műveletek, például kimenet átirányítása, az átirányítás vagy másolása, az előző példában szemléltetett meg kell előznie a **cmd.exe /c** parancs sikeres futtatásához.  

 **64 bites fájlrendszer-átirányítás letiltása**  
 64 bites operációs rendszerek használatakor a parancssorban alapértelmezés szerint a WOW64 fájlrendszer-átirányító keresi meg és futtatja a futtatható fájlt úgy, hogy megkeresi az operációs rendszer futtatható fájljainak és DLL-jeinek 32 bites verzióit.  E beállítás megadásával letilthatja a WOW64 fájlrendszer-átirányító használatát, annak érdekében, hogy a rendszer megkeresse az operációs rendszer futtatható fájljainak és DLL-jeinek natív 64 bites verzióit.  Ennek a beállításnak 32 bites operációs rendszerek használatakor nincs hatása.  

 **Indítsa el**  
 A program végrehajtható mappáját határozza meg, legfeljebb 127 karakter hosszú lehet. A mappa megadható a célszámítógépen értelmezett abszolút elérési útként és a csomagot tartalmazó terjesztésipont-mappában értelmezett relatív elérési útként is. A mező kitöltése nem kötelező.  

 Példák:  

 **c:\OfficeXP**  

 **i386**  

> [!NOTE]  
>  A **Tallózás** gombbal a helyi számítógépen kereshet fájlokat és mappákat, ezért minden kiválasztott elemnek léteznie kell a célszámítógépen is, azonos helyen és ugyanazokkal a fájl- és mappanevekkel.  

 **Csomag**  
 Ha fájlokat vagy programokat ad meg, amelyek még nem található a cél számítógépen a parancssorból, válassza ezt a beállítást adja meg a Configuration Manager-csomagot, amely tartalmazza a megfelelő fájlokat. A csomag nem igényel programot. Ez a beállítás nem szükséges, ha a megadott fájl létezik a célszámítógépen.  

 **Időtúllépés**  
 Megadja, hogy mennyi ideig Configuration Manager jelző érték engedélyezi a parancssor futtatását. Ez az érték 1 perc és 999 perc lehet. Az alapértelmezett érték 15 perc.  

 A beállítás alapértelmezés szerint le van tiltva.  

> [!IMPORTANT]  
>  Ha olyan értéket ad meg, amely nem biztosít elég időt a Parancssor futtatása feladatütemezési lépés sikeres befejezéséhez, a feladatütemezési lépés sikertelen lesz, és egyéb vezérlési beállításoktól függően akár a teljes feladatütemezés is sikertelen lehet. Ha az időkorlát lejár, a Configuration Manager leállítja a parancssori folyamatot.  

 **Ezt a lépést a következő fiókként futtassa**  
 Azt adja meg, hogy a parancssor egy, a helyi rendszerfióktól eltérő Windows felhasználói fiók használatával legyen futtatva.  

> [!NOTE]  
>  Amikor másik fiókot ad meg ehhez a lépéshez, és erre egy operációsrendszer-telepítési lépés után kerül sor, a fiókot hozzá kell adnia a számítógéphez, ha egyszerű parancsfájlokat szeretne futtatni, összetettebb programok, például egy MSI-csomag futtatása esetén pedig vissza kell állítani a Windows felhasználói fiók profilját.  

 **Fiók**  
 A művelet által futtatandó, a feladatütemezésben szereplő parancssori feladatot futtató Windows felhasználói fiókot határozza meg. A parancssor a megadott fiók jogosultságaival lesz futtatva. A **Beállítás** gombra kattintva adhatja meg a helyi felhasználói vagy tartományi fiókot.  

> [!IMPORTANT]  
>  Ha Windows PE környezetben futtat egy felhasználói fiókot megadó **Parancssor futtatása** feladatütemezési műveletet, a művelet sikertelen lesz, mert a Windows PE nem csatlakoztatható tartományhoz. A hiba az smsts.log fájlban lesz rögzítve.  

##  <a name="BKMK_RunPowerShellScript"></a>PowerShell parancsfájl futtatása  
 A **PowerShell-parancsfájl futtatása** feladatütemezési lépéssel egy megadott PowerShell-parancsfájlt futtathat.  

 Ez a lépés normál operációs rendszeren és Windows PE környezetben is futtatható. A lépés csak akkor futtatható a Windows PE környezetben, ha a PowerShell engedélyezve van a rendszerindító lemezképben. A Windows PowerShellt (WinPE-PowerShell) a rendszerindító lemezkép tulajdonságainak **Választható összetevők** lapján engedélyezheti. A rendszerindító lemezképek módosításával kapcsolatos további információkért lásd: [rendszerindító lemezképek kezelése](../get-started/manage-boot-images.md).  

> [!NOTE]  
>  A Windows Embedded operációs rendszereken alapértelmezés szerint nincs engedélyezve a PowerShell.  

### <a name="details"></a>Részletek  
 A lépés **Tulajdonságok** lapján az ebben a szakaszban bemutatott beállításokat konfigurálhatja.  

 Ezenkívül a **Beállítások** lapon a következő műveleteket hajthatja végre:  

-   A lépés letiltása.  

-   Annak megadása, hogy a feladatütemezés folytatódjon-e, ha a lépés futtatása során hiba lép fel.  

-   Feltételek megadása, melyeknek teljesülnie kell a lépés futtatásához.  

 **Név**  
 Egy rövid, felhasználó által definiált nevet ad meg, mely leírja a futtatott parancssort.  

 **Leírás**  
 Részletesebb információkat biztosít az ebben a lépésben futtatott parancssorról.  

 **Csomag**  
 Adja meg a PowerShell-parancsfájlt tartalmazó Configuration Manager-csomagot. Egy csomag több PowerShell-parancsfájlt is tartalmazhat.  

 **Parancsfájl neve**  
 A futtatandó PowerShell-parancsfájl nevét adja meg. A mező kitöltése kötelező.  

 **Paraméterek**  
 A Windows PowerShell-parancsfájlnak átadandó paramétereket adja meg. Ugyanúgy konfigurálhatja a paramétereket, mintha egy parancssorban adná hozzá azokat a Windows PowerShell-parancsfájlhoz.  

> [!IMPORTANT]  
>  A parancsfájl által felhasznált paramétereket adja meg, ne a Windows PowerShell-parancssoréit.  
>   
>  Az alábbi példa érvényes paramétereket tartalmaz:  
>   
>  **-Paraméter1 érték1-Paraméter2 érték2**  
>   
>  Az alábbi példa érvénytelen paramétereket tartalmaz. A félkövér elemek Windows PowerShell parancssori paraméterek (-nologo és - executionpolicy unrestricted), és nem a parancsfájl által felhasznált.  
>   
>  **-nologo-executionpolicy unrestricted-fájl parancsfájl.ps1-paraméter1 érték1-Paraméter2 érték2**  

 **PowerShell végrehajtási házirend**  
 A PowerShell végrehajtási házirend kiválasztásával meghatározhatja, hogy mely Windows PowerShell-parancsfájlok (ha vannak) futtatása lesz engedélyezett a számítógépen. Válasszon egyet az alábbi végrehajtási házirendek közül:  

-   **AllSigned**: Csak a megbízható közzétevők által aláírt parancsfájlokat lehet futtatni.  

-   **Nem definiált**: Nincs végrehajtási házirend lett meghatározva. .  

-   **Áthidaló**: Minden konfigurációs fájlt betölt, és minden parancsfájlt futtat. Ha egy, az internetről letöltött aláíratlan parancsfájlt futtat, a rendszer nem kér engedélyt annak futtatása előtt.  

> [!IMPORTANT]  
>  A PowerShell 1.0 nem támogatja az Undefined és a Bypass végrehajtási házirendeket.  

##  <a name="BKMK_SetDynamicVariables"></a>Dinamikus változók megadása  
 A **Dinamikus változók beállítása** feladatütemezési lépéssel a következőket hajthatja végre:  

1.  Adatgyűjtés a számítógépről és annak környezetéről, majd a megadott feladatütemezési változók megadása az adatokkal.  

2.  A definiált szabályok kiértékelése és a feladatütemezési változók beállítása az igaz értéket visszaadó szabályokhoz beállított változók és értékek alapján.  

 A feladatütemezés automatikusan beállítja a következő csak olvasható feladatütemezési változókat:  

 -   &#95; SMSTSMake  

 -   &#95; SMSTSModel  

 -   &#95; SMSTSMacAddresses  

 -   &#95; SMSTSIPAddresses  

 -   &#95; SMSTSSerialNumber  

 -   &#95; SMSTSAssetTag  

 -   &#95; SMSTSUUID  

 Ez a feladatütemezési lépés normál operációs rendszeren és Windows PE környezetben is futtatható. További információ a feladatütemezési változók: [feladat feladatütemezési művelet változói](task-sequence-action-variables.md).  

### <a name="details"></a>Részletek  
 A lépés **Tulajdonságok** lapján az ebben a szakaszban bemutatott beállításokat konfigurálhatja.  

 Ezenkívül a **Beállítások** lapon a következő műveleteket hajthatja végre:  

-   A lépés letiltása.  

-   Annak megadása, hogy a feladatütemezés folytatódjon-e, ha a lépés futtatása során hiba lép fel.  

-   Feltételek megadása, melyeknek teljesülnie kell a lépés futtatásához.  

**Név**  
 A folyamatütemezési lépés rövid, felhasználó által definiált neve.  

**Leírás**  
 Részletesebb információk az ebben a lépésben végrehajtott műveletről.  

**Dinamikus szabályok és változók**  
 Egy, a feladatütemezésben használandó dinamikus változó beállításához hozzáadhat egy szabályt, majd megadhatja a szabályhoz megadott egyes változók értékét, vagy hozzáadhat egy vagy több, szabály hozzáadása nélkül beállítandó változót. Szabály hozzáadásakor a következő szabálykategóriák közül választhat:  

 -   **Számítógép**: Használja az ezzel a szabálykategóriával eszközcímke, UUID, sorozatszám vagy mac-cím értékeit értékelheti ki. Több értéket is megadhat, és ha bármely érték igaz, akkor a szabály is igaz értéked ad vissza. Például a következő szabály igaz értéket ad vissza, ha a sorozatszám 5892087, attól függetlenül, hogy a MAC-cím értéke 26-78-13-5A-A4-22 vagy sem.  

     `IF Serial Number = 5892087 OR MAC address = 26-78-13-5A-A4-22 THEN`  

-   **Hely**: Ezzel a szabálykategóriával segítségével az alapértelmezett átjáró értékeit értékelheti ki.  

-   **Gyártmány és modell**: Ezzel a szabálykategóriával segítségével gyártmányának és a számítógép modelljének értékeit értékelheti ki. A gyártmánynak és a modellnek is igaz értéket kell visszaadnia ahhoz, hogy a szabály igaz értéket adjon vissza.   

    A Configuration Manager verziója 1610 kezdődően megadhat egy csillag (*) és a kérdőjel (**?**) helyettesítő karakterek, mint ahol x több karaktert megegyezik és **?** egyetlen karakternek felel meg. Például a karakterlánc "DELL * 900?" DELL-ABC-9001 és DELL9009 fog egyezni.

-   **Feladatütemezési változó**: Ezen ezzel a szabálykategóriával egy feladatütemezési változót, az állapot és kiértékelendő értéket adhat. A szabály akkor ad vissza igaz értéket, ha a változó beállított értéke megfelel a megadott feltételnek.  

Megadhat egy vagy több olyan változót, melyek egy igaz értéket visszaadó szabályhoz lesznek beállítva, vagy beállíthat változókat szabály használata nélkül is. Választhat a meglévő változók közül is, vagy létrehozhat egy egyéni változót.  

 -   **Meglévő feladatütemezési változók**: Ez a beállítás segítségével válassza ki egy vagy több változót a meglévő feladatütemezési változók listájából. A tömbváltozók nem választhatóak.  

 -   **Egyéni feladatütemezési változók**: Ez a beállítás segítségével meg egy egyéni feladatütemezési változót. Megadhat egy meglévő feladatütemezési változót is. Ez meglévő tömbváltozók, mint például az OSDAdapter megadásához lehet hasznos, mivel a tömbváltozók nem szerepelnek a meglévő feladatütemezési változók listájában.  

Miután egy szabályhoz kiválasztotta a változókat, minden egyes változóhoz meg kell adnia egy értéket. A változó akkor lesz beállítva a megadott értékre, ha a szabály igaz értéket ad vissza. Elrejtheti az egyes változók értékét, ha az adott változónál engedélyezi a **Titkos érték** beállítást. Egyes meglévő változók, például az OSDCaptureAccountPassword feladatütemezési változó értéke alapértelmezés szerint el van rejtve.  

> [!IMPORTANT]  
>  Ha a Dinamikus változók beállítása lépéssel importál egy feladatütemezést, és a **Titkos érték** lehetőség be van jelölve a változó értékénél, a rendszer eltávolítja az értéket a feladatütemezés importálásakor. Ennek következtében a feladatütemezés importálása után újra meg kell adnia a dinamikus változó értékét.  

##  <a name="BKMK_SetTaskSequenceVariable"></a>Feladatütemezési változó beállítása  
 A **Feladatütemezési változó beállítása** feladatütemezési lépéssel egy feladatütemezésben használt változó értékét állíthatja be.  

 Ez a feladatütemezési lépés normál operációs rendszeren és Windows PE környezetben is futtatható. A feladatütemezési műveletek olvassák a feladatütemezési változókat, és így azok meghatározzák a műveletek viselkedését. További információ a konkrét feladatütemezési változókról: [feladat feladatütemezési művelet változói](task-sequence-action-variables.md).  

### <a name="details"></a>Részletek  
 A lépés **Tulajdonságok** lapján az ebben a szakaszban bemutatott beállításokat konfigurálhatja.  

 Ezenkívül a **Beállítások** lapon a következő műveleteket hajthatja végre:  

-   A lépés letiltása.  

-   Annak megadása, hogy a feladatütemezés folytatódjon-e, ha a lépés futtatása során hiba lép fel.  

-   Feltételek megadása, melyeknek teljesülnie kell a lépés futtatásához.  

 **Név**  
 A folyamatütemezési lépés rövid, felhasználó által definiált neve.  

 **Leírás**  
 Részletesebb információk az ebben a lépésben végrehajtott műveletről.  

 **A feladatütemezési változó**  
 A feladatütemezési változó felhasználó által definiált neve.  

 **Érték**  
 A feladatütemezési változóhoz rendelt érték. Az érték egy másik %<változónév\>% szintaxisú feladatütemezési változó lehet.  

##  <a name="BKMK_SetupWindowsandConfigMgr"></a>Windows és ConfigMgr beállítása  
 A **Windows és ConfigMgr beállítása** feladatütemezési lépéssel hajtható végre az áttérés a Windows PE környezetről az új operációs rendszerre. Ez a feladatütemezési lépés bármely operációs rendszer központi telepítésének kötelező része. A Configuration Manager-ügyfél telepíti az új operációs rendszerbe, és előkészíti a feladatütemezés végrehajtásának folytatását az új operációs rendszerben.  

 Ez a lépés csak Windows PE környezetben futtatható. Normál operációs rendszereken nem futtatható. A feladatütemezési művelet feladatütemezési változóival kapcsolatos további információkért lásd: [Windows és ConfigMgr beállítása feladatütemezési művelet változói feladat](task-sequence-action-variables.md#BKMK_SetupWindows).  

 A **Windows és ConfigMgr beállítása** feladatütemezési művelet a sysprep.inf vagy unattend.xml directory változók, például % WINDIR % és % ProgramFiles % változót lecseréli a Windows előtelepítési környezet X:\Windows telepítési könyvtára. A rendszer figyelmen kívül hagyja az ezen környezeti változókkal megadott feladatütemezési változókat.  

 Ezzel a feladatütemezési lépéssel a következő műveleteket végezheti el:  

1.  Előfeltételek: Windows PE  

    1.  Elvégzi a feladatütemezési változók behelyettesítését az unattend.xml fájlban.  

    2.  Letölti a csomagot, amely tartalmazza a Configuration Manager-ügyfél, és hozzáadja a telepített lemezképhez.  

2.  A Windows beállítása  

    1.  Lemezképalapú telepítés.  

        1.  Letiltja a Configuration Manager ügyfelet a lemezképben (Ez azt jelenti, hogy letiltja az automatikus indítását a Configuration Manager-ügyfél szolgáltatás).  

        2.  A telepített lemezkép beállításjegyzékének frissítésével biztosítja, hogy a telepített operációs rendszer ugyanazzal a meghajtóbetűjellel induljon el, mint a referencia-számítógépen.  

        3.  A telepített operációs rendszerben indul újra.  

        4.  A korábban megadott, minden végfelhasználói beavatkozást letiltó sysprep.inf vagy unattend.xml fájl használatával lefut a Windows Minitelepítő. Megjegyezés: Ha **hálózati beállítások alkalmazása** megadott tartományhoz való csatlakozáshoz, akkor ezt az információt a sysprep.inf vagy unattend.xml fájlt, és a Windows minitelepítő végrehajtja a tartományhoz való csatlakozást.  

    2.  Setup.exe-alapú telepítés.  Futtatja a Setup.exe fájlt, amely a szokásos Windows-telepítési folyamatot követi:  

        1.  Az operációs rendszer telepítőcsomagját egy korábbi **Operációs rendszer alkalmazása** feladatütemezésben megadott merevlemez-meghajtóra másolja.  

        2.  Az újonnan telepített operációs rendszerben indul újra.  

        3.  A korábban megadott, minden végfelhasználói beavatkozást letiltó sysprep.inf vagy unattend.xml fájl használatával lefut a Windows Minitelepítő. Megjegyezés: Ha **hálózati beállítások alkalmazása** megadott tartományhoz való csatlakozáshoz, akkor ezt az információt a sysprep.inf vagy unattend.xml fájlt, és a Windows minitelepítő végrehajtja a tartományhoz való csatlakozást.  

3.  A Configuration Manager-ügyfél beállítása  

    1.  A Windows Minitelepítő befejeződése után a feladatütemezés a setupcomplete.cmd fájl használatával folytatódik.  

    2.  A **Windows-beállítások alkalmazása** lépésben kiválasztott lehetőségnek megfelelően engedélyezi vagy letiltja a helyi rendszergazdai fiókot.  

    3.  Telepíti a Configuration Manager-ügyfél által a korábban letöltött csomaggal (1.b) és a feladatütemezés-szerkesztőben megadott telepítési tulajdonságokkal. Az ügyfelet azért kell „kiépítési üzemmódban” telepíteni, hogy a feladatütemezés befejeztéig ne dolgozza fel az új házirendkérelmeket.  

    4.  Megvárja, amíg az ügyfél teljesen működőképes lesz.  

    5.  Ha a számítógép olyan környezetben működik, melyben engedélyezve van a hálózatvédelem, az ügyfél ellenőrzi, hogy elérhetőek-e szükséges frissítések, és telepíti azokat, hogy az összes szükséges frissítés rendelkezésre álljon, mielőtt folytatódik a feladatütemezés futtatása.  

4.  A feladatütemezés futtatása a következő lépésével folytatódik.  

> [!NOTE]  
>  A **Windows és ConfigMgr beállítása** feladatütemezési művelet feladata a Csoportházirend futtatása az újonnan telepített számítógépen. A Csoportházirendet a feladatütemezés befejezése után alkalmazza a rendszer.  

### <a name="details"></a>Részletek  
 A lépés **Tulajdonságok** lapján az ebben a szakaszban bemutatott beállításokat konfigurálhatja.  

 Ezenkívül a **Beállítások** lapon a következő műveleteket hajthatja végre:  

-   A lépés letiltása.  

-   Ne válassza a feladatütemezés folytatását, ha a lépés futtatása során hiba lép fel. Ha hiba lépne fel, a feladatütemezés meghiúsul, függetlenül a beállítás kiválasztásától.  

-   Feltételek megadása, melyeknek teljesülnie kell a lépés futtatásához.  

 **Név**  
 Egy rövid, felhasználó által definiált nevet ad meg, mely leírja az ebben a lépésben végrehajtott műveletet.  

 **Leírás**  
 Kiegészítő információkat biztosít az ebben a lépésben végrehajtott műveletről.  

 **Ügyfélcsomag**  
 Adja meg a Configuration Manager ügyfél-telepítési csomag Ez a feladatütemezési lépés által használt. Kattintson a **Tallózás** válassza ki a Configuration Manager-ügyfél telepítéséhez használni kívánt Ügyféltelepítő csomagot.  

 **Éles üzem előtti ügyfélcsomag használata Ha elérhető**  
 Azt adja meg, hogy ha elérhető egy üzem előtti ügyfélcsomag, a feladatütemezési lépés ezt a csomagot használja az üzemi ügyfélcsomag helyett. Az üzem előtti ügyfélcsomag általában egy, az éles környezetben tesztelt újabb verzió. Kattintson a **Tallózás** és a Configuration Manager-ügyfél telepítéséhez használni kívánt üzem előtti ügyfél-telepítési csomag kiválasztása.  

 **Telepítés tulajdonságai**  
 A feladatütemezési művelet automatikusan meghatározza a helyhozzárendelést és az alapértelmezett konfigurációt. Ebben a mezőben további, az ügyfél telepítésekor használandó telepítési tulajdonságokat adhat meg, ha vannak. Ha több telepítési tulajdonságot kíván megadni, szóközzel válassza el őket.  

 Az ügyfél telepítése során használni kívánt parancssori paramétereket is megadhat. A **/skipprereq: silverlight.exe** paraméter megadásával például jelezheti a CCMSetup.exe programnak, hogy ne telepítse a Microsoft Silverlightot. A CCMSetup.exe használható parancssori paraméterekkel kapcsolatos további információkért lásd: [vonatkozó ügyfél-telepítési tulajdonságok](../../core/clients/deploy/about-client-installation-properties.md).  

##  <a name="BKMK_UpgradeOS"></a>Operációs rendszer verziófrissítéséhez  
 Az **Operációs rendszer verziófrissítésének elvégzése** feladatütemezési lépéssel végezheti el egy meglévő Windows 7, Windows 8, Windows 8.1 vagy Windows 10 operációs rendszer Windows 10-re való frissítését.  

 Ez a feladatütemezési lépés csak normál operációs rendszereken futtatható. Windows PE környezetben nem futtatható.  

### <a name="details"></a>Részletek  
 A lépés **Tulajdonságok** lapján az ebben a szakaszban bemutatott beállításokat konfigurálhatja.  

 Ezenkívül a **Beállítások** lapon a következő műveleteket hajthatja végre:  

-   A lépés letiltása.  

-   Annak megadása, hogy a feladatütemezés folytatódjon-e, ha a lépés futtatása során hiba lép fel.  

-   Feltételek megadása, melyeknek teljesülnie kell a lépés futtatásához.  

 **Név**  
 Egy rövid, felhasználó által definiált név, mely leírja az ebben a lépésben végrehajtott műveletet.  

 **Leírás**  
 Részletesebb információk az ebben a lépésben végrehajtott műveletről.  

 **Frissítési csomag**  
 Ezzel a beállítással adhatja meg a Windows 10 operációs rendszer verziófrissítő csomagját, melyet használni szeretne a frissítéshez.  

 **Forrás elérési útja**  
 A használni kívánt Windows 10-es adathordozó helyi vagy hálózati elérési útját adja meg (az /installFrom parancssori kapcsolónak felel meg). Megadhat egy változót is (például %tartalom_elérési_útja% vagy %DPC01%). Ha egy változót használ a forrás elérési útjához, ezt korábban meg kell adni a feladatütemezésben. Ha például használja a [Csomag tartalmának letöltése](#BKMK_DownloadPackageContent) lépést a feladatütemezésben, megadhat egy változót az operációs rendszer verziófrissítő csomagjának helyéhez. Ezután használhatja ezt a változót a forrás elérési útjaként ebben a lépésben.  

 **Edition**  
 A verzióváltáshoz használni kívánt, az operációs rendszer adathordozóján belüli kiadást határozza meg.  

 **Termékkulcs**  
 A verzióváltási folyamathoz alkalmazni kívánt termékkulcsot adja meg  

 **Adja meg a következő illesztőprogram-tartalmak frissítés során a Windows telepítő**  
 Ezzel a beállítással adhat hozzá illesztőprogramokat a célszámítógéphez a verzióváltási folyamat során (az /InstallDriver parancssori kapcsolónak felel meg). Az illesztőprogramoknak kompatibiliseknek kell lenniük a Windows 10-zel. Adja meg a következők valamelyikét:  

-   **Illesztőprogram-csomag**: Kattintson a **Tallózás** és válasszon ki egy meglévő illesztőprogram-csomagot a listából.  

-   **Előkészített tartalom**:  Ezt a beállítást adja meg az illesztőprogram-csomag helyét. Megadhat egy helyi mappát, egy hálózati elérési utat vagy egy feladatütemezési változót. Ha egy változót használ a forrás elérési útjához, ezt korábban meg kell adni a feladatütemezésben. Például a [Csomag tartalmának letöltése](task-sequence-steps.md#BKMK_DownloadPackageContent) lépéssel.  

 **Időkorlát (perc)**  
 A telepítő rendelkezik-e a Configuration Manager sikertelen lesz, a feladatütemezési lépés végrehajtása percek számát adja meg.  

 **A Windows telepítő kompatibilitási vizsgálatának végrehajtása a frissítés megkezdése nélkül**  
 Azt adja meg, hogy a rendszer a frissítés megkezdése nélkül hajtsa végre a Windows telepítő kompatibilitási vizsgálatát (a /Compat ScanOnly parancssori kapcsolónak felel meg). Ha ezt a beállítást használja, később a teljes telepítési forrást telepítenie kell. A telepítő a vizsgálat eredményeképpen egy kilépési kódot ad vissza. A következő táblázat néhány gyakori kilépési kódot tartalmaz.  

|Kilépési kód|Részletek|  
|-|-|  
|MOSETUP_E_COMPAT_SCANONLY (0xC1900210)|Nincs kompatibilitási probléma („sikeres”).|  
|MOSETUP_E_COMPAT_INSTALLREQ_BLOCK (0xC1900208)|Kezelhető kompatibilitási problémák.|  
|MOSETUP_E_COMPAT_MIGCHOICE_BLOCK (0xC1900204)|A kiválasztott áttelepítési beállítás nem érhető el. Például az Enterprise kiadásról a Professional kiadásra való frissítés.|  
|MOSETUP_E_COMPAT_SYSREQ_BLOCK (0xC1900200)|Nem jogosult a Windows 10-re.|  
|MOSETUP_E_COMPAT_INSTALLDISKSPACE_BLOCK (0xC190020E)|Nincs elég szabad lemezterület.|  

 További információk a paraméterrel kapcsolatban: [Windows Setup Command-Line Options](https://msdn.microsoft.com/library/windows/hardware/dn938368\(v=vs.85\).aspx) (A Windows-telepítő parancssori kapcsolói).  

 **A mellőzhető kompatibilitási üzenetek figyelmen kívül**  
 Azt határozza meg, hogy a telepítő az esetleges mellőzhető kompatibilitási üzenetek figyelmen kívül hagyásával végezze el a telepítést (a /Compat IgnoreWarning parancssori kapcsolónak felel meg).  

 **Windows telepítő dinamikus frissítése a Windows Update-tel**  
 Azt adja meg, hogy a telepítő végezzen-e dinamikus frissítési műveleteket, például frissítések keresését, letöltését és telepítését (a /DynamicUpdate parancssori kapcsolónak felel meg). Ez a beállítás nem kompatibilis a Configuration Manager szoftverfrissítések, de azt is engedélyezhető, ha a WSUS (önálló) vagy a Windows Update használatával kezeli a frissítéseket.  

 **Házirend felülbírálása és az alapértelmezett Microsoft Update használata**: Válassza ezt a beállítást, a helyi házirendet a dinamikus frissítés műveletek futtatásához, és a frissítések a Windows Update szolgáltatásból szerezze be a számítógép valós időben ideiglenesen felülbírálhatja.  

