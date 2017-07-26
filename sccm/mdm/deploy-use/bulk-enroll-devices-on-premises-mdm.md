---

title: "Eszközök csoportos regisztrálása |} Microsoft dokumentumok |} A helyszíni MDM"
description: "Eszközök csoportos regisztrálása a helyszíni mobileszköz-kezelés a System Center Configuration Managerben az automatizált módon."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: b36f5e4a-2b57-4d18-83f6-197081ac2a0a
caps.latest.revision: 13
caps.handback.revision: 0
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3b1451edaed69a972551bd060293839aa11ec8b2
ms.openlocfilehash: be9596537e9c80a6d78aa0685d33382bfd242afe
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-bulk-enroll-devices-with-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>A helyszíni mobileszköz-kezelés a System Center Configuration Manager-eszközök tömeges regisztrálása

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


A System Center Configuration Manager helyszíni mobileszköz-kezelés csoportos regisztrálás automatizáltabb regisztrálást tesz, felhasználóregisztráció, amely megköveteli a felhasználóktól a hitelesítő adatokat, hogy regisztrálja az eszközt képest-eszközök regisztrációjával kapcsolatos.  A csoportos regisztrálás során az eszköz hitelesítése egy regisztrációs csomaggal történik. A csomag (egy .ppkg fájl) tartalmaz egy tanúsítványprofilt és opcionálisan egy Wi-Fi profilt, amennyiben az eszköznek intranetkapcsolatra van szüksége a regisztrálás támogatásához.  

> [!NOTE]  
>  Az aktuális ág a Configuration Manager helyszíni mobileszköz-kezelés a következő operációs rendszereket futtató eszközök beléptetési támogatja:  
>   
> -  Windows 10 Enterprise  
> -   Windows 10 Pro  
> -   Windows 10 Team  
> -   Windows 10 mobil verzió  
> -   Windows 10 Mobile Enterprise
> -   Windows 10 IoT Enterprise   

Az alábbi feladatok azt ismertetik, hogyan csoportos regisztrálása számítógépek és eszközök a\-helyszíni mobileszköz-kezelés:  

