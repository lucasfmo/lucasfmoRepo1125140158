---
title: "Méret és a skála |} Microsoft Docs"
description: "Helyrendszer-szerepkörök és a helyek, amelyeket kezelni kell a System Center Configuration Manager környezetben támogatja az eszközök számának meghatározásához."
ms.custom: na
ms.date: 12/30/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c5a42100-2f60-4952-b495-918025ea6559
caps.latest.revision: 4
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f9c43e26758d5171a6ef56e827b4b054ebc8a5e5
ms.openlocfilehash: c7ad33339e65e6e00e88f98d6e13baceb98dae77
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="size-and-scale-numbers-for-system-center-configuration-manager"></a>Méret és a skálázási számok a System Center Configuration Managerhez

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*



Minden System Center Configuration Manager telepítési lesz a helyek, a helyrendszer-szerepköröket és az azt által támogatott eszközök maximális számát. Ezeket a számokat eltérők lehetnek, attól függően, hogy a hierarchia struktúra (milyen típusának és számának használt helyek) és a helyrendszerszerepkörök, amelyek központi telepítése.  A következő területeken információk segítségére lehetnek a helyrendszer-szerepkörök és a helyek, amelyek lesz szüksége a környezet kezelése várt eszközök támogatását számának meghatározása.

Olvassa el ebben a témakörben együtt található a következő cikkekben talál információkat:
-   [Ajánlott hardver](../../../core/plan-design/configs/recommended-hardware.md)
-   [Támogatott operációs rendszerek a helyrendszer-kiszolgálókhoz](../../../core/plan-design/configs/supported-operating-systems-for-site-system-servers.md)  
-   [Az ügyfelek és eszközök támogatott operációs rendszerek](../../../core/plan-design/configs/supported-operating-systems-for-clients-and-devices.md)
-   [Hely és hely rendszer Előfeltételek](../../../core/plan-design/configs/site-and-site-system-prerequisites.md)


A következő támogatási számok alapján ajánlott a hardvert használja a Configuration Manager és az alapértelmezett beállításokat az összes rendelkezésre álló Configuration Manager-szolgáltatásokat. Ha nem a javasolt hardver, vagy szigorúbb egyéni beállítások (például futó hardver és szoftver-nyilvántartási gyakrabban az alapértelmezett beállításokat, a hét naponta), a helyrendszerek teljesítményének romlásához vezethet, és előfordulhat, hogy nem felel meg az itt megadott szintű támogatást.

##  <a name="bkmk_SiteSystemScale"></a>Helytípusok  
 **Központi adminisztrációs hely:**  

-   A központi adminisztrációs hely legfeljebb 25 gyermek elsődleges helyek támogatja.  

**Elsődleges hely:**  

-   Minden elsődleges hely legfeljebb 250 másodlagos helyet támogat.  

