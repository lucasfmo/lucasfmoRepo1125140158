---
title: "Erősítse meg a tartománynevekre vonatkozó követelményeknek a System Center Configuration Manager |} Microsoft Docs"
description: "Erősítse meg a tartománynevekre vonatkozó követelményeknek a System Center Configuration Managerrel."
ms.custom: na
ms.date: 03/21/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 522c2e82-20eb-4f38-859b-d55640b24e32
caps.latest.revision: 18
caps.handback.revision: 0
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 1b9e49da1a5bbfca93fe683b82d2c0056a22cc1f
ms.openlocfilehash: 35b24294073956a6bdb14cae07705f56d31e00a9
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="confirm-domain-name-requirements-with-system-center-configuration-manager-and-microsoft-intune"></a>Erősítse meg a tartománynevekre vonatkozó követelményeknek a System Center Configuration Manager és a Microsoft Intune

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ha szükséges, a következő lépésekkel függőségek teljesítéséhez külső a Configuration Manager:

1. Minden felhasználóhoz rendelt eszközök regisztrálása az Intune-licencet kell rendelkeznie. Intune-licenceket rendelhetnek a felhasználókhoz rendelni minden felhasználónak rendelkeznie kell egy egyszerű felhasználónév (UPN), amely nyilvánosan feloldható (például johndoe@contoso.com) vagy az Azure Active Directoryban konfigurált másodlagos bejelentkezési Azonosítóval. Másodlagos bejelentkezési Azonosítóval beállítása lehetővé teszi a felhasználóknak jelentkezzen be egy e-mail címet, például, akkor is, ha az egyszerű Felhasználónevük NetBIOS formátumban (például contoso\budaipeter).

  - Ha a vállalat használ nyilvánosan feloldható UPN-EK (azaz johndoe@contoso.com), nem igényel további konfigurálást.
  - Ha a vállalata nem feloldható egyszerű felhasználónév (azaz contoso\budaipeter) használ, meg kell [a másik azonosító konfigurálása az Azure Active Directoryban](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-get-started-custom/#pages-under-the-section-sync).

2.  Telepítheti és konfigurálhatja az Active Directory összevonási szolgáltatások (AD FS). (opcionális)

     Ha beállít egyszeri bejelentkezést, a felhasználók bejelentkezhetnek vállalati hitelesítő adataikkal a szolgáltatásokat az Intune-ban.

     További információ a következő témakörökben:
    -   [Egyszeri bejelentkezés előkészítése](http://go.microsoft.com/fwlink/?LinkID=271124)
    -   [Tervezése és telepítése az AD FS 2.0 használatra az egyszeri bejelentkezést.](http://go.microsoft.com/fwlink/?LinkID=271125)

3.  Címtár-szinkronizálás telepítése és konfigurálása

     A címtár-szinkronizálás lehetővé teszi az Intune feltöltése a szinkronizált felhasználói fiókok. A szinkronizált felhasználói fiókok és biztonsági csoportok kerülnek az Intune-hoz. Gyakran a címtár-szinkronizálás engedélyezésének elmulasztása okozza azt, hogy az eszközöket nem sikerül regisztrálni a Configuration Manager-alapú mobileszköz-felügyelet Microsoft Intune-nal való beállítása során.

     További információ: a [Címtár-integráció áttekintése](http://go.microsoft.com/fwlink/?LinkID=271120) az Active Directory dokumentációs könyvtárában.

4.  Nem kötelező, nem ajánlott: Ha nem használ Active Directory összevonási szolgáltatások, állítsa vissza a felhasználók Microsoft Online-jelszavát.

     Ha nem használja az AD FS szolgáltatást, mindegyik felhasználó részére Microsoft Online jelszót kell beállítani.

> [!div class="button"]
[< Előző lépés](create-mdm-collection.md)[következő lépés >  ](configure-intune-subscription.md)

