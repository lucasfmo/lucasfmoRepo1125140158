---
title: "Használja a határok és határcsoportok |} Microsoft Docs"
description: "Határok és határcsoportok segítségével határozza meg a hálózati helyek és a felügyelt eszközökön elérhető helyrendszerek."
ms.custom: na
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 54aa20d5-791e-4416-9db4-5aaea472c0b7
caps.latest.revision: 10
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dda2f4c01078fbbd174cbcb30357554c24f6abeb
ms.openlocfilehash: 0fea1dece0768a2b7bcd3fcedc2288ea2d52e73d
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="define-site-boundaries-and-boundary-groups-for-system-center-configuration-manager"></a>Helyhatárok és határcsoportok megadása a System Center Configuration Managerhez

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Határok a System Center Configuration Manager határozza meg a kezelni kívánt eszközöket tartalmazó intranetes hálózati helyeket. A határcsoportok a határok beállított logikai csoportjai.

 Egy hierarchia tetszőleges számú határcsoportot tartalmazhat, az egyes csoportok pedig az alábbi határtípusok tetszőleges kombinációjából állhatnak:  

-   IP-alhálózat,  
-   Active Directory-webhely neve  
-   IPv6-előtag  
-   IP-címtartománnyal  

Az intraneten az ügyfelek felmérhetik aktuális hálózati helyüket, és ezt az információt felhasználva azonosíthatják azokat a határcsoportokat, amelyekhez tartoznak.  

 Az ügyfelek a határcsoportokat a következőkre használhatják:  
-   **Hozzárendelt hely keresése:** Határok lehetővé teszik az ügyfelek számára, hogy egy elsődleges helyet találjanak (automatikus helyhozzárendelés) ügyfél-hozzárendelés.  
-   **Egyes helyrendszer-szerepkörök is található:** Ha egy határcsoporthoz hozzárendel bizonyos helyrendszer-szerepkörök, a határcsoport az ügyfelek helyrendszerek listáját, hogy számára biztosít Tartalomkeresés során és előnyben részesített felügyeleti pontokat.  

Az intraneten található vagy csak internetes használatra konfigurált ügyfelek nem használnak határadatokat. Az ilyen ügyfelek nem tudják használni az automatikus helyhozzárendelést, és bármikor letölthetnek tartalmakat a hozzájuk rendelt hely bármely olyan terjesztési pontjáról, amely engedélyezi az internetről érkező ügyfélkapcsolatokat.  

**Első lépések:**
- Első, [határozza meg a hálózati helyeket határokként](/sccm/core/servers/deploy/configure/boundaries).
- Ezután [határcsoportok konfigurálása](/sccm/core/servers/deploy/configure/boundary-groups) rendelni az ügyfelek ezeket a határokat a helyrendszer-kiszolgálókon is.



##  <a name="BKMK_BoundaryBestPractices"></a>Határok és határcsoportok ajánlott eljárásai  

-   **A legkevesebb határokat, amelyek megfelelnek az igényeinek vegyesen használni:**  
   A múltban a néhány határtípusok használatát keresztül mások ajánlott. A teljesítmény javítása érdekében azt most már használhatja bármelyik határtípusként vagy a munkát a környezetében, amelyekkel Ön úgy dönt, típusok használata a lehető legkevesebb határok ajánlott változások egyszerűsítse a felügyeleti feladatok is.      

-   **Kerülje az átfedésben lévő határok használatát automatikus helyhozzárendelés esetén:**  
     Bár minden határcsoport egyaránt támogatja a hely-hozzárendelési konfigurációkat és a tartalomhelyek konfigurációit, ajánlott létrehozni olyan határcsoportokat, amelyeket csak helyhozzárendeléshez használ. Ez azt jelenti, hogy gondoskodnia kell arról, hogy az egy határcsoportban szereplő határok ne legyenek egy olyan másik határcsoport tagjai, amelyhez eltérő helyhozzárendelés tartozik. Ennek oka a következő:  

    -   Egy határ több határcsoportba is tartozhat.  

    -   Az egyes határcsoportok eltérő elsődleges helyekkel társíthatók a helyhozzárendeléskor.  

    -   Ha egy ügyfél olyan határon belül található, amely két különböző határcsoport tagja, és azok helyhozzárendelése eltérő, az ügyfél véletlenszerűen fogja kiválasztani, hogy melyik helyhez csatlakozik. Ilyenkor előfordulhat, hogy az ügyfél nem a tervezett helyhez csatlakozik.  Az ilyen konfigurációt átfedésben lévő határoknak nevezik.  

     Az átfedésben lévő határok konfigurálása a tartalomhelyek esetében nem jelent problémát, mi több, gyakran kívánatosnak számít, hiszen az ügyfeleknek további használható erőforrásokat és tartalomhelyeket biztosít.  

