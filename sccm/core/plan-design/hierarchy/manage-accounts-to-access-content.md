---
title: "A System Center Configuration Managerben tartalom eléréséhez fiókok |} Microsoft Docs"
description: "További tudnivalók a System Center Configuration Manager tartalom elérhetik az ügyfelek fiókokat."
ms.custom: na
ms.date: 2/6/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a7df9d0f-fbde-47eb-97e7-3d29536424fa
caps.latest.revision: 4
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: e592a732259147ee71d404a68982c28e5138e243
ms.openlocfilehash: 0e982d08d54af39b13f553fc531a200f921e94a6
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="manage-accounts-to-access-content-in-system-center-configuration-manager"></a>A System Center Configuration Managerben tartalom eléréséhez fiókok kezelése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Managerben tartalom központi telepítése előtt fontolja meg, hogyan ügyfelek érik el ezt a tartalmat a terjesztési pontokról. Ez a cikk ismerteti az erre a célra használja a következő fiókokat:

-   **Hálózatelérési fiók**. Ügyfelek használják a terjesztési pont csatlakozhat, és hozzáférhetnek a tartalomhoz. Alapértelmezés szerint az ügyfelek először a számítógépfiók próbálja meg.

     Ez a fiók is beszerzése a tartalom egy távoli erdőben lévő forrásként szolgáló terjesztési pontról lekéréses terjesztési pontok használják.  

-   **Csomag-hozzáférési fiók**. Alapértelmezés szerint a Configuration Manager hozzáférést biztosít a tartalmat egy terjesztési ponton nevű beépített fiókok **felhasználók** és **rendszergazdák**. Beállíthat további engedélyeket korlátozhatja a hozzáférést.  

-   **Csoportos kapcsolat fiókja**. Az operációs rendszer központi telepítésére használatos.  

##  <a name="bkmk_NAA"></a>Hálózati hozzáférési fiók  
 Ügyfélszámítógépek számára a hálózati elérésre szolgáló fiókot használja, ha a saját helyi számítógépfiókjuk nem használhatják a terjesztési pontokon a tartalom eléréséhez. Ez vonatkozik a munkacsoport-ügyfelekre és a nem megbízható tartományokban levő számítógépekre is. Ez a fiók az operációs rendszer telepítése során is használható, ha az operációs rendszert telepítő számítógépnek még nincs számítógépfiókja a tartományban.  

-   Az ügyfelek csak a hálózati elérésre szolgáló fiókot erőforrások eléréséhez használják a hálózaton.  

-   Minden elsődleges helyen beállíthat több fiók olyan hálózatelérési fiókot használni.  

-   Az ügyfelek először próbálja elérni a tartalmat a terjesztési pont használatával a *számítógépnév*$ fiókot. Ha ez a fiók nem sikerül, az ügyfelek próbálja használják a hálózatelérési fiókot. Az ügyfelek továbbra is használatára történt kísérlet a hálózatelérési fiókot, akkor is, ha korábban sikertelen volt.  

### <a name="permissions"></a>Engedélyek
Ezt a fiókot, amelyhez az ügyfél a tartalom szoftverének eléréshez szükségesek a minimálisan szükséges engedélyeket adja.  

-   A fióknak rendelkeznie kell a **a számítógép elérése a hálózatról** közvetlenül a terjesztési ponton.  

-   Bármely tartomány, amely hozzáférést biztosít a szükséges erőforrások hozza létre a fiókot. A hálózatelérési fióknak tartalmaznia kell a tartomány nevét. Átmenő hitelesítés nem támogatott ehhez a fiókhoz. Ha több tartományban is vannak terjesztési pontok, akkor egy megbízható tartományban hozza létre a fiókot.  

> [!TIP]  
>  A fiók zárolásának elkerülése érdekében ne módosítsa a meglévő hálózatelérési fiók jelszavát. Ehelyett hozzon létre egy új fiókot, és állítsa be az új fiókot a Configuration Manager alkalmazásban. Elegendő idő elteltével az összes ügyfél megkapta az új fiók adatait, távolítsa el a régi fiókot a megosztott hálózati mappákból, és törölje ezt a fiókot.  

> [!IMPORTANT]  
>  Nem jogot adni ehhez a fiókhoz interaktív bejelentkezéshez.  
>   
>  Ne engedélyezze a fióknak, hogy számítógépeket csatlakoztasson a tartományhoz. Ha egy feladatütemezés végrehajtása közben tartományhoz kell csatlakoztatnia a számítógépeket, használja a Feladatütemezés-szerkesztő tartományhoz való csatlakozásra szolgáló fiókját.  

### <a name="to-configure-the-network-access-account"></a>A hálózatelérési fiók konfigurálása  

1.  Kattintson a Configuration Manager konzol **felügyeleti** >   **Helykonfiguráció** >  **helyek**, majd válassza ki a helyet.  

2.  Az a **beállítások** csoportjában válassza **Helyösszetevők** > **szoftverterjesztés**.  

3.  Válassza ki a **hálózatelérési fiók** fülre. Állítson be egy vagy több fiókot, és válassza a **OK**.  

