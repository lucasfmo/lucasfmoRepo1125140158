---
title: "Tartalom kezelése – alapok |} Microsoft Docs"
description: "Ezen eszközök és beállítások a System Center Configuration Managerben kezelheti a központilag telepített tartalomhoz."
ms.custom: na
ms.date: 05/04/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c201be2a-692c-4d67-ac95-0a3afa5320fe
caps.latest.revision: 28
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 212628639300e9c361f7cee61b3df6b1cb6874ce
ms.openlocfilehash: f73dde64e0e8a0fc49f45b3afb3b8f00c926a820
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="fundamental-concepts-for-content-management-in-system-center-configuration-manager"></a>A System Center Configuration Manager tartalomkezelésének alapvető fogalmai

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager eszközök és az alkalmazások, csomagok, szoftverfrissítések és operációs rendszerek központi telepítésének formájában terjesztett tartalom kezeléséhez beállítások hatékony rendszerét támogatja.  

A központilag telepített tartalmat tárolja helykiszolgálókon és terjesztési pont helyrendszer-kiszolgálóján. Ez a tartalom is igényelnek nagy mennyiségű hálózati sávszélesség, ha azt helyek közötti adatátvitel. Hatékony tervezéséhez és tartalomkezelési infrastruktúra használatára, azt javasoljuk, hogy a rendelkezésre álló lehetőségeket és konfiguráció megismeréséhez, és annak megfontolása, hogyan használhatja ezeket a legjobb térkihasználás érdekében a hálózati környezethez és a tartalomterjesztései igényekhez.  

