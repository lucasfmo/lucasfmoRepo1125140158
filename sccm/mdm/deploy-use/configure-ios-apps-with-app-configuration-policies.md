---
title: "IOS-alkalmazások konfigurálása alkalmazás-konfigurációs házirendek |} Microsoft Docs"
description: "Kiiktathatja iOS 8 vagy újabb rendszerű eszközök még alkalmazások futtatása előtt alkalmazáskonfigurációs szabályzatok telepítésével a felhasználók számára a konfigurációs problémákat."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f0a78038-ea22-4826-9c07-1771b7dd2e8d
caps.latest.revision: 18
caps.handback.revision: 0
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 23b1d24e908d04b64c3bbfa518793a44e696d468
ms.openlocfilehash: 50aea2afaf34974ca92ac58b6569bff56403a9ab
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="apply-settings-to-ios-apps-with-app-configuration-policies-in-system-center-configuration-manager"></a>Beállítások alkalmazása az iOS-alkalmazások az alkalmazáskonfigurálási szabályzatokkal a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


Segítségével alkalmazáskonfigurációs szabályzatok a System Center Configuration Manager (a Configuration Manager) terjesztése a beállításokat, amelyekre szükség lehet, amikor egy felhasználó egy alkalmazást futtat. Például egy alkalmazás kérheti a felhasználót, hogy adja meg ezeket az adatokat:
- Egyéni portszám
- Nyelvi beállítások
- Biztonsági beállítások
- Márkajelzési beállítások, például a vállalat logója

Ha a felhasználó adja meg a beállításokat nem megfelelő, a teher javítsa ki a támogatási szolgálat esik, és alkalmazástelepítés lassú.
Segítségével megakadályozható, hogy az ilyen problémák, alkalmazás-konfigurációs házirendek segítségével szükséges beállításokat telepíthet a felhasználók számára, az alkalmazás futtatása előtt. A beállítások automatikusan társítva a felhasználó. A felhasználónak nem kell semmilyen művelet végrehajtására.
A Configuration Managerben az alkalmazás-konfigurációs házirend használata helyett a konfigurációs házirendek telepítésének közvetlenül a felhasználók és eszközök számára, hogy házirend társítása egy központi telepítési típus az alkalmazás központi telepítésekor. Amikor egy alkalmazás keresi azokat (általában az első az alkalmazás futtatásakor), a rendszer alkalmazza a házirend-beállításokat.

Alkalmazás-konfigurációs házirendek jelenleg csak 8 és újabb verziók iOS rendszerű eszközökön, és ezek alkalmazás esetében érhető el:

- **Alkalmazáscsomag iOS rendszerhez (*.ipa-fájl)**
- **Alkalmazáscsomag az iOS App Store-ból**

Alkalmazástelepítés-típusokról kapcsolatos további információkért tekintse meg a [Alkalmazáskezelés bemutatása](/sccm/apps/understand/introduction-to-application-management).

## <a name="create-an-app-configuration-policy"></a>Alkalmazás-konfigurációs házirend létrehozása

1. Kattintson a Configuration Manager konzol **szoftverkönyvtár** > **Alkalmazáskezelés** > **alkalmazáskonfigurációs szabályzatok**.
2. Az a **Home** lap a **alkalmazáskonfigurációs szabályzatok** csoportjában válassza **új alkalmazáskonfigurációs szabályzat létrehozása**.
3. Az alkalmazás konfigurációs szabályzat létrehozása varázsló a a **általános** lapján állítsa be a házirend adatait:
  - **Név**. Adjon meg egy egyedi nevet a házirend.
  - **Leírás**. (Választható) Könnyebben azonosíthatja a házirend, egy leírást is hozzáadhat.
  - **Kategóriák a Keresés és szűrés javítása érdekében hozzárendelt**. (Választható) Hozzon létre és kategóriák hozzárendelése a házirendet, válassza a **kategóriák**. Kategóriák könnyebben rendezési és keresési elemek a Configuration Manager konzolon.
