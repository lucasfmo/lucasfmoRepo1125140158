---
title: "Wi-Fi profilok létrehozása |} Microsoft Docs"
description: "Útmutató: a Wi-Fi profilok használatával a System Center Configuration Managerben a szervezethez tartozó felhasználók vezeték nélküli hálózati beállításokat telepíthet."
ms.custom: na
ms.date: 12/11/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 321b19b2-a093-4b8f-995f-41f74b886eb5
caps.latest.revision: 13
caps.handback.revision: 0
author: arob98
ms.author: angrobe
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: f1ae976899de1fd3efcbde0c7268f071a5d0218b
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="create-wi-fi-profiles"></a>Wi-Fi profilok létrehozása

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


Wi-Fi profilok használatával a System Center Configuration Managerben a szervezethez tartozó felhasználók vezeték nélküli hálózati beállításokat telepíthet. Ezen beállítások telepítésével, megkönnyíti a felhasználók számára a Wi-Fi csatlakozni.  

 Például hogy minden iOS-eszközön való csatlakozáshoz engedélyezni kívánt Wi-Fi hálózat. A vezeték nélküli hálózathoz való kapcsolódáshoz szükséges beállításokat tartalmazó Wi-Fi profil létrehozása. Ezt követően a profilt minden felhasználó számára telepíti, amelyek a hierarchiában lévő iOS-eszközök rendelkeznek. Az iOS-eszközök felhasználói látják majd a vezeték nélküli hálózatok listájában a vállalati hálózatot, és egyből tudnak kapcsolódni a hálózathoz.  

 A Wi-Fi profilokkal a következő eszközök konfigurálhatóak:  

-   A Windows 8.1 32 bites verzióját futtató eszközök  

-   A Windows 8.1 64 bites verzióját futtató eszközök  

-   Windows RT 8.1 rendszerű eszközök  

-   A Windows 10 asztali vagy mobil verzióját futtató eszközök  

[Mobil eszközök Wi-Fi profilok létrehozása](../../mdm/deploy-use/create-wifi-profiles.md) információkat nyújt azokról a mobileszköz-felhasználók vezeték nélküli hálózati beállításokat telepíthet a Configuration Manager Wi-Fi profilok használata. "