> [!TIP]    
> További tudnivalók a tartalomterjesztési folyamatot, és az általános tartalom terjesztése probléma diagnosztizálásának és megoldásának talál segítséget. Lásd: [ismertetése és hibaelhárítása a Microsoft Configuration Manager terjesztési tartalom](https://support.microsoft.com/help/4000401/content-distribution-in-mcm) a support.microsoft.com címen.

Az alábbiakban a tartalomkezeléssel kapcsolatos alapfogalmakat. Ha egy fogalom megértéséhez további vagy összetett információkra van szüksége, használja az ezekre mutató hivatkozásokat.

## <a name="accounts-used-for-content-management"></a>Tartalomkezeléshez használt fiókok  
 Tartalomkezeléshez a következő fiókok használhatók:  

-   **Hálózatelérési fiók**: Ügyfelek használják a terjesztési pont csatlakozhat, és hozzáférhetnek a tartalomhoz. Alapértelmezés szerint a számítógépfiók próbált először.  

     Ez a fiók is beszerzése a tartalom egy távoli erdőben lévő forrásként szolgáló terjesztési pontról lekéréses terjesztési pontok használják.  

-   **Csomag-hozzáférési fiók**: Alapértelmezés szerint a Configuration Manager a tartalmat egy terjesztési ponton általános hozzáférési fiókok felhasználók és rendszergazdák számára hozzáférést biztosít. Azonban a hozzáférés korlátozásához beállíthat további engedélyeket.   

-   **Csoportos kapcsolat fiókja**: Az operációs rendszer központi telepítésére használatos.  

Ezek a fiókok kapcsolatos további információkért lásd: [tartalom eléréséhez fiókok kezelése](../../../core/plan-design/hierarchy/manage-accounts-to-access-content.md).

## <a name="bandwidth-throttling-and-scheduling"></a>Sávszélesség-szabályozás és ütemezés  
 Mind a szabályozás, mind az ütemezés olyan beállítások, amelyek segítségével szabályozhatja, mikor történjen a tartalom terjesztése a helykiszolgálóról a terjesztési pontokra. Ez hasonló a helyek közötti fájlalapú replikáció sávszélesség-vezérléséhez, bár nincs vele közvetlen kapcsolatban.  

 További információkért lásd: [a hálózati sávszélesség szabályozása](/sccm/core/plan-design/hierarchy/manage-network-bandwidth).

## <a name="binary-differential-replication"></a>Bináris különbözeti replikáció  
 Előfeltétele a terjesztési pontok, a bináris olyan különbözeti replikációt (BDR), amelyet néha változásreplikálásként is említenek, automatikusan használja a sávszélesség-használat csökkentésére, ha Ön most tartalomhoz terjeszt frissítéseket, amelyek korábban telepített más helyekre vagy távoli terjesztési pontokra.  

 A BDR minimálisra csökkenti a terjesztett tartalom frissítéseinek küldéséhez használt hálózati sávszélességet, mert a tartalomforrásfájlok teljes készlete helyett csak az új vagy módosult tartalmat küldi el, amikor megváltoznak a forrásfájlok.  

 Bináris különbözeti replikáció használata esetén a Configuration Manager azonosítja a forrásfájlok, hogy a korábban terjesztett tartalom beállításainak változásait.  

-   Ha módosítja a tartalmat a fájlokat, a Configuration Manager a tartalomkészlet egy új növekményes verziót hoz létre, és csak a módosult fájlokat replikálja a célhelyekre és a terjesztési pontokon. A fájl abban az esetben ha átnevezi vagy helyezi, vagy ha módosult a fájl tartalmát. Ha például lecserél egy illesztőprogramot egy operációs rendszer központi telepítési csomagjában, amely korábban már el lett küldve több helyre, akkor a rendszer ezekre a célhelyekre csak a módosult illesztőprogramfájlt replikálja.  

-   A Configuration Manager egy tartalomkészletek azt a teljes tartalomkészletet legfeljebb öt növekményes verziót támogatja. Az ötödik frissítést követően a tartalomkészlet következő módosításának hatására a tartalomkészlet új verzióját hozza létre a Configuration Manager. A Configuration Manager majd továbbítja a tartalmat, és ezzel felülírja az előző készletet és annak növekményes verzióit új verziója. Az új tartalomkészlet terjesztése után a forrásfájlok további növekményes változásait ismét a bináris különbözeti replikációval fogja küldeni.  


A BDR a hierarchia minden szülő- és gyermekhelye között támogatott. Egy helyen belül a BDR a helykiszolgáló és a normál terjesztési pontjai között támogatott. Azonban a lekéréses terjesztési pontok és a felhő alapú terjesztési pontok nem támogatja a bináris különbözeti replikációt a tartalom átviteléhez. A lekéréses terjesztési pontok támogatják a fájlszintű eltérések, új fájlok, de nem a fájlon belüli blokkok átvitele.

Az alkalmazások mindig a bináris különbözeti replikációt használják. A csomagok esetében a bináris különbözeti replikáció választható, de alapértelmezés szerint nincs engedélyezve. Ha bináris különbözeti replikációt kíván használni a csomagokhoz, minden csomagnál engedélyeznie kell ezt a funkciót. Ehhez adja meg a **Bináris különbözeti replikáció engedélyezése** beállítást, amikor új csomagot hoz létre, vagy amikor az **Adatforrás** lapon módosítja a csomag tulajdonságait.  

## <a name="branchcache"></a>BranchCache  
 Egy Windows-technológia, amely lehetővé teszi az ügyfelek, amelyek támogatják a BranchCache szolgáltatást, és letöltöttek egy olyan telepítést, amelyet a BranchCache gyorsítótárhoz, hogy más BranchCache kezelésére képes ügyfelek tartalomforrásként szolgáljanak beállított.  

 Ha például az első BranchCache kezelésére képes ügyfélszámítógép tartalmat kér egy Windows Server 2012 rendszert futtató, és BranchCache-kiszolgálóként konfigurált terjesztési pontról, akkor az ügyfélszámítógép ezt a tartalmat letölti és gyorsítótárazza.  

-   Ügyfélszámítógép elérhetővé teheti a tartalmat az BranchCache szolgáltatást használó ügyfelek ugyanazon az alhálózaton, amelyek szintén gyorsítótárazzák a tartalmat.  

-   Így az azonos alhálózatban lévő további ügyfeleknek nem kell letölteniük a tartalmat a terjesztési pontról, és a tartalom több ügyfélre is terjeszthető a későbbi átvitelek lehetővé tételéhez.  

## <a name="peer-cache"></a>Társ-gyorsítótárazás
1610 verziójával kezdve a társ-gyorsítótárazási ügyfél segítségével felügyelheti a tartalmat a távoli ügyfelek központi telepítését. Társ-gyorsítótárazás a beépített Configuration Manager megoldással, amely lehetővé teszi az ügyfelek számára, hogy közvetlenül a helyi gyorsítótárból más ügyfelekkel tartalmat osszanak.

Miután ügyfélbeállítások, amelyek lehetővé teszik a társ-gyorsítótárazás egy gyűjteményhez, tagjai működhet társ tartalomforrásként más ügyfelek számára az ugyanahhoz a határcsoporthoz.

További információkért lásd: [Configuration Manager-ügyfelek számára társ-gyorsítótárazás](/sccm/core/plan-design/hierarchy/client-peer-cache).


## <a name="windows-pe-peer-cache"></a>Windows PE társ-gyorsítótárazás
A System Center Configuration Manager új operációs rendszer telepítésekor a feladatütemezést futtató számítógépek használható Windows PE társ-gyorsítótárazás a tartalmak való beszerzésére egy terjesztési pontról történő letöltésük helyett egy helyi társtól (társ-gyorsítótárazási forrástól). Így minimálisra csökkenthető a nagykiterjedésű hálózat (WAN) forgalma a helyi terjesztési pont nélküli fiókirodai forgatókönyvek esetén.

További információkért lásd: [Windows PE társ-gyorsítótárazás](../../../osd/get-started/prepare-windows-pe-peer-cache-to-reduce-wan-traffic.md).


## <a name="client-locations"></a>Ügyfelek helyei  
 Az alábbiakban azok a helyek szerepelnek, ahol az ügyfelek hozzáférnek a tartalmakhoz:  

-   **Intranet** (helyszíni):  

    -   Terjesztési pontok használhatnak HTTP vagy HTTPS protokollt.  

    -   Tartalék használja a felhő alapú terjesztési pont csak ha a helyszíni terjesztési pontok nem érhetők el.  

-   **Internet**:  

    -   Terjesztési pontok a HTTPS-forgalom fogadásához szükséges.  

    -   Használható tartalék tartalomhelyként a felhőalapú terjesztési pont.  

-   **Munkacsoport**:  

    -   Terjesztési pontok a HTTPS-forgalom fogadásához szükséges.  

    -   Használható tartalék tartalomhelyként a felhőalapú terjesztési pont.  



## <a name="content-library"></a>Tartalomtár  
 A tartalomtár az Egypéldányos tároló, amely a Configuration Manager a kombinált törzse terjesztett tartalom teljes méretének csökkentésére használ a tartalom.  

- További információ a [tartalomtár](../../../core/plan-design/hierarchy/the-content-library.md).
- Használja a [tartalomtár Lemezkarbantartó eszköz](/sccm/core/plan-design/hierarchy/content-library-cleanup-tool) eltávolítása már nem az alkalmazáshoz kapcsolódó tartalmat.  


## <a name="distribution-points"></a>Terjesztési pontok  
 A Configuration Manager terjesztési pontok használatával tárolja az ügyfélszámítógépeken futtatandó szoftverekhez szükséges fájlokat. Az ügyfelek hozzá kell férniük legalább egy terjesztési pontot, amelyről letölthetik a fájlokat központilag telepített tartalomhoz.  

 Az alapvető (nem speciális) terjesztési pont gyakran a normál terjesztési pont hivatkozunk. A normál terjesztési pontoknak két változata kap külön figyelmet:  

-   **Lekéréses terjesztési pont**: Egy változata egy terjesztési pontot, ahol a terjesztési pont le tudja kérni a tartalmat egy másik terjesztési pontról (egy forrás terjesztési pontról). Ez a folyamat hasonlít hogyan ügyfelek le tartalmat a terjesztési pontokon. A lekéréses terjesztési pontok segíthetnek fordulhat elő, ha a helykiszolgáló közvetlenül a tartalmat az egyes terjesztési pontokra kell terjesztenie, a hálózati sávszélesség szűk keresztmetszetek elkerülése érdekében.  [A lekéréses terjesztési pontok használata a System Center Configuration Managerrel](/sccm/core/plan-design/hierarchy/use-a-pull-distribution-point).

-   **Felhőalapú terjesztési pont**: Telepítve van a Microsoft Azure terjesztési pontok egy változata. [A felhőalapú terjesztési pont használata a System Center Configuration Managerrel](../../../core/plan-design/hierarchy/use-a-cloud-based-distribution-point.md).  


Normál terjesztési pontok támogatják a számos konfigurációkat és funkciókat, például a szabályozás és ütemezés, PXE és csoportos küldés, vagy manuálisan előkészített tartalom.  

-   Használhatja például a vezérlők **ütemezések** vagy **sávszélesség-szabályozás** az átvitel szabályozása érdekében.  

-   Is használhatja más beállításokat, beleértve a **előzetesen beállított tartalom**, és **lekéréses terjesztési pontok**. Ezenkívül használhatja **BranchCache** tartalom központi telepítése során használt hálózati sávszélesség csökkentése érdekében.  

-   A terjesztési pontok támogatják a különböző konfigurációkat, például a  **[PXE](../../../osd/get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_PXEDistributionPoint)**  és  **[csoportos](../../../osd/get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_DPMulticast)**  operációs rendszerek központi telepítéséhez, vagy a konfigurációs lépésekre **mobileszközök**.  

 Felhőalapú és lekéréses terjesztési pontok több ugyanazokat a konfigurációkat támogatják, de minden terjesztésipont-változatnak vonatkozó korlátozások is érvényesek.  

## <a name="distribution-point-groups"></a>A terjesztésipont-csoportok  
 Terjesztésipont-csoportok, amelyek megkönnyíthetik a tartalomterjesztést a terjesztési pontok logikai csoportok.  

 További információkért lásd: [terjesztésipont-csoportok kezelése](../../../core/servers/deploy/configure/install-and-configure-distribution-points.md#bkmk_manage).

## <a name="distribution-point-priority"></a>Terjesztési pontok prioritása  
 A terjesztési pontok prioritási értéke azon alapul, hogy mennyi ideig tartott a korábbi telepítések átvitele az adott terjesztési pontra.  

-   Ez az Configuration Manager átviteli tartalom segíti a rövidebb idő alatt több terjesztési pontra terjesztési ponthoz rendelt önhangolási érték.  

-   A tartalmak terjesztése során egyszerre több terjesztési pontot vagy terjesztési pont csoport, a Configuration Manager küldi el a tartalmat a legmagasabb prioritású terjesztési pontra, azután küldi el egy alacsonyabb prioritású terjesztési pontra.  

-   Ez nem helyettesíti a a csomagok terjesztési prioritását, amelyek továbbra is a döntő tényező a különböző terjesztések átviteli meghatározásakor a sorrendben.  


Például terjeszti egy terjesztési pontra, amely egy alacsony terjesztési prioritású pontra magas terjesztési prioritású tartalmat, ha a magas terjesztési prioritású csomag mindig visz át egy csomagot, amely alacsonyabb terjesztési prioritású előtt. A terjesztési prioritás akkor is érvényben van, ha alacsonyabb terjesztési prioritású csomagokat küld olyan terjesztési pontokra, amelyek magasabb terjesztési prioritással rendelkeznek.

A csomag magas prioritása biztosítja, hogy a Configuration Manager alacsonyabb terjesztési prioritású csomagok elküldése előtt továbbítja az adott tartalmaz a megfelelő terjesztési pontokra.  

> [!NOTE]  
>  A lekéréses terjesztési pontok a prioritás elvét használva állítják sorrendbe a forrásként használt terjesztési pontjaikat.  
>   
>  -   A terjesztési pontra irányuló tartalomátvitel a terjesztési pontok prioritása nem azonos azzal a prioritással, amelyet a lekéréses terjesztési pontok kereséséhez használja a forrásként szolgáló terjesztési pont tartalmat.  
>  -   További információkért lásd: [lekéréses terjesztési pontot használ a System Center Configuration Managerrel](/sccm/core/plan-design/hierarchy/use-a-pull-distribution-point).  


## <a name="fallback"></a>Tartalék  
 Számos dolgot változásai 1610 verziójával kezdve, hogy az ügyfelek található, a tartalma, többek között a következőket tartalék terjesztési pont módon. Használja az Ön által használt verzióhoz a következő információkat:

**1610 és újabb verziók**   
A terjesztési pontról, az aktuális határcsoporthoz társított tartalom nem található ügyfelek visszatérhetnek szomszédos határcsoporthoz társított tartalomforrás-helyek használata. Tartalékként használandó szomszédos határcsoportban kell rendelkeznie a definiált kapcsolatot az ügyfél aktuális határcsoporthoz. Ez a kapcsolat ügyfél, amely nem találja a tartalmat a helyi tartalmazhatnak a szomszédos határcsoport a tartalomforráshoz keresését részeként meg kell felelnie konfigurált időpontot tartalmazza.

Az előnyben részesített terjesztési pontok már nincsenek használatban kapcsolatos alapfogalmakat és beállításainak **engedélyezése a tartalék tartalomhelyekről** már nem érhető el vagy érvényben levő.

További információkért lásd: [határcsoportok](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#boundary-groups).


**1606, 1511-es és az 1602-es verzió**   
Tartalék forráshelyre vonatkozó beállítások használatához kapcsolódó **előnyben részesített terjesztési pontok** és az ügyfelek által használt tartalomforrásának helyekre.

-   Alapértelmezés szerint az ügyfelek csak le a tartalmat egy előnyben részesített terjesztési pontról (egy az ügyfél határcsoportjaihoz társított).  

-   Ha azonban egy különálló terjesztési pont **Az ügyfelek tartalék tartalomhelyként használhatják ezt a helyrendszert** beállítással rendelkezik, ez a terjesztési pont érvényes tartalomforrásként szolgálhat bármely ügyfélnek, amely nem tud valamelyik előnyben részesített terjesztési pontjáról letölteni egy telepítést.  


További információ a különböző tartalomhelyekre és tartalék helyeinek: [tartalom forráshelyei – esetek](../../../core/plan-design/hierarchy/content-source-location-scenarios.md). A határcsoportok kapcsolatos információkért lásd: [1511,1602 és 1606 határcsoportjainak](/sccm/core/servers/deploy/configure/boundary-groups-for-1511-1602-and-1606).

## <a name="network-bandwidth"></a>Hálózati sávszélesség  
 A tartalmak terjesztése során használt hálózati sávszélesség kezeléséhez, használhatja a következő beállításokat:  

-   **Előzetesen beállított tartalom**:  A folyamat egy terjesztési pontra tartalom anélkül, hogy a Configuration Manager terjessze a tartalmat a hálózaton keresztül történő továbbítása.  

-   **Ütemezési és sávszélesség-szabályozási**: Konfigurációkat, amelyekkel szabályozhatja, mikor és hogyan tartalom terjesztése terjesztési pontokra.  

További információkért lásd: [a hálózati sávszélesség szabályozása](/sccm/core/plan-design/hierarchy/manage-network-bandwidth).

## <a name="network-connection-speed-to-content-source"></a>A tartalom forrásának eléréséhez használt hálózati kapcsolat sebessége  
Számos dolgot változásai 1610 verziójával kezdve a módon, hogy az ügyfelek található terjesztési pont, a tartalma, beleértve a hálózati kapcsolat sebességét, a tartalom forrásához. Használja az Ön által használt verzióhoz a következő információkat:

**1610 és újabb verziók**   
Hálózati kapcsolat sebessége, amelyek meghatározzák egy terjesztési pontot **gyors** vagy **lassú** már nincsenek használatban. Ehelyett a rendszer minden határcsoporthoz társított helyrendszer azonos.

További információkért lásd: [határcsoportok](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#boundary-groups).


**1606, 1511-es és az 1602-es verzió**   
 Minden terjesztési pont hálózati kapcsolati sebességét beállíthatja egy határcsoportban:  

-   Ügyfelek használják ezt az értéket, amikor csatlakoznak a terjesztési ponthoz.

-   Alapértelmezés szerint a hálózati kapcsolat sebességének beállítása **gyors**, de az is beállítható **lassú**.  

-   A **hálózati kapcsolat sebessége**, és a központi telepítés konfigurációja határozza meg, ha egy ügyfél letölthet-tartalom a terjesztési pontról Ha az ügyfél egy hozzá társított határcsoportban szerepel  

További információ a különböző tartalomhelyekre és tartalék helyeinek: [tartalom forráshelyei – esetek](../../../core/plan-design/hierarchy/content-source-location-scenarios.md). A határcsoportok kapcsolatos információkért lásd: [1511,1602 és 1606 határcsoportjainak](/sccm/core/servers/deploy/configure/boundary-groups-for-1511-1602-and-1606).

## <a name="on-demand-content-distribution"></a>Igény szerinti tartalomterjesztés  
 Beállíthatja, hogy egyedi lehetősége az igény szerinti tartalomterjesztést alkalmazásokhoz és csomagokhoz (központi telepítésekhez) engedélyezése az igény szerinti tartalomterjesztést az előnyben részesített terjesztési pontokra.  

-   Ez a központi telepítés engedélyezéséhez **tartalmának terjesztése az előnyben részesített terjesztési pontokon a csomag**.  

-   Ha ez a beállítás engedélyezve van a központi telepítés és az ügyfél megkísérel kért tartalmakat, de a tartalom nem áll rendelkezésre az ügyfél előnyben részesített terjesztési pont bármely, a Configuration Manager automatikusan továbbítja az adott tartalmaz az ügyfél előnyben részesített terjesztési pontokra.  

-   Bár ez elindítja a Configuration Manager automatikusan tartalmának terjesztése az előnyben részesített terjesztési pontokra, hogy az ügyfélszámítógépek számára, az ügyfél is beszerezheti a tartalmat más terjesztési pontokról az ügyfél az előnyben részesített terjesztési pontokra kapni a telepítés előtt. Ha ez történik, a tartalom elérhető lesz ezen a terjesztési ponton, amely az adott központi telepítés célja a következő ügyfél általi használatra.  

Ha 1610 vagy újabb verzióját használja, tekintse meg [határcsoportok](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#boundary-groups).
Ha az 1511-es, a 1602-es vagy 1606 verzióját használja, tekintse meg [tartalom forráshelyei – esetek](../../../core/plan-design/hierarchy/content-source-location-scenarios.md) további információ a különböző tartalomhelyekre és tartalék helyeinek.  



## <a name="package-transfer-manager"></a>Package Transfer Manager  
 A Package Transfer Manager a helykiszolgáló-összetevő, amely továbbítja a tartalmat a terjesztési pontokat a többi számítógépen.  

 További információ a [a Package Transfer Manager](../../../core/plan-design/hierarchy/package-transfer-manager.md).  

## <a name="preferred-distribution-point"></a>Előnyben részesített terjesztési pont  
 Előnyben részesített terjesztési ponton minden olyan ügyfél aktuális határcsoportjaival társított terjesztési pontok tartalmazza.  

 Lehetősége van egy vagy több határcsoporthoz hozzárendelni minden egyes terjesztési pontot:  

-   A hozzárendelés révén az ügyfél azonosíthatja azokat a terjesztési pontok, amelyből tartalmat tölthet le.  
-   Alapértelmezés szerint az ügyfelek csak letölthető tartalom előnyben részesített terjesztési ponton.  


További információ:
 - Ha 1610 vagy újabb verzióját használja, tekintse meg [határcsoportok](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#boundary-groups).
 - Ha az 1511-es, a 1602-es vagy 1606 verzióját használja, tekintse meg [tartalom forráshelyei – esetek](../../../core/plan-design/hierarchy/content-source-location-scenarios.md).

## <a name="prestage-content"></a>Tartalom előkészítése  
 Előzetes beállításának a tartalom a tartalom terjesztési pontra anélkül, hogy a Configuration Manager keresztül terjeszteni a tartalmat a hálózaton keresztül történő továbbítása.  

 További információkért lásd: [a hálózati sávszélesség szabályozása](/sccm/core/plan-design/hierarchy/manage-network-bandwidth).

