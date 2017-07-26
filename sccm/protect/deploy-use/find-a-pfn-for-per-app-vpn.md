---
title: "Csomagcsalád nevének (PFN) megkeresése az alkalmazásonkénti VPN |} Microsoft Docs"
description: "További tudnivalók a kétféleképpen található egy csomagcsalád nevét, hogy egy alkalmazásonkénti VPN konfigurálásához."
ms.custom: na
ms.date: 10/06/2016
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 47118499-3d26-4c25-bfde-b129de7eaa59
caps.latest.revision: 3
author: Nbigman
ms.author: nbigman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: bff083fe279cd6b36a58305a5f16051ea241151e
ms.openlocfilehash: ce50645155ecb14a82d8b982aa69c0f87dd15fbf
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="find-a-package-family-name-pfn-for-per-app-vpn"></a>Csomagcsalád nevének (PFN) megkeresése az alkalmazásonkénti VPN

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


Két módon lehet a PFN megkeresése egy alkalmazásonkénti VPN konfigurálásához.

## <a name="find-a-pfn-for-an-app-thats-installed-on-a-windows-10-computer"></a>A Windows 10 rendszerű számítógépeket telepített alkalmazás pfn-JÉNEK megkeresése

Ha dolgozunk az alkalmazás már telepítve van a Windows 10 rendszerű számítógépeket, használhatja a [Get-AppxPackage](https://technet.microsoft.com/library/hh856044.aspx) PowerShell-parancsmag segítségével beolvashatja a PFN.

A Get-AppxPackage szintaxisa a következő:

` Parameter Set: __AllParameterSets`
` Get-AppxPackage [[-Name] <String> ] [[-Publisher] <String> ] [-AllUsers] [-User <String> ] [ <CommonParameters>]`

> [!NOTE]
> Előfordulhat, hogy a PFN lekéréséhez rendszergazdaként futtathatja a Powershellt

Ha például a a számítógép-használat telepített összes univerzális alkalmazásra vonatkozó adatokat lekérni `Get-AppxPackage`.

Amelyet egy alkalmazás tudja a nevét, vagy a név egy részének adatait `Get-AppxPackage *<app_name>`. Megjegyzés: a helyettesítő karaktert, különösen hasznos használatát, ha nem biztos abban, az alkalmazás teljes nevét. A OneNote adatainak lekéréséhez például használja `Get-AppxPackage *OneNote`.


A OneNote beolvasott adatok itt található:

`Name                   : Microsoft.Office.OneNote`

`Publisher              : CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US`

`Architecture           : X64`

`ResourceId             :`

`Version                : 17.6769.57631.0`

`PackageFullName        : Microsoft.Office.OneNote_17.6769.57631.0_x64__8wekyb3d8bbwe`

`InstallLocation        : C:\Program Files\WindowsApps`

`\Microsoft.Office.OneNote_17.6769.57631.0_x64__8wekyb3d8bbwe`

`IsFramework            : False`

**`PackageFamilyName      : Microsoft.Office.OneNote_8wekyb3d8bbwe`**

`PublisherId            : 8wekyb3d8bbwe`



## <a name="find-a-pfn-if-the-app-is-not-installed-on-a-computer"></a>A PFN megkeresésére, ha az alkalmazás nincs telepítve a számítógépen

1.    Ugrás a https://www.microsoft.com/en-us/store/apps
2.    A keresési sávon, írja be az alkalmazás nevét. A jelen példában keressen OneNote-bA.
3.    Kattintson az alkalmazásra mutató hivatkozást. Vegye figyelembe, hogy az elérhető URL-cím végén egy több betűből álló rendelkezik. A példánkban az URL-cím néz ki:`https://www.microsoft.com/en-us/store/apps/onenote/9wzdncrfhvjl`
4.    Egy másik lapon illessze be a következő URL-címet, `https://bspmts.mp.microsoft.com/v1/public/catalog/Retail/Products/<app id>/applockerdata`, ahol `<app id>` azonosítót a https://www.microsoft.com/en-us/store/apps -, hogy a 3. lépésben az URL-cím végén betűsorra kapott. A fenti példában, a OneNote, például kell beillesztenie: `https://bspmts.mp.microsoft.com/v1/public/catalog/Retail/Products/9wzdncrfhvjl/applockerdata`.

Az Edge a kívánt információk; az Internet Explorerben kattintson **nyitott** -információt. A PFN értéke az első sor kap. Ez a példa az eredmények megjelenítését:


`{`
`  "packageFamilyName": "Microsoft.Office.OneNote_8wekyb3d8bbwe",`
`  "packageIdentityName": "Microsoft.Office.OneNote",`
`  "windowsPhoneLegacyId": "ca05b3ab-f157-450c-8c49-a1f127f5e71d",`
`  "publisherCertificateName": "CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US"`
`}`

