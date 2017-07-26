---
title: "Hálózati sávszélesség szabályozása a tartalom |} Microsoft Docs"
description: "Ütemezés, sávszélesség-szabályozás és a manuálisan előkészített tartalmat a System Center Configuration Manager konfigurálása."
ms.custom: na
ms.date: 2/6/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e80d1151-91db-4a27-8411-a957297b67d0
caps.latest.revision: 15
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 37e4f27fcea0bbdd39c9fd3ab38aa46e3059f73a
ms.openlocfilehash: d9dff97126c34a726677de60dd7647370c553b6e
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---

# <a name="manage-network-bandwidth-for-content"></a>Hálózati sávszélesség szabályozása a tartalom
A tartalomkezelési folyamathoz a System Center Configuration Manager használt hálózati sávszélesség kezeléséhez érdekében használható beépített vezérlők ütemezési és sávszélesség-szabályozás. Manuálisan előkészített tartalmat is használható. A következő szakaszok ismertetik részletesebben ezeket a beállításokat.

##  <a name="BKMK_PlanningForThrottling"></a>Ütemezési és sávszélesség-szabályozás  

 Hozzon létre egy csomagot, módosítsa a tartalom forrásának elérési útját vagy frissíti a tartalmat a terjesztési ponton, a fájlokat a rendszer a forrás elérési útjáról a helykiszolgálón lévő tartalomtárba másolja. Ezt követően a tartalom átmásolva a tartalomtár a helykiszolgálón a terjesztési pontokon található tartalomtárhoz. Ha a tartalom forrásfájljainak frissítésekor és a forrásfájlok terjesztésének megtörténte, a Configuration Manager csak az új vagy frissített fájlokat kéri le, és majd elküldi azokat a terjesztési pontra.

 Ütemezési és szabályozási vezérlőket is használhatja, pont-pont kommunikáció, és a helykiszolgáló és a távoli terjesztési pontok közötti kommunikációhoz. Ha hálózati sávszélessége korlátozott még az ütemezési és szabályozási vezérlők beállítása után, érdemes lehet a terjesztési pont a tartalom manuális előkészítését.  

 A Configuration Managerben ehhez is ütemezés beállításához és sávszélesség-szabályozási beállítások a távoli terjesztési pontokra, amelyekkel meghatározhatja, hogy mikor és hogyan terjessze a tartalmakat történik. Mindegyik távoli terjesztési pontra is rendelkezik különböző konfigurációkat, amelyek segítenek a cím hálózati sávszélességgel kapcsolatos korlátozásai a helykiszolgálóról a távoli terjesztési pontra. A vezérlők ütemezési és sávszélesség-szabályozás a távoli terjesztési pontra a szabványos küldő címének beállításaihoz hasonlóak. Ebben az esetben a beállításokat egy Package Transfer Manager nevű új összetevő által használt.

 A Package Transfer Manager eljuttatja a tartalmat helykiszolgálóról, másodlagos hely vagy elsődleges hely helyrendszerre telepített terjesztési pontra. A sávszélesség-szabályozási beállítások nincsenek megadva a **sebességhatárok** fülre, és az ütemezési beállítások adhatók meg a **ütemezés** lapon, a terjesztési ponton, amely nem a helykiszolgálón. A beállításokat az időzónát a küldő helyről, nem a terjesztési pont alapulnak.  

> [!IMPORTANT]  
>  A **sebességhatárok** és **ütemezés** lapok csak a nem a helykiszolgálón telepített terjesztési pontok tulajdonságaiban jelennek meg.  

További információkért lásd: [telepíteni és konfigurálni a terjesztési pontokat a System Center Configuration Manager](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points).  

##  <a name="BKMK_PrestagingContent"></a>Előzetesen beállított tartalomhoz  
 Előkészíthet tartalmat a tartalomfájlokat vegyen fel egy helykiszolgálón vagy terjesztési ponton lévő tartalomtárba, a tartalom terjesztése előtt. Mivel a tartalomfájlok már eleve a tartalomtárban vannak, nem kell másolnia azokat a hálózaton keresztül a tartalom terjesztésekor. Akkor is készíthet elő tartalomfájlokat alkalmazásokhoz és csomagokhoz.  

A Configuration Manager konzolon válassza ki a manuálisan előkészíteni, és a kívánt tartalmat a **manuálisan előkészített tartalomfájl létrehozása varázsló**. Ezzel létrehoz egy tömörített, manuálisan előkészített tartalomfájlt, amely tartalmazza a fájlok és a tartalomhoz kapcsolódó metaadatokkal. Ezután manuálisan importálhatja egy helykiszolgáló vagy terjesztési pont a tartalmat. Vegye figyelembe a következő szempontokat:  

-   Amikor a manuálisan előkészített tartalomfájlt helykiszolgálón importálja, a tartalomfájlok a helykiszolgálón lévő tartalomtárba hozzá, és regisztrálja a helykiszolgáló adatbázisából.  

