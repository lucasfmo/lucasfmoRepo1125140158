---

title: "Eszközök regisztrálása |} Microsoft Docs"
description: "További információk a módszerek eszközök regisztrálása a helyszíni mobileszközök kezeléséhez a System Center Configuration Managerben."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: b58472e3-31a5-4305-8eb6-2522befebe02
caps.latest.revision: 6
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3b1451edaed69a972551bd060293839aa11ec8b2
ms.openlocfilehash: 4abaef35969ef1a5340ae8ca8aa5699cd3942642
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="enroll-devices-for-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>Eszközök regisztrálása a System Center Configuration Manager helyszíni mobileszköz-felügyeletében

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Számítógépek és a System Center Configuration Manager helyszíni mobileszköz-kezelés az eszközök kezelésére, az eszközök úgy, hogy a Configuration Manager képes kommunikálni a felügyeleti feladatok eszközöket regisztrálni kell. A Configuration Manager-eszközök regisztrációjával kapcsolatos két módszert kínál:  

-   **Felhasználói regisztrálás** – ezzel a módszerrel a felhasználók kezdeményezhetik a regisztrációs folyamatot az eszközeiken. A felhasználóregisztráció sikeres az eszköz telepítve van-e megbízható legfelső szintű tanúsítvánnyal kell rendelkeznie, és a felhasználónak ki kell építenie a regisztrációt a Configuration Manager által.  Az eszköz regisztrálásához a felhasználónak egyszerűen csak meg kell adnia munkahelyi hitelesítő adatait, és a rendszer regisztrálja az eszközt felügyeletre.  

     További információkért lásd: [a helyszíni mobileszköz-kezelés a System Center Configuration Manager-eszközök regisztrálása a felhasználók](../../mdm/deploy-use/user-enroll-devices-on-premises-mdm.md)  

-   **Csoportos regisztrálás** – ezen módszer esetében a felhasználónak nem kell kezdeményeznie az eszköz regisztrálását. Ehelyett egy csoportos regisztrációs csomagot a Configuration Manager alkalmazásban létrehozott majd elhelyez az eszközön és megnyitni. Az eszköz regisztrálásához szükséges adatokat a csomag biztosítja a megnyitásakor.  

     További információkért lásd: [a helyszíni mobileszköz-kezelés a System Center Configuration Manager-eszközök tömeges regisztrálása](../../mdm/deploy-use/bulk-enroll-devices-on-premises-mdm.md)  

 > [!NOTE]  
>  Az aktuális ág a Configuration Manager helyszíni mobileszköz-kezelés a következő operációs rendszereket futtató eszközök beléptetési támogatja:  
>   
>  -   Windows 10 Enterprise  
> -   Windows 10 Pro  
> -   Windows 10 Team 
> -   Windows 10 mobil verzió  
> -   Windows 10 Mobile Enterprise   