##  <a name="bkmk_Paa"></a>Csomag-hozzáférési fiókok  
 Csomag-hozzáférési fiókok lehetővé teszik az NTFS fájlrendszerbeli engedélyeket úgy adja meg a felhasználók és felhasználói csoportokat, amelyeknek férhetnek hozzá a terjesztési pontokon a csomag tartalmát. Alapértelmezés szerint a Configuration Manager hozzáférést csak az általános **felhasználók** és **rendszergazdák** fiókok. Akkor is hozzáférést az ügyfélszámítógépek számára, azonban további Windows-fiókokat vagy csoportokat. Mobileszközök ne használjon a csomag-hozzáférési fiókokat, mert ezek az eszközök mindig az névtelenül csomag tartalmának lekéréséhez.  

 Alapértelmezés szerint amikor a Configuration Manager másolja a tartalomfájlokat egy csomag egy terjesztési ponton, alapértelmezésben **olvasási** hozzáférést ad a helyi **felhasználók** csoport és **teljes hozzáférés** a helyi **rendszergazdák** csoport. A tényleges engedélyek, amelyek szükségesek a csomagtól függ. Ha munkacsoportokban vagy nem megbízható erdőkben levő ügyfelekkel rendelkezik, ezek az ügyfelek hálózatelérési fiókon keresztül férnek hozzá a csomagtartalomhoz. Győződjön meg arról, hogy rendelkezik-e a hálózati elérésre szolgáló fiókot a csomag engedélyekkel a megadott csomagelérési fiókok segítségével.  

 Olyan tartomány fiókjait használja, amely hozzáfér a terjesztési pontokhoz. Ha azt követően hozza létre vagy módosítja a fiókot, hogy a csomag létrejött, újra kell terjesztenie a csomagot. A csomag frissítése nem módosítja az NTFS fájlrendszer engedélyeit a csomagra.  

 Nincs hozzáadása a hálózatelérési fiókot csomag-hozzáférési fiókként, mert tagsága a **felhasználók** csoport automatikusan felveszi. Az ügyfelek attól még hozzáférhetnek a csomaghoz, hogy a csomag-hozzáférési fiók csak a hálózatelérési fiókra van korlátozva.  

### <a name="to-manage-access-accounts"></a>Hozzáférési fiókokat szeretne kezelni  

1.  Kattintson a Configuration Manager konzol **szoftverkönyvtár**.  

2.  Az a **szoftverkönyvtár** munkaterületen határozza meg a tartalomtípushoz, amelyhez hozzáférési fiókokat szeretne kezelni kívánt, és kövesse az itt ismertetett lépéseket:  

    -   **Alkalmazások**: Bontsa ki a **Alkalmazáskezelés**, válassza a **alkalmazások**, majd válassza ki az alkalmazásokat, amelyhez hozzáférési fiókokat szeretne kezelni.  

    -   **Csomagok**: Bontsa ki a **Alkalmazáskezelés**, válassza a **csomagok**, majd válassza ki a csomagokat, amelyhez hozzáférési fiókokat szeretne kezelni.  

    -   **Központi telepítési csomagok**: Bontsa ki a **szoftverfrissítések**, válassza a **központi telepítési csomagok**, majd válassza ki a központi telepítési csomagokat, amelyhez hozzáférési fiókokat szeretne kezelni.  

    -   **Illesztőprogram-csomagok**: Bontsa ki a **operációs rendszerek**, válassza a **illesztőprogram-csomagok**, majd válassza ki az illesztőprogram-csomagokat, amelyhez hozzáférési fiókokat szeretne kezelni.  

    -   **Operációsrendszer-lemezképek**: Bontsa ki a **operációs rendszerek**, válassza a **operációsrendszer-lemezképek**, majd válassza ki az operációsrendszer-lemezképek, amelyhez hozzáférési fiókokat szeretne kezelni.  

    -   **Operációs rendszerek telepítőcsomagjai**: Bontsa ki a **operációs rendszerek**, válassza a **operációs rendszerek telepítőcsomagjai**, majd válassza ki az operációs rendszer telepítőcsomagokat, amelyek esetében hozzáférési fiókokat szeretne kezelni.  

    -   **Rendszerindító lemezképek**: Bontsa ki a **operációs rendszerek**, válassza a **rendszerindító lemezképek**, majd válassza ki a rendszerindító lemezképeket, amelyhez hozzáférési fiókokat szeretne kezelni.  

3.  Kattintson a jobb gombbal a kijelölt objektum, és válassza a **hozzáférési fiókok kezelése**.  

4.  Az a **fiók hozzáadása** párbeszédpanelen adja meg a fióktípust, amelynek a tartalmakhoz való hozzáférést kapnak, és adja meg a fiókhoz rendelt hozzáférési jogosultságokat.  

    > [!NOTE]  
    >  Ha hozzáadta a fiók felhasználói nevét, és a Configuration Manager talál egy helyi felhasználói fiók és a tartományi felhasználói fiók ezzel a névvel, a Configuration Manager a tartományi felhasználói fiók hozzáférési jogait állítja be.  

##  <a name="bkmk_multi"></a>Csoportos kapcsolat fiókja  
 A csoportos kapcsolat fiókja adatok olvasása a Helyadatbázis csoportos küldésre beállított terjesztési pontokat használják.  

-   Meg kell adnia egy fiókot használja, ha a csoportos küldésre beállított Configuration Manager Helyadatbázis-kapcsolatot.  

-   Alapértelmezés szerint a terjesztési pont számítógépfiókját használja, de beállíthat egy felhasználói fiók helyett.  

-   Ha a helyadatbázis egy nem megbízható erdőben van, akkor muszáj megadni egy felhasználói fiókot.  

-   A fióknak rendelkeznie kell **olvasási** engedéllyel kell rendelkeznie a helykiszolgáló adatbázishoz.  

Ha például az adatközpontnak szegélyhálózata van egy másik erdőben, mint ahol a helykiszolgáló és a helyadatbázis található, akkor ezzel a fiókkal lehet kiolvasni a csoportos küldés adatait a helyadatbázisból.

Ha létrehozza ezt a fiókot, hozzon létre egy alacsony jogosultságú, helyi fiók a Microsoft SQL Server rendszert futtató számítógépen.  

> [!IMPORTANT]  
>  Nem jogot adni ehhez a fiókhoz interaktív bejelentkezéshez.  

