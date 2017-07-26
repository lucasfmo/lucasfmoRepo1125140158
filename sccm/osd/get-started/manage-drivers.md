---
title: "Kezelheti az illesztőprogramokat - Configuration Manager |} Microsoft Docs"
description: "A Configuration Manager illesztőprogram-katalógus használatáról az importálandó illesztőprogramokat, a csoport illesztőprogram-csomagban, és csomagok olyan terjesztési pontokra terjesztéséhez."
ms.custom: na
ms.date: 01/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 84802d55-112e-4f7f-9a48-74a80d91a0f4
caps.latest.revision: 10
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 89158debdf4c345a325feeb608db2215a88ed81b
ms.openlocfilehash: 87ab9925717a307cbda3cea1f2e470ae012fa067
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="manage-drivers-in-system-center-configuration-manager"></a>Illesztőprogramok kezelése a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager biztosít egy illesztőprogram-katalógust, a Configuration Manager-környezetben a Windows alapú eszközök illesztőprogramjainak kezelésére használhat. Az illesztőprogram-katalógus használatával eszközillesztők importálása a Configuration Managerbe, csomagokba csoportosításához, és a csomagok olyan terjesztési pontokra, ahonnan azok az operációs rendszer központi telepítésekor terjesztéséhez. Az eszközök illesztőprogramjai a teljes operációs rendszer célszámítógépre telepítésekor és a Windows PE rendszerindító lemezképpel történő telepítésekor használhatók. A Windows alapú eszközök illesztőprogramjai tartalmazzák a Telepítési információs fájlt (INF), és az eszköz támogatásához szükséges további fájlokat. Az operációs rendszer telepítésekor a Configuration Manager általi a hardverére és platformjára számára az eszköz INF fájljából. A következő segítségével kezelheti az illesztőprogramokat a Configuration Manager környezetben.

