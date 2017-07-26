---
title: "Operációs rendszer központi telepítései közötti együttműködés tervezése |} Microsoft Docs"
description: "Együttműködési problémák ismerje meg, amikor egy hierarchián belül különböző System Center Configuration Manager-helyek eltérő verziókat használnak."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: e327ce38-6c07-4a27-b6eb-7e5bf74ed04b
caps.latest.revision: 10
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: 50a4b75b8c8c1cb6f7a8e696abad285f99080fcd
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="planning-for-operating-system-deployment-interoperability-in-system-center-configuration-manager"></a>Operációs rendszerek központi telepítései közötti együttműködés tervezése a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Amikor egy hierarchián belül különböző System Center Configuration Manager-helyek eltérő verziókat használnak, néhány a Configuration Manager funkcióihoz nem érhető el. A Configuration Manager újabb verziója funkciói általában nem érhető el az helyeken vagy ügyfeleknél, amelyek alacsonyabb verziójú szervizcsomaggal működnek. További információk: [Együttműködés a System Center Configuration Manager különböző verziói között](../../core/plan-design/hierarchy/interoperability-between-different-versions.md).  

 Amikor a legfelső szintű helyet a hierarchiában, és futtassa a Configuration Manager egy korábbi verziójával a hierarchia más helyeinek frissít, vegye figyelembe a következőket:  

-   Ügyfél-telepítési csomag  

    -   Az alapértelmezett ügyfél-telepítési csomag forrását a rendszer automatikusan frissíti, és a hierarchiában lévő összes terjesztési pont frissítődik az új ügyfél-telepítési csomaggal, még akkor is, a hierarchiában található, amely korábbi verziójú helyeken lévő terjesztési pontokra.  

    -   Az új verzióval működő ügyfelek nem rendelhető olyan helyekhez, amelyek még nincsenek frissítve az új verziót. Hozzárendelés a felügyeleti ponton blokkolva van.  

-   Rendszerindító lemezképek  

    -   Amikor a legfelső szintű helyen a Configuration Manager legújabb verziójára frissít, az alapértelmezett rendszerindító lemezképeket (x86 és x64) automatikusan Windows PE 10 használó Windows ADK for Windows 10-alapú rendszerindító lemezképekre frissülnek. Az alapértelmezett rendszerindító lemezképekhez társított fájlok is frissülnek a fájlok legújabb Configuration Manager verziójával. Az egyéni rendszerindító lemezképek nem frissülnek automatikusan. Szüksége lesz az egyéni rendszerindító lemezképek frissítéséhez manuálisan, mert az régebbi Windows PE azon verzióit tartalmazza.  

    -   Ha a helyhierarchiában a Configuration Manager eltérő verziójú helyei, ne kell a dinamikus média használatát. Inkább helyalapú médiát egy adott felügyeleti pont csatlakozni, amíg az összes hely frissítése a Configuration Manager azonos verzióját.  

    -   Győződjön meg arról, hogy a legújabb Configuration Manager rendszerindító lemezképek tartalmazzák a kívánt testreszabásokat, és módosítsa a hely összes terjesztési pontján a legújabb verzióra a Configuration Manager az új rendszerindító lemezképekkel.  

-   User State Migration Tool (USMT)  

    -   Amikor a legfelső szintű helyen a Configuration Manager legújabb verziójára frissít, az alapértelmezett USMT-csomagot automatikusan frissül a legújabb verzióra. Az egyéni USMT-csomagok nem frissülnek automatikusan. A csomagokat manuálisan kell frissítenie.  

-   Új feladatütemezési lépések  

    -   Időnként új feladatütemezési lépések új, a Configuration Manager új verziói. Amikor új lépéssel telepít feladatütemezést régebbi verziójú ügyfelekre, az új feladatütemezési lépés sikertelen lesz. Mielőtt egy feladatütemezést új lépéssel telepítene, győződjön meg arról, hogy a célgyűjtemény ügyfelei már frissítettek az új verzióra.  