-   Amikor a manuálisan előkészített tartalomfájlt terjesztési ponton importálja, a tartalomfájlokat a terjesztési ponton lévő tartalomtárba kerülnek. Egy állapotüzenetet küld a helykiszolgálónak, amelyben arról tájékoztatja a helyet, hogy a tartalom elérhető a terjesztési ponton.  

Konfigurálhatja a terjesztési pontot **előkészített** a tartalomterjesztés könnyebb kezelése. Ezt követően amikor tartalmat terjeszt, választhat, hogy el kívánja:  

-   Mindig manuálisan előkészíti a tartalmat a terjesztési ponton.  

-   A csomag kezdő tartalmát, és aztán a normál tartalomterjesztési folyamatot a tartalom frissítéseit.  

-   A csomag tartalmának mindig használjon a normál tartalomterjesztési folyamatot.  

###  <a name="BKMK_DetermineToPrestageContent"></a>Döntés a tartalom manuális előkészítéséről  
 Az alkalmazások és csomagok a következő esetekben a tartalom-érdemes manuális előkészítéséről:  

-   **A probléma megoldására korlátozott hálózati sávszélesség a helykiszolgálóról egy terjesztési pontra.** Ha ütemezési és sávszélesség-szabályozás nem elegendő a sávszélességgel kapcsolatos szempontok kielégítéséhez, fontolja meg a terjesztési pont a tartalom manuális előkészítését. Minden terjesztési ponton megtalálható az **engedélyezése e terjesztési pont használatát előzetesen beállított tartalomhoz** , amelyek segítségével a terjesztési pont tulajdonságainak beállítása. Ha engedélyezi ezt a beállítást, a terjesztési pontot, amelynél a manuálisan előkészített terjesztési pontok, és kiválaszthatja, hogyan kezelheti a tartalmat egy csomagonként a.  

    A következő beállítások érhetők el, egy alkalmazás, a csomag, az illesztőprogram-csomag, a rendszerindító lemezképet, a operációs rendszeri telepítőcsomag és a lemezkép tulajdonságainak. Ezek a beállítások lehetővé teszik a módját a terjesztési előkészítettként azonosított távoli terjesztési pontokon kezelt tartalom:  

    -   **Tartalom automatikus letöltése, amikor csomagok vannak hozzárendelve a terjesztési pontokra**: Használja ezt a beállítást kisebb csomagok, és az ütemezési és sávszélesség-szabályozási beállítások megfelelő kontrollt biztosítanak a tartalom terjesztése.  

    -   **Csak a tartalmi változások letöltése a terjesztési pontra**: Használja ezt a beállítást, ha a tartalom jövőbeli frissítései várhatóan kisebbek, mint az eredeti csomagot lesznek a csomagban. Például manuálisan előkészítheti egy alkalmazás, például a Microsoft Office, mert a kezdeti csomagméret 700 MB-nál nagyobb és túl nagy a hálózaton keresztüli küldéshez. Csomag Tartalomfrissítések azonban 10 MB-nál kevesebb lehet, és fogadhatók a hálózaton keresztül terjeszteni. Egy másik példa lehet az illesztőprogram-csomagok, ahol a kezdeti mérete nagy, de előfordulhat, hogy a csomag túl növekményes frissítések kis.  

    -   **Tartalmának manuális másolása a csomag a terjesztési pontra**: Használja ezt a beállítást, ha nagy méretű, például operációs rendszert tartalmazó csomagok és soha nem használni kívánt a hálózaton keresztül terjeszteni a tartalmat a terjesztési pontra. Ha ezt a beállítást kell előkészíteni a tartalmat a terjesztési ponton.  

    > [!IMPORTANT]  
    >  Az előző beállítások egy csomagonként alkalmazhatók, és csak használata, amikor a terjesztési pont előkészítettként van azonosítva. Nem azonosított manuálisan előkészített terjesztési pontok figyelmen kívül hagyja ezeket a beállításokat. Ebben az esetben a tartalom terjesztése mindig a hálózaton a helykiszolgálóról a terjesztési pontokra.  

-   **A helykiszolgálón lévő tartalomtár visszaállítása.** Ha egy helykiszolgáló meghibásodik, a tartalomtárban lévő csomagokkal és alkalmazásokkal kapcsolatos információkat a visszaállítási folyamat részeként van visszaáll a helyadatbázisban, de a tartalomtár fájljainak visszaállítását nem végzi meg a folyamat részeként. Ha nem rendelkezik a fájl biztonsági másolattal a fájlrendszerről a tartalomtár visszaállításához, létrehozhat egy manuálisan előkészített tartalomfájlt, amely tartalmazza a szükséges csomagokat és alkalmazásokat kell, hogy egy másik helyről. Majd nyerhet ki a manuálisan előkészített tartalomfájlt a helyreállított helykiszolgálón. További információ a helykiszolgáló biztonsági mentéséhez és a helyreállítási: [biztonsági mentés és helyreállítás a System Center Configuration Manager](/sccm/protect/understand/backup-and-recovery).  

