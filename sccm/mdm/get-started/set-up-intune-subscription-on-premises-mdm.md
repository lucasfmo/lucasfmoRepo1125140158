---
title: "Intune-előfizetés beállítása |} Microsoft Docs"
description: "Az Intune-előfizetés beállítása helyszíni mobileszközök kezeléséhez a System Center Configuration Managerben Licenckezelés nyomon követéséhez."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 1e42b1c1-3d58-481f-8647-5c7ae640c5f5
caps.latest.revision: 8
caps.handback.revision: 0
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: 5a81ec06e16992ae1c41b0fc98ebcd07386c5381
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="set-up-a-microsoft-intune-subscription-for-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>A Microsoft Intune-előfizetés beállítása helyszíni mobileszközök kezeléséhez a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager a\-helyszíni mobileszköz-kezelés a Microsoft Intune-előfizetés Licenckezelés nyomon követéséhez szükséges. Az Intune szolgáltatás nem használatos az eszközök felügyeletére vagy a felügyeleti információk tárolására. Az a\-helyszíni mobileszköz-kezelés, az összes eszköz kezelése a Configuration Manager infrastruktúrájának kezeli.  

> [!NOTE]  
> 1610 verziójától kezdve a Configuration Manager támogatja mindkét Microsoft Intune-nal és helyszíni mobileszközök felügyeletéhez egy időben a Configuration Manager-infrastruktúrát.   

> [!TIP]  
>  Azt javasoljuk, hogy a állít be az Intune-előfizetés\-helyszíni mobileszköz-kezelés, az újonnan telepített helyrendszerszerepkör működőképességéhez szükséges idő minimalizálásához szükséges helyrendszerszerepkörök telepítése előtt.  

##  <a name="sign-up-for-microsoft-intune"></a>Iratkozzon fel a Microsoft Intune  
 Adja meg a szükséges Intune\-helyszíni működési mobileszköz-kezelés. Egyszerűen [regisztráljon](http://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/) egy próbaverziós vagy fizetős előfizetésre, és ugorjon a következő lépésre az előfizetés felvételéhez a Configuration Manager.  

##  <a name="add-the-intune-subscription-to-configuration-manager"></a>Az Intune-előfizetés felvétele a Configuration Manager  
 Az előfizetés felvételéhez a Configuration Manager, hogy ugyanazokat a lépéseket alapvető ugyanúgy, ha az előfizetés felvétele a mobileszköz-kezelés az Intune-nal. A speciális eltéréseket alábbi megjegyzésekben olvassa el, és kövesse az utasításokat a [az Intune-előfizetés konfigurálása](../deploy-use/configure-intune-subscription.md).  

> [!NOTE]  
>  Az Intune-előfizetés hozzáadásakor vegye figyelembe a következőket:  
>   
>  -   A Microsoft Intune előfizetés hozzáadása varázslóban megadott gyűjtemény nem használatos a\-helyszíni mobileszköz-kezelés felhasználói jogok delegálásához. Az Intune-nal a mobileszköz-kezelés csak szolgál. A folytatáshoz azonban meg kell adnia egy gyűjteményt a varázslónak.  
> -   A kód beállítása a varázslóban megadott ignorálja a rendszer a\-helyszíni mobileszköz-kezelés. A használt helykód az, amelyiket Ön ad meg abban a regisztrálási profilban, amely engedélyezi a felhasználóknak a készülékek regisztrálását.  
> -   Ne engedélyezze a többtényezős hitelesítést, Azt nem támogatja a\-helyszíni mobileszköz-kezelés.  

##  <a name="configure-the-intune-subscription-for-on-premises-mobile-device-management"></a>A helyszíni mobileszköz-kezelés az Intune-előfizetés konfigurálása  

1.  A Configuration Manager konzolon kattintson a jobb gombbal a **Microsoft Intune-előfizetés**, és kattintson a **tulajdonságok**.  

2.  A helyszíni mobileszköz-kezelés a párbeszédpanelen válassza ki a következők egyikét:

  - Ha azt tervezi, hogy csak a felügyelt a helyszíni eszközök, jelölje be a jelölőnégyzetet a **csak a helyszíni eszközök kezelése**, és kattintson a **OK**.  

      > [!NOTE]  
      >  A jelölőnégyzet bejelölésével konfigurálása az Intune-előfizetés az összes felügyeleti információt a helyszínen és a felhő replikálja az adatokat.  

    - Ha azt tervezi, szeretné, hogy az Intune-ban és a Configuration Manager helyszíni által kezelt eszközök, hagyja bejelölve a mezőt.

3.  Ha Windows 10 Mobile rendszerű eszközöket szeretne felügyelni, kattintson a jobb gombbal a **Microsoft Intune-előfizetés**elemre, kattintson a **Platformok konfigurálása**parancsra, majd válassza a  **Windows Phone**elemet.  

4.  Jelölje be a **Windows Phone 8.1 és a Windows 10 Mobile**jelölőnégyzetet, majd kattintson az **OK**gombra.  

5.  Ha Windows 10 asztali számítógépeket szeretne felügyelni, kattintson a jobb gombbal a **Microsoft Intune-előfizetés**elemre, kattintson a **Platformok konfigurálása**parancsra, majd válassza a **Windows-igénylés engedélyezése**elemet.  

6.  Jelölje be a **Windows-igénylés engedélyezése**jelölőnégyzetet, és kattintson az **OK**gombra.  

