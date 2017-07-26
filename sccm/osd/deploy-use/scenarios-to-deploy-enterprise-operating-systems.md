---
title: "A vállalati operációs rendszerek központi telepítésének forgatókönyvei |} Microsoft Docs"
description: "További tudnivalók több forgatókönyv szerint, központi telepítéséhez a vállalati operációs rendszerek a System Center Configuration Managerrel."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f74fdb86-c7c2-447f-91f6-b42df6370d7f
caps.latest.revision: 11
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: b1bea8b1b890f7c96a432835d28ad840a9b6873d
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="scenarios-to-deploy-enterprise-operating-systems-with-system-center-configuration-manager"></a>A vállalati operációs rendszerek System Center Configuration Managerrel való központi telepítésének módszerei

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Operációs rendszer következő telepítési helyzetekben érhetők el a System Center Configuration Managerben:  

-   [A Windows frissítése a legújabb verzióra](upgrade-windows-to-the-latest-version.md): Ez a forgatókönyv frissíti az operációs rendszer Windows 7, Windows 8, Windows 8.1 vagy Windows 10 jelenleg futtató számítógépeken. A frissítési folyamat megőrzi az alkalmazásokat, a beállításokat és a felhasználói adatokat a számítógépen. Ez a módszer nem függ külső tényezőktől, például a Windows ADK-tól, emellett gyorsabb és rugalmasabb, mint az operációs rendszerek központi telepítésére szolgáló hagyományos eljárások.  

-   [A Windows új verziójára meglévő számítógép frissítése](refresh-an-existing-computer-with-a-new-version-of-windows.md): A módszer particionálja és formázza az adathordozót (Törlés) egy meglévő számítógép és az új operációs rendszert telepít a számítógépre. Az operációs rendszer telepítése után áttelepítheti a beállításokat és a felhasználói adatokat.  

-   [A Windows új verziójának telepítése egy új (operációs rendszer nélküli) számítógépre](install-new-windows-version-new-computer-bare-metal.md): Ebben a forgatókönyvben az operációs rendszer telepítése egy új számítógépre. Ez az operációs rendszer friss telepítését jelenti, és nem terjed ki a beállítások vagy felhasználói adatok áttelepítésére.  

-   [Meglévő számítógép cseréje és a beállítások átvitele](replace-an-existing-computer-and-transfer-settings.md): Ebben a forgatókönyvben az operációs rendszer telepítése egy új számítógépre. Szükség esetén a beállításokat és felhasználói adatokat is áttelepítheti a régi számítógépről az újra.  

## <a name="things-to-consider-before-you-deploy-operating-system-images"></a>Operációsrendszer-lemezképek központi telepítése előtt megfontolandó szempontok  
 Bizonyos tényezőket érdemes számításba venni az operációs rendszer telepítésének megkezdése előtt.  

### <a name="operating-system-image-size"></a>Az operációsrendszer-lemezkép mérete  
 Az operációsrendszer-lemezkép mérete igen tekintélyes lehet. A Windows 7 rendszer lemezképmérete például 3 gigabájt (GB) vagy több. A lemezkép mérete és azon számítógépek száma, amelyekre az operációs rendszer egy időben települ központilag, hatással van a hálózati teljesítményre és a sávszélességre. A hálózati teljesítmény ellenőrzésével biztosíthatja, hogy jobban fel tudja mérni a lemezkép központi telepítésének esetleges hatását és a központi telepítés befejezéséhez szükséges időt. Hálózati teljesítményt befolyásoló a Configuration Manager tevékenységei közé tartoznak, a lemezkép terjesztési pontra, a lemezkép egyik helyről egy másikra, és a lemezkép letöltése a Configuration Manager-ügyfél.  

 Arra is ügyeljen, hogy elegendő tárolófelület álljon rendelkezésre az operációsrendszer-lemezképeket tároló terjesztési pontokon.  

### <a name="client-cache-size"></a>Ügyfélgyorsítótár mérete  
 Ha a Configuration Manager-ügyfelek a tartalom letöltése, automatikusan a használják, háttérben futó intelligens átviteli szolgáltatás (BITS) Ha rendelkezésre áll. Operációs rendszert telepítő feladatütemezés központi telepítésekor megadhat egy beállítást az üzemelő példányon, úgy, hogy a Configuration Manager-ügyfelek a teljes lemezképet a helyi gyorsítótárba letöltése a feladatütemezés futtatása előtt.  

 Általában a Configuration Manager-ügyfél le kell töltenie egy operációsrendszer-lemezképet (vagy bármilyen más csomagot), de nincs elég hely a gyorsítótárban, az ügyfél ellenőrzi, hogy a gyorsítótárban lévő többi csomagot, vagy az összes, a legrégebbi csomagok egy részének törlésével felszabadul elég szabad lemezterület a kép elférjen benne. Ha a csomagok törlésével nem szabadul fel elegendő lemezterület, az ügyfél nem tölti le az új lemezképet, így a központi telepítés sikertelen lesz. Ez akkor fordulhat elő, ha a gyorsítótár egy olyan nagyméretű csomagot tartalmaz, amely a gyorsítótárban való megőrzésre van konfigurálva. Ha a csomagok törlésével elegendő lemezterület szabadul fel, az ügyfél törli őket, majd letölti az új lemezképet a gyorsítótárba.  

 A Configuration Manager-ügyfelek alapértelmezett gyorsítótárméret nem feltétlenül elég nagy operációsrendszeri lemezképek központi telepítésére. Ha azt tervezi, hogy a teljes lemezképet letölti az ügyfél gyorsítótárába, módosítania kell a Configuration Manager ügyfél gyorsítótárméretét a célszámítógépeken, hogy megfeleljen a központilag telepíteni a lemezkép méretének.  

 További információ: [A Configuration Manager-ügyfelekhez tartozó ügyfélgyorsítótár konfigurálása](../../core/clients/manage/manage-clients.md#BKMK_ClientCache).  

## <a name="task-sequence-deployments"></a>Feladatütemezések központi telepítése  
 Az Ön által létrehozott feladatütemezés az operációs rendszer lemezképét a Configuration Manager-ügyfél számítógépen telepítheti a következő módszerek valamelyikével:  

-   Töltse le a lemezkép és benne lévő tartalom először a Configuration Manager-ügyfél gyorsítótárába egy terjesztési pontról, és telepítse azt.  

-   A lemezkép és a benne lévő tartalom telepítése egyenesen a terjesztési pontról.  

-   A lemezkép és a benne lévő tartalom telepítése az előírt módon a terjesztési pontról.  

 Alapértelmezés szerint a feladatütemezés, a központi telepítés létrehozásakor a lemezkép előbb letöltődik a Configuration Manager-ügyfél gyorsítótára és települ. Ha letölti a lemezképet a Configuration Manager-ügyfél gyorsítótárába, mielőtt futtatja a lemezképet, és a feladatütemezésben szerepel egy végezni a merevlemez újraparticionálását, az ismételt particionálása lépés sikertelen lesz, mivel a merevlemez particionálása töröl a Configuration Manager-ügyfél gyorsítótárának tartalmát. Amennyiben a feladatütemezés során el kell végezni a merevlemez újraparticionálását, Önnek a **Program futtatása terjesztési pontból**  lehetőség kiválasztásával futtatnia kell a lemezkép-telepítést a terjesztési pontról a feladatütemezés központi telepítésekor.  

 További információk: [Feladatütemezés telepítése](manage-task-sequences-to-automate-tasks.md#BKMK_DeployTS).  

