---
title: "Ügyfélbeállítások konfigurálása |} Microsoft Docs"
description: "Válassza ki az ügyfél beállításait a System Center Configuration Managerben."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 95e9858a-bad4-4651-9e61-2e31dc5050fa
caps.latest.revision: 5
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 478d562bfb7fdb3921a4278741ff096e81e6092a
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="how-to-configure-client-settings-in-system-center-configuration-manager"></a>Ügyfélbeállítások konfigurálása a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Kezelheti az összes ügyfél beállításai a System Center Configuration Managerben a **felügyeleti** > **ügyfélbeállítások**. Az alapértelmezett beállítások módosításával konfigurálhatja a hierarchiában lévő összes ügyfél és eszköz olyan beállításait, amelyekre nem kell egyéni beállítást megadni. Ha néhány felhasználóra vagy eszközre eltérő beállításokat szeretne alkalmazni, hozzon létre egyéni beállításokat, és telepítse azokat a gyűjteményükre.  

További információ az egyes ügyfélbeállításokról: [információ a System Center Configuration Manager ügyfélbeállításainak](../../../core/clients/deploy/about-client-settings.md).

> [!NOTE]  
>  Használhat konfigurálási elemeket, hogy felügyelje az ügyfeleket az eszközök felmérése, követése és a konfigurálásuk megfelelőségének karbantartása vonatkozásában. További információkért lásd: [a System Center Configuration Managerrel eszközök megfelelőségének biztosítása](../../../compliance/understand/ensure-device-compliance.md).  

##  <a name="configure-the-default-client-settings"></a>Az alapértelmezett ügyfélbeállítások konfigurálása    

1.  Kattintson a Configuration Manager konzol **felügyeleti** > **ügyfélbeállítások** > **alapértelmezett ügyfélbeállítások**.  

3.  Az a **Home** lapra, majd **tulajdonságok**.  

4.  Tekintse át és konfigurálja megfelelően a navigációs ablaktáblában található beállításcsoportokban lévő ügyfélbeállításokat.  

 Az ügyfélszámítógépek ezekkel a beállításokkal lesznek konfigurálva, amikor legközelebb letöltik az ügyfélházirendet. Egy ügyfél házirend lekérésének kezdeményezéséhez, lásd: [Házirendlekérésről kezdeményezése a Configuration Manager-ügyfél](../../../core/clients/manage/manage-clients.md#BKMK_PolicyRetrieval) a [ügyfélszoftverek kezelése a System Center Configuration Managerben](../../../core/clients/manage/manage-clients.md).  

##  <a name="create-and-deploy-custom-client-settings"></a>Hozzon létre és egyéni ügyfélbeállítások központi telepítése  
Amikor alkalmazza ezeket az egyéni beállításokat, azok felülírják az alapértelmezett ügyfélbeállításokat. Mielőtt elkezdi a művelet végrehajtását, hozzon létre egy gyűjteményt, amely ezeket az egyéni ügyfélbeállításokat igénylő felhasználókat vagy eszközöket tartalmazza.  

1.  Kattintson a Configuration Manager konzol **felügyeleti** > **ügyfélbeállítások**.  

3.  Az a **Home** lap a **létrehozása** csoportjában válassza **egyéni ügyfélbeállítások létrehozása**, majd válassza:  

    -   **Egyedi ügyfél-eszközbeállítás létrehozása**  

    -   **Egyedi ügyfélfelhasználó-beállítások létrehozása**  

4.  Adjon meg egyedi nevet és a beállítás leírását.  

5.  Jelöljön ki legalább egy, a megfelelő jelölőnégyzeteket jeleníti meg a beállításokat.  

6.  A navigációs ablaktáblán válassza ki a beállításcsoportokban és a rendelkezésre álló beállítások konfigurálása, majd kattintson **OK**.   

8.  Válassza ki a létrehozott egyéni ügyfélbeállítások. Az a **Home** lap a **ügyfélbeállítások** csoportjában válassza **telepítés**.  

9. Az a **gyűjtemény választása** párbeszédpanelen válassza ki a megfelelő gyűjteményt, és válassza a **OK**. A kijelölt gyűjtemény ellenőrzéséhez a részletek ablaktáblájában kattintson a **Központi telepítések** lapra.  

10. Tekintse meg az imént létrehozott egyéni ügyfélbeállítások sorrendjét. Ha több egyéni ügyfélbeállítással rendelkezik, azokat sorszámuk szerint alkalmazza a rendszer. Ütközés esetén a kisebb sorszámú beállítás felülbírálja a többi beállítást. A sorszám megváltoztatásához a a a **Home** lap a **ügyfélbeállítások** csoportjában válassza **elem áthelyezése felfelé** vagy **elem áthelyezése lefelé**.  

 Az ügyfélszámítógépek ezekkel a beállításokkal lesznek konfigurálva, amikor legközelebb letöltik az ügyfélházirendet. Egy ügyfél házirend lekérésének kezdeményezéséhez, lásd: [Házirendlekérésről kezdeményezése a Configuration Manager-ügyfél](../../../core/clients/manage/manage-clients.md#BKMK_PolicyRetrieval) a [ügyfélszoftverek kezelése a System Center Configuration Managerben](../../../core/clients/manage/manage-clients.md).  

##  <a name="view-client-settings"></a>Ügyfél beállítások megjelenítése  
 Ha több ügyfélbeállítás lett telepítve ugyanarra az eszközre, felhasználóhoz vagy felhasználócsoporthoz, a beállítások elsődlegességének és kombinálásának meghatározása bonyolult lehet. Az ügyfélbeállítások megtekintése:  

1.  Kattintson a Configuration Manager konzol **eszközök és megfelelőség** > **eszközök** > **felhasználók** vagy **Felhasználógyűjtemények**.  

3.  Jelöljön ki egy eszközt, felhasználót vagy felhasználócsoportot, és az **Ügyfél beállításai** csoportban válassza az **Eredő ügyfélbeállítások**elemet.  

4.  Kijelöl egy ügyfélbeállítást a bal oldali ablaktáblán, és a beállítások is megjelennek. Ebben a nézetben a beállítások nem módosíthatók. 

    > [!NOTE]  
    >  Az ügyfélbeállítások megtekintéséhez ügyfélbeállítások olvasási hozzáféréssel kell rendelkeznie.  

    
