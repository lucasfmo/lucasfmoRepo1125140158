---
title: "A Lookout munkahelyi alkalmazás telepítéséhez |} Microsoft Docs"
description: "Konfigurálhatja és telepítheti a Lookout a munkahelyi alkalmazásokhoz."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3f62b763-4347-453d-b0a7-1f4a0d1d4105
caps.latest.revision: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: 59f43c922d1d3bc64625733014b0def1e42c4d2d
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="configure-and-deploy-lookout-for-work-apps"></a>Konfigurálhatja és telepítheti a Lookout munkahelyi alkalmazások

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ez a cikk azt ismerteti, hogyan konfigurálhatja és telepítheti a Lookout munkahelyi alkalmazás Android és iOS-eszközökhöz.

## <a name="android-google-play-store-app"></a>Android (Google Play Store-alkalmazás)
1.  Kattintson a Configuration Manager konzolon **szoftverkönyvtár** > **Alkalmazáskezelés** > **alkalmazások**.

2.  A Szoftver központi telepítése varázsló **Általános** lapján adja meg az alábbi adatokat:
  * Írja be: a select **alkalmazáscsomag az Androidhoz a Google Playről**.
  * Hely: a Lookout for work alkalmazásra mutató hivatkozás másolása, illessze be ide a Google Play áruházból
  * Közzétevő: A lookout mobilbiztonsági
  * Név: A lookout for Work
  * Leírás: A lookout mobil ellen, hogy az eszköz biztonsága a legjobb védelmet nyújt. Ha a Lookout alkalmazás telepítve van az eszközön, az alkalmazás védelmet nyújt az eszköz fenyegetésekkel szembeni hatékony, és riasztást küld, és a vállalati rendszergazda, a megtalált.
  * Felügyeleti kategória: Számítógép-kezelés

  Sikeres befejezését követően megjelenik a Lookout munkahelyi alkalmazás elemre az alkalmazások.

3.  A a **Home** lap a **telepítési** csoportjában válassza **telepítés** keressen olyan munkahelyi alkalmazás telepítése a felhasználók számára.
>[!IMPORTANT]
>Ugyanazokat a felhasználókat a beléptetési lehetőséget a Lookout MTP-konzolon egészül ki kell választania.

  Válassza ki a **kötelező telepítés** beállítással kötelezővé teheti, hogy a felhasználó eszközén telepíthető a Lookout alkalmazás segítségével.

## <a name="ios-enterprise-signed-version-of-lookout-app"></a>iOS (vállalat által aláírt verzióját a Lookout alkalmazás)

* **1. lépés:** Győződjön meg arról, hogy **IOS-eszközök kezelését** be van állítva az eszközön. További információk az hogyan állíthatja az eszközt az IOS-eszközök kezelését, lásd: [iOS és Mac-Eszközkezelés beállítása]().

* **2. lépés:** **Írja alá újra** keressen olyan munkahelyi iOS-alkalmazás. A lookout osztja el a munkahelyi iOS-alkalmazást az iOS App Store kívül a Lookout. **Az alkalmazás terjesztése előtt**, újra kell aláírni az alkalmazás az iOS vállalati fejlesztői tanúsítványával. Keressen olyan munkahelyi iOS-alkalmazások újbóli aláírása részletes utasításokért lásd: [újból aláírhatják a folyamat a munkahelyi iOS-alkalmazást a Lookout](https://personal.support.lookout.com/hc/en-us/articles/114094038714) a Lookout helyen.


* **3. lépés:** Az iOS-felhasználók Azure Active Directory-hitelesítés engedélyezése a következő módon:
  1.  Jelentkezzen be a [Azure Active Directory felügyeleti portálon](https://manage.windowsazure.com), és nyissa meg az alkalmazás a lapot.
  2.  Adja hozzá a **munkahelyi iOS-alkalmazást a Lookout** , egy **natív ügyfélalkalmazás**.
  ![a native client alkalmazást pontját megjelenítő add apps párbeszédpanel képernyőképe](media/aad-add-app.png)

  3. Cserélje le a **com.lookout.enterprise.yourcompanyname** az ügyfél a csomagot kijelölt során az IPA azonosítója.
  4.  Adja hozzá a további átirányítási URI-ja:  **&lt;companyportal://code/ >** az eredeti átirányítási URI-t egy URLencoded verziója követ.
  5.  Adja hozzá **delegált engedélyekkel** az alkalmazáshoz.

  További részletekért lásd: [natív ügyfélalkalmazás konfigurálása](https://azure.microsoft.com/en-us/documentation/articles/app-service-mobile-how-to-configure-active-directory-authentication/#optional-configure-a-native-client-application).


* **4. lépés:** A újra aláírt .ipa-fájl feltöltése, lásd: a [iOS-alkalmazások létrehozása a System Center Configuration Manager témakör](https://docs.microsoft.com/en-us/sccm/apps/get-started/creating-ios-applications) témakör. Állítsa be az operációs rendszer minimális verziója iOS 8.0-s vagy újabb.


* **5. lépés:** A kezelt alkalmazás-konfigurációs házirend létrehozása leírtak szerint a [iOS-alkalmazások konfigurálása mobilalkalmazás-konfigurációs házirendek a System Center Configuration Managerben](https://docs.microsoft.com/en-us/sccm/apps/deploy-use/configure-ios-apps-with-app-configuration-policies) témakör.


* **6. lépés:** **Az alkalmazás központi telepítése a felhasználók számára**, válassza ki a Lookout munkahelyi alkalmazás a **alkalmazások** lap, a a **Home** lap a **központi telepítési** csoportjában válassza **központi telepítése**.

  Ki kell választania a beléptetési lehetőséget a Lookout konzolján felvett ugyanazokat a felhasználókat.  
Válassza ki a **kötelező telepítés** beállítással kötelezővé teheti, hogy a felhasználó eszközén telepíthető a Lookout alkalmazás segítségével.

## <a name="what-happens-when-the-deployed-app-is-opened-on-the-device"></a>Mi történik, ha a telepített alkalmazás meg van nyitva, az eszközön




Amikor a felhasználó megnyitja a Lookout for Work az eszközön meg kell aktiválja az alkalmazást, majd válassza ki a be kell jelentkezniük az Azure Active Directory lehetőséget. Részletes bemutatóért a végfelhasználói folyamat a következő témakörökben található:

* [Android-eszközön a Lookout for Work telepítésére kéri](http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

* [Hárítsa el a Lookout for Work Android-eszközön található fenyegetést szeretne](http://docs.microsoft.com/intune/enduser/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)

## <a name="next-steps"></a>További lépések
* [Az eszköz threat protection-szabályt a megfelelőségi szabályzat engedélyezése](enable-device-threat-protection-rule-compliance-policy.md)

