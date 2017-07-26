---
title: "MacOS ügyfelek - Configuration Manager frissítése |} Microsoft Docs"
description: "Frissítse az ügyfeleket a System Center Configuration Manager Mac számítógépeken."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 74c60941-5eae-4905-9e58-252bdb39df96
caps.latest.revision: 10
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 502116b66fc14914ca0606ae416e82202824de7a
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-upgrade-clients-on-mac-computers-in-system-center-configuration-manager"></a>A Mac számítógépeken lévő ügyfelek frissítése a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Kövesse a Mac számítógépeken futó ügyfele frissítése a System Center Configuration Manager-alkalmazás használatával magas szintű lépéseket. Választhatja azt is, hogy letölti a Mac-ügyfél telepítési fájljait, egy megosztott hálózati helyre vagy a Mac számítógép egyik helyi mappájába másolja azokat, és megkéri a felhasználókat, hogy futtassák manuálisan a telepítést.  

> [!NOTE]  
>  Mielőtt elvégzi ezeket a lépéseket, győződjön meg arról, hogy a Mac számítógép megfelel az előfeltételeknek. Lásd: [Mac számítógépeken támogatott operációs rendszerek](../../../plan-design/configs/supported-operating-systems-for-clients-and-devices.md#mac-computers).  

## <a name="step-1-download-the-latest-mac-client-installation-file-from-the-microsoft-download-center"></a>1. lépés: Töltse le a Mac ügyfél legújabb telepítési fájlját a Microsoft Download Center webhelyről  
 A Mac-ügyfél a Configuration Manager nem található meg a Configuration Manager telepítési adathordozóján, és a Microsoft Download Center kell letölteni. A Mac-ügyfél telepítési fájljait egy ConfigmgrMacClient.msi nevű Windows Installer-fájl tartalmazza.  

 Ezt a fájlt a [Microsoft letöltőközpontból](http://go.microsoft.com/fwlink/p/?LinkId=525184)töltheti le.  

## <a name="step-2-run-the-downloaded-installation-file-to-create-the-mac-client-installation-file"></a>2. lépés: Futtassa a letöltött telepítési fájlt, hogy létrehozza a Mac ügyfél telepítő fájlját  
 Windows alapú számítógépen futtassa a letöltött **ConfigmgrMacClient.msi** fájlt, hogy az kicsomagolja a Mac ügyfél **Macclient.dmg**nevű telepítő fájlját. Ez a fájl a fájlok kicsomagolása után alapértelmezetten a **C:\Program Files (x86)\Microsoft\System Center 2012 Configuration Manager Mac Client** nevű mappában található a Windows számítógépen.  

## <a name="step-3-extract-the-client-installation-files"></a>3. lépés: Bontsa ki az Ügyféltelepítő fájlokat  
 Másolja a Macclient.dmg fájlt egy hálózati megosztási helyre vagy a Mac számítógép egyik helyi mappájába. Ezek után a Mac számítógépről indulva csatlakoztassa, majd nyissa meg a Macclient.dmg fájlt, és másolja a Mac számítógép egyik helyi mappájába.  

## <a name="step-4-create-a-cmmac-file-that-can-be-used-to-create-an-application"></a>4. lépés: Hozzon létre olyan .cmmac fájlt, amely használható alkalmazás létrehozása  

1.  Használja a **CMAppUtil** eszközt (ez a Mac ügyféltelepítési fájlok **Eszközök** mappájában található), hogy az ügyféltelepítési csomagból .cmmac fájlt hozzon létre. Ezt a fájlt a Configuration Manager-alkalmazás létrehozására használható.  

2.  Másolja az új **CMClient.pkg.cmmac** fájlt olyan helyre, a Configuration Manager konzolt futtató számítógép számára elérhető.  

 További információkért lásd: a [kiegészítő eljárások alkalmazások Mac számítógépeken létrehozása és telepítése](/sccm/apps/get-started/creating-mac-computer-applications#supplemental-procedures-to-create-and-deploy-applications-for-mac-computers).  

## <a name="step-5-create-and-deploy-an-application-containing-the-mac-client-files"></a>**5. lépés:** Hozzon létre és telepítsen egy alkalmazást, a Mac ügyfél fájljait tartalmazó  

1.  Az alkalmazás létrehozása a Configuration Manager konzolon a **CMClient.pkg.cmmac** fájlt, amely tartalmazza az Ügyféltelepítő fájlokat.  

2.  Végezze el a Mac számítógépek ezen alkalmazásának központi telepítését a hierarchiájába.  

 További információkért lásd: [létrehozása Mac számítógépekhez készült alkalmazások a System Center Configuration Managerrel](../../../../apps/get-started/creating-mac-computer-applications.md).  

## <a name="step-6-users-install-the-latest-client"></a>6. lépés: Felhasználók telepítik a legfrissebb ügyfélszoftvert  
 A Mac ügyfelek felhasználók felszólítást kapnak, hogy egy frissítést adunk ki a Configuration Manager-ügyfél áll rendelkezésre, és telepítenie kell. Miután a felhasználók telepítették az ügyfelet, újra kell indítaniuk a Mac számítógépüket.  

 A számítógép újraindítása után a számítógép beléptetési varázslója automatikusan lekéri az új tanúsítványt.  

 Ha nem használja a Configuration Manager-regisztrációt, de egymástól függetlenül telepíti az ügyféltanúsítványt a Configuration Manager alkalmazásból, lásd: [a frissített ügyfelet a létező tanúsítvány használatára konfigurálja](#BKMK_UpgradingClient_MachineEnrollment).  

##  <a name="BKMK_UpgradingClient_MachineEnrollment"></a> Configure the upgraded client to use an existing certificate  
 Hajtsa végre a következő eljárást, hogy elkerülje a számítógép beléptetési varázslójának futását, és hogy a frissített ügyfelet a már meglévő ügyféltanúsítvány használatára konfigurálja.  

-   A Configuration Manager konzolon a típusú konfigurációelem létrehozása **Mac OS X**.  

-   Adjon hozzá ehhez a konfigurálási elemhez **Parancsfájl**beállítástípusú beállítást.  

-   A beállításhoz adja hozzá a következő parancsfájlt:  

    ```  
    #!/bin/sh  
    echo "Starting script\n"  
    echo "Changing directory to MAC Client\n"  
    cd /Users/Administrator/Desktop/'MAC Client'/  
    echo "Import root cert\n"  
    /usr/bin/sudo /usr/bin/security import /Users/Administrator/Desktop/'MAC Client'/Root.pfx -A -k /Library/Keychains/System.Keychain -P ROOT  
    echo "Using openssl to convert pfx to a crt\n"  
    /usr/bin/sudo openssl pkcs12 -in /Users/Administrator/Desktop/'MAC Client'/Root.pfx -out Root1.crt -nokeys -clcerts -passin pass:ROOT  
    echo "Adding trust to root cert\n"  
    /usr/bin/sudo /usr/bin/security add-trusted-cert -d -r trustRoot -k /Library/Keychains/System.Keychain Root1.crt  
    echo "Import client cert\n"  
    /usr/bin/sudo /usr/bin/security import /Users/Administrator/Desktop/'MAC Client'/MacClient.pfx -A -k /Library/Keychains/System.Keychain -P MAC  
    echo "Executing ccmclient with MP\n"  
    sudo ./ccmsetup -MP https://SCCM34387.SCCM34387DOM.NET/omadm/cimhandler.ashx  
    echo "Editing Plist file\n"  
    sudo /usr/libexec/Plistbuddy -c 'Add:SubjectName string CMMAC003L' /Library/'Application Support'/Microsoft/CCM/ccmclient.plist  
    echo "Changing directory to CCM\n"  
    cd /Library/'Application Support'/Microsoft/CCM/  
    echo "Making connection to the server\n"  
    sudo open ./CCMClient  
    echo "Ending Script\n"  
    exit  

    ```  

-   Felveheti a konfigurációelemet egy referenciakonfigurációba, majd telepítse a referenciakonfigurációt minden olyan Mac számítógépre, amelyek egymástól függetlenül telepítsen egy tanúsítványt a Configuration Manager alkalmazásból.  

 Hozhat létre és telepíthet a Mac számítógépek konfigurálási elemeinek kapcsolatos további információkért lásd: [a System Center Configuration Manager ügyfélalkalmazással felügyelt Mac OS X-eszközökön a konfigurálási elemeinek létrehozásáról](../../../../compliance/deploy-use/create-configuration-items-for-mac-os-x-devices-managed-with-the-client.md) és [központi telepítése a System Center Configuration Managerben referenciakonfigurációk](../../../../compliance/deploy-use/deploy-configuration-baselines.md).  

