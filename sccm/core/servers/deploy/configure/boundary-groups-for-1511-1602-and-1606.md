---
title: "Az 1511-es, a 1602-es és a 1606 határcsoportok |} System Center Configuration Managerben"
description: "A Configuration Manager verzióira 1511-es, a 1602-es és a 1606 használják a határcsoportokat."
ms.custom: na
ms.date: 2/8/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: dec1e0d7-5864-43a8-9f56-413923b3914e
caps.latest.revision: 10
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 640cdc67f301a81a45bf27f95eb03cbc8754a9aa
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="boundary-groups-for-system-center-configuration-manager-version-1511-1602-and-1606"></a>System Center Configuration Manager 1511-es, a 1602-es és a 1606 határcsoportok

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A jelen témakörben található információk csak az 1511-es, a 1602-es és a 1606 a System Center Configuration Manager verziójú határcsoportok használatával elő.
Ha 1610 vagy újabb verzióját használja, tekintse meg [határcsoportok konfigurálása](/sccm/core/servers/deploy/configure/boundary-groups) újratervezett határcsoportok használatával kapcsolatos információt.  


##  <a name="BKMK_BoundaryGroups"></a> Boundary groups  
 Határcsoportok létrehozásával logikailag csoportosíthatja az egymáshoz kapcsolódó hálózati helyeket (határokat), ami megkönnyíti az infrastruktúra kezelését. Ahhoz, hogy egy határcsoport használhatóvá váljon, előbb határokat kell hozzárendelnie. Az ügyfelek a határcsoport-konfigurációt a következőre használják:  

-   Automatikus helyhozzárendelés  

-   Tartalom helye  

-   Előnyben részesített felügyeleti pontok

    Ha előnyben részesített felügyeleti pontokat használja, engedélyeznie kell ezt a beállítást a hierarchiához és helyett a határcsoport konfigurációjának. Tekintse meg a *előnyben részesített felügyeleti pontok használatának engedélyezése* Ez a témakör későbbi részében található.  

A határcsoportok beállításakor adja hozzá egy vagy több határt a határcsoportba. Majd konfigurálása ezeken a határokon belül található ügyfelek által használandó további beállításokat.  

#### <a name="to-create-a-boundary-group"></a>Határcsoport létrehozása  

1.  Kattintson a Configuration Manager konzol **felügyeleti** > **Hierarchiakonfiguráció** >  **Határcsoportok**.  

2.  Az a **Home** lap a **létrehozása** csoportjában válassza **Határcsoport létrehozása**.  

3.  Az a **Határcsoport létrehozása** párbeszédpanelen válassza ki a **általános** lapra, és írja be a **neve** a határcsoport számára.  

4.  Válasszon **OK** az új határcsoport mentéséhez.  

#### <a name="to-set-up-a-boundary-group"></a>A határcsoport beállítása  

1.  Kattintson a Configuration Manager konzol **felügyeleti** > **Hierarchiakonfiguráció** >  **Határcsoportok**.  

2.  Válassza ki a módosítani kívánt határcsoportban.  

3.  Az a **Home** lap a **tulajdonságok** csoportjában válassza **tulajdonságok**.  

4.  Az a **tulajdonságok** párbeszédpanel a határcsoport, válassza ki a **általános** lapon a határcsoporthoz tagként tartozó határok módosításához:  

    -   Adja hozzá a határokat, válassza a **Hozzáadás**, jelölje be a jelölőnégyzetet, egy vagy több határ jelölőnégyzetét, és válassza a **OK**.  

    -   Határok eltávolításához jelölje ki a megfelelő határt, és válassza a **eltávolítása**.  

5.  Válassza ki a **hivatkozások** lapon, a helyhozzárendelés és a társított helyrendszer-kiszolgáló konfigurációjának módosítása:  

    -   Ahhoz, hogy ezt a határcsoportot a hely hozzárendeléséhez ügyfelek által használandó, jelölje be a jelölőnégyzetet a **használja ezt a határcsoportot a hely hozzárendeléséhez**, és válasszon egy helyet a **hozzárendelt hely** legördülő listában.  

    -   Ehhez a határcsoporthoz társított elérhető helyrendszer-kiszolgálók beállítása:  

    1.  Válasszon **Hozzáadás**, majd jelölje be egy vagy több kiszolgáló jelölőnégyzetét. A kiszolgálókat a rendszer társított helyrendszer-kiszolgálóként adja hozzá a határcsoporthoz. Csak a telepített és támogatott helyrendszerszerepkörrel rendelkező kiszolgálók érhetők el.  

        > [!NOTE]  
        >  Az elérhető helyrendszerek bármilyen kombinációját kijelölheti a hierarchia bármelyik helyéről. A beállított helyrendszerek az ehhez a határcsoporthoz tagként tartozó egyes határok tulajdonságai közt a **Helyrendszerek** lapon láthatóak.  

    2.  Eltávolít egy kiszolgálót a határcsoporthoz, válassza ki a kiszolgálót, és válassza a **eltávolítása**.  

        > [!NOTE]  
        >  Állítsa le ezt a határcsoportot helyrendszerek társításához használatát, el kell távolítania társított helyrendszer-kiszolgálóként felsorolt összes kiszolgálójára.  

    3.  Ha módosítani szeretné a hálózati kapcsolat sebességét a határcsoporthoz tartozó helyrendszer-kiszolgáló, válassza ki a kiszolgálót, és válassza **kapcsolat megváltoztatása**.  

         Alapértelmezés szerint a kapcsolat sebességének beállítása minden helyrendszernél van **gyors**, de módosítható az a sebesség **lassú**. A hálózati kapcsolat sebessége és a központi telepítés konfigurációja határozza meg, hogy egy ügyfél letölthet-e tartalmat a kiszolgálóról.  

