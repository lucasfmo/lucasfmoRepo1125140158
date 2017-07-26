---
title: "Automatikusan eszközök kategorizálása gyűjteményekbe |} Microsoft Docs"
description: "Eszközök kategorizálása gyűjteményekbe automatikusan a System Center Configuration Managerrel."
ms.custom: na
ms.date: 04/23/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 98b038b4-1a13-4228-bdb8-a12194e32b0e
caps.latest.revision: 5
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: d1b79fb091a6ae4b967d63843ae7b45a0cbeb555
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="automatically-categorize-devices-into-collections-with-system-center-configuration-manager"></a>Automatikusan eszközök kategorizálása gyűjteményekbe a System Center Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Eszközök automatikus elhelyezése a eszközgyűjtemények használatakor a Configuration Manager a Microsoft Intune-nal használható eszközkategóriákat hozhat létre. A felhasználóknak majd kell az válasszon egy eszközkategóriát, amikor regisztrálják az eszköz Intune-ban. A Configuration Manager konzol eszközkategória módosítható.

> [!IMPORTANT]  
    >  Ez a funkció együttműködik az **2016. június** kibocsátási a Microsoft Intune, és később. Győződjön meg arról, hogy Ön frissített ebben a kiadásban ahhoz, hogy próbálja ki ezeket az eljárásokat.

## <a name="create-device-categories"></a>Eszközkategóriák létrehozása

1.  Ugrás a **eszközök és megfelelőség** > **áttekintése** > **Eszközgyűjtemények**.
2.  Az a **Home** lap a **Eszközgyűjtemények** csoportjában válassza **kezeléséhez eszközkategóriák**.
3.  Hozzon létre, szerkeszthet és eltávolíthat kategóriák.

## <a name="associate-a-collection-with-a-device-category"></a>Egy gyűjtemény társítandó eszközkategória

Eszközkategória hozzárendel egy gyűjteményt, ha az adott kategória minden eszköz megkapja a gyűjteményhez. Nem adható hozzá egy eszköz kategória szabály olyan beépített gyűjteményeket, mint például a **minden rendszer**.

1.  Az a **tagsági szabályok** lapján a **tulajdonságok** párbeszédpanel egy eszközgyűjteményt, válasszon **szabály hozzáadása** > **eszköz kategória szabály**.
2.  Az a **eszközkategóriákat válasszon** párbeszédpanelen válassza ki egy vagy több eszközkategóriákat a gyűjteményben lévő összes eszközre alkalmazni fogja őket.

## <a name="change-the-category-of-a-device"></a>Egy eszköz kategóriájának módosítása

1.  A **eszközök és megfelelőség** > **áttekintése** > **eszközök**, jelöljön ki egy eszközt a a **eszközök** listája.
2.  Az a **Home** lap a **eszköz** csoportjában válassza **változás kategóriája**.
3.  Válasszon ki egy kategóriát, majd kattintson a **OK**.

## <a name="view-which-category-a-device-belongs-to"></a>Egy eszköz mely kategóriába tartozik megtekintése

A **eszközök és megfelelőség** > **áttekintése** > **eszközök**, a a **eszközök** listája, a kategória jelenik meg a **eszközkategóriát** oszlop.

Ha a **eszközkategóriát** oszlop nem jelenik meg, az oszlopok egyikének kattint a jobb gombbal a **eszközök** lista (például **neve**) elemre, majd válassza **eszközkategóriát**.

Ha egy eszköz hozzárendelése egy kategóriát, és ezt követően törli a kategóriát, a jelentés **Microsoft Intune-ban felhasználónként regisztrált eszközök az** GUID, amely megjeleníti a **eszközkategóriát** oszlop, a kategória neve helyett.

