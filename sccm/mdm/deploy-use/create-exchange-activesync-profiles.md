---
title: "Exchange ActiveSync e-mail profilok létrehozása |} Microsoft Docs"
description: "Megtudhatja, hogyan hozza létre és konfigurálja az e-mail profilok a System Center Configuration Manager a Microsoft Intune-nal használható."
ms.custom: na
ms.date: 03/28/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 120442be-179e-450c-a0c4-284046895da3
caps.latest.revision: 4
caps.handback.revision: 0
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 761c3f58f7c57d8f87ee802da37821895062546d
ms.openlocfilehash: bcf337d2abbcd5aad0f99098f6afd4a73ada3a0b
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---

# <a name="exchange-activesync-email-profiles-in-system-center-configuration-manager"></a>Exchange ActiveSync e-mail profilok a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A Microsoft Intune és Exchange ActiveSync használatával állíthat be az eszközökön e-mail profilokat és korlátozások. Ez lehetővé teszi, hogy a felhasználók hozzáférést vállalati e-mailekhez az eszközeiken a lehető legkevesebb beállítás megadásával.  

 A következő eszköztípusokon állíthat be e-mail profilokat:  

- Windows 10
- Windows Phone 8.1
- Windows Phone 8.0
- iOS 5, iOS 6, iOS 7 és iOS 8 rendszerű iPhone-OK  
- iOS 5, iOS 6, iOS 7 és iOS 8 rendszerű Ipadek  
- Samsung KNOX Standard (4 és újabb verziók)
- Android for Work