6.  Válasszon **OK** a határcsoport tulajdonságainak bezárásához és a konfiguráció mentéséhez.  

#### <a name="to-associate-a-content-deployment-server-or-management-point-with-a-boundary-group"></a>Tartalomtelepítő kiszolgáló vagy felügyeleti pont határcsoporthoz való társítása  

1.  Kattintson a Configuration Manager konzol **felügyeleti** > **Hierarchiakonfiguráció** >  **Határcsoportok**.  

2.  Válassza ki a módosítani kívánt határcsoportban.  

3.  Az a **Home** lap a **tulajdonságok** csoportjában válassza **tulajdonságok**.  

4.  Az a **tulajdonságok** párbeszédpanel a határcsoport, válassza ki a **hivatkozások** lapon.  

5.  A **helyrendszer-kiszolgálók kiválasztása**, válassza a **Hozzáadás**, jelölje be a jelölőnégyzetet, a helyrendszer-kiszolgálók, a határcsoporthoz társítani, és válassza a kívánt **OK**.  

6.  Válasszon **OK** zárja be a párbeszédpanelt, és a határcsoport konfigurációjának mentéséhez.  

#### <a name="to-enable-use-of-preferred-management-points"></a>Előnyben részesített felügyeleti pontok használatának engedélyezése  

1.  A Configuration Manager konzolon válassza a **felügyeleti** > **Helykonfiguráció** > **helyek**, majd a a **Home** lapra, majd **Hierarchiabeállítások**.  

2.  Az a **általános** lapján **Hierarchiabeállítások**, válassza a **ügyfelek részesítsék előnyben a határcsoportokban megadott felügyeleti pontok használatát**.  

3.  Válasszon **OK** zárja be a párbeszédpanelt, és a konfiguráció mentéséhez.  

#### <a name="to-set-up-a-fallback-site-for-automatic-site-assignment"></a>Az automatikus helyhozzárendelés tartalék helyének beállítása  

1.  Kattintson a Configuration Manager konzol **felügyeleti** > **Helykonfiguráció** >  **helyek**.  

2.  Az a **Home** lap a **helyek** csoportjában válassza **Hierarchiabeállítások**.  

3.  A a **általános** lapra, jelölje be a jelölőnégyzetet a **tartalék hely használata**, és válasszon egy helyet a **tartalék hely** legördülő listából.  

4.  Válasszon **OK** a konfiguráció mentéséhez.  

 A következő szakaszok további információkat tartalmaznak a határcsoportok konfigurációiról.  

###  <a name="BKMK_BoundarySiteAssignment"></a> Helyhozzárendelés  
 Az ügyfelek egy hozzárendelt helyet határcsoportokhoz állíthat be.  

-   Az automatikus helyhozzárendelést használó, újonnan telepített ügyfelek az ügyfél aktuális hálózati helyét tartalmazó határcsoporthoz hozzárendelt helyhez csatlakoznak.  

-   A helyhez hozzárendelt ügyfél nem módosítja a helyhozzárendelését, amikor az ügyfél hálózati helye módosul. Például ha az ügyfél a határ, amelyen egy eltérő hely-hozzárendelésű határcsoportban által képviselt új hálózati helyre barangol, az ügyfél hozzárendelt helye változatlan marad.  

-   Amikor az Active Directory-rendszerfelderítés új erőforrást derít fel, a felderített erőforrásra vonatkozó hálózati információkat a határcsoportokban található határokhoz képest értékeli ki. Ez a folyamat az új erőforrást egy hozzárendelt helyhez társítja, és ezt tudja használni az ügyfélleküldéses telepítési mód.  

-   Ha egy határ több, különböző hozzárendelt helyekkel rendelkező határcsoporthoz tagja, az ügyfelek véletlenszerűen választanak a helyek.  

-   Egy határcsoporthoz hozzárendelt helyhez módosítások csak az új hely-hozzárendelési műveleteket. A korábban egy helyhez hozzárendelt ügyfelek nem értékelik ki újra a módosításokat a határcsoport konfigurációjában (vagy a saját hálózati helyükön) alapján helyhozzárendeléseiket.  

