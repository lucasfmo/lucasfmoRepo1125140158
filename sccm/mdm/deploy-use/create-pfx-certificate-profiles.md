---
title: "PFX-tanúsítványprofilok létrehozása |} Microsoft Docs"
description: "Útmutató a PFX-fájlok a System Center Configuration Manager segítségével titkosított adatcsere támogatására felhasználó-specifikus tanúsítványokat hoz létre."
ms.custom: na
ms.date: 04/04/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e3bb3e13-3037-4122-93bc-504bfd080a4d
caps.latest.revision: 5
caps.handback.revision: 0
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 26feb0b166beb7e48cb800a5077d00dbc3eec51a
ms.openlocfilehash: 27435316c6e47531ff989bc8956ca0c874131a0e
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-create-pfx-certificate-profiles-in-system-center-configuration-manager"></a>PFX-tanúsítványprofilok létrehozása a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Tanúsítványprofilok működik az Active Directory tanúsítványszolgáltatások és a felügyelt eszközöknek tanúsítványhitelesítést biztosítsanak kiépítése a hálózati eszközök tanúsítványigénylési szolgáltatása szerepkör, úgy, hogy a felhasználók zökkenőmentesen a vállalati erőforrások eléréséhez. Létrehozhat és telepíthet például olyan tanúsítványprofilokat, amelyek ellátják a felhasználókat a szükséges tanúsítványokkal, hogy kezdeményezzenek VPN és vezetéknélküli kapcsolatokat.

[Tanúsítványprofilok](../../protect/deploy-use/introduction-to-certificate-profiles.md) létrehozásáról és konfigurálásáról a tanúsítványprofilok általános információkat nyújt. Ez a témakör a tanúsítványprofilok a PFX-tanúsítványok kapcsolatos néhány vonatkozó információkat mutatja be.

-  A Configuration Manager támogatja a tanúsítványok különböző tanúsítványtárakba, attól függően, hogy a követelmények, az eszköz típusát és az operációs rendszer telepítését. A következő eszközöket az Intune-nal regisztrálásakor támogatja:

 -   iOS  

- Egyéb előfeltételeket, lásd: [profil Előfeltételek tanúsítvány](../../protect/plan-design/prerequisites-for-certificate-profiles.md).

## <a name="pfx-certificate-profiles"></a>PFX-tanúsítványprofilok
System Center Configuration Manager segítségével importálja, majd kiépíteni a felhasználói eszközök személyes információcsere (.pfx) fájlok. A PFX-fájlok segítségével létrehozhat felhasználó-specifikus tanúsítványokat a titkosított adatcsere támogatására.