4. Az a **iOS-házirend** lapon, válassza ki a konfigurációs házirenddel kapcsolatos információk beállítása:
  - **Adja meg a név-érték párok**. Ez a beállítás használható tulajdonságlista-fájlok, amelyek nem használnak beágyazásakor.

      *Adjon meg egy név-érték párt a*
        1. Adhatja hozzá egy új kulcspár **új**.
        2. Az a **név-érték pár hozzáadása** párbeszédpanelen adja meg a következőket:
            - **Típus**. A listában jelölje ki, hogy meg szeretné határozni érték típusa.
            - **Név**. Adja meg a legyen értéket lista tulajdonságkulcs nevét.
            - **Érték**. Adja meg, amelyek érvényesek a megadott kulcs értékét.

  - **Keresse meg a tulajdonságlista-fájlokban**. Használja ezt a beállítást, ha már rendelkezik az alkalmazás konfigurációs XML-fájl, vagy az összetettebb, beágyazást használó fájlok.

    *Tallózással keresse meg a tulajdonságlista-fájl*

      1.  Az a **Alkalmazáskonfigurálási szabályzat** mezőbe írja be a tulajdonságlista-adatainak XML formátuma helytelen.

      XML-tulajdonságlistákkal kapcsolatos további információért lásd: [Understanding XML Property Lists](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html) az IOS Developer Library.

Az XML-tulajdonságlista formátuma a konfigurált alkalmazás függ. A formátum használatára vonatkozó további információért forduljon az alkalmazás szállítójához.
Az Intune a következő adattípusokat támogatja a tulajdonságlistákban:
            
            ```
            <integer>
            <real>
            <string>
            <array>
            <dict>
            <true /> or <false />
            ```
Az adattípusokkal kapcsolatban további információkért lásd: [kapcsolatos Property Lists](https://developer.apple.com/library/content/documentation/Cocoa/Conceptual/PropertyLists/AboutPropertyLists/AboutPropertyLists.html) az IOS Developer Library.
Intune-ban is a következő tokentípusokat támogatja a tulajdonságlistában:
            
            ```
            {{userprincipalname}} - (Example: John@contoso.com)
            {{mail}} - (Example: John@contoso.com)
            {{partialupn}} - (Example: John)
            {{accountid}} - (Example: fc0dc142-71d8-4b12-bbea-bae2a8514c81)
            {{deviceid}} - (Example: b9841cd9-9843-405f-be28-b2265c59ef97)
            {{userid}} - (Example: 3ec2c00f-b125-4519-acf0-302ac3761822)
            {{username}} - (Example: John Doe)
            {{serialnumber}} - (Example: F4KN99ZUG5V2) for iOS devices
            {{serialnumberlast4digits}} - (Example: G5V2) for iOS devices
            ```

A {{és}} karaktereket csak használja, és más célokra nem használhatók.
            
5. Válassza ki a korábban létrehozott XML-fájl importálásához **fájl kijelölése**.
6. Válasszon **következő**. Ha nincsenek hibák az XML-kódban, összekapcsolta a folytatás előtt javítsa ki őket.
7. Fejezze be a varázsló bemutatott lépések.

Az új konfigurációs házirend látható a **szoftverkönyvtár** munkaterületen, a a **alkalmazáskonfigurációs szabályzatok** csomópont.

## <a name="associate-an-app-configuration-policy-with-a-configuration-manager-application"></a>Alkalmazás-konfigurációs házirend társítása Configuration Manager-alkalmazással

Az alkalmazás-konfigurációs házirend társítása egy iOS-alkalmazás központi telepítését, az alkalmazás központi telepítése a szokásos módon az eljárás használatával a [telepíthet központilag alkalmazásokat](/sccm/apps/deploy-use/deploy-applications) témakör.

A szoftver központi telepítése varázslóban meg a **alkalmazáskonfigurációs szabályzatok** lapon, válassza ki **új**. Az a **Alkalmazáskonfigurálási szabályzat kiválasztása** párbeszédpanelen válassza ki azokat az alkalmazás központi telepítési típust, és a konfigurációs házirend, amelyet szeretne társítja azt.
Ha telepítve van a központi telepítési típus, az alkalmazás konfigurációs házirend-beállítások automatikusan alkalmazva.

## <a name="example-format-for-the-mobile-app-configuration-xml-file"></a>A mobilalkalmazás-konfigurációs XML-fájl példaformátuma

Mobilalkalmazás-konfigurációs fájl létrehozásakor ezt a formátumot segítségével adjon meg legalább egy, a következő értékeket:

```
<dict>
  <key>userprincipalname</key>
  <string>{{userprincipalname}}</string>
  <key>mail</key>
  <string>{{mail}}</string>
  <key>partialupn</key>
  <string>{{partialupn}}</string>
  <key>accountid</key>
  <string>{{accountid}}</string>
  <key>deviceid</key>
  <string>{{deviceid}}</string>
  <key>userid</key>
  <string>{{userid}}</string>
  <key>username</key>
  <string>{{username}}</string>
  <key>serialnumber</key>
  <string>{{serialnumber}}</string>
  <key>serialnumberlast4digits</key>
  <string>{{serialnumberlast4digits}}</string>
  <key>udidlast4digits</key>
  <string>{{udidlast4digits}}</string>
</dict>
```

