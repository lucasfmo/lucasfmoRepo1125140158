---
title: "Eszközök regisztrálása az eszközregisztráció-kezelő - a Configuration Manager a |} Microsoft Docs"
description: "A készülékregisztráció-kezelői fiók a System Center Configuration Managerrel a vállalat által birtokolt eszközök regisztrálása."
ms.custom: na
ms.date: 03/24/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2905f26e-7859-497d-b995-5ff48261efa2
caps.latest.revision: 8
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 7573590763c68a4c97d388be1e64054c318da9cc
ms.openlocfilehash: 8c491636925670732e6af67d8c1c741e4793ef96
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="enroll-devices-with-device-enrollment-manager-with-configuration-manager"></a>Eszközök regisztrálása a készülékregisztráció-kezelőt a Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A szervezetek Intune használatával nagyszámú mobileszközt felügyelhetnek egyetlen felhasználói fiókkal. A *eszközregisztráció-kezelő* (DEM-) fiók egy különleges felhasználói fiókkal, amely legfeljebb 1000 eszközt regisztrálhat. A meglévő felhasználók hozzáadása a DEM-fiók érdekében, hogy azok a speciális DEM képességeket. Minden egyes regisztrált eszköz egyetlen licencet használ. Azt javasoljuk, hogy használja-e ezen a fiókon keresztül megosztott eszközök felhasználói affinitás nélkül regisztrált eszközök megjelenítéséhez, nem pedig saját, dedikált eszközök.  

## <a name="enroll-corporate-owned-devices-with-the-device-enrollment-manager"></a>Az eszközregisztráció-kezelővel a vállalat által birtokolt eszközök regisztrálása  
 Hozzárendelhet egy tárolókezelői vagy, például eszközregisztráció-kezelői felhasználói fiókot, hogy végrehajthassa az alábbiakat:  

-   Legfeljebb 1000 eszközök regisztrálása felügyeletre  
-   A vállalati portál alkalmazás használata a vállalati alkalmazások telepítésével  
-   Vállalati adatok elérésének konfigurálása  

A készülékregisztráció-kezelői fiók segítségével felügyelt eszközöket a következő korlátozások vonatkoznak:

- A tárolókezelő nem állíthatja alaphelyzetbe az eszközt a vállalati portálról.  
- Eszközök munkahelyhez csatlakoztatott nem törölhetik vagy Azure Active Directoryhoz csatlakoztatott. Ez megakadályozza, hogy ezek az eszközök feltételes hozzáférés.
-  Vállalati alkalmazások telepítéséhez és az eszközregisztráció-kezelővel felügyelt eszközökre telepíthető a vállalati portál alkalmazás, egy **kötelező telepítés** az eszközregisztráció-kezelő felhasználói fiókhoz. Az eszközregisztráció-kezelő majd is elindíthatja a vállalati portál alkalmazás további alkalmazások telepítéséhez.
- A teljesítmény javítása érdekében a vállalati portál alkalmazás csak a helyi eszközön jeleníti meg. A Configuration Manager-konzol és a rendszergazda csak végezhető többi DEM-eszköz távoli felügyelete
- Eszközregisztráció-kezelői fiókok nem érhető el a vállalati portál webhelyét. A vállalati portál alkalmazás használata.
- (csak iOS) Ha DEM iOS-eszközök regisztrálása, eszközök regisztrálása az Apple Configuratorral vagy az Apple eszköz beléptetési Program (DEP) nem használható.

 **Eszközregisztráció-kezelői forgatókönyvek példái:**   
