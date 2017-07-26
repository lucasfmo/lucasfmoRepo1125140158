---
title: "A System Center Configuration Manager az Intune-előfizetés konfigurálása |} Microsoft Docs"
description: "A System Center Configuration Manager az Intune-előfizetés konfigurálása."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 99de8fe7-560e-401a-8ab2-6d87d091be17
caps.latest.revision: 18
caps.handback.revision: 0
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: 10cc64ae7e4d91f53201c2896b359e77ef04d32d
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="configure-your-intune-subscription-with-system-center-configuration-manager-and-microsoft-intune"></a>Az Intune-előfizetés konfigurálása a System Center Configuration Manager és a Microsoft Intune

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Az Intune-előfizetés lehetővé teszi az eszközök kezelését az interneten keresztül. Ez magában foglalja, adja meg, melyik felhasználói gyűjtemény regisztrálhatják eszközeiket, és a felhasználók számára megjelenő adatok meghatározása. Az Intune-előfizetés létrehozása során azt is megteheti vállalati arculat megjelenítése az Intune vállalati portál a vállalat emblémájának elhelyezésével és egyéni színsémák rendszerek.

Az Intune-előfizetés a következőket hajtja végre:

-   Beolvassa a tanúsítványt, amelyre a szolgáltatáskapcsolódási pontnak szüksége van az Intune szolgáltatáshoz való csatlakozáshoz
-   Definiálja a felhasználógyűjteményt, amely lehetővé teszi a felhasználóknak a mobileszközök regisztrálását
-   Definiálja és konfigurálja a támogatni kívánt mobilplatformokat

> [!IMPORTANT]
>  A Configuration Manager a Microsoft Intune-előfizetés létrehozása a hely szolgáltatáskapcsolódási pont helyezzük "online módba". Lásd: [A System Center Configuration Manager szolgáltatáskapcsolódási pontjának ismertetése](../../core/servers/deploy/configure/about-the-service-connection-point.md).

## <a name="to-create-the-microsoft-intune-subscription"></a>A Microsoft Intune-előfizetés létrehozása

1.  Ha még nincs Microsoft Intune-fiókja, regisztráljon a [Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=258216) webhelyén.  Az Intune-fiók létrehozása után nem kell azokat a felhasználókat hozzáadása az Intune-fiókkal, vagy további beállításokat konfigurációk végrehajtása.

2.  A Configuration Manager konzolon kattintson az **Adminisztráció**elemre.

3.  Az **Adminisztráció** munkaterületen bontsa ki a **Felhőszolgáltatások** csomópontot, és kattintson a **Microsoft Intune-előfizetések** elemre. A **Kezdőlapon** kattintson a **Microsoft Intune-előfizetés hozzáadása** elemre.

![Az Intune-előfizetés létrehozása](../media/mdm-set-intune.png)

4.  Olvassa el a Microsoft Intune-előfizetés létrehozása varázsló **Bevezetés** lapján írtakat, és kattintson a **Tovább** gombra.

5.  Az **Előfizetés** lapon kattintson a **Bejelentkezés** gombra, és jelentkezzen be munkahelyi vagy intézményi fiókjával. Az a **a mobileszköz-kezelő szolgáltatás beállítása** párbeszédpanelen jelölje be a jelölőnégyzetet, hogy csak mobileszközök kezelése a Configuration Manager konzol segítségével a Configuration Manager használatával. Az előfizetés folytatásához be kell jelölnie ezt a lehetőséget.

    > [!IMPORTANT]
    >  Miután a Configuration Manager t választotta felügyeleti szolgáltatóként, nem módosíthatja a felügyeleti hatóság a Microsoft Intune a jövőben.

6.  Az adatvédelmi szabályzatok megtekintéséhez kattintson a megfelelő hivatkozásokra, majd kattintson a **Tovább** gombra.

7.  Az **Általános** lapon adja meg a következő beállításokat, majd kattintson a **Tovább** gombra.

  -   **Gyűjtemény**: Adjon meg egy felhasználógyűjteményt azokkal a felhasználókkal, akik regisztrálni fogják a mobileszközeiket.

      > [!NOTE]
      >  Ha egy felhasználót eltávolít a gyűjteményből, a felhasználó-eszköz továbbra is felügyeli a legfeljebb 24 óra, amikor a felhasználó rekordját a felhasználói adatbázis törlődik.

  -   **Vállalat neve**: Adja meg a cég nevét.

  -   **Vállalat adatvédelmi dokumentumának URL-címe**: Ha a munkahelyi adatvédelmi információkat közzéteszi a hivatkozást, amellyel az interneten, adja meg a hivatkozást, amellyel a felhasználók férhetnek hozzá a vállalati portálról, például http://www.contoso.com/CP_privacy.html. Az adatvédelmi tudnivalók pontos információkkal szolgálhatnak arról, hogy a felhasználók milyen adatokat osztanak meg a munkahellyel.

  -   **Vállalati portál színsémája**: Igény szerint megváltoztathatja a munkahelyi portálok kék az alapértelmezett színét.

  -   **A Configuration Manager-hely kódja**: Adja meg a mobileszközök felügyeletére szolgáló elsődleges hely helykódját.

    > [!NOTE]
    >  A helykód módosítása csak az új regisztrálásokat érinti, a már korábban regisztrált eszközöket nem.

8.  Az a **vállalat kapcsolattartási adatai** adja meg azokat a felhasználók számára megjelenő vállalati kapcsolattartási adatokat **IT-csoport elérhetősége** a vállalati portál alkalmazás. A vállalat kapcsolattartási adatokat, és kattintson a **következő**.

9. Az a **vállalati emblémát** lap, dönthet úgy, hogy emblémák meg a vállalati portálon, és kattintson a **tovább**.

10. Fejezze be a varázslót.

> [!div class="button"]
[< Előző lépés](confirm-dns.md)[következő lépés >  ](terms-and-conditions.md)

