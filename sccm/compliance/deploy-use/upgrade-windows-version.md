---
title: "Windows-eszközök váltson egy másik verzió a Configuration Manager |} Microsoft Docs"
description: "Automatikus frissítése a Windows 10 asztali verzió, a Windows 10 Mobile vagy a Windows 10 Holographic és Configuration Manager másik kiadásra rendszerű eszközök."
ms.custom: na
ms.date: 04/18/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b0c9db74-841e-46eb-8924-957cde968bf7
caps.latest.revision: 8
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4eee9731a4a27328c47c0d15931cab28cf520a18
ms.openlocfilehash: cfde0a43947013bbd3a1093688cee19fe309fd03
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---

# <a name="upgrade-windows-devices-with-the-edition-upgrade-policy-in-system-center-configuration-manager"></a>A Kiadásfrissítési házirend a System Center Configuration Manager frissítési Windows-eszközök

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


A System Center Configuration Manager **Kiadásfrissítési házirend** lehetővé teszi, hogy a következő Windows 10-verziók valamelyikét-t futtató másik kiadásra eszközök automatikus frissítését:

- Windows 10 asztali verzió
- Windows 10 mobil verzió
- Windows 10 Holographic

A következő frissítési útvonalak használhatók:

- A Windows 10 Pro-fiókra a Windows 10 Enterprise
- A Windows 10 Education Windows 10 otthonról
- A Windows 10 mobil vállalati a Windows 10 Mobile
- A Windows 10 Holographic Pro a Windows 10 Holographic Enterprise

Az eszközök Microsoft Intune-ban regisztrált vagy a Configuration Manager ügyfélszoftver futtatásához. Ez a házirend jelenleg nem kompatibilis a helyszíni MDM által felügyelt számítógépek

## <a name="before-you-start"></a>Előkészületek  
 Az eszközök legújabb verzióra történő frissítésének megkezdése előtt szüksége lesz a következők valamelyikére:  

-   Termékkulcsra, amely érvényes a Windows új verziójának a házirend céljaként meghatározott összes eszközre történő telepítésére (asztali operációs rendszer esetén).  

-   A Microsoft által kiadott licencfájlra, amely tartalmazza azokat a licencelési adatokat, amelyek szükségesek a Windows új verziójának a házirend céljaként meghatározott összes eszközre történő telepítéséhez (a Windows 10 mobil és a Windows Holographic verzió esetén).

- Hozzon létre, és ez a szabályzattípus telepítése, akkor kell rendelni a Configuration Manager **teljes körű rendszergazda** biztonsági szerepkört.

## <a name="configure-the-edition-upgrade-policy"></a>A kiadásfrissítési házirend konfigurálása  

1.  Kattintson a Configuration Manager konzolon **eszközök és megfelelőség** > **megfelelőségi beállítások** > **Windows 10-kiadás frissítése**.  

3.  A **Kezdőlap** **Létrehozás** csoportjában kattintson a **Kiadásfrissítési házirend létrehozása**elemre.  

4.  Kattintson a **Házirend létrehozása**elemre.  

5.  A **Kiadásfrissítési házirend létrehozása varázsló** **Általános**lapján adja meg a következő információkat:  

    -   **Név** – Adja meg a kiadásfrissítési házirend nevét.  

    -   **Leírás** (nem kötelező) – Megadhatja a házirend leírását, hogy könnyebb legyen azonosítani az Intune-konzolon.  

    -   **Eszközfrissítési SKU** – A legördülő listából válassza ki a Windows 10 asztali, Windows 10 Holographic vagy Windows 10 mobil rendszernek azt a verzióját, amelyre a megcélzott eszközöket frissíteni szeretné.  

    -   **Licencadatok** – Válasszon az alábbi lehetőségek közül:  

        -   **Termékkulcs** – Adjon meg egy érvényes Windows 10-termékkulcsot a Windows 10 asztali operációs rendszert futtató, megcélzott eszközök frissítéséhez.  

            > [!NOTE]  
            >  Miután létrehozta a termékkulcsot tartalmazó házirendet, a termékkulcsot már nem szerkesztheti. Ennek oka a kulcs biztonsági okokból történő elrejtése. Ha módosítani szeretné a termékkulcsot, a teljes kulcsot újra meg kell adnia.  

        -   **Licencfájl** – Kattintson a **Tallózás** lehetőségre egy XML formátumú érvényes licencfájl kiválasztásához, amelyet a rendszer a megcélzott Windows 10 Holographic és Windows 10 mobil verziójú operációs rendszerű eszközök frissítésére fog használni.  

6.  Fejezze be a varázslót.  

Az új házirend az **Eszközök és megfelelőség** munkaterület **Windows 10-kiadás frissítése** csomópontjában jelenik meg.  

## <a name="deploy-the-edition-upgrade-policy"></a>A kiadásfrissítési házirend központi telepítése  

1.  Kattintson a Configuration Manager konzolon **eszközök és megfelelőség** > **megfelelőségi beállítások** > **Windows 10-kiadás frissítése**.  

3.  Válassza ki a telepíteni kívánt Windows 10-kiadás frissítési házirendjét, majd a **Kezdőlap** **Központi telepítés** csoportjában kattintson a **Telepítés**elemre.  

4.  Az a **központi telepítése Windows 10-kiadás frissítése** párbeszédpanelen válassza ki a kívánt központi telepítése a házirend- és az ütemezést, amely szerint a házirend kiértékelendő, és kattintson a gyűjtemény **OK**. A Configuration Manager ügyfélalkalmazással felügyelt számítógépekhez a házirend egy eszközgyűjteménybe kell telepítenie. A számítógépek regisztrált az Intune-nal telepítheti a házirendet egy felhasználót vagy eszközgyűjteményt. 

Az imént létrehozott központi telepítést a **Megfigyelés** munkaterület **Telepítések** csomópontjából figyelheti.  

 Amennyiben a szabályzat elér a célként megadott Windows-számítógép, és ki lesz értékelve, akkor a frissítés alkalmazásához két órán belül újraindul. Győződjön meg arról értesíti azokat a felhasználókat telepítette a házirendet, vagy a házirendet, a felhasználók futtatható ütemezése munkaidőn.