-   Operációsrendszer-telepítési adathordozó  

    -   Minden media (rendszerindító, rögzítési, előkészített és különálló) frissíteni kell a Configuration Manager-ügyfél új csomagot a hely egy új verzióra való frissítésekor.  

-   Külső bővítmények operációs rendszer központi telepítéséhez  

    -   Ha külső bővítmények operációs rendszerek központi telepítése és a Configuration Manager-helyek vagy a Configuration Manager-ügyfelek, a vegyes hierarchiában különböző verziójú, a bővítményekkel problémák lehet.  

 Amikor a hierarchiában lévő helyeket aktív módon frissíti, a következő szakaszok segítséget nyújtanak az operációs rendszerek központi telepítésével kapcsolatban.  

## <a name="latest-version-of-configuration-manager-sites-in-a-mixed-hierarchy"></a>Legújabb verzióját a Configuration Manager-helyek vegyes hierarchiában  
 Amikor frissít egy helyet a legújabb verzióra a Configuration Manager, feladatütemezések, amelyek az alapértelmezett ügyfél-telepítési csomag hivatkozás automatikusan elindul, a Configuration Manager-ügyfél legújabb verziójának telepítéséhez. Egy ügyfél-telepítési csomagra hivatkozó feladatütemezések továbbra is fogják telepíteni az ügyfélnek, amelyik tartalmazza az adott egyéni csomagban (valószínűleg egy előző Configuration Manager ügyfélverzió) verzióját, és a feladat feladatütemezési központitelepítési hibák elkerülése érdekében meg kell adni. Ha egy feladatütemezés egyéni ügyfél-telepítési csomag használatára van konfigurálva, frissítenie kell a feladatütemezési lépés az ügyfél-telepítési csomag a Configuration Manager legújabb verzióját használja, vagy frissítse a legújabb Configuration Manager ügyfél-telepítési forrását használja az egyéni csomagot.  

> [!IMPORTANT]  
>  Ne telepítse a legújabb Configuration Manager Ügyféltelepítő csomagot az ügyfelek számára az régebbi a Configuration Manager-helyek hivatkozó feladatütemezést. Ha egy régebbi a Configuration Manager-helyhez hozzárendelt ügyfelek frissítése a legújabb Configuration Manager-ügyfél verziója, a Configuration Manager letiltja a társítást régebbi a Configuration Manager-hely. Ezért az ügyfél nem ettől kezdve nincs hozzárendelve egyetlen helyhez sem, és marad, amíg manuálisan hozzá nem rendeli egy legfrissebb Configuration Manager-hely vagy telepítse újra az ügyfél a Configuration Manager régebbi verzióját a számítógépen.  

## <a name="older-versions-of-configuration-manager-in-a-mixed-hierarchy"></a>Régebbi a Configuration Manager verziói vegyes hierarchiában  
 Amikor frissítette a központi adminisztrációs hely a Configuration Manager legújabb verziójára, győződjön meg arról, hogy operációs rendszer telepítési feladatütemezések központi telepítése (a Configuration Manager legújabb verziójára még nem frissített) régebbi a Configuration Manager-helyhez hozzárendelt ügyfelekhez beállított hagyják ezeket az ügyfeleket kezeletlen állapotban a következő lépéseket kell tennie.  

-   Hozzon létre egy feladatütemezést, amely csak a Configuration Manager-hely ügyfelekre történő központi telepítéséhez használhatja. Valószínűleg fog készíteni egy feladatütemezést, amely a legújabb Configuration Manager-hely ügyfelekhez, és ezután módosítja a feladatütemezést, így az ügyfelek számára az régebbi a Configuration Manager-helyek Ezután telepítheti azt egy példányát. Ezt követően konfigurálja a feladatütemezést, amely a régebbi a Configuration Manager ügyfél-telepítési forrását használja egyéni ügyfél-telepítési csomagra hivatkozzon. Ha még nem rendelkezik a régebbi a Configuration Manager ügyfél-telepítési forrásának hivatkozó egyéni ügyfél-telepítési csomagra majd manuálisan kell létrehoznia egyet.  