##  <a name="BKMK_DriverCategories"></a> Eszközillesztők kategóriái  
 Az eszközillesztők importálásakor azokat kategóriához lehet társítani. Az eszközillesztők kategóriába sorolása megkönnyíti a hasonlóan használt eszközillesztők egy csoportba foglalását az illesztőprogram-katalógusban. Például minden hálózati adapter eszközillesztőjét társíthatja egy adott konkrét kategóriával. Ezután, amikor olyan feladatütemezést hoz létre, amely tartalmazza az [Illesztőprogramok automatikus alkalmazása](../understand/task-sequence-steps.md#BKMK_AutoApplyDrivers) lépést, megadhat egy konkrét eszközillesztő-kategóriát. A Configuration Manager majd megvizsgálja a hardvert, és kiválasztja azokat a megfelelő illesztőprogramokat, amelyeket előkészít a rendszeren a Windows telepítő számára.  

##  <a name="BKMK_ManagingDriverPackages"></a> Illesztőprogram-csomagok  
 A hasonló eszközök illesztőprogramjai csomagokba csoportosíthatók, hogy egyszerűbb legyen az operációs rendszerek központi telepítése. Dönthet például úgy, hogy az egyes számítógépgyártókhoz hoz létre egy-egy illesztőprogram-csomagot. Illesztőprogram-csomagokat az illesztőprogramok illesztőprogram-katalógusba való importálásakor, közvetlenül az **Illesztőprogram-csomagok** csomópontban hozhat létre. Az illesztőprogram-csomag létrehozása után terjeszteni a terjesztési pontokra, mely Configuration Manager ügyfelek telepíthessék az eszközillesztőket azok szükségesek. Ügyeljen a következőkre:  

-   Az illesztőprogram-csomag létrehozásakor a csomag forráshelyének olyan üres hálózati megosztási helyre kell mutatni, amelyiket más illesztőprogram-csomag nem használ, az SMS-szolgáltatónak pedig erre a helyre olvasási és írási jogosultsággal kell rendelkezni.  

-   Eszközillesztők illesztőprogram-csomagba való hozzáadásakor a Configuration Manager az eszközillesztőt az illesztőprogram-csomag forráshelyére másolja. Csak olyan eszközillesztőket lehet felvenni illesztőprogram-csomagba, amelyek importálva lettek, és az illesztőprogram-katalógusban illesztőprogram-csomaghoz engedélyezve lettek.  

-   Ha az eszközillesztők egy részhalmazát szeretné másolni egy meglévő illesztőprogram-csomagból, hozzon létre egy új illesztőprogram-csomagot, és vegye fel abba az eszközillesztők részhalmazát, majd terjessze az új csomagot egy terjesztési pontra.  

 A következő szakaszok ismertetik az illesztőprogram-csomagok létrehozását és kezelését.  

###  <a name="CreatingDriverPackages"></a> Illesztőprogram-csomag létrehozása  
 Az alábbi módon hozhat létre új illesztőprogram-csomagot.  

> [!IMPORTANT]  
>  Illesztőprogram-csomag létrehozásához szükség van egy üres hálózati mappára, amelyet nem használ másik illesztőprogram-csomag. A legtöbb esetben új mappát kell létrehoznia az eljárás megkezdése előtt.  

> [!NOTE]  
>  Ha feladatütemezéssel telepít illesztőprogramokat, kevesebb, mint 500 eszközillesztőt tartalmazó illesztőprogram-csomagokat hozzon létre.  

 Az alábbi eljárással hozhat létre illesztőprogram-csomagot.  

#### <a name="to-create-a-driver-package"></a>Illesztőprogram-csomag létrehozása  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Operációs rendszerek**pontot, majd kattintson az **Illesztőprogram-csomagok**elemre.  

3.  A **Kezdőlap** **Létrehozás** csoportjában kattintson az **Illesztőprogram-csomag létrehozása**elemre.  

4.  A **Név** mezőben adjon meg egy leíró nevet az illesztőprogram-csomag számára.  

5.  A **Megjegyzés** mezőbe leírást adhat meg az illesztőprogram-csomagról (nem kötelező). A leírásnak az illesztőprogram-csomag tartalmával vagy céljával kapcsolatos információval célszerű szolgálnia.  

6.  Az **Elérési út** mezőben adjon meg egy üres forrásmappát az illesztőprogram-csomag számára. A forrásmappa elérési útját az univerzális elnevezési konvenciónak (UNC) megfelelő formátumban adja meg. Minden illesztőprogram-csomagnak egyedi mappát kell használnia.  

    > [!IMPORTANT]  
    >  A helykiszolgáló fiókjának **Írás** és **Olvasás** engedéllyel kell rendelkeznie a megadott forrásmappához.  

 Az új illesztőprogram-csomag nem tartalmaz illesztőprogramot. A következő lépés az illesztőprogramok felvétele a csomagba.  

 Ha az **Illesztőprogram-csomagok** csomópont több csomagot tartalmaz, a csomópont alatt mappák felvételével logikai csoportokba rendezheti a csomagokat.  

###  <a name="BKMK_PackageActions"></a> Az illesztőprogram-csomagok további műveletei  
 Amikor kiválaszt egy vagy több illesztőprogram-csomagot az **Illesztőprogram-csomagok** csomópontból, további műveleteket is elvégezhet a csomagok kezelésével kapcsolatban. Az ilyen műveletek közé tartoznak a következők:  

|Művelet|Leírás|  
|------------|-----------------|  
|**Manuálisan előkészített tartalomfájl létrehozása**|Olyan fájlok létrehozására szolgál, amelyek tartalmak és kapcsolódó metaadatok manuális importálására használhatók. Akkor célszerű manuálisan előkészített tartalmat használni, ha a helykiszolgáló és az illesztőprogram-csomag tárolására szolgáló terjesztési pont között szűk a hálózati sávszélesség.|  
|**Törlés**|Eltávolítja az illesztőprogram-csomagot az **Illesztőprogram-csomagok** csomópontból.|  
|**Tartalom terjesztése**|Az illesztőprogram-csomag terjesztése terjesztési pontokra, terjesztésipont-csoportokba és gyűjteményekhez rendelt terjesztésipont-csoportokba.|  
|**Elérési fiókok kezelése**|Az illesztőprogram-csomaghoz tartozó hozzáférési fiókok hozzáadása, módosítása és eltávolítása.<br /><br /> További információ a csomag-hozzáférési fiókokról: [a Configuration Managerben használt fiókok](../../core/plan-design/hierarchy/accounts.md).|  
|**Áthelyezés**|Az illesztőprogram-csomag áthelyezése másik mappába az **Illesztőprogram-csomagok** csomópontban.|  
|**Terjesztési pontok frissítése**|Az eszközillesztő-csomag frissítése az összes olyan terjesztési ponton, amelyen a csomag megtalálható. A művelet során a rendszer csak a legutóbbi terjesztés óta megváltozott tartalmat másolja.|  
|**Tulajdonságok**|A **Tulajdonságok** párbeszédpanel megnyitására szolgál, amelyen áttekintheti és módosíthatja az eszközillesztő tartalmát és tulajdonságait. például megváltoztathatja az eszközillesztő nevét és leírását, engedélyezheti az eszközillesztőt, és meghatározhatja, hogy mely platformokon futtatható.|  

##  <a name="BKMK_DeviceDrivers"></a> Eszközillesztők  
 Az eszközillesztőket úgy is telepítheti a célszámítógépeken, hogy nem adja hozzá őket a telepítendő operációs rendszer rendszerképéhez. A Configuration Manager biztosít egy illesztőprogram-katalógust, amely az összes Configuration Manager alkalmazásba importálható eszközillesztők hivatkozásait tartalmazza. Az illesztőprogram-katalógusban található a **szoftverkönyvtár** munkaterület és a következő két csomópontot tartalmazza: **Illesztőprogramok** és **illesztőprogram-csomagok**. Az **Illesztőprogramok** csomópontban található az illesztőprogram-katalógusba importált összes illesztőprogram listája. Ebben a csomópontban tekintheti át az egyes importált illesztőprogramok adatait, módosíthatja az illesztőprogram-csomagok és rendszerindító lemezképek által tartalmazott illesztőprogramokat, engedélyezheti és letilthatja az illesztőprogramokat, és így tovább.  

###  <a name="BKMK_ImportDrivers"></a> Eszközillesztők importálása az illesztőprogram-katalógusba  
 Mielőtt azokat az operációs rendszer központi telepítéséhez használhatná, importálni kell az eszköz illesztőprogramjait az illesztőprogramok katalógusába. Az illesztőprogramok jobb kezelése érdekében csak azon eszközök illesztőprogramját importálja, amelyeket az operációs rendszer központi telepítésének részeként tervez telepíteni. Az illesztőprogram-katalógusban az eszközök illesztőprogramjainak több verzióját is tárolhatja, hogy könnyű megoldást biztosítson a létező illesztőprogramok frissítésére, amikor a hálózatán a hardveres eszköz követelményei megváltoznak.  

 Az eszközillesztő importálási folyamata keretében a Configuration Manager beolvassa a szolgáltató, osztály, verzió, aláírás, támogatott hardver és támogatott platform információit, amelyek az eszközhöz kapcsolódnak. Alapértelmezés szerint az eszközillesztőt a rendszer az általa támogatott első hardvereszköz alapján nevezi el, a név azonban később módosítható. A támogatott platformok listája az eszközillesztő INF-fájljában szereplő információkon alapul. Mivel ezek az információk nem minden esetben pontosak, az illesztőprogram-katalógusba való importálást követően manuális módszerrel ellenőrizze, hogy az eszközillesztő támogatott-e.  

 A katalógusba való importálás után illesztőprogram-csomagokhoz és rendszerindítólemezkép-csomagokhoz is hozzáadhatja az eszközillesztőket.  

> [!IMPORTANT]  
>  Az eszközillesztők nem importálhatók közvetlenül az **Illesztőprogramok** csomópont almappáiba. Ha egy eszközillesztőt almappába szeretne importálni, először importálja az **Illesztőprogramok** csomópontba, majd onnan helyezze át a kívánt almappába.  

 Windows-eszközillesztők importálásához kövesse az alábbi eljárást.  

#### <a name="to-import-windows-device-drivers-into-the-driver-catalog"></a>Windows-eszközillesztők importálása az illesztőprogram-katalógusba  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Operációs rendszerek**pontot, majd kattintson az **Illesztőprogramok**elemre.  

3.  A **Kezdőlapon** a **Létrehozás** csoportban kattintson az **Illesztőprogram importálása** elemre az **Új illesztőprogram importálása varázsló**elindításához.  

4.  Az **Illesztőprogram keresése** lapon adja meg a következő beállításokat, majd kattintson a **Tovább**gombra:  

    -   **A következő hálózati elérési útról (UNC) összes illesztőprogram importálása**: Egy adott mappában lévő összes eszközillesztőt szeretne importálni, adja meg a mappa hálózati elérési útját az eszköz illesztőprogram. Például:  **\\\kiszolgálónév\mappa**.  

        > [!NOTE]  
        >  Nagy mennyiségű mappa és illesztőprogramfájl (.inf) esetén az összes illesztőprogram importálásának folyamata hosszabb időt is igénybe vehet.  

    -   **Adott illesztőprogram importálása**: Egy adott illesztőprogram importálni egy mappából, adja meg a hálózati elérési útja (UNC) a Windows-eszközillesztő. INF vagy háttértár tárolási Txtsetup.oem fájlt.  

    -   **Adja meg a beállítást a duplikált illesztőprogramok**: Válassza ki, hogy miként kezelje az illesztőprogram-kategóriákat ismétlődő eszközillesztők importálása a Configuration Manager.  

    > [!IMPORTANT]  
    >  Illesztőprogramok importálásakor a helykiszolgálónak **Olvasás** engedélyre van szüksége a mappához, ellenkező esetben az importálás sikertelen lesz.  

5.  Az **Illesztőprogram adatai** lapon adja meg az alábbi beállításokat, majd kattintson a **Tovább**gombra:  

    -   **Nem (a rendszerindító lemezképek esetén) tárolási vagy hálózati osztályban található illesztőprogramok elrejtése**: Ez a beállítás használatával csak a tárolási és hálózati illesztőprogramokat jeleníti meg, és más, a rendszerindító lemezképeket, például a video- vagy modem-illesztőprogramokat általában nem szükséges illesztőprogramok elrejtése.  

    -   **Digitális aláírás nélküli illesztőprogramok elrejtése**: Ez a beállítás segítségével elrejtheti a digitális aláírással nem rendelkező illesztőprogramokat.  

    -   A listában jelölje ki azokat az illesztőprogramokat, amelyeket szeretne importálni az illesztőprogram-katalógusba.  

    -   **Illesztőprogramok engedélyezése, valamint lehetővé teszi a számítógépek telepítéshez**: Válassza ki az ezzel a beállítással engedélyezheti a számítógépeknek az illesztőprogramok telepítését. A négyzet alapértelmezés szerint be van jelölve.  

        > [!IMPORTANT]  
        >  Ha valamelyik eszközillesztő problémát okoz, vagy szeretné felfüggeszteni egy eszközillesztő telepítését, az **Illesztőprogramok engedélyezése, valamint telepítésük engedélyezése a számítógépek számára** jelölőnégyzet kijelölésének visszavonásával letilthatja az illesztőprogramot. Az illesztőprogramok az importálás után is letilthatók.  

    -   Ha az eszközillesztőket szűrési célból adminisztratív kategóriákhoz szeretné rendelni (például „Asztali gépek” vagy „Notebookok”), kattintson a **Kategóriák** elemre, és válasszon a meglévő kategóriák közül, vagy hozzon létre újat. A kategória-hozzárendeléssel azt is meghatározhatja, hogy a rendszer mely eszközillesztőket alkalmazza központi telepítéskor az [Illesztőprogramok automatikus alkalmazása](../understand/task-sequence-steps.md#BKMK_AutoApplyDrivers) feladatütemezési lépés során.  

6.  Az **Illesztőprogram hozzáadása csomagokhoz** lapon adja meg, hogy az illesztőprogramokat hozzá kívánja-e adni egy csomaghoz, majd kattintson a **Tovább**gombra. Az illesztőprogramok csomaghoz való hozzáadásához vegye figyelembe a következőket:  

    -   Jelölje ki az eszközillesztők terjesztésére szolgáló illesztőprogram-csomagokat.  

         Ha új illesztőprogram-csomagot szeretne létrehozni, kattintson az **Új csomag** parancsra. Ha új illesztőprogram-csomagot hoz létre, meg kell adnia egy hálózati megosztást, amelyet nem használ más illesztőprogram-csomag.  

    -   Ha a csomag már terjesztésre került a terjesztési pontokra, kattintson a párbeszédpanelen az **Igen** gombra a rendszerindító lemezképek frissítéséhez a terjesztési pontokon. Az eszközillesztők addig nem használhatók, amíg nem továbbítja őket a terjesztési pontokra. Ha a **Nem**gombra kattint, akkor ahhoz, hogy a rendszerindító lemezkép tartalmazza a frissített illesztőprogramokat, futtatnia kell a **Terjesztési pont frissítése** műveletet . Ha az illesztőprogram-csomag korábban még nem volt terjesztve, az **Illesztőprogram-csomagok** csomóponton kattintson a **Tartalom terjesztése** elemre.  

7.  Az **illesztőprogram hozzáadása rendszerindító lemezképekhez** lapon adja meg, hogy az eszközillesztőket hozzá kívánja-e adni meglévő rendszerindító lemezképekhez, majd kattintson a **Tovább**gombra. Ha kiválaszt egy rendszerindító lemezképet, vegye figyelembe a következőket:  

    > [!NOTE]  
    >  Az ajánlott eljárásnak megfelelően operációs rendszerek központi telepítéséhez csak háttértárolókhoz és hálózati adapterekhez tartozó eszközillesztőket vegyen fel a rendszerindító lemezképekbe.  

    -   Kattintson a párbeszédpanelen az **Igen** gombra a rendszerindító lemezképek frissítéséhez a terjesztési pontokon. Az eszközillesztők addig nem használhatók, amíg nem továbbítja őket a terjesztési pontokra. Ha a **Nem**gombra kattint, akkor ahhoz, hogy a rendszerindító lemezkép tartalmazza a frissített illesztőprogramokat, futtatnia kell a **Terjesztési pont frissítése** műveletet . Ha az illesztőprogram-csomag korábban még nem volt terjesztve, az **Illesztőprogram-csomagok** csomóponton kattintson a **Tartalom terjesztése** elemre.  

    -   A Configuration Manager figyelmezteti, ha egy vagy több illesztőprogram architektúrája nem felel meg a kiválasztott rendszerindító lemezkép architektúrájának. Ha nem egyeznek, kattintson az **OK** gombra, és térjen vissza az **Illesztőprogram adatai** oldalra, ahol törölheti a kiválasztott rendszerindító lemezkép architektúrájának nem megfelelő illesztőprogramokat. Ha például x64-es és x86-os rendszerindító lemezképet választ, minden illesztőprogramnak támogatnia kell mindkét architektúrát. Ha x64-es rendszerindító lemezképet választ, minden illesztőprogramnak támogatnia kell az x64-es architektúrát.  

        > [!NOTE]  
        >  -   Az architektúra a gyártó által az .INF fájlban ismertetett architektúrán alapul.  
        > -   Ha egy illesztőprogram jelentésében az szerepel, hogy mindkét architektúrát támogatja, akkor azt bármelyik rendszerindító lemezképbe importálhatja.  

    -   A Configuration Manager figyelmezteti, ha nem hálózati vagy tárolási illesztőprogramokat a rendszerindító lemezképhez van, mert a legtöbb esetben nincs szükség a rendszerindító lemezképhez eszközillesztőket hozzá. Az illesztőprogramok hozzáadásához a rendszerindító lemezképhez kattintson az **Igen** gombra, vagy kattintson a **Nem** gombra, ha visszalép és módosítja a kiválasztott illesztőprogramokat.  

    -   A Configuration Manager figyelmezteti, ha egy vagy több kiválasztott illesztőprogram nem rendelkezik megfelelő digitális aláírással. A folytatáshoz kattintson az **Igen** gombra, vagy kattintson a **Nem** gombra, ha visszalép és módosítja a kiválasztott illesztőprogramokat.  

8.  Fejezze be a varázslót.  

###  <a name="BKMK_ModifyDriverPackage"></a> Egy illesztőprogram-csomagban lévő eszközillesztők kezelése  
 Az illesztőprogram-csomagok és a rendszerindító lemezképek módosításához kövesse az alábbi eljárást. Eszközillesztők hozzáadásához vagy eltávolításához keresse meg a kívánt illesztőprogramokat az **Illesztőprogramok** csomópont alatt, és szerkessze azokat a csomagokat vagy lemezképeket, amelyekhez a kiválasztott illesztőprogramok tartoznak.  

#### <a name="to-modify-the-device-drivers-in-a-driver-package"></a>Egy illesztőprogram-csomagban lévő eszközillesztők módosítása  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Operációs rendszerek**pontot, majd kattintson az **Illesztőprogramok**elemre.  

3.  Az **Illesztőprogramok** csomópontban jelölje ki az illesztőprogram-csomaghoz hozzáadni kívánt eszközillesztőket.  

4.  A **Kezdőlap** **Illesztőprogram** csoportjában kattintson a **Szerkesztés**, majd az **Illesztőprogram-csomagok**elemre.  

5.  Jelölje be azon illesztőprogram-csomagok négyzeteit, amelyekhez hozzá szeretné adni az eszközillesztőket, vagy törölje azon illesztőprogram-csomagok négyzeteit, amelyekből el szeretné távolítani az eszközillesztőt.  

     Az eszközillesztők illesztőprogram-csomagba való felvételekor szükség esetén új csomagot is létrehozhat – ehhez kattintson az **Új csomag**elemre az **Illesztőprogram-csomag létrehozása** párbeszédpanel megnyitásához.  

6.  Ha a csomag már terjesztésre került a terjesztési pontokra, kattintson a párbeszédpanelen az **Igen** gombra a rendszerindító lemezképek frissítéséhez a terjesztési pontokon. Az eszközillesztők addig nem használhatók, amíg nem továbbítja őket a terjesztési pontokra. Ha a **Nem**gombra kattint, akkor ahhoz, hogy a rendszerindító lemezkép tartalmazza a frissített illesztőprogramokat, futtatnia kell a **Terjesztési pont frissítése** műveletet . Ha az illesztőprogram-csomag korábban még nem volt terjesztve, az **Illesztőprogram-csomagok** csomóponton kattintson a **Tartalom terjesztése** elemre. Mielőtt elérhetők lennének az illesztőprogramok, frissítenie kell az illesztőprogram-csomagot a terjesztési pontokon.  

     Kattintson az **OK**gombra.  

###  <a name="BKMK_ManageDriversBootImage"></a> Egy rendszerindító lemezképben lévő eszközillesztők kezelése  
 A Windows olyan eszközillesztői vehetők fel, amelyek importálva lettek a rendszerindító lemezképek illesztőprogram-katalógusába. A rendszerindító lemezkép illesztőprogram-katalógusába történő felvételéhez használja a következő irányelveket:  

-   A rendszerindító lemezképekbe csak a tömegtároló és a hálózati adapter eszközillesztőit vegye fel, mert az egyéb típusúakra általában nincs szükség. A nem szükséges illesztőprogramok szükségtelenül növelik a rendszerindító lemezkép méretét.  

-   Csak Windows 10-hez készült eszközillesztőket vegyen fel a rendszerindító lemezképbe, mert a szükséges Windows PE-verzió Windows 10-alapú.  

-   Győződjön meg róla, hogy a rendszerindító lemezkép architektúrájának megfelelő eszközillesztőt használja.  Ne vegyen fel x64 rendszerindító lemezképbe x86 eszközillesztőt.  

 Egy rendszerindító lemezképben lévő eszközillesztők hozzáadásához vagy eltávolításához kövesse az alábbi eljárást.  

#### <a name="to-modify-the--device-drivers-associated-with-a-boot-image"></a>Egy rendszerindító lemezképhez tartozó eszközillesztők módosítása  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Operációs rendszerek**pontot, majd kattintson az **Illesztőprogramok**elemre.  

3.  Az **Illesztőprogramok** csomópontban jelölje ki az illesztőprogram-csomaghoz hozzáadni kívánt eszközillesztőket.  

4.  A **Kezdőlap** **Illesztőprogram** csoportjában kattintson a **Szerkesztés**, majd a **Rendszerindító lemezképek**elemre.  

5.  Jelölje be azon rendszerindító lemezképek négyzeteit, amelyekhez hozzá szeretné adni az eszközillesztőket, vagy törölje azoknak a négyzeteit, amelyekből el szeretné távolítani az eszközillesztőt.  

6.  Ha nem szeretné frissíteni a rendszerindító lemezképet tároló terjesztési pontokat, vonja vissza a **Terjesztési pontok frissítése a befejezés után** jelölőnégyzet kijelölését. A rendszer alapértelmezés szerint a rendszerindító lemezképpel együtt a terjesztési pontokat is frissíti.  

     Kattintson az **OK** gombra, és vegye figyelembe a következőket:  

    -   Kattintson a párbeszédpanelen az **Igen** gombra a rendszerindító lemezképek frissítéséhez a terjesztési pontokon. Az eszközillesztők addig nem használhatók, amíg nem továbbítja őket a terjesztési pontokra. Ha a **Nem**gombra kattint, akkor ahhoz, hogy a rendszerindító lemezkép tartalmazza a frissített illesztőprogramokat, futtatnia kell a **Terjesztési pont frissítése** műveletet . Ha az illesztőprogram-csomag korábban még nem volt terjesztve, az **Illesztőprogram-csomagok** csomóponton kattintson a **Tartalom terjesztése** elemre.  

    -   A Configuration Manager figyelmezteti, ha egy vagy több illesztőprogram architektúrája nem felel meg a kiválasztott rendszerindító lemezkép architektúrájának. Ha nem egyeznek, kattintson az **OK** gombra, és térjen vissza az **Illesztőprogram adatai** oldalra, ahol törölheti a kiválasztott rendszerindító lemezkép architektúrájának nem megfelelő illesztőprogramokat. Ha például x64-es és x86-os rendszerindító lemezképet választ, minden illesztőprogramnak támogatnia kell mindkét architektúrát. Ha x64-es rendszerindító lemezképet választ, minden illesztőprogramnak támogatnia kell az x64-es architektúrát.  

        > [!NOTE]  
        >  -   Az architektúra a gyártó által az .INF fájlban ismertetett architektúrán alapul.  
        > -   Ha egy illesztőprogram jelentésében az szerepel, hogy mindkét architektúrát támogatja, akkor azt bármelyik rendszerindító lemezképbe importálhatja.  

    -   A Configuration Manager figyelmezteti, ha nem hálózati vagy tárolási illesztőprogramokat a rendszerindító lemezképhez van, mert a legtöbb esetben nincs szükség a rendszerindító lemezképhez eszközillesztőket hozzá. Az illesztőprogramok hozzáadásához a rendszerindító lemezképhez kattintson az **Igen** gombra, vagy kattintson a **Nem** gombra, ha visszalép és módosítja a kiválasztott illesztőprogramokat.  

    -   A Configuration Manager figyelmezteti, ha egy vagy több kiválasztott illesztőprogram nem rendelkezik megfelelő digitális aláírással. A folytatáshoz kattintson az **Igen** gombra, vagy kattintson a **Nem** gombra, ha visszalép és módosítja a kiválasztott illesztőprogramokat.  

7.  Kattintson az **OK**gombra.  

###  <a name="BKMK_DriverActions"></a> Az eszközillesztők további műveletei  
 Amikor egy vagy több eszközillesztőt kiválaszt az **Illesztőprogramok** csomópontból, további eszközillesztő-kezelési műveleteket is végrehajthat. Az ilyen műveletek közé tartoznak a következők:  

|Művelet|Leírás|  
|------------|-----------------|  
|**Kategorizálás**|Adminisztratív kategóriák törlése, kezelése vagy beállítása a kijelölt eszközillesztők kapcsán.|  
|**Törlés**|Az eszközillesztő törlése az **Illesztőprogramok** csomópontból és a kapcsolódó terjesztési pontokról.|  
|**Letiltás**|Letiltja az eszközillesztő telepítését. Úgy, hogy a Configuration Manager-ügyfél számítógépeinek és feladatütemezései nem telepíthetik azokat az operációs rendszerek telepítésekor ideiglenesen letilthatja az eszközillesztőket. **Megjegyzés:**  A letiltás művelet csak megakadályozza, hogy illesztőprogramokat az illesztőprogramok automatikus alkalmazását végrehajtó feladatütemezési lépés segítségével hajtja végre.|  
|**Engedélyezés**|Lehetővé teszi, hogy a Configuration Manager-ügyfélszámítógépek és a feladatütemezések az eszközillesztő telepítéséhez, az operációs rendszer központi telepítésekor.|  
|**Áthelyezés**|Az eszközillesztő áthelyezése másik mappába az **Illesztőprogramok** csomópontban.|  
|**Tulajdonságok**|Megnyitja a **Tulajdonságok** párbeszédpanelt, amelyen áttekintheti és módosíthatja az eszközillesztő tulajdonságait. például megváltoztathatja az eszközillesztő nevét és leírását, engedélyezheti az eszközillesztőt, és meghatározhatja, hogy mely platformokon futtatható.|  

##  <a name="BKMK_TSDrivers"></a> Eszközillesztők telepítése feladatütemezések használatával  
 Feladatütemezések használatával automatikussá teheti, hogy az operációs rendszer hogyan legyen telepítve központilag. A feladatütemezésben lévő egyes lépések olyan adott műveletet hajthatnak végre, mint például egy eszközillesztő telepítése. Az operációs rendszerek központi telepítésekor a következő két feladatütemezési lépést használhatja az eszközillesztők telepítéséhez.  

-   [Illesztőprogramok automatikus alkalmazása](../understand/task-sequence-steps.md#BKMK_AutoApplyDrivers): Ez a lépés lehetővé teszi automatikusan egyeztetheti és telepítheti az eszközillesztőket az operációs rendszer központi telepítésének részeként. A feladatütemezési lépés konfigurálható úgy, hogy az egyes észlelt hardveres eszközök részére csak a legjobban illeszkedő illesztőprogramot telepítse, illetve megadhatja azt, hogy mindegyik észlelt hardverhez telepítse az összes kompatibilis illesztőprogramot, és majd a Windows Telepítő válassza ki a legjobbat. Ezenkívül megadhatja az eszközillesztők egyik kategóriáját is, hogy korlátozza ebben a lépésben az illesztőprogramok használhatóságát.  

-   [Illesztőprogram-csomag alkalmazása](../understand/task-sequence-steps.md#BKMK_ApplyDriverPackage): Ez a lépés lehetővé teszi minden eszközillesztőt egy adott illesztőprogram-csomagban lévő elérhetővé tétele a Windows telepítő számára. A Windows Telepítő megkeresi a megadott illesztőprogram-csomagban a szükséges eszközillesztőket. Különálló adathordozó létrehozásakor ezzel a lépéssel kell telepítenie az eszközillesztőket.  

 Ha ezeket a feladatütemezési lépéseket használja, azt is megadhatja, hogy az eszközillesztők hogyan legyenek telepítve olyan számítógépre, amelyiknél az operációs rendszert központilag telepíti. További információkért lásd: [feladatok automatizálásához a feladatütemezések kezeléséhez](../deploy-use/manage-task-sequences-to-automate-tasks.md).  

##  <a name="BKMK_InstallingDeviceDiriversTS"></a> Eszközillesztők központi telepítése számítógépeken feladatütemezések használatával  
 Az alábbi eljárással telepíthet eszközillesztőket az operációs rendszer központi telepítése keretében.  

#### <a name="use-a-task-sequence-to-install-device-drivers"></a>Eszközillesztők telepítése feladatütemezés használatával  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Operációs rendszerek**pontot, majd kattintson a **Feladatütemezések**elemre.  

3.  A **Feladatütemezések** csomópontban jelölje ki azt a feladatütemezést, amelyet módosítani szeretne az eszközillesztő telepítéséhez, majd kattintson a **Szerkesztés**parancsra.  

4.  Kattintson a **Hozzáadás** gombra ott, ahol hozzá szeretné adni az **Illesztőprogram**lépéseit, majd válassza az **Illesztőprogramok**lehetőséget.  

5.  Adja hozzá az **Illesztőprogramok automatikus alkalmazása** lépést, ha a feladatütemezés során az összes eszközillesztőt vagy a megjelölt kategóriákat telepíteni szeretné. Adja meg a lépés beállításait a **Tulajdonságok** lapon, majd a lépéshez tartozó feltételeket a **Beállítások** lapon.  

     Adja hozzá az **Illesztőprogram-csomag alkalmazása** lépést, ha a feladatütemezés során csak a kijelölt csomagban található eszközillesztőket szeretné telepíteni. Adja meg a lépés beállításait a **Tulajdonságok** lapon, majd a lépéshez tartozó feltételeket a **Beállítások** lapon.  

    > [!IMPORTANT]  
    >  A **Beállítások** lapon **A lépés letiltása** elemet választva letilthatja a lépést a feladatütemezés során tapasztalt problémák elhárításához.  

6.  A feladatütemezés mentéséhez kattintson az **OK** gombra.  

 Egy feladatütemezés egy operációs rendszer telepítéséhez létrehozásával kapcsolatos további információkért lásd: [hozzon létre egy feladatütemezést az operációs rendszer telepítéséhez](../deploy-use/create-a-task-sequence-to-install-an-operating-system.md).  

##  <a name="BKMK_DriverReports"></a> Illesztőprogram-kezelési jelentések  
 Az illesztőprogram-katalógusban lévő eszközillesztőkre vonatkozó általános információk meghatározásához használhatja az **Illesztőprogram-kezelő** jelentéseinek kategóriájában található jelentéseket. A jelentésekkel kapcsolatos további információkért lásd: [jelentéskészítési](../../core/servers/manage/reporting.md).

