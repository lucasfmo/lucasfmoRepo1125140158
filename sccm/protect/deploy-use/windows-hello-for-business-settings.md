---
title: "Üzleti beállítások a Windows Hello |} Microsoft Docs"
description: "Ismerje meg, hogyan integrálható a vállalati Windows Hello-a System Center Configuration Managerrel."
ms.custom: na
ms.date: 04/25/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a95bc292-af10-4beb-ab56-2a815fc69304
caps.latest.revision: 17
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 699b79b68440b61904a9053e5004318a2a248bfd
ms.openlocfilehash: 75def95561feb35f2f060f0daa72291983324d4f
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="windows-hello-for-business-settings-in-system-center-configuration-manager"></a>A Windows Hello for Business megadható beállításai a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager lehetővé teszi az integrációt a Windows Hello-üzleti (korábbi nevén Microsoft Passport for Windows), amely egy alternatív bejelentkezési mód a Windows 10-eszközökre. A Hello for Business Active Directoryt vagy egy Azure Active Directory-fiókot használ jelszó, intelligens kártya vagy virtuális intelligens kártya helyett.  

A Hello for Business lehetővé teszi jelszó helyett **felhasználói kézmozdulatok** használatát a bejelentkezéshez. A felhasználói hitelesítési mód lehet egy egyszerű PIN-kód, biometrikus hitelesítés vagy egy külső eszköz, például egy ujjlenyomat-olvasó.