Az ügyfelek helyhozzárendeléséről kapcsolatban bővebben lásd: [automatikus helyhozzárendelés használata számítógépekhez](../../../../core/clients/deploy/assign-clients-to-a-site.md#BKMK_AutomaticAssignment) a [ügyfelek hozzárendelése a System Center Configuration Manager hely](../../../../core/clients/deploy/assign-clients-to-a-site.md).  

###  <a name="BKMK_BoundaryContentLocation"></a> A tartalom helye  
 Mindegyik határcsoport egy vagy több terjesztési pontok és állapotáttelepítési pontok állíthat be, és ugyanazt a terjesztési pontot és állapotáttelepítési pontok társíthatja több határcsoporthoz.  

-   **Szoftverterjesztés közben**az ügyfelek kérnek egy helyet a telepítési tartalom számára. A Configuration Manager elküldi az ügyfélnek az ügyfél aktuális hálózati helyét tartalmazó határcsoporthoz társított terjesztési pontok listáját.  

-   **Operációs rendszer központi telepítése során**, az ügyfelek kérnek egy helyet elküldeni vagy fogadni az állapotáttelepítési adatokat. A Configuration Manager elküldi az ügyfélnek az ügyfél aktuális hálózati helyét tartalmazó határcsoporthoz társított állapotáttelepítési pontok listáját.  

Ez a viselkedés lehetővé teszi, hogy az ügyfél, ahonnan a tartalmat a legközelebbi kiszolgálót válassza vagy az állapotáttelepítési adatokat.  

###  <a name="BKMK_PreferredMP"></a> Előnyben részesített felügyeleti pontok  
 Előnyben részesített felügyeleti pontok segítségével egy ügyfelet, mely az aktuális hálózati hely (határ) társított felügyeleti pontot.  

-   Egy ügyfél kísérletet tesz egy előnyben részesített felügyeleti pontot használ a hozzárendelt helyéről, mielőtt egy felügyeleti pontot használ a hozzárendelt helyről, amely nincs beállítva előnyben részesítettként.  

-   Használja ezt a beállítást, kell engedélyezni a hierarchiában, és beállítása határcsoportokat az egyes elsődleges helyeken kell lennie az adott határcsoport társított határaihoz társított felügyeleti pontokat tartalmazza  

-   Ha előnyben részesített felügyeleti pontok vannak beállítva, és egy ügyfél rendszerezi a felügyeleti listáját mutat, az ügyfél helyek az előnyben részesített felügyeleti pontokat a hozzárendelt felügyeleti pontok listáját, beleértve az ügyfél hozzárendelt helyének összes felügyeleti pontja tetején.  

> [!NOTE]  
>  Egy ügyfél barangolás közben, például amikor egy hordozható számítógép egy távoli iroda választ, és, hálózati helye módosul használhatja a helyi oldal felügyeleti pontot (vagy proxy felügyeleti pont) az új helyre, mielőtt megpróbálja egy felügyeleti pont használatát a hozzárendelt helyről (amely az előnyben részesített felügyeleti pontokat tartalmazza).  Lásd: [ismertetése ügyfelek és a System Center Configuration Manager szolgáltatáskeresés](../../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md) további információt.  

###  <a name="BKMK_BoundaryOverlap"></a> Átfedésben lévő határok  
 Configuration Manager a tartalmak helyénél támogatja az átfedésben lévő határokat tartalmazó konfigurációkat:  

-   **Amikor egy ügyfél tartalmat igényel**, és az ügyfél hálózati helye több határcsoporthoz tartozik, a Configuration Manager elküldi az ügyfélnek az összes olyan terjesztési pontot, amelyen megtalálható a tartalom listáját.  

-   **Amikor egy ügyfél kiszolgálót kér, hogy elküldeni vagy fogadni a állapotáttelepítési adatainak**, és az ügyfél hálózati helye több határcsoporthoz tartozik, a Configuration Manager elküldi az ügyfélnek az összes olyan állapotáttelepítési pont az ügyfél aktuális hálózati helyét tartalmazó határcsoporthoz társított listáját.  

Ez a viselkedés lehetővé teszi, hogy az ügyfél, ahonnan a tartalmat a legközelebbi kiszolgálót válassza vagy az állapotáttelepítési adatokat.  

###  <a name="BKMK_BoudnaryNetworkSpeed"></a> A hálózati kapcsolat sebessége  
 A hálózati kapcsolat sebességét minden helyrendszer-kiszolgáló egy határcsoportban állíthatja be. Ez a beállítás a határcsoporthoz konfigurációtól függően helyrendszer csatlakozó ügyfelek vonatkozik. Ugyanahhoz a helyrendszer-kiszolgálóhoz eltérő határcsoportokban különböző kapcsolati sebességet lehet beállítani.  

 Alapértelmezés szerint a hálózati kapcsolat sebességét értéke **gyors**, de módosítható úgy, hogy **lassú**. A hálózati kapcsolat sebessége és a központi telepítés konfigurálása ellenőrizze, hogy egy ügyfél letölthet tartalmat egy terjesztési pontról Ha az ügyfél egy hozzá társított határcsoportban szerepel.  

 Hogyan befolyásolja a hálózati kapcsolat sebességének konfigurációja hogyan ügyfelek tartalmat beolvasni kapcsolatban bővebben lásd: [tartalom forráshelyei – esetek](../../../../core/plan-design/hierarchy/content-source-location-scenarios.md).  