-   [Tanúsítványprofil létrehozása](#bkmk_createCert)  

-   [Wi-Fi profil létrehozása](#CreateWifi)  

-   [Beléptetési profil létrehozása](#bkmk_createEnroll)  

-   [Regisztrációs csomagfájl (.ppkg fájl) létrehozása](#bkmk_createPpkg)  

-   [Eszköz csoportos regisztrálása a csomag használatával](#bkmk_getPpkg)  

-   [Eszköz regisztrálásának ellenőrzése](#bkmk_verifyEnroll)  

##  <a name="bkmk_createCert"></a> Tanúsítványprofil létrehozása  
 A regisztrációs csomag fő összetevője egy tanúsítványprofil, amellyel a rendszer automatikusan kiépít egy megbízható főtanúsítványt az eszköz regisztrálása során.  A legfelső szintű tanúsítványra szükség az eszközök és a szükséges helyrendszerszerepkörök közötti megbízható kommunikációhoz\-helyszíni mobileszköz-kezelés. A főtanúsítvány nélkül az eszköz nem lesz megbízható a közte és a beléptetési pont, a beléptetési proxypontot, a terjesztési pont és az eszközfelügyeleti pont helyrendszerszerepköröket üzemeltető szerverek közötti HTTPS-kapcsolatok tekintetében.  

 A rendszer a előkészítése során\-helyszíni mobileszköz-kezelés, a regisztrációs csomag tanúsítványprofiljában használhat legfelső szintű tanúsítvány exportálása. A megbízható legfelső szintű tanúsítvány beszerzésére, lásd: [a legfelső szintű tanúsítvány exportálása a webkiszolgáló-tanúsítvány](../../mdm/get-started/set-up-certificates-on-premises-mdm.md#bkmk_exportCert).  

 Hozzon létre egy tanúsítványprofilt az exportált főtanúsítvány használatával. Útmutatásért lásd: [tanúsítványprofilok létrehozása a System Center Configuration Managerben](../../protect/deploy-use/create-certificate-profiles.md).  

##  <a name="CreateWifi"></a> Wi-Fi profil létrehozása  
 A csoportos regisztráláshoz használt csomag másik összetevője egy Wi-Fi profil. Egyes eszközök a hálózati beállítások kiépítéséig nem rendelkeznek a regisztráció támogatásához szükséges hálózati kapcsolattal. A regisztrációs csomagban lévő Wi-Fi profil arra szolgál, hogy hálózati kapcsolatot lehessen létesíteni az eszköz számára.  

 A Configuration Manager Wi-Fi profil létrehozásához kövesse a [Wi-Fi profilok létrehozása a System Center Configuration Managerben](../../protect/deploy-use/create-wifi-profiles.md).  

> [!IMPORTANT]  
>A következő két problémák tartsa szem előtt, amikor csoportos regisztráláshoz Wi-Fi profil létrehozása:
>
> - A Configuration Manager aktuális ágának csak támogatja a következő Wi-Fi biztonsági beállításokat a\-helyszíni mobileszköz-kezelés:  
>   
>   - Biztonsági típusok: **WPA2-Enterprise** vagy **WPA2-Personal**  
>   - Titkosítási típusok: **AES** vagy **TKIP**  
>   - EAP-típusok: **Intelligens kártya vagy egyéb tanúsítvány** vagy **PEAP**  
>
>
> - Habár a Configuration Manager egy beállítást a proxykiszolgáló-adatok a Wi-Fi profil, azt nem konfigurálja a proxyt az eszköz regisztrálásakor. Állítsa be a proxykiszolgáló a regisztrált eszközökkel kell, ha a beállításokat a konfigurációs elemek, eszközök regisztrált, vagy a második csomagot, a Windows Image and Configuration Designer (ICD) terjesztendő ügyféloldali a csoportos regisztrációs csomagot a létrehozása után telepítheti.

##  <a name="bkmk_createEnroll"></a> Beléptetési profil létrehozása  
 A beléptetési profil segítségével megadhatja az eszköz beléptetéséhez szükséges beállításokat, beleértve egy tanúsítványprofilt, amely dinamikusan kiépíti az eszközhöz szükséges főtanúsítványt, valamint egy Wi-Fi profilt, amely kiépíti a hálózati beállításokat, amennyiben szükséges.  

 Beléptetési profil létrehozása előtt bizonyosodjon meg arról, hogy rendelkezik létrehozott tanúsítványprofillal és Wi-Fi profillal (amennyiben szükséges). További információkért lásd: [Tanúsítványprofil létrehozása](#bkmk_createCert) és [Wi-Fi profil létrehozása](#CreateWifi).  

#### <a name="to-create-an-enrollment-profile"></a>Beléptetési profil létrehozása:  

1.  Kattintson a Configuration Manager konzolon **eszközök és megfelelőség** >**áttekintése** >**minden céges eszköz** >**Windows** >**beléptetési profilok**.  

2.  Kattintson a jobb gombbal a **Beléptetési profil** lehetőségre, majd kattintson a **Profil létrehozása**opcióra.  

3.  A Beléptetési profil létrehozása varázslóban adja meg a profil nevét, ellenőrizze, hogy **Felügyeleti szolgáltatóként** **Helyszíni**van megadva, majd kattintson a **Tovább**gombra.  

4.  Válassza ki a helykódot és kattintson a **Tovább**gombra.  

5.  Válassza ki a **Csak intranet**lehetőséget, jelölje ki a beléptetési proxy pontokat, amelyek segítségével az eszköz elindítja a beléptetési folyamatot, majd kattintson a **Tovább**gombra.  

6.  Válassza ki a megbízható főtanúsítványt tartalmazó tanúsítványprofilt (a [Create a certificate profile](#bkmk_createCert)című szakaszban létrehozott profilt), majd kattintson a **Tovább**gombra.  

7.  Válassza ki az eszközök számára az internethez való csatlakozáshoz szükséges hálózati beállításokat tartalmazó Wi-Fi profilt (a [Create a Wi-Fi profile](#CreateWifi)című szakaszban létrehozott profilt), majd kattintson a **Tovább**gombra.  

    > [!NOTE]  
    >  Ha nem használ Wi-Fi profilt a regisztrációs csomaghoz, akkor hagyja ki ezt a lépést.  

8.  Erősítse meg a beléptetési profil beállításait, és kattintson a **tovább**. Kattintson a **Bezárás** gombra a varázslóból való kilépéshez.  

##  <a name="bkmk_createPpkg"></a> Regisztrációs csomagfájl (.ppkg fájl) létrehozása  
 A regisztrációs csomag a fájl, amely eszközök csoportos regisztrálása a a segítségével\-helyszíni mobileszköz-kezelés.  Ezt a fájlt a Configuration Manager létre kell hozni. Windows Image and Configuration Designer (ICD) is létrehozhat hasonló csomagokat, de csak a Configuration Manager alkalmazásban létrehozott csomagokkal használható az eszközök regisztrálása a\-helyszíni mobileszköz-kezelés kezdetétől a végéig. A Windows ICD használatával létrehozott csomagok csak a regisztráláshoz szükséges egyszerű felhasználónevet (UPN-t) biztosítják, magát a regisztrációs folyamatot nem hajtják végre.  

 A regisztrációs csomag létrehozásához a Windows 10-hez készült Windows Assessment and Deployment Toolkit (ADK) szükséges.  A Configuration Manager konzolt futtató kiszolgálón győződjön meg arról, hogy az 1511-es verziója a Windows ADK telepítése. További információkért lásd a [Download kits and tools for Windows 10](https://msdn.microsoft.com/windows/hardware/dn913721.aspx)című témakör az ADK-ra vonatkozó szakaszát.  

> [!TIP]  
>  Ha eltávolítja a Configuration Manager konzol egy regisztrációs csomagot, az eszközök regisztrálása nem használható. A csomagok eltávolításával is kezelheti azokat a csomagokat, amelyeket már nem kíván eszközök csoportos regisztrálására használni.  

#### <a name="to-create-an-enrollment-package-ppkg-file"></a>Regisztrációs csomagfájl (.ppkg fájl) létrehozása:  

1.  Kattintson a jobb gombbal az imént (a [Beléptetési profil létrehozása](#bkmk_createEnroll)című szakaszban) létrehozott profilra, majd kattintson az **Exportálás**lehetőségre.  

2.  Kattintson a **Tallózás**gombra, keressen egy helyet, ahová menteni szeretné a .ppkg fájlt, adja meg a csomag nevét, majd kattintson a **Mentés**lehetőségre.  

3.  Ha jelszavas védelemmel szeretné ellátni a csomagot, jelölje be a **Csomag titkosítása**jelölőnégyzetet, kattintson az **Exportálás** gombra és várjon nagyjából 10 másodpercet, amíg az exportálás befejeződik.  

    > [!NOTE]  
    >  Ha titkosította a csomagot, a Configuration Manager biztosít egy üzenetet, amelyben a visszafejtett jelszót. Mindenképpen mentse el a jelszóadatokat, mivel szüksége lesz rájuk a csomag eszközökön való kiépítéséhez.  

4.  Kattintson az **OK**gombra.  

##  <a name="bkmk_getPpkg"></a> Eszköz csoportos regisztrálása a csomag használatával  
 A csomagot az adott eszköz a kezdőélmény (OOBE) folyamatával való kiépítését megelőzően vagy azt követően is használhatja eszközök regisztrálására.   A regisztrációs csomagot az eredeti hardvergyártó (OEM) kiépítési csomagja is tartalmazhatja.  

 Csoportos regisztráláshoz a csomagot fizikailag el kell juttatni az eszközre. A regisztrációs csomagot igényeitől függően számos módon eljuttathatja az eszközre:  

-   Másolás a fájlrendszerből  

-   Csatolás e-mailhez  

-   Másolás kis hatótávolságú kommunikációt (NFC) használó kapcsolaton keresztül  

-   Másolás memóriakártyáról  

-   Vonalkód beolvasása  

-   Másolás megosztott eszközről  

-   Felvétel OEM kiépítési csomagba  

#### <a name="to-bulk-enroll-a-device"></a>Eszköz csoportos regisztrálása:  

1.  A regisztrálni kívánt eszközön keresse meg a regisztrációs csomagot (a fájlkezelő segítségével) és kattintson duplán a .ppkg fájlra.  

2.  Kattintson az **Igen** gombra a Felhasználó fiókok felügyeletének üzenetében.  

3.  A párbeszédpanelen kéri fel, ha a csomag helyről, megbízható, kattintson a **Igen, vegye fel azt**.  

     A regisztrációs folyamat elindul és körülbelül 5 percet vesz igénybe.  

4.  Nyissa meg a **Beállításokat**.  

5.  Kattintson a  **Fiókok** > **Munkahelyi hozzáférés**rendszerhez szükséges helyrendszerszerepkörök közötti megbízható kommunikációhoz szükséges. Sikeres beléptetés esetén megjelenik egy fiók a **Vállalati alkalmazások**szakaszban.  

6.  Kattintson a fiókra, és kattintson a **szinkronizálási**, amely elindítja kezelése a Configuration Managerrel.  

##  <a name="bkmk_verifyEnroll"></a> Eszköz regisztrálásának ellenőrzése  
 Ellenőrizheti, hogy eszközök sikeres regisztrálását a Configuration Manager konzolon.  

-   A Configuration Manager konzol elindítása.  

-   Kattintson a **Eszközök és megfelelőség** > **Áttekintés** > **Eszközök**rendszerhez szükséges helyrendszerszerepkörök közötti megbízható kommunikációhoz szükséges. A regisztrált eszköz megjelenik a listán.  

