---
title: "Bevezetés a lekérdezésekbe |} Microsoft Docs"
description: "Hozzon létre, és a lekérdezési feltételeknek megfelelő objektumok kereséséhez a System Center Configuration Manager-hierarchia lekérdezések futtatásához."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 03d1b3a9-41db-4d3a-a70e-e05ab5dc8141
caps.latest.revision: 5
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 10b1010ccbf3889c58c55b87e70b354559243c90
ms.openlocfilehash: f84d518670c0ece3c08c890d2293335518f7f8e9
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="introduction-to-queries-in-system-center-configuration-manager"></a>A System Center Configuration Manager lekérdezéseinek bemutatása

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Hozzon létre, és futtassa a lekérdezések objektumok kereséséhez a System Center Configuration Manager-hierarchiában, amely megfelel a lekérdezési feltételeknek. Ezek az objektumok elemeket, például adott típusú számítógépeket vagy felhasználói csoportokat tartalmaznak. Lekérdezések visszaadhatják a legtöbb típusú Configuration Manager-objektumok, például a helyek, gyűjteményeket, alkalmazásokat és leltáradatokat.  

 A lekérdezés létrehozásakor meg kell adnia legalább két paramétert: azt, hogy hol szeretne keresni, illetve hogy mit. Például a Configuration Manager-hely összes számítógépén elérhető merevlemez-terület mennyisége található, létrehozhat egy lekérdezést a **logikai lemez** attribútumosztály és a **szabad terület (MB)** attribútum a szabad lemezterület.  

 Miután létrehozott egy kezdeti lekérdezést, további feltételeket is megadhat. Megadhatja például, hogy a lekérdezés eredményei csak a megadott helyhez rendelt számítógépeket tartalmazzák. Módosíthatja azt is, hogy hogyan jelenjenek meg az eredmények, hogy az eredmények megfelelő, kifejező sorrendben legyenek megtekinthetők. Megadhatja például, hogy az eredmények a szabad merevlemez-terület mennyisége alapján növekvő vagy csökkenő sorrendben legyenek rendezve.  

 A lekérdezés létrehozásakor a Configuration Manager által tárolt és jelenik meg a **lekérdezések** csomópontja a **figyelés** munkaterületen. Erről a helyről hozhat létre új lekérdezést és futtathatja, frissítheti vagy kezelheti a meglévő lekérdezéseket.  

 A lekérdezés egy Configuration Manager gyűjtemény egy lekérdezési szabályba is importálhat. További információkért lásd: [gyűjtemények létrehozása a System Center Configuration Managerben](../../../core/clients/manage/collections/create-collections.md).  

## <a name="see-also"></a>Lásd még:  
 [Lekérdezések technikai útmutató a System Center Configuration Managerhez](../../../core/servers/manage/queries-technical-reference.md)

