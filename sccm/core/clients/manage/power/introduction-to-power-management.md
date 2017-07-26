---
title: "Energiagazdálkodás – bevezetés |} Microsoft Docs"
description: "Bevezetés az energiagazdálkodás a System Center Configuration Managerben."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3ddff2a7-99eb-4ef8-b969-f3f7f24053db
caps.latest.revision: 4
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: fc392e4440e84614f92218e9c7a09ec1c2c64f53
ms.openlocfilehash: f46c9479021c814b1102d72c7d493f21a7243bf1
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="introduction-to-power-management-in-system-center-configuration-manager"></a>Az energiagazdálkodás a System Center Configuration Manager bemutatása

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Managerben az energiagazdálkodás megoldást kell, hogy a szervezetek figyelhessék és csökkenthessék számítógépeik energiafogyasztását. Ez a szolgáltatás a Windowsba beépített energiagazdálkodási szolgáltatásokat kihasználva megfelelő és egységes beállításokat alkalmaz a szervezet számítógépein. A számítógépeken különböző energiaellátási beállításokat alkalmazhat a munkaidőre és a munkaidőn kívüli időszakokra. Érdemes lehet például egy sokkal korlátozóbb energiasémát alkalmazni a számítógépeken a munkaidőn kívüli időszakokban. Letilthatja az energiagazdálkodási beállítások alkalmazását azokban az esetekben, amikor a számítógépeknek állandóan bekapcsolt állapotban kell lenniük.  

 Az energiagazdálkodás a Configuration Manager segítségével elemezheti energiafogyasztását és a számítógép energiaellátási beállításait a szervezetben számos jelentést tartalmaz. A jelentéseket az energiagazdálkodással kapcsolatos problémák elhárításához is használhatja.  

 Konfigurálhatja és használhatja az energiagazdálkodás kapcsolatos részletes munkafolyamatáról, lásd: [rendszergazdai ellenőrzőlista az energiagazdálkodáshoz a System Center Configuration Managerben](../../../../core/clients/manage/power/administrator-checklist-for-power-management.md).  

> [!IMPORTANT]  
>  Configuration Manager energiagazdálkodási virtuális gépeken nem támogatott. Virtuális gépeken nem alkalmazhat energiasémákat, és nem jelentheti róla az energiagazdálkodási adatokat.  

## <a name="the-power-management-workflow"></a>Az energiagazdálkodás munkafolyamata  
 Használja a következő folyamat három szakaszból tervezésével és megvalósításával az energiagazdálkodás a Configuration Manager alkalmazásban.  

### <a name="monitoring-and-planning-phase"></a>Figyelési és tervezési fázis  
 Az energiagazdálkodás a Configuration Manager-Hardverleltár számítógép és a-beállításaival kapcsolatban a helyen található számítógépek adatainak gyűjtéséről. Az adatok elemzéséhez és a számítógépek optimális energiagazdálkodási beállításainak meghatározásához számos jelentés használható. Az energiagazdálkodási munkafolyamat figyelési és tervezési fázisában például az **Energiaellátási lehetőségek** jelentésben szereplő adatok alapján gyűjteményeket hozhat létre, és az adatokat használva azonosíthatja az energiagazdálkodásra nem alkalmas számítógépeket. Ezután kizárhatja az adott számítógépeket az energiagazdálkodásból.  

> [!IMPORTANT]  
>  Csak az ügyfélszámítógépek energiagazdálkodási adatainak összegyűjtését és elemzését követően alkalmazzon energiasémákat helye számítógépeire. Ha a meglévő beállítások vizsgálata nélkül alkalmaz új energiagazdálkodási beállításokat a számítógépekre, az energiafogyasztás növekedését tapasztalhatja.  

### <a name="enforcement-phase"></a>Alkalmazási fázis  
 Az energiagazdálkodás lehetővé teszi, hogy a hely számítógép-gyűjteményére alkalmazható energiasémákat hozzon létre. Ezek az energiasémák konfigurálják a Windows energiagazdálkodási beállításait a számítógépeken. Használhatja a Configuration Manager részét képező energiasémákat, vagy a saját egyéni energiasémákat is beállíthat. A figyelési és tervezési fázis során gyűjtött energiagazdálkodási adatokat kiindulópontként használva értékelheti ki az energiamegtakarítást, miután energiasémát alkalmazott a számítógépeken. További információkért lásd: [rendszergazdai ellenőrzőlista az energiagazdálkodáshoz a System Center Configuration Managerben](../../../../core/clients/manage/power/administrator-checklist-for-power-management.md).  

### <a name="compliance-phase"></a>Megfelelőségi fázis  
 A megfelelőségi fázisban jelentéseket futtathat, amelyek segítségével kiértékelheti szervezete energiafogyasztását és energiaköltség-megtakarítását. A számítógépek által generált CO2 mennyiségének terén elért fejlesztéseket ismertető jelentéseket is futtathatja. Rendelkezésre állnak olyan jelentések is, amelyekkel kiértékelheti, hogy az energiaellátási beállításokat megfelelően alkalmazta-e a számítógépekre, és amelyek segítségével elháríthatja az energiagazdálkodási szolgáltatással kapcsolatos hibákat.  