[További információk a vállalati Windows Hello-](https://docs.microsoft.com/windows/access-protection/hello-for-business/hello-identity-verification)

 A Configuration Manager két módon integrálható a vállalati Windows Hello:  

-   A Configuration Manager segítségével szabályozhatja, hogy mely kézmozdulatok felhasználók és nem használható a bejelentkezéshez.  

-   A hitelesítési tanúsítványokat tárolhatja a Windows Hello for Business kulcstároló-szolgáltatójában. További információkért lásd: [Tanúsítványprofilok](introduction-to-certificate-profiles.md).  

- Telepítheti a Windows Hello üzleti házirendek tartományhoz csatlakoztatott Windows 10 rendszerű eszközökre a Configuration Manager-ügyfél. Ez a konfiguráció leírása [konfigurálása vállalati Windows Hello tartományhoz csatlakoztatott Windows 10 eszközökön](#configure-windows-hello-for-business-on-domain-joined-windows-10-devices), az alábbi. A Configuration Manager használatakor az Intune (hibrid) is ezeket a beállításokat a Windows 10 és Windows 10 Mobile-eszközökhöz, de nem a Configuration Manager-ügyfelet futtató, tartományhoz csatlakozó eszközök. Lásd: [konfigurálása vállalati Windows Hello (hibrid) beállítások](../../mdm/deploy-use/windows-hello-for-business-settings.md) további információt.

## <a name="configure-windows-hello-for-business-on-domain-joined-windows-10-devices"></a>Konfigurálja a vállalati Windows Hello-tartományhoz csatlakoztatott Windows 10-eszközökön
Szabályozhatja a Windows Hello for Business-beállítások tartományhoz csatlakoztatott Windows 10-eszközök háromféleképpen:

- Hozzon létre, és központi telepítése a Windows Hello-profil üzleti. Ez az az ajánlott módszer.
- Csoportházirend segítségével.  
- Egy PowerShell-parancsfájlt is használhatja.

Megjegyzendő, hogy ez a konfiguráció mellett is telepíteni kell a tanúsítványprofilokat, a [tanúsítványprofil konfigurálása](#configure-a-certificate-profile).

## <a name="configure-a-windows-hello-for-business-profile"></a>A Windows Hello-profil üzleti konfigurálása  

A Configuration Manager konzolon a **hozzáférés a vállalati erőforrásokhoz**, kattintson a jobb gombbal **üzleti profilok a Windows Hello-** válassza **új** profil varázsló elindításához. Adja meg a beállítások a varázsló által kért tekintse át és hagyja jóvá a beállításokat az utolsó oldalon, és kattintson a **Bezárás**. Íme egy példa hogyan nézhet ki a beállítások:  

![A Windows Hello for Business beállításai](../media/Hello-for-Business-settings.png)

## <a name="configure-windows-hello-for-business-with-group-policy-in-active-directory"></a>A csoportházirend az Active Directory vállalati Windows Hello konfigurálása  

Az Active Directory csoportházirend segítségével konfigurálhatja a Windows 10-es tartományhoz csatlakozó eszközök Hello rendelkezés felhasználó a vállalati hitelesítő adatok, amikor a felhasználók bejelentkeznek a Windowsba:

1.  A Windows Server-számítógépen nyissa meg a Kiszolgálókezelőt, és navigáljon a **eszközök** > **csoportházirend-kezelő**.    

2.  Az a **csoportházirend-kezelő** párbeszédpanelen bontsa ki a tartományhoz, amelyben engedélyezze az automatikus munkahelyi csatlakoztatást szeretne.    

3.  Kattintson a jobb gombbal **csoportházirend-objektumok**, és kattintson a **új**.  

4.  Az a **új csoportházirend-objektum** párbeszédpanel mezőbe írjon be egy nevet az új csoportházirend-objektum, például **engedélyezése vállalati Windows Hello**, és kattintson a **OK**.  

5.  Az a **csoportházirend-objektumok** csomópontot, kattintson a jobb gombbal az objektum imént létrehozott, és kattintson **szerkesztése**.  

6.  Az a **Csoportházirendkezelés-szerkesztő** párbeszédpanel navigáljon a **számítógép konfigurációja** > **házirendek** > **felügyeleti sablonok** > **Windows-összetevők** > **vállalati Windows Hello**.  

7.  Kattintson a jobb gombbal **engedélyezése vállalati Windows Hello** majd **szerkesztése**.   

8.  Válassza ki **engedélyezve**, kattintson a **alkalmaz**, és kattintson a **OK**.

Most társíthatja az imént létrehozott csoportházirend-objektum egy tetszés szerinti helyre. Példa:    

   Egy adott szervezeti egység (OU) az Active Directory, ahol a Windows 10-es tartományhoz csatlakoztatott számítógépek lesznek elhelyezve.    

   Windows 10-tartományhoz csatlakoztatott számítógépeket, amelyek automatikusan regisztrálva lesz az Azure AD tartalmazó biztonsági csoport.    

## <a name="configure-windows-hello-for-business-by-deploying-a-powershell-script-with-configuration-manager"></a>Konfigurálja a vállalati Windows Hello egy PowerShell-parancsfájlt a Configuration Manager központi telepítésével    
Hozzon létre, és központi telepítése a következő PowerShell-parancsfájl alkalmazások kezelése a Configuration Manager használatával.    

**PowerShell.exe - ExecutionPolicy áthidaló - NoLogo - NoProfile-parancs "& {új ItemProperty"HKLM:\Software\Policies\Microsoft\PassportForWork"-Name"engedélyezett"értékét 1 - PropertyType típusa"DWord"-Force}" ** 

A Configuration Manager alkalmazás-kezeléssel kapcsolatos további információkért lásd: [alkalmazások kezelése a System Center Configuration Manager bemutatása](/sccm/apps/understand/introduction-to-application-management).  

## <a name="configure-a-certificate-profile-to-enroll-the-windows-hello-for-business-enrollment-certificate-in-configuration-manager"></a>Tanúsítványprofil konfigurálása a Windows Hello for Business beléptetési tanúsítvány Configuration Managerbe való beléptetéséhez  
 Ha Windows Hello for Business tanúsítvány-alapú bejelentkezést kíván használni, konfigurálja az alábbiakat:  

-   A Configuration Manager-tanúsítványprofil.  

-   A tanúsítványprofilban válassza ki a sablont, amely intelligens kártyás bejelentkezési kibővített kulcshasználatot alkalmaz.  

-    Ha szeretné tárolni a tanúsítványprofilok a Windows Hello-üzleti kulcstároló, és a tanúsítványprofil használja a **intelligens kártyás bejelentkezés** EKU, konfigurálnia kell a következő engedélyeket kulcs regisztrációt, hogy a tanúsítvány helyesen érvényességéről.
Kell először hozott létre a **kulcs rendszergazdák** csoportnak, és az összes Configuration Manager felügyeletipont-számítógépek tagként ehhez a csoporthoz hozzáadni.

    1.    Bejelentkezés egy tartomány tartományvezérlői vagy a felügyeleti munkaállomásokra tartományi rendszergazda vagy a megfelelő hitelesítő adatokat.
    2.    Nyissa meg **Active Directory – felhasználók és számítógépek**.
    3.    A navigációs ablaktáblában kattintson a jobb gombbal tartománynevére, és kattintson **tulajdonságok**.
    4.    Az a **biztonsági** lapján a  *<domain name>*  **tulajdonságok** párbeszédpanel, kattintson a **speciális**. Ha a **biztonsági** lap nem jelenik meg, kapcsolja be a **speciális funkciók** a a **nézet** menüjében **Active Directory – felhasználók és számítógépek**.
    5.    Kattintson a **Hozzáadás** gombra.
    6.    Az a **engedélybejegyzés**  *<domain name>*  párbeszédpanel, kattintson a **rendszerbiztonsági tag kiválasztása**.
    7.    Az a **válassza ki a felhasználó, számítógép, szolgáltatásfiók vagy csoport** párbeszédpanelen írja be **kulcs rendszergazdák** a a **adja meg a kiválasztandó objektum nevét** szövegmezőben.  Kattintson az **OK** gombra.
    8.    Az a **vonatkozik** listáról válassza ki **leszármazott felhasználó objektumai**.
    9.    Görgessen a lap alján, és kattintson a **törli az összes**.
    10.    Az a **tulajdonságok** szakaszban jelölje be **olvassa el az msDS-KeyCredentialLink**.
    11.    Kattintson a **OK** háromszor a feladat végrehajtásához.


 További információkért lásd: [Tanúsítványprofilok](introduction-to-certificate-profiles.md).  





