---
title: "Helyszíni mobileszköz-kezelés (MDM) |} Microsoft Docs"
description: "További információk a helyszíni mobileszköz-kezelés, egy MDM-megoldás a System Center Configuration Managerben."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 497c05c7-fe9f-4b88-983b-1c5b3d59308e
caps.latest.revision: 8
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: 7b96c4d4d87aa150eacc5d7d20710f5d2199e48a
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="on-premises-mobile-device-management-mdm-in-system-center-configuration-manager"></a>A helyszíni mobileszköz-kezelés (MDM) a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager a\-helyszíni mobileszköz-kezelés egy Eszközkezelési megoldás, amely az eszköz operációs rendszerek (az Open Mobile Alliance Device Management vagy OMA DM szabvány alapján) beépített kezelési képességeire támaszkodik használja ki a vállalat Configuration Manager infrastruktúrájának kezeli és tartja karban az eszközöket. A\-helyszíni mobileszköz-kezelés megköveteli a Microsoft Intune-t állítsa be a felügyeleti funkció, de csak szükség esetén az előfizetés (és időpontokban kereséséhez házirend módosításai eszközök értesítésére segítségével), de nem használatos az eszközök kezeléséhez, vagy a rájuk vonatkozó adatok tárolására.  

 ![A\-fogalmi helyi](media/On-premises-conceptual.png)  

 A\-a helyszíni mobileszköz-kezelés eltér a Microsoft Intune-ból, amelyek beépített OMA DM képességeket is használ, de felhőszolgáltatásokkal vannak összes felügyeleti funkció.  A\-helyszíni mobileszköz-kezelés is eltér az ügyfél-alapú megoldás a Configuration Manager által hagyományosan kínált a abban a hasonló vállalati infrastruktúrára támaszkodik, de nem használ különállóan telepített ügyfélszoftvert a számítógépek és az általa felügyelt eszközök.  

 Az alábbi táblázat felsorolja a előnyeit és hátrányait On\-helyszíni mobileszköz-kezelés hagyományos ügyfélalapú felügyelet képest:  

|Előnyök|Hátrányok|  
|----------------|-------------------|  
|**Egyszerűsített infrastruktúra** – kevesebb helyrendszerszerepkör szükséges.<br /><br /> **Egyszerűbben kezelhető** -felügyeleti funkciók be építve az eszköz operációs rendszere, mert az ügyfélszoftver új verzióját esetén nem szükséges új felügyeleti funkciókkal bővül a Configuration Manager rendszerben.<br /><br /> **Helyszíni** – minden kezelés és adat a helyszínen marad.|**Kevesebb ügyfélkezelési funkció** – nem érhető el a vezénylés, a szoftverhasználat-mérés, a harmadik féltől származó szoftverek integrációja és a feladatütemezés, illetve nem támogatott a Szoftverközpont használata.<br /><br /> **Korlátozott eszköztámogatás** – jelenleg\-helyszíni mobileszköz-kezelés csak Windows 10 és Windows 10 Mobile rendszerű eszközöket támogatja.|  

 A következő témakörök nyújtanak információkat segítségével tervezéséhez, előkészítéséhez és az eszközök regisztrálása a\-helyszíni mobileszköz-kezelés:  

-   [Tervezze meg a helyszíni mobileszköz-kezelés a System Center Configuration Managerben](../plan-design/plan-on-premises-mdm.md)  

     Megtudhatja, mit kell figyelembe venni, amikor a Configuration Manager-infrastruktúra beállítása és az eszközök regisztrálásával az tervezése\-helyszíni mobileszköz-kezelés.  

-   [Előkészítő lépések helyszíni mobileszközök kezeléséhez a System Center Configuration Managerben](../get-started/preparation-steps-for-on-premises-mdm.md)  

     További tudnivalók a rendszer a Configuration Manager készen áll a az beszerzése\-helyszíni mobileszköz-kezelés által a Microsoft Intune-előfizetés beállítása, a tanúsítványok beállításával, a helyrendszerszerepkörök telepítéséről és a eszközregisztráció beállításával.  

-   [Eszközök regisztrálása a helyszíni mobileszköz-kezelés a System Center Configuration Managerben](../deploy-use/enroll-devices-on-premises-mdm.md)  

     További információ a regisztrálás folyamatáról, illetve arról, a felhasználók hogyan regisztrálhatják saját eszközeiket, és hogyan végezhető el az eszközök tömeges regisztrálása regisztrációs csomagokkal.  