E-mail profilok központi telepítése az eszközökre, regisztrálnia kell az eszközöket az Intune-ban. Az eszközök beléptetéséről további információért lásd: [Mobileszközök kezelése a Microsoft Intune-nal](https://technet.microsoft.com/en-us/library/dn646962.aspx).

> [!NOTE]
> Az Intune munkahelyi e-mail-profilok, egyet a Gmailes e-mail alkalmazást, és a kilenc munkahelyi e-mail alkalmazást az Android két biztosítja. Ezek az alkalmazások érhetők el a Google Play áruházat, és támogatják a kapcsolatok az Exchange-hez. Ahhoz, hogy az e-mailek működését, telepíthet egy e-mailek alkalmazásokat a felhasználók eszközeire, majd hozzon létre és a megfelelő profilt. Előfordulhat, hogy e-mailek alkalmazásokhoz, például a kilenc munkahelyi nem szabad. Ellenőrizze az alkalmazás részletek licencelési, vagy lépjen kapcsolatba az alkalmazás vállalati bármely kérdésekkel.

 E-mail fiókot az eszközön, másrészt a névjegyek, naptárak és feladatok szinkronizálási beállításokat konfigurálhatja.  

 Az e-mail profilok létrehozásakor számos különféle biztonsági beállítás is megadhat. Ezek a beállítások közé tartozik a System Center Configuration Manager tanúsítványprofilok használatával beállítása a identitáshitelesítési, titkosítási és aláírási tanúsítványokat. További információk a tanúsítványprofilokról: [Tanúsítványprofilok a System Center Configuration Managerben](/sccm/protect/deploy-use/introduction-to-certificate-profiles).    

## <a name="create-an-exchange-activesync-email-profile"></a>Exchange ActiveSync e-mail profil létrehozása  

Profil létrehozása, használhatja az Exchange ActiveSync E-mail profil létrehozása varázsló. 

1.  Kattintson a Configuration Manager konzol **eszközök és megfelelőség**.  

2.  Az a **eszközök és megfelelőség** munkaterületet, bontsa ki a **megfelelőségi beállítások**, bontsa ki a **hozzáférés a vállalati erőforrásokhoz**, és válassza a **E-mail profilok**.  

3.  Az a **Home** lap a **létrehozása** csoportjában válassza **Exchange ActiveSync E-mail profil létrehozása** varázsló elindításához.

4.  Az a **általános** oldalon a varázsló konfigurálja a következőket:

    - **Név**. Adjon meg egy leíró nevet az e-mail profil.

    - **Leírás**. Ha szükséges adjon meg egy leírást, az e-mail profil könnyebben azonosítható legyen a Configuration Manager konzolon.

    - **Az e-mail profil van Android for Work**. Válassza ezt a beállítást, ha az e-mail profil csak munkahelyi eszközök Android rendszer telepít. Ha bejelöli a jelölőnégyzetet, a **által támogatott platformok** varázsló lapja nem jelenik meg. A munkahelyi e-mail-profilok csak Android úgy vannak konfigurálva.

4.  Az a **Exchange ActiveSync** lap a varázslóban adja meg a következő adatokat:  

    -   **Exchange ActiveSync-állomás**. Adja meg a vállalati Exchange server állomásnevét, amely futtatja az Exchange ActiveSync-szolgáltatásokat.  

    -   **Fióknév**. Adja meg az e-mail fiók nevét, a felhasználók eszközein fog látható módon.  

    -   **Fiók felhasználóneve**. Válassza ki, hogyan legyen az e-mail fiók felhasználóneve konfigurálva az ügyféleszközökön. A legördülő listából választhat az alábbi lehetőségek közül:  

        -   **Egyszerű felhasználónév**. A teljes egyszerű felhasználónév használatával jelentkezzen be az Exchange-hez.  

        -   **Fióknév**. Az Active Directory teljes felhasználói fiók nevét használja.

        -   **Elsődleges SMTP-cím**. A felhasználó elsődleges SMTP-címének használatával jelentkezzen be az Exchange-hez.  

    -   **E-mail cím**. Válassza ki, hogy a az e-mail címet a felhasználókhoz egyes ügyféleszközökön hogyan generáljon a rendszer. A legördülő listából választhat az alábbi lehetőségek közül:  

        -   **Elsődleges SMTP-cím**. A felhasználó elsődleges SMTP-címének használatával jelentkezzen be az Exchange-hez.  

        -   **Egyszerű felhasználónév**. A teljes egyszerű felhasználónév használata e-mail címként.  

    -   **Fiók tartománya**. Válasszon egyet az alábbi lehetőségek közül:  

        -   **Lekérés az Active Directoryból**  

        -   **Egyéni**  

         Ez a mező akkor alkalmazható csak akkor, ha **sAMAccountName** kiválasztásakor a **fiók felhasználóneve** legördülő listában.  

    -   **Hitelesítési módszer**. Az Exchange ActiveSync-kapcsolat hitelesítésére használható a következő hitelesítési módszerek közül választhat:  

        -   **Tanúsítványok**. Az identitás tanúsítványának az Exchange ActiveSync-kapcsolat hitelesítéséhez használandó.  

        -   **Felhasználónév és jelszó**. Az eszköz felhasználója kapcsolódni az Exchange ActiveSync jelszót kell megadnia. (A felhasználónév az e-mail profil részeként van konfigurálva.)  

    -   **Identitás tanúsítványa**. Válasszon **válasszon** és válassza ki az identitáshoz használandó tanúsítványt.  

        > [!NOTE]  
        > Az identitás tanúsítványának kiválasztása előtt először konfigurálnia kell az egyszerű tanúsítványigénylési protokoll (SCEP) szerinti tanúsítványprofilként. További információk a tanúsítványprofilokról: [Tanúsítványprofilok a System Center Configuration Managerben](/sccm/protect/deploy-use/introduction-to-certificate-profiles).  

         Ez a beállítás csak akkor, ha úgy döntött, hogy akkor **tanúsítványok** alatt **hitelesítési módszer**.  

    -   **S/MIME használata**. Kimenő e-mailek küldése S/MIME titkosítással. Ez a beállítás csak iOS-eszközökre érvényes. Az alábbi lehetőségek közül választhat:

        -   **Titkosítási tanúsítványok**. Válasszon **válasszon** és válassza ki a titkosításhoz használandó tanúsítványt. Kiválaszthatja, hogy csak egy PFX-tanúsítvány titkosítási tanúsítvány használatára.

        Ha úgy dönt, a titkosítási tanúsítványt, és egy aláíró tanúsítványt, ezek lehet PFX formátumban.

        > [!NOTE]  
        > Tanúsítvány kiválasztása előtt először konfigurálnia kell őket egy SCEP- vagy PFX szerinti tanúsítványprofilként. További információk a tanúsítványprofilokról: [Tanúsítványprofilok a System Center Configuration Managerben](/sccm/protect/deploy-use/introduction-to-certificate-profiles).  

## <a name="configure-synchronization-settings-for-the-exchange-activesync-email-profile"></a>Az Exchange ActiveSync e-mail profil szinkronizálási beállításainak konfigurálása  

Az Exchange ActiveSync e-mail profil létrehozása varázsló **Szinkronizálás beállításainak konfigurálása** lapján adja meg az alábbi adatokat:  

-   **Ütemezés**. Válassza ki azt az ütemezést, amellyel eszközöket szinkronizálja az adatokat az Exchange server kiszolgálóról. Ez a beállítás csak Windows Phone-eszközökre érvényes. A következő lehetőségek közül választhat:  

    -   **Nincs konfigurálva**. Nem érvényes a szinkronizálási ütemezés. Ez lehetővé teszi, hogy a felhasználók a saját szinkronizálási ütemezés konfigurálását.  

    -   **Üzenetek érkezésekor**. Adatok például az e-mailek és a naptári elemek automatikusan szinkronizálható, amikor azok beérkeznek.  

    -   **15 percenként**. Adatok például az e-mailek és a naptári elemek lesznek automatikusan szinkronizálva 15 percenként.  

    -   **30 perc**. Adatok például az e-mailek és a naptári elemek lesznek automatikusan szinkronizálva 30 percenként.  

    -   **60 perc**. Adatok például az e-mailek és a naptári elemek lesznek automatikusan szinkronizálva 60 percenként.  

    -   **Kézi**. Az eszköz felhasználója manuálisan kell kezdeményeznie szinkronizálást.  

-   **Hány napnyi e-mail legyen szinkronizálva**. A legördülő listából válassza ki a szinkronizálni kívánt e-mailek számát. Válasszon egyet az alábbi lehetőségek közül:  

    -   **Nincs konfigurálva**. A beállítás nem lép életbe. Használatával a felhasználók mennyi e-mailek letöltésének az eszközükre.  

    -   **Korlátlan**. Az összes elérhető e-mail szinkronizálása.  

    -   **1 nap**  

    -   **3 nap**  

    -   **1 hét**  

    -   **2 hét**  

    -   **1 hónap**  

-   **Üzenetek más e-mail fiókba történő áthelyezésének engedélyezése**. Válassza ezt a beállítást, hogy a felhasználók e-mailek áthelyezését az eszközön konfigurált más fiókokba. Ez a beállítás csak iOS-eszközökre érvényes.  

-   **E-mailek, harmadik féltől származó alkalmazásokból küldésének engedélyezése**. Válassza ezt a beállítást, így a felhasználók nem alapértelmezett, harmadik féltől származó e-mail alkalmazásokból küldjenek e-mailt. Ez a beállítás csak iOS-eszközökre érvényes.  

-   **Legutóbb használt e-mail címek szinkronizálása**. Válassza ezt a beállítást, az eszközön legutóbb használt e-mail címek listájának szinkronizálásához. Ez a beállítás csak iOS-eszközökre érvényes.  

-   **SSL használata**. Válassza ezt a beállítást, a Secure Sockets Layer (SSL) kommunikáció használata az e-mailek küldésekor, fogadásakor és az Exchange server kiszolgálóval való kommunikációhoz.  

-   **Szinkronizálandó tartalomtípus**. Válassza ki az eszközökre szinkronizálni kívánt tartalomtípusokat. Ez a beállítás csak Windows Phone-eszközökre érvényes. A következő lehetőségek közül választhat:  

    -   **E-mail**  

    -   **Névjegyek**  

    -   **Naptár**  

    -   **Feladatok**  

## <a name="specify-supported-platforms-for-the-exchange-activesync-email-profile"></a>Adja meg az Exchange ActiveSync e-mail profil által támogatott platformok  

1.  Az a **által támogatott platformok** lapon válassza ki az operációs rendszerek, amelyek az e-mail profilt telepíteni fogja az Exchange ActiveSync E-mail profil létrehozása varázsló. Válassza ki vagy **válassza ki az összes** kattintva telepítheti az e-mail profilt az összes rendelkezésre álló operációs rendszeren.  

2.  Fejezze be a varázsló futtatását.

Az Exchange ActiveSync e-mail profil telepítésével kapcsolatos információkért lásd: [profilok a System Center Configuration Manager központi telepítése](../../protect/deploy-use/deploy-wifi-vpn-email-cert-profiles.md).  