-   Az elsődleges helyenként megengedett másodlagos helyek száma a folyamatosan csatlakoztatott és megbízható nagy kiterjedésű hálózati (WAN) kapcsolatok alapul. Kevesebb mint 500 ügyféllel rendelkező helyek fontolja meg a terjesztési pont egy másodlagos hely helyett.  

 További információ az ügyfelek és az elsődleges hely által támogatott eszközök száma: [helyek és hierarchiák ügyfelek száma](#bkmk_clientnumbers) ebben a témakörben.  

**Másodlagos hely:**  

-   A másodlagos helyek nem támogatják a gyermek helyeken.  

-   A központi adminisztrációs hely legfeljebb 25 gyermek elsődleges helyek támogatja.  

**Az Alkalmazáskatalógus weboldal-elérési pontja:**  

-   Az Alkalmazáskatalógus weboldal-elérési pontja az elsődleges helyeken több példánya is telepíthető.  

    > [!TIP]  
    >  Ajánlott eljárásként telepíthető az Alkalmazáskatalógus weboldal-elérési pontja és az Alkalmazáskatalógus webszolgáltatási pontja együtt az adott hely rendszer, ha az intraneten az ügyfelek biztosítanak szolgáltatást.  

    -   Tervezze meg a jobb teljesítmény érdekében példányonként legfeljebb 50 000 ügyfél támogatásához.  

    -   A helyrendszer-szerepkör minden példánya támogatja a hierarchia által támogatott ügyfelek maximális számát.  

## <a name="bkmk_roles"></a>Helyrendszer-szerepkörök    

**Az Alkalmazáskatalógus webszolgáltatási pontja:**  

-   Az Alkalmazáskatalógus webszolgáltatási pontja az elsődleges helyeken több példánya is telepíthető.  

    > [!TIP]  
    >  Ajánlott eljárásként telepíthető az Alkalmazáskatalógus weboldal-elérési pontja és az Alkalmazáskatalógus webszolgáltatási pontja együtt az adott hely rendszer, ha az intraneten az ügyfelek biztosítanak szolgáltatást.  

    -   Tervezze meg a jobb teljesítmény érdekében példányonként legfeljebb 50 000 ügyfél támogatásához.  

    -   A helyrendszer-szerepkör minden példánya támogatja a hierarchia által támogatott ügyfelek maximális számát.  

**Terjesztési pont:**  

-   Terjesztési pontok száma helyenként:  

    -   Minden elsődleges és másodlagos hely legfeljebb 250 terjesztési pontot támogat.  

    -   Minden elsődleges és másodlagos hely legfeljebb 2000 újabb terjesztési pontokat a lekéréses terjesztési pontként konfigurált támogat. **Például**, egyetlen elsődleges hely támogathat 2250 terjesztési pontot, ha ezen terjesztési pontok közül 2000 lekéréses terjesztési pontként van konfigurálva.  

    -   Minden terjesztési pont legfeljebb 4 000 ügyféltől származó kapcsolatot támogat.  

    -   A lekéréses terjesztési pontok ügyfélként működnek, amikor tartalmakat érnek el egy forrás terjesztési pontról.  

-   Minden elsődleges hely összesen legfeljebb 5 000 terjesztési pontot támogat. Ebbe beletartozik az elsődleges hely összes terjesztési pont és az elsődleges hely másodlagos gyermekhelyeihez tartozó összes terjesztési pont van.  

-   Minden terjesztési pont összesen legfeljebb 10 000 csomagot és alkalmazást támogat.  

> [!WARNING]  
>  Egy terjesztési pont által támogatható ügyfelek tényleges száma a hálózat sebességétől és a terjesztési pont számítógép hardverkonfigurációjától függ.  
>   
>  A lekéréses terjesztési pontok egy forrás terjesztési pont által támogatott hasonlóan a hálózat sebességétől és a forrás terjesztési pont számítógép hardverkonfigurációjától függ. Azonban ez a szám is hatással van a telepítése után tartalom mennyiségét. Ennek oka, hogy az ügyfelekkel ellentétben, amelyek általában hozzáférhetnek a tartalomhoz különböző időpontokban, a telepítés során, az összes lekéréses terjesztési pontok tartalomkérelem egyszerre –, és az összes elérhető tartalom, nem csak az adott vonatkoznak rájuk, mint egy ügyfél tartalmat. Ha túl sok feldolgozási terhelés a forrásként szolgáló terjesztési pont, lehet nem várt késedelmeket a környezetben lévő betervezett terjesztési pontokon a tartalom terjesztése.  


**Tartalék állapotkezelő pont:**  

-   Minden tartalék állapotkezelő pont legfeljebb 100 000 ügyfél támogatására alkalmas.  

**Felügyeleti pont:**  

-   Minden elsődleges hely legfeljebb 15 felügyeleti pontot támogat.  

    > [!TIP]  
    >  Ne telepítse a felügyeleti pontok kiszolgálókat, amelyek lassú kapcsolaton keresztül csatlakoznak az elsődleges helykiszolgálón vagy a Helyadatbázis-kiszolgáló szolgáltatást.  

-   Minden másodlagos hely egyetlen felügyeleti pont, amelyet telepíteni kell a másodlagos helykiszolgáló támogat.  

 További információ az ügyfelek és a felügyeleti pont által támogatott eszközök száma: a [felügyeleti pontok](#bkmk_mp) szakaszában talál.  

**Szoftverfrissítési pont:**  

-   A helykiszolgálón telepített szoftverfrissítési pont akár 25 000 ügyfél támogatására alkalmas.  

-   A helykiszolgáló távoli szoftverfrissítési pontot is legfeljebb 150 000 ügyfél támogatására, ha a távoli számítógép megfelel a Windows Server Update Services (WSUS) ilyen számú ügyfél támogatására.  

-   Alapértelmezés szerint a Configuration Manager nem támogatja a szoftverfrissítési pontok konfigurálása, a hálózati terheléselosztási (NLB) fürt. A Configuration Manager SDK használatával azonban legfeljebb négy szoftverfrissítési pont konfigurálása NLB-fürt.  

##  <a name="bkmk_clientnumbers"></a>Helyek és hierarchiák ügyfelek száma  
 A következő információ használatával határozhatja meg, hány ügyfelet és milyen típusú ügyfeleket képes támogatni, egy adott helyre vagy hierarchiába.  

###  <a name="bkmk_cas"></a>Központi adminisztrációs hellyel rendelkező hierarchiára  
A központi adminisztrációs hely támogatja az olyan eszközök teljes számát, amely tartalmazza a következő három csoport a felsorolt eszközök száma legfeljebb:  

-   700 000 asztali számítógép (Windows, Linux és UNIX rendszerű számítógépek)  

-   25 000 Mac vagy Windows CE 7.0 rendszerű eszközök  

-   A következők egyike, attól függően, hogy a központi telepítés hogyan támogatja a mobileszköz-kezelés (MDM):  

    -   100 000 helyszíni MDM segítségével felügyelt eszközökön  

    -   300 000 felhőalapú eszköz  

 Például egy hierarchiában, támogathatja 700 000 asztali számítógép, legfeljebb 25 000 Mac és a Windows CE 7.0-ban, és akár 300 000 felhőalapú eszköz Microsoft Intune integrálásakor – azaz összesen 1 025 000 eszköz. Támogatja a helyszíni MDM által felügyelt eszközökre, a teljes hierarchia esetén 825,000 eszközök.  

> [!IMPORTANT]  
>  Egy hierarchiában, ahol a központi adminisztrációs hely az SQL Server Standard verzióját használja a hierarchia legfeljebb 50 000 asztali számítógép és eszköz. Az önálló elsődleges helyen használt SQL Server kiadása nem korlátozza, hogy a hely tud hány ügyfelet támogatni.  


###  <a name="bkmk_chipri"></a>Gyermek elsődleges hely  
Összes alárendelt elsődleges hely a hierarchia központi adminisztrációs hellyel rendelkező támogatja a következőket:  

-   150 000 teljes ügyfelek és eszközök, amelyek nem csak egy csoportra vagy típusra vonatkozó, mindaddig, amíg támogatás nem haladhatja meg a számát, a hierarchia által támogatott.  

Például egy elsődleges helyet, amely támogatja a 25 000 (mivel ez a hierarchiára vonatkozó korlát) Mac és a Windows CE 7.0 rendszerű számítógépeken is majd egy további 125,000 asztali számítógépek támogatásához. Ekkor az alárendelt elsődleges hely által támogatott maximális legfeljebb 150 000 legfeljebb támogatott eszközök teljes száma.

###  <a name="bkmk_pri"></a>Önálló elsődleges hely  
Önálló elsődleges hely a következő számú eszközöket támogatja:  

-   175 000 teljes ügyfelek és eszközök, a következő korlátozásokkal:  

    -   150 000 asztali számítógép (Windows, Linux és UNIX rendszerű számítógépek)  

    -   25 000 Mac vagy Windows CE 7.0 rendszerű eszközök

    -   A következők egyike, attól függően, hogy a központi telepítés hogyan támogatja a mobileszköz-kezelés:  

        -   50 000 helyszíni MDM segítségével felügyelt eszközökön  

        -   150 000 felhőalapú eszköz  

Például egy önálló elsődleges helyet, amely támogatja a 150 000 asztali számítógép és 10 000 Mac vagy Windows CE 7.0 csak egy további 15 000 eszközt támogathat. Az eszközöket lehet felhőalapú vagy kezelt helyszíni MDM segítségével  

###  <a name="bkmk_sec"></a>A másodlagos helyek  
A másodlagos helyek támogatják a következőket:  

-   15 000 asztali számítógép (Windows, Linux és UNIX rendszerű számítógépek)  

###  <a name="bkmk_mp"></a>Felügyeleti pontok  
Minden olyan felügyeleti pont támogathatja a következő eszközök száma:  

-   25 000 teljes ügyfelek és eszközök, a következő korlátozásokkal:  

    -   25 000 asztali számítógép (Windows, Linux és UNIX rendszerű számítógépek)  

    -   A következők egyikére (mindkettő nem):  

        -   10 000 helyszíni MDM segítségével felügyelt eszközökre  

        -   10 000 Mac és a Windows CE 7.0 rendszerű ügyfelek futtató eszközök

