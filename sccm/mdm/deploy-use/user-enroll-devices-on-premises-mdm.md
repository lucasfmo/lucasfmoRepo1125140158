---
title: "A helyszíni MDM - Configuration Manager-eszközök regisztrálása a felhasználók |} Microsoft Docs"
description: "Ismerje meg a helyszíni mobileszköz-kezelés a System Center Configuration Manager-eszközök regisztrálása a felhasználók."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 59004b34-b64f-4d77-898c-07bf3dc75430
caps.latest.revision: 9
caps.handback.revision: 0
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 507bad02c6e028f09a8b0c8a566ac55f7c3942a5
ms.openlocfilehash: 8c7438c2cc0bc66654eb3e74de10553df53181d9
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-users-enroll-devices-with-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>A helyszíni mobileszköz-kezelés a System Center Configuration Manager-eszközök regisztrálása a felhasználók

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager helyszíni mobileszköz-kezelés, a felhasználók regisztrálhatják eszközeiket Ha kaptak regisztrálási jogosultságot (vállalja frissített ügyfélbeállításokkal), és az eszközeiken a szükséges helyrendszerszerepköröket üzemeltető kiszolgálókkal való megbízható kommunikációra a szükséges főtanúsítvány. Regisztráció beállításával kapcsolatos további információkért lásd: [a helyszíni mobileszköz-kezelés a System Center Configuration Managerben az eszközregisztráció beállítása](../../mdm/get-started/set-up-device-enrollment-on-premises-mdm.md).  

> [!NOTE]  
>  Az aktuális ág a Configuration Manager helyszíni mobileszköz-kezelés a következő operációs rendszereket futtató eszközök beléptetési támogatja:  
>   
> -  Windows 10 Enterprise  
> -   Windows 10 Pro  
> -   A Windows 10 Team \(kezdve a Configuration Manager 1602-es verzió\)  
> -   Windows 10 mobil verzió  
> -   Windows 10 Mobile Enterprise
> -   Windows 10 IoT Enterprise   

A következő feladatok azt ismertetik, hogyan kell regisztrálni, és ellenőrizze, hogy a számítógépek és eszközök regisztrálását\-helyszíni mobileszköz-kezelés:  

-   [Windows 10 rendszerű számítógép regisztrálása](#bkmk_enrollDesk)  

-   [Windows 10 Mobile rendszerű eszköz regisztrálása](#bkmk_enrollMob)  

-   [Eszközbeléptetés ellenőrzése](#bkmk_verify)  

##  <a name="bkmk_enrollDesk"></a> Windows 10 rendszerű számítógép regisztrálása  

1.  A Windows 10 rendszerű számítógépen nyissa meg a **Gépházat**.  

2.  Kattintson a **Fiókok**, majd a **Munkahelyi hozzáférés**lehetőségre.  

3.  A Munkahelyi hozzáférés terület **Csatlakozás munkahelyi vagy iskolai rendszerhez**szakaszában kattintson a **Csatlakozás**lehetőségre, adja meg a munkahelyi e-mail címét, majd kattintson a **Tovább**gombra.  

4.  Adja meg a beléptetési proxy pont helyrendszerszerepkört futtató kiszolgáló teljes Tartománynevét, majd kattintson a **Folytatás**.  

5.  A Csatlakozás szolgáltatáshoz szakaszban adja meg a munkahelyi e-mail címéhez tartozó jelszót, majd kattintson a **Bejelentkezés**lehetőségre.  

6.  A bejelentkezési adatok megjegyzésénél kattintson a **Kihagyás** lehetőségre. Az eszköz rövid idő múlva csatlakoztatva lesz.  

##  <a name="bkmk_enrollMob"></a> Windows 10 Mobile rendszerű eszköz regisztrálása  

1.  Nyissa meg a **Gépházat**a Windows 10 Mobile rendszerű eszközön.  

2.  Kattintson a **Fiókok**, majd a **Munkahelyi hozzáférés**lehetőségre.  

3.  Kattintson a **Csatlakozás**gombra.  

4.  Adja meg a munkahelyi e-mail címét és a beléptetési proxypont helyrendszerszerepkört futtató kiszolgáló teljes tartománynevét. Kattintson a **Csatlakozás**gombra.  

5.  A következő képernyőn írja be a munkahelyi e-mail címét és az ahhoz tartozó jelszót, majd kattintson a **Bejelentkezés**lehetőségre. Rövid idő múlva az eszköz regisztrálva lesz. Kattintson a **Befejezés**lehetőségre.  

##  <a name="bkmk_verify"></a> Eszközbeléptetés ellenőrzése  
 Ellenőrizheti, hogy eszközök sikeres regisztrálását a Configuration Manager konzolon.  

1.  A Configuration Manager konzol elindítása.  

2.  Kattintson a **Eszközök és megfelelőség** > **Áttekintés** > **Eszközök**rendszerhez szükséges helyrendszerszerepkörök közötti megbízható kommunikációhoz szükséges. A regisztrált eszköz megjelenik a listán.  