Egy étterem POS táblagépeket szeretne beállítani a várakozási munkatársak és kijelzőket a konyhai személyzetnek. Az alkalmazottaknak nincs szükségük hozzáférésre a vállalati adatokhoz, vagy jelentkezzen be egy olyan felhasználó nevében. Az Intune-rendszergazda létrehoz egy eszközregisztráció-kezelői fiókot, és regisztrálja a vállalat által birtokolt eszközöket fiókot használva. Másik lehetőségként a rendszergazda sikerült eszközregisztráció-kezelői hitelesítő adatokat adhat egy étterem, amely lehetővé teszi, hogy az eszközök regisztrálására és kezelésére.  

 A rendszergazda vagy a kezelő szerepkör-specifikus alkalmazásokat telepíthet a éttermi eszközök. A rendszergazda is jelöljön ki egy eszközt a konzolon, és kivonhatják a mobileszköz-felügyelet alól.  

#### <a name="add-a-device-enrollment-manager"></a>Az eszközregisztráció-kezelő hozzáadása  

1.  A Configuration Manager konzolon kattintson az **Adminisztráció**elemre.  

2.  Az **Adminisztráció** munkaterületen bontsa ki a **Felhőszolgáltatások** csomópontot, és kattintson a **Microsoft Intune-előfizetések** elemre. Válassza ki a Microsoft Intune-előfizetést, amelyhez Ön lesz az eszközregisztráció-kezelő hozzáadása, és kattintson **tulajdonságok**.  

3.  A Microsoft Intune-előfizetés tulajdonságai párbeszédpanelen kattintson a **Eszközregisztráció-kezelő** lapon.  

4.  Kattintson a **hozzáadása**.  

5.  Az a **Eszközregisztráció-kezelő** párbeszédpanelen írja be a felhasználónevet adja hozzá az eszközregisztráció-kezelő, és kattintson a kívánt felhasználó **keresési**. Válassza ki a felhasználót, az Eszközregisztráció-kezelő hozzáadása, és kattintson a kívánt **Hozzáadás**.  

6.  Győződjön meg arról, hogy a rendszer egy készülékregisztráció-kezelőt, majd kattintson a felhasználói fiók **hozzáadása**.  Előfizetési licencre szükség minden olyan felhasználóhoz, aki hozzáfér a szolgáltatáshoz és a *eszközregisztráció-kezelő* nem lehet Intune-rendszergazda. Határozza meg, hogy szükséges-e adnia további licenceket, ez a funkció használata előtt.  

7.  Az eszközregisztráció-kezelő most már ugyanazzal az eljárással a felhasználó használja a bring your-saját eszközök (használata BYOD) esetén a vállalati portál mobileszközök regisztrálása.  

#### <a name="delete-a-device-enrollment-manager-from-intune"></a>Az eszközregisztráció-kezelő törlése az Intune-ból  

1.  A Configuration Manager konzolon kattintson az **Adminisztráció**elemre.  

2.  Az **Adminisztráció** munkaterületen bontsa ki a **Felhőszolgáltatások** csomópontot, és kattintson a **Microsoft Intune-előfizetések** elemre. Válassza ki a Microsoft Intune-előfizetést, amelyhez Ön lesz az eszközregisztráció-kezelő hozzáadása, és kattintson **tulajdonságok**.  

3.  A Microsoft Intune-előfizetés tulajdonságai párbeszédpanelen kattintson a **Eszközregisztráció-kezelő** lapon.  

4.  **Keresési** a törölje, majd kattintson a kívánt készülékregisztráció-kezelő **eltávolítása**, majd **OK**.  

 Az eszközregisztráció-kezelő törlése nincs hatással a regisztrált eszközökön. Az eszközregisztráció-kezelő törlésekor:  

-   A regisztrált eszközöket nem érinti.  

-   A regisztrált eszközök továbbra is teljes mértékben felügyeltek  

-   A törölt eszközregisztráció manager fiók hitelesítő adatai továbbra is érvényesek a jelentkezzen be a vállalati portálra az alkalmazások eléréséhez  

-   A törölt eszközregisztráció manager fiók hitelesítő adatai nem törölhetik vagy vonhatják vissza az eszközöket  

-   A törölt eszközregisztráció-kezelői fiók kapcsolata megmarad a regisztrált fiókokkal, de további eszközöket nem lehet regisztrálni

