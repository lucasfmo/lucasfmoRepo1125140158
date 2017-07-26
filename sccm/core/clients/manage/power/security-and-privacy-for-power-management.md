---
title: "Biztonság és adatvédelem az energiagazdálkodás |} Microsoft Docs"
description: "Biztonsági és adatvédelmi tudnivalókat az energiagazdálkodáshoz a System Center Configuration Managerben beolvasása."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 469ff35f-59a1-484d-902b-107dd6070baf
caps.latest.revision: 5
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 94d5418c364c318dba92dc9f9066f54d1130aa34
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="security-and-privacy-for-power-management-in-system-center-configuration-manager"></a>Biztonság és adatvédelem az energiagazdálkodáshoz a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ez a szakasz az energiagazdálkodáshoz a System Center Configuration Manager biztonsági és adatvédelmi tudnivalókat tartalmaz.  

## <a name="security-best-practices-for-power-management"></a>Ajánlott biztonsági eljárások az energiagazdálkodáshoz  
 Az energiagazdálkodásnak nincsenek ajánlott biztonsági eljárásai.  

## <a name="privacy-information-for-power-management"></a>Az energiagazdálkodásra vonatkozó adatvédelmi tudnivalók  
 Az energiagazdálkodás a Windows beépített funkcióit használva figyeli az energiahasználatot és alkalmazza az energiaellátási beállításokat a számítógépekre a munkaidő során és a munkaidőn kívül. A Configuration Manager gyűjti össze az energiahasználati adatokat számítógépeket, beleértve egy felhasználó mikor használ egy számítógép adatait. Bár a Configuration Manager figyeli az egyes számítógépek helyett gyűjtemények erőforrás-használatot, a gyűjtemény csak egy számítógépet is tartalmazhat. Az energiagazdálkodás alapértelmezés szerint nem engedélyezett, és a rendszergazdának kell beállítania.  

 Energiahasználati adatokat a Configuration Manager-adatbázis tárolja, és a Microsoftnak nem küldi el. A részletes információkat 31 napig, az összesített információkat pedig 13 hónapig őrzi meg a rendszer az adatbázisban. A törlési időközt nem állíthatja be.  

 Az energiagazdálkodás konfigurálása előtt gondolja át az adatvédelmi követelményeit.  