> [!TIP]  
>  A folyamatot leíró lépésenkénti útmutató: [PFX-tanúsítványprofilok létrehozása és telepítése a Configuration Managerben](http://blogs.technet.com/b/karanrustagi/archive/2015/09/01/how-to-create-and-deploy-pfx-certificate-profiles-in-configuration-manager.aspx).  

## <a name="create-and-deploy-a-personal-information-exchange-pfx-certificate-profile"></a>Hozzon létre, és a személyes információcseréhez kapcsolódó (PFX) tanúsítványprofil központi telepítése  

### <a name="get-started"></a>Első lépések

1.  A System Center Configuration Manager konzolon kattintson **eszközök és megfelelőség**.  

2.  Az **Eszközök és megfelelőség** munkaterületen bontsa ki a **Megfelelőségi beállítások**, majd a **Hozzáférés a vállalati erőforrásokhoz**pontot, és kattintson a **Tanúsítványprofilok**lehetőségre.  

3.  A **Kezdőlap** **Létrehozás** csoportjában kattintson a **Tanúsítványprofil létrehozása**elemre.

4.  A **Tanúsítványprofil létrehozása varázsló** **Általános** lapján adja meg az alábbi adatokat:  

    -   **Név**: Adjon meg egy egyedi nevet a tanúsítványprofilnak. Legfeljebb 256 karakter használható.  

    -   **Leírás**: Adjon meg egy leírást, amely áttekintést ad a tanúsítványprofilról, valamint más olyan releváns információkat, ami segít azonosítani a System Center Configuration Manager-konzolon. Legfeljebb 256 karakter használható.  

    -   **Adja meg a létrehozni kívánt tanúsítványprofil típusát**: PFX-tanúsítványok esetén adja meg:  

        -   **Személyes információk Exchange PKCS #12 (PFX) beállítások – importálás**: Válassza ezt a PFX-tanúsítvány importálásához.  
       

### <a name="import-a-pfx-certificate"></a>PFX-tanúsítvány importálásához

PFX-tanúsítvány importálásához, a Configuration Manager SDK lesz szüksége. Bármely felhasználó számára importált tanúsítványok pedig települnek egyik eszközön sem, amely a felhasználó regisztrálja.

1. Az a **PFX-tanúsítvány** oldalán a **Tanúsítványprofil létrehozása varázsló**, adja meg a tanúsítványt a rendszer hol tárolja az eszközökön, amelyre telepítheti azt:
    -     **Telepítés platformmegbízhatósági modulba (TPM), ha van**  
    -   **Telepítés csak platformmegbízhatósági modulba (TPM)** 
    -   **Telepítse a Windows Hello for Business szolgáltatásba, másként meghibásodás történik** 
    -   **Telepítés szoftverkulcstároló-szolgáltatóba** 
2. Kattintson a **Tovább** gombra. 
3. Az a **által támogatott platformok** lap a varázslóban válassza ki az eszközplatformokat, amelyeken ez a tanúsítvány lesz telepítve, majd kattintson az **következő**.
4. A Letöltőközpontból ([http://go.microsoft.com/fwlink/?LinkId=613525](http://go.microsoft.com/fwlink/?LinkId=613525)) elérhető, Windows 8.1 rendszerhez készült SDK segítségével telepítse a PFX-létrehozási parancssori eszközt. A Configuration Manager 2012 SP2 verzióhoz adott PFX-létrehozási parancsfájl hozzáad egy SMS_ClientPfxCertificate osztályt az SDK-hoz. Ez az osztály az alábbi módszereket foglalja magába:  

    -   ImportForUser  

    -   DeleteForUser  

     Mintaparancsfájl:  

```  
    $EncryptedPfxBlob = "<blob>"  
    $Password = "abc"  
    $ProfileName = "PFX_Profile_Name"  
    $UserName = "ComputerName\Administrator"  

    #New pfx  
    $WMIConnection = ([WMIClass]"\\nksccm\root\SMS\Site_MDM:SMS_ClientPfxCertificate")  
        $NewEntry = $WMIConnection.psbase.GetMethodParameters("ImportForUser")  
        $NewEntry.EncryptedPfxBlob = $EncryptedPfxBlob  
        $NewEntry.Password = $Password  
        $NewEntry.ProfileName = $ProfileName  
        $NewEntry.UserName = $UserName  
    $Resource = $WMIConnection.psbase.InvokeMethod("ImportForUser",$NewEntry,$null)  

```  

A következő parancsfájl-változókat módosítani kell a parancsfájljában:  

   -   blob\ = a PFX base64-titkosított blobja  
   -   $Password = A PFX-fájl jelszava  
   -   $ProfileName = A PFX-profil neve  
   -   ComputerName = A gazdaszámítógép neve   



### <a name="finish-up"></a>Végül

1.  Kattintson a **Tovább**gombra, tekintse át az **Összegzés** lapot, majd zárja be a varázslót.  
2.  A PFX-fájlt tartalmazó tanúsítványprofil mostantól elérhető a **Tanúsítványprofilok** munkaterületen. 
3.  A profilt telepítheti a **eszközök és megfelelőség** munkaterületen nyissa meg **megfelelőségi beállítások** > **hozzáférés a vállalati erőforrásokhoz** > **Tanúsítványprofilok**, kattintson a jobb gombbal, majd kattintson a tanúsítvány **telepítés**. 



## <a name="see-also"></a>További információ
[Hozzon létre egy új tanúsítványprofilt](../../protect/deploy-use/create-certificate-profiles.md#create-a-new-certificate-profile) végigvezeti a Tanúsítványprofil létrehozása varázsló.

[Wi-Fi, VPN, e-mail és a tanúsítványprofilok központi telepítése](../../protect/deploy-use/deploy-wifi-vpn-email-cert-profiles.md) információkat nyújt azokról a tanúsítványprofilok központi telepítése.