> [!IMPORTANT]  
>  Android, iOS, Windows Phone és beléptetett Windows 8.1 vagy újabb rendszerű eszközök profilokat telepíteni, ezek az eszközök Microsoft Intune-ban regisztrált kell. Az eszközök regisztrálása beolvasásával kapcsolatos információkért lásd: [eszközök regisztrálása az Intune-ban felügyeletre](https://docs.microsoft.com/intune/deploy-use/enroll-devices-in-microsoft-intune).  

 Wi-Fi profil létrehozásakor egy sor biztonsági beállítás is megadható a profilban. Ezek közé tartozik a kiszolgáló-ellenőrzési és ügyfél-hitelesítési tanúsítványok, amelyek a Configuration Manager tanúsítványprofilok használatával értesítését. További információk a tanúsítványprofilokról: [Tanúsítványprofilok a System Center Configuration Managerben](introduction-to-certificate-profiles.md).  

## <a name="create-a-wi-fi-profile"></a>Wi-Fi profil létrehozása  

1.  Kattintson a Configuration Manager konzol **eszközök és megfelelőség** > **megfelelőségi beállítások** >  **hozzáférés a vállalati erőforrásokhoz** > **Wi-Fi profilok**.  

3.  Az a **Home** lap a **létrehozása** csoportjában válassza **Wi-Fi profil létrehozása**.  

1.  Az a **általános** lapján adjon meg egy egyedi nevet és a Wi-Fi profil leírását.  Ha egy másik Wi-Fi profil beállításait használná, válassza a **Létező wifi-profilelem importálása fájlból** lehetőséget.  

    > [!IMPORTANT]  
    >  Az importált Wi-Fi profilnak érvényes XML-t kell tartalmaznia egy Wi-Fi profilra vonatkozóan. A Configuration Manager nem érvényesíti a profilt, amikor importálja a fájlt.  

3.  A **meg nem felelés súlyossága jelentésekhez**, milyen súlyossági szintről készüljön jelentés, ha a Wi-Fi profil kiderül, hogy nem megfelelő az ügyféleszközökön (például, ha a profil telepítése sikertelen lesz), adja meg. A használható súlyossági szintek a következők:  

    -   **Nincs**: A megfelelőségi szabályt nem teljesítő számítógépek nem kerül a hiba súlyossága a Configuration Manager-jelentések.  

    -   **Információk**: A megfelelőségi szabályt nem teljesítő számítógépek a jelentés a súlyosságot **információk** a Configuration Manager jelentésekben.  

    -   **Figyelmeztetés**: A megfelelőségi szabályt nem teljesítő számítógépek a jelentés a súlyosságot **figyelmeztetés** Configuration Manager jelentések.  

    -   **Kritikus**: A megfelelőségi szabályt nem teljesítő számítógépek a jelentés a súlyosságot **kritikus** a Configuration Manager jelentésekben.  

    -   **Kritikus eseménnyel**: A megfelelőségi szabályt nem teljesítő számítógépek a jelentés a súlyosságot **kritikus** a Configuration Manager jelentésekben. Ezt a súlyossági szintet az alkalmazás eseménynaplója is rögzíti Windows-eseményként.  

1.  Az a **Wi-Fi profil** oldalon adja meg a nevét, amely eszközöket jelenít meg a hálózat neveként.  

    > [!IMPORTANT]  
    >  A Configuration Manager nem támogatja az aposztróf (**â "˜**) és a vessző (**,**) karakterek használatát a hálózat nevében.  

2.  Adja meg a kis-és nagybetűket **SSID**
3.  Válassza ki a többi megfelelő kapcsolati lehetőségek, többek között.   **Csatlakozás, ha a hálózat nem teszi közzé a nevét (SSID)**, ha lehetséges, hogy van-e rejtve az SSID  

4.  Az a **biztonsági konfiguráció** lapon, válassza ki, hogy a vezeték nélküli hálózat által használt, vagy válassza ki a biztonsági protokoll **nincs hitelesítés (nyílt)** Ha a hálózat nem biztonságos.
    > [!IMPORTANT]  
    >  Ha a Wi-Fi profilt hoz létre\-helyszíni mobileszköz-kezelés, a Configuration Manager aktuális ágának csak a következő Wi-Fi biztonsági konfigurációkat támogatja:  
    >   
    >  Biztonsági típusok: **WPA2-Enterprise** vagy **WPA2-Personal**  
    > Titkosítási típusok: **AES** vagy **TKIP**  
    > EAP-típusok: **Intelligens kártya vagy egyéb tanúsítvány** vagy **PEAP**  

    > Android-eszközök esetén a biztonsági típusok **WPA-Personal**, **WPA2 személyes** és **WEP** nem támogatottak.  

2.  Adja meg a vezeték nélküli hálózat által használt titkosítási módszert.  

3.  Adja meg a vezeték nélküli hálózatnál a hitelesítéshez használt EAP-típust.  

     Csak Windows Phone-eszközök esetén: a **LEAP** és az **EAP-FAST** EAP-típusok nem támogatottak.  

4.  A **Konfigurálás** gombra kattintva adhatja meg a kiválasztott EAP-típus tulajdonságait. Előfordulhat, hogy egyes kiválasztott EAP-típusoknál ez a beállítás nem használható.  

    > [!IMPORTANT]  
    >  Amikor a **Konfigurálás** gombra kattint, a megjelenő párbeszédpanel a Windows rendszerhez tartozó párbeszédpanel. Emiatt biztosítania kell, hogy a Configuration Manager-konzol támogatja a kiválasztott EAP-típus konfigurálását futtató számítógép operációs rendszerének.  
    >   
    >  Ha iOS-eszközök esetén nem EAP-módszert használ a hitelesítéshez, a csatlakozáshoz az MS-CHAP v2-t használja a rendszer a kiválasztott módszertől függetlenül.  

5.  Ha szeretné tárolni a felhasználói hitelesítő adatokat, hogy a felhasználóknak ne kelljen minden bejelentkezéskor megadnia azokat, jelölje be a **Felhasználói hitelesítő adatok megjegyzése minden bejelentkezéskor** beállítást.  

6. **IOS-eszközök esetén:**  
 Konfigurálja a Wi-Fi kapcsolathoz esetleg szükséges tanúsítványok adatait. Az ügyféltanúsítványt és vagy a megbízható kiszolgáló tanúsítványának nevét, vagy a főtanúsítványt a következők szerint kell konfigurálni:  

    -   **Megbízható kiszolgálók tanúsítványainak nevei**: Ha a kiszolgálót, amely az eszköz csatlakozik, olyan kiszolgálói hitelesítési tanúsítványt használ a kiszolgáló azonosítására, illetve a kommunikációs csatorna védelmére, adja meg vagy neveit, hogy certificateâ "™ s tulajdonos neve vagy a tulajdonos alternatív neve. A név általában a kiszolgáló teljes tartományneve. Ha például a kiszolgálói tanúsítvány köznapi neve a tulajdonosnál srv1.contoso.com, az **srv1.contoso.com** nevet adja meg. Ha a kiszolgálói tanúsítványhoz a tulajdonos alternatív neveként több név is meg van adva, adja meg a neveket egymástól pontosvesszővel elválasztva.  

    > [!TIP]  
    >  Ha az iOS rendszerrel működő eszközhöz EAP alapú vagy ügyfél-hitelesítéshez kiválasztott ügyféltanúsítvánnyal RADIUS-kiszolgálón (például a hálózati házirend-kiszolgálót futtató kiszolgálón) történik hitelesítés, a tulajdonos alternatív nevét kell beállítania egyszerű felhasználónévként.  

    -   **Főtanúsítványok kiválasztása a kiszolgálóérvényesítéshez**: Ha a kiszolgálót, amely az eszköz csatlakozik, olyan kiszolgálói hitelesítési tanúsítványt, amely az eszköz nem tekint megbízhatónak, válassza ki a megbízható tanúsítványlánc létrehozásához az eszközön a kiszolgálói tanúsítványhoz tartozó főtanúsítványt tartalmazó tanúsítványprofilt.  

    -   **Válasszon ügyféltanúsítványt az ügyfél-hitelesítéshez**: Ha a kiszolgáló vagy a hálózati eszköz ügyféltanúsítványt a csatlakozó eszköz hitelesítéséhez, válassza ki az ügyfél-hitelesítési tanúsítványt tartalmazó tanúsítványprofilt.  

    > [!NOTE]  
    >  Ahhoz, hogy a főtanúsítványt és az ügyféltanúsítványt ki tudja választani, előbb tanúsítványprofilként kell azokat konfigurálnia és telepítenie. További információk a tanúsítványprofilokról: [Tanúsítványprofilok a System Center Configuration Managerben](introduction-to-certificate-profiles.md).  

7.  Az a **speciális beállítások** adja meg azokat a hitelesítési módot, az egyszeri bejelentkezésre vonatkozó beállításokat, és a FIPS megfelelőségi például a Wi-Fi profil speciális beállításainak megadása. További információt ezekről a beállításokról a Windows dokumentációjában talál. A speciális beállításokat és azok elérhetőségét a varázsló **Biztonsági konfiguráció** oldalán megadott lehetőségek határozzák meg.  

1.  Az a **proxybeállítások** lapon jelölje be **a Wi-Fi profil proxybeállításainak konfigurálása** , ha a vezeték nélküli hálózat proxykiszolgálót használ, és adja meg a konfigurációs adatokat.  

2. Az a **által támogatott platformok** lapon, válassza ki az operációs rendszerek, amelyik számára a Wi-Fi profilt telepíteni kívánja. Másik megközelítésként az **Összes kiválasztása** lehetőségre kattintva telepítheti a Wi-Fi-profilt az összes rendelkezésre álló operációs rendszeren.  

### <a name="next-steps"></a>További lépések
 Információ a Wi-Fi profilok üzembe helyezéséről: [Wi-Fi profilok központi telepítése a System Center Configuration Managerben](deploy-wifi-vpn-email-cert-profiles.md).  

