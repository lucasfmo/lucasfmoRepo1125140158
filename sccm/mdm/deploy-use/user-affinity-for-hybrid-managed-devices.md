---
title: "A hibrid felhasználókapcsolat felügyelt eszközöket a Configuration Manager |} Microsoft Docs"
description: "A felügyelt eszközök felhasználói affinitás konfigurálása a Configuration Managerben."
ms.custom: na
ms.date: 03/05/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b5d520a7-e9e5-40ee-91f9-f2684214beb6
caps.latest.revision: 6
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: d039792a88b9e7704f37718a88f841dd9216d1b1
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="user-affinity-for-hybrid-managed-devices-in-configuration-manager"></a>A hibrid felhasználókapcsolat kezelt eszközökre a Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A vállalati tulajdonú eszközök profilok konfigurálásakor a rendszergazda adhat meg, hogy lehet-e a kezelt eszközök *felhasználókapcsolat* amely azonosítja az egy adott felhasználó az eszközhöz.  

##  <a name="BKMK_iOSCP"></a>Felügyelt felhasználói affinitással rendelkező eszközök  
 A **user affinity** konfigurált eszközökön az alkalmazások letöltéséhez és az eszközök felügyeletéhez a Vállalati portál alkalmazást is telepítheti és futtathatja. Miután a felhasználók megkapják az eszközeiket, több további lépést kell végrehajtaniuk a Telepítősegéd befejezéséhez és a vállalati portál alkalmazás telepítéséhez el kell végezniük.  

#### <a name="how-to-enroll-ios-devices-with-user-affinity"></a>Felhasználói affinitással rendelkező iOS-eszközök regisztrálása  

1.  Amikor a felhasználók először az új eszközökön, meg kell végrehajtaniuk a Telepítősegéd befejezéséhez. A beléptetési profilt a telepítés során bekéri a hitelesítő adatokat adhat meg. Felhasználók felhasználóknak az Intune-előfizetésükhöz tartozó hitelesítő (azaz az egyedi felhasználónevüket vagy UPN) kell használnia.  

2.  A telepítés során is is lehet kéri a felhasználóktól az Apple ID azonosítóra. Az Apple ID Azonosítót meg kell adni, az eszköz a vállalati portál telepítése előtt. A felhasználók megadhatják az Apple ID Azonosítót telepítés az IOS befejezése után **beállítások** menü.  

3.  Telepítés befejezése után az iOS-eszközön telepíteni kell a vállalati portál alkalmazást az App Store áruházból, például [vállalati portál alkalmazás](https://itunes.apple.com/us/app/id719171358).  

4.  A felhasználó ekkor bejelentkezhet a vállalati portálhoz, a megadott egyszerű felhasználónév az eszköz beállítása során is.  

5.  A bejelentkezés után a rendszer kérni fogja a felhasználótól az eszköz regisztrálását. Ennek első lépése az **eszköz azonosítása**. Az alkalmazás megjeleníti a végfelhasználók Intune-fiókhoz rendelt és a vállalat által birtokolt iOS-eszközök listáját. Válassza ki a megfelelő eszközt.  

     Ha az eszköz már nem a vállalat által birtokolt, jelölje be az "új eszköz" folytatja a normál regisztrálási folyamata.  

6.  A következő képernyőn a felhasználónak meg kell erősítenie az új eszköz sorozatszámát. A felhasználó a „sorozatszám megerősítése” hivatkozásra koppintva indíthatja el a beállítási alkalmazást a sorozatszám ellenőrzéséhez. A felhasználónak ezután meg kell adnia a sorozatszám utolsó 4 számjegyét a Vállalati portál alkalmazásban.  

     Ez a lépés azt ellenőrzi, hogy az eszköz az Intune-ban regisztrált vállalati eszköz-e. Ha az eszközön található sorozatszám nem egyezik, nem a megfelelő eszköz választotta ki. Lépjen vissza az előző képernyőre, és egy másik eszköz kiválasztásához.  

7.  A sorozatszám ellenőrzése után a vállalati portál alkalmazás átirányítja a felhasználókat a vállalati portál webhelyre a regisztrálás véglegesítéséhez, és megkéri a felhasználót az alkalmazáshoz való visszatérésre.  

8.  Ezzel befejeződött a regisztráció. Ezután az összes funkciójával együtt használhatja az eszközt.  

##  <a name="BKMK_noUA"></a>Felhasználói affinitás nélkül kezelt eszközök  
 A **no user affinity** konfigurált eszközök nem támogatják a Vállalati portált, ezért ezekre az eszközökre ne telepítse az alkalmazást. A Vállalati portál az olyan felhasználók számára készült, akik rendelkeznek vállalati hitelesítő adatokkal, és hozzá kell férniük a személyre szabott vállalati erőforrásokhoz (pl. az e-mailhez). A **felhasználói affinitás nélkül** beléptetett eszközökhöz nem tartozhat dedikált felhasználói bejelentkezés. A felhasználói affinitás nélkül regisztrált eszközök jellemző példái közé tartoznak a kioszkok, a pénztári eszközök (POS) és a megosztott segédeszközök. Ha szükség van a felhasználói affinitás használatára, az eszköz beléptetése előtt adja meg a **Felhasználói affinitás** beállítást az eszközbeléptetési profilban. Módosítja az affinitási állapotot, az eszközön, kivonás, és újból regisztrálja az eszközt.

